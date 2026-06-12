---
title: "New Nvidia GPU and Ubuntu wont boot."
date: 2008-02-18
forum: General Help
---

### Post by burritoking924 on 2008-02-18
I purchased a 8400GS and it works fine in Windows XP but whenever I try to boot into Ubuntu 7.10 it says running local boot scripts. Theres a blinking cursor to type stuff, but I dont know what to put. Any solutions to this problem?

---

### Post by burritoking924 on 2008-02-19
Sorry to bump, but nobody can help with this?

---

### Post by PmDematagoda on 2008-02-19
Boot Ubuntu in Recovery Mode and then execute:-
```
dpkg-reconfigure -phigh xserver-xorg
```
after the X-Server is reconfigured restart Ubuntu using:-
```
reboot
```

If that solves your problem then we can get onto installing the Nvidia driver:).

---

### Post by Sephy7KillerMech on 2008-02-19
I'm bumping this thread because I am having the same problem. I'm trying to try out ubuntu with the livecd and it stops at running local boot scripts.

*Starting deferred execution scheduler atd     [OK]
*Starting periodic command scheduler crond    [OK]
*Checking battery state...                                [OK]
*Running local boot scripts (/etc/rc.local)         [OK]



then nothing. no commands give a response. i've tried with just the install/use ubuntu option and the run ubuntu is safe graphics mode.


 I'm using an ATI all-in-wonder x1900, amd 64 3800+, 3 gigs of ram.

i don't have the option of starting in recovery mode from the bootable disc.

---

### Post by PmDematagoda on 2008-02-19
> **Sephy7KillerMech said:**
> I'm bumping this thread because I am having the same problem. I'm trying to try out ubuntu with the livecd and it stops at running local boot scripts.

*Starting deferred execution scheduler atd     [OK]
*Starting periodic command scheduler crond    [OK]
*Checking battery state...                                [OK]
*Running local boot scripts (/etc/rc.local)         [OK]



then nothing. no commands give a response. i've tried with just the install/use ubuntu option and the run ubuntu is safe graphics mode.


 I'm using an ATI all-in-wonder x1900, amd 64 3800+, 3 gigs of ram.

i don't have the option of starting in recovery mode from the bootable disc.

In your case you may have to try booting the Live CD in safe mode or install Ubuntu using the Alternate CD.

---

### Post by Crafty Kisses on 2008-02-19
> **PmDematagoda said:**
> In your case you may have to try booting the Live CD in safe mode or install Ubuntu using the Alternate CD.

The alternate CD would probably work.

---

### Post by Skabbymuff on 2008-05-17
MAN, THANKYOU SO MUCH FOR -

'Boot Ubuntu in Recovery Mode and then execute:-
Code:

dpkg-reconfigure -phigh xserver-xorg

after the X-Server is reconfigured restart Ubuntu using:-
Code:

reboot

If that solves your problem then we can get onto installing the Nvidia driver.'

i have been up all night trying to fix my damn laptop, just got ubuntu working how i liked it, alkl was well, and then it died the second i tried to plug it into my plasma screen and messed with video settings. i was SCREWING. ive been up all night, and your advice here has basicaly saved my laptop! THANKYOU!

---

