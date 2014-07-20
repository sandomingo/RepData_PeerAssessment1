# Reproducible Research: Peer Assessment 1

## Loading and preprocessing the data

```r
raw.data <- read.csv('activity.csv', header=T, stringsAsFactors=F)
# transform the date column to Date type
raw.data$date <- as.Date(raw.data$date)
# omit the missing observations
data <- na.omit(raw.data)
```


## What is mean total number of steps taken per day?

```r
# Calculate total number of steps taken each day
total.daily.steps <- aggregate(data$steps, by=list(data$date), FUN=sum)
names(total.daily.steps) <- c("date", "steps.total")
total.daily.steps
```

```
##          date steps.total
## 1  2012-10-02         126
## 2  2012-10-03       11352
## 3  2012-10-04       12116
## 4  2012-10-05       13294
## 5  2012-10-06       15420
## 6  2012-10-07       11015
## 7  2012-10-09       12811
## 8  2012-10-10        9900
## 9  2012-10-11       10304
## 10 2012-10-12       17382
## 11 2012-10-13       12426
## 12 2012-10-14       15098
## 13 2012-10-15       10139
## 14 2012-10-16       15084
## 15 2012-10-17       13452
## 16 2012-10-18       10056
## 17 2012-10-19       11829
## 18 2012-10-20       10395
## 19 2012-10-21        8821
## 20 2012-10-22       13460
## 21 2012-10-23        8918
## 22 2012-10-24        8355
## 23 2012-10-25        2492
## 24 2012-10-26        6778
## 25 2012-10-27       10119
## 26 2012-10-28       11458
## 27 2012-10-29        5018
## 28 2012-10-30        9819
## 29 2012-10-31       15414
## 30 2012-11-02       10600
## 31 2012-11-03       10571
## 32 2012-11-05       10439
## 33 2012-11-06        8334
## 34 2012-11-07       12883
## 35 2012-11-08        3219
## 36 2012-11-11       12608
## 37 2012-11-12       10765
## 38 2012-11-13        7336
## 39 2012-11-15          41
## 40 2012-11-16        5441
## 41 2012-11-17       14339
## 42 2012-11-18       15110
## 43 2012-11-19        8841
## 44 2012-11-20        4472
## 45 2012-11-21       12787
## 46 2012-11-22       20427
## 47 2012-11-23       21194
## 48 2012-11-24       14478
## 49 2012-11-25       11834
## 50 2012-11-26       11162
## 51 2012-11-27       13646
## 52 2012-11-28       10183
## 53 2012-11-29        7047
```

```r
# histogram of the total number of steps taken each day
hist(total.daily.steps$steps.total)
```

![plot of chunk unnamed-chunk-2](figure/unnamed-chunk-2.png) 

```r
# Calculate and report the mean and median total number of steps taken per day
mean.daily.steps <- aggregate(data$steps, by=list(data$date), FUN=mean)
names(mean.daily.steps) <- c("date", "steps.mean")
mean.daily.steps
```

```
##          date steps.mean
## 1  2012-10-02     0.4375
## 2  2012-10-03    39.4167
## 3  2012-10-04    42.0694
## 4  2012-10-05    46.1597
## 5  2012-10-06    53.5417
## 6  2012-10-07    38.2465
## 7  2012-10-09    44.4826
## 8  2012-10-10    34.3750
## 9  2012-10-11    35.7778
## 10 2012-10-12    60.3542
## 11 2012-10-13    43.1458
## 12 2012-10-14    52.4236
## 13 2012-10-15    35.2049
## 14 2012-10-16    52.3750
## 15 2012-10-17    46.7083
## 16 2012-10-18    34.9167
## 17 2012-10-19    41.0729
## 18 2012-10-20    36.0938
## 19 2012-10-21    30.6285
## 20 2012-10-22    46.7361
## 21 2012-10-23    30.9653
## 22 2012-10-24    29.0104
## 23 2012-10-25     8.6528
## 24 2012-10-26    23.5347
## 25 2012-10-27    35.1354
## 26 2012-10-28    39.7847
## 27 2012-10-29    17.4236
## 28 2012-10-30    34.0938
## 29 2012-10-31    53.5208
## 30 2012-11-02    36.8056
## 31 2012-11-03    36.7049
## 32 2012-11-05    36.2465
## 33 2012-11-06    28.9375
## 34 2012-11-07    44.7326
## 35 2012-11-08    11.1771
## 36 2012-11-11    43.7778
## 37 2012-11-12    37.3785
## 38 2012-11-13    25.4722
## 39 2012-11-15     0.1424
## 40 2012-11-16    18.8924
## 41 2012-11-17    49.7882
## 42 2012-11-18    52.4653
## 43 2012-11-19    30.6979
## 44 2012-11-20    15.5278
## 45 2012-11-21    44.3993
## 46 2012-11-22    70.9271
## 47 2012-11-23    73.5903
## 48 2012-11-24    50.2708
## 49 2012-11-25    41.0903
## 50 2012-11-26    38.7569
## 51 2012-11-27    47.3819
## 52 2012-11-28    35.3576
## 53 2012-11-29    24.4688
```

```r
median.daily.steps <- aggregate(data$steps, by=list(data$date), FUN=median)
names(median.daily.steps) <- c("date", "steps.median")
median.daily.steps
```

```
##          date steps.median
## 1  2012-10-02            0
## 2  2012-10-03            0
## 3  2012-10-04            0
## 4  2012-10-05            0
## 5  2012-10-06            0
## 6  2012-10-07            0
## 7  2012-10-09            0
## 8  2012-10-10            0
## 9  2012-10-11            0
## 10 2012-10-12            0
## 11 2012-10-13            0
## 12 2012-10-14            0
## 13 2012-10-15            0
## 14 2012-10-16            0
## 15 2012-10-17            0
## 16 2012-10-18            0
## 17 2012-10-19            0
## 18 2012-10-20            0
## 19 2012-10-21            0
## 20 2012-10-22            0
## 21 2012-10-23            0
## 22 2012-10-24            0
## 23 2012-10-25            0
## 24 2012-10-26            0
## 25 2012-10-27            0
## 26 2012-10-28            0
## 27 2012-10-29            0
## 28 2012-10-30            0
## 29 2012-10-31            0
## 30 2012-11-02            0
## 31 2012-11-03            0
## 32 2012-11-05            0
## 33 2012-11-06            0
## 34 2012-11-07            0
## 35 2012-11-08            0
## 36 2012-11-11            0
## 37 2012-11-12            0
## 38 2012-11-13            0
## 39 2012-11-15            0
## 40 2012-11-16            0
## 41 2012-11-17            0
## 42 2012-11-18            0
## 43 2012-11-19            0
## 44 2012-11-20            0
## 45 2012-11-21            0
## 46 2012-11-22            0
## 47 2012-11-23            0
## 48 2012-11-24            0
## 49 2012-11-25            0
## 50 2012-11-26            0
## 51 2012-11-27            0
## 52 2012-11-28            0
## 53 2012-11-29            0
```


## What is the average daily activity pattern?

```r
pattern.daily.steps <- aggregate(data$steps, by=list(data$interval), FUN=mean)
names(pattern.daily.steps) <- c("interval", "steps.mean")

# Make a time series plot of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis)
plot(pattern.daily.steps$interval, pattern.daily.steps$steps.mean, type="l")
```

![plot of chunk unnamed-chunk-3](figure/unnamed-chunk-3.png) 

```r
# Which 5-minute interval, on average across all the days in the dataset, contains the maximum number of steps?
pattern.daily.steps[pattern.daily.steps$steps.mean == max(pattern.daily.steps$steps.mean), "interval"]
```

```
## [1] 835
```


## Imputing missing values

```r
# Total number of missing values in the dataset 
nrow(raw.data) - nrow(data)
```

```
## [1] 2304
```

```r
# Use mean(converted to integer) for that 5-minute interval to fill the missing data
index.na <- which(is.na(raw.data))
for (i in index.na) {
  ival <- raw.data[i,  "interval"]
  raw.data[i,"steps"] <- as.integer(pattern.daily.steps[pattern.daily.steps$interval==ival, "steps.mean"])
}

# Recalculate values for the new data
# Calculate total number of steps taken each day
new.total.daily.steps <- aggregate(raw.data$steps, by=list(raw.data$date), FUN=sum)
names(new.total.daily.steps) <- c("date", "steps.total")
new.total.daily.steps
```

```
##          date steps.total
## 1  2012-10-01       10641
## 2  2012-10-02         126
## 3  2012-10-03       11352
## 4  2012-10-04       12116
## 5  2012-10-05       13294
## 6  2012-10-06       15420
## 7  2012-10-07       11015
## 8  2012-10-08       10641
## 9  2012-10-09       12811
## 10 2012-10-10        9900
## 11 2012-10-11       10304
## 12 2012-10-12       17382
## 13 2012-10-13       12426
## 14 2012-10-14       15098
## 15 2012-10-15       10139
## 16 2012-10-16       15084
## 17 2012-10-17       13452
## 18 2012-10-18       10056
## 19 2012-10-19       11829
## 20 2012-10-20       10395
## 21 2012-10-21        8821
## 22 2012-10-22       13460
## 23 2012-10-23        8918
## 24 2012-10-24        8355
## 25 2012-10-25        2492
## 26 2012-10-26        6778
## 27 2012-10-27       10119
## 28 2012-10-28       11458
## 29 2012-10-29        5018
## 30 2012-10-30        9819
## 31 2012-10-31       15414
## 32 2012-11-01       10641
## 33 2012-11-02       10600
## 34 2012-11-03       10571
## 35 2012-11-04       10641
## 36 2012-11-05       10439
## 37 2012-11-06        8334
## 38 2012-11-07       12883
## 39 2012-11-08        3219
## 40 2012-11-09       10641
## 41 2012-11-10       10641
## 42 2012-11-11       12608
## 43 2012-11-12       10765
## 44 2012-11-13        7336
## 45 2012-11-14       10641
## 46 2012-11-15          41
## 47 2012-11-16        5441
## 48 2012-11-17       14339
## 49 2012-11-18       15110
## 50 2012-11-19        8841
## 51 2012-11-20        4472
## 52 2012-11-21       12787
## 53 2012-11-22       20427
## 54 2012-11-23       21194
## 55 2012-11-24       14478
## 56 2012-11-25       11834
## 57 2012-11-26       11162
## 58 2012-11-27       13646
## 59 2012-11-28       10183
## 60 2012-11-29        7047
## 61 2012-11-30       10641
```

```r
# histogram of the total number of steps taken each day
hist(new.total.daily.steps$steps.total)
```

![plot of chunk unnamed-chunk-4](figure/unnamed-chunk-4.png) 

```r
# Calculate and report the mean and median total number of steps taken per day
new.mean.daily.steps <- aggregate(raw.data$steps, by=list(raw.data$date), FUN=mean)
names(new.mean.daily.steps) <- c("date", "steps.mean")
new.mean.daily.steps
```

```
##          date steps.mean
## 1  2012-10-01    36.9479
## 2  2012-10-02     0.4375
## 3  2012-10-03    39.4167
## 4  2012-10-04    42.0694
## 5  2012-10-05    46.1597
## 6  2012-10-06    53.5417
## 7  2012-10-07    38.2465
## 8  2012-10-08    36.9479
## 9  2012-10-09    44.4826
## 10 2012-10-10    34.3750
## 11 2012-10-11    35.7778
## 12 2012-10-12    60.3542
## 13 2012-10-13    43.1458
## 14 2012-10-14    52.4236
## 15 2012-10-15    35.2049
## 16 2012-10-16    52.3750
## 17 2012-10-17    46.7083
## 18 2012-10-18    34.9167
## 19 2012-10-19    41.0729
## 20 2012-10-20    36.0938
## 21 2012-10-21    30.6285
## 22 2012-10-22    46.7361
## 23 2012-10-23    30.9653
## 24 2012-10-24    29.0104
## 25 2012-10-25     8.6528
## 26 2012-10-26    23.5347
## 27 2012-10-27    35.1354
## 28 2012-10-28    39.7847
## 29 2012-10-29    17.4236
## 30 2012-10-30    34.0938
## 31 2012-10-31    53.5208
## 32 2012-11-01    36.9479
## 33 2012-11-02    36.8056
## 34 2012-11-03    36.7049
## 35 2012-11-04    36.9479
## 36 2012-11-05    36.2465
## 37 2012-11-06    28.9375
## 38 2012-11-07    44.7326
## 39 2012-11-08    11.1771
## 40 2012-11-09    36.9479
## 41 2012-11-10    36.9479
## 42 2012-11-11    43.7778
## 43 2012-11-12    37.3785
## 44 2012-11-13    25.4722
## 45 2012-11-14    36.9479
## 46 2012-11-15     0.1424
## 47 2012-11-16    18.8924
## 48 2012-11-17    49.7882
## 49 2012-11-18    52.4653
## 50 2012-11-19    30.6979
## 51 2012-11-20    15.5278
## 52 2012-11-21    44.3993
## 53 2012-11-22    70.9271
## 54 2012-11-23    73.5903
## 55 2012-11-24    50.2708
## 56 2012-11-25    41.0903
## 57 2012-11-26    38.7569
## 58 2012-11-27    47.3819
## 59 2012-11-28    35.3576
## 60 2012-11-29    24.4688
## 61 2012-11-30    36.9479
```

```r
new.median.daily.steps <- aggregate(raw.data$steps, by=list(raw.data$date), FUN=median)
names(new.median.daily.steps) <- c("date", "steps.median")
new.median.daily.steps
```

```
##          date steps.median
## 1  2012-10-01         33.5
## 2  2012-10-02          0.0
## 3  2012-10-03          0.0
## 4  2012-10-04          0.0
## 5  2012-10-05          0.0
## 6  2012-10-06          0.0
## 7  2012-10-07          0.0
## 8  2012-10-08         33.5
## 9  2012-10-09          0.0
## 10 2012-10-10          0.0
## 11 2012-10-11          0.0
## 12 2012-10-12          0.0
## 13 2012-10-13          0.0
## 14 2012-10-14          0.0
## 15 2012-10-15          0.0
## 16 2012-10-16          0.0
## 17 2012-10-17          0.0
## 18 2012-10-18          0.0
## 19 2012-10-19          0.0
## 20 2012-10-20          0.0
## 21 2012-10-21          0.0
## 22 2012-10-22          0.0
## 23 2012-10-23          0.0
## 24 2012-10-24          0.0
## 25 2012-10-25          0.0
## 26 2012-10-26          0.0
## 27 2012-10-27          0.0
## 28 2012-10-28          0.0
## 29 2012-10-29          0.0
## 30 2012-10-30          0.0
## 31 2012-10-31          0.0
## 32 2012-11-01         33.5
## 33 2012-11-02          0.0
## 34 2012-11-03          0.0
## 35 2012-11-04         33.5
## 36 2012-11-05          0.0
## 37 2012-11-06          0.0
## 38 2012-11-07          0.0
## 39 2012-11-08          0.0
## 40 2012-11-09         33.5
## 41 2012-11-10         33.5
## 42 2012-11-11          0.0
## 43 2012-11-12          0.0
## 44 2012-11-13          0.0
## 45 2012-11-14         33.5
## 46 2012-11-15          0.0
## 47 2012-11-16          0.0
## 48 2012-11-17          0.0
## 49 2012-11-18          0.0
## 50 2012-11-19          0.0
## 51 2012-11-20          0.0
## 52 2012-11-21          0.0
## 53 2012-11-22          0.0
## 54 2012-11-23          0.0
## 55 2012-11-24          0.0
## 56 2012-11-25          0.0
## 57 2012-11-26          0.0
## 58 2012-11-27          0.0
## 59 2012-11-28          0.0
## 60 2012-11-29          0.0
## 61 2012-11-30         33.5
```


## Are there differences in activity patterns between weekdays and weekends?

```r
raw.data$weekday <- weekdays(raw.data$date)
raw.data[which(raw.data$weekday=="Sunday" | raw.data$weekday=="Saturday"), "weekday"] <- "weekend"
raw.data[which(raw.data$weekday!="weekend"), "weekday"] <- "weekday"
raw.data$weekday <- as.factor(raw.data$weekday)

weekday.raw.data <- raw.data[raw.data$weekday == "weekday", ]
weekend.raw.data <- raw.data[raw.data$weekday != "weekday", ]

pattern.weekday.steps <- aggregate(weekday.raw.data$steps, by=list(weekday.raw.data$interval), FUN=mean)
names(pattern.weekday.steps) <- c("interval", "steps.mean")
pattern.weekend.steps <- aggregate(weekend.raw.data$steps, by=list(weekend.raw.data$interval), FUN=mean)
names(pattern.weekend.steps) <- c("interval", "steps.mean")

# Make a time series plot of the 5-minute interval (x-axis) and the average number of steps taken, averaged across all days (y-axis) for both weekday & weekend

par(mfrow=c(2,1), mar=c(2,2,2,2))
plot(pattern.weekday.steps$interval, pattern.weekday.steps$steps.mean, type="l", main="weekday")
plot(pattern.weekend.steps$interval, pattern.weekend.steps$steps.mean, type="l", main="weekend")
```

![plot of chunk unnamed-chunk-5](figure/unnamed-chunk-5.png) 
