# Swisstronik Mint ERC721 Token Task

Testnet link : [HERE](https://www.swisstronik.com/testnet2/dashboard)


## Steps

### 1. Clone Repository

```bash
git clone https://github.com/zilong77/swisstronik-mint-erc721-token.git
```

```
cd swisstronik-mint-erc721-token
```

### 2. Install Dependency

```bash
npm install
```

### 3. Set .env File

create .env file in root project

```bash
PRIVATE_KEY="your private key"
```

### 4. Update Smart Contract (Skipp if you won't modify NFT name)

- Open contracts folder
- Open Nft.sol file
- Feel free to modify token name and token symbol

```
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC721/ERC721.sol";

contract TestNFT is ERC721 {
    uint256 private _currentTokenId = 0;

    event NFTMinted(address recipient, uint256 tokenId);

    constructor() ERC721("ZilongNFT", "ZILNFT") {}

    function mintNFT(address recipient) public returns (uint256) {
        _currentTokenId += 1;
        uint256 newItemId = _currentTokenId;
        _mint(recipient, newItemId);

        emit NFTMinted(recipient, newItemId);

        return newItemId;
    }

    function burnNFT(uint256 tokenId) public {
        _burn(tokenId);
    }
}

```

### 5. Compile Smart Contract

```bash
npm run compile
```

### 6. Deploy Smart Contract

```bash
npm run deploy
```

### 7. Mint Token

```bash
npm run mint
```

### 8. Last Step

- Open the deployed-adddress.ts (location in utils folder)
- Copy the address and paste the address into testnet dashboard
- Open the tx-hash.txt (location in utils folder)
- Copy the address and paste the tx hash link into testnet dashboard
- push this project to your github and paste your repository link in testnet dashboard

credit :
[Mnuralim](https://github.com/Mnuralim)

