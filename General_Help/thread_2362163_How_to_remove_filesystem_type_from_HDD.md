---
title: "How to remove filesystem type from HDD"
date: 2017-05-25
forum: General Help
---

### Post by courtney2 on 2017-05-25
I had a blank HDD and made the filesystem on it btrfs for lxd containers using mkfs. However, now my issue is I just want to completely remove this filesystem type. I've done new partition tables with parted and fdisk and cfdisk and the filesystem just flat out won't go away to a plain unallocated disk. I'm CLI only right now. Any help eliminating any type of filesystem on this disk?

---

### Post by pruda on 2017-05-25
So you want to start fresh, right? Try ```
sudo dd if=/dev/zero of=/dev/sdX bs=1M count=100
sudo partprobe #or sudo reboot ;-)
``` which will **overwrite** first 100MB of the desired hard disk. Make sure you replace X with correct device letter (example: /dev/sdb).

---

### Post by Bucky Ball on 2017-05-25
> **pruda said:**
> Make sure you replace X with correct device letter (example: /dev/sdb).

+1. Double indeed. If you go for the wrong target, the target will be obliterated. 'dd' takes no prisoners (which is why it is also fondly known as 'disk destroyer', among other things ...).

---

### Post by shridhar-kapshikar on 2017-05-25
You can use fdisk utility to delete the brts partition:
```
 fdisk /dev/<device>
```

For example here are help options of fdisk utitlity  in Ubuntu 16.04 LTS
```

Help:


  DOS (MBR)
   a   toggle a bootable flag
   b   edit nested BSD disklabel
   c   toggle the dos compatibility flag


  Generic
   d   delete a partition
   F   list free unpartitioned space
   l   list known partition types
   n   add a new partition
   p   print the partition table
   t   change a partition type
   v   verify the partition table
   i   print information about a partition


  Misc
   m   print this menu
   u   change display/entry units
   x   extra functionality (experts only)


  Script
   I   load disk layout from sfdisk script file
   O   dump disk layout to sfdisk script file


  Save & Exit
   w   write table to disk and exit
   q   quit without saving changes


  Create a new label
   g   create a new empty GPT partition table
   G   create a new empty SGI (IRIX) partition table
   o   create a new empty DOS partition table
   s   create a new empty Sun partition table




Command (m for help): 

```

---

