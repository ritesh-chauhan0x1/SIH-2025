# INRChain

**Indian Rupee (INR) cryptocurrency.**

INRChain is a stablecoin and blockchain ecosystem designed to simplify global trade and become a major competitor to USDT. It runs on its own custom blockchain, supporting free crypto trading and exchanges. INRChain integrates with UPI for free and instant payments worldwide, enabling seamless crypto integration with India's payment infrastructure. The INRChain token is a stablecoin pegged 1:1 to the Indian Rupee (INR).

## Key Features
- Custom blockchain mainnet (not just a token)
- Free and instant crypto trading and exchanges
- UPI integration for global, instant, and free payments
- Stablecoin: 1 INRChain = 1 INR
- Designed to simplify global trade and remittance
- Aims to be a major competitor to USDT

## Repository Structure
- `chain/` — Rust workspace for the INRChain blockchain node and supporting crates
- `backend/` — APIs/services (to be implemented)
- `wallet/` — Web wallet (React/TypeScript, to be implemented)
- `explorer/` — Block explorer (backend + frontend, to be implemented)
- `ops/` — DevOps: Docker, K8s, CI/CD (to be implemented)
- `scripts/` — Helper scripts for local/testnet/mainnet (to be implemented)
- `docs/` — Whitepaper outline, tokenomics, and guides


## Technical Architecture Flowchart

```mermaid
flowchart TD
	subgraph User
		U1[Web Wallet (React/TS)]
		U2[UPI App]
	end
	subgraph Blockchain
		N1[INRChain Node (Rust)]
		N2[Consensus Engine (PoS)]
		N3[State Storage (RocksDB)]
		N4[P2P Network (libp2p)]
		N5[JSON-RPC/REST API]
		N6[Smart Contract Runtime (WASM)]
	end
	subgraph Backend
		B1[Trading Engine]
		B2[UPI Integration Service]
		B3[Remittance/Settlement]
	end
	subgraph Explorer
		E1[Block Explorer UI]
		E2[Indexer (Node.js/PG)]
	end
	subgraph Monitoring
		M1[Prometheus]
		M2[Grafana]
	end

	U1 -- "Buy/Sell, Transfer, Query" --> N5
	U1 -- "UPI Payment" --> B2
	U2 -- "INR ↔ INRChain" --> B2
	B2 -- "Mint/Burn, Notify" --> N5
	N5 -- "RPC Calls" --> N1
	N1 -- "Block Proposals" --> N2
	N1 -- "State Read/Write" --> N3
	N1 -- "Broadcast Blocks/Txs" --> N4
	N1 -- "Smart Contract Calls" --> N6
	N1 -- "Emit Events" --> E2
	E2 -- "Index Data" --> E1
	N1 -- "Metrics" --> M1
	M1 -- "Dashboards" --> M2
	B1 -- "Orderbook, Trades" --> N5
	B3 -- "Settlement" --> N5
```

> This diagram can be previewed in Markdown editors that support Mermaid (e.g., VS Code with the Mermaid extension).
