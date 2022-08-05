### Problem Statement

I am a data scientist that wants to help people that come from other countries to the U.S. to better communicate with colleagues in work chats, emails and texts. One way to do this is throug sports. Sports is a subject that many colleagues talk about and it could help new workers make connections with their colleagues. Workers from other countries might not know NBA and NFL very well, which are two of the most popular sports in the U.S. I plan to create a model that can predict if messages are talking about the NBA or NFL. I will be taking reddit posts from r/nba and r/nfl to create a model that can predict this accurately. This model might not help people know more about each sport, but it will help them from accidentally making a mistake about what sport their colleagues are talking about.

### Data Dictionary

|Feature|Type|Dataset|Description|
|---|---|---|---|
|subreddit|object|nba_nfl_modelling_data|The values are either nba or nfl, the two subreddits the data was scraped from.| 
|title|object|nba_nfl_modelling_data|The title of posts that came from the nba and nfl subreddits.| 


The data-set has two columns that are connected to eachother. The title column is the title of posts that were scraped from reddit and the subreddit column are the subreddits that data was scraped from which were either nba or nfl. 

### Analysis Summary

Analyzing the data gave me an understanding on what parts of the data can be useful to help create a model that can predict what subreddit a post came from. When looking at data the first important part is the column that would be the y-variable, which is what the model has to predict. This was the subreddit column that contained the subreddits nba and nfl. The second is what columns should be used for the X-variable. The two best choices would be title and selftext. The problem with selftext is that most selftexts in the nfl reddit are either pictures or videos which would not be able to be used. Because of this reason I dropped the selftext columns and just used the title column for my X-variable.

I created a subreddit_word_count column to look at the number of words in each title. I then used group by to find the average number of words in nba titles and nfl titles. nfl titles on average contained 17.1 words, while nba titles on average contained 14.6 words. nfl titles on average had 2.5 more words than nba. I then did train-test-split with X = Title and y = subreddit. I then used CountVectorizer to create a dataframe of words used in the data's title. I then analyzed the dataframe finding the top 25 words found and looked at CountVectorizer stop_words.

I then created three different models with their purpose being able to use the words in title to predict if it came from the nba subreddit or the nfl subreddit. I used a pipeline to use CountVectorizer with each classifier. The three classifiers used were MultinomialNB, KNeighbors Classifier, and Logistic Regression. I analyzed the models and saw how well they did by printing out best parameters, best score, training scores, testing scores, cross val scores, and the specificity, which tells us how well a model can predict true negatives. I then used those scores to find which model did the best at predicting the subreddits titles came from. 

### Conclusions/Recommendations

The classifier that did the best with Count Vectorizer was Logistic Regression. This model had the highest best score, training scores, testing scores, cross val scores, and specificity. There were two Logistic Regression models that did well, one had a higher testing score, while the other had more parameters,higher best score, training score and cross val score. For this reason I chose the latter because the difference in testing scores was only .004. Also because cross val score is better at evaluating models. This model can be used to predict if messages are talking about the NBA or NFL. In the future it would be good to delve deeper into the parameters of classifiers to improve the predicting ability of the model as well as create a model that not only predicts if a message is about the NBA or NFL, but can help craft a message that could be a response to the one recieved.