---
title: "One Swap Partition for Two Ubuntus, Changing Partition"
date: 2007-06-06
forum: General Help
---

### Post by DeathOnJuice on 2007-06-06
I'm setting up a separate install of Ubuntu for MythTV, and I have two questions about how to configure the swap.

1. Can I use the same swap partition for both installs?

2. When I first installed Ubuntu, it made the swap partition a logical partition completely filling an extended partition. I really don't see the point of this, other than wasting the one extended partition I get per hard drive. Can I simply delete the partition, make a primary one in its place formatted as swap, and change my /etc/fstab accordingly to fix this?

Thanks.

---

### Post by mcduck on 2007-06-06
1. Yes, all Linux installs can share the same swap partition. The only problem is if you use Suspend-To-Disk, as it stores it's data into swap (so suspending one Linux install, and booting into other would destroy the first ones suspend data).

2. Yes, you could do that. But you would also have to edit /etc/fstab to point to correct swap partition, and probably also use the mkswap command to make your new partition into swap. Also, keep in mind that you can only have 4 primary partitions, or 3 primary ones and one extended containing as many logical partitions as you want.

---

### Post by H.E. Pennypacker on 2007-06-06
1.   I have done a forum search on this, and others have reported it is absolutely fine.  Here's the thread:

[http://ubuntuforums.org/showthread.php?t=447109&highlight=share+swap+partition](http://ubuntuforums.org/showthread.php?t=447109&highlight=share+swap+partition)

2.  Swap should be a logical partition.  It should be part of an extended partition dedicated to Ubuntu.  That Ubuntu extended partition should include three logical partitions: home, root, and swap.  You can have a max of four extended partitions per hard drive.

You can always delete the swap partition, and start over.  It's not like you're losing something, but make sure you get it back.  At this point, I am not expecting any fstab problems, but if problems do occur, you can always, of course, modify fstab, and fix whatever is needed.

---

### Post by DeathOnJuice on 2007-06-06
Pennypacker, only the swap partition is inside the extended partition. Why is it necessary to have an extended partition?

Also, I'm pretty sure you can only have one extended partition.

Thanks for the help! Can anyone clarify on this point?

---

### Post by mcduck on 2007-06-06
> **DeathOnJuice said:**
> Pennypacker, only the swap partition is inside the extended partition. Why is it necessary to have an extended partition?

Also, I'm pretty sure you can only have one extended partition.

Thanks for the help! Can anyone clarify on this point?

Ubuntu doesn't need any extended/logical partitions, and you only need 2 partitions, root and swap. Both can be primary ones :)

(Of course separate home partition is nice if you reinstall often. I prefer having a separate storage partition instead, so I can easily share my files between different Linux installs without having problems caused by all the configuration files that are kept inside home.)

---

### Post by H.E. Pennypacker on 2007-06-07
> Pennypacker, only the swap partition is inside the extended partition. Why is it necessary to have an extended partition?

It looks like you're right about only having one extended partition.  The limit, however, is four primary partitions.

You can have all partitions (home, root, swap) as separate primary partitions, but for organizational purposes, I would say it is better to keep them under one extended partition.

---

