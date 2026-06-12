---
title: "I mounted Linux on the wrong partition!"
date: 2018-03-19
forum: General Help
---

### Post by jacksonaiken32 on 2018-03-19
So i installed ubuntu to my windows partition. When i try and create a windows bootable and launch it, the screen flashes blue and wont work. There is a picture of my partitions, sorry if its hard to read. I want to just reinstall windows on the correct partitions then install ubuntu on the correct one. The 6.8g partition was meant for linux and the 86 was meant for windows.[ATTACH=CONFIG]278997[/ATTACH]

---

### Post by HermanAB on 2018-03-20
Well, if the data on the disk is not important, wipe the partition table and start over.

---

### Post by Impavidus on 2018-03-20
Just wipe the disk and start over.

6.8 GB is a bit too small for Ubuntu. You may be able to squeeze it in, but I recommend at least 20 GB if you actually want to use it.

---

### Post by yancek on 2018-03-20
I think you need to start over.  Your GParted output does show 4 windows (ntfs) partitions but the only one which might have enough space for a minimal windows install is sda4 and that is only 20GB. If you've installed Ubuntu on the 86GB drive, it has overwritten data there during the install and format. If you have data that you want to save, try to do that first and reinstall both systems.

> When i try and create a windows bootable and launch it, the screen flashes blue and wont work

What does that mean?  Are you trying to create a bootable DVD/flash drive from a windows iso?
I don't think you will be able to install Ubuntu on a 6.8GB partition.  That information is provided during the install, it will tell you what the minimum size for the partition needs to be.

You need to install both systems UEFI as your system has an EFI partition.  Not sure what if anything you could do to recover your windows.  YOu might try the microsoft support site or a windows forum about the blue screen.

THe link below is the official documentation on dual booting windows/Ubuntu UEFI.

ttps://help.ubuntu.com/community/UEFI

---

