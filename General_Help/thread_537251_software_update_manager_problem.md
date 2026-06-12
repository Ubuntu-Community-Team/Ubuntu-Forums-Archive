---
title: "software update manager problem"
date: 2007-08-28
forum: General Help
---

### Post by guarnibl on 2007-08-28
> 
guarnibl@guarnibl-desktop:/var/cache/apt/archives$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  compiz-gnome
The following packages will be upgraded:
  compiz-gnome
1 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
7 not fully installed or removed.
Need to get 161kB of archives.
After unpacking 893kB of additional disk space will be used.
Do you want to continue [Y/n]? 


This won't go away :( I press Y and the output I get is the following

> 
Get:1 [http://download.tuxfamily.org](http://download.tuxfamily.org) feisty/eyecandy compiz-gnome 1:0.5.5~git20070828+3v1ubuntu0 [161kB]
Fetched 161kB in 0s (179kB/s)       
(Reading database ... 106355 files and directories currently installed.)
Preparing to replace compiz-gnome 1:0.3.6-1ubuntu13 (using .../compiz-gnome_1%3a0.5.5~git20070828+3v1ubuntu0_i386.deb) ...
Unpacking replacement compiz-gnome ...
dpkg: error processing /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070828+3v1ubuntu0_i386.deb (--unpack):
 trying to overwrite `/usr/lib/compiz/libgconf.so', which is also in package compiz-plugins
Errors were encountered while processing:
 /var/cache/apt/archives/compiz-gnome_1%3a0.5.5~git20070828+3v1ubuntu0_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
guarnibl@guarnibl-desktop:/var/cache/apt/archives$


This is a freaking vicious cycle. I click update manager -- it says it's broken and to run "sudo apt-get install f" so I do that -- and the damn thing breaks itself again. GRR.

Help :(

---

### Post by flagg on 2007-08-28
You are installing a package from a third party which has a file that conflicts with an already installed package. In this case compiz-gnome conflicts with compiz-plugins. Try removing compiz-plugins and then trying again.

---

### Post by padamon on 2007-08-29
Can you go to system >> admin>> synapatic package manager then go to custom filters broken packages and then remove them.

---

