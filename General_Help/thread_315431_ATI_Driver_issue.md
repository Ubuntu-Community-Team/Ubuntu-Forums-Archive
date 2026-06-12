---
title: "ATI Driver issue"
date: 2006-12-09
forum: General Help
---

### Post by sub7 on 2006-12-09
I have followed the binarydriverhowto on installing for edgy eft but it gets me this ```
clickme@clickme-desktop:~$ sudo apt-get install xorg-driver-fglrx
Reading package lists... Done
Building dependency tree... Done
Package xorg-driver-fglrx is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xorg-driver-fglrx has no installation candidate
clickme@clickme-desktop:~$ sudo apt-get install fglrx-control
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package fglrx-control
```
I have downloaded the linux driver from ati.com and after typing in a few codes, this appeared in my apps menu...
[IMG]http://www.onepic.com/2/1165582095.81.153.152.26.jpg[/IMG]

I have a radeon 9600, any ideas?

---

### Post by jocko on 2006-12-09
To install fglrx from the repos, first make sure the restricted repos are enabled:
```
sudo /usr/bin/software-properties
```
Check that "Proprietary drivers for devices" is enabled (not sure if my translation from swedish is absolutely correct).
Then:
```
sudo aptitude update && sudo aptitude install xorg-driver-fglrx fglrx-control
```

---

### Post by sub7 on 2006-12-09
this has enabled a few updates, thanks!

After doing that, i re-enabled all the blocked things on the software sources menu and went through the how-to tutorial again and everything installed ok.
It then took effect after i pressed ctrl + alt + backspace.

I can play all the games i want! My ubuntu test is over and i will continue using it now.

---

