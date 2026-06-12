---
title: "Can't resume after suspend and power off issues with ubuntu 14.04"
date: 2016-04-09
forum: General Help
---

### Post by nic16 on 2016-04-09
I installed a fresh copy of Ubuntu on my desktop computer and now I face several power related issues:


**Can't resume after I suspend the system:**
When I suspend the system, it screen goes blank and there is a white dash blinking. All the fans and lights stay on, and if I hit a key on the keyboard or move the mouse the system does not wake up.


**System is power on when suspended**
All lights and fans are still running when I click suspend


**Can't power off the system**
When I click shut down the system goes blank with a white dash blinking and all fans and lights are on.


**Steps I tried:**
I tried to disable all power saving settings in the bios
I tried to use proprietary drivers for nvidia
I updated everything
I can't power off system with this command sudo init 0
I can't power off system with this command sudo shutdown -P now
I can't power off system with this command sudo shutdown -H now
Changing grup to GRUB_CMDLINE_LINUX_DEFAULT="quiet splash acpi=off" doesnt change anything
I read this documentation page and didn't help
To power off the computer I must press and hold the power button for 5 seconds and do a hard power off
[B]
System Spec:[/B]
128GB SSD
GeForce GTX 560 Ti (using the x.org x server open source driver)

It is been two days and I have been trying to search and fix this issue but I can't get it to work. Any suggestion is appreciated.

---

### Post by nic16 on 2016-04-10
any suggestions? 
this post has been viewed more than 200 times and no reply, is the question too simple? I can post more info if needed

---

### Post by QIII on 2016-04-10
Your thread has been viewed by exactly two members who have been logged in: You and me.

That means the other 209 views were by people who were not logged in or by web crawlers/indexing bots.

Please be patient.  If, after about 12 hours, you do not get a response, simple add another post with the word "bump".  This will put your thread at the top again.

---

