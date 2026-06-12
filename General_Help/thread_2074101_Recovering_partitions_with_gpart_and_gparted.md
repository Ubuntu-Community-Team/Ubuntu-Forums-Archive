---
title: "Recovering partitions with gpart and gparted"
date: 2012-10-21
forum: General Help
---

### Post by newb85 on 2012-10-21
So, my brother's hard drive took a dive.

The computer manufacturer replaced the original HD when half of the sectors went bad.  That time, Gparted (Live CD) could see the different partitions, but couldn't mount them.

This time, Gparted shows the whole drive as unallocated, and the SMART data is "unsupported".  I'm assuming the same sort of problem (sectors going bad) has occurred, and this time, the partition table has been affected.

If that's the case, is there a way to use Gpart and Gparted to bring the partitions back up on a Live CD so that documents can be recovered?

Note: the partitions in question are NTFS (for Windows 7).

---

### Post by carl4926 on 2012-10-21
I use parted Magic
Open a terminal and get the result of

```
fdisk -l
```

---

### Post by newb85 on 2012-10-21
> **carl4926 said:**
> I use parted Magic

Good for you.  Any reason why?  Gpart is in the repos and Magic is not.

---

### Post by newb85 on 2012-10-21
```
fdisk -l
```
doesn't return anything.

```
sudo fdisk -l
```
returns:
```
Disk /dev/sda: 640.1 GB, 640135028736 bytes
255 heads, 63 sectors/track, 77825 cylinders, total 1250263728 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xd2e8d2e6

Disk /dev/sda doesn't contain a valid partition table
```

---

### Post by carl4926 on 2012-10-21
> This time, Gparted shows the whole drive as unallocatedOk
And you are saying that you know there is a partitioning scheme in place?
What are you expecting to be there?

---

### Post by newb85 on 2012-10-22
Yes, definitely.  The manufacturer restored the original partitioning scheme and OS last time, and nothing has been done to change that since.

I'm not absolutely certain, but I think it should look like this:
sda1 -   1.46GB - ntfs - boot, diag
sda2 - 580.59GB - ntfs - (Windows 7)
sda3 -  14.12GB - ntfs - hidden (recovery partition)

In Gparted, I hit Device>Attempt Data Rescue, and it's been "Searching for filesystems on sda" for about 12 hours, now.  For a 600GB drive, should it really take that long?

---

### Post by newb85 on 2012-10-22
@ 24 hours, I'm assuming it's never going to successfully identify the partitions.  

I'm throwing in the towel on this one.  Last time, half the sectors on the HDD were bad.  There has to be a point where software can't sort things out anymore, and I guess it has hit that point.

I'll see if the professional repair shop has any more luck recovering files.

---

### Post by newb85 on 2012-10-24
The drive still had 90% health, but the repair shop still found the data irrecoverable.  They tried three different recovery methods, and none worked.

---

### Post by Mark Phelps on 2012-10-24
Sorry I didn't see this thread sooner ... but my experience is that Windows-based data recovery programs tend to work better with Windows filesystems than do Linux-based recovery programs.

If you have a similar problem in the future with NTFS partitions, consider using RecoverMyFiles from Runtime Software, installed in Windows.  The scanning program is free; file recovery requires a paid license.

You would have to hook the drive up to a working Windows PC, but at least this way, you might be able to recover some files.

---

### Post by newb85 on 2012-10-24
As I said, I didn't have bootable Windows media on hand.  (They don't exactly ship them with pre-installed machines anymore.)

I would venture a guess that RecoverMyFiles was one of the methods the computer shop tried (unsuccessfully).

Thanks for the suggestions, though.

---

