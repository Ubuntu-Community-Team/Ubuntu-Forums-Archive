---
title: "Botched Dual Boot Install - Grub error 22"
date: 2008-01-07
forum: General Help
---

### Post by sirana on 2008-01-07
I had a dual boot of Windows XP and Ubuntu and wanted to change to an dual boot of Vista and Ubuntu. I deleted all the partitions of the one hard drive (which turned out to be a really bad idea) and format them with ntfs. Now when I try to install Vista I get a Blue Screen of Death (Stop error: last line is fastfat.sys and some hex-adresses)
When I try to boot "normally" I get a GRUB error 22. 
My interpretation is that my MBR still has Grub in it and since it points to nothing I get this error. I tried to get it out of the MBR via the Windows Recovery Console (fixmbr) but that hasn't changed anything.
My current state is this:

HardDisk 1 (this was the original disk, where both Windows XP and Ubuntu were installed): 
1. Partition: NTFS 130GB (Windows sees this as D:\)
2. Partition: NTFS 100 GB(Windows sees this as E:\)

HardDisk 2(Data):
1. Parition: FAT32 500 GB (Windows sees this as C:\)

I am quite at a loss what to do, I already tried installing XP, but that runs against the same GRUB error 22. 

If my clueless actions didn't give it away, I'm pretty much a linux newbie. Help is much appreciated.

---

### Post by stump138 on 2008-01-07
edited, apologies and ignore

---

