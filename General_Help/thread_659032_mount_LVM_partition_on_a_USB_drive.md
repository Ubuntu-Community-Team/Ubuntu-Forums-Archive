---
title: "mount LVM partition on a USB drive?"
date: 2008-01-05
forum: General Help
---

### Post by jabster on 2008-01-05
Hi.

I have a ubuntu server on which at least one of the drives is bad. It had two drives.

I have purchased a new drive, and am trying to copy files over from the old drives to a backup USB drive. I am currently using a IDE-USB adapter to plug these old drives into my desktop machine (kubuntu).

Problem is, I had the two drives setup using LVM, and now see no way of accessing the LVM partitions. I can't even fsck them, as they aren't recognized as ext2 filesystems.

Is there any way to mount these partitions on my kubuntu machine and recover the files?

Do I need to install LVM on my kubuntu box? Would LVM work with USB drives? Or is there a "mount -t lvm" option?

thanks,
john

---

