---
title: "Changing ext3 partition size with Gparted"
date: 2007-10-10
forum: General Help
---

### Post by ToyotaDiesel on 2007-10-10
Ubuntu 7.1 beta

When installing, I swear I set the linux partition to 28GB, leaving roughly 12GB to the XP partition, but after it installed the ext3 was only 8, and the FAT part was 26!  Either way, I installed Gparted and was able to drop the fat partition back to 12, but I cant figure out how to expand the ext3 part to take up the newly unallocated space.  I see it's locked...is there any way around this?

Thanks in advance.

---

### Post by logos34 on 2007-10-10
It's locked because it's mounted--can't resize mounted partition.

Use gparted from the ubuntu live cd.

---

### Post by az on 2007-10-10
Another reason is that you are trying to move the beginning of a partition.  Parted can't do that.  It can only resize from the end.  You can copy the partition to the free space, delete the original and then extend the copy.

This may rename your partition, so edit your fstab (if needed) and grub menu.list and reinstall grub.

---

### Post by ToyotaDiesel on 2007-10-10
Ouch.  I'm building a dual boot machine, with Ubuntu (hopefully) having the lion's share of the 40GB drive.

Should I have installed ubuntu 1st, then XP, which would put ubuntu at the front of the disk?  Wonder if that would have made things simpler....

I can nuke everything and start over i guess.  I'm really confused why what is going on during the partition sizing when ubuntu installed.  This is the 2nd install i've done where the partition sizes turned out to be NOTHING close to what I told the partitioner during install....

Thanks for your help.

---

### Post by logos34 on 2007-10-10
> **az said:**
> Another reason is that you are trying to move the beginning of a partition.  Parted can't do that.  It can only resize from the end.

Sure it can.  At least the newer versions can (0.3.4). 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

---

### Post by ToyotaDiesel on 2007-10-10
> **logos34 said:**
> Sure it can.  At least the newer versions can (0.3.4). 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

MAN you are a life saver!  OK, at least a day saver.  Gparted from the link you posted did the trick.  I've attached the shot of the new partitions.  Thanks again!

---

### Post by FuturePilot on 2007-10-10
> **logos34 said:**
> Sure it can.  At least the newer versions can (0.3.4). 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

Yep it can. Takes extremely long though.

---

### Post by ToyotaDiesel on 2007-10-10
It resized my partition and moved 5+ gigs of data in minutes.  Saved me HOURS of vaulable time....

---

### Post by az on 2007-10-11
> **ToyotaDiesel said:**
>  This is the 2nd install i've done where the partition sizes turned out to be NOTHING close to what I told the partitioner during install....


When you resize a partition using the installer, you are choosing the new size for the old partition, and not the size of the new partition.  Perhaps this is the confusion?  You are not the first person to describe that issue - it is confusing.

> **logos34 said:**
> Sure it can.  At least the newer versions can (0.3.4). 

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=173828)

W00t!  It's about time!

---

### Post by ToyotaDiesel on 2007-10-11
> **az said:**
> When you resize a partition using the installer, you are choosing the new size for the old partition, and not the size of the old partition.  

You have my complete attention, but i don't totally understand your statement.  Is there a typo maybe?

Are you saying that when the partitioner asks for a value during install, that value is the resized (smaller) size for the existing partition, NOT for the new size of the ubuntu partition.  Correct?

---

### Post by az on 2007-10-11
> **ToyotaDiesel said:**
> You have my complete attention, but i don't totally understand your statement.  Is there a typo maybe?

Are you saying that when the partitioner asks for a value during install, that value is the resized (smaller) size for the existing partition, NOT for the new size of the ubuntu partition.  Correct?

Typo, sorry.  Talk about confusing......

I fixed it:
"When you resize a partition using the installer, you are choosing the new size for the old partition, and not the size of the new partition. Perhaps this is the confusion? You are not the first person to describe that issue - it is confusing."

---

### Post by ToyotaDiesel on 2007-10-11
Cool.  Thanks.  I'm doing a lot of these installs, and I'm trying to streamline the process.  Thanks again.

---

