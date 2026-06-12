---
title: "[SOLVED] Seeking for external HD id"
date: 2008-03-19
forum: General Help
---

### Post by geo909 on 2008-03-19
Hello everybody.

 I have an external USB hard drive. Is there a way (maybe with fdisk or something)
to find out its id? I want to treat it in a specific way in fstab. 


 Thanks in advance!

---

### Post by insineratehymn on 2008-03-19
I don't think I understand what you mean by ID... like its grub ID? Like hd(1,1) or like where it is mounted in dev? If I'm completely off the point just slap me around a bit and I'll go drink some more coffee.

---

### Post by neerajadsul on 2008-03-19
Try

fdisk -l

---

### Post by geo909 on 2008-03-19
Hi,

no, 'fdisk -l' don't gives me any IDs.

 Every volume has an Id, that's the string you see from your bios settings when you see your connected hard disks. 
 For example my 1st disks ID is:
scsi-SATA_ST380811AS_6PS0GFKJ

Something similar should be in the bios of your PC!

Ok, I sort of answered my question, (look at the BIOS) but I would like to know if there's a handy way..

---

### Post by milton1 on 2008-03-19
blkid might do it.

---

### Post by geo909 on 2008-03-20
OK, it was simpler:

everything's on /dev/disk/by-id
When I went there it was obvious which id was for every disk

Thanks for your time, everybody

---

