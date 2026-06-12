---
title: "Resizing Boot partition"
date: 2014-11-08
forum: General Help
---

### Post by rare HERO on 2014-11-08
1. Is there a way to increase the size of the boot partition without doing a new install?

2. How to install with a sufficiently sized boot partition?

---

### Post by Impavidus on 2014-11-08
1: Theoretically, you can boot from a live disk, shrink the other partitions and then expand the /boot partition. However, as the boot partition is usually the first partition, you have to move the others to the right, which is slow. Even worse, the other partitions are usually LVM partitions (else there would be no need for a /boot partition), which makes matters even more complicated. Few people ever try.
2: Partition manually.

---

### Post by coffeecat on 2014-11-08
@rare HERO, time to let the old thread you posted to rest in peace. I've moved your post and the reply its own new thread.

---

### Post by yancek on 2014-11-08
If you posted the output of sudo fdisk -l and df -h, someone might have a suggestion.  It's likely that you will run into the problems mentioned above.  If your boot partition is filling up you might be able to resolve whatever problems you are having by removing some kernels.

---

### Post by rare HERO on 2014-11-10
> **yancek said:**
> If you posted the output of sudo fdisk -l and df -h, someone might have a suggestion.  It's likely that you will run into the problems mentioned above.  If your boot partition is filling up you might be able to resolve whatever problems you are having by removing some kernels.

```
sudo fdisk -l
Disk /dev/sda: 320.1 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders, total 625142448 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0004f281

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      499711      248832   83  Linux
/dev/sda2          501758   625141759   312320001    5  Extended
/dev/sda5          501760   625141759   312320000   83  Linux

Disk /dev/mapper/sda5_crypt: 319.8 GB, 319813582848 bytes
255 heads, 63 sectors/track, 38881 cylinders, total 624635904 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/sda5_crypt doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--gnome--vg-root: 311.4 GB, 311359963136 bytes
255 heads, 63 sectors/track, 37854 cylinders, total 608124928 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--gnome--vg-root doesn't contain a valid partition table

Disk /dev/mapper/ubuntu--gnome--vg-swap_1: 8434 MB, 8434745344 bytes
255 heads, 63 sectors/track, 1025 cylinders, total 16474112 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/mapper/ubuntu--gnome--vg-swap_1 doesn't contain a valid partition table
```

```
sudo df -h
Filesystem                          Size  Used Avail Use% Mounted on
/dev/mapper/ubuntu--gnome--vg-root  286G   21G  251G   8% /
none                                4.0K     0  4.0K   0% /sys/fs/cgroup
udev                                3.9G  4.0K  3.9G   1% /dev
tmpfs                               785M  1.3M  783M   1% /run
none                                5.0M     0  5.0M   0% /run/lock
none                                3.9G   34M  3.8G   1% /run/shm
none                                100M   56K  100M   1% /run/user
/dev/sda1                           236M  162M   62M  73% /boot
```

---

### Post by rare HERO on 2014-11-10
> **Impavidus said:**
> 1: Theoretically, you can boot from a live disk, shrink the other partitions and then expand the /boot partition. However, as the boot partition is usually the first partition, you have to move the others to the right, which is slow. Even worse, the other partitions are usually LVM partitions (else there would be no need for a /boot partition), which makes matters even more complicated. Few people ever try.
2: Partition manually.

Seems a bit behind my ability to do that. I'd still say I'm a linux novice. I was able to remedy my original problem, unable to update due to not enough free disk space on disk '/boot' by doing the following. 

```
sudo apt-get autoremove

sudo apt-get clean

sudo apt-get update
```

I installed Ubuntu Gnome 14.04 from the USB I created with the startup disk creator.

---

