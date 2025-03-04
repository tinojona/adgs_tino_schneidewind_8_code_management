# 8 Code Management

This repository is where worked through the exercises for Session 8 of ADGS1.

## Structure

The structure of the template follows the structure of an R package without
actually being one. There are several reasons for this.

- Familiarizes you with an R package structure
  - allowing for an optional switch to an R package
- Avoids top level aggregation of data, code and reporting files
- Splits the dynamic reporting from academic writing (`vignettes` vs. `manuscript`)
- Splits pre-processing of data from working / included data (`data-raw` vs. `data`)
- Splits R code from other scripts (bash / python in `src`)
- Splits R functions from R analysis scripts (`R` vs `analysis`)

Below you find a comprehensive list of what goes where an why, as well as some
best practices on how to structure further data within these folders.

### The R folder

The `R` folder contains R functions, not scripts. This means code wrapped in a
structure as such

### The src folder

The `src` folder contains scripts and code which is not R related, in packages
this folder often contains Fortran or C code which needs to be compiled. Here,
it is common to store bash or python functions which might assist in data
cleaning or data gathering which can't be done in R alone.

### The data-raw folder

The `data-raw` folder contains, as the name suggests, raw data and the scripts
to download and pre-process the data. This is data which requires significant
pre-processing to be of use in analysis. In other words, this data is not 
analysis ready (within the context of the project).

### The data folder

The `data` folder contains analysis ready data. This is data which you can use,
as is. This often contains the output of a `data-raw` pre-processing workflow,
but can also include data which doesn't require any intervention, e.g. a land
cover map which is used as-is. 

### The analysis folder

The `analysis` folder contains, *surprise*, R scripts covering analysis of your
analysis ready data (in the `data` folder). These are R scripts with output
which is limited to numbers, tables and figures. It should not include R
markdown code!


### The manuscript folder

The `manuscript` folder contains a true working document often written in an 
external word processing software. It also, at times, contain the output of 
any analysis script, such as tables and rendered figures.


### The vignettes folder

The `vignettes` folder contains dynamic notebooks, i.e. R markdown files. These
might serve a dual use between analysis and manuscript. However, the use case
in reality should be considered very narrowly. In general, as they are commonly
used, R markdown files are rarely portable.
