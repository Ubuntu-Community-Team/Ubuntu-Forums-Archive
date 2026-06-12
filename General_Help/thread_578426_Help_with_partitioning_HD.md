---
title: "Help with partitioning HD"
date: 2007-10-17
forum: General Help
---

### Post by jrharvey on 2007-10-17
My girlfriend asked me to put Ubuntu on her laptop (Dell inspiron B120). She wants to keep windows so i told her I could install a dual boot. I knew there would be problems with wireless and screen resolutions but I didnt think the install would be so difficult. I tried to use GParted to partition the existing windows install (30G) and divide that in half to use for ubuntu. Gparted will not let me resize the existing partition that only uses 9G for windows. I did this with my computer but its not working for her for some reason. Is there another program that will let me do this. Also i noticed that she had 4 partitions already on there and im not sure why, a fat 16 (15M), a NTFS (32G), a fat 32 (3G) and ntfs (8M) im not sure why there are so many since she does not have a recovery partition and even if she did I would think it would be in ntfs.

---

### Post by bigken on 2007-10-17
the other partitions are the tools and system restore image what you need to do is defrag windows a few times and back up any data 

then use the gparted live cd to down size and create an extended partition

---

### Post by jrharvey on 2007-10-17
So If i defrag windows then it may let me resize it????

---

### Post by bigken on 2007-10-17
it might do but you will have to create an extended partition to make more partitions as you can only have 4 primary partitions

it looks like you have four partitions if I were you I would delete the fat 16 as this is the dell diagnostic tools

---

### Post by jrharvey on 2007-10-17
Make an extended partition? Im not sure what you mean. How do I do this, i dont see any options for this.

---

### Post by bigken on 2007-10-17
you can only have four primary partitions which you have delete the fat 16 then downsize the hdd using gparted live cd and create an extended partition to create your ubuntu partitions try googling and do some home work before you try as you could mess the whole thing up and lose your windows restore image

---

### Post by jrharvey on 2007-10-17
Ok I will try this but I may just delete all partitions and start from scratch if it doesnt work, as her windows is RIDDEN with spyware and stupid weatherbug bullcrap. I have to make sure I have all the drivers before I do this though so I will be back if I have any problems. Thank you :)

---

### Post by bigken on 2007-10-17
if you delete all the partitions you lose your windows restore image this is the three gig one unless you have a windows cd it dont matter the driver are easily
downloaded from the dell web site

---

### Post by jrharvey on 2007-10-17
Yes I do have a cd.

---

### Post by rkillcrazy on 2007-10-17
> **bigken said:**
> if you delete all the partitions you lose your windows restore image this is the three gig one unless you have a windows cd it dont matter the driver are easily
downloaded from the dell web site

The drivers are only easily downloaded if you know what you have in it.  Before you blow that partition away, look in **%SystemDrive%\Dell\Drivers** or **%SystemDrive%\Drivers** for the drivers that were left there from Dell.  Get that directory off that drive before you blow it away!  That will help you greatly.  I build, maintain, reload, et cetera many Windows machines and getting drivers from Dell sucks when you go to grab NIC drivers and they have 10 NICs to choose from.

10-17-07
1044

---

### Post by bigken on 2007-10-17
if you have the cd then just delete the ntfs partitions there should a folder in c:\
called delll this has all your drivers in it leave the dell diagnostic and restore image partitions on the drive :)

---

