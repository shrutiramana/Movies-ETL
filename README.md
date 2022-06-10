# Movies-ETL Overview of Project
Amazing Prime likes dataset and wants to keep it updated on a daily basis.To help Britta,an automated pipeline that takes in new data, performs the appropriate transformations, and loads the data into existing tables is created. This part is divided into 4 deliveratbles.

## Resources
1. Data Source 
  - ratings.csv(added in .gitignore as its a huge file)
  - movies_metadata.csv
  - wikipedia-movies.json
2. Software - Python 3.8.5, Jupiter Notebook 6.1.4 
3. pgAdmin 4
4. PostgreSQL 13

## Deliverable 1. Write an ETL Function to Read Three Data Files. 
An ETL function is written to read in the three data files. The function converts:
  * the Wikipedia JSON file to a Pandas DataFrame
  * the Kaggle metadata file to a Pandas DataFrame
  * MovieLens ratings data file to a Pandas DataFrame
  * ETL_function_test.ipynb
displayed in the ETL_function_test.ipynb file.
<img width="1095" alt="wiki_movies" src="https://user-images.githubusercontent.com/98556229/173103731-68c723f0-fd19-47f0-9536-567a47b23d53.png">
<img width="1027" alt="Kaggle" src="https://user-images.githubusercontent.com/98556229/173103745-781a204a-b01f-4f38-8bbf-e1b96ffc3b50.png">
<img width="418" alt="ratings" src="https://user-images.githubusercontent.com/98556229/173103753-1e406381-62dc-4330-a32b-1e299af94e02.png">



## Deliverable 2. Extract and Transform the Wikipedia Data
In ### ETL_clean_wiki_movies.ipynb, we include all the movies , exclude TV shows and a new wiki_movies_df is created. We use regex to extract the data and transform of wikipedia data.Below are the steps that are performed for ETL process : 
1. A list comprehension is used to keep columns with non-null values and they are converted to string values usig the lambda & join functions.
2. To get uniform data so that we can load them in database we use regex to transform the data, below are the columns that are cleaned in the Wikipedia DataFrame:
      box_office 
      budget 
      release_date 
      running_time

<img width="1029" alt="image" src="https://user-images.githubusercontent.com/98556229/173106168-bf8820a8-0aeb-427e-a326-1206c867de0a.png">


## Deliverable 3. Extract and Transform the Kaggle Data.
We extract and transform the Kaggle metadata and then Kaggle & wikipedia dataframes are merged to create a new dataframe movies_df.
Duplicated columns are dropped, missing data is filled in kaggle data, specific columns are filtered and columns are renamed.
MovieLens ratings data is cleaned and  movies_with_ratings_df DataFrame is created. Empty values in ratings are filled with 0s. New df's are displayed.

<img width="1101" alt="image" src="https://user-images.githubusercontent.com/98556229/173107719-809e85df-8454-4082-935e-377bb75ca4d6.png">

<img width="1048" alt="image" src="https://user-images.githubusercontent.com/98556229/173107809-1ca83eda-6e09-492f-925e-b32be2d08069.png">


## Deliverable 4: Create the Movie Database 
* The data from the movies_df is loaded in movies table in the SQL database, as in movies_query.png
* The data from the MovieLens rating CSV file is added to the ratings table in the SQL database, as in ratings_query.png. 
* The elapsed time to add the data to the database is displayed in the ETL_create_database.ipynb file. 

<img width="668" alt="Screen Shot 2022-06-10 at 11 30 23 AM" src="https://user-images.githubusercontent.com/98556229/173111040-12ff09ef-cb68-4fc7-b03a-af6d0302b353.png">

<img width="999" alt="image" src="https://user-images.githubusercontent.com/98556229/173111415-d5acda7a-21a5-4dbf-87cb-eb3dcd32342d.png">


<img width="1201" alt="image" src="https://user-images.githubusercontent.com/98556229/173111261-160e0643-fd1b-40d7-84fb-a34584891efc.png">
