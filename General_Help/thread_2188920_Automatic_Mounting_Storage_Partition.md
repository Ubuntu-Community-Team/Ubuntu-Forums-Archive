---
title: "Automatic Mounting Storage Partition"
date: 2013-11-19
forum: General Help
---

### Post by helmetjanedoe on 2013-11-19
Hi, I have installed lubunut on one of my systems 

now I partitioned the hard drive so about 20gigs is for lubunu, 20 gigs for user folders and the rest I partitioned it as storage space. Now every time I boot this computer I have to press S to skip the boot mounting of storage to actualy be able to boot. 

once then I must also give my system password to mount the disk, 

The computer is just my media player computer and don't care who can read this partition. Eventuly I'd like to be able to FTP files to the stroage drive. but I can figure the ftp stuff on my own.

---

### Post by papibe on 2013-11-19
Hi helmetjanedoe. Welcome to the forum ):P

You should be able to create either permanent mount, or mount points available for every user to mount without password, by creating entries on /etc/fstab.

Take a look at this [tutorial]("https://help.ubuntu.com/community/Fstab"), and let us know if you need more help with that.

Regards.

---

### Post by helmetjanedoe on 2013-11-19
> **papibe said:**
> Hi helmetjanedoe. Welcome to the forum ):P

You should be able to create either permanent mount, or mount points available for every user to mount without password, by creating entries on /etc/fstab.

Take a look at this [tutorial]("https://help.ubuntu.com/community/Fstab"), and let us know if you need more help with that.

Regards.


Thanks But I dont understand how "[COLOR=#333333][FONT=UbuntuMono]sudo mkdir /media/Storage" would make the volume mount while the other volumes mount at boot 

at boot the system says "The DiskDrive for /Storage is not ready yet or present" S to skip or M for manual Recovery[/FONT][/COLOR]

---

### Post by papibe on 2013-11-19
Could you post the result of these commands?
```
cat /etc/fstab

sudo fdisk -l

sudo blkid 

mount -l
```
Regards.

---

### Post by Bucky Ball on 2013-11-19
> **helmetjanedoe said:**
> Thanks But I dont understand how "[COLOR=#333333][FONT=UbuntuMono]sudo mkdir /media/Storage" would make the volume mount while the other volumes mount at boot [/FONT][/COLOR]

... because you're not following the howto at the link posted by papibe. You need to create the mount point, that is only ONE step of a few. You then need to put a line in the fstab, etc .........

Read the link and follow it from start to finish and then it will make sense rather than dragging one line out at random. 

Of course making a mount point only will make no difference whatsoever. That goes without saying. :-k

---

### Post by helmetjanedoe on 2013-11-20
Well, Is there a easy fix? see thats my problem with linux, There is never an easy fix. But hell for the use on my netbook its perfect besides this stupid mounting problem 

any ways I ran thoes comnads and i posted a screen shot of what it spat out to me

[https://drive.google.com/file/d/0B6ZTKLM2Bxvib1VwTEdMa0xtY2s/edit?usp=sharing](https://drive.google.com/file/d/0B6ZTKLM2Bxvib1VwTEdMa0xtY2s/edit?usp=sharing)

---

### Post by papibe on 2013-11-20
Could you copy the text from the terminal and paste it back here on a post?
Regards.

---

### Post by helmetjanedoe on 2013-11-20
I can't coppy paste from there. edit i fixed the google linked picture of the thingey

---

### Post by Morbius1 on 2013-11-20
1st: You are going to have to learn how to run commands in a terminal and post the output to the forum. Anyone who attempts to try to help you depends on that information in a readable format.

2nd: You should be able to see the problem for yourself:

The /Storage partition line in fstab references the partition UUID as 36f42.... ( That's a guess since it's really hard to read it ).

But the blkid command references no such UUID. It would appear the correct UUID is caeb62...... ( That one is even harder to read but it's the one labelled "Stuff" )

---

