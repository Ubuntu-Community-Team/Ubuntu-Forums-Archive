---
title: "Defragging FROM Linux?"
date: 2007-09-21
forum: General Help
---

### Post by NeutrinoX on 2007-09-21
Alright guys. Yep, I checked the prior threads about this and similar topics, and seem like they haven't got too much useful information. This is what I want to do: It turns out that I have my PC currently as a dual boot with Kubuntu and XP. Now, I've got a FAT32 and a NTFS partition for XP. Sometimes, I'd like to do system maintenance from GNU/Linux, and more specifically, defragmenting my FAT32/NTFS partitions from it. My main question is: Is it there a program or script that I can use to defragment FAT/FAT32/NTFS partitions from Kubuntu? If there isn't, if I use any of the many freeware defragging programs with WINE over those partitions, will it work?

[Here]("http://ubuntuforums.org/showthread.php?t=169551") I found something that could suit my needs. But seems like it won't work with NTFS partitions. Does that limitation still apply?

Thanks in advance for your help! :D

---

### Post by kidders on 2007-09-22
Hi there,

Defragmenting hard disks isn't something that gets done much outside of the Microsoft world. Non-Windows defragmenters for certain filesystems do exist, but personally, I would be slow enough to use one written for an open source filesystem ... let alone one for a proprietary filesystem like NTFS.

I may well be wrong, but I very much doubt an NTFS filesystem defragmenter exists for *any* non-MS operating system. Even if one did exist, I would certainly never use it. Similarly, I wouldn't recommend even attempting to run one made for Windows in Wine.

I know this probably couldn't be further from what you want to hear (sorry for that), but I couldn't possibly bring myself to recommend using anything other than Windows to defragment MS filesystems.

---

### Post by fenario on 2007-09-22
I second Kidders. Be extremely careful with defragmenting or partitioning, unless you are prepared to do a total Sprinclean.

---

### Post by NeutrinoX on 2007-09-23
Hehe, well, thanks for the advice... 8-[ Right now, I just tried to use pyfragtools over a couple of exceptionally fragmented folders inside my NTFS drive (After doing a nice backup, of course), and did a so-so work. They did turned out less fragmented than before, but the job wasn't nearly as good as with Windows' built-in defragmenter. Didn't reported any checksum errors either, so the data is OK. The thing is, if anybody is reading this, pyfragtools now **works** using the latest version of the NTFS driver, but I'd rather not use it for defragmenting a NTFS drive. In my case it was kinda an emergency thing as I wanted to defragment quickly that partition, I was doing a backup snapshot of it with ntfsclone before resizing.

---

