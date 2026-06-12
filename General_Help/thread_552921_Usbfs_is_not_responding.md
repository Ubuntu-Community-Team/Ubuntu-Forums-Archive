---
title: "Usbfs is not responding"
date: 2007-09-17
forum: General Help
---

### Post by Robbyx on 2007-09-17
When I use the file manager XFE I am getting an error message

mount point /proc/bus/usb/.usbfs is not responding.

Does any one know why I am getting the error message?

```
proc /proc proc defaults 0 0
tmpfs /dev/shm tmpfs defaults,ro 0 0
usbfs /proc/bus/usb usbfs auto 0 0
# Entry for /dev/hda1 :
UUID=221d448e-c456-4e67-b1f4-675a654e16c8 / ext3 defaults,errors=remount-ro,data=writeback,noatime 0 0
# Entry for /dev/hda5 :
UUID=5abbef3f-03f4-4927-868f-93ec33fe1a6f none swap sw 0 0
/dev/hdc /media/cdrom0 udf,iso9660 user,noauto 0 0
/dev/fd0 /media/floppy0 auto rw,user,noauto 0 0
/dev/hdb1 /media/hdb1 vfat iocharset=utf8,umask=000 0 0
/dev/sda1 /media/sda1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/sdb1 /media/sdb1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb5 /media/hdb5 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb6 /media/hdb6 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdb7 /media/hdb7 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd1 /media/hdd1 ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
/dev/hdd5 /media/win2k4msi ntfs-3g defaults,uid=1000,gid=1000,locale=en_US.utf8 0 0
```

Robin

---

### Post by Robbyx on 2007-09-18
Is there anyone who can comment on my problem?

Robin

---

