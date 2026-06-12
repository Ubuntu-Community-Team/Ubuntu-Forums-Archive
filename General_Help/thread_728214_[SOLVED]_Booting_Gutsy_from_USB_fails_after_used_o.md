---
title: "[SOLVED] Booting Gutsy from USB fails after used once"
date: 2008-03-18
forum: General Help
---

### Post by T0MA on 2008-03-18
Hi all,
I followed the guide [http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/](http://www.pendrivelinux.com/2007/09/28/usb-ubuntu-710-gutsy-gibbon-install/) to install Gutsy on my 8gb sandisk thumbdrive and it works fine.

The problem is that after I restart Ubuntu that I booted from the USB, the USB becomes unbootable, so I have to fix it from my permanent Ubuntu with lilo. After that it will become bootable again but the same problem occurs after I boot and restart from the USB.

Any idea how can I fix this?

---

### Post by T0MA on 2008-03-20
Ok, I figured out what was the problem. When I restart it asks to remove the disk from the cd just as if I booted from a Live CD. If I leave the usb drive plugged in it makes it unbootable. Simple solution is to remove the drive when it says and the usb's mbr won't be touched this way.

It is still weird that it messes up the mbr on the usb though.

---

