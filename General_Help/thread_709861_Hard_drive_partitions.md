---
title: "Hard drive partitions"
date: 2008-02-27
forum: General Help
---

### Post by patrickaupperle on 2008-02-27
I ran sudo fdisk -l and the output shows:

Disk /dev/sda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x000b4dd8

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        6992    56163208+  83  Linux
/dev/sda2            6993        7296     2441880    5  Extended
/dev/sda5            6993        7296     2441848+  82  Linux swap / Solaris


Why are there three partitions?
I only have Ubuntu.

---

### Post by kaginken on 2008-02-27
That's the ubuntu way!  Swap is like windows 'pagefile' or virtual memory, then the boot partition...

---

### Post by mrsteveman1 on 2008-02-27
Technically there are only 2 true partitions.

sda2 is actually a wrapper for an extended partition table, which is why your swap partition is sda5 and not 3 (ext partitions always start at 5).

---

### Post by patrickaupperle on 2008-02-28
> **mrsteveman1 said:**
> Technically there are only 2 true partitions.

sda2 is actually a wrapper for an extended partition table, which is why your swap partition is sda5 and not 3 (ext partitions always start at 5).

Thank you, That is what I was wandering. What is an extended partition?

---

### Post by mrsteveman1 on 2008-02-29
Normally hard drives can be split into 4 partitions and no more because the space at the start of the drive (where the partition table is), isn't big enough to handle the data for more than 4 partitions.

The pseudo answer to this problem has been to use extended partitions, which further divides one of the partitions into multiple partitions. Basically the extended partition is given its own specific ID (as opposed to 83-linux or 07-ntfs) so that operating systems know there are multiple partitions inside it, then there is another sort of partition table inside the extended partition that tells the OS how it is divided.

Inside the extended partition you have logical volumes/partitions, which can be used just like normal partitions with the exception that you cant boot from them, since the BIOS has no idea how to read them.

It's a crude hack to a problem that has gone on way too long. Hopefully HP and the rest will switch to using EFI and GUID soon like Apple has, which will make life much easier for everyone.

---

### Post by patrickaupperle on 2008-02-29
> **mrsteveman1 said:**
> Normally hard drives can be split into 4 partitions and no more because the space at the start of the drive (where the partition table is), isn't big enough to handle the data for more than 4 partitions.

The pseudo answer to this problem has been to use extended partitions, which further divides one of the partitions into multiple partitions. Basically the extended partition is given its own specific ID (as opposed to 83-linux or 07-ntfs) so that operating systems know there are multiple partitions inside it, then there is another sort of partition table inside the extended partition that tells the OS how it is divided.

Inside the extended partition you have logical volumes/partitions, which can be used just like normal partitions with the exception that you cant boot from them, since the BIOS has no idea how to read them.

It's a crude hack to a problem that has gone on way too long. Hopefully HP and the rest will switch to using EFI and GUID soon like Apple has, which will make life much easier for everyone.

Thank you for the reply. I am still a bit confused, but now I know enough to get the basic idea. 
On the same line as the original post is this (screenshot) the same thing as the partiton number 2, or is it something different? If it is different, what is it?

---

### Post by patrickaupperle on 2008-03-01
I wouldn't normally bump this, but I posted this when not too many where on.

---

### Post by mrsteveman1 on 2008-03-01
The screenshot you posted is showing the filesystems on the system, root is at the top and NFS is below it.

If you want to know why you need more than one partition, the other one is a swap partition which the system uses if it runs out of ram memory, and also for hibernation.

---

### Post by patrickaupperle on 2008-03-01
> **mrsteveman1 said:**
> The screenshot you posted is showing the filesystems on the system, root is at the top and NFS is below it.

If you want to know why you need more than one partition, the other one is a swap partition which the system uses if it runs out of ram memory, and also for hibernation.

I understand the swap partition now. Why are there two file systems?

---

### Post by mrsteveman1 on 2008-03-01
Its listing NFS as being mounted because NFS is technically a filesystem in a way. If you aren't actually using it just ignore it.

I think ubuntu might do that automatically

---

### Post by patrickaupperle on 2008-03-01
Ok Thankyou.

---

