---
title: "Filesystem choices"
date: 2007-12-24
forum: General Help
---

### Post by eapache on 2007-12-24
I'm thinking of getting a mac and setting up a triple-boot, but I'm wondering what filesystem to use for data.

Mac can't write to NTFS
Windows can't write to HFS+
Fat32 has a 32GB limit

Is there any filesystem that is universally used and supports >32GB partitions?

---

### Post by tomcheng76 on 2007-12-24
It denpends on which OS you mainly use
window, use ntfs,  you can use ntfs-3g to access ntfs in linux/mac
linux,use ext2, there is 3rd party software for ext2 filesystem, designed for windows

or i think NAS may be a good choice to share files via networks

---

### Post by eapache on 2007-12-24
Is there ntfs-3g for mac?

---

### Post by tomcheng76 on 2007-12-24
According to the official website
Yes, it supports Mac OS X

---

### Post by tomcheng76 on 2007-12-25
you just need to do a google search on "macfuse ntfs-3g"
there are plenty of howtos.

---

### Post by LaRoza on 2007-12-25
> **eapache said:**
> I'm thinking of getting a mac and setting up a triple-boot, but I'm wondering what filesystem to use for data.

Mac can't write to NTFS
Windows can't write to HFS+
Fat32 has a 32GB limit

Is there any filesystem that is universally used and supports >32GB partitions?

FAT32 doesn't have a 32 GB limit. It can't have a file over 4 GB - 1 byte, but the partition can be 8 TiB, although I doubt you'll actually have a partition that large. Windows limits the size it will format so you are forced to use NTFS. Using GParted or some other tool allows large partitions.

---

### Post by eapache on 2007-12-25
> FAT32 doesn't have a 32 GB limit. It can't have a file over 4 GB - 1 byte, but the partition can be 8 TiB, although I doubt you'll actually have a partition that large. Windows limits the size it will format so you are forced to use NTFS. Using GParted or some other tool allows large partitions.I didn't know that, thanks. I have a virtual machine disk that runs over 4GB, but I don't really need to share that. I'll also take a look at ntfs-3g for mac.

Thank you everybody, and Merry Christmas.

---

