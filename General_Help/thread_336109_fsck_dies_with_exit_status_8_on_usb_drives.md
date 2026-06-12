---
title: "fsck dies with exit status 8 on usb drives"
date: 2007-01-11
forum: General Help
---

### Post by ryan8403 on 2007-01-11
Hi All,

Hope someone can help. I have 6.10 server edition running as an nfs server. Problem is at boot i get the following error message.

fsck.ext3: Unable to resolve 'UUID=bf2a67b2-ec21-4f56-8b8d-63eb372ac7ab'
fsck.ext3: Unable to resolve 'UUID=bc743902-4999-4f59-bcb9-2aa4f6b7fe96'
fsck.ext3: Unable to resolve 'UUID=2f5756bf-6a03-4dc2-a230-12c341d37d92'
fsck died with exit status 8

and then i boot into the maintenance shell. Promptly after booting into the maintenance shell the usb drives appear and then if i hit control-d everything is fine.

this is an ls -l on /dev/disk/by-uuid/

2f5756bf-6a03-4dc2-a230-12c341d37d92 -> ../../sdc1
84066f1a-f61f-412b-b839-2e3af0da31b1 -> ../../hda1
bc743902-4999-4f59-bcb9-2aa4f6b7fe96 -> ../../sdb1
bf2a67b2-ec21-4f56-8b8d-63eb372ac7ab -> ../../sda1
fed1eda5-82aa-48cb-815e-25810708809a -> ../../hda2

and this is my fstab

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=84066f1a-f61f-412b-b839-2e3af0da31b1 /               ext3    defaults,errors=remount-ro 0       1
# /dev/sda1
UUID=bf2a67b2-ec21-4f56-8b8d-63eb372ac7ab /media/drive1   ext3    defaults,errors=remount-ro 0       2
# /dev/sdb1
UUID=bc743902-4999-4f59-bcb9-2aa4f6b7fe96 /media/drive2   ext3    defaults,errors=remount-ro 0       2
# /dev/sdc1
UUID=2f5756bf-6a03-4dc2-a230-12c341d37d92 /media/drive3   ext3    defaults,errors=remount-ro 0       2
# /dev/hda2
UUID=fed1eda5-82aa-48cb-815e-25810708809a none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

thanks for any help that can be provided ](*,)

---

