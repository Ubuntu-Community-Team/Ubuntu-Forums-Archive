---
title: "Can't Boot!!!! Help!!!!!"
date: 2006-12-06
forum: General Help
---

### Post by jdogg707 on 2006-12-06
So I have been using 6.10 since release as a file/media server with no problems.  I have a hardware RAID 5 array consisting of 4 500GB drives, with one large / partition where all my data is located.  Yesterday one of the drives in my RAID array goes bad, I rebuild it, and when the system boots back up it throw a "Disk Boot Failure...etc." error.  I check to make sure the array is working correctly, check the consistency of the drives, and get the same problem.  I used the system disc to load the Live CD and run terminal.  fdisk -l gives me the following info:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500307783680 bytes
255 heads, 63 sectors/track, 182402 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500102594560 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

Gpart doesn't even see partitions on the discs!  I am pretty new to Linux in general, so some help in resolving this would be amazing!  I have over 500GB of media I really don't want to lose!

---

### Post by dcstar on 2006-12-06
> **jdogg707 said:**
> So I have been using 6.10 since release as a file/media server with no problems.  I have a hardware RAID 5 array consisting of 4 500GB drives, with one large / partition where all my data is located.  Yesterday one of the drives in my RAID array goes bad, I rebuild it, and when the system boots back up it throw a "Disk Boot Failure...etc." error.  I check to make sure the array is working correctly, check the consistency of the drives, and get the same problem.  I used the system disc to load the Live CD and run terminal.  fdisk -l gives me the following info:

```
ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 1500.3 GB, 1500307783680 bytes
255 heads, 63 sectors/track, 182402 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sda doesn't contain a valid partition table

Disk /dev/sdb: 500.1 GB, 500102594560 bytes
255 heads, 63 sectors/track, 60800 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Disk /dev/sdb doesn't contain a valid partition table

```

Gpart doesn't even see partitions on the discs!  I am pretty new to Linux in general, so some help in resolving this would be amazing!  I have over 500GB of media I really don't want to lose!

On second thoughts, if Linux reports two separate drives now (instead of one), then the second drive is not part of the RAID 5 array - Linux should only see one drive which contains all 4 physical drives.

It looks very much like you haven't "rebuilt" your array correctly, and it may well be that you have wiped it.

---

### Post by jdogg707 on 2006-12-06
> **dcstar said:**
> On second thoughts, if Linux reports two separate drives now (instead of one), then the second drive is not part of the RAID 5 array - Linux should only see one drive which contains all 4 physical drives.

It looks very much like you haven't "rebuilt" your array correctly, and it may well be that you have wiped it.

Sorry, the second drive is a fifth drive I have setup, it is separate from the RAID 5 array and was meant to be added as a hot spare, but currently is setup as a /Home Directory.  It is suffering from the same problems, and since it is not a part of the array, it can't be the rebuilding of one drive that caused the problem.

---

### Post by jdogg707 on 2006-12-06
Anyone else have an idea?

---

### Post by jdogg707 on 2006-12-06
up for a resolution!

---

