---
title: "Unable to mount SD card"
date: 2016-04-15
forum: General Help
---

### Post by duckfeeder105.5 on 2016-04-15
So I've got a chromebook. I've installed Crouton on it and installed unity with the ubuntu desktop. When I put my sd card in, it asks me for password - I put it in and I get this error

```
Error mounting /dev/mmcblk1p1 at /media/bobotov/3333-3331: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/mmcblk1p1" "/media/bobotov/3333-3331"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
```

---

### Post by papibe on 2016-04-15
Hi duckfeeder105.5.

It looks like an exfat formated card. Try installing this, and then try to mount it again.
```
sudo apt-get install exfat-utils exfat-fuse
```
Hope it helps. Let us know how it goes.
Regards.

---

### Post by duckfeeder105.5 on 2016-04-15
Thank you for the reply, papibe. It seems to have worked, but I will keep this thread open 'til something goes wrong.

Edit: Just a side note: It's a microsd card.

---

### Post by Boju! on 2016-04-26
Thank you Papibe! This fixed the same problem with me mounting my microSD card on my laptop.

---

