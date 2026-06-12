---
title: "I need help in Ubuntu 10.4 with Unmet Dependencies."
date: 2012-10-29
forum: General Help
---

### Post by Blue78 on 2012-10-29
The following packages have unmet dependencies:
  libasound2: Breaks: libasound2-plugins (< 1.0.24) but 1.0.22-0ubuntu6 is to be installed
  libglib2.0-0: Breaks: gvfs (< 1.8) but 1.6.1-0ubuntu1build1 is to be installed
  libpango1.0-0: Breaks: plymouth (< 0.8.2-2ubuntu19) but 0.8.2-2ubuntu2.2 is to be installed
  ppp: Breaks: network-manager (<= 0.8.0.999-1) but 0.8-0ubuntu3.3 is to be installed
       Breaks: network-manager-pptp (<= 0.8.0.999-1) but 0.8-0ubuntu3 is to be installed

What do I need to do to Fix this? I'm just trying to install Fluxbox and Codky and it will not let me.  My computer just keeps saying this everytime. Thanks for your time.

---

### Post by jerrrys on 2012-10-29
Did you download from the software center/synaptic or did you use another source?

Have you updated lately?  In terminal:

sudo apt-get update

---

### Post by Blue78 on 2012-10-29
Yes, I tried sudo apt-get update. Then i tried to sudo apt-get autoremove each breaks didn't work. Then I tried to update each one in Synaptic Package Manager. All it says when I hit apply is a sign pops up saying could not apply changes fix broken packages. How are you post to Fix them if SPM will not let you update or Remove them or unmark them. I can't believe how hard this is. Now I remember what happen I was in Update Manager and saw that I could update Ubuntu to 12.04.1 LSD by hitting the update button. I did and in the middle of downloading my labtop battery run out and it turnoff. I went home and charged it and turned it back on and went back to Update Manager and started downloading again and it didnt work. Now I'm having this Problem. Please Let Me Know What I should Do Thanks for Your Time.

---

### Post by sucksatcompiling on 2012-10-29
sudo apt-get -f install

---

### Post by vanquishedangel on 2012-10-29
> **Blue78 said:**
> Yes, I tried sudo apt-get update. Then i tried to sudo apt-get autoremove each breaks didn't work. Then I tried to update each one in Synaptic Package Manager. All it says when I hit apply is a sign pops up saying could not apply changes fix broken packages. How are you post to Fix them if SPM will not let you update or Remove them or unmark them. I can't believe how hard this is. Now I remember what happen I was in Update Manager and saw that I could update Ubuntu to 12.04.1 LSD by hitting the update button. I did and in the middle of downloading my labtop battery run out and it turnoff. I went home and charged it and turned it back on and went back to Update Manager and started downloading again and it didnt work. Now I'm having this Problem. Please Let Me Know What I should Do Thanks for Your Time.

Synaptic has an option to fix broken packages as well
 synaptic-edit-fix broken packages

open synaptic, click edit, select fix broken packages

Hope this helps

---

### Post by jerrrys on 2012-10-30
try sudo apt-get -f install like suggested and if your still getting errors also post the output of:

cat /etc/apt/sources.list

---

### Post by Blue78 on 2012-10-30
Man guys I thought I figured it out I went in Synaptic manager and did update packages. It updated 1801 packages. Then once it was done it said (Error occurred : could not perform immediate configuration on 'Python minimal' Please see Man 5 apt conf under immediate-configure for details. I'll have to look into this now. Anyway the update still didnt fix the broken packages. I also tried in Synaptic fix broken packages and it wouldn't let me but heres the information you asked for thanks for all your help so far.

blue@blue-laptop:~$ sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 1186 not upgraded.

blue@blue-laptop:~$ cat /etc/apt/sources.list
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/kubu/ lucid main restricted
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/myth/ lucid main multiverse restricted universe
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/netb/ lucid main restricted
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/ubun/ lucid main restricted
# deb cdrom:[Ubuntu 10.04 LTS _Lucid Lynx_ - Release i386 (20100429)]/xubu/ lucid main multiverse restricted universe
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) precise-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) lucid-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) precise partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) lucid partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) precise-security multiverse
blue@blue-laptop:~$
```

---

### Post by snowpine on 2012-10-30
The problem appears to be that you have a failed upgrade from 10.04 to 12.04. The easiest option in my opinion is to back up your documents and do a fresh reinstall of 12.04 giving you a "clean slate" in effect.

---

### Post by Blue78 on 2012-10-30
Ok sounds good , Now how would I go about doing the back up data? and how do you do A clean install?  Should I find 12.4 Ubuntu on a Web-site or Get it on a disk? I tried to upgrade 10.4 to 12.4 by using Update Manager it had the option to upgrade on it. Once it started Updating 12.4 my computer turned off. should I just try to use Update Manager again? What are your thoughts about it?

---

### Post by snowpine on 2012-10-30
That could explain it! If your computer turned off then the updates are not complete and your computer is in a "limbo" state. 

Here are the complete upgrade instructions, follow them step by step and post any error messages (but hopefully you will not have any errors right ;))

[https://help.ubuntu.com/community/PreciseUpgrades](https://help.ubuntu.com/community/PreciseUpgrades)

---

### Post by Blue78 on 2012-10-30
Ok I'm going to give it a try hopefully everything will work out just fine.  I'll keep you posted. My fingers are crossed. lol,  Thanks for all your help

---

### Post by Blue78 on 2012-11-01
Well I did everything in Update Manager to Upgrade to 12.4 and It said upgrade compleat but there were Errors and this is what the Error said.

ERROR: root: Exception during pm. DoInstall ()
Traceback (most recent call last): File "/usr/lib/python2.6/distpackages/distupgrade/distupgradeview.py. line 182, in run res=pm. Doinstall (self.writefd) system Error: E: Could not perform immediate, configuration on 'python-minimal: Please see man 5 apt.conf under APT: Immediate-Configure for details. (2)
So I guess It will not upgrade because I'm having a problem with Python-Minimal.  So How can I fix this and if I do will it upgrade right? Please let me know what I have to do thanks.

---

