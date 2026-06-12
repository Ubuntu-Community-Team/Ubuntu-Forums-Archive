---
title: "Ubuntu 14.04 exfat problem"
date: 2014-08-07
forum: General Help
---

### Post by zuheyr2 on 2014-08-07
Hello,

Problem mounting USB or camera on Ubuntu 14.04 Acer C720 chromebook, 64 bit:

Error mounting /dev/sdb1 at /media/user/disk: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/user/disk"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

I found a solution, using Disks utility and changing the automount options, it does let me change the mount point to, say what the post says /mnt/Data but it does not let me change the item "Identify as" as it is hown in the post. n off th

When I use turn off the automount and try to mount myself I get

Error mounting system-managed device /dev/sdb1: Command-line `mount "/mnt/pci-0000:00:14.0-usb-0:2:1.0-scsi-0:0:0:0-part1"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'



I will greatly appreciate if you can help please. Thanks for reading, regards.

---

### Post by zuheyr2 on 2014-08-07
[TABLE]
[TR]
[TD="class: votecell"]Hi,

Sorry I solved my problem.
Installing the below packages only will auto-mounts your exFAT formatted drives ,
  sudo apt-get install exfat-fuse exfat-utils


[/TD]
                [TD="class: answercell"]     
[/TD]
[/TR]
[/TABLE]

---

### Post by z3usbo1 on 2014-12-13
> **zuheyr2 said:**
> [TABLE]
[TR]
[TD="class: votecell"]Hi,

Sorry I solved my problem.
Installing the below packages only will auto-mounts your exFAT formatted drives ,
[SIZE=7]  sudo apt-get install exfat-fuse exfat-utils[/SIZE]


[/TD]
                [TD="class: answercell"]     
[/TD]
[/TR]
[/TABLE]

Brilliant! solved my issue in no time.
Thanks

---

