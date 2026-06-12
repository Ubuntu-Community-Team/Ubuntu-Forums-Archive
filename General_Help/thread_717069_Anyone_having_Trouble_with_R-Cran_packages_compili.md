---
title: "Anyone having Trouble with R-Cran packages compiling?"
date: 2008-03-06
forum: General Help
---

### Post by Jaffar on 2008-03-06
I have searched two days in www, but i didn't find a hint for this strange errors.

First my system is an Ubuntu Gutsy. Whenever i install a package for the statistical language
R (2.6.2)  i get this error:

* Installing *source* package 'cluster' ...
** libs
cd: 1: can't cd to src
WARNING: no source files found
chmod: Zugriff auf „/home/ghost/R/i486-pc-linux-gnu-library/2.6/cluster/libs/*“ nicht möglich: No such file or directory
/bin/sed: kann DESCRIPTION nicht lesen: No such file or directory
/bin/sed: kann DESCRIPTION nicht lesen: No such file or directory
No man pages found in package 'cluster'
** building package indices ...
* DONE (cluster)

Some packages work correctly, others not. Inside the packages there is the src folder with source files
and the other folder ('home/ghost...../libs") exists.

So has anyone an idea whats the problem with my ##+# system? I need bioconductor 2.1
working and i don't want to switch back to windows...

here another package:
* Installing *source* package 'pvclust' ...
** R
** data
** help
 >>> Building/Updating help pages for package 'pvclust'
     Formats: text html latex example 
Note: unmatched right brace in 'lung' on or after line 8
  lung                              text    html    latex   example
  msfit                             text    html    latex
  msplot                            text    html    latex
  plot.pvclust                      text    html    latex
  print.pvclust                     text    html    latex
  pvclust                           text    html    latex   example
  pvpick                            text    html    latex
  seplot                            text    html    latex
** building package indices ...
* DONE (pvclust)

working. What is the difference? Is there are missing depencies?

Thanks in advance for every little clue. Hope i can sleep (thinking the whole night about this damn problem)

---

### Post by MsShellman on 2008-04-01
Actually, I also can't install anything from Bioconductor, but random CRAN packages work.  I get the following message when I try to install the 'biomaRt' package:

>     source("http://bioconductor.org/biocLite.R")
Warning messages:
1: In safeSource() : Redefining ‘biocinstall’
2: In safeSource() : Redefining ‘biocinstallPkgGroups’
3: In safeSource() : Redefining ‘biocinstallRepos’

>     biocLite("biomaRt")
Running biocinstall version 2.1.11 with R version 2.6.2 
Your version of R requires version 2.1 of BioConductor.
Warning in install.packages(pkgs = pkgs, repos = repos, dependencies = dependencies,  :
  argument 'lib' is missing: using '/usr/local/lib/R/site-library'
also installing the dependencies ‘RCurl’, ‘XML’

trying URL 'http://bioconductor.org/packages/2.1/extra/src/contrib/RCurl_0.8-3.tar.gz'
Content type 'application/x-gzip' length 218153 bytes (213 Kb)
opened URL
==================================================
downloaded 213 Kb

trying URL 'http://cran.fhcrc.org/src/contrib/XML_1.93-2.tar.gz'
Content type 'application/x-gzip' length 870234 bytes (849 Kb)
opened URL
==================================================
downloaded 849 Kb

trying URL 'http://bioconductor.org/packages/2.1/bioc/src/contrib/biomaRt_1.12.2.tar.gz'
Content type 'application/x-gzip' length 276683 bytes (270 Kb)
opened URL
==================================================
downloaded 270 Kb

* Installing *source* package 'RCurl' ...
checking for curl-config... no
Cannot find curl-config
ERROR: configuration failed for package 'RCurl'
** Removing '/usr/local/lib/R/site-library/RCurl'
* Installing *source* package 'XML' ...
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ISO C89... none needed
checking how to run the C preprocessor... gcc -E
checking for sed... /bin/sed
checking for xml2-config... no
Cannot find xml2-config
ERROR: configuration failed for package 'XML'
** Removing '/usr/local/lib/R/site-library/XML'
* Installing *source* package 'biomaRt' ...
** R
** inst
** preparing package for lazy loading
Loading required package: RCurl
Warning in library(pkg, character.only = TRUE, logical.return = TRUE, lib.loc = lib.loc) :
  there is no package called 'RCurl'
Error: package 'RCurl' could not be loaded
Execution halted
ERROR: lazy loading failed for package 'biomaRt'
** Removing '/usr/local/lib/R/site-library/biomaRt'

The downloaded packages are in
        /tmp/RtmpmDdMiV/downloaded_packages
Warning messages:
1: In install.packages(pkgs = pkgs, repos = repos, dependencies = dependencies,  :
  installation of package 'RCurl' had non-zero exit status
2: In install.packages(pkgs = pkgs, repos = repos, dependencies = dependencies,  :
  installation of package 'XML' had non-zero exit status
3: In install.packages(pkgs = pkgs, repos = repos, dependencies = dependencies,  :
  installation of package 'biomaRt' had non-zero exit status

I've updated gcc and installed gfortran and done other random things that people have tried in other forum posts, but I cannot get any bioconductor packages to install.  It's actually really frustrating because it means I can't do any work on my home computer.

Any help would be awesome.

---

### Post by Rainbow Jeremy on 2008-04-05
I had the same problem when I tried installing various packages.  Try this, as it worked for me:

sudo apt-get install r-base-dev

After you have installed this, then open R using the "sudo R" command.  Then you can "install.packages('package-name')" and it should work.  It did for me.

---

### Post by MsShellman on 2008-04-05
Ohhh, well I don't know why, but that fixed my problems with Bioconductor packages.  Thanks!

---

### Post by Carambakaracho on 2008-06-19
> **Rainbow Jeremy said:**
> sudo apt-get install r-base-dev

After you have installed this, then open R using the "sudo R" command.  Then you can "install.packages('package-name')" and it should work.  It did for me.

So did it for me though I'm running Hardy. Thanks.

In fact a lot of dependecies are additionally installed, it's rather due to them that ```
sudo R
``` works with the >install.packages() and >bioclite() commands than the dev package

---

### Post by MSBF on 2008-07-15
Any other ideas? It looks as if it's not installing Rcurl, XML and Biomart

---

### Post by MSBF on 2008-07-21
Installing libxml2-dev seemed to help.

---

