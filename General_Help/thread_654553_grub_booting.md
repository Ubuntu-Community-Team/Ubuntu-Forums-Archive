---
title: "grub booting"
date: 2007-12-31
forum: General Help
---

### Post by shadows123 on 2007-12-31
It's special case here lol..
i had windows vista..
Then i bought a webcam.. apparently only works for xp and older, ( not vista ) so i installed xp pro gold again..

==> at this time there was no dualboot to boot into vista, it went straight to xp always
Then i was interested in ubuntu again lol :P
and i installed it..
==> boot menu :
-ubuntu
-ubuntu safe
-other non-upgraded one
- above safe
-other:
-vista

When i click vista..
I get a black screen with a dissapearing _ ..
i want to be able to go to xp & vista again lol...
I should edit the boot entries in a way or another.. idk how lol..

some more partitioning info:
root@Kevin-PC:/home/kevin# sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       23925   192169530    f  W95 Ext'd (LBA)
/dev/sda2   *       27258       38914    93625344    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           23926       27257    26764290   83  Linux
/dev/sda5               2       20643   165799452+   7  HPFS/NTFS
/dev/sda6           20643       23682    24414062+   7  HPFS/NTFS
/dev/sda7           23683       23925     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order


Thanks for your help :)

---

### Post by dcstar on 2007-12-31
> **shadows123 said:**
> It's special case here lol..
i had windows vista..
Then i bought a webcam.. apparently only works for xp and older, ( not vista ) so i installed xp pro gold again..

==> at this time there was no dualboot to boot into vista, it went straight to xp always
Then i was interested in ubuntu again lol :P
and i installed it..
==> boot menu :
-ubuntu
-ubuntu safe
-other non-upgraded one
- above safe
-other:
-vista

When i click vista..
I get a black screen with a dissapearing _ ..
i want to be able to go to xp & vista again lol...
I should edit the boot entries in a way or another.. idk how lol..

some more partitioning info:
root@Kevin-PC:/home/kevin# sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               2       23925   192169530    f  W95 Ext'd (LBA)
/dev/sda2   *       27258       38914    93625344    7  HPFS/NTFS
Partition 2 does not end on cylinder boundary.
/dev/sda3           23926       27257    26764290   83  Linux
/dev/sda5               2       20643   165799452+   7  HPFS/NTFS
/dev/sda6           20643       23682    24414062+   7  HPFS/NTFS
/dev/sda7           23683       23925     1951866   82  Linux swap / Solaris

Partition table entries are not in disk order


Thanks for your help :)

Post the contents of your /boot/grub/menu.lst file.

---

### Post by shadows123 on 2008-01-02
It says on /dev/sda2/ when it's 5.. i'm going to try what someone else told me (hd0,4)
Thanks!
```
# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda2
title		Windows Vista/Longhorn (loader)
root		(hd0,1)
savedefault
makeactive
chainloader	+1
```

-didn't work...

---

