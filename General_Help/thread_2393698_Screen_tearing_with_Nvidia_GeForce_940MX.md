---
title: "Screen tearing with Nvidia GeForce 940MX"
date: 2018-06-06
forum: General Help
---

### Post by Furycd001 on 2018-06-06
HI Guys

I have a thinkpad e470 with Nvidia GeForce 940MX graphics. With Nvidia proprietary drivers installed screen tearing is literally non-stop. How can I put a stop to screen tearing without having to revert to Intel graphics ??


Many thanks in advanced....

---

### Post by Autodave on 2018-06-07
What driver do you have installed and where did you get it from?

---

### Post by Furycd001 on 2018-06-07
I just went to additional drivers & installed the nvidia driver that was offered. Xubuntu 16.04.4 LTS is what I'm currently running...

> Settings Manager >> Additional Drivers >> NVIDIA binary driver - version 384.130 from nvidia-384 (proprietary tested)

---

### Post by #&amp;thj^% on 2018-06-07
The only other suggestion I can think of is to "try" adding ppa:graphics-drivers/ppa
Found here:[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
The rest below is just a run down of other things to try:
Check in the GUI Nvidia-Settings>>under OpenGL Settings and see if "Sync to VBlank and Allow Flipping and Use Conformant Textture Clamping" is checked.

---

### Post by Furycd001 on 2018-06-07
> **1fallen said:**
> The only other suggestion I can think of is to "try" adding ppa:graphics-drivers/ppa
Found here:[https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa](https://launchpad.net/~graphics-drivers/+archive/ubuntu/ppa)
The rest below is just a run down of other things to try:
Check in the GUI Nvidia-Settings>>under OpenGL Settings and see if "Sync to VBlank and Allow Flipping and Use Conformant Textture Clamping" is checked.

I just tried looking in Nvidia settings but cannot find anything to do with "Sync to VBlank". I may try the ppa if I can't find a solution within the next couple of days. Thanks for your reply :)

---

### Post by #&amp;thj^% on 2018-06-07
See if this helps "Screenshot"

---

### Post by mc4man on 2018-06-07
Do like here, in 2nd step use 384  instead of 375 (if still on 384 driver
[https://ubuntuforums.org/showthread.php?t=2365449&p=13663158&viewfull=1#post13663158](https://ubuntuforums.org/showthread.php?t=2365449&p=13663158&viewfull=1#post13663158)

Note that you have to installed from 16.04.3 or newer image or have enabled the hwe hardware stack, i.e now using xserver-xorg-core-hwe-16.04 (2:1.19.5-0ubuntu2~16.04.1

---

### Post by Furycd001 on 2018-06-08
> **1fallen said:**
> See if this helps "Screenshot"

My settings window looks completely different to that....

[ATTACH=CONFIG]280041[/ATTACH]

---

### Post by Furycd001 on 2018-06-08
> **mc4man said:**
> Do like here, in 2nd step use 384  instead of 375 (if still on 384 driver
[https://ubuntuforums.org/showthread.php?t=2365449&p=13663158&viewfull=1#post13663158](https://ubuntuforums.org/showthread.php?t=2365449&p=13663158&viewfull=1#post13663158)

Note that you have to installed from 16.04.3 or newer image or have enabled the hwe hardware stack, i.e now using xserver-xorg-core-hwe-16.04 (2:1.19.5-0ubuntu2~16.04.1

Thank you very much for your post. I've tried what was said in that thread and I think it has worked. I'm going to leave this thread open a little just in case it hasn't worked....

---

### Post by mc4man on 2018-06-08
If it has worked keep in mind that in 16.04 if you later change nvidia driver version you have to also change the the version number in the .conf file & re-run sudo update-initramfs -u command
If ever moving to 18.04 it's the same idea but in 18.04 you don't specify the nvidia driver version, i.e options nvidia_drm modeset=1

---

### Post by Furycd001 on 2018-06-08
> **mc4man said:**
> If it has worked keep in mind that in 16.04 if you later change nvidia driver version you have to also change the the version number in the .conf file & re-run sudo update-initramfs -u command
If ever moving to 18.04 it's the same idea but in 18.04 you don't specify the nvidia driver version, i.e options nvidia_drm modeset=1

Thanks for the heads up :)

---

