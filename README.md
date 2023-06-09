# patent-verification-nft

# Purpose:

Consider a scenario where you have conceived a potential startup idea, but you are hesitant to disclose it to the public until you have developed a product from it.
This period between ideation and product release is a critical phase during which the idea must not be exposed to the public. However, in the event that the idea is
leaked and someone steals it, it would be advantageous to have a means of demonstrating that you were the first to conceive of it. 

# Reference Algorithm
	
1.	Define fields related to Intellectual Property.

```
struct IntellectualProperty{
	property_owner: String
	hash: String
	value: String
	uri: String
	is_public: String
	for_sale: String
}
```

2.Match the nft account owner with the program id supplied by the client to verify the blockchain owner.
```
nft_account.owner == program_id
```

3.Read first byte of the data received from the client to get instruction to operate upon.

```
instruction_byte =  data.split_first()
```

I.If  instruction_byte  = = 0, then create new NFT

```
nft_account_data.property_owner = nft_account_owner.key.to_string()
nft_account_data.hash = hash;
nft_account_data.value="00000".to_string()
nft_account_data.is_public = "0".to_string();
nft_account_data.for_sale = "0".to_string();
```

II.If  instruction_byte = = 1, then make NFT public.
```
nft_account_data.is_public = "1".to_string()
```

III.If  instruction_byte = = 2, then make NFT for sale.
```
nft_account_data.for_sale = "1".to_string();
```

IV.If  instruction_byte = = 3, then transfer ownership.
```
nft_account_data.property_owner = new_nft_account_owner.key.to_string();
```

2.2       Data/ Data structure

“struct" is a keyword used in Solidity, a smart contract programming language used on the Ethereum blockchain. 

```
struct PatentNFT { 
uint256 id; // Unique identifier for the PatentNFT 
address owner; // Ethereum address of the current owner of the NFT 
string patentTitle; // Title of the patent 
string patentAbstract; // Abstract of the patent 
string inventorName; // Name(s) of the inventor(s) 
uint256 filingDate; // Date the patent was filed 
uint256 patentNumber; // Patent number assigned by the patent office 
string nftName; // Name of the NFT 
string nftDescription; // Description of the NFT 
string nftImage; // URL of an image representing the NFT 
uint256 nftRoyalty; // Percentage of sales revenue to be paid as royalty to the patent owner 
}

```
