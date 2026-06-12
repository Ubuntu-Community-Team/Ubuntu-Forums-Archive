---
title: "LCD Brightness keys fix"
date: 2020-05-22
forum: General Help
---

### Post by maestrobwh1 on 2020-05-22
This wasn't terribly easy to find, but if you have an intel card on your laptop and the brightness keys, create this file

/usr/share/X11/xorg.conf.d/20-intel.conf

```
Section "Device"
        Identifier  "card0"
        Driver      "intel"
        Option      "Backlight"  "intel_backlight"
        BusID       "PCI:0:2:0"
EndSection
```

---

