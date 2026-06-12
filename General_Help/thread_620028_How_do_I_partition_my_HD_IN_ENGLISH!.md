---
title: "How do I partition my HD? IN ENGLISH!"
date: 2007-11-22
forum: General Help
---

### Post by tomcullpepper on 2007-11-22
I've searched all over this forum for an answer, I have no idea what a partition really is, only that it is a division of your hard drive, I have no idea what a swap space is or what HDA3 is or anything like that.  All I want to know is, how the hell do I partition my HD from Windows Vista in English.  I know that partitioning is needed because windows doesn't like other OSes in its personal space.  So can someone tell me how to do this/ what I should do first, a complete step by step (in english, cannot stress this enough) would be the awesome-est thing since ice cream was invented.  :confused:

---

### Post by kpkeerthi on 2007-11-22
[http://tldp.org/HOWTO/html_single/Partition/](http://tldp.org/HOWTO/html_single/Partition/)

If you are planning to install ubuntu alongside Vista (ofcourse on a separate partition), check [this ]("http://www.psychocats.net/ubuntu/installing#partitioning")out. Ubuntu installer can do that for you.

[See this]("http://www.howtogeek.com/howto/windows-vista/resize-a-partition-for-free-in-windows-vista/") if you want to know how to create a parition in vista.

---

### Post by Sef on 2007-11-22
Read [Psychocat's installing]("http://psychocats.net/ubuntu/installing").

> I have no idea what a partition really is, only that it is a division of your hard drive, I have no idea what a swap space is or what HDA3 is or anything like that.

You have a good basic definition of parition.   It is a piece of your hard drive that has been cut from the whole.   (Like when you slice a cake.)  

Swap is basically some extra memory.   You use it if your computer runs out of ram.  However, if you have more than a gigabyte of ram, then swap is really not necessary, unless you do heavy gaming or making movies.  

HDAx (x = number) stands for hard drive A (A = the first hard drive; it may be the only hard drive.  A second hard drive it will be called HDB, a third HDC, etc.)  x is for the partition number.  Hence HDA1 is the first partion on the first drive, HDA2 is the second partition on the first drive, HDA3 is the third partition on the first hard drive.  If there was a second hard drive, then those three partitions would be called HDB1, HDB2, and HDB3.

In Windows, HDA1 would be C, HDA2 would be D, HDA3 would be E.

---

### Post by tomcullpepper on 2007-11-22
> **Sef said:**
> Read [Psychocat's installing]("http://psychocats.net/ubuntu/installing").



You have a good basic definition of parition.   It is a piece of your hard drive that has been cut from the whole.   (Like when you slice a cake.)  

Swap is basically some extra memory.   You use it if your computer runs out of ram.  However, if you have more than a gigabyte of ram, then swap is really not necessary, unless you do heavy gaming or making movies.  

HDAx (x = number) stands for hard drive A (A = the first hard drive; it may be the only hard drive.  A second hard drive it will be called HDB, a third HDC, etc.)  x is for the partition number.  Hence HDA1 is the first partion on the first drive, HDA2 is the second partition on the first drive, HDA3 is the third partition on the first hard drive.  If there was a second hard drive, then those three partitions would be called HDB1, HDB2, and HDB3.

In Windows, HDA1 would be C, HDA2 would be D, HDA3 would be E.

So I partitioned my HD from within windows, and am now trying to run Sabayon, unfortunately both Sabayon and Ubuntu both freeze at kernal initialization, disk spins hard drive light blinks RIGHT UP until it initializes, wtf?  I tried every boot option on Ubuntu and Sabayon, and all of them do the same effin thing, what is wrong with my computer?  Surely two ubuntu disks and an official release DVD of Sabayon can't all be flawed in the same way!

---

