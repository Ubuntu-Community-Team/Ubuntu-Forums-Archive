---
title: "Ubuntu 16.04 doesn't see my usb periphials"
date: 2016-08-01
forum: General Help
---

### Post by burt67 on 2016-08-01
Trying to plug in, via usb, zoom Q4N video camera as an SD card reader, but this is what it tells me...

Error mounting /dev/sdb1 at /media/burt/Q4N_SD: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdb1" "/media/burt/Q4N_SD"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'

How can I fix this? I just did a complete update on the OS...

BTW, I'm a techno-noob...

---

### Post by burt67 on 2016-08-01
Nevermind...Installed ExFat utility

```
sudo apt-get install exfat-utils exfat-fuse
```

---

