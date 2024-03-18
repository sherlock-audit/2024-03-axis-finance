
# Axis Finance contest details

- Join [Sherlock Discord](https://discord.gg/MABEWyASkp)
- Submit findings using the issue page in your private contest repo (label issues as med or high)
- [Read for more details](https://docs.sherlock.xyz/audits/watsons)

# Q&A

### Q: On what chains are the smart contracts going to be deployed?
Mainnet, OP Stack Rollups (Blast, Mode, Optimism, Base), Arbitrum Stack Rollups (Arbitrum One, Kinto)
___

### Q: Which ERC20 tokens do you expect will interact with the smart contracts? 
Any that implement ERC20 Metadata, have between 6 and 18 decimals, and do not have a fee-on-transfer functionality. We know that rebasing tokens can be accounted for incorrectly and aren't generally supported. In the case of Blast's USDB and WETH (which rebase), the contract owner accrues the rebases for tokens sitting in the contract.
___

### Q: Which ERC721 tokens do you expect will interact with the smart contracts? 
None
___

### Q: Do you plan to support ERC1155?
No
___

### Q: Which ERC777 tokens do you expect will interact with the smart contracts? 
None
___

### Q: Are there any FEE-ON-TRANSFER tokens interacting with the smart contracts?

Fee-on-transfer tokens are not supported unless the contract is allowlisted to transfer tokens with no fee.
___

### Q: Are there any REBASING tokens interacting with the smart contracts?

See above. Rebasing tokens with strictly increasing token balances should work in the contract, but extra balances will be accrued by the contract. Rebasing tokens with decreasing token balances are not supported.
___

### Q: Are the admins of the protocols your contracts integrate with (if any) TRUSTED or RESTRICTED?
TRUSTED
___

### Q: Is the admin/owner of the protocol/contracts TRUSTED or RESTRICTED?
TRUSTED
___

### Q: Are there any additional protocol roles? If yes, please explain in detail:
The only role for the protocol is the AuctionHouse owner. They can install new modules and upgrade existing modules (Auctions or Derivatives) in the AuctionHouse, set fee values, set the address that protocol fees accrue to, and set configuration parameters on the modules.
___

### Q: Is the code/contract expected to comply with any EIPs? Are there specific assumptions around adhering to those EIPs that Watsons should be aware of?
No
___

### Q: Please list any known issues/acceptable risks that should not result in a valid finding.
See above for known issues with rebasing tokens. Additionally, there are known risks with the ECIES encryption library around the security of the alt_bn_128 curve and the use of hash-based key derivation functions. More info is provided in src/lib/ECIES.sol. 
___

### Q: Please provide links to previous audits (if any).
None
___

### Q: Are there any off-chain mechanisms or off-chain procedures for the protocol (keeper bots, input validation expectations, etc)?
No
___

### Q: In case of external protocol integrations, are the risks of external contracts pausing or executing an emergency withdrawal acceptable? If not, Watsons will submit issues related to these situations that can harm your protocol's functionality.
There aren't external integrations except for Blast-specific yield and fee accrual integrations. Since these are part of the base chain deployment, emergency pausing or withdrawal is acceptable.
___

### Q: Do you expect to use any of the following tokens with non-standard behaviour with the smart contracts?
In general, it's possible that some of these tokens will be used to create auctions. However, we don't commit to supporting every ERC20 token. We only care about issues with these tokens that would result in loss of funds from users or the protocol as a result of an auction being created with one of these tokens.
___

### Q: Add links to relevant protocol resources
See the REA
___



# Audit scope


[moonraker @ 3cc44b63da95a41616617300bca24a159ad6a52b](https://github.com/Axis-Fi/moonraker/tree/3cc44b63da95a41616617300bca24a159ad6a52b)
- [moonraker/src/AuctionHouse.sol](moonraker/src/AuctionHouse.sol)
- [moonraker/src/Catalogue.sol](moonraker/src/Catalogue.sol)
- [moonraker/src/bases/Auctioneer.sol](moonraker/src/bases/Auctioneer.sol)
- [moonraker/src/bases/FeeManager.sol](moonraker/src/bases/FeeManager.sol)
- [moonraker/src/blast/BlastAuctionHouse.sol](moonraker/src/blast/BlastAuctionHouse.sol)
- [moonraker/src/blast/modules/BlastGas.sol](moonraker/src/blast/modules/BlastGas.sol)
- [moonraker/src/blast/modules/auctions/BlastEMPAM.sol](moonraker/src/blast/modules/auctions/BlastEMPAM.sol)
- [moonraker/src/blast/modules/derivatives/BlastLinearVesting.sol](moonraker/src/blast/modules/derivatives/BlastLinearVesting.sol)
- [moonraker/src/lib/Callbacks.sol](moonraker/src/lib/Callbacks.sol)
- [moonraker/src/lib/ECIES.sol](moonraker/src/lib/ECIES.sol)
- [moonraker/src/lib/MaxPriorityQueue.sol](moonraker/src/lib/MaxPriorityQueue.sol)
- [moonraker/src/lib/Transfer.sol](moonraker/src/lib/Transfer.sol)
- [moonraker/src/modules/Auction.sol](moonraker/src/modules/Auction.sol)
- [moonraker/src/modules/Condenser.sol](moonraker/src/modules/Condenser.sol)
- [moonraker/src/modules/Derivative.sol](moonraker/src/modules/Derivative.sol)
- [moonraker/src/modules/Modules.sol](moonraker/src/modules/Modules.sol)
- [moonraker/src/modules/auctions/EMPAM.sol](moonraker/src/modules/auctions/EMPAM.sol)
- [moonraker/src/modules/auctions/FPAM.sol](moonraker/src/modules/auctions/FPAM.sol)
- [moonraker/src/modules/derivatives/LinearVesting.sol](moonraker/src/modules/derivatives/LinearVesting.sol)
- [moonraker/src/modules/derivatives/SoulboundCloneERC20.sol](moonraker/src/modules/derivatives/SoulboundCloneERC20.sol)

