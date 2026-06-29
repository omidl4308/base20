# base20
from web3 import Web3

# RPC Endpoints
BASE_RPC = "https://mainnet.base.org"
LINEA_RPC = "https://rpc.linea.build"

base = Web3(Web3.HTTPProvider(BASE_RPC))
linea = Web3(Web3.HTTPProvider(LINEA_RPC))

# آخرین بلاک
base_block = base.eth.block_number
linea_block = linea.eth.block_number

# دریافت اطلاعات بلاک
base_info = base.eth.get_block(base_block)
linea_info = linea.eth.get_block(linea_block)

base_tx_count = len(base_info.transactions)
linea_tx_count = len(linea_info.transactions)

print("=" * 50)
print(" Base vs Linea Transaction Comparison ")
print("=" * 50)

print(f"Base")
print(f"Latest Block : {base_block}")
print(f"Transactions : {base_tx_count}")

print()

print(f"Linea")
print(f"Latest Block : {linea_block}")
print(f"Transactions : {linea_tx_count}")

print()

if base_tx_count > linea_tx_count:
    print(f"Base has {base_tx_count - linea_tx_count} more transactions.")
elif linea_tx_count > base_tx_count:
    print(f"Linea has {linea_tx_count - base_tx_count} more transactions.")
else:
    print("Both networks have the same number of transactions.")
