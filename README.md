# DataWarehousingETL-Redshift-Udacity
Data Warehousing project for Udacity: Build an ETL pipeline, which pulls the data from S3 bucket (JSON files) and keeps in Redshift Staging tables. Then create analytics tables by copying data from staging tables. Python is the base, AWS resource are used.


# >>>>>>>>>>P R O J E C T : D a t a W a r e h o u s e<<<<<<<

## >>>>>>>>>>>Objetive<<<<<<<<<<

   Create an ETL pipeline to move the data and processes to cloud, from existing S3 JSON files.
   
   
## >>>>>>>>>>>Instructions<<<<<<<<<<

> Create table schemas

  ### Step 1:
    Design Fact and Dimension tables
    
    ----------------------------------------
    Staging Tables
       stage_events - To store the log data from input JSON files for ETL process
         (artist,auth, firstName, gender, lastName, length, level, location, method, page,
          registration, sessionId, song, status, ts, userAgent, userId)
          
       stage_songs - To store the song data from input JSON files for ETL process
        (num_songs, artist_id, artist_latitude, artist_longitude, artist_location,
         artist_name, song_id, title, duration, year)
    
    Fact Table
       songplays - records in event data associated with song plays i.e. records with page NextSong
         (songplay_id, start_time, user_id, level, song_id, artist_id, session_id, location, user_agent)

    Dimension Tables
       users - users in the app
         (user_id, first_name, last_name, gender, level)
       songs - songs in music database
         (song_id, title, artist_id, year, duration)
       artists - artists in music database
         (artist_id, name, location, lattitude, longitude)
       time - timestamps of records in songplays broken down into specific units
         (start_time, hour, day, week, month, year, weekday)
         
    ----------------------------------------
  
  ### Step 2:
    Update the dwh.cfg file with configuration data
       

  ### Step 3:
    Write create and insert SQL statement for tables in sql_queries.py
    (staging table data needs to be copied from S3 JSON Files)
    
  ### Step 4:
    Connect to Redshift cluster and AWS resources in create_tables.py
    (create a IAM role that has read only access to S3 and launch a Redshift cluster,
     provide these details in dwh.cfg file)

> Running the queries     

  ### Step 5:
    Implement the logic to load data from S3 to staging table on Redshift and from staging 
    tables to analytics tables on Redshift in etl.py

  ### Step 6:
    Test the programs by running create_tables.py, then etl.py, query the results:
    example:
        
        select * from public.stage_songs limit 10;
        select * from public.songplays limit 10;         
    
  ### Step 7:
    Delete the Redshift cluster once the ETL process is completed.
    
## >>>>>>>>>>> N o t e s <<<<<<<<<<

Open DWH-Workbook.ipynb and follow the sequence 
Create a Cluster, only if it does not exists
run create_tables.py, to create db schema
run etl.py, to start the ETL process
run analytics query to check the results 
