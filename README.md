# triple_ten_final
Identify clients at risk of churn for a telecommunication company. There's 4 csv files about their customers, and the services they use from InterConnect. Forecast churn for customers of InterConnect, specifically our goal is to pinpoint which clients are most likely to leave, allowing them to intervene with targeted promotions to retain business


For this churn problem, I began with raw data, that was decently clean to begin with. The project began with merging the four dataframes on customerID. As I moved through the features, I cleaned while exploring. There were still missing values, some naming conventions to correct, columns needed to be encoded for modeling, true false converted into binary, and handled outliers.

The investigation included visualizing the data in segments. These segments might have been grouped data sharing numerical data in charts, distributions of data, and using multi-variant comparisons. During the investigation it was discovered that churn had surpassed signups. We also generated new features through feature engineering.

Once the data had been cleaned, some prepro

cessing was conducted to further prepare the data for classification modeling, including spliting the data into train, valid, and test sets. We decided to go with a couple different models. Logistic Regression for a linear style model, good for looking at how/ why the model is making its determinations. Random Forest for a touch more complicated approach and lastly XGBoost for a more complicated model.

After the initial run of the models, we got rather good results. Random Forest was the worst so I skipped that model at this point. Logistic Regression was used to explore feature importance and XGBoost performed the best. We then tuned XGBoost using randomized gridsearch cv. The results hardly improved, but we now had our optimal perimeters and tested our models abilities on the test set. AUC-ROC was 0.89, precision was 0.72 and recall 0.68. Next we explored how could we optimize recall? The penalty for losing a customer out weighes the cost of offering an unnecessary discount, so increasing the recall of the model is imperitive. InterConnect would hopefully provide more information on how they evaluate lifetime customer value. From there an ideal threshold for classification can be calculated, with the goal of increasing revenue the most or decreasing losses the most.

We did not look at feature importance for XGBoost due to the IDE not having SHAP installed. We are not allowed to install packages in this course IDE.

The most difficult part of this project was definitely model training time. Kernels were crashing. Ultimately I discovered that the model ran best in parallel, like way better. 2-3 hours down to 30mins. Another difficult part was my mac screen cracked on me, and I had to finish this on a new computer.

Every step is key in a way. Ultimately I believe the data was cleaned very well. I believe this because of the performance of Logistic Regression. EDA, even though it wasn't able to give predictions like modeling it still provided actionable ideas. Feature importance from looking at logisitic regression only confirmed what we saw earlier in EDA.