---
title: "removing gateway recovery partition"
date: 2007-05-29
forum: General Help
---

### Post by bdean42 on 2007-05-29
I have recently been running a bit short on space in my /home partition and I've decided that what I need to do is get rid of the gateway recovery partition on my laptop which is taking up about ... 6 gigs or so.

fdisk -l  looks like this:
```
Disk /dev/hda: 100.0 GB, 100030242816 bytes
255 heads, 63 sectors/track, 12161 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *         894        5757    39070080    7  HPFS/NTFS
/dev/hda2               1         893     7172991    b  W95 FAT32
/dev/hda3            5758       12161    51440130    5  Extended
/dev/hda5   *        5758        6730     7815591   83  Linux
/dev/hda6            7180        7301      979933+  82  Linux swap / Solaris
/dev/hda7            7302       12161    39037918+  83  Linux
/dev/hda8            6731        7179     3606561   83  Linux
```

so the /dev/hda2 partition is the one i would like to get rid of. /dev/hda8 is where my home directory lives.

the problem is, i don't want to just delete all this information. my laptop didn't come with any recovery cds so the recovery partition represents the only copy of winxp home install files that i have. it's not likely that i'd need these but i'd rather not just throw them away. 

what i would like to do is create a bootable dvd with the recovery partition information on it. the problem is... i don't know how to do this. my MBR has grub installed in it and i do chainloading for the bootloaders of winxp and the recovery partition (some win2000-ish MiniNT operating system). I tried telling K3B to do some sort of hard drive emulation for a bootable DVD but it didn't do anything, probably because the MBR is on /dev/hda not /dev/hda2 (what i want to copy).  (I think it is worth noting that while /dev/hda2 has 7172098 blocks, it only contains about 2.5gb of data, so writing to a dvd is feasible).

i'm sure dd would be useful here but i don't really know how.

also, i'll worry about how to move the free space from /dev/hda2 around after i've figured out how to do this bootable dvd thing.

Thanks! :)

---

### Post by kuja on 2007-05-29
Perhaps you could back it up with partimage then burn the backup image to a DVD?

---

