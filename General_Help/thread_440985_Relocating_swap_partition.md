---
title: "Relocating swap partition"
date: 2007-05-12
forum: General Help
---

### Post by akudewan on 2007-05-12
Hi,

I'm planning on merging my two partitions. This, however, will relocate my swap partition. I will need to edit /etc/fstab to accommodate these changes, right?

But in the fstab file, I see this:
```

# /dev/hdc3 -- converted during upgrade to edgy
UUID=738c3dcb-0f49-452d-944f-eb39f87f367d none swap sw 0 0

```

This was apparently done when I upgraded to edgy, what do the strange hex numbers mean ?

---

### Post by heimo on 2007-05-12
It's another way of referring to partitions. You can check it with tune2fs like this:
```
tune2fs -l /dev/hda1 | grep UUID
```
where hda1 is the partition and output gives you the corresponding UUID

---

### Post by akudewan on 2007-05-12
It seems to work only with ext2/3 partitions. Any way of finding the UUID of fat32 & swap partitions? If I just edit the fstab file with the usual /dev/* notation, will it work?

Another question: When I upgraded to Feisty, all my hda* partitions became sda* partitions, and even my DVD drive became /dev/scd0. Why did this happen?

Thanks.

---

### Post by heimo on 2007-05-12
> **akudewan said:**
> It seems to work only with ext2/3 partitions. Any way of finding the UUID of fat32 & swap partitions? If I just edit the fstab file with the usual /dev/* notation, will it work?
Yes.

> **akudewan said:**
> 
Another question: When I upgraded to Feisty, all my hda* partitions became sda* partitions, and even my DVD drive became /dev/scd0. Why did this happen?
Changes in kernel. I don't know details.

---

### Post by akudewan on 2007-05-12
Ok, thanks for the info. :)

---

### Post by Pat123 on 2007-06-25
I know this is an old thread..but just in case someone ends up here when searching something similar,i have a better solution:

To find UUID corresponding to your partition(s),just type "blkid" in terminal (without quotes)

---

