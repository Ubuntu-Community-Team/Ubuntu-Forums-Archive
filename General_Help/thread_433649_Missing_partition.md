---
title: "Missing partition"
date: 2007-05-05
forum: General Help
---

### Post by pepotis on 2007-05-05
Hi comunity!
I've installed Ubuntu Feisty 7.04, and in the Desktop cd all my partitions were detected. I have two hard disks, one with three partitions and the other with only one. When the installation finished and I rebooted, only the partitions of my first disk (sda, even it is a IDE), were mounted.
I can find in /dev my second device, but no partitions are created, I mean, /dev/sdb1 doesn't exists. And it is not created in /dev/disks/by-UUID too.
I have searched in google and in a lot of forums, but I couldn't find a solution.

Please help me....

It worked without problems with 6.06... But this is a new installation

Thanks

---

### Post by pepotis on 2007-05-05
Nobody???
Help please!
...

---

### Post by taurus on 2007-05-05
Can you post the output of this command from a terminal?

```
sudo fdisk -l
```

---

### Post by pepotis on 2007-05-05
pepotis@piposoft:~$ sudo fdisk -l

> Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3316    26635738+   7  HPFS/NTFS
/dev/sda2            3317        6066    22089375   83  Linux
/dev/sda3            6067        7233     9373927+  83  Linux
/dev/sda4            7234        7297      514080   82  Linux swap / Solaris
pepotis@piposoft:~$ sudo fdisk -l

Disk /dev/sda: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3316    26635738+   7  HPFS/NTFS
/dev/sda2            3317        6066    22089375   83  Linux
/dev/sda3            6067        7233     9373927+  83  Linux
/dev/sda4            7234        7297      514080   82  Linux swap / Solaris

Disk /dev/sdb: 13.0 GB, 13022324736 bytes
255 heads, 63 sectors/track, 1583 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table


...

Doesnt contain a valid partition table?? How can I fix it?
Thx

---

### Post by taurus on 2007-05-05
Is there anything on the second harddrive, /dev/sdb?

---

### Post by pepotis on 2007-05-05
This is the partition which doesn't work, and yes, I have a FAT32 partition. I can read and write in it from win...

---

### Post by taurus on 2007-05-05
So it's an empty partition then.  Why don't you use gparted (System -> Administration) and create a partition, /dev/sdb1, with fat32/vfat filesystem.  And if you don't have gparted, install it.

```
sudo aptitude update
sudo aptitude install gparted
```

---

### Post by pepotis on 2007-05-05
Gparted detects the partitions, but it says that sdb1 doesnt exists.... It says it is unallocated. I dont want to format my partition! I only want to see it on Linux....
Thaks for your help... What can be the problem?

---

### Post by taurus on 2007-05-05
Can you read /dev/sdb from Windows?

---

### Post by pepotis on 2007-05-05
Yes  I do... Or I did it ten minuts ago... I will try in a moment another time... But I have a lot of data in sdb1 and I don't want to lose it...

---

### Post by pepotis on 2007-05-05
My partition has been destroyed!!! I can't see it anymore... What have hapenned??? I haven't destroyed it!!, but now, even in Windows, it's only unallocated space...

---

### Post by pepotis on 2007-05-05
I have reinstalled Ubuntu... and now my partitions are recognized by hd*,,. I don't understand anything... Furthermore my second disk partition has disapeared, and I have lost all my music collection...

---

