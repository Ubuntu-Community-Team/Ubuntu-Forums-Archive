---
title: "[SOLVED] mount windows"
date: 2007-12-25
forum: General Help
---

### Post by skymera on 2007-12-25
i reinstalled ubuntu on a new hard drive and left my windows unplugged, (turns out the plug it was in was trned off in the BIOS)

anyway, i added windows manually to grub, but how do i mount it?

ive tried sudo mount -a but no luck.

it shows in fdisk -l and gparted

---

### Post by taurus on 2007-12-25
You need to add an entry in /etc/fstab to mount it when you boot Ubuntu.  Can you post the output of that command?

```
sudo fdisk -l
```

---

### Post by skymera on 2007-12-25
scott@scott-desktop:~$ sudo fdisk -l

Disk /dev/sda: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xe686f016

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       19452   156248158+   7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
255 heads, 63 sectors/track, 18241 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000d9a32

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        5957    47849571   83  Linux
/dev/sdb2            5958        6079      979965   82  Linux swap / Solaris
/dev/sdb3            6080       18241    97691265    f  W95 Ext'd (LBA)
/dev/sdb5            6080       18241    97691233+   7  HPFS/NTFS

Disk /dev/sdd: 2 MB, 2097152 bytes
2 heads, 32 sectors/track, 64 cylinders
Units = cylinders of 64 * 512 = 32768 bytes
Disk identifier: 0xf547c58c

---

### Post by taurus on 2007-12-25
I see there are two ntfs partitions there, /dev/sda1 & /dev/sdb5.  Which one do you want to mount or do you want to mount both?

---

### Post by skymera on 2007-12-26
ermm

just sda1 :)
sdb5 is program files

---

### Post by taurus on 2007-12-26
Okay.  Edit /etc/fstab

```
gksudo gedit /etc/fstab
```
and add this line to the end of it.

```
/dev/sda1   /media/sda1   ntfs-3g   defaults   0   0
```
Save it and close gedit window.  Then, install ntfs-3g if you haven't done so, create a new mount point for it, and mount it.

```
sudo apt-get update
sudo apt-get install ntfs-3g
sudo mkdir /media/sda1
sudo mount -a
ls -la /media/sda1
```

---

### Post by skymera on 2007-12-29
thanks!

---

