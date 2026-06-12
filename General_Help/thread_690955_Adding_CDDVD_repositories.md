---
title: "Adding CD/DVD repositories"
date: 2008-02-08
forum: General Help
---

### Post by karthik_jce on 2008-02-08
Hi,

   I have ubuntu installable CD's and I had added them as repositories in synaptic. But still when I try to install using "apt-get" or synaptic, it says it has to download the packages and uses the internet. 

   My query is that, does the Ubuntu CD have most of the packages, i.e is it necessary to go through the internet for every package installation ?

  As my internet connection is 256kbps only it seems to be slow and takes a long time.

Regards
Karthigeyan

---

### Post by dcstar on 2008-02-08
> **karthik_jce said:**
> 
   I have ubuntu installable CD's and I had added them as repositories in synaptic. But still when I try to install using "apt-get" or synaptic, it says it has to download the packages and uses the internet. 

   My query is that, does the Ubuntu CD have most of the packages, i.e is it necessary to go through the internet for every package installation ?
.......

No, the CD does not have "most" of the packages, a DVD would struggle to have most of the packages.

The Ubuntu CD contains the install scrips, a live O/S and packages that the developers believe will be required by the average user for a default install, but that still is only a small fraction of the available packages in all the official repositories (let alone the "unofficial" ones).

Sometimes you will be prompted to insert the CD when the system knows the** current version** of a package exists on it, but otherwise it will download the latest version.

---

### Post by winkman on 2008-02-08
Hi Karthigeyan,
There is PLENTY of information on the net about Ubuntu repositories (look mainly at the ubuntu documentation) but basically only the most basic programs are contained on the Ubuntu install cd... If you have a repository cd, then that will contain many more, but the majority of files will need to be downloaded from the internet. I believe, that if you look through the Synaptic repository, any programs with the ubuntu sign next to them are contained on the ubuntu install cd. 

Linux's system of software repositories is the most functional for the way the distributions work, because there is not one sole developer- there are hundreds (if not thousands) around the world, and if someone was to publish a repository cd (as Ubuntu occasionally does) then it would quickly become out of date. 

You mention your internet is slow- check out AptOnCD, a program that you can use easily to transfer your downloaded apt software. It could help... 

Hope this was of some help...
Mitch

---

