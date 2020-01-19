# Implicit Recommendation System for Meetup.com 
![meetup](https://user-images.githubusercontent.com/44115595/72675526-0ccde600-3a4b-11ea-990f-7689736ddc16.PNG)

### Introduction
With increased popularity and growth in event-based online services like [Meetup](https://www.meetup.com/), it has also become difficult for users to find the events that match their interests. Building a strong recommendation engine would be the natural answer to this problem. However, this is different from the classic recommendation scenarios (music, movies etc.) where there are explicit ratings for the items to be recommended. In this case, the events or groups to be recommended cannot be rated before it has occured, so we use certain implicit feedback data as a proxy for the users' intention or propensity towards a certain event/group.

In this project, we collected data using the [Meetup API](https://www.meetup.com/meetup_api/) for the groups, events and members in the Austin, TX area. We use two different kinds of implicit feedback data - RSVPs and TimeDelta to build and analyze the performance and limitations of several well known recommendation algorithms. Finally, we tie this together with how Meetup can generate more revenue through user engagement which is facilitated by recommending personalized groups and events to the members. 

### Technology
The project was implemented in Python 3.7.3 and PySpark.

#### Packages
* meetup.api
* implicit
* pyspark.mllib.recommendation

### Approach
1. Extracted JSON objects of groups, events, members and RSVP counts for Austin, TX area from the Meetup API
2. Data Pre-processing to generate two different implicit feedbacks:
    * RSVP count - For each user and group, the normalized ratio between the number of events that a user has RSVP'd for in each group and the total number of events organized by the group.
    * TimeDelta - Refers to the difference in months between the lats time that the user attended an event in a group and the first time the user joined the group (indicative of a prolonged interest in the group)
3. Built the basic memory-based collaborative filtering and content-based recommender systems.
4. Hyperparameter tuning for the ALS matrix factorization to find the optimal number of latent factors using PySpark on Databricks
5. Built and evaluated(using RMSE) ALS and Logistic Matrix factorization models

### General Summary

### Insights and Recommendations
