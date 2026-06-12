---
title: "ext3 FS UTF8 Support for Swedish Characters"
date: 2006-11-28
forum: General Help
---

### Post by ba5e on 2006-11-28
Hi,

I have NTFS, ReiserFS file systems on my system which display Swedish characters (ÅÖÄ) correctly, however I am moving my NTFS partition to ext3 as I am having serious problems with NTFS-3g and have added the following in my fstab:

/dev/hde7	/media/Data1     ext3    defaults	0       1

The problem is that the Swedish characters show up as ? in diamond shaped characters....weird! I am running the following locale:

en_US.UTF-8

---

### Post by ba5e on 2006-11-30
bump

---

### Post by PriceChild on 2006-11-30
Have you made a new filesystem and copied the files onto it... or are you just changing your fstab entry and assuming the filesystem'll change?

---

### Post by ba5e on 2006-12-01
> **PriceChild said:**
> Have you made a new filesystem and copied the files onto it... or are you just changing your fstab entry and assuming the filesystem'll change?

okay:

1)100gb NTFS, 100gb EXT3
2) copy NTFS drive to EXT3 (in windows with the ext3 driver)
3)removed NTFS Partition.
4)mounted EXT3 drive with the issue described above.

is there some special option I need in fstab for ext3?

---

