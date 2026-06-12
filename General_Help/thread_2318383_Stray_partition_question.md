---
title: "Stray partition question"
date: 2016-03-25
forum: General Help
---

### Post by ra7411 on 2016-03-25
I've got a stray partition (sda2) that I'd like to incorporate into another (sda3) /home.

Oddly, on terminal w/ lsblk command, it shows up as 1K; on disks and gparted it's 100+gb. It's unmounted.

On this install, the o/s  /  is sda6 and separate from /home sda3.

Gparted's info says it's "Busy (At least one logical partition is mounted)" and the commands for delete, resize/move are all light gray inactive.

I'm not short on disk space, so I don't want to do anything that might  wreck any partitions.

There's a pic attached showing what I'm seeing from the various sources.
Any ideas? Just leave it alone?

Thanks

---

### Post by deadflowr on 2016-03-25
/dev/sda2 is actually the partitions /dev/sda6 and /dev/sda5.
/dev/sda2 is an extended partition which is a house (of sorts) for the sda5 and sda6 partitions.

So to resize /dev/sda2 you will need to shrink those (more likely, is you will only need to resize the /dev/sda6 partition.)
You would need to do this unmounted.
To do that you would need to boot from a secondary system.
Most people  would use the Ubuntu livecd, since you can run gparted from there, and it will not mount the file systems.

(since you have a swap partition, the livecd might try to mount that, you will need to turn that off.
To turn of the swap partition in a livecd, simply right click on it and choose the option in the dropdown for swapoff)


That said, I see no reason to resize it anyway.
You've already set a sizable home partition.
and even though some would probably say 100 GB root (/) parttion is rather large.
I find it to be quite adequate.
It gives you plenty of leeway to work with.


I'm not sure if this makes sense or not.
hope it does

---

### Post by yancek on 2016-03-25
> I've got a stray partition (sda2) that I'd like to incorporate into another (sda3) /home.

No you don't, explained by deadflwr.  Leave it alone or you will wreck your system.

---

### Post by grahammechanical on 2016-03-25
To put it another way.

You have, like me, MBR partitioning. That means we are only allowed 4 primary partitions. To get around this we use one of the allocated 4 primary partitions as a special primary partition called an Extended partition. Inside the extended partitions we can create any number of logical partitions.

You have an unusual set up. If you do not mind me saying so. The home partition (sda3) is a primary partition and Ubuntu is sda6 that is inside the extended partition (sda2). So, deleting sda2 will delete Ubuntu. You may not be allowed to delete sda2 until you have first deleted all logical partitions inside sda2. I do not know. I have never tried doing that.

Even if things were the other way around with the home partition (sda3) inside the extended partition (sda2) you would still break Ubuntu by deleting sda2 and the home partition along with it.

Regards.

---

### Post by ra7411 on 2016-03-25
Since it works, I think I'll just leave it alone.

---

### Post by yancek on 2016-03-25
>  			 			Since it works, I think I'll just leave it alone. 		

Smart move.

---

