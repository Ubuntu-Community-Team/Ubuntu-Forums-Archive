---
title: "Can't upgrade Open Office"
date: 2007-07-13
forum: General Help
---

### Post by Seine on 2007-07-13
Hi

There was an Open Office upgrade a few days ago. I can see it in synaptic but I can't get it.

Here's my aptitude upgrade attempt:

```
jem@fawkes:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information       
Initializing package states... Done
Building tag database... Done      
The following packages will be upgraded:
  openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk 
  openoffice.org-impress openoffice.org-math openoffice.org-writer python-uno ttf-opensymbol 
13 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 305kB/53.7MB of archives. After unpacking 0B will be used.
Do you want to continue? [Y/n/?] Y
Err http://au.archive.ubuntu.com feisty-security/main python-uno 2.2.0-1ubuntu4
  404 Not Found
Err http://au.archive.ubuntu.com feisty-security/main ttf-opensymbol 2.2.0-1ubuntu4
  404 Not Found
Err http://au.archive.ubuntu.com feisty-security/main openoffice.org 2.2.0-1ubuntu4
  404 Not Found
E: Failed to fetch http://au.archive.ubuntu.com/ubuntu/pool/main/o/openoffice.org/python-uno_2.2.0-1ubuntu4_i386.deb: 404 Not Found
```

Here's my sources list

```

jem@fawkes:~$ cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.
## Use the following sources.list at your own risk.

deb cdrom:[Ubuntu 6.06 _Dapper Drake_ - Release i386 (20060531)]/ dapper main restricted
deb http://au.archive.ubuntu.com/ubuntu/ feisty main restricted universe multiverse

deb http://au.archive.ubuntu.com/ubuntu/ feisty-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://au.archive.ubuntu.com/ubuntu/ feisty-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://au.archive.ubuntu.com/ubuntu/ feisty-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://au.archive.ubuntu.com/ubuntu/ feisty-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
# deb http://medibuntu.sos-sts.com/repo/ edgy free
# deb http://medibuntu.sos-sts.com/repo/ edgy non-free
# deb-src http://medibuntu.sos-sts.com/repo/ edgy free
# deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.)
deb http://archive.canonical.com/ubuntu feisty-commercial main

## Listen
# deb http://theli.free.fr/packages/ edgy listen


# deb http://media.blutkind.org/xgl/ edgy main-edgy

## www.go-compiz.org/index.php?title=Ubuntu_Installation_Guide
# deb http://gandalfn.club.fr/ubuntu edgy stable dev
# deb http://wine.budgetdedicated.com/apt edgy main

deb http://ubuntu.beryl-project.org feisty main

deb http://download.tuxfamily.org/3v1deb feisty eyecandy 
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy


```

Can anyone see why the OOo packages fail for me? Are the au servers bongos at the moment?

Thank you!

---

### Post by ThrobbingBrain66 on 2007-07-13
Try swtiching to the Main servers for the time being.  In System>Administration>Software Sources, change the "Download from" box to say Main server.

EDIT: You may also want to clean up your sources.list file a bit.  I noticed that you have Beryl's Ubuntu repo AND Trevino's EyeCandy repo enabled.  Trevino's repo has both Compiz and Beryl, so you don't need Beryl's Ubuntu repo (Breakage and general unpleasentness could occur).  

You can get rid of the first line about the Dapper cd-rom unless you need it for somthing I'm not aware of. 

 And if I remember right, the PLF shut down a while back and Medibuntu took its place.

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by Seine on 2007-07-13
Thank you for the tip. I've done a sources list clean up and all is well. Cheers!

---

