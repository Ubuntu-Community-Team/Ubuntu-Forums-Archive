---
title: "Error screen before install"
date: 2007-09-10
forum: General Help
---

### Post by Ballou on 2007-09-10
Hi every one
I used Wubi to install Kubuntu..I downloaded the iso directly, checked the MD5 signature and put it in install directory of Wubi..
When i reboot, i choose Ububtu..and then a black screen come, during 4~5 minutes it show me errors..but it ends and the install continue!!
It seems that the install now ended (successfully?)..
it reboot, i choose ubuntu..when it comes to loading bar, the same black screen come again, take over 4minutes, but after, kubuntu launch!!
and every thing i try to boot on kubuntu, I must wait those 4 minutes..
Who can tell me what's the problem exactly?
notes:
-I use Windows XP
-I make a chkdsk of the drive I choosed for Wubi after doing anything..
-I tried to install on both my C: and D: ->same problem
I'm not ready to wait 4 minutes every time I want to use Kubuntu :( ..
Thanks in advance ;)

---

### Post by ago on 2007-09-10
You can have a more verbose boot by pressing alt+f1 or looking at the logs in /var/log. If you find out where it stops it might be easy to fix.

Sometimes mounting the swap file creates problems, renaming the swap.virtual.disk to noswap.virtual.disk should address it

---

### Post by Ballou on 2007-09-10
This is the first time I m using a linux distrubution, I'm not pretty sure I understood you
> Sometimes mounting the swap file creates problems, renaming the swap.virtual.disk to noswap.virtual.disk should address it
Where shall I rename it? from linux no?
I precise that my problem occur before the install, and when kubuntu is loading..but in the end, Kubuntu work just fine :confused:

---

### Post by ago on 2007-09-10
c:\wubi\disks
You can rename from withing windows
Assuming that the issue is due to the swap...

---

### Post by Ballou on 2007-09-10
I renamed it, the problem remains :(
Any other suggestion or solution ?
Thanks in advance :)

---

