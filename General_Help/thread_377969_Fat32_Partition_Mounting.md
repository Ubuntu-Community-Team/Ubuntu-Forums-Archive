---
title: "Fat32 Partition Mounting"
date: 2007-03-06
forum: General Help
---

### Post by g3brownsc on 2007-03-06
I know there have been a thousand posts about how to do this, but i genuinely have never seen anything like this before. I want to mount my Windows Me partition, but i cant figure out which one(s) to add to the fstab.

g3brownsc@g3brownsc-laptop:~$ sudo fdisk -l

Disk /dev/hda: 40.0 GB, 40007761920 bytes
255 heads, 63 sectors/track, 4864 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        2194    17623273+   c  W95 FAT32 (LBA)
/dev/hda2            4415        4864     3614625    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hda3   *        2195        4414    17832150   83  Linux
/dev/hda5            4508        4864     2865208+   c  W95 FAT32 (LBA)
/dev/hda6            4415        4507      746959+  82  Linux swap / Solaris

Partition table entries are not in disk order

Disk /dev/sda: 254 MB, 254410752 bytes
16 heads, 48 sectors/track, 647 cylinders
Units = cylinders of 768 * 512 = 393216 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1         647      248419+   e  W95 FAT16 (LBA)

I'm sure the fix is simple and that i'll bash my head on the table repeatedly after being given the answer, but please help.

---

### Post by yabbadabbadont on 2007-03-06
I would guess hda1 and hda5.

---

### Post by g3brownsc on 2007-03-06
Thanks for the reply. So what do i add to etc/fstab to get that to automatically appear on my desktop when i login?

---

### Post by yabbadabbadont on 2007-03-06
[http://www.psychocats.net/ubuntu/mountwindows](http://www.psychocats.net/ubuntu/mountwindows)

That's the website of one of the moderators.  Lots of Ubuntu goodness there.  ;)

---

### Post by halw on 2007-03-06
[https://help.ubuntu.com/community/MountingWindowsPartitions]("https://help.ubuntu.com/community/MountingWindowsPartitions")

I used the instructions in the above link. Works like a champ.

---

### Post by g3brownsc on 2007-03-07
I read those howtos, but still am unclear on how to change the config file i included in my first post. I understand that 6.10 changed how that file is displayed, and was wondering if someone could actually show me the exact changes i would need to make. I absolutely cannot afford to mess up my partitions, and i was hoping you guys could show me how to edit it and get it right.
Thanks

---

