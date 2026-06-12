---
title: "FAT Table Issues"
date: 2015-07-24
forum: General Help
---

### Post by pthfdr on 2015-07-24
I formatted my storage card(FAT32) on a Windows Mobile 6.1 phone and copied some files from Ubuntu 12.04 LTS.
However,when I insert the card back,a "FAT Tables do not match" error occured,and it asked me which FAT to use (main FAT or backup FAT).
Since the card is empty before copying,I assume Ubuntu system caused the problem.
Please fix it.

---

### Post by Vladlenin5000 on 2015-07-24
How large is that card? 64GB and up, in Windows, are all formatted in exFAT.

---

### Post by HermanAB on 2015-07-24
Howdy,

It sounds like you yanked the device out before copying was finished.   A FAT device has two partition tables, the primary and a backup. They should normally be the same, but there is no way to know which one will work best when they are different.  The solution is simple - don't be so hasty and run 'sync' before you unmount.

---

