---
title: "XP Partition not mounting and can not boot"
date: 2008-03-06
forum: General Help
---

### Post by austin286 on 2008-03-06
I installed Ubuntu 7.10 and dual booted with XP MCE. Well, windows got rid of the GRUB bootloader causing me to not boot ubuntu. well, i re-installed grub and now XP MCE will not boot. it comes up in the boot menu, but will not boot. Ubuntu treats the XP partition as an unmounted drive and it will not mount it. i get an error that states: 
"Unexpected clusters per mft record (-1). Failed to mount '/devsda1': Invalid argument The device '/dev/sda1" doesn't have a valid NTFS. Maybe you selected the wrong device? Or the whole disk instead of a partition (e.g. /dev/hda, not /dev/hda1)?"
Please help. Im still new to linux but have a large knowledge of computers, and i still need files the are on the XP partition. Thanks!

---

### Post by breakerfall on 2008-03-06
hmm...
whats your partition setup look like?

```

sudo fdisk -l /dev/sda

```
will list the partitions on sda, assuming the drive in question _is_ sda...
sda will usually be the first (or only) sata drive on newer systems..

---

### Post by austin286 on 2008-03-06
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x32543254

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        8423    67657716    7  HPFS/NTFS
/dev/sda2            8424        9729    10490445   83  Linux

---

### Post by tbadal09 on 2008-03-08
hi! i have dell inspiration 530 that orignally came with ubunto, tried to install XP home won't work. and after couple of unsuccessful attempts, i finally got it to work but have to get rid of ubuntu. once xp home was up and running and tried to install ubuntu it was piece of cake but the next morning window will show up in boot menu but would not load . any help please.
i think it is somthing with dell computers. not sure.

---

