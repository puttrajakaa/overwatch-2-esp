# API Reference

## WalletManager

| Method | Description |
|--------|-------------|
| `InitializeAsync()` | Opens SQLite store and applies schema migrations |
| `ImportMnemonicAsync(label, mnemonic, passphrase, networks)` | Creates encrypted vault and derives initial accounts |
| `ListVaultsAsync()` | Returns all vault metadata entries |
| `GetAccountsAsync(vaultId, networkId?)` | Lists derived accounts with cached balances |

## SyncCoordinator

| Method | Description |
|--------|-------------|
| `RunFullSyncAsync(vaultId, networkId)` | Executes full discover → fetch → index → persist cycle |

## CLI Commands

```bash
ow2esp import --label "main" --mnemonic "..." --passphrase "..."
ow2esp list
ow2esp sync <vault-id>
ow2esp balance <vault-id>
ow2esp export <vault-id>
```

## Configuration (`appsettings.json`)

| Key | Default | Description |
|-----|---------|-------------|
| `Wallet:DefaultVaultDirectory` | `.wallets` | Local vault storage path |
| `Wallet:DefaultAccountScanDepth` | `5` | Accounts derived per network on import |
| `Wallet:MaxConcurrentNetworkRequests` | `4` | RPC concurrency limit |
| `Wallet:RpcTimeoutSeconds` | `30` | HTTP timeout for node requests |
| `Wallet:EnabledNetworks` | `[eth, btc, polygon]` | Default networks for new vaults |
