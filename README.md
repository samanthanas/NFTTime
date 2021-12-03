# NFTTime - The NFT Sale Price Predictor

A time series modeling tool to help you begin trading NFTs.

![Cryptopunk NFTs](images/nftshutter.jpg)

Author: Samantha Nasti

## Overview

#### Why Trade NFTs? 
    
   - Large investment firms are moving money into crypto 
   - Governments (like City of Miami) are incorporating crypto into city infrastructure
   - Some renowned investment firms are beginning to buy NFTs (like Cryptopunks)
   - Contemporary art has outperformed S&P for years
   - Digital art is more liquid than physical art
    
#### Risks:
   - Industry is new and uncertain: "long term hold" investment strategy is higher risk than short term gains
   - Asset can be traded 24/7 - gap risk is intense ATM especially as space continues to develop "hype"
    
#### Purpose of this Model:
   - Capture prices for NFT "flipping" (swing trading)
   - Help NFT traders forecast what their NFT purchase might look like a week or two later to provide a baseline to assess the approximate risk in this highly volatile space

## Data

Opensea Events API: https://docs.opensea.io/reference/retrieving-asset-events

This model allows you to select an NFT collection of your choice on Opensea and generate a forecast of future sales price (in Ethereum).

I used the Opensea API to create a dataset for several different NFT collections (Cool Cats, Gutter Cat Gang, and Pudgy Penguins) to explore, test, and compare time series model performance on.

I collected a minimum of 10,000 observations of sales transactions for each collection. I only selected collections that were found in Opensea's Top NFTs (By Volume) stats list, since our goal is to sell for a profit within a short time frame.

### Data Preparation

I used the Opensea API's "Events" collection to pull collection-specific sales transactions for various different NFTs. I then wrote functions to convert the dataframe index to a datetime index, and then another function to clean the dataset for easier EDA and engineer our target variable to be a readable Ethereum sale price. 

Data collection, preparation, engineering and modeling was performed on 3 different NFT collections to compare modeling results.

## Modeling

For each collection I run an auto-arima grid search to find the best parameters. We created a function to store the optimal parameters from the gridsearch, and another function that inputs our gridsearch variables into our model ready to make predictions.

## Results

Our model's forecasting performance on unseen data can be visualized below:

![GCG Model Forecast](images/modelforecastunseen.PNG)

Our final model has a RMSE of 0.93, compared to our baseline model RMSE score of 2.48.

Our forecast, though improvable, is looking promising. We can use this forecast to make assisted NFT purchasing decisions. The model results allows us to assess today's purchase price of our NFT asset of interest, and then forecast the valuation of that NFT asset in the future.

Let's demonstrate this concept in action. At the time of writing, on 12/2/2021, the Gutter Cat Gang floor is: 3.98 ETH. According to our model's forecast, the minimum valuation at the floor of Gutter Cat Gang is predicted to be worth more Ethereum than today's current floor price, at roughly 4.3 ETH. Based on these findings, we would recommend purchasing this asset for a profitable NFT swing trade.


