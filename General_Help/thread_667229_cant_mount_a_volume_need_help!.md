---
title: "cant mount a volume need help!"
date: 2008-01-14
forum: General Help
---

### Post by c001os on 2008-01-14
Hi!

I need help!

(sorry for my bad english)! A have a multi boot system, and now i dont need any more my vista. I have formated with qtparted that volume. The problem is i have an other volume that is invisible now, i can't mount etc...
At boot time i have an error message too. 

I post my /var/log/fsck/checkfs error log:

Log of fsck -C -R -A -a 
Mon Jan 14 13:00:16 2008

fsck 1.40.2 (12-Jul-2007)
fsck.ext3: Unable to resolve 'UUID=5020699020697E3A'

drive2: clean, 7724/9781248 files, 17814368/19545344 blocks
fsck died with exit status 8

Mon Jan 14 13:00:16 2008
----------------


All my important data is in that partition that i cant mount. This is not the formated partition. The formated partiton is ok, but this other is "dissapered".

Can anybody help me???

Thx

---

### Post by anaconda on 2008-01-14
Can you see the "lost" partition if you type (in terminal)
sudo fdisk -l

Post the output of that command here, and if you can tell which partition is the "lost" one..

If yo can see the partition, then you should also be able to mount it using terminal..

---

### Post by c001os on 2008-01-14
Hi!

yes I can see

udo fdisk -l
[sudo] password for c001os:

Disk /dev/sda: 80.0 GB, 80060424192 bytes
255 heads, 63 sectors/track, 9733 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        9734    78181376   83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x16f316f3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5099    40957686    7  HPFS/NTFS
/dev/sdb2            5100        9476    35158252+  83  Linux
/dev/sdb3            9477        9729     2032222+  82  Linux swap / Solaris



How i can mount in terminal? (this is sda1)

---

### Post by vanadium on 2008-01-14
I guess you did not change the UUID of the partition in /etc/fstab. When you format a partition, it acquires a new UUID. You can lookup the UUIDS of your drive with the command

blkid

Change the UUID mentionned in your /etc/fstab mentioneed for /dev/sda1 with the UUID you find in the output of blkid.

A less good way to fix this is to replace UUID=... with the device specification (/dev/sda1) but I don't recommend that.

Post your /etc/fstab if you are unsure.

---

### Post by anaconda on 2008-01-14
Mounting in terminal:
```

sudo mkdir /media/disk_sda1
sudo mount /dev/sda1 /media/disk_sda1

```
then just use eg. nautilus (file browser) and navigate to that folder /media/disk_sda1 and you can access sda1 from there..

---

