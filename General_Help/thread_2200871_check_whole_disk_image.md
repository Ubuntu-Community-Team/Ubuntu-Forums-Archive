---
title: "check whole disk image"
date: 2014-01-21
forum: General Help
---

### Post by leodp on 2014-01-21
Hi,

I could not find a clear answer even if it should be a typical situation.

I have a corrupted HDD, NTFS filesystem.
I created an image of the whole disk with ddrescue.
No errors on the HW side.
The original HDD has this partition table:

fdisk -l ddrescue.ntfs
...
  Dispositivo Boot      Start         End      Blocks   Id  System
ddrescue.ntfs1   *          63  1465144064   732572001    7  HPFS/NTFS/exFAT
...
where ddrescue.ntfs is the image dumped by ddrescue

I can mount the image with:
mount -o ro,loop,offset=32256 -t ntfs ddrescue.ntfs mountDir
where offset is 63*512

Question: how can I fix the filesystem, which is corrupted?
I cannot run ntfsfix because the image is of the whole hdd (/dev/sdb) and not only of hte ntfs partition (/dev/sdb1)
I would like to avoid copying again hundreds of GB by extracting dirctly /dev/sdb1.


Thanks,
leodp

---

### Post by sudodus on 2014-01-21
- Do you want to repair the original system or the image or both?

- It is usually better to use Windows tools to repair a Windows file system. So if you have Windows installed somewhere, I suggest that you connect the drive with the original file system to that computer and repair it, or use a Windows preinstall environment, for example BartPE or Win7PE. Or maybe you can borrow a computer with Windows and repair your file system there.

---

### Post by leodp on 2014-01-21
I have solved it with:

losetup -o 32256 /dev/loop0 ddrescue.ntfs
where ddrescue.ntfs is the HDD image file, 32256 is the offset at which the first partition is starting 

and then:
ntfsfix  /dev/loop0 2>&1 |tee --append fsck1.log
ntfsfix  -b   /dev/loop0 2>&1 |tee --append fsck2.log

---

### Post by sudodus on 2014-01-21
Congratulations and thank you for sharing :KS

---

