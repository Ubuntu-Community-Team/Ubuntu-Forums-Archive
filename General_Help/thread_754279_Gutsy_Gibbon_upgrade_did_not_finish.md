---
title: "Gutsy Gibbon upgrade did not finish"
date: 2008-04-13
forum: General Help
---

### Post by Albrecht on 2008-04-13
I'm a pretty unexperience user, so please excuse any obvious solutions that I missed.

I just tried using update manager to go from 7.04 -> 7.10 and during the installing upgrades part (the status bar was about 2/3 full), I got an error.  The error said that the update for upgrade manager had failed and that the entire upgrade to 7.10 had failed.  The upgrade process then halted.

I can reboot my system, load the 7.10 kernel, and update manager tells me that my system is up-to-date.  Is there any way that I can finish the upgrade to 7.10, though?  

Thanks

---

### Post by sekinto on 2008-04-13
Could you post the output of "cat /etc/apt/sources.list"?

---

### Post by Albrecht on 2008-04-13
Here is the output

$ cat /etc/apt/sources.list

# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy main restricted multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted multiverse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted multiverse universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe

---

### Post by sekinto on 2008-04-13
Well that all seems correct.
Try "apt-get update" and then "apt-get dist-upgrade".

---

### Post by Albrecht on 2008-04-13
Here's the output.  Its just weird that the upgrade process didn't complete, and that every package seems to be up to date.

$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

### Post by sekinto on 2008-04-13
Try "apt-get clean" and then see if it says you can upgrade, maybe it isn't telling you to upgrade because it has downloaded the archives but hasn't installed them. Alternatively you could try "apt-get install".

---

### Post by Albrecht on 2008-04-13
After "apt-get clean", I still get the same output for 
"apt-get update" and then "apt-get dist-upgrade"

For "apt-get install", I get

$ sudo apt-get install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  feisty-wallpapers libstlport5.1 dvipng libmysqlclient15-dev libgpod1 libgd2-noxpm linux-headers-2.6.20-16-generic
  python-tz libslab0 rcs linux-headers-2.6.20-16 feisty-session-splashes libgs-esp8 libqscintilla6 libgdiplus libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

---

