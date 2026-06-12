---
title: "Could someone check my fstab for me please?"
date: 2007-02-11
forum: General Help
---

### Post by tictacman on 2007-02-11
I was checking dmesg (which had errors) earlier on and noticed that my cdrom/dvdwriter is listed as hda, whereas my hard drive partitions are also hda partitions and I am wondering if this wrong (shouldn't been hdc or something).  Here is output from fdisk -l:

Disk /dev/sda: 163.9 GB, 163928604672 bytes
255 heads, 63 sectors/track, 19929 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1        3648    29302528+   7  HPFS/NTFS
/dev/sda2            3649        7296    29302560    f  W95 Ext'd (LBA)
/dev/sda3            7297       19929   101474572+  83  Linux
/dev/sda5            3649        3712      514048+  82  Linux swap / Solaris
/dev/sda6            3713        7296    28788448+  83  Linux

Disk /dev/sdb: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               2       30401   244188000    f  W95 Ext'd (LBA)
/dev/sdb5               2       30401   244187968+   7  HPFS/NTFS



Here is my fstab file that I would like checked:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=43cdf8d7-d10b-47cc-a94e-ed6ce3bda1d9 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda3
UUID=82dd120c-8276-4ce9-a8a8-66013503503e /home           ext3    defaults        0       2
# /dev/sdb5
UUID=5AC0F147C0F12A41 /media/backup   ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda1
UUID=D6CC049ACC0476D1 /media/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/sda5
UUID=c9eaac10-cf13-44c0-a16e-67daa4528306 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

and here is the tail end of dmesg that had errors - specifically complaining that it couldn't open the tray (why?):

Bluetooth: RFCOMM ver 1.7
[17184659.016000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17184659.028000] ISOFS: changing to secondary root
[17185307.796000] hda: tray open
[17185307.796000] end_request: I/O error, dev hda, sector 64
[17185307.796000] Buffer I/O error on device hda, logical block 8
[17185307.796000] hda: tray open
[17185307.796000] end_request: I/O error, dev hda, sector 64
[17185307.796000] Buffer I/O error on device hda, logical block 8
[17185307.804000] hda: tray open
[17185307.804000] end_request: I/O error, dev hda, sector 64
[17185307.804000] Buffer I/O error on device hda, logical block 8
[17185307.880000] hda: tray open
[17185307.880000] end_request: I/O error, dev hda, sector 64
[17185307.880000] Buffer I/O error on device hda, logical block 8
[17185307.888000] hda: tray open
[17185307.888000] end_request: I/O error, dev hda, sector 64
[17185307.888000] Buffer I/O error on device hda, logical block 8
[17185325.744000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17185325.744000] ISOFS: changing to secondary root
[17185678.428000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17185678.428000] ISOFS: changing to secondary root
[17185857.340000] hda: tray open
[17185857.340000] end_request: I/O error, dev hda, sector 64
[17185857.340000] Buffer I/O error on device hda, logical block 8
[17185857.344000] hda: tray open
[17185857.344000] end_request: I/O error, dev hda, sector 64
[17185857.344000] Buffer I/O error on device hda, logical block 8
[17185875.084000] ISO 9660 Extensions: Microsoft Joliet Level 1
[17185875.084000] ISOFS: changing to secondary root
[17190998.864000] NVRM: Xid (0003:00): 6, PE0002 11ec c0395b84 000f0328 00000000 00183400
[17190998.864000] NVRM: Xid (0003:00): 28,  L1 -> L0
[17194552.440000] uli526x: eth0 NIC Link is Up 100 Mbps Full duplex
[17203265.104000] NVRM: Xid (0003:00): 6, PE0002 0004 00102400 00110e9c 00010004 00043450
[17203265.104000] NVRM: Xid (0003:00): 28,  L1 -> L0
[17203900.588000] NVRM: Xid (0003:00): 6, PE0002 180c 00000000 00000000 00000000 00000000
[17203900.588000] NVRM: Xid (0003:00): 28,  L1 -> L0
[17204581.504000] NVRM: Xid (0003:00): 6, PE0002 0000 3f79f3e8 0008e794 00000000 01000101
[17204581.504000] NVRM: Xid (0003:00): 28,  L1 -> L0
[17204583.656000] NVRM: Xid (0003:00): 6, PE0002 0a00 04000007 00046204 00000000 00000000
[17204583.656000] NVRM: Xid (0003:00): 28,  L1 -> L0
[17204583.660000] NVRM: Xid (0003:00): 6, PE0002 08f4 130e0300 00000000 00000000 00000000
[17204583.660000] NVRM: Xid (0003:00): 28,  L0 -> L0
[17204628.524000] NVRM: Xid (0003:00): 13, 0002 beef3097 00003597 0000023c 00182900 00000002
[17204628.524000] NVRM: Xid (0003:00): 28,  L1 -> L0
[17204700.264000] NVRM: Xid (0003:00): 6, PE0002 0a00 04000007 00110814 be9ec654 be6bd051
[17204700.264000] NVRM: Xid (0003:00): 28,  L1 -> L0
[17251655.780000] ISO 9660 Extensions: Microsoft Joliet Level 3
[17251655.924000] ISOFS: changing to secondary root


If anyone could enlighten me as to what is happening here I would grateful.

---

### Post by PgR on 2007-02-11
Hmm. I don't see where it's refering to your hard drive partitions as hda partitions.

It looks to me as though you've a dual-booting machine with Windows, and your HDD's are either SATA or SCSI, and your DVD is the only IDE/ATA device you have... In which case your fstab is correct...

Don't know about opening the tray, though.

---

