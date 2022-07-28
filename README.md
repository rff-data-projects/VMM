# Vehicle Market Model Overview

_By Joshua Linn, RFF Senior Fellow_

Source: [Balancing Equity and Effectiveness for Electric Vehicle Subsidies, RFF Working Paper 22-7](https://media.rff.org/documents/WP_22-7_January_2022.pdf)

## Model Summary

RFF maintains a model of the US market for new passenger vehicles and light trucks. Underpinning the model is a unique dataset of 1.5 million vehicle purchase decisions made by households during 2010-2018 and updated on a regular basis. These data include a detailed description of the vehicle purchased, other vehicles considered for purchase, and household demographics and economic characteristics.  Consumer preferences for vehicle attributes are estimated from the survey data. The model integrates household preferences for vehicle attributes with manufacturer decisions of vehicle technology and pricing and of entry of new electric vehicles. This model can simulate the economic and environmental impacts of policies that affect the new vehicle market.  Such policies include, but are not limited to, fuel economy and greenhouse gas standards, electric vehicle mandates and subsidies, electric vehicle charging infrastructure investments, gasoline and/or carbon taxes, and greenhouse gas cap and trade programs. Extensions of the model to the region and state level enable analysis of policies such as the zero-emissions vehicle mandate, regional carbon policies, state gasoline taxes, and electric vehicle subsidies (including charging infrastructure investments).

## Data and Summary Statistics

### Data

The subsection describes the construction of the main data set. The primary data source is the MaritzCX New Vehicle Customer Survey (NVCS). MaritzCX sends the survey to households that recently purchased new vehicles and sells the data to vehicle manufacturers, industry analysts, and researchers. Each year, MaritzCX collects about 200,000 responses (the response rate is about 9 percent). I use data from the 2010–2018 surveys, which include about 1.5 million responses representing about 1 percent of buyers.

Survey respondents report the transaction price of their vehicles, which excludes tradein value and includes taxes, along with identifying information about the vehicle, such as make, model, trim, drive type (such as front-wheel drive), and power train specifications (engine size, transmission type, and fuel type). Demographics include income, age, and zip code of residence. I define 20 demographic groups that include five income groups, two age groups, and two urbanization groups based on population density. I selected these demographics because they parsimoniously explain a large share of cross-household purchase variation. The cutoffs used to define the groups are selected so that each of the 20 groups has approximately the same number of NVCS observations.[^1]

The NVCS data have four distinguishing features: a) respondents provide information about the vehicles they purchased and their own demographics; b) the sample represents about 1 percent of all buyers; c) the data include vehicle transaction prices; and d) the data include highly detailed information about the vehicle purchased. The large sample size reduces measurement error for transaction prices and vehicle choices. Transaction prices
differ substantially from the manufacturer’s suggested retail price (MSRP), and using these rather than MSRP yields more economically plausible and precisely estimated parameter values.

The transaction prices are particularly important for estimating WTP for vehicle attributes. Transaction prices respond to short-term market conditions such as surprises in gasoline prices, whereas manufacturers choose MSRP once each year; using MSRP can lead to biased estimates for WTP (Langer and Miller, 2013).

The detailed vehicle information allows me to define about 1,200 unique vehicles each year, which is several times larger than the number of unique choices that can be found in most previous studies. The vehicle aggregation corresponds closely to the choice set that consumers face (just as in the literature, I do not have sufficient data to construct individual-specific choice sets). For example, the data distinguish all-wheel drive and
front-wheel drive versions and between the base and sport trims of a model. The vehicle disaggregation also aids the demand estimation (see Estimation section).

I supplement the MaritzCX data with data from IHS and the Consumer Expenditure Survey (CEX) to obtain a regionally representative sample of households. A vehicle is defined by a unique model year, make, model, trim, fuel type, drive type, body style, and engine displacement. For example, a unique vehicle in the data is the 2018 Volkswagen Jetta SE sedan with a 1.4 liter gasoline engine and front-wheel drive. I match the MaritzCX data with IHS data on new registrations by vehicle, region, and year. From the CEX, I compute the numbers of new and used vehicles purchased by year, quarter, and demographic group. The appendix explains the procedure for using the IHS and CEX data to weight MaritzCX observations and match the distributions of new registrations across vehicles, regions, and demographic groups.

I obtain vehicle attributes from Wards and EPA, which I merge to the Maritz data by vehicle and year. The Wards and EPA data include transaction price, fuel economy, electricity consumption per mile, horsepower, weight, wheelbase, width, and MSRP.[^2] I aggregate the household data by vehicle, region, demographic group, and year using the weights constructed from IHS and CEX. I also collect counts of public electric charging stations from the Alternative Fuels Data Center.

Vehicle and fuel prices are converted to 2018 dollars using the BLS Consumer Price Index. The final data set consists of vehicle prices and attributes for each demographic group (20 groups), vehicle (about 1,200 unique vehicles each year), region (California, other ZEV states, and non-ZEV states), and year (2010–2018). I supplement the data with plug-ins that have entered the market since 2018 and vehicles that manufacturers intend to introduce by 2023. For those that have already entered, I collect vehicle attributes from the same data sources as in the MaritzCX data. For vehicles that have not yet entered, I collect data from public announcements by the corresponding manufacturers. For missing values, I impute values using averages across entrants with nonmissing data.

### Summary Statistics

This subsection reports summary statistics of the main data used for the computational model estimation and simulations and some background on plug-in sales over time and across demographic groups. In Table 1, observations are by vehicle, demographic group, region, and year, and the sample shows extensive variation in vehicle attributes. 

#### Table 1: Summary Statistics for Demand Data Set (2010–2018)
|     | Mean | Standard Deviation | 10th Percentile | 90th Percentile |
| --- | --- | --- | --- | --- |
| Transaction price (2018$, including subsidies) | 34,411 | 12,518 | 21,924 | 49,434 |
| Fuel costs (2018$) per mile | 0.111 | 0.027 | 0.080 | 0.144 |
| Log (horsepower/weight) | -2.82 | 0.21 | -3.07 | -2.57 |
| Footprint (sq feet) | 49.9 | 6.7 | 43.9 | 60.2 |
| Hybrid vehicle market share | 0.021 | | | |
| Plug-in hybrid vehicle market | 0.007 | | | |
| Electric vehicle market share | 0.014 | | | |
_Note: Observations are weighted by sales. The data include 647,440 observations._

The figure below illustrates the variation of vehicle attributes across income groups. 

#### Figure: Mean Transaction Price, Fuel Economy, Horsepower, and Light Truck Share by Income
Group
![Figure showing Mean Transaction Price, Fuel Economy, Horsepower, and Light Truck Share by Income
Group](https://github.com/rff-data-projects/VMM/blob/cbf31cc16d3f20427040c01d7401cd90bc3a0d5b/Screen%20Shot%202022-07-28%20at%2010.12.49%20AM.png)

_Note: For each income group, panels A through C show the sales-weighted mean of the attribute indicated
in the panel title. Panel D shows the share of light trucks in total sales. The sample includes observations
from 2010 through 2018._

Individuals belonging to the highest-income group purchase vehicles with average prices about 60 percent higher than those in the lowest group. Average fuel economy is about 10 percent higher for the lowest- than the highest-income group. Horsepower and the share of light trucks in total purchases increase with income. Such extensive variation in vehicle attributes across income groups motivates the structure of the demand model, which allows preferences for vehicle attributes to vary across demographic groups. 

The figure below shows market shares of hybrids, plug-in hybrids, and EVs by year. Hybrids represent about 3 percent of sales through 2014 and decline to about 2 percent by 2018. Plug-in and EV shares increase steadily and at about the same rate as one another between 2010 and 2017. In 2018, the EV share increases relative to the plug-in hybrid share, which is largely due to the entry of the Tesla Model 3.

#### Market Shares of Hybrids, Plug-in Hybrids, and Electric Vehicles by Year
![Figure: Market Shares of Hybrids, Plug-in Hybrids, and Electric Vehicles by Year](https://github.com/rff-data-projects/VMM/blob/f646e1061145f95dda465499ac8642285f5f5731/Screen%20Shot%202022-07-28%20at%2010.16.39%20AM.png)

The next two figures show variation of plug-in purchasing patterns across income groups. The lowest-income group is substantially more likely to purchase a hybrid. In contrast, the probability of purchasing a plug-in hybrid or EV increases by income. A possible interpretation of this pattern is that many hybrid buyers are interested in the fuel cost savings, whereas the plug-in buyers are interested in the new technology. The figure indicates one of the challenges of the demand estimation, which is to disentangle consumer demand for fuel cost savings from demand for the technology per se; for example, plug-in technology could be a status symbol, and some consumers may like being early adopters.

#### 2018 Market Shares of Hybrids, Plug-in Hybrids, and Electric Vehicles by Income Group
![Figure: 2018 Market Shares of Hybrids, Plug-in Hybrids, and Electric Vehicles by Income Group](https://github.com/rff-data-projects/VMM/blob/4ba21206c3c22ab94088449682bd3087a5df2f3f/Screen%20Shot%202022-07-28%20at%2010.19.32%20AM.png)

The next figure shows that hybrids and plug-in hybrids have lower transaction prices than EVs on average. For context, the average transaction price across all vehicles is about $35,000, indicating that EVs are substantially more expensive than the average, whereas hybrid and plug-in hybrid vehicles are below average. Battery costs partly explain the higher prices of EVs, as they have larger battery packs. Another factor is that many EV models compete
with luxury rather than midlevel vehicles and offer features common in luxury vehicles such as advanced safety technologies and automated driving features.

#### Transaction Prices of Hybrids, Plug-in Hybrids, and Electric Vehicles by Income Group
![Figure showing transaction Prices of Hybrids, Plug-in Hybrids, and Electric Vehicles by Income Group](https://github.com/rff-data-projects/VMM/blob/c2dba88f39d715b835e264c0e0c94041d79b6053/Screen%20Shot%202022-07-28%20at%2010.20.44%20AM.png)

Whereas the previous figures showed variation in vehicle attributes across fuel types, the next figure shows variation in hybrid and plug-in market shares across regions. The market shares of plug-ins and EVs are about 10 times higher in California than in non-ZEV states. The ZEV program may explain this difference, but the figure indicates that consumer preferences also play a role. The ZEV program does not incentivize hybrid sales, and yet
the share of hybrids in California is higher than in non-ZEV states. Moreover, although the ZEV programs provides the same incentives for ZEV sales in California and the other ZEV states, market shares of plug-ins are still higher in California.

#### 2018 Market Shares of Hybrids, Plug-in Hybrids, and Electric Vehicles by Region
![Figure showing 2018 Market Shares of Hybrids, Plug-in Hybrids, and Electric Vehicles by Region](https://github.com/rff-data-projects/VMM/blob/0e44932bd8fdf32a8c50c346f02fa64aa48cd240/Screen%20Shot%202022-07-28%20at%2010.23.11%20AM.png)
_Notes: The figure shows the 2018 market shares of hybrid, plug-in hybrid, and electric vehicles for the
indicated region. Other zero-emission vehicle (ZEV) states are Connecticut, Delaware, Maine, Maryland,
Massachusetts, New Jersey, New York, Oregon, Pennsylvania, Rhode Island, Vermont, and Washington._

The next figure shows the increasing supply of plug-ins over time. The numbers of available plug-in hybrids and EVs increased steadily (some plug-in hybrids have exited, such as the RAV4). By 2018, the number of plug-ins was similar to that of hybrids. The number of available hybrids peaked in 2013 and declined gradually through 2018. This pattern could be explained by declining gasoline prices after 2014 (not shown) and competition between
hybrids and plug-ins.

#### Number of Available Hybrids, Plug-in Hybrids, and Electric Vehicles by Year
![Figure showing Number of Available Hybrids, Plug-in Hybrids, and Electric Vehicles by Year](https://github.com/rff-data-projects/VMM/blob/faffec372b39ce755ad3054cea4c881f8c06ae10/Screen%20Shot%202022-07-28%20at%2010.23.54%20AM.png)

## Equilibrium Model

See section 4, 'Equilibrium Model' in [Balancing Equity and Effectiveness for Electric Vehicle Subsidies, RFF Working Paper 22-7](https://media.rff.org/documents/WP_22-7_January_2022.pdf)

## Estimation

See section 5, 'Estimation' in [Balancing Equity and Effectiveness for Electric Vehicle Subsidies, RFF Working Paper 22-7](https://media.rff.org/documents/WP_22-7_January_2022.pdf)

## End Notes
[^1]: I use the Consumer Expenditure Survey (CEX) to weight NCVS observations to account for nonuniform
response rates across demographic groups. Because of the CEX sample size, it is not possible to construct
more than about 20 demographic groups. The 20 groups that include income, age, and urbanization explain
a larger share of variation in vehicle attributes across households than other possible definitions.
[^2]: For the small number of missing values for vehicle attributes, values are imputed using data from
Cars.com.
