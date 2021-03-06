## Introduction

The internet as we know it was introduced all the way back in 1983 but it wasn’t until 1994 that a company known as NetMarket first started selling internet services. And since then, the satellite service providing industry has increased exponentially. Every company aims to provide the best network conditions to customers in an industry where quality is so important. And that is specifically where improvements can always be made. Being able to detect network issues and monitor network performance for issues is so important in the real world for positive customer experience and that is the problem we home to tackle with our project. At the end of the day, the customer makes the business and increasing customer satisfaction is always a priority in successful business. 

Before going into the specifics about the approach to tackling this problem, it is important to understand a few key technical terms. The two biggest network conditions that we are targeting with this project are latency and packet loss. Packet loss refers to the loss in packets of data when these packets of data don’t reach the destination. This will be represented as a ratio in our project. The packet loss ratio is the number of packets lost divided by the total number of packets since the last lost one (1/2000 refers to 1 packet lost out of 2000 packets). Latency on the other hand, refers to delays in the network that are observed from a cause and effect of some physical change in the system. This will be represented in our data as an integer. Being able to successfully predict these could be instrumental for Viasat as this will allow service providers to better monitor network performance and identify issues.

### Motivating Problem

The motivating problem is that predicting latency and packet loss can be extremely beneficial from a network providers perspective as they aim to give out the best service possible. This information is vital in the monitoring of network conditions to ensure the quality of the product. Being able to predict these issues based on machine learning models before they happen will drastically improve the internet experience for hundred of thousands of customers.

### Why should you care?

As a customer, this type of analysis is so important when choosing the right internet provider. Machine learning has become the future of the industry and using it to further improve customer experience is a real plus. The benefits of this research are profound and can truly revolutionize the industry. Being able to predict when packets may be lost or when latency issues will occur from a internet provider's perspective can be beneficial as they monitor their networks. They could then reroute traffic or use other creative ideas to solve these issues and improve the overall experience for customers.

## Methods & Approach

The models (Linear Regression, Bayesian Ridge Regression, Support Vector Regression, and KNN Regression) that we built this quarter to predict latency and patent loss rely heavily on a tool called DANE. DANE is a dataset generation tool that creates artificial and deterministic network data under configurable network conditions. DANE produces separate data files for each latency/loss configuration. Before training our models, we will combine these datasets into a single dataset and label each row with their corresponding latency and loss ratio. We will then use this resulting dataset to train, test, and validate our models. When building our models, we will split our data into the following ratios: 80% to train, 10% to test, and another 10% to validate.

We engineered 11 features to train our models: the maximum packet size for each interaction, range of packet sizes, average packet size, average packet duration, total number of directions, total packets, total bytes, interaction length, packets to duration ratio, and bytes to duration ratio.

## Results

### Key Figures

This section displays the values for many of the features used, as well as how these values change across different packet loss ratioes and latencies. 

The graphs below show the average packet size sent in bytes in each interaction over different packet loss ratioes and latencies, respectively.  
![image](https://user-images.githubusercontent.com/43732347/156982499-e7b05a5f-d0fd-4f27-bfd7-98c842b5ec38.png) 
![image](https://user-images.githubusercontent.com/43732347/156982524-4d66fbd9-ca16-4225-b6bd-6096da2bceee.png)  

The graphs below are formatted the same way, but they show the total number of packets sent in each interaction.  
![image](https://user-images.githubusercontent.com/43732347/156983311-995f88bb-422c-463d-9936-9dbfe2567fac.png) 
![image](https://user-images.githubusercontent.com/43732347/156983329-a8af73ad-94da-43a6-ad61-cf540c1ea92d.png)  

The following graphs look very similar to the previous ones. This is because they show total bytes sent, which is closely related to total packets sent.  
![image](https://user-images.githubusercontent.com/43732347/156983444-1530c624-174c-4c7e-8c17-680496aae748.png) 
![image](https://user-images.githubusercontent.com/43732347/156983462-b77ff683-a4df-4b31-b60d-1fb868f65d39.png)  

The next set of graphs display the length of each interaction in milliseconds.  
![image](https://user-images.githubusercontent.com/43732347/156983546-9c346158-b17c-4a80-8cff-7fb2b795cb9f.png) 
![image](https://user-images.githubusercontent.com/43732347/156983562-a6f11b03-aa91-435e-9c02-fd41a354eee4.png)  

The following sets of graphs are based on the previous ones. These show the number of packets sent divided by the interaction length. This provides an idea of the rate at which packets are being sent.  
![image](https://user-images.githubusercontent.com/43732347/156983745-7ca462e5-d684-47b8-bdba-b61567f2bc5f.png) 
![image](https://user-images.githubusercontent.com/43732347/156983761-4a2ace78-0c18-4750-967c-b6d95cac9b41.png)  

The final two graphs are similar to the previous two, but they show the rate of bytes being sent instead of packets.  
![image](https://user-images.githubusercontent.com/43732347/156983835-b705362e-2f02-4950-8a3c-a2cb7de61e9e.png) 
![image](https://user-images.githubusercontent.com/43732347/156983848-2924ba38-f557-43e3-b7d8-1b17236823b3.png)  


### Analysis

Packet Loss Predictions
 
|Model|Mean Squared Error|Coefficient of Determination|
| :----: | :----: | :----: |
|Linear Regression|3.01 * 10^-7|0.181|
|Ridge Regression|3.05 * 10^-7|0.183|
|Decision Trees|1.92 * 10^-7|0.940|
|Support Vector Regression|3.52 * 10^-7|0.675|
|KNN Regression|2.89 * 10^-7|0.204|
|KNN Classification|4.58 * 10^-7|-0.219|

 
The table above represents the results of our 6 models on predicting packet loss ratios. Hyperparameters were tuned for all models to ensure the best performance and the mean squared errors were compared between them. As seen in the table, the Decision Trees model performed best in terms of lowest mean squared error and highest coefficient of determination. Although the mean square error is fairly similar and significantly small across all models, the high r-squared value makes it clear that Decision Trees is the best model to use when predicting packet loss. 

 
Latency Predictions
 
|Model|Mean Squared Error|Coefficient of Determination|
| :----: | :----: | :----: |
|Linear Regression|8.07 * 10^4|0.886|
|Ridge Regression|8.14 * 10^4|0.885|
|Decision Trees|0.0|1.0|
|Support Vector Regression|5.66 * 10^4|0.777|
|KNN Regression|1.83 * 10^5|0.740|
|KNN Classification|2.18 * 10^4|0.693|

 
Similarly, the results from the latency predictions show that the Decision Trees model was also the best performing model in terms of mean squared error and correlation. A mean square	error of 0 and correlation coefficient of 1 seems too good to be true. Although we did not get the chance to further investigate this outcome, we will make sure to validate this outcome in the future. Until then, we want to offer the KNN Classification model as the best predictor for latency as it has the smallest mean squared error compared to the other models.


### Future Impact

In terms of future impact, we believe this sort of analysis will be instrumental in the future of the industry. Using models to predict network conditions based on real-world data will have huge positives and the beauty of this process is that as more and more data gets fed into the model, the more accurate it becomes. It is an ever evolving study that will only get better with time and we feel like it can have a huge impact on the satisfaction of customers if coupled with some sort of monitoring API.
