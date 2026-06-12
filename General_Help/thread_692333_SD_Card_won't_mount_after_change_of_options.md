---
title: "SD Card won't mount after change of options"
date: 2008-02-09
forum: General Help
---

### Post by hops on 2008-02-09
I mounted a 4GB Micro SD card (in an adapter) and it came up read only.  I decided to change it using properties->Volume->settings.  The change that I made was invalid and now everytime I try to mount the SD card I get a popup which says that it Cannot mount the volume.  The error message is "Invalid mount option when attempting to mount the volume".  Now I don't know how to get back to the original mount options.

I did a udevinfo:

Udevinfo:
P: /block/mmcblk0
N: mmcblk0
S: disk/by-id/mmc-SU04G_0x20000c3c
E: DEVTYPE=disk
E: ID_NAME=SU04G
E: ID_SERIAL=0x20000c3c

P: /block/mmcblk0/mmcblk0p1
N: mmcblk0p1
S: disk/by-id/mmc-SU04G_0x20000c3c-part1
S: disk/by-uuid/6333-6330
E: DEVTYPE=partition
E: ID_NAME=SU04G
E: ID_SERIAL=0x20000c3c
E: ID_FS_USAGE=filesystem
E: ID_FS_TYPE=vfat
E: ID_FS_VERSION=FAT32
E: ID_FS_UUID=6333-6330
E: ID_FS_UUID_ENC=6333-6330
E: ID_FS_LABEL=
E: ID_FS_LABEL_ENC=
E: ID_FS_LABEL_SAFE=

The relevant lines from dmesg:

[ 4921.240000] mmcblk0: mmc0:d555 SU04G 3979776KiB (ro)
[ 4921.240000]  mmcblk0: p1
[ 4964.720000] mmcblk0: mmc0:d555 SU04G 3979776KiB (ro)
[ 4964.720000]  mmcblk0: p1
[ 5008.900000] mmcblk0: mmc0:d555 SU04G 3979776KiB (ro)
[ 5008.900000]  mmcblk0: p1

Any help greatly appreciated.

---

