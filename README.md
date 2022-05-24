# RegressionAndOtherStories.jl v0.3.3

| **Project Status**          |  **Build Status** |
|:---------------------------:|:-----------------:|
|![][project-status-img] | ![][CI-build] |

[CI-build]: https://github.com/stanjulia/StanSample.jl/workflows/CI/badge.svg?branch=master

[issues-url]: https://github.com/stanjulia/ROSbase.jl/issues

[project-status-img]: https://img.shields.io/badge/lifecycle-experimental-orange.svg

## Purpose (once completed, maybe late 2022)

RegressionAndOtherStories.jl contains supporting (Julia) functions and the data files used in ["Regression and Other Stories"](https://avehtari.github.io/ROS-Examples/) by Andrew Gelham, Jennifer Hill and Aki Vehtari.



## Contents

The **supporting functions** are intended to be used in (currently) 2 Julia projects (also under development), ROSStanPluto.jl and ROSTuringPluto.jl.
See the lists of exported and not exported funtiens at the end of this file.

All **data files** are in `.csv` format and located in the `data` directory.

If RegressionAndOtherStories.jl is loaded, the files can be read in as a DataFrame using:
```
hibbs = CSV.read(ros_datadir("ElectionsEconomy", "hibbs.csv"), DataFrame)
```

For that purpose `ros_datadir()` is exported.

If needed, Stata files (`.dat`) have been converted to `.csv` files using the scripts in the `scripts` directory, e.g. see `scripts\hdi.jl`. To access the Stata files in the R package `ROS-Examples` RegressionAndOtherStories.jl expects the environment variable `JULIA_ROS_HOME` to be defined, e.g.:
```
ENV["JULIA_ROS_HOME"] = expanduser("~/Projects/R/ROS-Examples")
```

R itself does not necessarily need to be installed for this to work. The ROS-Examples package can be found [here](https://github.com/avehtari/ROS-Examples).

If so desired, direct use of the Stata files is also possible as the Stata to .csv file conversion scripts mentioned above show.

## Approach

The initial approach I attempted in RegressionAndOtherStories.jl (v0,2) and associated projects was different from StatisticalRethinking.jl. But that approach did not work out as I expected, so I will switch to a similiar setup as in StatisticalRethinking.jl using Requires.jl from v0.3 onwards. 

In particular Turing, Stan, Makie and AlgebraOfGraphics, if needed, will all be included using Requires.jl.

Over time I might minimize the use of AlgebraOfGraphics.jl. It is a nice package but also a bit more difficult to tailor (compared to Makie/GLMakie).

For testing puposes the packages enabled using Requires.jl will move to the test section of RegrassionAndOtherStories.jl.

In doing this I will move over several important functions from StatisticalRethinking.jl as well, e.g. `link()`.

I expect I can use ParetoSmoothedImportanceSampling.jl and StructuralCausalModels.jl as is.

## Issues, comments and questions

Please file issues, comments and questions [here](https://github.com/stanjulia/ROSbase.jl/issues).

Pull requests are also welcome.

## Versions

### Version 0.3.3

1. Add initial version of notebook maintenance routines.
2. Tag this version (if not done by TagBot)

### Version 0.3.2

1. Fix Makie and AoG glue scripts.

### Version 0.3.1

1. StatsFuns compat entry to 1.0.

### Version 0.3.0 (under development)

1. Switch back to using Requires.jl
2. Switch to using `eachindex()` where appropriate.
3. Experimental versions for chapter 3.

### Version 0.2.4

1. Chapter 2 mostly done
2. Added trankplot function

### Version 0.2.0

1. Support for the 5 examples from chapter 1 done.
2. Added plot_chains() and model_summary() functions.
3. Added Makie and AlgebraOfGraphics as dependencies.

Note: Source files for Makie/AoG are all in src/Makie/ to simplify moving those to a separate repo (not my intention right now, but still).

4. In sync with both ROS[Turing|Stan]Pluto projects tagged 2.3 and up.

### Version 0.1.0

1. Initial commit (to registrate the package for usage in projects).

## References

Of course this package is focused on:

0. [Gelman, Hill, Vehtari: Regression and Other Stories](https://www.cambridge.org/highereducation/books/regression-and-other-stories/DD20DD6C9057118581076E54E40C372C#overview)

which in a sense is a major update to item 3. below.

There is no shortage of other good books on Bayesian statistics. A few of my favorites are:

1. [Bolstad: Introduction to Bayesian statistics](http://www.wiley.com/WileyCDA/WileyTitle/productCd-1118593227.html)

2. [Bolstad: Understanding Computational Bayesian Statistics](http://www.wiley.com/WileyCDA/WileyTitle/productCd-0470046090.html)

3. [Gelman, Hill: Data Analysis Using Regression and Multilevel/Hierarchical Models](http://www.stat.columbia.edu/~gelman/arm/)

4. [McElreath: Statistical Rethinking](http://xcelab.net/rm/statistical-rethinking/)

5. [Kruschke: Doing Bayesian Data Analysis](https://sites.google.com/site/doingbayesiandataanalysis/what-s-new-in-2nd-ed)

6. [Lee, Wagenmakers: Bayesian Cognitive Modeling](https://www.cambridge.org/us/academic/subjects/psychology/psychology-research-methods-and-statistics/bayesian-cognitive-modeling-practical-course?format=PB&isbn=9781107603578)

7. [Betancourt: A Conceptual Introduction to Hamiltonian Monte Carlo](https://arxiv.org/abs/1701.02434)

8. [Gelman, Carlin, and others: Bayesian Data Analysis](http://www.stat.columbia.edu/~gelman/book/)

9. [Pearl, Glymour, Jewell: Causal Inference in Statistics: A Primer](https://www.wiley.com/en-us/Causal+Inference+in+Statistics%3A+A+Primer-p-9781119186847)

10. [Pearl, Judea and MacKenzie, Dana: The Book of Why](https://www.basicbooks.com/titles/judea-pearl/the-book-of-why/9780465097616/)

11. [Scott Cunningham: Causal Inference - the mixtapes](https://mixtape.scunning.com)

A good book to understand most of the Julia constructs used in this book is:

12. [Bogumił Kamiński: Julia for Data Analysis](https://www.manning.com/books/julia-for-data-analysis).

## Functions defined in this package:

### Currently (v0.3.0) exported functions (see online help)

1. ros_path
2. ros_data
3. ros_datadir
4. plot_chains
5. model_summary
6. trankplot


### Currently not exported functions (see online help)

1. rank_vector
2. bin_vector

All documentation is on-line.
