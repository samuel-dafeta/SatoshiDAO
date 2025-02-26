# SatoshiDAO: Bitcoin-Native Decentralized Governance Protocol

A Layer 2 decentralized autonomous organization protocol leveraging Bitcoin's security through Stacks blockchain.

## Overview

SatoshiDAO implements enterprise-grade DAO infrastructure with native Bitcoin integration, featuring:

- Bitcoin-settled governance decisions
- STX-based staking mechanics
- Reputation-weighted voting system
- Cross-DAO collaboration framework
- Regulatory-compliant treasury management

## Key Features

### 1. Membership Management

- Permissionless joining/leaving
- STX token staking with time locks
- Last interaction tracking (block height)
- Sybil-resistance through stake weighting

### 2. Governance Engine

- Proposal lifecycle management:
  - Creation → Voting → Execution → Archival
- Time-bound proposals (1440 blocks ≈ 10 days)
- Stake-weighted voting power calculation:
  ```clarity
  Voting Power = (Reputation × 10) + STX Stake
  ```

### 3. Treasury Management

- Multi-signature compatible vault
- Transparent fund allocation
- Donation tracking with reputation incentives
- STX-based asset handling

### 4. Reputation System

- Earned through:
  - Proposal creation (+1 REP)
  - Voting participation (+1 REP)
  - Successful execution (+5 REP)
  - Treasury donations (+2 REP)
- Inactivity decay (50% reduction after 4320 blocks)

### 5. Cross-DAO Collaboration

- Secure inter-DAO proposal sharing
- Mutual acceptance protocol
- Joint governance auditing trails

## Technical Specifications

| Component               | Specification           |
| ----------------------- | ----------------------- |
| Blockchain              | Stacks (Bitcoin L2)     |
| Smart Contract Language | Clarity 2.0             |
| Consensus Mechanism     | Proof of Transfer (PoX) |
| Proposal Lifetime       | 1440 blocks (~10 days)  |
| Inactivity Threshold    | 4320 blocks (~30 days)  |
| Base Reputation Unit    | 1 REP                   |

## Installation & Deployment

### Prerequisites

- Node.js v18+
- [Clarinet](https://docs.hiro.so/clarinet)
- [Stacks CLI](https://docs.hiro.so/get-started/install)

## Usage Examples

### Join DAO

```clarity
(contract-call? .satoshidao-core join-dao)
```

### Create Proposal

```clarity
(contract-call? .satoshidao-core create-proposal
  "Upgrade Protocol"
  "UTF-8 description"
  u5000
)
```

### Vote on Proposal

```clarity
(contract-call? .satoshidao-core vote-on-proposal u42 true)
```

## Security Considerations

1. **Audited Contracts**  
   All core functions include:

   - Reentrancy protection
   - Overflow/underflow guards
   - Time-lock validations

2. **Access Controls**

   - Owner-restricted functions
   - Member-only governance actions
   - Proposal expiration enforcement

3. **Fund Safeguards**
   - Minimum stake requirements
   - Treasury withdrawal limits
   - Multi-sig execution approval

## Contributing

1. Fork repository
2. Create feature branch: `feat/your-feature`
3. Submit PR with:
   - Test coverage
   - Clarity-lint results
   - Architecture diagrams
