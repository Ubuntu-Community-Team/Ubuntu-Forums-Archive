---
title: "FAT32 as data filesystem"
date: 2007-09-05
forum: General Help
---

### Post by DiGiTY on 2007-09-05
I'm adding a 1 TB FAT32 drive (2 500 GB drives at RAID 0) to my Ubuntu 7.04 server and having this store my whole media library (movies, music, pictures, etc.) for streaming/sharing. Is there anything I should be aware of when having FAT32 drive as my main storage drive in Linux/Ubuntu? Will this perform just as well as a EXT2/3 storage drive in Linux/Ubuntu?

TIA

P.S. - This drive will only store media files, no Linux system, application, swap, etc. files.

P.P.S. - I'm going with FAT32 because I'll eventually move this RAID to a Windows machine down the road and would like everything in tact

---

### Post by Sef on 2007-09-05
> Is there anything I should be aware of when having FAT32 drive as my main storage drive in Linux/Ubuntu? Will this perform just as well as a EXT2/3 storage drive in Linux/Ubuntu?

You will need to defrag the FAT32 partition.  If I remember correctly, Windows can read ext2 and ext3.  Will check if that is true.

update:  Yes, with "[Ext2 Installable File System for Windows]("http://www.fs-driver.org/")."

---

### Post by rsambuca on 2007-09-05
I believe there is a 4GB minus 1 byte size limit of FAT32 files, which may or may not affect you depending on the size and format of your movie files.  Also, FAT32 doesn't allow you to keep permissions.

---

### Post by softtower on 2007-09-05
I would not use FAT32 for several reasons:
  - Inefficient. Small files will waste a lot of space.
  - Needs regular defragmentation
  - Unreliable: frequent "lost file links" 
  
Use NTFS on that drive and mount it with ntfs-3g.

---

