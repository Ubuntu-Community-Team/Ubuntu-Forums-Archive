---
title: "udev rule not working"
date: 2015-06-21
forum: General Help
---

### Post by dtree46 on 2015-06-21
# Be Pro
SUBSYSTEM=="usb", ATTR{idVendor}=="0e8d", ATTR{idProduct}=="201d", MODE="0666", GROUP="dlw"

Also tried with: ATTRS

Any help appreciated.
dlw

---

