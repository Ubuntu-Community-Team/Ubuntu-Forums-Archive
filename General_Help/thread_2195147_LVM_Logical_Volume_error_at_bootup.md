---
title: "LVM Logical Volume error at bootup"
date: 2013-12-22
forum: General Help
---

### Post by karnalta on 2013-12-22
Hi all,

After a power failure when I try to startup my ubuntusystem, I always got a error on one of my lvm logical volume..

I have a 5 HDD mdadm raid and over it I have one LVM volume group and 3 logical volume.

/dev/mapper/LR5-T***** -> Mount correctly
/dev/mapper/LR5-D***** -> Mount correctly
/dev/mapper/LR5-Stockage -> Cause error "UNEXPECTED INCONSISTENCY; RUN fsck MANUALLY ...."

When I try to run fsck, it tell me an error that the filesystem size is bigger than the physical size. It say that either superblock or partition table is likely to be corrupt...

And if I try to run resize2fs to fix that (I think), it tell me that I first need to run e2fsck which lead to the same error that fsck oO

Last time I got that kind of error, running every commands I could found on various forum just leaded me to lost all my data, so this time I'd like to have more specific help about my problem :s

Thank you if someone can help me.

---

### Post by karnalta on 2013-12-23
No body can help me ?

I have tried to do a resize2fs -f to set the system file size to the same size as the underlying volume but I got a error saying it can't read a bitmap block ..

I am really stuck, most of the post I found on that kind of problem are test machine where people just delete all and recreate... I am in a real environment I can't do that :s

---

