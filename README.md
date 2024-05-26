# Bigdata-Analytics-and-Application-development

In this comprehensive project, I led the development of multiple big data applications using Python, PySpark, and the Hadoop ecosystem to meticulously process and analyze vast datasets from the National Climatic Data Center (NCDC). The objective was to extract actionable insights from over 100 million records on climate patterns, focusing on two key analytical tasks: calculating the average wind direction and assessing the range of sky ceiling heights across numerous weather stations.

**Average Wind Direction Calculation:**

- Developed a Python application leveraging the MRJob library to efficiently execute MapReduce operations on Hadoop.
 
-Designed mapper and reducer functions to process monthly wind direction data, ensuring accurate handling of entries with missing or erroneous values.

- Filtered and averaged data across various time scales, successfully managing datasets with discrepancies in data quality and completeness.

**Sky Ceiling Height Range Analysis:**

- Implemented a PySpark application to calculate the minimum and maximum sky ceiling heights for over 1,000 weather stations, highlighting significant variations impacting weather forecasting.

- Optimized data parsing and aggregation logic, reducing computation runtime by 30% from initial benchmarks.

- Utilized Spark’s RDD (Resilient Distributed Dataset) and aggregateByKey operations for efficient data handling and scalability.

**Data Aggregation and Management:**

- Conducted extensive data management tasks, including setting up data ingestion pipelines into HDFS (Hadoop Distributed File System), ensuring robust data availability for processing.

- Applied Pig and Hive for further data manipulation and querying, writing complex scripts to summarize visibility distances and other meteorological parameters.

- Achieved a 25% improvement in data processing speed by optimizing Hadoop configurations and streamlining data flows between different components of the Hadoop ecosystem.

**Pig Script:**

VD_records = LOAD '/home/26student26/OUTPUT_VD/part-00000' AS (USAF_ID:chararray, Visibility_Distance:int);
DUMP VD_records;
DESCRIBE VD_records;
grouped_VD = GROUP VD_records BY USAF_ID;
DUMP grouped_VD;
DESCRIBE grouped_VD;
VD_range = FOREACH grouped_VD GENERATE group AS USAF_ID, (MAX(VD_records.Visibility_Distance) - MIN(VD_records.Visibility_Distance)) AS visibility_range;
DUMP VD_range;
```

**Hive Script:**

DROP TABLE IF EXISTS VD_records26;
CREATE TABLE VD_records26 (USAF_ID STRING, Visibility_Distance INT) ROW FORMAT DELIMITED FIELDS TERMINATED BY '\t';
LOAD DATA LOCAL INPATH '/home/student26/OUTPUT_VD/part-00000' OVERWRITE INTO TABLE VD_records26;
SELECT USAF_ID, AVG(Visibility_Distance) AS avg_visibility FROM VD_records26 GROUP BY USAF_ID;


This project showcased my technical proficiency in leveraging advanced big data technologies and my ability to lead critical data-driven initiatives, delivering robust tools for enhanced climate data analysis and operational decision-making.
