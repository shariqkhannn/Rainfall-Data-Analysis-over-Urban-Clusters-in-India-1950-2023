# _**Spatio-temporal Analysis of Urban Monsoon Rainfall (1950–2023)**_


# CHAPTER 1: 	INTRODUCTION

The Indian monsoon is the single most important climatic phenomena dictating the country’s agricultural productivity, water security and disaster resilience. About 70–80% of the annual rainfall in India takes place during monsoon months (June–September), serving as the backbone of the economy where agriculture, drinking water supply, and hydroelectricity generation and overall ecosystem stability rely heavily on the monsoon (Gadgil & Gadgil, 2006). But the changing climate and human impacts have made monsoons more inconsistent, resulting in more extremes of rain, with some places getting more downpours and floods, others plunging into long dry spells and droughts. These dynamic trends raise questions of urban sustainability and resilience, when they relate to rapidly growing Very Large Metropolitan Areas

As urbanization accelerates at an all-time high, cities in India are experiencing more dramatic shifts in land-use characteristics that affect local climate conditions and distribution of rainfall. Urban clusters, especially megacities such as Mumbai, Delhi, Kolkata, Chennai, and Bengaluru, have seen explosive changes in land-use attributes, built-up area, and anthropogenic effects of heat in the last few decades (Mishra et al., 2018). Such changes affect natural hydrological systems, modify monsoon circulation, and amplify extreme weather events. The Urban Heat Island (UHI), where urban areas attain elevated temperatures, arise due to built-up concrete/impervious surfaces with reduced vegetation cover, altering local atmospheric stability and changing expectation of not only amounts of total rainfall but also the possibility of rainfall itself depending on atmospheric conditions. Moreover, urban cluster, urbanization, change in land use, thermometer, intensify storm events, climate conditions, environmental changes, and rainfall periods. 

According to World Bank estimates, more than 35% of India’s population now lives in cities, and that is expected to increase considerably in the next few decades (World Bank, 2021). The growing trend of extreme monsoon events presents a significant challenge for urban planning, disaster management, and sustainable development. Cities will continue to be vulnerable to flooding during heavy rain because of inefficient drainage of stormwater, encroachment of floodplains and poor water management. In contrast, less than adequate rains or late arriving monsoons cause water scarcity impacting millions of residents (#) in the urban areas. It is also important to know the long-term trends and anomalies of monsoon rainfall and their impact over high-density urban clusters for infrastructure resilience and climate adaptation strategies.

This study focuses on analyzing monsoon rainfall trends over India’s urban clusters from 1950 to 2023, identifying long-term anomalies, and classifying extreme events such as floods (Z > 1) and droughts (Z < -1). By integrating high-resolution gridded rainfall data from the India Meteorological Department (IMD) with urban population data from WorldPop (2020), this research seeks to provide a comprehensive assessment of rainfall variability over urban clusters. The insights derived will contribute to better disaster preparedness, sustainable water resource management, and climate-resilient urban planning in India’s rapidly growing cities.



# CHAPTER 2: 	DATA AND METHODOLOGY

This chapter outlines the datasets, preprocessing steps, and analytical techniques used to investigate monsoon rainfall trends over urban clusters in India from 1950 to 2023. The study integrates IMD gridded rainfall data with urban population datasets, followed by statistical time-series analysis and extreme event detection using the Z-test.

**2.1	Dataset Description**
This study integrates two primary datasets: the IMD Gridded Rainfall Data and the WorldPop 100m Population Data. These datasets are preprocessed and analyzed to understand long-term monsoon rainfall trends over urban clusters in India.

  **2.1.1	IMD Gridded Rainfall Data**
  
  Source: India Meteorological Department (IMD)
  
  Temporal Range: 1950–2023
  
  Spatial Resolution: 25×25 km
  
  Data Format: NetCDF (.nc)
  
  Description: This dataset provides daily rainfall observations across India in a gridded format, allowing for spatial and temporal analysis of monsoon rainfall patterns.

  **2.1.2	Urban Population Data (WorldPop 100m)**
  
  Source: WorldPop (University of Southampton)
  
  Temporal Range: 2020 (Version 2.0)
  
  Spatial Resolution: 100m (resampled to 25×25 km)
  
  Data Format: GeoTIFF
  
  Description: The WorldPop dataset estimates population distribution at a fine spatial resolution, adjusted using UN population estimates. It provides insights into urbanization            patterns, essential for overlaying with rainfall data.

**2.2	Data Preprocessing**
To prepare the data for analysis, multiple steps were followed:

  **2.2.1	Processing IMD Rainfall Data**
   
  **1. Extract Monsoon Rainfall (June–September):**
  The dataset includes daily rainfall values. Only the monsoon season (June 1 – September 30) is extracted for each year (1950-2023).
  
  **2. Handling Missing Values:**
  The IMD dataset uses -999 for missing values, which are replaced with NaN (Not a Number) to prevent errors in analysis.
  
  **3. Spatial Aggregation:**
  The dataset is already in 25×25 km resolution, aligned with the study’s spatial scale.
    
  **4. Saving Processed Data:**
  The cleaned dataset is stored in NetCDF format for consistency and ease of access.

  **2.2.2	Processing WorldPop Population Data**
  
  **1. Resampling to 25×25 km Grid:**
  Since the WorldPop data is at 100m resolution, it is resampled in QGIS using the Resample Aggregate (SUM) method, ensuring that the total population count is preserved.
  
  **2. Identifying Urban Clusters:**
  Urban clusters are identified as grid cells with a total population > 1 million people based on the 2020 dataset.
  
  **3. Extracting Urban Cluster Locations:**
  The processed population grid is overlaid with the rainfall dataset to extract urban clusters.
  
  **4. Saving Processed Data:**
  The final urban population data is stored as a GeoTIFF file for spatial analysis.

**2.3	Composite Analysis of Rainfall & Urban Population Matrix**

To analyze the relationship between rainfall and urban population, an m×n matrix is constructed where:

m = Number of urban clusters (71 cities)

n = Yearly monsoon rainfall data (1950–2023)

  **2.3.1	Time Series Analysis of Monsoon Rainfall Over Urban Clusters**
    
  **1. Extract Rainfall Data for Each Urban Cluster**
  The processed IMD rainfall data is spatially matched with urban clusters to extract yearly monsoon rainfall for each city.

  **2. Calculate Long-Term Mean & Anomalies**
  The average monsoon rainfall for all clusters combinedly is computed, and anomalies (deviations from the mean) are identified.

**2.4	Z-Test for Extreme Event Detection**

The Z-test is employed in this study to statistically assess deviations in annual monsoon rainfall from the long-term mean across urban clusters. This test helps identify extreme events—droughts and floods—by determining whether a given year’s rainfall significantly deviates from the average. We chose the Z-test because it assumes a normal distribution of large-sample data, making it suitable for long-term climatic studies. 

  **2.4.1	Z-Test Formula**
    
  Z = (X - 𝞵 ) / 𝝈

  where:
    
  X = Observed rainfall for a given year
  𝞵 = Mean monsoon rainfall over the period (1950-2023)
  𝝈 = Standard deviation of monsoon rainfall

  **2.4.2	Defining Extreme Events**
  Based on statistical thresholds, extreme events were classified as:

  Flood Year → Z > 1 (Above normal rainfall)

  Drought Year → Z < -1 (Below normal rainfall)

  **2.4.3	Visualizing Extreme Events**
  
  To enhance interpretation, extreme events were marked on the time series plots:
  
  Floods (Z > 1) →  Black dots
  
  Droughts (Z < -1) →  Red dots



# CHAPTER 3: 	RESULTS AND ANALYSIS

  **1.	Resampled Population Data of India (25*25 km Resolution)**
  ![1  Resampled Population Data of India](https://github.com/user-attachments/assets/7bf20810-c79d-4707-847d-fb617f708fe1)

  **2. Identified Urban Clusters**
  ![2  Urban Clusters India](https://github.com/user-attachments/assets/ba754b8f-b4fa-4eda-854b-7e21cec461b8)

  Using the WorldPop dataset (2020), 71 urban clusters were identified based on a population threshold of  1 million. Some of these are mentioned below:   
  
  Mumbai
  
  Delhi
  
  Kolkata
  
  Bangalore
  
  Chennai
  
  Ahmedabad
  
  Hyderabad
  
  Pune

  **3. Time Series Analysis of Rainfall Data for all 71 clusters (1950-2023)**
  This section examines long-term monsoon rainfall trends across 71 identified urban clusters in India from 1950 to 2023. Using processed IMD gridded rainfall data, the analysis evaluates   temporal variations, computes mean annual rainfall, and identifies anomalies. The study employs statistical techniques, including Z-tests, to detect significant deviations corresponding   to extreme flood and drought years, providing insights into the evolving rainfall patterns over urbanized regions.

  ![3  Combined Annual Monsoon Rainfall Trend for All Clusters (1950-2023)](https://github.com/user-attachments/assets/609e5dd0-bab9-41c9-b792-48b3e321fa73)

  **Mean Annual Rainfall (1950-2023): 856.45 mm**

  **4. Z-Test for Extreme Event Detection**
  
  The Z-score was calculated for each year’s rainfall, using: 
  
  Z = (X - 𝞵 ) / 𝝈
  
  Flood Years (Z > 1): Indicating above-average rainfall.
  
  Drought Years (Z < -1): Indicating significantly lower rainfall.

  ![4  Extreme Events for Urban Clusters for 1950-2023](https://github.com/user-attachments/assets/bd743e58-2b54-4d63-b614-eaf4ca4df3f5)

  Z-score analysis identified several flood years and drought years, which are given below
  
  Flood Years: Years where monsoon rainfall exceeded the mean rainfall.

  **Flood Years:** Years where monsoon rainfall exceeded the mean rainfall.
  
  | Year | Rainfall (mm) | Deviation (mm) |
  |------|----------------|----------------|
  | 1950 | 979.81         | 123.37         |
  | 1953 | 987.74         | 131.30         |
  | 1956 | 973.04         | 116.60         |
  | 1961 | 1003.03        | 146.58         |
  | 1971 | 951.05         | 94.61          |
  | 1975 | 978.93         | 122.48         |
  | 1988 | 1038.53        | 182.08         |
  | 2005 | 954.37         | 97.92          |
  | 2007 | 1002.09        | 145.65         |
  | 2008 | 987.19         | 130.75         |
  | 2011 | 1047.88        | 191.44         |

  **1950-2000 - 7 Flood Years with highest deviation of +182.02 mm (1988)**

  **2000-2023: 4 Flood Years with highest deviation of +191.44 mm (2011)**

  **Drought Years:** Years where monsoon rainfall exceeded the mean rainfall.
  
  | Year | Rainfall (mm) | Deviation (mm) |
  |------|----------------|----------------|
  | 1951 | 723.46         | -132.98        |
  | 1965 | 696.62         | -159.83        |
  | 1966 | 735.91         | -120.54        |
  | 1972 | 610.52         | -245.92        |
  | 1979 | 725.49         | -130.95        |
  | 1982 | 690.73         | -165.72        |
  | 1987 | 760.13         | -96.31         |
  | 2002 | 723.66         | -132.78        |
  | 2009 | 731.82         | -124.63        |
  | 2014 | 721.23         | -135.22        |
  | 2015 | 704.60         | -151.85        |
  | 2023 | 743.09         | -113.35        |

 **1950-2000 - 7 Drought Years with highest deviation of -245.92 mm (1972)**
 
 **2000-2023 - 5 Drought Years with highest deviation of -151.85 mm (2015)**

  **5.	Decadal Comparison of Rainfall Patterns**
  
  It was observed that the overall precipitation over these urban clusters have declined in recent decades as shown below indicating climate change impact of recent decades.
  ![6  Decadal Variation of Monsoon Rainfall Over Urban Clusters (1950-2023)](https://github.com/user-attachments/assets/cb60923d-96c9-4b6f-b8f4-d82f6c669041)

  2011 was the last flood year over these clusters with a monsoon rainfall of **1047.88 mm**
  
  For the past decade, a declining trend in the rainfall patterns over India, however the regional extreme events (both floods and droughts) have increased.
  
  Last Decade has the lowest decadal average rainfall of **830.51 mm** from our analysis over these 71 clusters.



# CHAPTER 4: 	IMPACTS OF EXTREME EVENTS ON URBAN CLUSTERS

Floods are the deadliest of natural hazards in India. From 1980 to 2017, India had 235 floods that resulted in 126,286 fatalities and 1.93 billion affected individuals. Flooding is a huge problem for most urban cities in India, and major occurrences were noted in our selected cities that include Patna, Delhi, Ahmedabad, Bangalore, Chennai, Kanpur, Kolkata, and Mumbai. Droughts, however, have extensive social and economic impacts. They lead to extensive food insecurity through decreased agricultural productivity, pushing malnutrition and rural-urban migration. The social effects of floods in these cities are diverse but have similar themes, such as damage to infrastructure, displacement, health emergencies, economic losses, and environmental degradation.

| City       | Flood Years                 | Drought Years | Flood Impacts                                                                                                                                               | Drought Impacts                                                                                   |
|------------|-----------------------------|---------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------------------------------------------------------------------------------------------|
| Patna      | 1961, 1987, 1988, 2007      | 1966–67       | 551 lives lost (1961), 1,399 deaths (1987), property damage ₹68 billion (1987), severe slum flooding (2007), water contamination, disease outbreaks         | 35,000 starvation deaths, food grain production dropped from 7.5 to 7.2 million tonnes            |
| Mumbai     | 1988, 2007                  |               | Complete transportation shutdown (1988), 160 train cancellations, infrastructure collapse, slum areas particularly vulnerable                               |                                                                                                   |
| Chennai    | 1988, 2007, 2010            |               | Multiple fatalities, extensive paddy crop destruction, infrastructure damage                                                                                 |                                                                                                   |
| Bangalore  | 1988, 2007                  | 2017          | 6 deaths (1988), extensive property damage, collapsed houses, widespread utility disruptions                                                                | 6,900 of 13,900 borewells dried despite 1,500 feet depth, water crisis affecting 13 million people|
| Delhi      | 1988, 2010, 2013            | 1989          | Water levels reached 206.92m at Railway Bridge (1988), 16,000+ people evacuated, widespread transportation disruption                                       | Annual water shortages, inequitable distribution, slum areas particularly affected                |
| Kolkata    | 1988, 2007, 2011            |               | City-wide submersion (1988), thatched housing destruction, transportation paralysis                                                                          |                                                                                                   |
| Ahmedabad  | 1988, 2007, 2008, 2009, 2013| 1986–87       | 63 deaths (2007), 6,000 evacuated, infrastructure damage, power disruptions, 200+ houses damaged (1988)                                                     |                                                                                                   |
| Kanpur     | 1988, 2011                  |               | 611 deaths (1988), 22,433 combined deaths reported in Kanpur Dehat and Nagar (2011), 2.05 million people affected                                            |                                                                                                   |

  **_Table : Floods and Droughts in Major Indian Cities: Years of Occurrence and Societal Impacts_**



# CONCLUSION

This research provides a comprehensive exploration of the long-term trends of monsoon rainfall (1950-2023) over urban clusters in India focussing on extreme monsoon rainfall events and the implications for socio-economics and infrastructure. The analysis integrated high-resolution IMD gridded rainfall data with WorldPop urban population estimates documenting spatial and temporal anomalies in monsoon rainfall patterns across 71 urban clusters. Overall, the research findings suggest more frequent and intense extreme rainfall events in a number of cities indicating the role of urbanisation, climate change and land-use changes increases climate flood and drought risk. The extreme rainfall events on urban clusters assessed a significant level of social impact. Flood and drought events are natural hazards in the world which climate change inflates, but impact is often socially constructed through physical vulnerability, social vulnerability and governance factors. Constructing climate resilient communities requires collaborative action by governments, industries and communities to foster a just and equitable future. 

Flood resilience measures should include improved drainage systems, conservation of urban wetlands, and AI-based early warning systems.  Drought adaptation measures should include rainwater harvesting, groundwater recharge, and more urban greenery. There is need for incorporating climate projections into urban planning and infrastructure development to ensure cities are resilient against future extremes associated with climate change.In the end, this research highlights the compelling need for sustainable urban planning, proactive climate policies, and technological innovation in disaster management.  Addressing these challenges will be imperative for protecting India’s rapidly growing urban centers from increasing risks of extreme weather events.









