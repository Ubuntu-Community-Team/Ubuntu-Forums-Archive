---
title: "Higher displays not seen after changing VGA cable"
date: 2017-01-31
forum: General Help
---

### Post by Milind on 2017-01-31
My PC is an Ubuntu 16.10/Win 10 dual boot machine.

Processor:Intel® Core™2 Duo CPU E7400 @ 2.80GHz × 2 
Graphics: Intel® G33 
2GB Ram

A few days ago the display started turning weird shades of green, though I could still use the computer. The VGA cable seemed to be loose & at fault, so I changed it. After changing, though the colours were back to normal, in both Ubuntu & Windows 10 the maximum resolution shown was 1024*768 @60 Hz, though the Dell LCD monitor's maximum is 1600*900 @60 Hz. In Windows, I could find the higher settings in Advanced Display Settings and get things back to normal. But Ubuntu Settings do not show any resolutions except 800*600, & 1024*768. How can I get the higher resolutions back?

Thanks in advance for any help.

---

### Post by thehipho on 2017-01-31
run the xrandr command to see all the resolutions?

```
xrandr
```

---

