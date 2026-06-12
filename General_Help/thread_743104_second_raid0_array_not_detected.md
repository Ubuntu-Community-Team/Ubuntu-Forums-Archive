---
title: "second raid0 array not detected"
date: 2008-04-02
forum: General Help
---

### Post by jeezus84 on 2008-04-02
Evening everyone.

I have two 250GB SATA hard drives in my machine. At the bios level I have set up **two raid0 arrays**. The first one is 120GB for my three operating systems, Windows XP, Vista, and Ubuntu. The second one uses the rest of the disk (380GB) and contains only one large ntfs partition.

My problem is that I cannot load the second raid array. I am using dmraid to access the first array on which all of my operating systems are installed. Windows XP and Vista can see the large ntfs partition.

```

ian@bugeye:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc RS690 Host Bridge
00:02.0 PCI bridge: ATI Technologies Inc Unknown device 7913
00:07.0 PCI bridge: ATI Technologies Inc RS690 PCI to PCI Bridge (PCI Express Port 3)
00:12.0 RAID bus controller: ATI Technologies Inc SB600 Non-Raid-5 SATA
...

ian@bugeye:~$ sudo fdisk /dev/mapper/pdc_hjdj

The number of cylinders for this disk is set to 18236.
There is nothing wrong with that, but this is larger than 1024,
and could in certain setups cause problems with:
1) software that runs at boot time (e.g., old versions of LILO)
2) booting and partitioning software from other OSs
   (e.g., DOS FDISK, OS/2 FDISK)

Command (m for help): p

Disk /dev/mapper/pdc_hjdj: 149.9 GB, 149999976448 bytes
255 heads, 63 sectors/track, 18236 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xd5b0d5b0

               Device Boot      Start         End      Blocks   Id  System
/dev/mapper/pdc_hjdj1   *           1        7649    61440561    7  HPFS/NTFS
/dev/mapper/pdc_hjdj2            7650       15298    61440000    7  HPFS/NTFS
/dev/mapper/pdc_hjdj3           15299       15425     1020127+  83  Linux
/dev/mapper/pdc_hjdj4           15426       18236    22579357+   5  Extended
/dev/mapper/pdc_hjdj5           15426       17975    20482843+  83  Linux
/dev/mapper/pdc_hjdj6           17976       18236     2096451   83  Linux

Command (m for help): q 

```

```

ian@bugeye:~$ sudo ls -l /dev/mapper
total 0
crw-rw---- 1 root root  10, 63 2008-04-02 11:07 control
brw-rw---- 1 root disk 254,  0 2008-04-02 11:07 pdc_hjdj
brw-rw---- 1 root disk 254,  1 2008-04-02 11:07 pdc_hjdj1
brw-rw---- 1 root disk 254,  2 2008-04-02 11:07 pdc_hjdj2
brw-rw---- 1 root disk 254,  3 2008-04-02 11:07 pdc_hjdj3
brw-rw---- 1 root disk 254,  4 2008-04-02 11:07 pdc_hjdj5
brw-rw---- 1 root disk 254,  5 2008-04-02 11:07 pdc_hjdj6

```

```

ian@bugeye:~$ sudo dmraid -r
/dev/sda: pdc, "pdc_hjdj", stripe, ok, 146484352 sectors, data@ 0
/dev/sdb: pdc, "pdc_hjdj", stripe, ok, 146484352 sectors, data@ 0
ian@bugeye:~$ sudo dmraid -ay
RAID set "pdc_hjdj" already active
RAID set "pdc_hjdj1" already active
RAID set "pdc_hjdj2" already active
RAID set "pdc_hjdj3" already active
RAID set "pdc_hjdj5" already active
RAID set "pdc_hjdj6" already active

```

any ideas? thanks.

---

### Post by fjgaude on 2008-04-02
Are you booting off a raid0 array?

---

### Post by jeezus84 on 2008-04-02
yes I am booting off of a raid0 array.

the first raid array contains my three operating systems, including Ubuntu.

---

### Post by fjgaude on 2008-04-02
> **jeezus84 said:**
> yes I am booting off of a raid0 array.

the first raid array contains my three operating systems, including Ubuntu.

"I have two 250GB SATA hard drives in my machine. At the bios level I have set up two raid0 arrays. The first one is 120GB for my three operating systems, Windows XP, Vista, and Ubuntu. The second one uses the rest of the disk (380GB) and contains only one large ntfs partition."

You are trying to mount a partition on the array that is already mounted, i.e., the one that is not part of the three OSs?

Gosh, I've never seen anyone try such a thing before. Learn something new every day, eh?

I have to think about what advise to give.

I trust you have all important data backed up somewhere else, not on one of these two drives of the array. <smile>

---

### Post by jeezus84 on 2008-04-02
i think you mis-understand me.

my computer has TWO raid0 arrays. the first one contains all the partitions for my operating systems.

the second array contains only one partition for storing my files.

it is this second array that Ubuntu is not seeing. in windows the two arrays each show up as their own physical disk. in ubuntu, only the first array shows up. ubuntu cannot even see that the second array exists.

---

### Post by fjgaude on 2008-04-03
Do you mount the two arrays doing something like this:

```
sudo mount -t ntfs-3g /dev/mapperpdcl_hjdjn /raidset1
```

Are the mounts in your /etc/fstab file?

---

