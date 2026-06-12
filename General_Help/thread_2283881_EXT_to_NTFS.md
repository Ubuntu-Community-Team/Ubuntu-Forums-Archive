---
title: "EXT to NTFS"
date: 2015-06-25
forum: General Help
---

### Post by Slammmed on 2015-06-25
I lost power in the middle of the partition manager and upon reboot my Windows 8 partition is now recognized as extension with LVM

Since I'm sure it didn't actually make any changes to my data, is there any way I can convert the partition back to NTFS and fix the mbr?

---

### Post by steveo314 on 2015-06-26
Its saying extension with LVM in Ubuntu? 

If you weren't modifying your NTFS partition before the power loss then that partition was untouched.

---

### Post by oldfred on 2015-06-26
Windows 8 default installs by vendor use UEFI with gpt partitioning.
And LVM installs from Linux normally use entire hard drive.

Post this from Ubuntu live installer's terminal:
sudo parted -l

---

