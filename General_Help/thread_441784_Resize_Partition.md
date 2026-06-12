---
title: "Resize Partition"
date: 2007-05-12
forum: General Help
---

### Post by dude1701 on 2007-05-12
Is there a way to resize my main Ubuntu 7.04 partition? Ive tried the GNOME Partition Editor, but i cant resize my Ubuntu partition?

Anybody got any ideas?

---

### Post by taurus on 2007-05-12
You need to do it from the LiveCD since you cannot resize a partition while you are using it.

---

### Post by dude1701 on 2007-05-12
It still wont work, i get a message saying that:

Resize /dev/sda1 from 146.12 GiB ro 29.30 GiB could not be applied




Why is this happening?

---

### Post by taurus on 2007-05-12
Are you running gparted from the LiveCD?  Does / take up more than 29GB of space on your harddrive?

---

### Post by dude1701 on 2007-05-12
I am running ir from the Ubuntu 7.04 Live CD disk and running GNOME PARTITION EDITOR, and it takes up less than 15 gb

---

### Post by Rab22 on 2007-05-12
> **dude1701 said:**
> It still wont work, i get a message saying that:

Resize /dev/sda1 from 146.12 GiB ro 29.30 GiB could not be applied

Why is this happening?

What type of file system is it?

Also, how much of your original 146 GB do you have used? How much is free space?

I don't know much about Gparted, but I'm sure if you provide that information I can research and find the reasons why.

---

### Post by dude1701 on 2007-05-12
I have 1 EXT3 With Ubuntu installed and is 146.12 GiB Used: 11.08 Unused: 135.04 GiB
           1 extended and is 2.89 GiB
           1 linux-swap and is 2.89 GiB

---

### Post by taurus on 2007-05-12
Can you post the output of this command here from a terminal?

```
sudo fdisk -l
```
On the other hand, you should try to use GParted LiveCD instead of Ubuntu LiveCD.  

[http://gparted.sourceforge.net/livecd.php](http://gparted.sourceforge.net/livecd.php)

It comes with the latest version of gparted.

---

### Post by dude1701 on 2007-05-13
ksagert@Ronda-Ubuntu:~$ sudo fdisk -1
Password:
fdisk: invalid option -- 1

Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors





Ok, i typed it in and this is what i got

---

### Post by merlinus on 2007-05-13
It's a lower-case L, not a number 1.

sudo fdisk -l

Sorry if I may have read your post incorrectly....

-merlin

---

### Post by dude1701 on 2007-05-13
ksagert@Ronda-Ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19075   153219906   83  Linux
/dev/sda2           19076       19452     3028252+   5  Extended
/dev/sda5           19076       19452     3028221   82  Linux swap / Solaris
ksagert@Ronda-Ubuntu:~$ 




Either way, this is what i get when i type in sudo fdisk -l

---

### Post by merlinus on 2007-05-13
IIRC from days of DOS and manually partitioning at a CLI with fdisk --

You can have one main partition, and then the rest of the disk is an extended partition, which can then be divided up into smaller partitions.

It looks like you have allocated most of your disk to a large main partition, sda1.  Even if you made it smaller, you could not add another partition to that area.  

Whilst I would definitely get confirmation from other forum members who may be more knowledgeable, your only option may be to back up your data and start over.

-merlin

---

### Post by Thingymebob on 2007-05-13
> **merlinus said:**
> IIRC from days of DOS and manually partitioning at a CLI with fdisk --

You can have one main partition, and then the rest of the disk is an extended partition, which can then be divided up into smaller partitions.

It looks like you have allocated most of your disk to a large main partition, sda1.  Even if you made it smaller, you could not add another partition to that area.  

Whilst I would definitely get confirmation from other forum members who may be more knowledgeable, your only option may be to back up your data and start over.

-merlin

This is incorrect, you can have a maximum of 4 primary partitions, everything else must be extended, you can only have 1 partition on which the boot flag is set making this the partition that must cotain a booloader if you do not have one in the MBR

---

### Post by merlinus on 2007-05-13
So does that mean I can shrink the size of an existing primary partition and then create other primary partitions in that freed-up space?

Or do all of the primary partitions have to be continguous, and created at the same time as I create an extended partition?

Also, what are the advantages/disadvantages of having more than one primary?

Thanks!

-merlin

---

### Post by Thingymebob on 2007-05-13
Yes, you should be able to shrink that primary partition and create others in the freed up space
If gparted isn't letting you the filesytsem is either still mounted somewhere or your trying to make it too small (you have more data than the size your trying to make it) which you say you don't.

---

