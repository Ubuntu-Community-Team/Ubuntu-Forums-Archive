---
title: "Nvidia display resolution resets to &quot;Auto&quot; after reboot (w/ xorg.conf edited)"
date: 2014-02-01
forum: General Help
---

### Post by DIFTOW on 2014-02-01
Using Ubuntu 13 and the GPU is a GT 630 (uses the latest Nvidia drivers)

I've edited the Xorg.conf file to remove the portion that specifies "auto-detect" so it is only the resolution I want, which is 1280x800.
But when I reboot, Nvidia is using "auto" which is setting it to 1920x1080; which makes the text on many websites and applications too small for my older relatives to read.

This is what is specified in the xorg.conf

```
Section "Screen"

    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "1280x800_60 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
```

---

### Post by jp734 on 2014-02-01
Try adding **Modes "1280x800"** under **SubSection "Display"** and also end the config with **EndSection.**

[COLOR="#0000FF"]Section ""[/COLOR]
[COLOR="#FF0000"]   SubSection ""
   EndSubSection ""[/COLOR]
[COLOR="#0000FF"]EndSection ""[/COLOR]

---

