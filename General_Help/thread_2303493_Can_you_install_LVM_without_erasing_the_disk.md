---
title: "Can you install LVM without erasing the disk?"
date: 2015-11-19
forum: General Help
---

### Post by Drenriza on 2015-11-19
Hi all

I have a quick question that i cant seem to find a straight answer to.

If you install Ubuntu 12.04 (virtual machine) without LVM from the get go, is it than possible later on. To install LVM on a disk without erasing what is already on it and than extending the size of it without loosing data already on the disk?

I see several examples on install LVM on a new disk, but none on a disk that contains data before hand.

Edit
Intersting that here is an article here [https://geekpeek.net/resize-filesystem-fdisk-resize2fs/](https://geekpeek.net/resize-filesystem-fdisk-resize2fs/) that allows you to resize a partition without
erasing it. It isin't lvm and im kinda wondering what the risk is in unmounting a device (with data on it), deleting the partition table and creating a new partition table (resize).
Besides setting the start sector at the wrong place.

Thanks on advance!
Kind regards.

---

