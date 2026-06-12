---
title: "Some questions, i have had some trouble..."
date: 2007-12-15
forum: General Help
---

### Post by keegan7390 on 2007-12-15
Alright so first off, not sure if this is the right place to post this, and also i am pretty new to linux so give me a break :D
So here is my problem, I want to install Ubuntu on my Inspiron 8000 and i have run into some problems...
When I put the live cd in sometimes it wont show up after i run it, and most of the time the screen is all messed up, which i have searched how to fix that. So when i go to install it, it seems to start fine until i get to the partioning portion. It like screws up every singe time](*,) dont remember the exact error message but i has to do with not being able to partition.
Soo, i tryed something else, I tryed using a live cd og GParted, and the same thing happened. :(
So if anybody could help me, that would be awesome. 

Thank You!
Keegan

---

### Post by cmnorton on 2007-12-16
We need more information to help you.

First, who burned the CD and what kind of CD is it, live, regular install?

If you burned the CD, how did you download it? The CD may have checksum errors.

If you just downloaded the image, then use Bittorrent or something similar. I have never had it fail. Else, purchase from a place like osdisc.com. If you have low network bandwidth, osdisc.com is cheap considering all the grief they save you, and I've never gotten a bad cd from them after two years of purchasing, in addition to downloading install images.

When you install, you may well have to use safe mode to start the installation.

---

### Post by mudguts on 2007-12-16
also, I'm curious if you already have Vista / XP installed?  have you created room on the existing drive for the install and for the swap file??  

are you running this on a wide screen as well?

---

### Post by keegan7390 on 2007-12-16
To answer both your questions I installed it myself, it is an image, and i know that it works because I have tryed it on my other comp. And yes i do have XP installed on it, and i want to make room for it but the problem is partitioning it, thats where i run into problems, it always says it is unable, whether i use gparted or the ubuntu intall. So i guess it really isnt ubuntu to be exact, but the whole partitioning part.

---

### Post by mudguts on 2007-12-23
I find that when i do a 'fresh' install.  I use FDISK to create a partition for XP and leave the rest blank.
install XP then afterwards, install Ubuntu and give yourself the swap file and then the install partition.   depending on drive size.. I have a small ubuntu partition on my notebook. 25GB or so.. the other 100GB is Vista and about another 25GB is set for 'Dell files' and the swap file (4GB)

good luck with it.

---

### Post by davarino on 2007-12-29
> **keegan7390 said:**
> To answer both your questions I installed it myself, it is an image, and i know that it works because I have tryed it on my other comp. And yes i do have XP installed on it, and i want to make room for it but the problem is partitioning it, thats where i run into problems, it always says it is unable, whether i use gparted or the ubuntu intall. So i guess it really isnt ubuntu to be exact, but the whole partitioning part.
This may be overly obvious, but it is also important when setting up a Windows/Ubuntu doubleboot that you 

* open Windows immediately before you start your Ubuntu installation and run Disk Defragmenter from Windows

* *then* restart your computer with the appropriate Ubuntu *Alternate* disk in your CD drive and do your partitioning, etc.

If you run anything on Windows after you defrag your disk you're asking for trouble, and if you do not defrag the disk you may well not find enough contiguous space to install a new partition.

---

