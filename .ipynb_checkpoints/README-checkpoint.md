# Crowdsale ERC20 Token
![ICO](https://miami.bootcampcontent.com/Miami-Boot-Camp/mia-virt-fin-pt-02-2021-u-c/-/raw/master/Homework/21-Advanced-Solidity/Instructions/Images/crowd.png)

### Task
Your company has decided to crowdsale their PupperCoin token in order to help fund the network development.
This network will be used to track the dog breeding activity across the globe in a decentralized way, and allow humans to track the genetic trail of their pets. You have already worked with the necessary legal bodies and have the green light on creating a crowdsale open to the public. However, you are required to enable refunds if the crowdsale is successful and the goal is met, and you are only allowed to raise a maximum of 300 Ether. The crowdsale will run for 24 weeks.
This Blockchain example utilizes the OpenZeppelin Solidity library to create an ERC20 token that is minted through a crowdsale contract.  The contract will allow users to send ETH and get back PUP, or PupperCoin, the hypothetical name of the company's token.  The contract mints the tokens automatically and distributes them to buyers in one transaction.  A real-world pre-production test is shown in which I deploy the crowdsale to the Kovan testnet.

---

# Contract Set-Up / Deployment:
## 1. In Remix create a PupperCoin.sol file to create a standard ERC20Mintable token to include:
- Import OpenZeppelin contracts:
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20Detailed.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/token/ERC20/ERC20Mintable.sol";
- Parameter hardcoded to 18 spaces
- Complile first code, in the construter fill in the Name, Symbol and Initial_Supply for your token and deploy to your local chain using MetaMask

![puppercoin1](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture2.png)
https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture3.png
![puppercoin2](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture3.png)

## 2. Create a PupperCoinSale.sol and import the OpenZepellin contracts for Crowdsale:
- Bootstrap the contract by importing OpenZeppelin contracts:
 - import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/Crowdsale.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/emission/MintedCrowdsale.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/validation/CappedCrowdsale.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/validation/TimedCrowdsale.sol";
    import "https://github.com/OpenZeppelin/openzeppelin-contracts/blob/release-v2.5.0/contracts/crowdsale/distribution/RefundablePostDeliveryCrowdsale.sol";
- Required by parameters set by the crowdsale import are to be set for compiling:
    --  symbol: PPC 
    --  payable wallet
    --  goal: Since RefundablePostDeliveryCrowdsale inherits the RefundableCrowdsale contract, which requires a goal             parameter, you must call the RefundableCrowdsale constructor from your PupperCoinCrowdsale constructor as well as the     others
    --  Cap: for the purpose to identify when the maximun number of Ether reached CappedCrowdsale will be part of the            constructor along with the RefundablePostDeliveryCrowdsale for the purpose to refund transactions that occure after      the goal has reached.
    --  Open and closing time: the tose the parameter of time delivery the Timedcrowsale will also be imported and               parameters set. 
    
- Use https://eth-converter.com/ to convert ETH to WEI. For the facilitation of this excerise hardcode a rate of 1, to maintain parity with Ether units (1 TKN per Ether, or 1 TKNbit per wei). A token (TKN) can be divided into TKNbits just like Ether can be divided into wei. When using a rate of 1, just like 1000000000000000000 wei is equal to 1 Ether, 1000000000000000000 TKNbits is equal to 1 TKN.

## 3. Deploy Crowdsale to local blockchain using MetaMask:
- Deploy the contract for PupperCoinSaleDeployer to be able to have access, to the PupperCoin and PopperSale contracts.
- Indentify and copy past the diffrent token addresses to further expose the contract to be able to interact for transactions.

![coinsale_deploy](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture4.png)

![coinsale_deploy2](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture5.png)

- Switch to PupperCoinSale, find the token sale address that was generated when you deployed the above contract, copy and past that address into the "At Address" field, and select "At Address" button.  You now have an a deplyment of your PupperCoinSale contract and all the additional functionality that comes with it:

![coinsale_deploy3](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture6.png)

- To deploy the PupperCoin contract, select the PupperCoin.sol.  Switch your contract to PupperCoin, and copy and past the token address generated by the PupperCoinSale deployer corresponding to the token_address in your "At Address" field:

![coinsale_deploy4](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture7.png)

## 4. Test Crowdsale by Purchasing Tokens:
1. Change values from Wei to Ether, and transact to interact with MetaMask
2. Scroll up to your PupperCoinSale to access buy token function of the constructer. Access your ganache copy an address and past in the benificiary part of the constructer and transact. Observe MetaMask, accept and confirm the transaction. Once transaction is completed verify in your contructor area the token address, copy and past this in your ADD token area of MetaMask:

![coinsale_deploy5](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture8.png)
![coinsale_deploy6](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture9.png)
---

## 5. Deploy Crowdsale to Ropsten testnet:
- Store the deployed address for later. Switch MetaMask to your desired network (Ropsten), and use the Deploy tab in Remix to deploy your contracts. Take note of the total gas cost, and compare it to how costly it would be in reality. 
- Since you are deploying to a network that you don't have control over, faucets will not likely give out 300 test Ether. You can simply reduce the goal when deploying to a testnet to an amount much smaller, like 10,000 wei.
- Via Etherscan access https://ropsten.etherscan.io/address/0x5ead244f423720d37xXxxxxxxxXXXxxX  - this will link you to the address of your token.

![ropsten_deployment](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture10.png)

## 6. Add Token to MyCrypto and test a transaction:
- You can test the time functionality by replacing now with fakenow, and creating a setter function to modify fakenow to whatever time you want to simulate. You can also set the close time to be now + 5 minutes, or whatever timeline you'd like to test for a shorter crowdsale.
- When sending Ether to the contract, make sure you hit your goal that you set (in this case, 300 ETH), and finalize the sale using the Crowdsale's finalize function. In order to finalize, isOpen must return false (isOpen comes from TimedCrowdsale which checks to see if the close time has passed yet). Since the goal is 300 Ether, you may need to send from multiple accounts. If you run out of prefunded accounts in Ganache, you can create a new workspace.
- Remember, the refund feature of RefundablePostDeliveryCrowdsale only allows for refunds once the crowdsale is closed and the goal is met.  See the OpenZeppelin RefundableCrowdsale documentation for details as to why this is logic is used to prevent potential attacks on your token's value.
- You can add custom tokens in MyCrypto from the Add custom token feature.
- You can also do the same for MetaMask. Make sure to purchase higher amounts of tokens in order to see the denomination appear in your wallets as more than a few wei worth.

![ropsten_deployment_2](https://raw.githubusercontent.com/sheldonpalm69/Crowdsale-ERC20-Token/main/HWCrowdsale/CrowdsaleIMG/ScreenShot/Picture11.png)
