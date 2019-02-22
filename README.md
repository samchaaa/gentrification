# gentrification

Data Sources:

SPD Reports (Kaggle, data.seattle.gov)
~684,000 entries, from 1965-2016
Feature used: Reports of theft (not including car prowls). Thefts were the second highest type of report, beside car prowls. Car prowls were not included because people often report them out of obligation for insurance purposes.
https://www.kaggle.com/sam/seattle-crime#SPD_Reports.csv

Seattle Land Use Permits (Kaggle, City of Seattle Open Data)
~14,000 entries, from 1992-2018
Features used: Commerical and Multifamily land use permit applications.
https://www.kaggle.com/city-of-seattle/seattle-land-use-permits

Seattle Police Department 911 Incidents Response (Kaggle, City of Seattle)
~1,430,000 entries, from 2009-2018
Feature used: Suspicious person reports. We speculated suspicious person reports would increase with gentrification (aka the Barbeque Becky Index).
https://www.kaggle.com/sohier/seattle-police-department-911-incident-response

Seattle Code Violation Cases (Kaggle, City of Seattle Open Data)
~41,000 entries, from 2003-2018
Feature used: Tenant Reloction Ordinance records, indicating where low-income tenants forced to relocate due to buildings being torn down or renovated.
https://www.kaggle.com/city-of-seattle/seattle-code-violation-cases

House Sales in King County, USA (Kaggle, Public Domain)
~21,000 entries, from 2014 - 2015
Feature used: House sales, weighted by price.
https://www.kaggle.com/harlfoxem/housesalesprediction

All datasets included latitude and longitude.

Process:

For each feature, data was clustered by latitude and longitude.

Clustering used DBSCAN (Density-Based Spatial Clustering of Applications with Noise) with ball tree algorithm and haversine metric.

Note using latitude and longitude is troublesome as the relationship between distance and degrees varies between the equator and the poles. We were not concerned with this issue because we were only dealing with a very local area.

The resulting cluster midpoints were assigned a weight (count of data in cluster/total number of instances in the dataset).

The resulting lat/long pairs with weights (for each feature) were then again clustered, returning one set of lat/long pairs with weights generalizing all our features.
