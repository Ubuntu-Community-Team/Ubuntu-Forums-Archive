---
title: "Partition image backup: xfs, image file splitting, Clonezilla"
date: 2014-10-01
forum: General Help
---

### Post by Kirkx on 2014-10-01
I use Clonezilla for creating image files to save and restore Linux logical partitions. I can save and restore partitions without problems but I'm trying to fine tune the process. Any ideas would be appreciated. Here is the layout:

- hard disk: 500 GB with 512 byte sectors (Seagate ST500DM002)
- MBR and 3 Windows primary partitions: for now backed-up and restored with Acronis True Image on BartPE (because it has incremental backups)
- several logical Ext4 partitions with a few Linux distros (backed-up and restored with Clonezilla)
- dedicated Clonezilla image repository partition: file system type XFS
- Clonezilla v2.2.3-25 (because it has been tested and works ok on my hardware)

I have three questions.

1) Is it really a good idea to have XFS file system type for the dedicated Clonezilla image repository partition? I have read somewhere that XFS is better than Ext4 if you have large files. Some of my image files are 2-3 GB, so XFS seems to make sense.

2) In my script that runs "saveparts" (to create a partition image) I have turned off image file splitting by using:

-i 1024000

instead of the default:

-i 2000

Are there any advantages of having image files split into a few parts? I've been using single image files for my Windows XP Acronis backups w/o any problems for years. Windows XP full backup image file is always around 8 GB (incrementals are around 500 MB). Xubuntu full backup image files created with Clonezilla are much smaller (2.2 GB with gzip, 2.6 GB with lzop) so I'm not sure about the merits of splitting them up.

Here is the complete "saveparts" script:

```

#!/bin/bash
datetime=$(date +"%y%m%d-%H%M")
/usr/sbin/ocs-sr -q2 -j2 -z1 -i 1024000 -fsck-src-part-y -p true saveparts linuxlite-$datetime sda21 sda22

```

3) In my script that runs "restoreparts" (to restore partition from an image) I have the parameter -e2. It was preset by defualt and I just left it intact because I'm not sure if it's really needed in my particular situation:

a) the bootloader installed in MBR is BootUS (it boots to different versions of Windows)
b) the bootloader installed in PBR of 3rd primary partition is Grub4Dos (it boots to different Linux distros)
c) Grub2 of any Linux distro is never used for normal booting and is only used in emergencies
d) I never restore MBR with Clonezilla (parameter -t)
e) I don't want Clonezilla to overwrite existing partition table when restoring a partition (parameter -k)

Here is the complete "restoreparts" script:

```

#!/bin/bash
/usr/sbin/ocs-sr -e2 -c -t -r -k -p true restoreparts ask_user sda21 sda22

```

-e2 [--load-geometry-from-edd]: force to use the CHS (cylinders, heads, sectors) from EDD (Enhanced Disk Device) instead of from kernel when creating partition table by sfdisk. Recommended for non-grub bootloader.

-t: do not restore MBR
-k: do not create/overwrite partition table

Should the parameter -e2 be removed from the command line or is it better to leave it as is?

-----------
Help Links:

[http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php](http://clonezilla.org/clonezilla-live/doc/02_Restore_disk_image/advanced/09-advanced-param.php)

[http://drbl.org/faq/fine-print.php?path=./2_System/88_mbr_related_options.faq#88_mbr_related_options.faq](http://drbl.org/faq/fine-print.php?path=./2_System/88_mbr_related_options.faq#88_mbr_related_options.faq)

Original Post on Clonezilla Forums:

[https://sourceforge.net/p/clonezilla/discussion/Clonezilla_live/thread/a5814dab/](https://sourceforge.net/p/clonezilla/discussion/Clonezilla_live/thread/a5814dab/)

---

### Post by Bucky Ball on 2014-10-01
*Thread moved to **General Help**.*

Better here and may improve your chances of getting support. (***Installation & Upgrades*** is for support issues related to the install and upgrading of the Ubuntu OS itself). Good luck. ;)

---

