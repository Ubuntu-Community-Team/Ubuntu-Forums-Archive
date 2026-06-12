---
title: "jpg corrupted during copying"
date: 2016-11-09
forum: General Help
---

### Post by Wim De Winter on 2016-11-09
I use Kubuntu 16.04.1 LTS, nautilus for copying, a SanDisk Extreme 64GB SDXC card to copy from and an ext4 HDD with 190GB of free space to copy to.

While copying from my camera to my laptop some jpg files get corrupted, they're partially gray on the bottom, while ok on top. Nautilus takes forever to create thumbnails and GwenView is as good as unresponsive while viewing a folder with corrupted jpg's.

My guess is it's a problem with the format of the SD card. It's in exfat format. In my previous camera I used an 8GB SDHC card, fat32 formatted, and never had any issues.

I have exfat-fuse and exfat-utils installed of course.

Can anyone help me pinpoint what's wrong? I have been googling for ages without success.

---

### Post by Wim De Winter on 2016-11-20
I've been doing some more research. Could this be a problem with the cluster size, as explained [here]("https://ubuntuforums.org/showthread.php?t=818188")? I don't quite understand it, can someone try to explain?

Thanks!

---

