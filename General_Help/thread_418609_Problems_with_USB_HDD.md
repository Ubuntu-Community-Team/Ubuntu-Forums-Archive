---
title: "Problems with USB HDD"
date: 2007-04-22
forum: General Help
---

### Post by Amilius on 2007-04-22
hey there,

having problems with my external HDD, first of all, I have to manually mount it every time I plug it in, which is kind of annoying, since in my last install of kubuntu it didn't happen that way, and secondly, I can only take files out, but I can't copy or moves files into the HDD, what's up with that?

---

### Post by Amilius on 2007-04-22
I googled my problem, and I believe that the problem is because the HDD is NTFS formated (sadly), but that I can emulate it using ntfs-3g. But, by doing so, will it not compromise my files? it's weird, but as I said, on my previous kubuntu installation I didn't have problems with my HDD, and it was NTFS format back then also.

---

### Post by StoneDragon on 2007-04-23
confirmed. Problem with ntfs-partitions that do not automount, when the usb-device connects..

---

### Post by strabes on 2007-04-23
format it as ext3 (or fat32?) and then use the driver from [www.fs-driver.org](www.fs-driver.org) to read & write to it in windows.

---

### Post by rich.bradshaw on 2007-04-23
Just

sudo apt-get install ntfs-3g ntfs-config

then you can tell it to allow read write on all drives.

---

### Post by mbourd25 on 2007-04-23
Will there be a fix for this bug which it can operate the same way it did in Ubuntu 6.10?

Thanks.

---

### Post by StoneDragon on 2007-04-23
Yeah, since I run into this ntfs-mount-problem all 3-6 months with several distribution, this seems to be the best solution to flush away ntfs from my usb-hd finally.

---

