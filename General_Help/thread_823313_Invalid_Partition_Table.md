---
title: "Invalid Partition Table"
date: 2008-06-09
forum: General Help
---

### Post by raghavneon on 2008-06-09
i tried to instaall xp after ubuntu8.04 but after putting the xp cd it copied files into my partition as usual changed by ubuntu grub..but before installation wen goingg into the comp it says invalid partition table......................pls help me i want to install xp on the 10.3 gb ntfs partition i have given in the screen shot

---

### Post by mdurham on 2008-06-09
I would suggest making partition 1 for XP and moving the swap to partition 2.
I believe XP prfers to be installed on the first partition.
Cheers, Mike

---

### Post by ne0h on 2008-06-09
It seems you have 3 primary partition on a HD!:shock: Anyway, as you mentioned, you want to install /dev/sda2 I think (closest to your stated 10.3 GB). Get a bootable XP CD. Boot from it, after some initial checkings it'll show a screen mentioning the install drive. Press Escape in that screen, the setup will throw you a screen with all the partitions in your HD with size, FS type details. Then just choose your desired partition to install (if you dont recognize your partition - better calculate the size and confirm.)

Good Luck!

---

### Post by dburnett77 on 2008-06-09
> **raghavneon said:**
> i tried to instaall xp after ubuntu8.04 but after putting the xp cd it copied files into my partition as usual changed by ubuntu grub..but before installation wen goingg into the comp it says invalid partition table......................pls help me i want to install xp on the 10.3 gb ntfs partition i have given in the screen shot

Windows error.  The first NTFS partition you showed in your screen grab says you only have 50 megabytes, on a ~9 gigabyte drive.

You could try to re-size it.  Or delete non-essential prog's.

The bootloader wants a swap, per windows requirements, and it's flagging.

---

