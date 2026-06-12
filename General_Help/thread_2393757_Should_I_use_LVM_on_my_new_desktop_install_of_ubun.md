---
title: "Should I use LVM on my new desktop install of ubuntu 18.04?"
date: 2018-06-07
forum: General Help
---

### Post by Tom_Carr on 2018-06-07
I am a lightweight user.  I use my desktop to browser the internet, print documents, scan documents, and do some stuff with LibreOffice.  That is all.  I like to keep things simple.  When putting 18.04 on a new desktop, should I select LVM or not?  Why or why not?

---

### Post by ajgreeny on 2018-06-07
If you want to keep everything simple avoid LVM like the plague; it adds extra difficulties to managing drives and partitions about which, I suspect, a lot of forum members know little so it will be less easy to get help.

---

### Post by Doug S on 2018-06-07
> **ajgreeny said:**
> If you want to keep everything simple avoid LVM like the plague; it adds extra difficulties to managing drives and partitions about which, I suspect, a lot of forum members know little so it will be less easy to get help.+1. I stopped using LVM a few years ago, and am happy I did.

---

### Post by oldfred on 2018-06-08
LVM is more for advanced users.
It is often used on servers and is required if you want full drive encryption. That erases entire hard drive and converts it to LVM, logical volumes.

       Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

I also do not use LVM, but with gpt partitioning, now used with UEFI have no issues with partitioning.

---

