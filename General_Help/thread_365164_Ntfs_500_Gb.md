---
title: "Ntfs 500 Gb"
date: 2007-02-19
forum: General Help
---

### Post by erugalatha on 2007-02-19
Hello,

I have a 500 GB disk but coming from a Windows system to Linux it's already formatted with the NTFS file system - so I can't write to the disk in ubuntu.

I want to reformat the disk but not sure which file system I should format it with as I want to use the disk with both my ubuntu laptop and work laptop (which has XP on it).

First problem is finding somewhere with enough space available to back up my data but after that should I format it with FAT32 or ext3 or is there a way in ubuntu that might allow me to write to the drive?

Thanks for any help.

---

### Post by nikhilk on 2007-02-19
The most straight forward and hassle free way would be to format the shared drive as FAT32. You can also format it as ext3 and still use it with Windows (using [ext2fs]("http://e2fsprogs.sourceforge.net/ext2.html"))  or keep it as NTFS and write to it from Ubuntu (using [ntfs3g]("http://swik.net/ntfs3g")). But both of these alternatives require installation of extra software.

---

