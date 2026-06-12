---
title: "Mounting drive through USB bridge: can only see GRUB directory"
date: 2018-02-17
forum: General Help
---

### Post by backfour94 on 2018-02-17
Recently purchased a new lap top and I'd like to load the hard drive from the old one through a USB bridge.

The seems to be recognised as 250gb drive but the only directories I can see is GRUB.

I welcome any help in how I can get to see the rest of the drive. Thanks.

HP Pavilion
Ubuntu 16.04
Core i5

---

### Post by TheFu on 2018-02-17
Did you use encryption or lvm or both?

---

### Post by backfour94 on 2018-02-17
Thanks for coming back.

No encryption, sorry don't know what lvm is.

I see the drive on in a 'files' window between 'network' and 'Computer' as "255 MB Volume" with a load of files but the only directory being the grub one.

This is 500gb disk.

---

### Post by TheFu on 2018-02-17
LVM beginners: [https://www.howtoforge.com/linux_lvm](https://www.howtoforge.com/linux_lvm)

Probably best to post the output from **sudo parted -l**  <-- that's an el (l), not a I or 1. Please use "code tags" so it is readable and aligned.

---

### Post by backfour94 on 2018-02-17
Thanks for coming back.

No encryption, sorry don't know what lvm is.

I see the drive on in a 'files' window between 'network' and 'Computer' as "255 MB Volume" with a load of files but the only directory being the grub one.

This is 500gb disk.

---

### Post by backfour94 on 2018-02-17
Model: ATA TOSHIBA MQ01ABD1 (scsi)
Disk /dev/sda: 1000GB
Sector size (logical/physical): 512B/4096B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                          Flags
 1      1049kB  274MB   273MB   fat32           EFI system partition          boot, esp
 2      274MB   290MB   16.8MB                  Microsoft reserved partition  msftres
 3      290MB   251GB   250GB   ntfs            Basic data partition          msftdata
 6      251GB   979GB   728GB   ext4
 7      979GB   983GB   4208MB  linux-swap(v1)
 4      983GB   984GB   1028MB  ntfs            Basic data partition          hidden, diag
 5      984GB   1000GB  15.8GB  ntfs            Basic data partition          hidden, msftdata


Model: Hitachi HTS547550A9E384 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End    Size   Type      File system  Flags
 1      1049kB  256MB  255MB  primary   ext2         boot
 2      257MB   500GB  500GB  extended
 5      257MB   500GB  500GB  logical                lvm

---

### Post by TheFu on 2018-02-17
Well - it is using lvm, so you'll need to learn about that.

and code tags look like this:
```

Model: Hitachi HTS547550A9E384 (scsi)
Disk /dev/sdb: 500GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags:

Number Start End Size Type File system Flags
1 1049kB 256MB 255MB primary ext2 boot
2 257MB 500GB 500GB extended
5 257MB 500GB 500GB logical lvm
```
See how everything lines up nice?

---

### Post by backfour94 on 2018-02-18
Excellent thanks, looks like I just needed to do vgchange -a y

---

### Post by TheFu on 2018-02-18
> **backfour94 said:**
> Excellent thanks, looks like I just needed to do vgchange -a y

If solved, please mark the thread "SOLVED" using the thread tools button at the top.

---

