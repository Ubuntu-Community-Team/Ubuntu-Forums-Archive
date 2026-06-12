---
title: "Sata drives recognised as removable drives"
date: 2007-04-21
forum: General Help
---

### Post by tictacman on 2007-04-21
I'm using 7.04 and xfce, and i'm trying to remove hard drive device icons from the desktop.  I've figured out that I can make them disappear by changing desktop settings > behaviour and unchecking removable devices.  However I want to see 'real' removable drives such ipod, pen drives.

In short, how can I tell feisty that my sata hard drives really are permanent drives?

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/sda6
UUID=0179ca4d-36cc-4592-9293-21d5284f67bf /               ext3    defaults,erro$
# /dev/sda3
UUID=82dd120c-8276-4ce9-a8a8-66013503503e /home           ext3    defaults     $
# /dev/sdb1
UUID=271702c7-afcd-4e5b-bf75-b887ae55f79c /mnt/backup   reiserfs defaults      $
# /dev/sda1
UUID=D6CC049ACC0476D1 /mnt/windows  ntfs    defaults,nls=utf8,umask=007,gid=46 $
# /dev/sda5
UUID=c9eaac10-cf13-44c0-a16e-67daa4528306 none            swap    sw           $
/dev/hdb        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/fd0        /media/floppy0  auto    rw,user,noauto  0       0

---

