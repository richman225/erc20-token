# ERC20 Token

This is an example in solidity language of an ERC-20 standard Ethereum Token, mintable and burnable, with owner access permissions and module pausable.

## Erc-20

ERC-20 is a standard interface for tokens. 

The following standard allows for the implementation of a standard API for tokens within smart contracts. 

This standard provides basic functionality to transfer tokens, as well as allow tokens to be approved so they can be spent by another on-chain third party.E

More Information about Solidity Language and ERC-20 Standard:

- [Solidity](https://solidity.readthedocs.io/en/v0.6.8/): `v0.6.8`
- [ERC-20](https://eips.ethereum.org/EIPS/eip-20)

## Erc-20 Methods

### Constructor

The `constructor` function set the `name`, `symbol`, `decimals` and `totalSupply` of the token.

### Balance

The view function `balanceOf` returns the account balance of account with address `_owner`.

### Transfer and transferFrom

The method `transfer` transfers `_value` amount of tokens to address `_to`, and fire the `Transfer` event.

The method `transferFrom` allow third account transfers `_value` amount of tokens from other address `_from` to address `_to`, and fire the `Transfer` event.

### Approve

The method `increaseApproval` allows `_spender` to withdraw from one account multiple times, up to the `_addedValue` amount. 

The method `decreaseApproval` reduces the value aprroveed to `_spender` to withdraw from one account multiple times, substracting the `_subtractedValue` to the approval amount. 

If the `_subtractedValue` is bigger than previously approved the value will reduce to 0. 

### Allowance

The view function `allowance` returns the amount which address `_spender` is still allowed to withdraw from `_owner`.

### Mint And Burn

Those methods are not a ERC-20 standard but are commonly used to create and destroy tokens.

The `mintTo` function creates `amount` tokens and assigns them to `account`, increasing the total supply.

The `burnFrom` function destroys `amount` tokens from `account`, reducing the total supply.

Only owner can mint or burn tokens in this case.

## Erc-20 Modules in this example

### Ownable

The Ownable module provides a basic access control mechanism, where there is an account (an owner) that can be granted exclusive access to specific functions.

This module is used through inheritance. 

It will make available the modifier `onlyOwner`, which can be applied to your functions to restrict their use to the owner.

By default, the owner account will be the one that deploys the contract. 

The owner address can be changed with method `transferOwnership`.

### Pausable

Contract module which allows children to implement an emergency stop mechanism that can be triggered by an authorized account.

This module is used through inheritance. 

It will make available the modifiers `whenNotPaused` and `whenPaused`, which can be applied to the functions of your contract.

Only owner can trigger call `pause` and `unpause` methods. 

## Requeriments

- [Node.js](https://nodejs.org/download/release/latest-v10.x/): `>=10.0.0`
- [Truffle](https://www.trufflesuite.com/truffle): `v5.1.9`


## Usage

Clone or donwload this repositorie.

Go to path and run on terminal:

```sh
npm install
```
After running, all dependecies will be downloaded.

### Compile contracts

```sh
truffle compile
```

After running, contract information &mdash; including ABI &mdash; will be available at the `build/contracts/` directory.

### Run tests on Truffle

You can run tests which can be found in the test directory(/test) runing on terminal:

```sh
truffle test
```

Or run tests within a specific file:

```sh
truffle test <file_path>
```

### Run migration and deploy contracts

Create .env file on root with:

```
MNENOMIC = // Your metamask's recovery words
INFURA_API_KEY = // Your Infura API Key after its registration
TOKEN_NAME = "Token Name"
TOKEN_SYMBOL = "ERC"
TOKEN_DECIMALS = 18
TOKEN_TOTALSUPLY = 0
```
Run migrate command

```sh
truffle migrate --network <network_name>
```

Contract address and transaction ID will be shown on screen.
