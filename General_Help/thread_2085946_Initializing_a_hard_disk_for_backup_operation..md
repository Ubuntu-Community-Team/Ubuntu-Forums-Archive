---
title: "Initializing a hard disk for backup operation."
date: 2012-11-19
forum: General Help
---

### Post by Raafat1991 on 2012-11-19
Hi guys....


I have hard disk with size two TB, i want to back data up to .

the compure that contains data is with ubuntu OS.
my computer Also is ubuntu OS.

i will backup using rsync , but my problem is i don't know how to mount hard disk to the compure that contains my data.
 
precisely which settings will i use for initializing my hard disk ? 

i have GParted.
.

thank you .

---

### Post by oldfred on 2012-11-19
You need to partition and format a partition on the new drive. You may want more than one partition depending on what you are using it for.

Is this a permanent drive or a USB drive that may not always be connected?

If permanent it is easier to edit fstab so each partition is always mounted and mounted to a name you can use to identify it like "backup". I have several partitions, backup, data, shared. And then folders in each partition for music, documents etc.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Since using rsync, you need to use a Linux format like ext4. Otherwise you will not be able to preserve ownership or permissions. 

I have a permanent backup partition, but do not mount with fstab and just mount with my rsync script.
Some examples of scripts:

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

           rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

---

### Post by Raafat1991 on 2012-11-21
> **oldfred said:**
> You need to partition and format a partition on the new drive. You may want more than one partition depending on what you are using it for.

Is this a permanent drive or a USB drive that may not always be connected?

If permanent it is easier to edit fstab so each partition is always mounted and mounted to a name you can use to identify it like "backup". I have several partitions, backup, data, shared. And then folders in each partition for music, documents etc.

       GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

Since using rsync, you need to use a Linux format like ext4. Otherwise you will not be able to preserve ownership or permissions. 

I have a permanent backup partition, but do not mount with fstab and just mount with my rsync script.
Some examples of scripts:

 Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)

           rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)
Check for mount of backup partition
[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)
#[http://ubuntuforums.org/showthread.php?t=1555647&page=4](http://ubuntuforums.org/showthread.php?t=1555647&page=4)
more scripts:
[http://ubuntuforums.org/showthread.php?t=1319155](http://ubuntuforums.org/showthread.php?t=1319155)

thank you ....

---

