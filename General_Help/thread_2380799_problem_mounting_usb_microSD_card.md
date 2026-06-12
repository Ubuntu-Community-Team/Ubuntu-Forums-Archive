---
title: "problem mounting usb microSD card"
date: 2017-12-22
forum: General Help
---

### Post by matrooswolf on 2017-12-22
Hi everybody,

I have taking some pictures with a canon digital camera and I cannot copy them to my computer. I can take pictures, I can see them, I can scroll through them on my camera. But when I attach my camera to my computer (HP Probook 6570b running Ubuntu 16) it doesn't connect (using a micro usb cable).

When I take the card out of the camera and put it in a card reader I get this error:

```
Error mounting /dev/sdd1 at /media/matroosje/0123-4567: Command-line `mount -t "exfat" -o "uhelper=udisks2,nodev,nosuid,uid=1000,gid=1000,iocharset=utf8,namecase=0,errors=remount-ro,umask=0077" "/dev/sdd1" "/media/matroosje/0123-4567"' exited with non-zero exit status 32: mount: unknown filesystem type 'exfat'
```

Any help would be much appreciated! (I have movies of my little daughter dancing on that camera, that I would really like to save, she is so cute ;)

(It could be that I have used that card before for something else, if that helps, like volumio, or runeaudio, but I'm not sure, as I cannot see what's on the card...)

---

### Post by coffeecat on 2017-12-22
It looks as though you don't have the exfat driver installed in Ubuntu. It doesn't come with a default install. Try installing the packages exfat-utils and exfat-fuse. exfat-fuse is the driver, but if you try and install just one, you'll get the other as a dependency.

---

### Post by matrooswolf on 2017-12-22
Thank you Coffeecat,

That actually helped.

I did:```
sudo apt install exfat-fuse exfat-utils
``` and I can download the pictures.

Me and my daughter thank you!

---

