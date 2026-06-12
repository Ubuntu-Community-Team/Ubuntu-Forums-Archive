---
title: "Trouble Mounting dvd"
date: 2007-10-08
forum: General Help
---

### Post by Thorin129 on 2007-10-08
Hey all,

My drive won't mount some newer game dvd/cds such as Medal of Honor Airborne, CNC3, Civ4, etc..I tried making it automount, but no avail...
Here's the error it gives me.



baller123@baller123-pc:~$ sudo mount /dev/hdc
mount: block device /dev/hdc is write-protected, mounting read-only
mount: wrong fs type, bad option, bad superblock on /dev/hdc,
       missing codepage or other error
       In some cases useful info is found in syslog - try
       dmesg | tail  or so


Here's the /fstab:

# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda2
UUID=b9b6cbe9-927b-4e07-a41f-9841d8da7eaf /               ext3    defaults,errors=remount-ro 0       1
# /dev/hda5
UUID=1029a0c8-57a8-4d63-94f1-932f33c52b3e none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,auto     0       0

---

