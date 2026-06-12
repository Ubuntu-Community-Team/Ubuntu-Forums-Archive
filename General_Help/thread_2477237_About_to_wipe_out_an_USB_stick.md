---
title: "About to wipe out an USB stick"
date: 2022-07-19
forum: General Help
---

### Post by satimis on 2022-07-19
Hi all,

Which will be an easy and safe way to wipe out an USB installer (Linux) so the total USB stick can be used for storage of Linux files.

Thanks

Regards

---

### Post by Impavidus on 2022-07-19
Any of the partitioning tools can do that. Wipe the drive and create one big partition to store files. If this is for Linux only, you can use a Linux filesystem. f2fs is made for flash drives. Classical filesystems like ext4 work too, but may be worse for drive life expectancy. They support permissions, which is often good, but can be a nuisance on removable drives (especially if you move it between two systems where you've got different user IDs). If this is also for Windows, use fat32 or exfat for larger drives. ntfs works too, but be prepared to format it whenever it gets corrupted. There's no repair option. The easiest GUI partitioning tool is gparted (not installed by default, except on live disks), but there are other tools, including command line.

---

### Post by ajgreeny on 2022-07-19
Depending on how the USB installer was created, ie, what application was used, you may find that simply wiping the partitions is not enough.

If that is the situation you can try either creating a new partition table using gparted, or you can use [mkusb]("https://help.ubuntu.com/community/mkusb") which is my go-to for both creating USB install disks and then returning the USB to mass-storage.

---

### Post by satimis on 2022-07-19
Hi all,

Thanks for your advice.

According to my recollection, it was created running "Make Startup Disk"

Regards

---

