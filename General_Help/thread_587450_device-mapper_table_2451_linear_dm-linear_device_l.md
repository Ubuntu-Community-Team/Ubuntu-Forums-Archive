---
title: "device-mapper: table: 245:1: linear: dm-linear: device lookup failed"
date: 2007-10-22
forum: General Help
---

### Post by awd-s on 2007-10-22
After upgrade to 7.10, the disk on one of my machines was thrashing and the error message in the subject-line was repeatedly posted to tty1. After some judicious searching, I discovered that it is some incompatibility between EVMS (Enterprise Volume Management System) and the latest Kernel. I cured the problem with this command, since I don't think I use EVMS:

sudo aptitude remove evms

As a bonus, the foregoing voodoo not only exorcised the EVMS poltergeist but also resurrected the mount to /dev/hdb1 which had gone missing in action between 7.04 and 7.10.

I hope this bit of *ubuntu-for-you-too* helps. Good luck!

---

### Post by werebus on 2007-10-22
I had the same problem and removing evms *did* in fact fix the problem.  The odd thing is that it works fine if I boot using the previous kernel version.  Does anyone know if I actually need evms?  The package description is kind of vague.  Is there another solution to this problem?

---

### Post by sulemankm on 2007-10-23
Hi thanks for the info.  I had the same problem after I updated to 7.10.  The old kernel boots correctly but the new one does not.  I'll try to remove emvs just now.

---

### Post by sulemankm on 2007-10-23
I opened synaptic to remove evms package.  But, in its description it is mentioned that in order to use evms another package called linux-patch-evms should also be installed.  I installed the linux-patch-evms package but the device-mapper: device lookup failed problem still persisted.

So, I guess removing the evms package is the only solution for this problem with kernel 2.6.22-14-386.

---

### Post by pguedes on 2007-10-24
sudo aptitude remove evms

:guitar:

Worked to me Like a Charm!!!!

I was going desperate, with this message! I initially thought that it was related do the Upgrade from Feisty to Gutsy on Nvidia Graphics Card problem, but after doing everything to solve the graphic problem, I finally decided to think that the Upgrade add more than one BUG.

In Conclusion there were two diferent BUGS:
Nvidia Card Upgrade from feisty to gutsy
Device Mapper

It took two frustrating days....

Thanks AWD-S for sharing this important Info! :)

---

### Post by awd-s on 2007-10-24
During my research, I saw a report that said restoring the earlier kernel also cured the problem. I elected to retain the latest kernel and remove EVMS. I don't know the whys and wherefores, I'm just a user who did what worked. I think that an up-to-date kernel is more important because they often include security improvements and corrections.

---

### Post by awd-s on 2007-10-24
I'm glad this information helped. It is the meaning of Ubuntu -- helping each other.

---

### Post by jpgeerets on 2007-10-25
same problem here...
at this moment my disk is readonly-mount....
so i cant remove evms....
but, i can try to boot with different kernel...
perhaps that can be an option....

thanks guys....

---

### Post by jpgeerets on 2007-10-25
hmm,
ok, now i have made a server-boot to the previous kernel.
all seems well, except 1 (minor) thing...

the root-drive is mount as read-only....

someone any idea?

---

### Post by jpgeerets on 2007-10-26
ok.
things workd for me now.
what had i done...
- boot with server-cd in rescue mode
- edit fstab with vi
- boot the system with an older kernel in normal mode
- apt-get remove evms
- boot in normal mode with new kernel

at this moment i can read and write with new kernel...

thanks folks!

---

### Post by one19 on 2007-10-31
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/115616](https://bugs.launchpad.net/ubuntu/+source/linux-source-2.6.22/+bug/115616) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				Thanks awd-s! You're a life saver. Upgraded from 7.04 to 7.10, system was trashed, Googled "device-mapper table linear dm-linear device lookup failed" and found this thread. The fastest time for me to find a solution.

---

### Post by madman91 on 2007-11-04
Thank you!!! Fixed my problem instantly.

---

### Post by jkgruet on 2007-12-29
Yes!  The bug is still in existence; and I was more frustrated than you can imagine (since my wife was eager to get back to the computer).  Removing *evms* done did the trick.  What a great resource this forum is.

---

### Post by kevinp on 2008-01-13
Drat.  I actually do use EVMS.  What are my options?

I confirm that when I downgraded to using the 2.6.20-16 kernel, everything booted properly.

---

