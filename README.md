# MyToken Smart Contract

A simple smart contract for creating and managing your own token on the Ethereum blockchain.

## Description

This project demonstrates a basic ERC-20 like token implementation in Solidity. The contract includes functionalities to mint new tokens and burn existing tokens. It also keeps track of token balances and total supply.

## Getting Started

### Installing

1. Clone the repository:
   ```bash
   git clone https://github.com/yourusername/your-repository.git
   cd your-repository

2.Ensure you have a Solidity development environment set up. You can use Remix IDE (https://remix.ethereum.org/) or any other local development setup.
Executing Program
1.Open the MyToken.sol file in your Solidity development environment.

2.Compile the contract using the Solidity compiler.

3.Deploy the contract to a local or test Ethereum network with the required constructor parameters (name, symbol, initial supply).

4.Interact with the contract functions:

Mint Tokens:

MyToken.mint(0xRecipientAddress, 100);

Burn Tokens:

MyToken.burn(0xHolderAddress, 50);

Help

For common issues, ensure:

1.You have a proper Solidity development environment.
2.You are connected to the right Ethereum network.
3.The addresses you are interacting with are valid.
4.If you encounter any issues, refer to the Solidity documentation or reach out to the authors below.

Authors
Your Name - @sarth9

License
This project is licensed under the MIT License - see the LICENSE.md file for details.

// SPDX-License-Identifier: MIT
pragma solidity 0.8.18;

contract MyToken {
    
    // Public variables to store the details about your coin
    string public name;
    string public symbol;
    uint256 public totalSupply;

    // Mapping from addresses to their balances
    mapping(address => uint256) public balances;

    // Constructor to initialize the token details
    constructor(string memory _name, string memory _symbol, uint256 _initialSupply) {
        name = _name;
        symbol = _symbol;
        totalSupply = _initialSupply;
        balances[msg.sender] = _initialSupply; // Initial supply goes to the contract deployer
    }

    // Mint function to create new tokens
    function mint(address _to, uint256 _value) public {
        totalSupply += _value;
        balances[_to] += _value;
    }

    // Burn function to destroy tokens
    function burn(address _from, uint256 _value) public {
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
