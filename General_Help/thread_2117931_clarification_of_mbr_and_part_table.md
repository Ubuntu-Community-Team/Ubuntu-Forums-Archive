---
title: "clarification of mbr and part table"
date: 2013-02-19
forum: General Help
---

### Post by OlorinIWas on 2013-02-19
I'm questioning the possibility that I've deleted my partition table using:
    
dd if=/dev/zero of=/dev/sda1 bs=446 count=1

...trying to remove a grub that may or may not have been there. This is an advanced format disk, but I was under the impression that the partition table followed bs 446 (I did this on 3 drives with no problem on the others)

Neither windows or linux recognizes the drive as formatted. Any clarification would be helpful...I can't loose the data, but I hope there is a more simple solution that I am unaware of. I'm assuming window's restore does nothing for mbr.  Thanks

---

### Post by OlorinIWas on 2013-02-19
As it just occured to me, This drive has only one partition, and was formatted by windows...

EDIT: I have boot access to widows7 and linux distros

---

### Post by rnerwein on 2013-02-20
> **OlorinIWas said:**
> I'm questioning the possibility that I've deleted my partition table using:
    
dd if=/dev/zero of=/dev/sda1 bs=446 count=1

...trying to remove a grub that may or may not have been there. This is an advanced format disk, but I was under the impression that the partition table followed bs 446 (I did this on 3 drives with no problem on the others)

Neither windows or linux recognizes the drive as formatted. Any clarification would be helpful...I can't loose the data, but I hope there is a more simple solution that I am unaware of. I'm assuming window's restore does nothing for mbr.  Thanks
hi
as i know is the MBR [COLOR=Red]not[/COLOR] on /dev/sda1 it is [COLOR=SeaGreen]on[/COLOR] /dev/sda - and that isn't the same disk-address.
ciao

---

### Post by Laobi on 2013-02-20
The MBR should be on /dev/sda, so you didn't overwrite the MBR, but you probably did overwrite the first 446 bytes of the /dev/sda1 partition, so it has lost the information about the internal stuff of the partition. Depending on what type the partition was (FAT, NTFS...), this information can be reconstructed from backups that are stored within the partition itself. You should be able to do it with TestDisk.

If the partition is not too big and you have enough space, it would be safer to make an image of the pratition with dd command and then work on that image with TestDisk to see if everything goes OK.


**EDIT: I just saw you've said it is an advanced format disk. I'm not sure if TestDisk can work with this...**

---

### Post by OlorinIWas on 2013-02-20
> **Laobi said:**
> The MBR should be on /dev/sda, so you didn't overwrite the MBR, but you probably did overwrite the first 446 bytes of the /dev/sda1 partition, so it has lost the information about the internal stuff of the partition. Depending on what type the partition was (FAT, NTFS...), this information can be reconstructed from backups that are stored within the partition itself. You should be able to do it with TestDisk.

If the partition is not too big and you have enough space, it would be safer to make an image of the pratition with dd command and then work on that image with TestDisk to see if everything goes OK.


**EDIT: I just saw you've said it is an advanced format disk. I'm not sure if TestDisk can work with this...**

Ok that makes sense. Am I to assume that manual retrieval is my only real option then? testdisk seems like a bad idea 2 me...the format is ntfs at 2 TB...
Anyone know if data retrieval is likely possible at this pt?

---

### Post by OlorinIWas on 2013-02-20
> **OlorinIWas said:**
> Ok that makes sense. Am I to assume that manual retrieval is my only real option then? testdisk seems like a bad idea 2 me...the format is ntfs at 2 TB...
Anyone know if data retrieval is likely possible at this pt?

well after messing with testdisk all night...I got around to trying the boot recovery...which worked, and I have all my data available..

so I'm not sure exactly what I did...what I deleted, but the advanced testdisk functions (the scan was way off) were very helpful on this advanced format disk

---

