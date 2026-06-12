---
title: "Ubuntu 7.04 Problem"
date: 2008-01-18
forum: General Help
---

### Post by KevMeistr on 2008-01-18
Plain and simple problem... I think.

I was busy adding a printer from a network to my linux system when all of a sudden the electricity goes off...when I switched my computer back on it booted to the ubuntu grub loader but then it said that there are system errors and came up with a message that apt-get could not be found... So that means my computer is useless unless I install ubuntu again.

Has anybody got anyway of solving this problem.

---

### Post by dcstar on 2008-01-18
> **KevMeistr said:**
> Plain and simple problem... I think.

I was busy adding a printer from a network to my linux system when all of a sudden the electricity goes off...when I switched my computer back on it booted to the ubuntu grub loader but then it said that there are system errors and came up with a message that apt-get could not be found... So that means my computer is useless unless I install ubuntu again.

Has anybody got anyway of solving this problem.

Boot off the live CD and manually run fsck on the hard disk partitions, if that doesn't help then you may well have to reinstall.

---

### Post by KevMeistr on 2008-01-18
Thanks dcstar

But do you have an idea of what happened and what can be done to prevent this in future

---

### Post by dcstar on 2008-01-18
> **KevMeistr said:**
> Thanks dcstar

But do you have an idea of what happened and what can be done to prevent this in future

Your disk was probably corrupted by the power failure, buy and install a UPS if you want to prevent this in the future.

You can also edit your /etc/hdparm.conf file to turn off write caching for your hard disk, this makes your system a bit slower but more resilient to situations like power cuts.

---

### Post by erfahren on 2008-01-18
could the OP use "dpkg -reconfigure" from the command line to reconfigure apt? Or reinstall the [apt package](http://packages.ubuntu.com/feisty/base/apt)?

---

### Post by KevMeistr on 2008-01-18
> **erfahren said:**
> could the OP use "dpkg -reconfigure" from the command line to reconfigure apt? Or reinstall the [apt package](http://packages.ubuntu.com/feisty/base/apt)?
You see the problem is that I can't even log in to my desktop because there are system errors, so I guess I won't even be able to download or even install packages from the internet without apt-get

---

### Post by Sef on 2008-01-18
> You see the problem is that I can't even log in to my desktop because there are system errors, so I guess I won't even be able to download or even install packages from the internet without apt-get

Have you tried going into GRUB and using recovery mode?

---

### Post by KevMeistr on 2008-01-18
> **Sef said:**
> Have you tried going into GRUB and using recovery mode?
Yeah, I have... gives me the same error as booting up normally.
I have this program called webmin which allows you to go online and see what's happening with your computer but cannot access it because I don't know how to get into it from the command line.

---

