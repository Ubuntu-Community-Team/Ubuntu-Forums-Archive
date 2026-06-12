---
title: "Disable use of USB flash drive"
date: 2008-04-09
forum: General Help
---

### Post by darkblack on 2008-04-09
For data security reasons, is it possible to disable the use of USB flash drives in an ubuntu PC. Trying to connect a USB drive should not recognize the drive or mount it (simply do nothing) Thanks a lot

---

### Post by kpkeerthi on 2008-04-09
Just disable USB support in your BIOS.

---

### Post by mrsteveman1 on 2008-04-09
Some bios won't disable usb entirely

What you can do is prevent the kernel from loading usb mass storage class drivers when usb sticks are inserted, i believe the kernel module is called usb-storage.ko, if you rename it or move it somewhere, the kernel can't load it, and accessing usb sticks will be impossible.

---

