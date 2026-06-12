---
title: "mdadm raid 5 failed, 2 disks missing, one of them has pending sectors"
date: 2013-03-30
forum: General Help
---

### Post by soomon on 2013-03-30
hello ubuntu forums, 
i hope you can help me...

i have an mdadm raid 5 which consists of 4 disks.
after a reboot of the machine 2 disks failed.
so i have UU__ (active, active, spare, missing). the spare disk is the one with bad sectors.
i tried re-assembling the array with --force and mdadm decided to mark 1 disk as good and started rebuilding the other one.
sadly, the disk which was marked as good and thus used for rebuild has pending sectors and the rebuild failes at 45% as it seems to reach a sector that is bad and couldnt be recoverd.
so the rebuild fails.

is there any way to force the rebuild and make it skip bad sectors? i know that causes data loss and i dont know what will happen to the LUKS encrypted data (the whole MD raid is encrypted with luks)

do i have any chance to get my data back?

btw i dont know why the 2 disks failed as smart status is ok for 3 of them and only one has pending sectors...

thanks, soomon

---

### Post by soomon on 2013-03-31
ok, the raid is up again.
one disk had bad blocks, i used ddrescue to copy as much data as possible to disk 3 and assembled the array with --force so i now got a degraded arrayx, but its running.
ddrescue said:
errsize:   1986 kB,  errors:     640

so now the question is: should i run fscheck on the ext4 system? i have no idea where the 2kb are that it couldnt repair.
or will the fscheck eventually destroy even more data?

---

