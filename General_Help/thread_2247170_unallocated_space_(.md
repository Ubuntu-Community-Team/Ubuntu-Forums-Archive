---
title: "unallocated space :("
date: 2014-10-06
forum: General Help
---

### Post by pushpendra2 on 2014-10-06
Guys, Help me with this unallocated space. I have installed ubuntu 14.04 along windows 7.

---

### Post by slickymaster on 2014-10-06
*Moved to the ***General Help*** sub-forum*

---

### Post by pushpendra2 on 2014-10-06
Okay

---

### Post by ibjsb4 on 2014-10-06
What do you want to do with it?

---

### Post by pushpendra2 on 2014-10-06
want to add in new disk or extent windows c drive.

---

### Post by ibjsb4 on 2014-10-06
> want to add in new disk
I do not know what that means.
> or extent windows c drive.
There is no 'c' drive.  Your HDD is 'sda', your partitions are 1 thru 7.

---

### Post by btindie on 2014-10-06
Windows has already consumed 3 out of the 4 primary partitions that you're allowed.

So the only way to make that unallocated space usable would be to extend your 'extended' partition (sda4) to consume that space and then create a new extended partition within it.

---

### Post by yancek on 2014-10-06
You should back up any important data before changing partitions as there is always a risk involved.  Using GParted, click on sda4 to highlight it then click the partition tab and select resize to the new size.

---

### Post by pushpendra2 on 2014-10-06
hmm in windows it showing 1 primary for windows boot, one for recovery, and rest 2 are for ubuntu.

well I have tried what you suggested but sda 4, 6 and sda 7 are not getting extended. I mean its showing their bars are not moving.

---

### Post by btindie on 2014-10-06
> **pushpendra2 said:**
> hmm in windows it showing 1 primary for windows boot, one for recovery, and rest 2 are for ubuntu.

It doesn't matter what windows is showing, the fact is that you've currently got 3 NTFS primary partitions, and 1 Extended partition. Windows may be including your 2 ext4 Logical partitions in that count while hiding the other primary NTFS ones.

An Extended partition is a container for additional Logical partitions. To make that space available, under GParted, right click on your Extended partition /dev/sda4 and select Resize/Mode. You should then be able to increase the size of it to the right to occupy the free space.

You can then add a new Logical partition within you Extended partition.

---

### Post by pushpendra2 on 2014-10-06
Yes that's what I have tried but sda 4 is not moving, Isspite the fact that recovery is extending in back direction but that leaves recovery of no  use.

---

### Post by mcduck on 2014-10-06
You can't move the extended partition if any of the contained logical partitions are in use. Which means you'll have to do the partition edits while running from a live-CD/USB, and also make sure to unmount the swap partition first...

(So, all sda5, sda6 and sda7 must be unmounted before you can change sda4 in any way. )

---

### Post by Impavidus on 2014-10-06
> **pushpendra2 said:**
> want to add in new disk or extent windows c drive.By "disk" or "drive" we mean the physical thing on which you can make partitions. Windows always confuses the terms so we can forgive you that you confused them too.

Adding the unallocated space to the C partition is tricky. The extended partition with the Ubuntu partitions in it is inbetween, so that would mean moving them to the right, which is a slow and dangerous operation. But there are two other options. You can expand your /home partition (that's not what you asked for but I give it as a bonus option) or you can create a data partition. The advantage of creating a data partition is that it allows you to share files between Windows and Ubuntu without mounting the C partition. Mounting C partitions is a risk as NTFS partitions are easely corrupted, which can be a problem if it contains the Windows system files. So, many use a shared data partition separate from the C partition. Expanding the /home partition just gives you more storage space in Ubuntu.

In either case you have to boot from your live disk. Open gparted, right-click on the swap partition and select "swap off" and expand the extended partition (/dev/sda4) into the unallocated space. Then either expand the /home partition or create a new partition for shared data inside the extended partition. This shared data partition must be of type NTFS.

---

### Post by wantdownload on 2014-10-06
I'd say back up and repartition your drive, this should fix the unallocated space as I'm pretty sure there's not any other options. Use GParted.

---

