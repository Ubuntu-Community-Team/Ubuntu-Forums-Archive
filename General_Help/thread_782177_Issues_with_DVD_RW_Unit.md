---
title: "Issues with DVD RW Unit"
date: 2008-05-04
forum: General Help
---

### Post by chichiri on 2008-05-04
I have ubuntu installed since 2 months and runs great.
But after updating to Hardy,i have a few issues with my DVD unit has some issues reading medias...

With data CD/DVD, appears the message

```
mount: wrong fs type, bad option, bad superblock on /dev/scd1,
      missing codepage or helper program, or other error
```

With DVD-Video, doesn't appear any message,and its seems that i never inserted a disc in the unit (BTW: I installed the packages libdvdread3 and libdvdnav4)

With Blank DVD and CD there's no problem,it's detect inmediatly and i can burn them with any tool

And,the media that i'm testing work fine in Windows.

Here's my FSTAB

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb1
UUID=54e4fbc8-d94a-4430-ad13-9562d64a100c /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda1
UUID=7E6014FE6014BEB9 /media/hda1     ntfs    defaults,umask=007,gid=46 0       1
# /dev/hdb2
UUID=0d3f1244-8761-4264-ae03-412f0a7de96a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
**/dev/hdd       /media/cdrom1   udf,iso9660 user,noauto,exec 0       0**
/dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0
```

The device "hdd" is the problem,the other hdc is a CD RW that works great

My dmesg | tail when i put data's cd/dvd is

```
-desktop:~$ dmesg | tail
[ 3329.450749] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 3329.450758] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 3329.450770] end_request: I/O error, dev sr1, sector 88
[ 3329.463765] ISOFS: unable to read i-node block
[ 3329.463800] isofs_fill_super: root inode is not a directory. Corrupted media?
[ 3416.602992] sr 1:0:1:0: [sr1] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE,SUGGEST_OK
[ 3416.603012] sr 1:0:1:0: [sr1] Sense Key : Hardware Error [current] 
[ 3416.603019] sr 1:0:1:0: [sr1] Add. Sense: Logical unit communication CRC error (Ultra-DMA/32)
[ 3416.603031] end_request: I/O error, dev sr1, sector 76
[ 3416.616102] UDF-fs: No VRS found
```


I been navigate in all the forums and i treated editing the fstab in some many ways with no success

Help is really appreciated!

---

### Post by daviation on 2008-05-17
I am experiencing the same problem.  I found a thread (Bug Report) indicating the problem occurs in kernel 2.6.24-16 only.  Supposedly the 2.6.24-12 kernel is OK.  I have not been able to confirm this yet.

---

### Post by mc4man on 2008-05-17
> I am experiencing the same problem. I found a thread (Bug Report) indicating the problem occurs in kernel 2.6.24-16 only. Supposedly the 2.6.24-12 kernel is OK. I have not been able to confirm this yet.
You could try loading the all_generic_ide module see here, post 80
[http://ubuntuforums.org/showthread.php?t=767449&page=8](http://ubuntuforums.org/showthread.php?t=767449&page=8)

---

