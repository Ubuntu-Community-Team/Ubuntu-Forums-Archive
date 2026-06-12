---
title: "installing RStudio greater than v2.14.1"
date: 2015-02-02
forum: General Help
---

### Post by redserpent on 2015-02-02
Hi:
 Am taking a class through edX (PH525.1x) About using [R (Statistical programming Language)]("http://en.wikipedia.org/wiki/R_%28programming_language%29") for life sciences. It is essential for the class to install RStudio(IDE) with the 'devtools' package.
 IDE (RStudio): [http://www.rstudio.com/](http://www.rstudio.com/) 
 Class:  [https://courses.edx.org/courses/HarvardX/PH525.1x/1T2015/courseware/2273065cc0f649b69c1240a58f7ab080/77c6a41ee38544c28d2d95ef7889cdb8/#](https://courses.edx.org/courses/HarvardX/PH525.1x/1T2015/courseware/2273065cc0f649b69c1240a58f7ab080/77c6a41ee38544c28d2d95ef7889cdb8/#) 
>** install.packages("devtools")**
I get an error:[COLOR=#ff0000]* Warning in install.packages :   package &#8216;devtools&#8217; is not available (for R version 2.14.1)*[/COLOR]
  The installation of this package "devtools" is essential for the class. 
**Is it possible to download a free version of RStudio (greater than 2.14.1), for Ubuntu?**
The only free version i have been able to find is [http://www.rstudio.com/products/rstudio/download/](http://www.rstudio.com/products/rstudio/download/) 
My system is: HPmini (laptop Intel® Atom&#8482; &#956;Processor CPU N455 @ 1.66GHz) Ubuntu 12.04LTS
) / Ubuntu 
When checking my current version of RStudio under the help/Abiut RStudio menu I get: RStudio Version 0.98.1091 &#8211; © 2009-2014 RStudio, ??

Thank you in advance for any insight.

---

### Post by ptn107 on 2015-02-02
The newest R studio is 0.98.1091.  What you want is the newest version of "R" which is 3.1.2.  Ubuntu 12.04 LTS repositories only have 2.14.1.  So you need to get the newest version directly.

Add this repository to your */etc/apt/sources.list* file (or make a file like */etc/apt/sources.list.d/r-cran.list*)
```
deb http://cran.rstudio.com/bin/linux/ubuntu precise/
```
then add the key
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
```
and then
```
sudo apt-get update; sudo apt-get install r-base
```

---

