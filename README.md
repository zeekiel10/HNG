#🗳️ Outlier Detection in Ebonyi Election Data#
📖 Project Overview

This project analyzes polling unit results from Ebonyi State, Nigeria to detect unusual voting patterns (outliers). By combining geolocation, clustering, and statistical checks, we identify polling units whose results differ significantly from their neighbors.

The goal: spot potential anomalies in election data that may require further investigation.

**🗂️ Data Sources**
Ebonyi_crosschecked.csv: Raw election results per polling unit (PU).

Columns include:

State, LGA, Ward, PU-Code, PU-Name

Voter counts (Accredited_Voters, Registered_Voters)

Party results (APC, LP, PDP, NNPP)

Metadata about result sheets.

****🔧 Steps Taken**

1. Data Preparation
Loaded the CSV file into Pandas.

Created a full address string for each polling unit (PU-Name + Ward + LGA + State).

Used the OpenCage Geocoding API to get latitude and longitude for each PU.

Saved the enriched dataset to Ebonyi_data.csv.

**🔧 Steps Taken**

**1. Data Preparation**
Loaded the CSV file into Pandas.

Created a full address string for each polling unit (PU-Name + Ward + LGA + State).

Used the OpenCage Geocoding API to get latitude and longitude for each PU.

Saved the enriched dataset to Ebonyi_data.csv.

**2. Cleaning & Subsetting**
Dropped unnecessary columns (e.g., result file links, cluster IDs).

Focused on essential fields: location + party votes.

Exported cleaned data to Excel for easy reviewng
Dropped unnecessary columns (e.g., result file links, cluster IDs).

Focused on essential fields: location + party votes.

Exported cleaned data to Excel for easy review.

**3. Neighbor Detection*
Defined a radius of 1 km around each polling unit.

For each PU, found neighboring PUs within that radius using geodesic distance.

This allowed comparison of voting patterns among geographically close polling units.

###4. Outlier Score Calculation
For each polling unit:

Compared its party vote counts (APC, LP, PDP, NNPP) against the average of its neighbors.

Calculated the absolute difference = outlier score.

Higher scores = more unusual compared to nearby polling units.

###5. Visualization
Created boxplots for each party’s outlier scores using Seaborn.

Saved plots as election_outliers.png.

These charts show the spread of anomalies across the state.

###6. Top Outliers
Identified the Top 3 polling units with the highest outlier scores for each party:

APC: EDUKWU OFEREKPE, EDUKWU EDO PRIMARY SCHOOL, NDIOCHIMBA VILLAGE HALL

PDP: AMAIGBO TOWN HALL, NGAMGBO OGELE, EDUKWIACHI TOWN HALL

LP: STADIUM COVER, EBSU PRESCO CAMPUS, OKPOSI STREET NURSERY II

NNPP: AMAIGBO TOWN HALL, NGAMGBO OGELE, EDUKWIACHI TOWN HALL

These units had vote counts that stood out sharply compared to their neighbors.

##📊 Key Insights
Outlier detection helps flag suspicious or unusual results.

Some polling units show extreme deviations in party votes compared to nearby units.

This does not prove fraud, but highlights where further manual review may be needed.

