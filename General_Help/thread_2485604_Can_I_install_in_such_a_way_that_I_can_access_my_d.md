---
title: "Can I install in such a way that I can access my data from a Live CD?"
date: 2023-04-03
forum: General Help
---

### Post by 777funk on 2023-04-03
I would like to be able to access the data from a Live CD incase I have trouble in the future. I don't care about encryption etc. I would just like to be able to see my Ubuntu partitions later if something goes wrong (as I can with the Windows partitions from a Live CD).

---

### Post by dragonfly41 on 2023-04-03
If as it seems you are in Windows there is an application named R-Linux which allows
installation on both Windows and Ubuntu.  I have it installed in my dual boot setup.

---

### Post by grahammechanical on 2023-04-03
What makes you think that you need to do something special? As a test I have just booted into a Try (live) Ubuntu session on a USB memory stick and I have no problem accessing my Ubuntu partitions. When people come on this forum with boot problems we often recommend using a Try Ubuntu session to backup the data in some way if it seems that a re-install is the easiest solution to the problem. By the way, I just have standard Ubuntu desktop installations. No encryption. No VM installs. That might make things difficult.

Regards

---

### Post by ne29914 on 2023-04-03
It's fairly easy.
Do the live boot, open the terminal and mount the relevant partition (usually /home). Then you will see your data.
Just did it myself due to botched install.
It helps a lot if /home has its own partition.

---

### Post by 777funk on 2023-04-03
Ok... maybe that's the problem. I tried (by just clicking) the old ubuntu install and it said permission denied. I'll try mounting it first as root and see what happens.

---

### Post by TheFu on 2023-04-03
Any "Try Ubuntu" setup (DVD, CDROM, Flash drive) can access any Linux file system if the file systems used are supported by that "Try Ubuntu" environment.  

Normal Unix permissions will always be there, so you'll need to understand those to access files in the way you need.  Not learning about UNIX file and directory permissions isn't an option. They are core to how all Unix-like OSes work.  Find a tutorial. Work through it.  Spend 30 minutes more trying every possible combination for permissions, groups, users that you can think of until something "clicks" in your brain - then you'll have 90% of the necessary knowledge and never have to be frustrated by file permissions again.  Or ... don't learn it and be frustrated for hours, days, weeks, months, years.  The choice is yours.

---

### Post by ne29914 on 2023-04-03
> **777funk said:**
> Ok... maybe that's the problem. I tried (by just clicking) the old ubuntu install and it said permission denied. I'll try mounting it first as root and see what happens.
I'm not certain that's a good idea, your live boot disk is probably already mounted as / (don't use the term "root" for this, it has at least five different meanings. Curse of UNIX/Linux).
Open the terminal after live boot and do:
```
macro@1dk6910p:~$ lsblk
NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINTS
sda      8:0    0 465,8G  0 disk 
&#9500;&#9472;sda1   8:1    0  29,3G  0 part /
&#9500;&#9472;sda2   8:2    0   5,9G  0 part [SWAP]
&#9492;&#9472;sda3   8:3    0 430,6G  0 part /home
sr0     11:0    1  1024M  0 rom 

```
Then you'll know what's mounted and what's not.

---

