---
title: "Can't install R (r-base) on 14.04"
date: 2016-03-23
forum: General Help
---

### Post by smrz14 on 2016-03-23
I'm unable to install R on an up to date Ubuntu 14.04 system.

I have added[INDENT]deb [http://stat.ethz.ch/CRAN/bin/linux/ubuntu](http://stat.ethz.ch/CRAN/bin/linux/ubuntu) trusty/

[/INDENT]
to sources.list and run apt-get update with no errors.

When I run[INDENT]apt-get install r-base 
[/INDENT]

I get```
[INDENT]Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 r-base : Depends: r-base-core (>= 3.2.4-revised-1trusty0) but it is not going to be installed
          Depends: r-recommended (= 3.2.4-revised-1trusty0) but it is not going to be installed
          Recommends: r-base-html but it is not going to be installed
 r-base-dev : Depends: r-base-core (>= 3.2.4-revised-1trusty0) but it is not going to be installed
              Depends: gfortran but it is not going to be installed
              Depends: liblapack-dev but it is not going to be installed or
                       libatlas-base-dev but it is not installable
E: Unable to correct problems, you have held broken packages.
[/INDENT]

```
Does anyone have any idea how to fix this?   I've  found references to this problems via google but the solutions suggested are exactly what I've already tried.

thanks

---

### Post by mörgæs on 2016-03-23
> **smrz14 said:**
> ...and run apt-get update with no errors.



What about ```
sudo apt-get dist-upgrade
```?

---

### Post by smrz14 on 2016-03-23
I've tried upgrade and dist-upgrade and still get exactly the same error message.

I've also tried aptitude install and using synaptic.  Both reported problems they could not resolve.

---

### Post by mörgæs on 2016-03-23
Please post the error messages (and use CODE tags).

---

### Post by slickymaster on 2016-03-23
*Moved to the ***General Help*** sub-forum*

---

### Post by smrz14 on 2016-03-23
Using aptitude:

```

root@bwud:/home/moi# aptitude install r-base
The following NEW packages will be installed:
  cdbs{a} dh-translations{a} gfortran{a} gfortran-4.8{ab} libblas-dev{a} libblas3{a} libbz2-dev{a} libgfortran-4.8-dev{ab} libgfortran3{ab} 
  libjpeg-dev{a} libjpeg-turbo8-dev{a} libjpeg8-dev{a} liblapack-dev{a} liblapack3{a} liblzma-dev{a} libncurses5-dev{a} libpcre3-dev{a} 
  libpcrecpp0{a} libpng12-dev{a} libreadline-dev{a} libreadline6-dev{a} libtinfo-dev{a} python-scour{a} r-base r-base-core{a} r-base-dev{a} 
  r-base-html{a} r-cran-boot{a} r-cran-class{a} r-cran-cluster{a} r-cran-codetools{a} r-cran-foreign{a} r-cran-kernsmooth{a} 
  r-cran-lattice{a} r-cran-mass{a} r-cran-matrix{a} r-cran-mgcv{a} r-cran-nlme{a} r-cran-nnet{a} r-cran-rpart{a} r-cran-spatial{a} 
  r-cran-survival{a} r-doc-html{a} r-recommended{a} zlib1g-dev{a} 
0 packages upgraded, 45 newly installed, 0 to remove and 0 not upgraded.
Need to get 47.8 MB of archives. After unpacking 105 MB will be used.
The following packages have unmet dependencies:
 gfortran-4.8 : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.1 is installed.
                Depends: gcc-4.8 (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.1 is installed.
 libgfortran3 : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.1 is installed.
 libgfortran-4.8-dev : Depends: gcc-4.8-base (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.1 is installed.
                       Depends: libgcc-4.8-dev (= 4.8.2-19ubuntu1) but 4.8.4-2ubuntu1~14.04.1 is installed.
The following actions will resolve these dependencies:

      Keep the following packages at their current version:
1)      gfortran [Not Installed]                           
2)      gfortran-4.8 [Not Installed]                       
3)      libgfortran-4.8-dev [Not Installed]                
4)      libgfortran3 [Not Installed]                       
5)      liblapack-dev [Not Installed]                      
6)      liblapack3 [Not Installed]                         
7)      r-base [Not Installed]                             
8)      r-base-core [Not Installed]                        
9)      r-base-dev [Not Installed]                         
10)     r-base-html [Not Installed]                        
11)     r-cran-boot [Not Installed]                        
12)     r-cran-class [Not Installed]                       
13)     r-cran-cluster [Not Installed]                     
14)     r-cran-codetools [Not Installed]                   
15)     r-cran-foreign [Not Installed]                     
16)     r-cran-kernsmooth [Not Installed]                  
17)     r-cran-lattice [Not Installed]                     
18)     r-cran-mass [Not Installed]                        
19)     r-cran-matrix [Not Installed]                      
20)     r-cran-mgcv [Not Installed]                        
21)     r-cran-nlme [Not Installed]                        
22)     r-cran-nnet [Not Installed]                        
23)     r-cran-rpart [Not Installed]                       
24)     r-cran-spatial [Not Installed]                     
25)     r-cran-survival [Not Installed]                    
26)     r-recommended [Not Installed]                      



Accept this solution? [Y/n/q/?] Y
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B of archives. After unpacking 0 B will be used.

```

---

### Post by dragonfly41 on 2016-03-23
You could try installing r-cran-cmdr .. the GUI for R

r-cran-cmdr dependencies include r-base-core (>=3.0.2-1ubuntu1)

I'm using Synaptic Package Manager to inspect all package installations on Ubuntu 14.04.

---

### Post by smrz14 on 2016-03-23
What repositories are you using?  On my system, Synaptic does not list r-cran-cmdr.

---

### Post by dragonfly41 on 2016-03-23
I installed **rcmdr** via Ubuntu Software Centre.

[Later edit]

Further read here ... 

[http://biostat.mc.vanderbilt.edu/wiki/pub/Main/TheresaScott/How.to.Install.pdf](http://biostat.mc.vanderbilt.edu/wiki/pub/Main/TheresaScott/How.to.Install.pdf)

[http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/installation-notes.html](http://socserv.mcmaster.ca/jfox/Misc/Rcmdr/installation-notes.html)

---

### Post by smrz14 on 2016-03-23
I tried to install rcmdr using the Ubuntu Software Center and got the following error:

```

r-cran-rcmdr: Depends: libc6 (>= 2.2.5) but 2.19-0ubuntu6.7 is to be installed
              Depends: r-base-core (>= 3.0.2-1ubuntu1) but 3.2.4-revised-1trusty0 is to be installed
              Depends: r-cran-car (>= 2.0-15-1) but 2.0-19-1 is to be installed
              Depends: r-cran-sm (>= 2.0.12-2) but 2.2-5.4-1 is to be installed

```

Does this mean that something installed on my system is too new for R?

---

### Post by mörgæs on 2016-03-23
Have you tried 
```
sudo dpkg --configure -a
sudo apt-get install -f

```?

---

### Post by dragonfly41 on 2016-03-23
This is a puzzle since I have Ubuntu 14.04 (32bit) as I understand you have.

I suggest that you first install Synaptic Package Manager since you can then inspect state of packages.
See thumbnail below.

I've browsed through Synaptic Package Manager and see these installed (search)

libc6 .. installed version 2.19-0ubuntu6.7
r-base-core .. installed version 3.0.2-1ubuntu1
r-cran-car .. installed version 2.0-19.1
r-cran-sm .. installed version 2.2-5.4-1

Now as one of the installation papers posted earlier suggests

> Therefore, in order to be able to use the R Commander, you must install both R and the R
Commander on your computer.

It seems that you might need to install R in full before you can install R Commander.
Attached is a snapshot of my Synaptic Package Manager search ..

---

