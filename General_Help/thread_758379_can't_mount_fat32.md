---
title: "can't mount fat32"
date: 2008-04-17
forum: General Help
---

### Post by Mchl923 on 2008-04-17
I've read all over the forums, but nothing I've read has helped.  I put ALL of my data on an external hard drive that I had just formatted as fat32.  Then I reinstalled Ubuntu (unrelated) and now I can't get the files.  Can't see files, can't mount hard drive. btw is their a reason I can't format a drive as ntfs in ubuntu?

---

### Post by MrFSL on 2008-04-18
> btw is their a reason I can't format a drive as ntfs in ubuntu?

Install:
```
sudo apt-get install ntfsprogs
```

Then use gparted:
```
sudo apt-get install gparted
```

---

### Post by mendahu on 2008-04-25
I have a similar problem.

Had a secondary harddrive that I formatted to FAT32 and backed up all date on this drive.  Made that partition in Windows XP, but I extended it using Ubuntu Gutsy so it could fit all my stuff (since Windows couldn't make one larger than 32 GB).  I know that data transferred well, because after I backed it up I did a little work with it (edited some files, etc.).

I wiped my computer, installed Hardy Heron, and now I'm having issues with the drive.  First of all, when I use the command "fdisk -l", it lists the drive oddly.  Here's what I get:

```
Disk /dev/sdb: 81.9 GB, 81964302336 bytes
191 heads, 59 sectors/track, 14205 cylinders
Units = cylinders of 11269 * 512 = 5769728 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5862    33027622    4  FAT16 <32M

Disk /dev/sdb1: 33.8 GB, 33820284928 bytes
191 heads, 59 sectors/track, 5861 cylinders
Units = cylinders of 11269 * 512 = 5769728 bytes
Disk identifier: 0x00000001

     Device Boot      Start         End      Blocks   Id  System
/dev/sdb1p1   *           1        5862    33027622    4  FAT16 <32M

```

Oddities: It's only one disk, but its coming up both as sdb 81.9 GB and sdb1 with 33.8 GB.  Also, its coming up as sd, which I thought was reserved for SATA drives, when this one is in fact an IDE drive.  

When I try to mount, I get this error:

```
jake@babydodds:~$ sudo mount /dev/sdb1 /home/jake/backup
mount: wrong fs type, bad option, bad superblock on /dev/sdb1,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```

I've also tried using this command:

```
jake@babydodds:~$ sudo mount -t vfat
```

...and the same error occurs. Some relevant outputs from dmesg | tail:

```
[  430.020823] FAT: invalid media value (0xb9)
[  430.020831] VFS: Can't find a valid FAT filesystem on dev sdb1.
```

I really need to recover this data (my wife will divorce me if I've lost her stuff). Any ideas?

-Jake

---

### Post by MrFSL on 2008-04-25
> I know that data transferred well, because after I backed it up I did a little work with it (edited some files, etc.).Let me ask, did you edit information using Linux or on the Windows box?

Next, have you tried running fdisk like this?
```
sudo fdisk -l /dev/sdb
```

> I've also tried using this command:
Code:
jake@babydodds:~$ sudo mount -t vfat

This should probably look like this:
```
sudo mount -t vfat /dev/sdb1 /home/jake/backup
```

```
and the same error occurs. Some relevant outputs from dmesg | tail:
Code:
[  430.020823] FAT: invalid media value (0xb9)
```
... A quick google search and it looks like people with this error needed to use a Windows machine to back the dataup and then a Linux machine to wipe the drive to zero and reformat.

Hope this is helpful.

---

### Post by mendahu on 2008-04-26
Thanks for your help; I ended up recovering it on my own.

There was an error with the partition table labeling.  A great program called testdisk was able to rewrite the table to correctly label the partition.  Then linux had not a single problem gettin' in there.

Thanks again!

-Jake

---

