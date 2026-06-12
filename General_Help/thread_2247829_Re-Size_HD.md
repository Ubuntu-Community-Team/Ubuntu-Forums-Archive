---
title: "Re-Size HD"
date: 2014-10-10
forum: General Help
---

### Post by Don DeGregori on 2014-10-10
I'm trying to re-size my dual boot system hard drive. I've used G-Parted before, but must be doing something wrong.

Attached is what  G-Parted looks like now. I want to increase size of sda1 to 75 GB. I use LiveCD to get access to what I want to do, but G-Parted does not allow me to increase the size beyond what it is now. I could increase the size of sda6 with no problem, but I don't want to do that. I just want ti increase size of sda1. Please help...Thanks

---

### Post by Dennis N on 2014-10-10
sda1 is mounted and cannot be resized until you unmount it. You can tell by the little 'mounted' symbol in the "partition" column after the partition name. In the image, it shows sda1, sda2 and sda5 are mounted.

---

### Post by Don DeGregori on 2014-10-10
Thanks Dennis,

Looks like you helped me fix my confusion. Also needed to do a swap off. Now I can re-size sda1 !      :p

---

### Post by jamesisin on 2014-10-10
Please mark your thread as Solved if it is so.

---

### Post by yancek on 2014-10-10
I would think you would first need to resize the Extended partitions (sda2) by moving it to the right before you will have any unallocated space between it and sda1 to expand sda1.  Never actually done that myself but in this case I would not think it would be difficult as you have a lot of free space at the beginning of sda2 so no data to move.

---

### Post by Dennis N on 2014-10-10
Next time you make a partition table, consider GPT instead of MSDOS. It works with BIOS systems as well as UEFI, and eliminates the need for extended and logical partitions. All partitions are primary partitions, and you can create 128 primary partitions by default. There is also a backup partition table maintained on the disk for insurance.

---

