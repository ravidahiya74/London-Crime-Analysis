# Module 3 Project: London crime analysis

### Team members:

**Khairul Omar & Ravi Dahiya**<br>
DS111819

### Executive summary:

We looked at a 3-year UK Police database on street crime and stop & search conducted by the police within a 1-mile radius around Moorgate, London between Dec 2016 and Nov 2019. We are taking the position of an independent data analyst to conduct a study on behalf of a neighbourhood newspaper on several aspects of crime rate in the area.
<br><br>
Some of our investigative questions are based on other UK-wide studies and news reports, but we want to want to dig deeper if the same findings are also true for the area around Moorgate. Upon analysing the dataset, we proceeded with addressing the following questions:
<br><br>
1. From the data, there appears to be a higher level of crime in the later half of the year compared to the first half. Are the differences in crime level by month statistically significant and what may be the drivers behind them?
<br><br>
2. Conviction rate for a crime is a matter of public concern as it can shape public perception on the effectiveness of the police force. Our data seems to suggest that the suspect for serious crimes around Moorgate is less likely to be identified than others, but is this true?
<br><br>
3. There has been independent reports that ethnic minorities are generally more likely to be stopped and searched compared to the general population. Would our data around Moorgate come up with the same conclusion?

### Methodology

1. **Data import and data cleansing**  
    - Download street crime and stop & search data from UK Police API interface and store them locally.
    - Explore raw data and perform data cleansing tasks.
<br><br>
2. **EDA & subsetting for hypothesis**  
    - Combine categorical information into larger groups: this was carried out for ethnicity information.
    - Assign weights to categorical data for more meaningful analysis: this was carried out for crime category using crime severity indices published by ONS.
    - Study the variation of crime level by month and possible drivers behind them, assisted by a line plot on the number of cases and the severity of cases.
    - Study the status of crime investigations to see how many cases were not resolved via a bar plot.
    - Study the breakdown of stop and search by ethnicity via a bar plot to see if the pattern is similar to what is claimed by the media.
<br><br>
3. **Hypothesis tests**
    - Formulate null and alternative hypotheses to be tested.
    - Select the appropriate statistical test for each hypothesis based on the availability and type of data in hand.
    - Prepare data subsets to be fed into statistical package.
    - Obtain additional data on population expected value: we used 2011 National Census for population breakdown by ethnicity.
    - Calculate p-value using scipy.stats package.
    - Using 95% confidence level, reject null hypothesis when p-value is lower than 0.05 for a one-side test.

### Key findings and conclusions:

1. **There is no conclusive seasonality effect between crime level and month**  
    - Our study defines crime level as the total number of crimes weighted by their severity index. Using several definitions of seasons in categorizing the months (i.e. cold/mild/warm, the four seasons, and holiday months vs. regular months) we could not find conclusive evidence that the crime rate is affected by any of these factors using one-way ANOVA test.
<br><br>
2. **Suspect for serious crimes is less likely to be identified than lesser crimes**   
    - Serious crimes are defined based on the severity index published ONS, which includes violent crimes, robbery, burgularly and arson. Using Chi-square test with equally likely outcome, we found that proportion of cases where a suspect is not found for serious crimes is statistically higher than lesser crimes.
<br><br>
3. **Ethnic minorities are more likely to be stopped and searched**  
    - Our data and tests support the claims made in the media that ethnic minorities are more likely to be stopped and searched on the street. For this hypothesis, we used Chi-square test where the expected outcome is based on UK census data for the demographic breakdown. We repeated the test using self-declared ethnicity and derived a similar conclusion.