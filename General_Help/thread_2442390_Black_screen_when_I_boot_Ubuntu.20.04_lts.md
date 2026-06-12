---
title: "Black screen when I boot Ubuntu.20.04 lts"
date: 2020-05-03
forum: General Help
---

### Post by greenarrow13 on 2020-05-03
When I choose Ubuntu form the grub I have black screen.I have tried editing the boot parameters, removing quiet splash, and changing with nomodeset but it doesn't work.any ideas;


Asus vivobook 15(amd ryzen 5 3500u,radeon vega 8)
Dual boot Ubuntu 20.04 and windows 10

---

### Post by gabo4au on 2020-05-05
I don't have that issue, but I've had all sorts of problems with my Vivobook and Ubuntu 20.04 (and 18.04 prior to that). The machine locks up on a regular basis, everything just freezes, no mouse, nothing. No key strokes work, only recourse is to power it off and back on. 

Then today, I upgraded my RAM, installing an 8G chip. First, Ubuntu only reports 9.9G (it has 4G stock). I know the reasons behind getting 11.9G or a few other variants, but 9.9?? 

After installing the memory and booting it back up, within 30 min, the screen went blank like you say yours does. Except I was surfing the web and it just blanked. I was able to log in remotely via SSH and reboot the box. Rebooting didn't bring the screen back, I had to power off/on to get it back. 

We'll see how long it runs, but clearly there is something about the Vivobook and Ubuntu that isn't quite right. I don't know if it's the Ryzen processor, or some other hardware, but it's not right.

Like you, I've tried a bunch of different things, all to no avail. I can't even make it do something different. For now I just keep updating it to see if it goes away.

gabo

EDIT: Someone in my thread suggested checking the UEFI version. Mine was at version 306 and the latest was 310. That might be something for you to try as well. I've updated mine and hoping it will help.



EDIT_2: I'm pretty sure you're having the same problems I am with your Vivobook. I'll keep posting my updates in my thread, [https://ubuntuforums.org/showthread.php?t=2442149](https://ubuntuforums.org/showthread.php?t=2442149)

---

### Post by greenarrow13 on 2020-05-08
Well I found a  very strange solution that I can't explain why it works.
1.connect my laptop with the power
2.in recovery mode I choose clean
3.reboot the laptop
And then it boots normal without problem.
It is temporary solution until i find something else.

---

### Post by wee-snoop on 2020-05-10
Hi,
I do believe that my laptop has the similar issue when boot into Ubuntu 20.04, using the default 5.4-kernel as your laptop does.

My laptop also has AMD Ryzen 5, Radeon RX Vega 8.

The problem seem to be with the the current kernel 5.4 and the graphic stack that ubuntu 20.04 is using, which affects AMD Ryzen 5, Radeon RX Vega 8.

So to get around this issue i updated ubuntu 20.04 with the following.....

sudo apt update

sudo apt install  linux-modules-5.6.0-1008-oem linux-image-5.6.0-1008-oem linux-oem-5.6-headers-5.6.0-1008 


Then i updated the graphic stack to the latest using PPA third-party repository [https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers](https://launchpad.net/~oibaf/+archive/ubuntu/graphics-drivers)   [https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation](https://linuxconfig.org/amd-radeon-ubuntu-20-04-driver-installation)

sudo add-apt-repository ppa:oibaf/graphics-driver 

sudo apt update && sudo apt -y upgrade

This the bug that is affecting me [https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1876835](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1876835)
I've now had ubuntu 20.04 running 5.6 kernel and the latest graphic stack for the last week without a problem, hopefully this will help you out too.

---

### Post by greenarrow13 on 2020-05-27
Thank you so much!!it works :)

---

