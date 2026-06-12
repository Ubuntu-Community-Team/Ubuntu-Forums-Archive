---
title: "Problems installing packages in R Studio"
date: 2021-01-10
forum: General Help
---

### Post by rhelpleeeaaasee on 2021-01-10
Hello everyone,

I see that many people have written about similar topics but after struggling for more than two days with this now I resort to writing a post about it and asking for help. 

I am trying to install the "car" package in RStudio. I have Ubuntu 20.04 and R version 3.6.3 (2020-02-29).

I tried many different things including reinstalling R and RStudio.

The last try gave me the following error messages after i ran install.packages("car"):

1: In utils::install.packages("pbkrtest", repos = "https://cloud.r-project.org") :
  installation of package ‘RcppEigen’ had non-zero exit status
2: In utils::install.packages("pbkrtest", repos = "https://cloud.r-project.org") :
  installation of package ‘lme4’ had non-zero exit status
3: In utils::install.packages("pbkrtest", repos = "https://cloud.r-project.org") :
  installation of package ‘pbkrtest’ had non-zero exit status
4: In utils::install.packages("lme4", repos = "https://cloud.r-project.org") :
  installation of package ‘RcppEigen’ had non-zero exit status
5: In utils::install.packages("lme4", repos = "https://cloud.r-project.org") :
  installation of package ‘lme4’ had non-zero exit status
6: In utils::install.packages("car", repos = "https://cloud.r-project.org") :
  installation of package ‘RcppEigen’ had non-zero exit status
7: In utils::install.packages("car", repos = "https://cloud.r-project.org") :
  installation of package ‘lme4’ had non-zero exit status
8: In utils::install.packages("car", repos = "https://cloud.r-project.org") :
  installation of package ‘pbkrtest’ had non-zero exit status
9: In utils::install.packages("car", repos = "https://cloud.r-project.org") :
  installation of package ‘car’ had non-zero exit status


I would be very grateful for any help.

---

