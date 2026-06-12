---
title: "ATI integrated graphics - how to control overscan"
date: 2016-02-20
forum: General Help
---

### Post by nmw01223 on 2016-02-20
Using 14.04. Motherboard has integrated ATI HD3200 graphics and the Open Source driver is installed. The screen in a Sony TV that overscans on HDMI (only available connection) and there is no way of disabling overscan in the TV.

How can I control the overscan from the Linux installation? I've tried xrandr:
```

xrandr --output HDMI-0 --set "underscan hborder" 71 --set "underscan vborder" 39
xrandr --output HDMI-0 --set underscan on

```
and whilst the screen flashes in an encouraging way when one does that, nothing actually changes.

I've tried to find a proprietary driver, but there doesn't appear to be one. Nothing in additional drivers with restricted enabled, anyway. The AMD site doesn't list a driver for that integrated graphics hardware.

I'm tearing my hair out over this. There must be a way of controlling it? I know how to do it with nVidia, but there appears to be nothing equivalent for ATI?

---

