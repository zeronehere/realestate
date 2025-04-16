#### Step 1: Install Dependencies for Both Client and Contract

You need to install the dependencies for both the client and the contract.

1. Open a terminal in the **contract** directory and run:
   cd contract
   npm install

2. Open another terminal in the **client** directory and run:
   cd client
   npm install

#### Step 2: Run Hardhat Node

In the **contract** directory, start a local Hardhat network. This will simulate an Ethereum blockchain locally.

   cd contract
   npx hardhat node

This will provide you with **20 testing accounts** and a local Ethereum node running at `http://localhost:8545` with the chain ID `31337`.

#### Step 3: Connect Metamask to Local Network

1. Open your **Metamask** extension in the browser.
2. Set up a new custom RPC network with the following details:
   - Network Name: Localhost
   - New RPC URL: `http://localhost:8545`
   - Chain ID: `31337`
   - Currency Symbol: `ETH`

3. Import one of the 20 testing accounts from the Hardhat console by copying the private key provided when you ran `npx hardhat node`. Use this private key in Metamask to import an account.

#### Step 4: Set Up Pinata IPFS

To store files on IPFS, you need to generate a Pinata API key and secret key.

1. Go to https://www.pinata.cloud/ and create an account if you haven't already.
2. After logging in, go to the **API Keys** section and generate a new key.
3. Copy the **API Key** and **Secret Key**.

#### Step 5: Configure Pinata Keys in the Client

In the **client** directory, configure the Pinata keys by editing the `client/context/constants.js` file:

export const PINATA_API_KEY = "Your_PINATA_API_KEY";
export const PINATA_SECRET_KEY = "Your_PINATA_SECRET_KEY";

#### Step 6: Deploy the Contract

After configuring the Pinata keys, you need to deploy the contract to the local Hardhat network.

In the **contract** directory, run the deployment script:

   cd contract
   npx hardhat run ./scripts/deploy.js --network localhost

This will deploy the contract on the local network and provide you with the contract's **lock address**.

#### Step 7: Update the Client with the Lock Address

Copy the **lock address** provided after the contract deployment, and paste it into `client/context/constants.js`:

export const REAL_ESTATE_ADDRESS = "Your_Lock_Address";

#### Step 8: Start the Client Development Server

Finally, go to the **client** directory and start the development server:
   cd client
   npm run dev

This will start the front-end of your application. Open `http://localhost:3000` in your browser to see the DApp in action.
