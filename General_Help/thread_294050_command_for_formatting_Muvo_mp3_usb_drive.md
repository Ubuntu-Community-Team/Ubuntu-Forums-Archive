---
title: "command for formatting Muvo mp3 usb drive?"
date: 2006-11-06
forum: General Help
---

### Post by grahams on 2006-11-06
I tried to format a Muvo mp3 drive using mkfs -t vfat /dev/sdc1
It formatted ok and I could mount it, however when I turned the device on as a mp3 player it errored with "file system error". I repeated with mkfs -t vfat -F16 /dev/sdc1, mkfs -t msdos /dev/sdc1 and even mkfs -t vfat -F32 /dev/sdc1, all fail to be recognised by the player. 

I plugged it into my girlfriends XP system and FAT formatted the Muvo and it works fine. An fdisk /dev/sdc show it's a FAT16 partition. I'm confused and curious as to what I missed.

---

### Post by grahams on 2006-12-21
I realized my error. 

1st step create a FAT16 partition with fdisk and then mkfs -t vfat /dev/sdb1. 
I was missing the 1st step and making a file system directly on /dev/sdb

---

