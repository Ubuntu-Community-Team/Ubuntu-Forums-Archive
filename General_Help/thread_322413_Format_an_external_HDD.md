---
title: "Format an external HDD ?"
date: 2006-12-20
forum: General Help
---

### Post by krypto_wizard on 2006-12-20
What program in Ubuntu can I use to format an external HDD. It has lot of crap and some files cannot be deleted for some reasosns. It was FAT32 drive.

I generally store photos, videos, songs in it. What is the right file system should I use. I cant use NTFS because Ubuntu doesnt write on NTFS. Please advise.

---

### Post by meng on 2006-12-20
Probably easiest to plug it in, determine the device identification (sudo fdisk -l should do the trick) then fdisk /dev/sda (or whatever the device is). You can still use fat32 as the filesystem, since that is recognized by both windows and linux.

---

### Post by krypto_wizard on 2006-12-20
Any easier way ? I used gparted but then it did not give me an option to format it ?

---

### Post by meng on 2006-12-20
What is the device ID/handle?

---

### Post by krypto_wizard on 2006-12-20
Disk /dev/sdh: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdh1               1       19457   156288321    c  W95 FAT32 (LBA)

---

### Post by meng on 2006-12-20
Try:
mkdosfs -F 32 /dev/sdh1

---

