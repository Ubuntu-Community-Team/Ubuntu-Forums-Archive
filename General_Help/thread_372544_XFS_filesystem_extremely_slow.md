---
title: "XFS filesystem extremely slow"
date: 2007-02-28
forum: General Help
---

### Post by L0rd_D4rk on 2007-02-28
Hi all,

I have had this problem for a long time, but now I have to copy some large ISO files (>4Gb) and I have to solve it.

When I try to copy a 4Gb file under normal conditions It takes about 4 hours, but I have verified that if I am under single user mode it finish in about 3:30 minutes without any problems. I don't know what causes this problem, but it is specific from XFS because my ReiserFS, NTFS and FAT32 works well under any condition.

I have an Asus A8N-SLI motherboard with a SATA Seagate 300Gb hard drive and I use ubuntu 6.10 with 2.6.17-10-386 kernel.

**Edit:** Some more information; it also takes a long time when a copy or delete a (not so) large number of files even they are very small. When I copy a file Gnome System Monitor Shows me a 100% use cpu and the entire system slows down, the programs take a lot to launch, etc... but with the command top I see all ok 

Thanks

---

### Post by exisn on 2007-03-07
Try looking into mounting the partition with nobarrier. It should come with an extra risc in case of power failure, but it significantly speed up my transfers.

---

