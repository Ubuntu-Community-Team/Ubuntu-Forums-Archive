---
title: "Grub errors with windows"
date: 2007-11-18
forum: General Help
---

### Post by spencertheman on 2007-11-18
Alright well i had XP installed on a 40gb internal with NTFS. I had a second 20gb hard drive where i had Feisty installed. I updated to Gutsy when the time came. I booted into Ubuntu a couple of times and then stopped when I installed WoW. I used XP from then on out. Then the other day I decided that I needed the extra 20gb where Ubuntu was installed. I used a copy of Norton Partition magic to delete the partition on the drive, then formatted it with Windows. I came home yesterday to find my computer had been restarted and it sitting at the bios password to start up my machine. I entered my password and it came up with a Grub 17 error. I tried everything. I changed the jumper settings, tried to boot just the XP drive and nothing. Well I took out the CMOS battery to reset the BIOS. I tried booting again and it gave me a Grub 21 error.


Any ideas?

Here's my setup:
Dell GX260 
40gb HD with XP
20gb HD with no OS


please help guys

---

### Post by meierfra on 2007-11-18
Grub comes in two parts: One part is on the MBR (the first sector of your hard drive), the other one on  the Ubuntu partition. Since your deleted the ubuntu partition, Grub can no longer function.   You need to put XP back in charge of the MBR. 
There are lots of ways to do this. I'll give you three:

1a)  If you have Windows XP: Boot from an XP installation or recovery CD. Press "R" to enter the recovery console. 

Type

```
fixmbr

exit
```

1b)  If you have Vista:   Boot from a Vista CD/DVD 
From there, click on "Repair your Computer"
Select your Vista installation, and then click "Next >"
Click on command prompt
At the prompt type:


```
Bootrec /FixMBR

exit
```

2)  Get Super Grub: [Hermanzone info on supergrub]("http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html")

3)   Boot  into  Ubuntu or from the Ubuntu Live CD and make sure you have a working internet connection.

Step I) Enable the "universe" repositories. 

Go to Systems-> Adminstration->Software Sources"

Click on the Box next to "Community-maintained Open Source Software (universe)

Click on Close (twice)

Step II)   Install the package "ms-sys"  ([Info on ms.sys]("http://ms-sys.sourceforge.net/")
 In a terminal

```

sudo apt-get update
sudo apt-get install ms-sys

```

Step III) Use "ms-sys" to installed a windows type boot-loader to the MBR:

```
sudo ms-sys -m /dev/sda

```

This assumes that the Windows is on the hard  disk  named  /dev/sda. If you don't know the disk's  name, you can find out by typing "sudo fdisk -l".

---

### Post by spencertheman on 2007-11-18
thanks! i'll try that when i get an xp disk


shouldn't be too long


:]

---

### Post by malfist on 2007-11-18
Any number of windows apps can fix the Masterboot record. Just make sure you find one that can be booted.

---

### Post by Lastaii on 2007-11-29
Thanks meierfra, I've had a similar problem* and the ms-sys solution worked wonderfully once *I'd* worked out which disk was which :)


*Not that I'm giving up on Ubuntu, I just needed it off that particular drive to give Windows more space

---

### Post by nikoPSK on 2007-11-29
generally you want to install ubuntu over windows, windows will screw up grub....

---

