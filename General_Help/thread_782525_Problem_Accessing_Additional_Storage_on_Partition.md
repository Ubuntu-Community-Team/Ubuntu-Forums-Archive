---
title: "Problem Accessing Additional Storage on Partition"
date: 2008-05-05
forum: General Help
---

### Post by killtacular on 2008-05-05
I'm a recently new user to ubuntu and am currently dual booting Windows Xp and Hardy Heron 8.04.  

I have two partitions on my 300 gb.  50 gb's for my Windows Xp and the additional 250 for storage.  I installed Ubuntu on the additional 250 on my E: partition and assigned 30gb's for Hardy Heron.  

My problem is that I can't seem to find the additional storage from that partition.  I have a variety of music, movies, and the like stored on the rest of the partition but no way to access it while in Ubuntu.  I would greatly appreciate if anybody could give me a clue how to access this while in Ubuntu.  

Thanks.

---

### Post by ASULutzy on 2008-05-05
click applications, then accessories, then terminal. Then type sudo fdisk -l and paste the output here

---

### Post by killtacular on 2008-05-05
```
Usage: fdisk [-b SSZ] [-u] DISK     Change partition table
       fdisk -l [-b SSZ] [-u] DISK  List partition table(s)
       fdisk -s PARTITION           Give partition size(s) in blocks
       fdisk -v                     Give fdisk version
Here DISK is something like /dev/hdb or /dev/sda
and PARTITION is something like /dev/hda7
-u: give Start and End in sector (instead of cylinder) units
-b 2048: (for certain MO disks) use 2048-byte sectors
killtacular@killtacular-desktop:~$ 

```

Here is the info.  I'm not sure how to properly display it, but at least I tried.

---

### Post by killtacular on 2008-05-06
Perhaps if someone could elaborate what to do with the output, I can continue learning ubuntu.  T

Thanks!

---

### Post by ASULutzy on 2008-05-06
Huh? I don't think you typed it right
```
sudo fdisk -l
``` that's a lower case L

---

### Post by killtacular on 2008-05-06
> **ASULutzy said:**
> Huh? I don't think you typed it right
```
sudo fdisk -l
``` that's a lower case L

Yeah, I'm not too sure what happened there.  Here we go:

```
Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x95e695e6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6527    52428096    7  HPFS/NTFS
/dev/sda2            6528       38913   260140545    7  HPFS/NTFS

```

---

### Post by ASULutzy on 2008-05-06
When you say you installed Ubuntu to your E: partition... that really doesn't make sense to me... Did you use Wubi to install Ubuntu?

edit: Oh yea I didn't even notice that the type was NTFS not linux...

I guess a caveman type solution would be to do the following```
sudo mkdir /mnt/sda1
sudo mkdir /mnt/sda2
sudo mount /dev/sda1 /mnt/sda1
sudo mount /dev/sda2 /mnt/sda2
``` Then you could just browse through the partitions by going to those two folders (/mnt/sda1 and /mnt/sda2)

Sorry I couldn't be more helpful, I have no experience with Wubi, or with installing linux to an NTFS partition. But perhaps that little block of commands I listed may be helpful!

---

