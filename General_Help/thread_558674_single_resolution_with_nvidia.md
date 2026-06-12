---
title: "single resolution with nvidia"
date: 2007-09-24
forum: General Help
---

### Post by mrpeenut24 on 2007-09-24
My xorg.conf file has *no* entry for any resolution, and I only have the one option in my System>Preferences>Screen Resolution (1680x1050), however, I would like to have more options.  I'm running Gutsy, so that may be an issue, and if so, please feel free to move this thread into the correct topic.  How can I add more resolutions?  Here's (the relevant sections from) my xorg.conf file (if you need the whole thing let me know):

```
Section "Monitor"

    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Seiko"
    HorizSync       30.0 - 75.0
    VertRefresh     61.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce Go 7600"
EndSection

Section "Screen"

    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```

---

