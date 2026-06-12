---
title: "Trouble with HAL cdroms and usb devices"
date: 2007-12-15
forum: General Help
---

### Post by kthakore on 2007-12-15
Fairly recently I started getting "failed to initialize HAL" popup on logon. After that I have been unable to copy stuff from cds dvds and use usb devices. I came across a fix that made it a little better, where I would do "sudo /etc/init.d/dbus restart" and log out and log back in. This mount my cds properly and I don't get a pop up say hal failed to initialize but I still get an I/O error when I copy from it. What can I do?

Here is my /etc/fstab

```


# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    defaults        0       0
# /dev/hda1
UUID=f505c445-7a30-47df-8098-636afb05e872 /               reiserfs notail          0       1
# /dev/hda6
UUID=17771f8e-2de0-4d18-af4a-039e4f309d78 /home           reiserfs defaults        0       2
# /dev/hdb1
# UUID=3987df69-e36b-4291-8961-42b30266f67e /media/hdb1     ext3    defaults        0       2
# /dev/hdb2
 UUID=a85ded52-5379-4c28-8d88-e7999422a4de /media/hdb2     ext3    defaults        0       2
/dev/hda5   none           swap    sw              0       0
#UUID=f7fa4180-0918-41e9-8e89-abf11114b4c2 none            swap    sw              0       0
# /dev/hdb3
# UUID=981b8340-587b-439a-bf69-5c88550d12e8 none            swap    sw              0       0
/dev/hdc        /media/cdrom0   udf,iso9660 user,noauto,exec 0       0
# /dev/fd0        /media/floppy0  auto    rw,user,noauto,exec 0       0

```

---

