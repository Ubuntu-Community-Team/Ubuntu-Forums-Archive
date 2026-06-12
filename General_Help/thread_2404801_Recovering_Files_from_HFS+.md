---
title: "Recovering Files from HFS+"
date: 2018-10-28
forum: General Help
---

### Post by apocalypsemystic on 2018-10-28
I have a 4TB hard drive formatted with HFS+. It is full of photographs  and lightroom catalogues. It had two partitions: the EFI partition in  front, which I assume contained the superblock, and the HFS+ partition.  Because I misunderstood how HFS+ works, I moved the entire ~4TB HFS+  partition left to the front of the drive, and overwrote the EFI  partition, which I thought was useless, and which seemed to be causing  problems getting the drive recognized on some devices. Now, of course, I  cannot mount because there is no superblock, which I assume was  contained on the EFI. Before I do anything else, I wanted to see if  anyone could help me understand what I had done, and what my options are  for recovering the data and file structure. Does it make sense to try to move everything back to the right and try to recover the original EFI partition, or should I just try to scan the whole disk for whatever photos I can find?

Thanks

---

### Post by yancek on 2018-10-28
THe EFI partition contains the boot files for a system using the UEFI (Unified Extensible Firmware Interface) rather than the older Legacy/MBR method.  The link below gives some information on it.

[https://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/](https://www.howtogeek.com/56958/htg-explains-how-uefi-will-replace-the-bios/)

You need to install specific software to access any Apple formatted (hfs) drive, see the link below.  This software is rarely installed on any Linux default installation. 

 [https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os](https://askubuntu.com/questions/332315/how-to-read-and-write-hfs-journaled-external-hdd-in-ubuntu-without-access-to-os)

---

### Post by apocalypsemystic on 2018-10-28
Hi, thanks for the response.

I think I'm saved. I had thought EFI was unrelated to the HFS+ partition, and was unnecessary for external hard drives, so I overwrote it, but when that overwrite caused a mounting error, I mistakenly assumed that I had misunderstood EFI and that it was, in fact, necessary. I do have hfsprogs installed, and I had been able to mount the drive before, but thanks to your link, I ran fsck.hfsprogs -f /dev/sdb2 and it just patched it up and I can mount again. All the files seem fine. Evidently the issue was just that there was a minor hitch when gparted moved the partition, but fsck fixed it. Many thanks.

---

