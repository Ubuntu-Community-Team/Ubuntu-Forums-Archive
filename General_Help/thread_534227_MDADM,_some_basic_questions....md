---
title: "MDADM, some basic questions..."
date: 2007-08-25
forum: General Help
---

### Post by jholmes on 2007-08-25
Hi, I'm struggling to find meaningful doco. on MDADM (I'm including the man pages here).

What are the definitions of Array Size & Device Size (and more importantly what are the two numbers that make up Array Size & Device Size)?
Why would these two numbers be different?

```
jah@autopsy-turvy:~$ sudo mdadm --misc --query --detail /dev/md1
/dev/md1:
Version : 00.90.03
Creation Time : Sun Aug 12 16:14:55 2007
Raid Level : raid1
Array Size : 476560128 (454.48 GiB 488.00 GB)
Device Size : 476560128 (454.48 GiB 488.00 GB)
Raid Devices : 2
Total Devices : 2
Preferred Minor : 1
Persistence : Superblock is persistent

Update Time : Sun Aug 12 20:53:11 2007
State : clean
Active Devices : 2
Working Devices : 2
Failed Devices : 0
Spare Devices : 0

UUID : 7ff8b7b2:30e45637:7d2d15a5:39e8ff79
Events : 0.16

Number Major Minor RaidDevice State
0 8 18 0 active sync /dev/sdb2
1 8 34 1 active sync /dev/sdc2

```

any help greatly appreciated

---

### Post by fjgaude on 2007-08-25
Array size is the storage capacity for the group of disk that form the array. The device is the disk capacity. If they are the same it means you are using only two disks in a mirror, raid1. If you were in raid5, say with four disks, the numbers would be very different. <smile>

The size numbers are in 1000-bytes and in Gigabytes, the ones in parenthesis.

These links help at putting it all together:

[http://gd.tuwien.ac.at/linuxcommand.org/man_pages/mdadm8.html](http://gd.tuwien.ac.at/linuxcommand.org/man_pages/mdadm8.html)
[http://www.networknewz.com/2003/0113.html](http://www.networknewz.com/2003/0113.html)

frank

---

### Post by jholmes on 2007-08-25
Ok, thanks for the reply. Just to clarify (as per my example above) 476560128 = 454.48 GiB = 488.00 GB?

I was concerned that somehow my array size turned out to be less than my partition size (which I know to be 488GB)

regs

---

### Post by Scorpuk on 2007-08-25
Your partition size is the unformatted size of the drive.

Example

My 500GB drive formats to 458.45 GB.


This is the case with all drives. You will get approx. 91% of the unformatted capacity.



EDIT:   I Think... ;-)

---

