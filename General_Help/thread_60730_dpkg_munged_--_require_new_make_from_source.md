---
title: "dpkg munged -- require new make from source?"
date: 2005-08-29
forum: General Help
---

### Post by trader-boy on 2005-08-29
Somehow i have munged dpkg (or [found this bug](http://www.mail-archive.com/debian-dpkg-bugs@lists.debian.org/msg00628.html) ) so that it won't work and therefore i can't install anything  using apt, aptitude, synaptic (don't like and uninstalled), etc. I can remove packages but not install. This happened while using aptitude and it was in the middle of a multiple item dpkg update. For the most part i use only apt -- quick and no fuss, but if a have a dependancy issue i find aptitude can resolve it easily.

[COLOR=Red]This is the error message:

dpkg: syntax error: unknown group `fuse' in statusoverride file [/COLOR]

I found the following bug report on this by googling at 

Bug#320952: marked as done [http://www.mail-archive.com/debian-dpkg-bugs@lists.debian.org/msg00628.html](http://www.mail-archive.com/debian-dpkg-bugs@lists.debian.org/msg00628.html) 
dpkg in unstable (base): 1.13.11

Because this is such a base level package and everything to install deb files uses it, how do i get dpkg working again??

This bug is apparently fixed in the unstable release just done earlier this month. Do i need to recompile, make and install dpkg manually? I downloaded the fixed unstable package from debian.org [[link here](http://ftp.us.debian.org/debian/pool/main/d/dpkg/dpkg_1.13.11_i386.deb)]. How do i unpack the .deb archive to get the source files? Is there another low level package intalling tool i can use (ipkg?) already an an Ubuntu system? :roll: 

Sean

---

