---
title: "SD Card can't be seen?"
date: 2017-01-18
forum: General Help
---

### Post by ryan++ on 2017-01-18
Hello, I recently tried uploading Raspbain to a micro SD card using the following command:
'sudo dd bs=1M if=2017-01-11-raspbian-jessie.img of=/dev/sdb1' 

There was something wrong with what I did, so I went back to format the drive and start over, though it doesn't show up in the file explorer. 
If i type 'sudo fdisk -l' it shows up as "/dev/sdb1        8192 62333951 62325760 29.7G  c W95 FAT32 (LBA)"

How do I get it to show up in the file explorer again? I'd like to reformat it to FAT32 if that info is needed.

---

