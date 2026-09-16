# BlockLand Zimbabwe

Blockchain-backed land registry for Zimbabwe — property registration, ownership
records, transfers, and dispute handling, anchored on Stacks.

## Structure

| Path | Stack | Purpose |
| --- | --- | --- |
| [`blockland-contracts/`](blockland-contracts/) | Clarity / Clarinet | On-chain registry contract |
| [`blockland-backend/`](blockland-backend/) | NestJS + TypeORM + Postgres | REST API, auth, IPFS documents |
| [`blockland-frontend/`](blockland-frontend/) | Next.js + Tailwind | Web dashboard |
| [`docs/`](docs/) | — | Wireframe specification |

## Getting started

Each sub-project is installed and run independently.

```bash
# Contracts
cd blockland-contracts && npm install && npm test

# Backend  (expects a Postgres instance)
cd blockland-backend && npm install && npm run start:dev

# Frontend
cd blockland-frontend && npm install && npm run dev
```

## Configuration

Secrets are read from the environment and are never committed. Copy the sample
files and fill them in locally:

- `blockland-backend/.env` — database, JWT, Stacks, and Pinata credentials
- `blockland-frontend/.env.local` — public API and contract addresses

Contract deployment reads `STACKS_DEPLOYER_PRIVATE_KEY` from the environment:

```bash
STACKS_DEPLOYER_PRIVATE_KEY=<hex key> node blockland-contracts/deploy.mjs
```
