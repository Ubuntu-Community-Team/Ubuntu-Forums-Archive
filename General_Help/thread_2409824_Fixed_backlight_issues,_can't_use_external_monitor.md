---
title: "Fixed backlight issues, can't use external monitors"
date: 2019-01-07
forum: General Help
---

### Post by david395 on 2019-01-07
Running Ubuntu + i3. I have spent some time trying to fix issues with  adjusting the backlight (specifically to allow apps like xbacklight to  work). The only solution seems to be to define an xorg config such as:
*/usr/share/X11/xorg.conf.d/20-intel.conf*
```

Section "Device"
    Identifier  "Intel Graphics" 
    Driver      "intel"
    Option      "Backlight"  "intel_backlight"
EndSection
```

However this seems to replace all external monitors with VIRTUAL1, which is never active (ie. I can't use external monitors).

---

