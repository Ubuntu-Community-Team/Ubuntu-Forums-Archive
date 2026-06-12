---
title: "Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2007-02-02
forum: General Help
---

### Post by MuddyGeek on 2007-02-02
When I attempted to update it came back with an error.  First I did sudo apt-get update which was fine.  When I apt-get upgrade it yields this:


> chris@chrisdesktop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  gtk2-engines-pixbuf libgtk2.0-0 libgtk2.0-bin libgtk2.0-common libwxbase2.6-0 libwxgtk2.6-0 python-wxgtk2.6
  python-wxversion
8 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/13.2MB of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 28801 package `language-pack-gnome-hr':
 `Replaces' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)


So I tried apt-get install -f 

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnash0 libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.

Following the apt-get autoremove advice leads me in a circle:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnash0 libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
chris@chrisdesktop:~$ 
chris@chrisdesktop:~$ sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnash0 libgtkglext1
The following packages will be REMOVED:
  libgnash0 libgtkglext1
0 upgraded, 0 newly installed, 2 to remove and 8 not upgraded.
Need to get 0B of archives.
After unpacking 2724kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: parse error, in file `/var/lib/dpkg/available' near line 28801 package `language-pack-gnome-hr':
 `Replaces' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)


So what should I do?

Thanks,
Chris

---

### Post by codejunkie on 2007-02-02
try running ```
sudo apt-get -f install
``` then try ```
sudo dpkg --configure -a
``` and try updating again, by the way what version of ubuntu are you using if your using feisty it could be related to a bug in that package a might not be fixable until they release a fix for that package.

---

### Post by MuddyGeek on 2007-02-02
I am using Edgy.  

I tried sudo apt-get -f install:

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnash0 libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.


sudo dpkg --configure -a yields:
> dpkg: parse error, in file `/var/lib/dpkg/available' near line 28801 package `language-pack-gnome-hr':
 `Replaces' field, invalid package name `


I ran update, upgrade, -f install all again but to no avail.

---

### Post by codejunkie on 2007-02-02
> **MuddyGeek said:**
> I am using Edgy.  

I tried sudo apt-get -f install:



sudo dpkg --configure -a yields:


I ran update, upgrade, -f install all again but to no avail.

do you need that language pack installed, sometimes they are installed as extras and you don't need them in which case you could just remove it permanently , if that is your native language and you need it try removing the package and reinstalling it by copying and pasting this command into the terminal```
sudo apt-get remove --purge language-pack-gnome-hr && sudo apt-get install language-pack-gnome-hr
```

---

### Post by MuddyGeek on 2007-02-02
Hmm...  still not working.

> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package language-pack-gnome-hr is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libgnash0 libgtkglext1
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 8 not upgraded.
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libgnash0 libgtkglext1
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  language-pack-gnome-hr-base
Recommended packages:
  language-support-hr
The following NEW packages will be installed:
  language-pack-gnome-hr language-pack-gnome-hr-base
0 upgraded, 2 newly installed, 0 to remove and 8 not upgraded.
Need to get 1130kB of archives.
After unpacking 4039kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy/main language-pack-gnome-hr-base 1:6.10+20061019 [929kB]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) edgy-updates/main language-pack-gnome-hr 1:6.10+20061203 [201kB]
Fetched 1130kB in 12s (90.9kB/s)                                               
dpkg: parse error, in file `/var/lib/dpkg/available' near line 28801 package `language-pack-gnome-hr':
 `Replaces' field, invalid package name `
E: Sub-process /usr/bin/dpkg returned an error code (2)


I followed that up by update, upgrade, -f install, autoremove.

---

### Post by codejunkie on 2007-02-02
> **MuddyGeek said:**
> Hmm...  still not working.



I followed that up by update, upgrade, -f install, autoremove.
hmm. it could be a bad package in us repos you could try changing your repos 
run ```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.orig
``` to backup your origional sources file, then run ```
sudo gedit /etc/apt/sources.list
``` and deleted everything in there and copy and paste this in there

```
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy main restricted universe multiverse

deb http://archive.ubuntu.com/ubuntu edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse
deb-src http://archive.ubuntu.com/ubuntu edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb http://medibuntu.sos-sts.com/repo/ edgy free
deb http://medibuntu.sos-sts.com/repo/ edgy non-free
deb-src http://medibuntu.sos-sts.com/repo/ edgy free
deb-src http://medibuntu.sos-sts.com/repo/ edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb http://archive.canonical.com/ubuntu edgy-commercial main

## Listen
#deb http://theli.free.fr/packages/ edgy listen

```
save the file then run ```
sudo apt-get update
``` then ```
sudo apt-get dist-upgrade
```

---

### Post by MuddyGeek on 2007-02-02
Repos did not seem to be the issue.  I followed your advice, changed my sources list, ran the update and dist-upgrade but came back with same error.  Also tried -f install once again.

---

### Post by codejunkie on 2007-02-02
> **MuddyGeek said:**
> Repos did not seem to be the issue.  I followed your advice, changed my sources list, ran the update and dist-upgrade but came back with same error.  Also tried -f install once again.
i don't know it has to be in that package i would submit a bug to launchpad so the developers can take a look at it.

---

### Post by MuddyGeek on 2007-02-03
Thanks for your help.  I'm going to research more and probably will hit Launchpad.

---

