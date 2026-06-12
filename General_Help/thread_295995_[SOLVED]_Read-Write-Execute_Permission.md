---
title: "[SOLVED] Read-Write-Execute Permission"
date: 2006-11-08
forum: General Help
---

### Post by HanaD on 2006-11-08
Hello friends!

I have daul booting system,

i am using Kubuntu(edgy), and can acess my NTFS file systems from it.
i wish to give read-write-edit and execute permissions to the NTFS files when i am logged in from Ubuntu..

Below is my /etc/fstab file..
Please help.. how should i alter the umask in order to give all permissions for NTFS partitions.


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hdb4
UUID=4e949b38-864c-4a76-83d6-ceb3e59493e8 /               ext3    defaults,errors=remount-ro 0       1
# /dev/hdb1
UUID=A48878118877E06A /media/hdb1     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb3
UUID=38F09D7FF09D4452 /media/hdb3     ntfs    defaults,nls=utf8,umask=007,gid=46 0       1
# /dev/hdb2
UUID=f69ce50e-34b8-4cab-b454-f5360fbefc78 none            swap    sw              0       0
/dev/hda        /media/cdrom0   udf,iso9660 user,noauto     0       0
/dev/           /media/floppy0  auto    rw,user,noauto  0       0

Regards,

Hana

---

### Post by aysiu on 2006-11-09
[HOWTO: NTFS with read/write support using the ntfs-3g (easy & safe method)](http://ubuntuforums.org/showthread.php?t=217009)

---

