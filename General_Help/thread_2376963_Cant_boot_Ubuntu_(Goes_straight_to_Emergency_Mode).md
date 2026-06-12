---
title: "Cant boot Ubuntu (Goes straight to Emergency Mode)"
date: 2017-11-07
forum: General Help
---

### Post by david1410 on 2017-11-07
Hello. I recently booted Ubuntu alongside Windows 10 on my laptop and have mostly been using Ubuntu ever since. I switched to Windows earlier and restarted, was met with GRUB screen and picked Ubuntu. It went to Emergency Mode

I read somewhere it may have been due to Windows fast boot and it wasn't, I don't think. My linux file system is on /dev/sda7 and linux swap is on /dev/sda8. I tried fsck on sda7 and there were block and inode count errors but now it seems to be "clean".

I went to recovery mode on the GRUB menu and did fsck again. here is some of the output:

fsck from util-linux 2.27.1
/dev/sda7: clean, 580616/20938752 files, 21821442/83749120 blocks
fsck.fat 3.0.28 (2015-05-16)
0x41: Dirty bit is set. Fs was not properly unmounted and some data may be corrupted.
   Automatically removing dirty bit.
There are differences between boot sector and its backup.
This is mostly harmless. Differences: (original/backup)
   65:00/01
   Not automatically fixing this
Performing changes.
/dev/sda2: 376 files, 53489/98304 clusters


I have tried booting from USB which failed and am considering running Ubuntu as a VM on Windows to troubleshoot. I haven't a clue though. Would really appreciate help. 

Thanks.

---

