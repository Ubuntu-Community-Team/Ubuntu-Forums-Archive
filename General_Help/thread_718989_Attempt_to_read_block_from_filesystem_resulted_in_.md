---
title: "Attempt to read block from filesystem resulted in short read while checking ext3 jou"
date: 2008-03-08
forum: General Help
---

### Post by jphekman on 2008-03-08
Hi all. I have a screwed-up disk (multiple power failures at bad times + broken UPS, all bad). Also backups apparently are not available (automated cronjob seems not to have run recently, I didn't notice). Much stress.

The disk has three partitions, / and /home and swap; I care about home:

```
root@ubuntu:~# fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x15091508

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        1216     9767488+  83  Linux
/dev/sda2            1217        9665    67866592+  83  Linux
/dev/sda3            9666        9729      514080   82  Linux swap / Solaris
```

I am running off of a gutsy live CD right now. When I try to mount sda2:

```
root@ubuntu:~# mount /dev/sda2 /media/sda/
mount: wrong fs type, bad option, bad superblock on /dev/sda2,
       missing codepage or helper program, or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so
```


I used TestDisk to find backup superblocks and tried to fsck with that information:

```
root@ubuntu:~# fsck -b 32768 /dev/sda2
fsck 1.40.2 (12-Jul-2007)
e2fsck 1.40.2 (12-Jul-2007)
/dev/sda2: Attempt to read block from filesystem resulted in short read while reading block 533
```

(which is essentially the same message as when I just try to fsck without specifying a block).

"badblocks" lists me a huge number of blocks, but I suspect that if there is a problem with the superblock, it would make reading the other blocks difficult, so I don't think the entire disk is necessarily gone.

All suggestions are very much appreciated!

Thanks,
Jessica

---

### Post by xdarkxanarchyx on 2008-03-13
I have a similar story. Only I'm loosing 180GB of videos. Nothing personal thankfully but still stinks. :(

---

### Post by jphekman on 2008-03-18
The end of the story is that I used ddrescue to copy the image off of the disk so that I could play with it on a drive that was working. I was unable to find a working superblock on the new image either, and had to ship the disk to a recovery place (DriveSavers appears to be the recommended option if you really want someone very good).

Hope this information helps someone.

Jessica

---

