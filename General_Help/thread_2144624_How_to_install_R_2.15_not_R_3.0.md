---
title: "How to install R 2.15 not R 3.0"
date: 2013-05-12
forum: General Help
---

### Post by TheItinerantSon on 2013-05-12
Hi,

I am using ubuntu server 12.04 and I need R 2.15 not R 3.0 (for Shiny).

I tried to install initially by using

# Install R
sudo add-apt-repository 'deb [http://cran.rstudio.com/bin/linux/ubuntu](http://cran.rstudio.com/bin/linux/ubuntu) precise/'
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys E084DAB9
sudo apt-get update
sudo apt-get install r-base r-base-dev


But this yields R 3.0

I tried to change the repository in sources from whats above to deb [http://cran.case.edu/bin/linux/debian](http://cran.case.edu/bin/linux/debian) squeeze-cran/ 
but that doesn't work at all.

I've tried to research 'pinning' R to version 2.15 but i dont understand how to define the package or pin in the  should put in the /etc/apt/preferences file.

Any suggestions?

---

### Post by TheItinerantSon on 2013-05-13
ok figured it out...

in case anyone else has this issue this is whati used (probably not the most elegant) but it works

sudo cd /usr/local
sudo mkdir R
sudo wget [http://cran.r-project.org/bin/linux/ubuntu/precise/r-base_2.15.3.orig.tar.gz](http://cran.r-project.org/bin/linux/ubuntu/precise/r-base_2.15.3.orig.tar.gz) 
sudo tar zxvf r-base_2.15.3.orig.tar.gz
cd R-2.15.3/
sudo apt-get install tk-dev gcc gfortran texlive texlive-fonts-extra libreadline-dev xorg-dev libxml2-dev libcurl4-gnutls-dev
sudo ./configure
sudo make
sudo make check
sudo make install

---

