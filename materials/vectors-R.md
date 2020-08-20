---
layout: page
element: notes
title: Vectors
language: R
--- 

### Vectors Basics

* Remember that all values in R have a type
* A vector is a sequence of values that all have the same type
* Create using the `c()` function, which stands for "combine"

```
sites <- c("a", "a", "b", "c")
```

* Using the `str` function we learned last time shows that this is a vector of 4 character strings 

```
str(sites)
```

* Select pieces of a vector by slicing the vector (like slicing a pizza)
* Use square brackets `[]`
* In general `[]` in R means, "give me a piece of something"
* `sites[1]` gives us the first value in the vector
* `sites[1:3]` gives us the first through the third values
* `1:3` works by makeing a vector of the whole numbers 1 through 3.
* So, this is the same as `sites[1:3]` is the same as `sites[c(1, 2, 3)]` 
* You can use a vector to get any subset or order you want `sites[c(4, 1, 3)]`

* Many functions in R take a vector as input and return a value
* This includes the function `length` which determines how many items are in a vector

```
length(sites)
```

* We can also calculate common summary statistics
* For example, if we have a vector of population densities

```
density <- c(2.8, 3.2, 1.5, 3.8)
mean(density)
max(density)
min(density)
sum(density)
```

> Do [Basic Vectors]({{ site.baseurl }}/exercises/Vectors-basic-vectors-R/).

### Null values

* So far we've worked with data with no missing values
* How many of you have missing values in your data?
* Missing or "null" values written in R as `NA`

```
density <- c(2.8, 3.2, 1.5, NA)
mean(density)
```

* Why did we get `NA`?
    * Hard to say what a calculation including `NA` should be
    * So most calculations return `NA` when `NA` is in the data
* Can tell many functions to remove the `NA` before calculating

```
mean(density, na.rm = TRUE)
```

> Do [Nulls in Vectors]({{ site.baseurl }}/exercises/Vectors-nulls-in-vectors-R/).

### Working with multiple vectors

#### Vector math

* Vector math combines values in the same position
* Element-wise: operating on one element at a time

```
density <- c(2.8, 3.2, 1.5, 3.8)
area <- c(3, 5, 1.9, 2.7)
total_number <- density * area
```

#### Filtering

* Subsetting or "filtering" is done using `[]`, like slicing
* The `[]` say "give me a piece of something"
* Selects parts of vectors based on "conditions" not position
* Get the area values for site a

```r
area[sites == 'a']
```

* `==` means "equal to" in most languages.
* Not `=`. `=` is used for assignment.

* Can also do "not equal to"

```r
area[sites != 'a']
```

* Numerical comparisons like greater or less than
* Select sites that meet some area condition

```r
sites[area > 3]
sites[area >= 3]
sites[area < 3]
```

* Can subset a vector based on itself

```r
sites[sites != 'a']
```

> Do [Shrub Volume Vectors 1-3]({{ site.baseurl }}/exercises/Vectors-shrub-volume-vectors-R/).