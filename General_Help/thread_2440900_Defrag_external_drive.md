---
title: "Defrag external drive?"
date: 2020-04-16
forum: General Help
---

### Post by RegUB on 2020-04-16
I have a USB disk drive which I use for backups. I simply copy my home directory to it. The disk is quite full, so I usually delete the oldest backup to make space for each new one. Recently it has started to take a long time to copy all the files, so I was wondering if defragging it would speed things up? If so what is the best tool to use?

---

### Post by CelticWarrior on 2020-04-16
> **RegUB said:**
> Recently it has started to take a long time to copy all the files, so I was wondering if defragging it would speed things up? If so what is the best tool to use?

No, it won't if not an HDD. Flash memory doesn't require it.

---

### Post by RegUB on 2020-04-16
> **CelticWarrior said:**
> No, it won't if not an HDD. Flash memory doesn't require it.
It is an actual disk, not flash memory.

---

### Post by sudodus on 2020-04-16
If you have a Microsoft file system you may need defragmentation (FAT32, exFAT, NTFS). Linux file systems need no defragging. If a Microsoft file system I recommend that you use Windows to defrag the file system or simply delete the files and start storing files from the beginning, which will cause less wear compared to defragging.

But there is another issue with USB drives, particularly USB pendrives and memory cards. They tend to get slow after some time and this is independent of the file system, depends more of the mapping between memory cells and logical memory locations. When the speed get below half of the original speed, you can wipe the whole USB drive (overwrite it with zeros). It will restore the write speed to almost the original speed. See [this link](https://ubuntuforums.org/showthread.php?t=2196858&p=13199297#post13199297).

---

### Post by HermanAB on 2020-04-17
If you need the disk to be Windows compatible, use NTFS, then you don't need defragging either.

---

