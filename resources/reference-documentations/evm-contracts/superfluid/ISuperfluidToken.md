# ISuperfluidToken

## Functions

### getHost

```solidity
function getHost(
) external returns (address host)
```

Get superfluid host contract address

### realtimeBalanceOf

```solidity
function realtimeBalanceOf(
    address account,
    uint256 timestamp
) external returns (int256 availableBalance, uint256 deposit, uint256 owedDeposit)
```

Calculate the real balance of a user, taking in consideration all agreements of the account

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | for the query |
| `timestamp` | uint256 | Time of balance |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `availableBalance` | int256 | Real-time balance |
| `deposit` | uint256 | Account deposit |
| `owedDeposit` | uint256 | Account owed Deposit |

### realtimeBalanceOfNow

```solidity
function realtimeBalanceOfNow(
    address account
) external returns (int256 availableBalance, uint256 deposit, uint256 owedDeposit, uint256 timestamp)
```

Calculate the realtime balance given the current host.getNow() value

realtimeBalanceOf with timestamp equals to block timestamp

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | for the query |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `availableBalance` | int256 | Real-time balance |
| `deposit` | uint256 | Account deposit |
| `owedDeposit` | uint256 | Account owed Deposit |
| `timestamp` | uint256 |  |

### isAccountCritical

```solidity
function isAccountCritical(
    address account,
    uint256 timestamp
) external returns (bool isCritical)
```

Check if account is critical

A critical account is when availableBalance < 0

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | The account to check |
| `timestamp` | uint256 | The time we'd like to check if the account is critical (should use future) |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `isCritical` | bool | Whether the account is critical |

### isAccountCriticalNow

```solidity
function isAccountCriticalNow(
    address account
) external returns (bool isCritical)
```

Check if account is critical now (current host.getNow())

A critical account is when availableBalance < 0

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | The account to check |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `isCritical` | bool | Whether the account is critical |

### isAccountSolvent

```solidity
function isAccountSolvent(
    address account,
    uint256 timestamp
) external returns (bool isSolvent)
```

Check if account is solvent

An account is insolvent when the sum of deposits for a token can't cover the negative availableBalance

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | The account to check |
| `timestamp` | uint256 | The time we'd like to check if the account is solvent (should use future) |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `isSolvent` | bool | True if the account is solvent, false otherwise |

### isAccountSolventNow

```solidity
function isAccountSolventNow(
    address account
) external returns (bool isSolvent)
```

Check if account is solvent now

An account is insolvent when the sum of deposits for a token can't cover the negative availableBalance

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | The account to check |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `isSolvent` | bool | True if the account is solvent, false otherwise |

### getAccountActiveAgreements

```solidity
function getAccountActiveAgreements(
    address account
) external returns (contract ISuperAgreement[] activeAgreements)
```

Get a list of agreements that is active for the account

An active agreement is one that has state for the account

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | Account to query |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `activeAgreements` | contract ISuperAgreement[] | List of accounts that have non-zero states for the account |

### createAgreement

```solidity
function createAgreement(
    bytes32 id,
    bytes32[] data
) external
```

Create a new agreement

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `id` | bytes32 | Agreement ID |
| `data` | bytes32[] | Agreement data |

### getAgreementData

```solidity
function getAgreementData(
    address agreementClass,
    bytes32 id,
    uint256 dataLength
) external returns (bytes32[] data)
```

Get data of the agreement

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `id` | bytes32 | Agreement ID |
| `dataLength` | uint256 |  |

#### Return Values

| Name | Type | Description |
| :--- | :--- | :---------- |
| `data` | bytes32[] | Data of the agreement |

### updateAgreementData

```solidity
function updateAgreementData(
    bytes32 id,
    bytes32[] data
) external
```

Create a new agreement

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `id` | bytes32 | Agreement ID |
| `data` | bytes32[] | Agreement data |

### terminateAgreement

```solidity
function terminateAgreement(
    bytes32 id,
    uint256 dataLength
) external
```

Close the agreement

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `id` | bytes32 | Agreement ID |
| `dataLength` | uint256 |  |

### updateAgreementStateSlot

```solidity
function updateAgreementStateSlot(
    address account,
    uint256 slotId,
    bytes32[] slotData
) external
```

Update agreement state slot

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | Account to be updated

NOTE
- To clear the storage out, provide zero-ed array of intended length |
| `slotId` | uint256 |  |
| `slotData` | bytes32[] |  |

### getAgreementStateSlot

```solidity
function getAgreementStateSlot(
    address agreementClass,
    address account,
    uint256 slotId,
    uint256 dataLength
) external returns (bytes32[] slotData)
```

Get data of the slot of the state of an agreement

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `account` | address | Account to query |
| `slotId` | uint256 | slot id of the state |
| `dataLength` | uint256 | length of the state data |

### settleBalance

```solidity
function settleBalance(
    address account,
    int256 delta
) external
```

Settle balance from an account by the agreement

The agreement needs to make sure that the balance delta is balanced afterwards

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `account` | address | Account to query. |
| `delta` | int256 | Amount of balance delta to be settled

Modifiers:
 - onlyAgreement |

### makeLiquidationPayoutsV2

```solidity
function makeLiquidationPayoutsV2(
    bytes32 id,
    bytes liquidationTypeData,
    address liquidatorAccount,
    bool useDefaultRewardAccount,
    address targetAccount,
    uint256 rewardAmount,
    int256 targetAccountBalanceDelta
) external
```

Make liquidation payouts (v2)

#### Parameters

| Name | Type | Description |
| :--- | :--- | :---------- |
| `id` | bytes32 | Agreement ID |
| `liquidationTypeData` | bytes | Data regarding the version of the liquidation schema and the type |
| `liquidatorAccount` | address | Address of the executor of the liquidation |
| `useDefaultRewardAccount` | bool | Whether or not the default reward account receives the rewardAmount |
| `targetAccount` | address | Account of the stream sender |
| `rewardAmount` | uint256 | The amount the reward recepient account will receive |
| `targetAccountBalanceDelta` | int256 | The amount the sender account balance should change by

- If a bailout is required (bailoutAmount > 0)
  - the actual reward (single deposit) goes to the executor,
  - while the reward account becomes the bailout account
  - total bailout include: bailout amount + reward amount
  - the targetAccount will be bailed out
- If a bailout is not required
  - the targetAccount will pay the rewardAmount
  - the liquidator (reward account in PIC period) will receive the rewardAmount

Modifiers:
 - onlyAgreement |

## Events

### AgreementCreated

```solidity
event AgreementCreated(
    address agreementClass,
    bytes32 id,
    bytes32[] data
)
```

Agreement created event

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `id` | bytes32 | Agreement ID |
| `data` | bytes32[] | Agreement data |
### AgreementUpdated

```solidity
event AgreementUpdated(
    address agreementClass,
    bytes32 id,
    bytes32[] data
)
```

Agreement updated event

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `id` | bytes32 | Agreement ID |
| `data` | bytes32[] | Agreement data |
### AgreementTerminated

```solidity
event AgreementTerminated(
    address agreementClass,
    bytes32 id
)
```

Agreement terminated event

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `id` | bytes32 | Agreement ID |
### AgreementStateUpdated

```solidity
event AgreementStateUpdated(
    address agreementClass,
    address account,
    uint256 slotId
)
```

Agreement account state updated event

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `account` | address | Account updated |
| `slotId` | uint256 | slot id of the agreement state |
### AgreementLiquidatedV2

```solidity
event AgreementLiquidatedV2(
    address agreementClass,
    bytes32 id,
    address liquidatorAccount,
    address targetAccount,
    address rewardAccount,
    uint256 rewardAmount,
    int256 targetAccountBalanceDelta,
    bytes liquidationTypeData
)
```

Agreement liquidation event v2 (including agent account)

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `id` | bytes32 | Agreement ID |
| `liquidatorAccount` | address | Address of the executor of the liquidation |
| `targetAccount` | address | Account of the stream sender |
| `rewardAccount` | address | Account that collects the reward or bails out insolvent accounts |
| `rewardAmount` | uint256 | The amount the reward recipient account balance should change by |
| `targetAccountBalanceDelta` | int256 | The amount the sender account balance should change by |
| `liquidationTypeData` | bytes | The encoded liquidation type data including the version (how to decode)

NOTE:
Reward account rule:
- if the agreement is liquidated during the PIC period
  - the rewardAccount will get the rewardAmount (remaining deposit), regardless of the liquidatorAccount
  - the targetAccount will pay for the rewardAmount
- if the agreement is liquidated after the PIC period AND the targetAccount is solvent
  - the liquidatorAccount will get the rewardAmount (remaining deposit)
  - the targetAccount will pay for the rewardAmount
- if the targetAccount is insolvent
  - the liquidatorAccount will get the rewardAmount (single deposit)
  - the rewardAccount will pay for both the rewardAmount and bailoutAmount
  - the targetAccount will receive the bailoutAmount |
### AgreementLiquidated

```solidity
event AgreementLiquidated(
    address agreementClass,
    bytes32 id,
    address penaltyAccount,
    address rewardAccount,
    uint256 rewardAmount
)
```

Agreement liquidation event (DEPRECATED BY AgreementLiquidatedBy)

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `agreementClass` | address | Contract address of the agreement |
| `id` | bytes32 | Agreement ID |
| `penaltyAccount` | address | Account of the agreement to be penalized |
| `rewardAccount` | address | Account that collect the reward |
| `rewardAmount` | uint256 | Amount of liquidation reward

NOTE:

[DEPRECATED] Use AgreementLiquidatedV2 instead |
### Bailout

```solidity
event Bailout(
    address bailoutAccount,
    uint256 bailoutAmount
)
```

System bailout occurred (DEPRECATED BY AgreementLiquidatedBy)

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `bailoutAccount` | address | Account that bailout the penalty account |
| `bailoutAmount` | uint256 | Amount of account bailout

NOTE:

[DEPRECATED] Use AgreementLiquidatedV2 instead |
### AgreementLiquidatedBy

```solidity
event AgreementLiquidatedBy(
    address liquidatorAccount,
    address agreementClass,
    bytes32 id,
    address penaltyAccount,
    address bondAccount,
    uint256 rewardAmount,
    uint256 bailoutAmount
)
```

Agreement liquidation event (DEPRECATED BY AgreementLiquidatedV2)

#### Parameters:

| Name | Type | Description |
| :--- | :--- | :---------- |
| `liquidatorAccount` | address | Account of the agent that performed the liquidation. |
| `agreementClass` | address | Contract address of the agreement |
| `id` | bytes32 | Agreement ID |
| `penaltyAccount` | address | Account of the agreement to be penalized |
| `bondAccount` | address | Account that collect the reward or bailout accounts |
| `rewardAmount` | uint256 | Amount of liquidation reward |
| `bailoutAmount` | uint256 | Amount of liquidation bailouot

NOTE:
Reward account rule:
- if bailout is equal to 0, then
  - the bondAccount will get the rewardAmount,
  - the penaltyAccount will pay for the rewardAmount.
- if bailout is larger than 0, then
  - the liquidatorAccount will get the rewardAmouont,
  - the bondAccount will pay for both the rewardAmount and bailoutAmount,
  - the penaltyAccount will pay for the rewardAmount while get the bailoutAmount. |
