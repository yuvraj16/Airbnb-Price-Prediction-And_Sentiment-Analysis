# Airbnb_NYC_Data_Analysis


## Problem Statement

Airbnb is an online marketplace that lets people rent out their properties to the guests. Users can use the Airbnb website to look for listings posted in the area which they are visiting. There are plenty of criteria to list for or search from a shared room to an entire house ranging from having luxurious amenities like swimming pool, parking to basic amenities such as no. of beds, kitchenware. New York City has been one of the hottest markets for Airbnb, with over 52,000 listings as of November 2018. This means there are over 40 homes being rented out per square km. in NYC on Airbnb! One can perhaps attribute the success of Airbnb in NYC to the high rates charged by the hotels, which are primarily driven by the exorbitant rental prices in the city.
The business problems we tried to solve as part of this project-
  - Predicting the listing price of particular house based on attributes of the listing
  - Perform Sentiment Analysis of Customer reviews of each listing on Airbnb

### Data Description

Source:
http://insideairbnb.com/get-the-data.html

#### Why this Dataset:
- The total data size of 550 MB was ideal to implement Big-Data tools and techniques
- It’s a classic dataset to explore and expand our feature engineering skills and day to day understanding from multiple reviews of the listings
- Working on such a huge dataset helped us to learn new things in pyspark

### Techniques

#### Price Prediction using Regression

- Data manipulation
On AirBnB listing data downloaded from the source, we analyzed 106 features for 49,748 listing ids. Out of which we removed null values and the columns containing textual information. 
- Feature Engineering
We separated all the integer features from the feature set to be fed into the model directly. On the categorical columns, we first numerically encoded them using StringIndexer and then applied One hot encoding. To perform these operations, we imported StringIndexer, OneHotEncoder, VectorAssembler from pyspark.ml.feature library. We implemented randomForest on the numerically encoded set and original numeric features and selected top 10 variables using the variable importance score given by randomForest. We split the data in the ration of 70-30 for train and test.

#### Sentiment Analysis using reviews classification

Sentiment Analysis using reviews classification

- #### Data manipulation
We analyzed 552,664 reviews in the dataset downloaded from AirBnb. Out of which we selected 50% for train and 50% for test. Only two columns – ‘id’ and ‘customer reviews’(comments) were useful in the reviews dataset for sentiment analysis. On customer reviews column, we performed cleaning operations such as blank string removal, punctuation removal, stop words removal, alpha numeric words removal, etc. We also performed lemmatization on the cleaned column.
- #### Feature engineering  
After performing lemmatization, we identified the polarity of the sentence using TextBlob. After this we obtained a score against each of the reviews. Using this score we obtained a label for our dataset. All the reviews which had a score greater than 0.1, was tagged as positive and the reviews which had a score less than zero, were tagged as negative. We eliminated neutral sentences (with a score of 0 and 0.1) from further steps. Post this on the review column, we implemented tokenization and tf-tdf approach to create vectors for each of the words. And built a classification model on the train data. Below is the attachment of EDA that we performed in Tableau on reviews data.

### Results 

![price_prediction_results](https://github.com/singhankit16/Airbnb_NYC_Data_Analysis/blob/master/Price_prediction_results.PNG)
![sentiment_analysis_results](https://github.com/singhankit16/Airbnb_NYC_Data_Analysis/blob/master/Price_prediction_results.PNG)
