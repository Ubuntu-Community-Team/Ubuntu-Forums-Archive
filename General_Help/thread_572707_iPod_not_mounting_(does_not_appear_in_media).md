---
title: "iPod not mounting (does not appear in /media/)"
date: 2007-10-10
forum: General Help
---

### Post by Warpedflash on 2007-10-10
I have been using amarok on this laptop to manage my ipod for a month or two and everything has been fine... untill recently...

basically i was having a problem when the ipod crashed out randomly while playing for long peroids of time. when to the apple store and they formatted it "for me"... great soi for home and formatted it bakc to a windows ipod. now it dosent appear in /media/ anymore and its not detected my amarok (for the previous reason)...
i'm not sure if this has any relation to the ipod being formated or i i accedently removed something needed by ubuntu for it to auto mount (one of my mates wanted to use linux a bit and i gave him control of this machine for a day... yea dumb i know)

i have looked in a few other threads and people have been asked to post this stuff so i figured it may help

dmesg (last 13 lines)

[ 5573.788000] scsi 3:0:0:0: Direct-Access     Apple    iPod             1.62 PQ: 0 ANSI: 0
[ 5573.796000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)
[ 5573.800000] sda: Write Protect is off
[ 5573.800000] sda: Mode Sense: 68 00 00 08
[ 5573.800000] sda: assuming drive cache: write through
[ 5573.808000] SCSI device sda: 1982464 2048-byte hdwr sectors (4060 MB)
[ 5573.812000] sda: Write Protect is off
[ 5573.812000] sda: Mode Sense: 68 00 00 08
[ 5573.812000] sda: assuming drive cache: write through
[ 5573.812000]  sda: sda1 sda2
[ 5573.820000] sd 3:0:0:0: Attached scsi removable disk sda
[ 5573.820000] sd 3:0:0:0: Attached scsi generic sg0 type 0

sudo fdisk -l

Disk /dev/hda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        9541    76638051   83  Linux
/dev/hda2            9542        9729     1510110    5  Extended
/dev/hda5            9542        9729     1510078+  82  Linux swap / Solaris
Note: sector size is 2048 (not 512)

Disk /dev/sda: 4060 MB, 4060086272 bytes
103 heads, 42 sectors/track, 458 cylinders
Units = cylinders of 4326 * 2048 = 8859648 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          12       96264    0  Empty
Partition 1 has different physical/logical beginnings (non-Linux?):
     phys=(0, 1, 1) logical=(0, 1, 22)
Partition 1 has different physical/logical endings:
     phys=(2, 254, 63) logical=(11, 14, 21)
Partition 1 does not end on cylinder boundary.
/dev/sda2              12         459     3868536    b  W95 FAT32
Partition 2 has different physical/logical beginnings (non-Linux?):
     phys=(3, 0, 1) logical=(11, 14, 22)
Partition 2 has different physical/logical endings:
     phys=(123, 102, 42) logical=(458, 27, 21)


all help is appreciated :)

---

### Post by Warpedflash on 2007-10-11
bump...

---

### Post by drFUNK on 2007-10-11
I'm not sure if this helps, but mine did that about a week before it showed a sad face and requied a trip back to cupertino.

---

### Post by HermanAB on 2007-10-11
See this: [http://www.aeronetworks.ca/ipod-howto.html](http://www.aeronetworks.ca/ipod-howto.html)

---

### Post by Warpedflash on 2007-10-12
> **drFUNK said:**
> I'm not sure if this helps, but mine did that about a week before it showed a sad face and requied a trip back to cupertino.

the ipod is fine (works on windows apple said it was fine) its something to do with ubuntu

> **HermanAB said:**
> See this: [http://www.aeronetworks.ca/ipod-howto.html](http://www.aeronetworks.ca/ipod-howto.html)

that didnt help... i now just have gtkpod... tis still not mounting (or not appearing to mount..)

some more info: (from that tut)

 tail -f /var/log/messages

Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.340000] VFS: Can't find a valid FAT filesystem on dev sda1.
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.384000] VFS: Can't find a valid FAT filesystem on dev sda1.
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.476000] hfs: unable to find HFS+ superblock
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.500000] hfs: unable to find HFS+ superblock
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.552000] hfs: can't find a HFS filesystem on dev sda1.
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.588000] hfs: can't find a HFS filesystem on dev sda1.
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.656000] VFS: Can't find an ext2 filesystem on dev sda1.
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.680000] VFS: Can't find an ext2 filesystem on dev sda1.
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.708000] ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1
Oct 12 18:08:58 rowan-ubuntu-laptop kernel: [72460.740000] ReiserFS: sda1: warning: sh-2021: reiserfs_fill_super: can not find reiserfs on sda1

---

### Post by Warpedflash on 2007-10-12
update : it appears my usb port has died ( laptop = 1usb) how can i test if its dead or not?

---

