# Experiment 3: Supply Chain Transparency for Luxury Goods
## Aim:
To develop a smart contract that tracks the supply chain of luxury goods, ensuring authenticity.
## Algorithm:
The manufacturer records product creation details on-chain.


The product moves through different supply chain checkpoints.


The ownership of the product can be transferred securely.


Buyers can verify the product’s authenticity.


## Program:
### Name : Masina Sree Karsh
### Register Number : 212223100033
```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

contract LuxurySupplyChain {
    struct Product {
        string name;
        address currentOwner;
        bool verified;
    }

    mapping(uint256 => Product) public products;

    event ProductRegistered(uint256 productId, string name);
    event OwnershipTransferred(uint256 productId, address newOwner);

    function registerProduct(uint256 productId, string memory name) public {
        require(products[productId].currentOwner == address(0), "Product already registered");
        products[productId] = Product(name, msg.sender, true);
        emit ProductRegistered(productId, name);
    }

    function transferOwnership(uint256 productId, address newOwner) public {
        require(products[productId].currentOwner == msg.sender, "Not the owner");
        products[productId].currentOwner = newOwner;
        emit OwnershipTransferred(productId, newOwner);
    }

    function verifyProduct(uint256 productId) public view returns (string memory, address, bool) {
        Product memory p = products[productId];
        return (p.name, p.currentOwner, p.verified);
    }
}
```
## Expected Output:
A luxury good (e.g., a Rolex watch) is registered on-chain.


Ownership is transferred at every checkpoint.


Buyers can check the authenticity before purchasing.

## Output:

![Output 1](https://github.com/user-attachments/assets/5fd131c0-d832-4128-8fc7-f7b619d3c1bf)

![Output 2](https://github.com/user-attachments/assets/aafddd20-a983-45bb-9775-7cd7b0925713)

![Output 3](https://github.com/user-attachments/assets/b8651dac-f6f7-44d4-8c44-29abc7516a8d)

![Output 4](https://github.com/user-attachments/assets/cb76eb0c-b2f3-498a-9ef0-0d695dbe90a6)

## High-Level Overview:
Helps prevent counterfeit luxury goods.


Teaches real-world supply chain use cases.

## RESULT : 
Thus, the execution of the suplly chain Transpanrency for Luxury Goods has executed successfully.
