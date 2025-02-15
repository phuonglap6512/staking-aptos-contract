
# Staking Aptos Contract

## Overview

This project provides a **staking contract** on the Aptos blockchain, allowing users to stake tokens and earn rewards. The contract includes functionalities for creating staking pools, depositing, withdrawing, and managing rewards efficiently.

## Features

-   **Create staking pools** with configurable rewards, duration, and limits per user.
    
-   **Stake tokens** to earn rewards over time.
    
-   **Withdraw staked tokens** with pending rewards.
    
-   **Emergency withdrawal** in case of urgent needs.
    
-   **Admin functions** to adjust rewards, stop staking, and manage the contract.
    
-   **Event logging** for tracking deposits, withdrawals, and other actions.
    

## Installation & Setup

### Prerequisites

-   Aptos CLI installed: Installation Guide
    
-   Rust and Move installed: Move Language Guide
    
-   An Aptos account with testnet/mainnet funds
    

### Clone the Repository

```
git clone https://github.com/phuonglap6512/staking-aptos-contract.git
cd staking-aptos-contract
```

### Deploy the Contract

1.  **Compile the Move module**:
    
    ```
    aptos move compile --named-addresses staking=your_aptos_address
    ```
    
2.  **Publish the contract**:
    
    ```
    aptos move publish --named-addresses staking=your_aptos_address
    ```
    

## Usage

### Create a Staking Pool

Admin users can create a staking pool with the following command:

```
stake::create_pool<StakeToken, RewardToken>(admin, symbol, decimals, logo_url, reward_per_second, start_timestamp, end_timestamp, pool_limit_per_user, seconds_for_user_limit);
```

### Stake Tokens

Users can stake tokens in a pool:

```
stake::deposit<StakeToken, RewardToken>(user, amount);
```

### Withdraw Tokens

Withdraw staked tokens along with rewards:

```
stake::withdraw<StakeToken, RewardToken>(user, amount);
```

### Emergency Withdraw

Users can withdraw all their staked tokens without rewards:

```
stake::emergency_withdraw<StakeToken, RewardToken>(user);
```

### Stop Reward Distribution (Admin Only)

Admins can stop rewards for a pool:

```
stake::stop_reward<StakeToken, RewardToken>(admin);
```

## Events

The contract emits events for important actions:

-   **CreatePoolEvent**: Pool creation
    
-   **DepositEvent**: Token deposits
    
-   **WithdrawEvent**: Token withdrawals
    
-   **EmergencyWithdrawEvent**: Emergency withdrawal
    
-   **StopRewardEvent**: Reward distribution stop
    

## Error Codes

-   `ERROR_ONLY_ADMIN (0)`: Only the admin can perform this action.
    
-   `ERROR_POOL_EXIST (1)`: The staking pool already exists.
    
-   `ERROR_INSUFFICIENT_BALANCE (6)`: Insufficient token balance.
    
-   `ERROR_POOL_NOT_EXIST (7)`: The specified pool does not exist.
    
-   `ERROR_POOL_END (14)`: The staking pool has ended.
    

## License

This project is licensed under the MIT License.

## Contact

For questions or support, open an issue on the GitHub repository or contact the developers.

----------

**Note:** Ensure you modify `your_aptos_address` in commands with your actual Aptos address.
