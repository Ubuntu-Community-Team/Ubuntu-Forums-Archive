---
title: "Virtual Disk Space"
date: 2007-07-09
forum: General Help
---

### Post by Uradox on 2007-07-09
Hi,
Firstly thanks to the wubi team for developing this fantastic product. All my past experiences with linux have always had one critical device driver not work, this time everything was smooth and works perfectly.

I did not allocate enough free space to the wubi installation and now when I goto install a game it stops at 13% downloaded and gives write error not enough free space. I used Toporesize to resize my home disk by 3gb, it would not resize the system disk. So I resume the games download (its only 200mb) and it gets to 96% and gives the same error. I just want to confirm what disk I should be resizing? I am assuming now its the system disk(theres no way that 200mb download would use 3gb) so when I get home today I will try the other methods to resize it.
Also will I loose anything since I am creating a new disk it seems?

Thanks

---

### Post by ago on 2007-07-09
You are probably better on to try lvpm, so you get a real installation on a real partition, you should keep all seetings and you help us debugging ;)

---

### Post by Uradox on 2007-07-09
Thanks for the fast reply.
I dont really like to split my hd with partitions, i was happy to read about wubi avoiding this actually. But lets say I have 10gb Free right now. I download and install this LVPM and run it and it basicly walks me through the process of moving the installation onto that 10gb free and removes the virtual disks from my windows drive?

---

### Post by ago on 2007-07-09
You'd need to have a free partition.

---

### Post by Uradox on 2007-07-09
Ok easiest way to do this? Inside ubuntu or windows? From memory the Windows XP disk managment isnt really good.
Also is my assumption with what it does correct? I want to go into it well informed :) Still a new ground for me. I create a 10gb partition and run this tool from ubuntu? And the rest is easy..

---

### Post by ago on 2007-07-09
Tuxcantfly is the author of lvpm so he would be the better person to guide you through. But yes you can resize from windows, then use gparted from within ubuntu to format the partition as ext3 and then run lvpm from ubuntu. The alternative is of course to use the Live CD. 

Note that by running: 'sudo apt-get clean' you can usually free up a bit of space

---

### Post by Uradox on 2007-07-09
Ok I will dive into lvpm very shortly. Just backing up very important recent holiday pictures in case everything goes to hell.
I look forward to hopefully being able to contribute to this community sometime in the future :)
Its quite exciting for me to see this working so well on my laptop.

---

### Post by Uradox on 2007-07-09
Ok everything appears to have gone smoothly. Although it seems to have slowed down a fair bit, maybe that will pass.
Oh I no longer have a boot menu anymore? Ubunto boots up without asking if I want windows..

---

### Post by ago on 2007-07-09
> **Uradox said:**
> Ok everything appears to have gone smoothly. Although it seems to have slowed down a fair bit, maybe that will pass.
Oh I no longer have a boot menu anymore? Ubunto boots up without asking if I want windows..

You'd probably need to edit /boot/grub/menu.lst (lvpm should do it automatically, it's something we might need to fix). Something like:

title Windows XP
root (hd0,1)
savedefault
makeactive
chainloader	+1

NOTE: (hd0,1) indicates disk 1, partition 2. Change as appropriate.

---

### Post by Uradox on 2007-07-09
Ok thanks Ago
You have been very helpful! I will try that when i get home today.

---

### Post by Uradox on 2007-07-10
ok its readonly and my user doesnt have permision to change it. How do I log in as root? I dont recall anything other than my user during wubi setup
EDIT ok i worked out the purpose of sudo :) all good now

---

