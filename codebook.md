The **run_analysis.R** script performs the data preparation and then followed by the 5 steps required as described in the course project’s definition.

**1. Download the dataset**
Dataset downloaded and extracted under the folder called _UCI HAR Dataset_

**2. Assign each data to variables**

_features_ <- _features.txt_ : "561 rows, 2 columns"
The features selected for this database come from the accelerometer and gyroscope 3-axial raw signals tAcc-XYZ and tGyro-XYZ.

_activities_ <- _activity_labels.txt_ : 6 rows, 2 columns
List of activities performed when the corresponding measurements were taken and its codes (labels)

_subject_test_ <- _test/subject_test.txt_ : 2947 rows, 1 column
contains test data of 9/30 volunteer test subjects being observed

_x_test_ <- _test/X_test.txt_ : 2947 rows, 561 columns
contains recorded features test data

_y_test_ <- _test/y_test.txt_ : 2947 rows, 1 columns
contains test data of activities’code labels

_subject_train_ <- _test/subject_train.txt_ : 7352 rows, 1 column
contains train data of 21/30 volunteer subjects being observed

_x_train_ <- _test/X_train.txt_ : 7352 rows, 561 columns
contains recorded features train data

_y_train_ <- _test/y_train.txt_ : 7352 rows, 1 columns
contains train data of activities’code labels

**3. Merges the training and the test sets to create one data set**

_X_ (10299 rows, 561 columns) is created by merging _x_train_ and _x_test_ using _rbind()_ function
_Y_ (10299 rows, 1 column) is created by merging y_train and y_test using _rbind()_ function
_Subject_ (10299 rows, 1 column) is created by merging _subject_train_ and _subject_test_ using _rbind()_ function
_Merged_Data_ (10299 rows, 563 column) is created by merging _Subject_, _Y_ and _X_ using _cbind()_ function

**4. Extracts only the measurements on the mean and standard deviation for each measurement**

_TidyData_ (10299 rows, 88 columns) is created by subsetting _Merged_Data_, selecting only columns: _subject_, _code_ and the measurements on the _mean_ and standard deviation (_std_) for each measurement

**5. Uses descriptive activity names to name the activities in the data set**

Entire numbers in code column of the TidyData replaced with corresponding activity taken from second column of the activities variable

**6. Appropriately labels the data set with descriptive variable names**

code column in TidyData renamed into activities
All _Acc_ in column’s name replaced by _Accelerometer_
All _Gyro_ in column’s name replaced by _Gyroscope_
All _BodyBody_ in column’s name replaced by _Body_
All _Mag_ in column’s name replaced by _Magnitude_
All start with character _f_ in column’s name replaced by _Frequency_
All start with character _t_ in column’s name replaced by _Time_

**7. From the data set in step 4, creates a second, independent tidy data set with the average of each variable for each activity and each subject**

_FinalData_ (180 rows, 88 columns) is created by sumarizing _TidyData_ taking the means of each variable for each activity and each subject, after groupped by subject and activity.
Export _FinalData_ into _FinalData.txt_ file.
