---
title: "Please Help Laptop Xbuntu Problems"
date: 2007-10-30
forum: General Help
---

### Post by spooter on 2007-10-30
Hi all

I would really like to use xbuntu on my Compaq 1.8Ghz laptop with 256 Mb of memory and have installed it but I have a couple of problems with it.

**First Problem**

Booting up the laptop takes ages, after the Grub loader it sits with a black screen for 3-4Mins before finally loading the desktop.

**Second Problem**

Add or Remove Programs won’t let me install anything it keeps giving me the option to refresh and says in need to be connected to the internet, but I am connected and can browse the net.

**Third Problem**

The Synaptic updates fail to fetch the programs.

Any help on the first issue would be greatly appreciated as I really would like to use this Operating system on my laptop..

Regards

---

### Post by spooter on 2007-10-30
Hi all,

After doing some more searching I think I may have found a fix to the first problem but havent tried it yet

change resolution in /etc/usplash.conf to the correct one for my/your screen:
Code:

     xres=1024
     yres=786

2) execute the following:
Code:

     sudo update-initramfs -u -k `uname -r`

Found it at [https://bugs.launchpad.net/ubuntu/+s...ty/+bug/150930](https://bugs.launchpad.net/ubuntu/+s...ty/+bug/150930)

---

