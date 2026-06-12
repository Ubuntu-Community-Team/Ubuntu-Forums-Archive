---
title: "How can I add missing partition numbers (similar to renumbering)"
date: 2021-04-15
forum: General Help
---

### Post by sofasurfer on 2021-04-15
My partitions are numbered sda(1) sda(2) sda(6) sda(5).
I learned how to reorder them to read sda1,2,5,6. using fdisk.
But I am still missing the 3 and 4. Is there a way renumber them so they read sda 1,2,3,4. (eliminating the 5 and 6?

---

### Post by oldfred on 2021-04-15
Not recommended.
And renumbering often causes issues for anything that is using device like /dev/sdX.
Most now use UUID, and that should not change, but if that changes, you have major issues.

You should show the output of these:
sudo fdisk -lu
sudo parted -l

It looks like you are using the very old MBR(msdos) partitioning. That has 4 primary partitions. One primary partition can be an extended partition which in effect is the container for as many logical partitions as you want. But primary partitions must be  1 thru 4. And logical partitions must start at 5 whether you use all 4 primary partitions or not. 
You could convert 5 & 6 to primary partitions, but then are locked into only having 4 partitions.

The longer term solution is not to use MBR, but to use gpt partitioning. I have used gpt with Ubuntu since 2010, but Windows in BIOS boot mode requires MBR. Windows also requires gpt for UEFI boot. But usually conversion erases a drive, or at minimum required grub re-install & editing of many system UUIDs & device settings. Conversion is better for data only drives, but good backups still required.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901) & 
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

gpt(GUID) [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)
MBR(msdos) [http://en.wikipedia.org/wiki/Master_boot_record](http://en.wikipedia.org/wiki/Master_boot_record)

---

