# OurToken

`OurToken` is an ERC20 token contract that allows you to create your own token with a custom name, symbol, and initial supply. It inherits from the OpenZeppelin `ERC20` contract, which provides a standard implementation of the ERC20 token standard.

## Features

- Customizable token name and symbol
- Minting of tokens to the contract deployer's address
- Standard ERC20 functionality (transfer, approve, transferFrom, etc.)

## Usage

### Hardhat

To use `OurToken` in your Hardhat project, follow these steps:

1. Install the OpenZeppelin library:
```zsh
npm install @openzeppelin/contracts
```


Copy the `OurToken.sol` file into your Hardhat project's contracts directory.

In your Hardhat configuration file (hardhat.config.js), make sure you have the following settings:
```js
module.exports = {
  solidity: "0.8.18",
  // ...other configurations
};
```


Write a deployment script or test that deploys the OurToken contract with the desired initial supply:
```js
const { ethers } = require("hardhat");

async function deployOurToken() {
  const initialSupply = ethers.utils.parseEther("1000"); // 1000 tokens
  const OurToken = await ethers.getContractFactory("OurToken");
  const ourToken = await OurToken.deploy(initialSupply);
  await ourToken.deployed();
  console.log("OurToken deployed to:", ourToken.address);
}
```


Run the deployment script or test using Hardhat:
```js
npx hardhat run scripts/deploy.js
```

Foundry
To use OurToken in your Foundry project, follow these steps:

Copy the `OurToken.sol` file into your Foundry project's src directory.

Install the OpenZeppelin library using Foundry's dependency manager:
```zsh
forge install OpenZeppelin/openzeppelin-contracts
```


Write a test or script that deploys the OurToken contract with the desired initial supply:
```solidity
pragma solidity ^0.8.18;

import "forge-std/Test.sol";
import "../src/OurToken.sol";

contract OurTokenTest is Test {
    function testDeployOurToken() public {
        uint256 initialSupply = 1000 ether; // 1000 tokens
        OurToken ourToken = new OurToken(initialSupply);
        assertEq(ourToken.totalSupply(), initialSupply);
    }
}
```


Run the test or script using Foundry:
```zsh
forge test
```

License
This contract is released under the MIT License.# foundry-erc20-f23
