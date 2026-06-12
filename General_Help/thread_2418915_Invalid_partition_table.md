---
title: "Invalid partition table"
date: 2019-05-13
forum: General Help
---

### Post by grieferrimix on 2019-05-13
After installing Ubuntu server onto my Dell Latitude E6430, whenever I try to boot from my drive it gives an error saying "Invalid partition table!" Pressing enter gets rid of the error and boots straight into the os. I'm booting from legacy because UEFI doesn't recognize the drive.

After running sudo fdisk -l I get

> 
Disk /dev/loop0: 89.4 MiB, 93720576 bytes, 183048 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/loop1: 91 MiB, 95408128 bytes, 186344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 698.7 GiB, 750156374016 bytes, 1465149168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: B774438B-AB4D-4449-B94A-D6BC4F9C0752


Device     Start        End    Sectors   Size Type
/dev/sda1   2048       4095       2048     1M BIOS boot
/dev/sda2   4096 1465145343 1465141248 698.6G Linux filesystem


Any and all help is appreciated, thank you!



[Solved]: Thank you u/HeidiH0 for the help!
[https://www.reddit.com/r/linuxquestions/comments/boayqd/invalid_partition_table/](https://www.reddit.com/r/linuxquestions/comments/boayqd/invalid_partition_table/)

---

