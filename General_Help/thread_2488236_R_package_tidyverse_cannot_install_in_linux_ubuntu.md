---
title: "R package tidyverse cannot install in linux ubuntu 22.04.2"
date: 2023-06-28
forum: General Help
---

### Post by hchen7 on 2023-06-28
Hi,

Like I mentioned in the title, the tidyverse package cannot be installed in our sever. 
1. we tried to install tidyverse, it gave us error message:"
---ANTICONF] --
Configuration failed to find the harfbuzz freetype2 fribidi library. Try installing:
* deb: libharfbuzz-dev libfribidi-dev (Debian, Ubuntu, etc)
* rpm :harfbuzz-devel fribidi-devel ( Fedora&#65292; EPEL)
* csw: libharfbuzz dev libfribidi dev (Solaris )
*brew: harfbuzz fribidi (osX)
If harfbuzz freetype2 fribidi is already installed, check that 'pkg-configis in yourPATH and PKG CONFIG PATH contains a harfbuzz freetype2 fribidi.pc file. Ifpkg-configis unavailable you can set INCLUDE DIR and LIB DIR manually via:R CMD INSTALL --configure-vars='INCLUDE DIR=... LIB DIR=...
-------------------------ERROR MESSAGE] --------------------
<stdin>:1:10: fatal error:hb-ft.h: No such file or directorycompilation terminated
ERROR: configuration failed for package "textshaping
*removing "/usr/local/lib/R/site-library/textshaping"textshaping' 
ERROR: dependency "textshaping' is not available for package "ragg'
* removing "/usr/local/lib/R/site-library/ragg"
ERROR: dependency  "ragg' is not available for *removing "/usr/local/lib/R/site-library/tidyverse

2. According to the warning message, we tried to install the "deb" manually with code "apt install libharfbuzz-dev libfribidi-dev"
it gave us this error message :
(base) root@inspur:/inspur/home1/Schen# apt install libharfbuzz-dev libfribidi-dev
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
libfribidi-dev is already the newest version (1.0.8-2ubuntu0.1).
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libmount-dev : Depends: libmount1 (= 2.34-0.1ubuntu9.4) but 2.37.2-4ubuntu3 is to be installed
                Depends: libblkid-dev but it is not going to be installed
 libpcre3-dev : Depends: libpcre3 (= 2:8.39-12ubuntu0.1) but 2:8.39-13ubuntu0.22.04.1 is to be installed
 libselinux1-dev : Depends: libselinux1 (= 3.0-1build2) but 3.3-1build2 is to be installed
                   Depends: libpcre2-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
3. we tried to install the specific version of libmount1 with code :apt install libmount1=2.34-0.1ubuntu9.4
the error message is 
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 mount : PreDepends: libmount1 (>= 2.37.2) but 2.34-0.1ubuntu9.4 is to be installed
 util-linux : PreDepends: libmount1 (>= 2.37.2) but 2.34-0.1ubuntu9.4 is to be installed
E: Error, pkgProblemResolver::Resolve generated breaks, this may be caused by held packages.

[B]Our question is here, if we install the lower version of the  dependencies, will it make the running problem of the whole system in the future? And how to solve the series problem mentioned above? 

Thank you very much in advance.[/B]

---

### Post by MAFoElffen on 2023-06-29
Just to confirm... This was when you tried to insall package 'r-cran-tidyverse'?

Do this as a simulated dry-run
```

sudo apt install -s -y r-cran-tidyverse

```

---

### Post by hchen7 on 2023-06-29
Thanks for replying my question. Yes, I met the problem when I wanna install [COLOR=#000000]r-cran-tidyverse.[/COLOR]  I used the code you gave to me, it seems not work:
(base) root@inspur:/inspur/home1/Schen# sudo apt install -s -y r-cran-tidyverse
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 r-cran-tidyverse : Depends: r-cran-googlesheets4 but it is not going to be installed
                    Depends: r-cran-ragg but it is not installable
                    Depends: r-cran-readxl but it is not going to be installed
                    Depends: r-cran-reprex but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

Then I tried to install the depends: r-cran-googlesheets4, and met the problem:
(base) root@inspur:/inspur/home1/Schen# apt install -s -y r-cran-googlesheets4
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 r-cran-cellranger : Depends: r-api-3.5
                     Depends: r-cran-rematch but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
Finally, I tried to install r-api-3.5
(base) root@inspur:/inspur/home1/Schen# sudo apt install r-api-3.5
Reading package lists... Done
Building dependency tree... Done
Reading state information... Done
Package r-api-3.5 is a virtual package provided by:
  r-base-core 3.6.3-2 [Not candidate version]


E: Package 'r-api-3.5' has no installation candidate

May I know how to fix it ? Thank you very much.

---

### Post by MAFoElffen on 2023-06-29
Everything is up-to-date on updates correct?

The reason this seem perplexing is look at my attachment. That is the output from my server doing a simulated dry-run of the same

Thinking about past problems similar to this... In the past, I would do
```

sudo apt install aptitude

```
Then post the output of this, (Please) within CODE Tags.
```

sudo aptitude install -s r-cran-tidyverse

```
'aptitude' has more intelligence than 'apt', especially if something needs to be downgraded to make it install. Often in cases like this, it may come up with multiple solutions to the same problem and have you select which option.

Please start using [noparse]```
 
```[/noparse] tags to post raw output and commands, within the tags.

If the output is too large to post, then compress it into a .zip or .tar.gz file to upload as an attachment.

'aptitude' also has options for --safe-resolve and --force-resolve which I will discuss after seeing that output...

---

### Post by digisus on 2024-02-12
> **MAFoElffen said:**
> Just to confirm... This was when you tried to insall package 'r-cran-tidyverse'?

Do this as a simulated dry-run
```

sudo apt install -s -y r-cran-tidyverse

```

Sorry, to jump in here, but I am facing the same problem as the OP today with a fresh ubuntu 22.04.1 and r-base-* from the repos plus  RStudio DEB from the posit website. 
Are you saying one should NOT use the RStudio DEB package from posit's website but use theses packages instead?

Thank you, digisus.

---

### Post by dragonfly41 on 2024-02-12
Just to jump in. This thread reminded me that I need to install RStudio on fresh Ubuntu 22.04. So I jumped in. Used Synaptic Package Manager to install a bunch or r-cran .. including r-cran-tidyverse as mentioned earlier in thread .. no issues encountered. Then I downloaded RStudio *.deb and installed that using Gdebi (closing Synaptic first).  RStudio launched O.K.

---

### Post by digisus on 2024-02-15
Thanks! In fact, I removed all R from-extra-repos and started fresh from synaptic plus r-cran-tidyverse (plus some more) and finally RStudio. Works now as well.

---

