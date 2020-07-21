1. Data preparation
run_analysis.R script performs data preparation followed by the 5 steps as instructed in this course project.

2.  Download the dataset
Download and extract the Dataset into the folder UCI HAR Dataset
Full path name: E:\06.Education\Course Project #3\UCI HAR Dataset

3. Assign data to each variable
features stores data from features.txt : 561 rows, 2 columns
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ. It consists of funcid, an integer (1-561) and funcdesc, its description (feature)

activities stores data from activity_labels.txt : 6 rows, 2 columns
List of activities performed when the corresponding measurements were taken, actid, an integer (1-6) and activity, its description (label)

subject_test stores data from test/subject_test.txt : 2947 rows, 1 column
Test data of 9/30 volunteer subjects being observed

x_test stores data from test/X_test.txt : 2947 rows, 561 columns
Recorded features test data

y_test stores data from test/y_test.txt : 2947 rows, 1 columns
Test data of activities (repetition of integer 1 - 6)

subject_train stores data from  train/subject_train.txt : 7352 rows, 1 column
Train data of 21/30 volunteer subjects being observed

x_train stores data from test/X_train.txt : 7352 rows, 561 columns
Recorded features train data

y_train stores data from test/y_train.txt : 7352 rows, 1 columns
Train data of activities (repetition of integer 1 - 6)

4. Merges the training and the test data sets to create one data set
measurements (10299 rows, 561 columns) is created by merging x_train and x_test using rbind() function
activity (10299 rows, 1 column) is created by merging y_train and y_test using rbind() function
subject (10299 rows, 1 column) is created by merging subject_train and subject_test using rbind() function
merge_data (10299 rows, 563 column) is created by merging subject, activity_id and measurements using cbind() function

5. Extracts only the measurements on the mean and standard deviation for each measurement
tidy_data (10299 rows, 88 columns) is created by subsetting merged_data, selecting only columns: subject, activity_id and measurements which are the features (variables) 
with "mean" and "standard deviation (std)" in the features

6. Uses descriptive activity names to name the activities in the data set
Replace all integers in activity_id column of tidy_data with corresponding activity, the description (label) taken from second column of the activities variable

7. Appropriately labels the data set with descriptive variable names
actid column in tidy_data renamed into activity
All Acc in column’s name replaced by Accelerometer
All Gyro in column’s name replaced by Gyroscope
All BodyBody in column’s name replaced by Body
All Mag in column’s name replaced by Magnitude
All start with character f in column’s name replaced by Freq
All start with character t in column’s name replaced by Time

From the data set in step 4 in the course project instruction, creates a second, independent tidy data set with the average of each variable for each activity and each subject
result_data (180 rows, 88 columns) is created by summarizing tidy_data taking the means of each variable for each activity and each subject, after grouped by subject and activity.
Export result_data into result_data.txt file.
