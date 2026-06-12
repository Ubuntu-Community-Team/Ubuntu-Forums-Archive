---
title: "Edgy Scrolling"
date: 2006-11-20
forum: General Help
---

### Post by firebadger on 2006-11-20
After upgrading from Dapper to Edgy, scrolling is jerky and very unpleasant.  Whether it is scrolling a page up and down in Firefox or moving windows about the Desktop the problem is the same.
I notice that while I am doing this Xorg is fully utilising the CPU.

Anybody know what is going on and more importantly how to fix?

---

### Post by flameproof on 2006-11-21
I had the same problem and managed to fix it:

[http://ubuntuforums.org/showthread.php?t=304459](http://ubuntuforums.org/showthread.php?t=304459)

---

### Post by Dual Cortex on 2006-11-21
Before attempting to follow his guide, be sure to have the nvidia driver installed (and, obviously, that means you should be using a an nvidia vid. card).

**or else you will kill xserver!**

---

### Post by firebadger on 2006-11-22
The thing is I don't have a Nvidia graphics card.  I've got an onboard SIS graphics interface on my Winfast motherboard.

---

### Post by firebadger on 2006-11-23
Anybody else have this problem who doesn't have a Nvidia card?  Any ideas about how to solve?

---

### Post by firebadger on 2006-11-23
Fixed it!

As I said earlier I have an onboard SIS graphics controller (a 741 or something).  Anyway, I went [here]("http://http://www.winischhofer.eu/linuxsispart1.shtml") and downloaded the driver file for X version 7, stopped X, copied the file to /usr/lib/xorg/modules/drivers, edited my xorg.conf so that the driver field of the graphix devise was set to "sis" and restarted.

Hey presto, all fine.

---

