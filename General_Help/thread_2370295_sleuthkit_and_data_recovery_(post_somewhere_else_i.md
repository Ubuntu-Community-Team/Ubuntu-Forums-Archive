---
title: "sleuthkit and data recovery (post somewhere else if needed)"
date: 2017-09-01
forum: General Help
---

### Post by bold33 on 2017-09-01
Hi,

A usb stick (8GB) was accidentally made into a live usb (xubuntu 1.3GB). Before the catastrophic event in the usb there was:

1. The ISO copy of Xubuntu 17.04 64 bits, the last addition to the usb stick
2. Portable apps with several apps (Firefox, geany, the whole and latest Libreoffice, Vlc, Unetbooting) 
3. A part of the usb was used both by xubuntu and windows OS. Here were the files that I care about, specifically a directory with several .txt files, no longer than 30KB, where several usernames and passwords were stored. The directorys' name is basic or Basic.

I am now reading about sleuthkit on [https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery) as I have never done forensics before. I am now working with an image copy of the whole usb I did with

```
sudo ddrescue /dev/sda /home/sherman/Damaged-USB/damaged-usb.img
```mmls damaged-usb.img 

Furthermore

> mmls damaged-usb.img 
returned
> 
DOS Partition Table
Offset Sector: 0
Units are in 512-byte sectors

      Slot      Start        End          Length       Description
000:  Meta      0000000000   0000000000   0000000001   Primary Table (#0)
001:  -------   0000000000   0000002047   0000002048   Unallocated
002:  000:000   0000002048   0015556607   0015554560   Win95 FAT32 (0x0b)

My question now is, in what partition should I start looking for the txt files?

---

