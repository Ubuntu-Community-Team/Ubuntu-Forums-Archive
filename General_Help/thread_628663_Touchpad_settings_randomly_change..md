---
title: "Touchpad settings randomly change."
date: 2007-12-01
forum: General Help
---

### Post by jasonpeinko on 2007-12-01
i insatlled 7.10 on my dv6000, everything works great. But my touch pad keeps getting messed up. I disabled the tap to click, and left the verticle scrolling on. It works when i first turn it on and then will randomly turn of the scrolling and turn on tap to click

---

### Post by VCSkier on 2007-12-06
My configuration seems slightly atypical as well.  Particularly when I'm browsing in Firefox, tapping the corners of my touchpad (most often accidentally) seems to do random things...  Is there a configuration file somewhere I should check, or perhaps a GUI configuration utility I could download?

---

### Post by metalheart on 2007-12-07
The configuration information for touchpad is kept in X server configuration file /etc/X11/xorg.conf , section InputDevice (identified as 'Synaptics Touchpad' on my laptop).

Graphical tool (one of many) for changing configuration for Synaptics touchpads is QSynaptics [http://qsynaptics.sourceforge.net/ss.html](http://qsynaptics.sourceforge.net/ss.html). If you have other manufacturers device, this probably won't work.

All that is needed for basic operation (on my system) is:
```

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizEdgeScroll"       "0"
EndSection

```
Maybe you have some options defined, causing this kind of behaviour.

---

