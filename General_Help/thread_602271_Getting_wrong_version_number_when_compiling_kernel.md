---
title: "Getting wrong version number when compiling kernel"
date: 2007-11-04
forum: General Help
---

### Post by KeithLM on 2007-11-04
I'm trying to compile the latest kernel with the dm-raid patch and am having issues with the version number.  I have 2.6.22-14 installed as well as the source.  I applied my patch, copied the config from /boot, made the changes to the config, and then the bad stuff happens.  After I edit the config with either menuconfig or xconfig, it now has the version 2.6.22.9 in .config.  Granted that is in a comment, so I don't think it should matter.  However once I kick off the compile the  .9 version starts appearing in various files, conf.vars and and some file in /usr/src/linux/debian.  Before the compile starts I can't find an occurrence of 2.6.22.9 in any file in /usr/src/linux.  

At the end vmlinux has the version 2.6.22.9 and the deb files are infested with 2.6.22.9, but when I try to install those it looks for 2.6.22.9 libraries and can't find any.  

I've considered softlinking any 2.6.22-14 directory to a 2.6.22.9 name, just to see if that would fool it, but that seems like a bad idea.  Anyone have an idea how I got this version number in there and how to fix it?

---

### Post by nick_h on 2007-11-04
You need to edit the EXTRAVERSION variable in the top level Makefile.

---

### Post by KeithLM on 2007-11-05
> **nick_h said:**
> You need to edit the EXTRAVERSION variable in the top level Makefile.
Sure enough, that looks like the problem.  Thanks for the help, I'll be sure and check that in future builds. I wonder why they did not set that correctly, other files in the source have the -14 set.  

As it is, I managed to get it working by creating some links to mask the directory names where the libraries were.

---

