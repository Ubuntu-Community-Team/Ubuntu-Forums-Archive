---
title: "want to increase ext3 and swap partitions"
date: 2007-08-14
forum: General Help
---

### Post by sippyCUP on 2007-08-14
I have xp pro and ubuntu 7.04 on my laptop, booting with grub. I decided that I want to make ubuntu my main OS, so I'd like to make the ext3 and swap partitions larger and pare my ntfs down. I can do all the resizing from acronis disk director in windows xp, but do I need to someone let linux know that I've resized my root partition and my swap file in order to prevent problems?

I backed up my system, and I already know that grub might crap out on me, but I'm prepared to boot with the live cd and chroot in to redo grub. What I really want to know is if there are any config files that have the partition size of the root partition or the swap set in stone that I need to change before booting back into ubuntu.

Thanks for your time,

Eric

---

### Post by shad0w_walker on 2007-08-14
As far as i am aware the size of your partitions isn't recorded anywhere that will screw up your system or stop it from running. I have never encountered any issues with changing root/swap/whatever partitions before and i did quite a bit of that not to long ago (About 9 resizes in 24 hours, don't ask)

---

### Post by merlinus on 2007-08-14
If /etc/fstab is listing your partitions with UUIDs, then these will most likely change upon resize.

If this happens, you will have to find the new ones via this:

```

sudo fdisk -l
blkid

```

The first will list the partitions and the second the UUIDs,  Compare the results and change in /etc/fstab if need be.

-merlin

---

### Post by sippyCUP on 2007-08-16
Thanks guys, I performed surgery and the results are perfect.

---

