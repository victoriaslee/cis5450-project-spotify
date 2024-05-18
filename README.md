# cis5450-project-spotify
Final project for CIS 5450: Big Data Analysis focusing on analysis of two Kaggle Spotify datasets 

# Group members: Victoria Lee and Clarice Wang

# Introduction
Many artists use Spotify streaming and charting as a major metric of successs. Our goal is to analyze the following two Kaggle datasets on the topic: 
https://www.kaggle.com/datasets/maharshipandya/-spotify-tracks-dataset/data
https://www.kaggle.com/datasets/yelexa/spotify200

The first set consists of 114k unique songs up to 2021 with columns regarding song information, such as artist and genre, as well as Spotify API characteristics, such as popularity and danceability. The second set consists of ~30k unique songs from a similar time period, all of which charted on some type of Spotify chart in any region across the globe. It contains all the columns in the first dataset except popularity as well as additional columns such as streams, rank, region, and chart. 

We first perfomed linear regression modeling on each dataset, predicting for popularity in the first, and streams in the second, noting the most impactful features after hyperparameter tuning. Then, we left merged the datasets on track_id, and created an additional binary column indicating whether the song charted or not, defined by its presence in the second dataset. We then performed classification on this dataset to predict which songs would chart. 

# Conclusions
For both linear regression models, our best results were achieved with Gradient Boosting Regression, with better performance occurring in the first dataset. A major consideration is that the Spotify API features are already engineered based off of raw characteristics such as streams, so it may be easier to predict for an arbitrary feature of popularity compared to the raw streams feature used in the second dataset. We didn't see strong underfitting or overfitting in either dataset after hyperparameter tuning, which minimized the MSE as well as improved the r^2, however we did note the absence of a strongly influential feature. For the classification models, Gradient Boosted Trees also were the most successful model, performing much better than Random Forest classification with our target variable of accuracy. Due to imbalance in the target variable, as well as high complexity, the recall was quite low in every model, but hyperparameter tuning successfully improved precision. In addition to high complexity, the overlap in the two datasets is only about ~3k, so better results may be seen with more values to allow for better tuning to features. Future modeling could consider implementing stacking or neural networks and using cross-validation or Bayesian optimization. In terms of considerations for the music industry, features such as number of tracks per album, loudness, and instrumentalness could be considered when aiming for a greater number of streams. For a more detailed analysis, check out the notebook!
