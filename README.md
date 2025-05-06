# Query a Data Warehouse in Microsoft Fabric

# Overview
This lab demonstrates how to work with a data warehouse in Microsoft Fabric, including creating a workspace, setting up a sample data warehouse, running queries, verifying data consistency, and creating views.

# Prerequisites
Microsoft Fabric trial account

# Web browser access

# Lab Steps
# 1. Create a Workspace
 - Navigate to the Microsoft Fabric home page

 - Select "Workspaces" from the left menu (🗇 icon)

 - Create a new workspace with your preferred name

# 2. Create Sample Data Warehouse
 - Select "Create" from the left menu

 - Choose "Sample warehouse" under the Data Warehouse section

 - Create a new data warehouse named sample-dw

# 3. Query the Data Warehouse
 - Use "New SQL query" to create queries

 - Run sample queries:
   -- Monthly trips and revenue
SELECT 
  D.MonthName, 
  COUNT(*) AS TotalTrips, 
  SUM(T.TotalAmount) AS TotalRevenue 
FROM dbo.Trip AS T
JOIN dbo.[Date] AS D ON T.[DateID]=D.[DateID]
GROUP BY D.MonthName;

# 4. Verify Data Consistency
Check for data anomalies:
-- Trips longer than 24 hours
SELECT COUNT(*) FROM dbo.Trip WHERE TripDurationSeconds > 86400;

-- Trips with negative duration
SELECT COUNT(*) FROM dbo.Trip WHERE TripDurationSeconds < 0;

# 5. Create Views
Save filtered queries as views:
CREATE VIEW vw_JanTrip AS
SELECT 
  D.DayName, 
  AVG(T.TripDurationSeconds) AS AvgDuration, 
  AVG(T.TripDistanceMiles) AS AvgDistance 
FROM dbo.Trip AS T
JOIN dbo.[Date] AS D ON T.[DateID]=D.[DateID]
WHERE D.Month = 1
GROUP BY D.DayName;

# 6. Clean Up Resources
 - To delete the workspace:

 - Navigate to workspace settings

 - Select "Remove this workspace"
 - 
# Key Learnings
 - Creating data warehouses in Microsoft Fabric

 - Executing SQL queries

 - Validating data quality

 - Creating and managing views
