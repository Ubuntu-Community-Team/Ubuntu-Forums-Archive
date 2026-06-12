---
title: "[SOLVED] apt-get install app"
date: 2007-10-09
forum: General Help
---

### Post by maz00 on 2007-10-09
Hi guys,

Being very new to Ubuntu, I've noticed that 'apt-get install ??????' works by asking you to insert the Ubuntu CD in the drive. Then it installs the requested application. Is there a way or another tool similar to FreeBSD ports that would actually connect to the internet and download the latest from the net? 

BTW, I'm using Ubunto Server edition with no GUI. 

Thx
Maz.

---

### Post by forestpixie on 2007-10-09
system > admin > software sources and you should be able to turn cd off so you get from internet

---

### Post by bionnaki on 2007-10-09
open the terminal and type

sudo nano /etc/apt/sources.list

and comment-out the first lines that direct apt-get to look at the cd (put a "#" in front of the line).

example:

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main $

# deb cdrom:[Ubuntu 7.04 _Feisty Fawn_ - Release i386 (20070415)]/ feisty main $
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


and then save (control-x, save)

---

### Post by maz00 on 2007-10-10
Thanks.. worked.

---

### Post by forestpixie on 2007-10-10
can you mark thread solved  - thread tools at top of thread :)

---

