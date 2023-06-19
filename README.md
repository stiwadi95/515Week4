# 515Week4

---
title: "Week 4 Assignment - Shruti Tiwadi"
output: html_document
date: "2023-06-19"
---

```{r setup, include=FALSE}
knitr::opts_chunk$set(echo = TRUE)

# Header
cat("Section One\n\n")

# Text
cat("The dataset being used is a database of collision reports. It offers details on a variety of factors that are connected to each collision, including the date, time, location, weather, and particulars about the collision type, road conditions, and more. Most likely, accident reports or other similar sources were used to collect the data. This dataset's goal is to examine and comprehend the trends, causes, and traits connected to traffic collisions. Research questions about the relationship between lighting and collision frequency, the effect of weather on collision rates, or the kinds of collisions that frequently happen in various locations can all be addressed using this data..\n")

# Header
cat("Section two\n\n")

library(readr)

# Reading the data into an R dataframe
collision_df <- read_csv("Maryland_Statewide_Vehicle_Crashes.csv")

# Header
cat("Section Three\n\n")

# Renaming columns for better readability
names(collision_df) <- c("Year", "Quarter", "Lighting_Description", "Lighting_Code", "County_Description", "County_Code", "Municipality_Description", "Municipality_Code", "Junction_Description", "Junction_Code", "Collision_Type_Description", "Collision_Type_Code", "Surface_Condition_Description", "Surface_Condition_Code", "Lane_Code", "Road_Condition_Description", "Road_Condition_Code", "Road_Division_Description", "Road_Division_Code", "Fixed_Object_Description", "Fixed_Object_Code", "Report_Number", "Report_Type", "Weather_Description", "Weather_Code", "Collision_Date", "Collision_Time", "Location_Code", "Signal_Flag_Description", "Signal_Flag", "C_M_Zone_Flag", "Agency_Code", "Area_Code", "Harmful_Event_Description1", "Harmful_Event_Code1", "Harmful_Event_Description2", "Harmful_Event_Code2", "Route_Number", "Route_Type_Code", "Route_Suffix", "Log_Mile", "Log_Mile_Direction_Flag_Description", "Log_Mile_Direction_Flag", "Main_Road_Name", "Distance", "Feet_Miles_Flag_Description", "Feet_Miles_Flag", "Distance_Direction_Flag", "Reference_Number", "Reference_Type_Code", "Reference_Suffix", "Reference_Road_Name", "Latitude", "Longitude", "Location")

# Converting the "Collision_Date" column to a Date format
collision_df$Collision_Date <- as.Date(collision_df$Collision_Date, format = "%Y%m%d", origin = "1970-01-01")

# Header
cat("Section Four\n\n")

# Number of rows and columns
num_rows <- nrow(collision_df)
num_cols <- ncol(collision_df)

# Displaying the number of rows and columns
cat("This dataframe has", num_rows, "rows and", num_cols, "columns.\n")

# Creating a table with column names and descriptions
library(knitr)
column_names <- colnames(collision_df)
column_descriptions <- c(
  "Year",
  "Quarter",
  "Lighting Description",
  "Lighting Code",
  "County Description",
  "County Code",
  "Municipality Description",
  "Municipality Code",
  "Junction Description",
  "Junction Code",
  "Collision Type Description",
  "Collision Type Code",
  "Surface Condition Description",
  "Surface Condition Code",
  "Lane Code",
  "Road Condition Description",
  "Road Condition Code",
  "Road Division Description",
  "Road Division Code",
  "Fixed Object Description",
  "Fixed Object Code",
  "Report Number",
  "Report Type",
  "Weather Description",
  "Weather Code",
  "Collision Date",
  "Collision Time",
  "Location Code",
  "Signal Flag Description",
  "Signal Flag",
  "C_M_Zone Flag",
  "Agency Code",
  "Area Code",
  "Harmful Event Description1",
  "Harmful Event Code1",
  "Harmful Event Description2",
  "Harmful Event Code2",
  "Route Number",
  "Route Type Code",
  "Route Suffix",
  "Log Mile",
  "Log Mile Direction Flag Desc",
  "Log Mile Direction Flag",
  "Main Road Name",
  "Distance",
  "Feet Miles Flag Desc",
  "Feet Miles Flag",
  "Distance Direction Flag",
  "Reference Number",
  "Reference Type Code",
  "Reference Suffix",
  "Reference Road Name",
  "Latitude",
  "Longitude",
  "Location"
)

column_table <- data.frame(Column_Name = column_names, Description = column_descriptions)
kable(column_table)


# Header
cat("Section Five\n\n")
# Selecting three columns for summary statistics
selected_columns <- c("Collision_Date", "Weather_Description", "Collision_Type_Description")

# Filtering the dataframe to exclude missing values
filtered_df <- collision_df[complete.cases(collision_df[, selected_columns]), ]

# Summary statistics
summary_stats <- summary(filtered_df[, selected_columns])
summary_stats

```



