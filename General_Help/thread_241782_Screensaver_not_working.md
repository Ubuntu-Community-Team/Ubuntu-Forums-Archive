---
title: "Screensaver not working"
date: 2006-08-22
forum: General Help
---

### Post by canadianwriterman on 2006-08-22
Has anyone noticed that their screensaver is not working after the xserver update? I'm not even getting a preview in the screensaver dialogue any more.

---

### Post by bigaltx on 2006-08-22
I have'nt updated xorg yet but I had the same problem after installing the nvidia driver. Check xorg.conf, in Section "Device" make sure driver is "nvidia". Your screensaver won't work if it's not.

---

### Post by canadianwriterman on 2006-08-23
You were right. The xserver upgrade had changed the device to "nv." All is well again. Thanks!

---

