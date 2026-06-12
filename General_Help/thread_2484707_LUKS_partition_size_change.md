---
title: "LUKS partition size change"
date: 2023-03-07
forum: General Help
---

### Post by shad2022 on 2023-03-07
I would like to change the size of a LUKS partition on a cloned ssd to max (new ssd is twice as big as the old one). Clonezille just cloned 1:1. Does changing the partition size with GParted break encryption or has it any downsides? I ask because it is not clear to me how this is technically possible regarding the encryption. Is the new data then stored encrypted, too?

---

### Post by TheFu on 2023-03-07
While possible, there is more accounting required than most people will like or handle.  Also, different file systems will have different header sizes and the blocksize of the physical storage device will matter.

It will be much easier and safer to just backup all the data, then resize the partitions without any consideration for what's inside, then re-setup the LUKS container and inside that, re-setup the LVM PVs, VGs, and LVs, as you desire.  I can't imagine using LUKS without LVM or ZFS. I suppose people do but I wouldn't.

If this is the drive that holds the OS that gets booted, It is even a less good idea to manually try to expand it.  I've done that, but was never really certain the values used for all the different moving parts weren't going to cause data loss.  It took me about a hour to come up with the plan and run the commands. Nothing was checking my work and at the level of the commands, I could have completely trashed the storage, making it useless.

---

### Post by MAFoElffen on 2023-03-07
RE: [https://help.ubuntu.com/community/ResizeEncryptedPartitions](https://help.ubuntu.com/community/ResizeEncryptedPartitions)

With native encrypted ZFS, is same a non-encrypted pool, except you unlock to work with... ZFS to enlarge, just 'add' partitions or drives to a pool. ZFS is '*different*' with resizing to smaller. You can do it online, but steps are: Create a snapshot. Create new pool (of different/smaller size). Restore snapshot to new pool. Test. Remove old pool.

---

### Post by TheFu on 2023-03-07
A pool is like a VG, I suppose.  It is possible to do the same with VGs or LVs or PVs.  But most people don't leave sufficient empty space on existing storage to create a new VG of the same or larger size on the same disk.

Now, if moving to a new disk, that opens up all sorts of possibilities.  Create a new LUKS container on a partition the size you want - I generally use the whole drive, minus about 1G for EFI/Grub stuff.  Then use the pvmove command to move the entire running PV from drive A to drive B inside the LUKS containers.  I've done this a few times. The systems can remain running the entire time while the PV is relocated bringing the VG and LVs it contains too.  A snapshot or snapshots for each LV wouldn't hurt, but they aren't necessary.  I'd rather see full backups.

---

### Post by MAFoElffen on 2023-03-08
@TheFu

I have done what you described, live on LVM to a new drive that I setup as a new root drive. LOL. That was an adventure.

That experience really showed me how flexible LVM2 was and 'sold me' on using it for over a decade. Also why I still install VM Guest systems with LVM. Gives the user the ability to do a lot of things to adapt.

---

### Post by shad2022 on 2023-03-09
Thank you for sharing your thoughts on this topic. I will do a clean install and I will give EndeavourOS a try on that machine (wanted to try that out since a few months).

---

