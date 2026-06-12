---
title: "New user help"
date: 2007-04-17
forum: General Help
---

### Post by Gre_ybeard on 2007-04-17
I just installed ubuntu 6.06 from CD and want to know if updating from with in it gets updates for that version only or does it upgrade me to 6.10.
How do I find out what version I am currently running. If I know this, then I can answer the above question.
Also, when my desktop hibernates, I cannot get back into it, I have to reboot it. I have tried the 3 or 4 options available in poser manager and nothing seems to make a difference. The only time it hibernates and is recoverable is when I reboot and don't login. It will eventually hibernate and recovers when I touch the mouse. Once I do login however, it never recovers.
Any help is much appreciated
Richard  Gre_ybeard

---

### Post by teddmeister2 on 2007-04-17
unless you did something like the following howto suggests: [https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29](https://help.ubuntu.com/community/EdgyUpgrades?highlight=%28upgrade%29)
then you probably just have regular dapper (6.06) on your computer.

---

### Post by matigol on 2007-04-17
You must look after your sources.list files.
If you have only dapper source, it will updating dapper and not edgy or feisty.

( excuse my english, i'm a little frenchy).

;-)

---

### Post by ajgreeny on 2007-04-17
As matigol says, have a look at your /etc/apt/sources.list file.  Mine looks like this:-

## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) dapper-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) dapper-backports main restricted universe multiverse

## Medibuntu - Ubuntu 6.06 LTS "dapper drake"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)
# deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free
# deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) dapper free non-free

## Ubuntu commercial repository
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

##Save My Modem
# deb [http://tassi.web.cs.unibo.it/debian/smm](http://tassi.web.cs.unibo.it/debian/smm) ./

## wine
## deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/

#wine
deb [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) binary/
deb-src [http://wine.sourceforge.net/apt/](http://wine.sourceforge.net/apt/) source/

## skype 
## only uncomment it if you need it
deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free

#flashplugin
# deb [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0
# deb-src [http://3v1n0.tuxfamily.org](http://3v1n0.tuxfamily.org) dapper 3v1n0

Note that until you get to the area below
##Save My Modem
# deb [http://tassi.web.cs.unibo.it/debian/smm](http://tassi.web.cs.unibo.it/debian/smm) ./
all the entries have dapper in their titles.  That means that only dapper repositories are being used and that you will not be upgrading the distro to edgy (6.10) or feisty (7.04), but just updating dapper to the fullest extent.

Personally, I think that dapper, even though it may have some slightly older packages than the newer versions of ubuntu, is still the best OS I've ever used, and that starts with dos and goes up to WinXP Home.  Rest assured you should be OK if you've added no new repos to your list.  The only odd ones in mine are all sites I trust, or for other packages I've tried and often given up on, hence many of the repos are commented out (#).

---

