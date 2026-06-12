---
title: "sudo apt-get update"
date: 2007-09-20
forum: General Help
---

### Post by giant22000 on 2007-09-20
Ok, here is the problem.  I'm new to linux and i'm trying to get my  wlan working.  For the life of me, I can not get anything, I mean anything to compile or install.  All I get is error messages.  I've been told to run several commands to update libraries.  ie... sudo apt-get install build-essential.  Well low and behold I get an error message with that as well.  Says that it can not find the build-essential.  Well i'm ok with that too, cause I found somwhere on google to run this command which should fix that last error message.  apt-get update.  Being I don't have internet, I can not update.  Well is there a work around to that problem.  I'm not even sure if this is my problem at all.  Let me give a little bit of history...  I bought a laptop (Gateway ML3109), brought it home, wipped out Vista and put Ubuntu on here, and proceeded to get my wlan working doing nothing else or setting up anything else on Ubuntu.  If anybody has any suggestions or ideas, it would be much appreciated!  Thank you very much!

---

### Post by sumguy231 on 2007-09-20
You can download the packages you need from packages.ubuntu.com using a computer or OS with an Internet connection and then put it on removable media and install them.

---

### Post by Maestro23 on 2007-09-20
Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

*Make sure you grab all dependencies as well.

---

### Post by giant22000 on 2007-09-21
> **Maestro23 said:**
> Ubuntu Packages: [http://packages.ubuntu.com/](http://packages.ubuntu.com/)

*Make sure you grab all dependencies as well.

I tried this as well... I downloaded the packages from this site.  Unzipped them to my desktop.  Opened a terminal and went to that directory and used sudo apt-get install ndiswrapper-common.  I am totally at a lose here...  Not sure what i'm doing wrong...

---

### Post by gaussian on 2007-09-21
sudo dpkg -i ***list of your .deb files***
should do the job

---

