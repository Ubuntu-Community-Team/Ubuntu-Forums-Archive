---
title: "Missing operating system error on bootable usb."
date: 2016-01-07
forum: General Help
---

### Post by steaksoldier on 2016-01-07
So i'm trying to install xubuntu and I'm running in to issues when I do. Whenever I would boot from the usb I get a "missing operating system" message that flashes across the screen really quickly and then it boots what I already have installed (kubuntu if it matters). I've used the DD command instead and it does the same thing. Even messed around with different filesystems like fat32 and ntfs and it stays the same. 


Intel i5 quad core 2.4 ghz
4 gigs ram
1 terabyte ssd/hdd hybrid.
gateway nv26u

---

### Post by ian-weisser on 2016-01-07
Have you checked the MD5 sums un your downloaded .iso to ensure it's good?
Howto: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
What to compare to: [https://help.ubuntu.com/community/UbuntuHashes](https://help.ubuntu.com/community/UbuntuHashes)

---

### Post by yancek on 2016-01-07
If you get a missing operating system message then the most likely scenarios are a bad download (do an md5 Checksum?) or it wasn't properly written to the flash drive.  What software did you use to put it on the flash drive?  Some software requires or recommends you use FAT32.  What was the exact command you used with dd?  Can you try the flash drive on another computer to eliminate that as a problem?

---

