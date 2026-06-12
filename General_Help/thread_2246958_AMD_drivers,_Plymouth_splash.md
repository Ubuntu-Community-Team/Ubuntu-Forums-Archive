---
title: "AMD drivers, Plymouth splash"
date: 2014-10-04
forum: General Help
---

### Post by expressotweaks on 2014-10-04
LONG STORY AHEAD. Skip down for question.

Hello guys because my mom's laptop was on windows I decided to install Ubuntu 14.04 on it because she used Ubuntu on her desktop and simply loves it. 

So I installed it all fine and dandy on here laptop with the AMD proprietary drivers working fine, but as mother you know they have to nitpick.

She couldn't help but to notice when booting up the laptop the Ubuntu logo wasn't shown all the way through like on her desktop and showed some ugly purple lines and command text which "embarrassed" her when booting in a public place.

QUESTION: Do you guys know how I can fix Plymouth to make it show the Ubuntu logo all the way through? Or atleast get rid of the command text (Which just says Trusty Tahar login)

LAPTOP SPECS
CPU: A4-3305M
GPU: 6480G

THANKS!

---

### Post by Dennis N on 2014-10-04
Problem:
Plymouth splash starts very late or not at all, with a black screen otherwise displaying until the log-in screen appears.

A solution was offered by Scott Remnant of Canonical:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2)

Based on his method, I did the following, which does the same thing as his in an alternate way. 

1) Create a text file named **splash** containing the line **FRAMEBUFFER=y** and copy it (with sudo) into 
the folder **[FONT=Courier New]/etc/initramfs-tools/conf.d/[/FONT]**
2) Execute in the terminal: **[FONT=Courier New]sudo update-initramfs -u[/FONT]**
3) Reboot.

After this, the splash starts in 3 or 4 seconds.

This is less likely to help much if you have an NVidia driver.

Your results may vary.

---

### Post by expressotweaks on 2014-10-04
> **Dennis N said:**
> Problem:
Plymouth splash starts very late or not at all, with a black screen otherwise displaying until the log-in screen appears.

A solution was offered by Scott Remnant of Canonical:
[https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2](https://bugs.launchpad.net/ubuntu/+source/plymouth/+bug/540801/comments/2)

Based on his method, I did the following, which does the same thing as his in an alternate way. 

1) Create a text file named **splash** containing the line **FRAMEBUFFER=y** and copy it (with sudo) into 
the folder **[FONT=Courier New]/etc/initramfs-tools/conf.d/[/FONT]**
2) Execute in the terminal: **[FONT=Courier New]sudo update-initramfs -u[/FONT]**
3) Reboot.

After this, the splash starts in 3 or 4 seconds.

This is less likely to help much if you have an NVidia driver.

Your results may vary.
Where do you live  so I can come kiss you? I have been searching for a solution to this for 6months and I decide to post on the forums.... Then you come in here like a prince and save the day LOL.

---

### Post by Dennis N on 2014-10-04
Sounds like your had good results - and thanks for the feedback!

---

