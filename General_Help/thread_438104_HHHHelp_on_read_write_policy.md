---
title: "HHHHelp on read/ write policy"
date: 2007-05-09
forum: General Help
---

### Post by sarium on 2007-05-09
Hi,

I am not expert with linux, I have installed ubuntu on a partition of my hard disk while I have win XP on the other. 

I can see and access the XP partition from ubuntu but I only have read permission .

I tried to change the permission from the graphics interface but did not allowed me.

Is there a way to be able to write on the XP partition from ubuntu?

Thanks 

Raf

---

### Post by dfreer on 2007-05-09
the problem is that ubuntu does not ship with the ability to write to NTFS partitions, only read. You can install the NTFS3G driver in order to write to your ntfs partition, or you can create a shared FAT32 partition that both OS's can see and share data that way.


[http://lunapark6.com/?p=1710](http://lunapark6.com/?p=1710)
[http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g](http://www.howtoforge.com/ubuntu_edgy_eft_ntfs_ntfs_3g)

---

### Post by sarium on 2007-05-09
Thank you !

that was helpful !!

---

