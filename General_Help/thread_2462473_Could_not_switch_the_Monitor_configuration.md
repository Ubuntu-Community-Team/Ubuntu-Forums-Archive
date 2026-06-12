---
title: "Could not switch the Monitor configuration"
date: 2021-05-21
forum: General Help
---

### Post by monkeybrain20122 on 2021-05-21
Whenever my laptop wakes up from suspension, there is a warning that says "Could not switch the Monitor configuration, could not set the configuration for CRTC 441"

I have googled the issue but everything I found involves people having two graphic cards or two monitors, I have only one graphic card (Nvidia GTX 1070) and no external monitor is attached
```
$ xrandr -q
Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 32767 x 32767
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.02*+  47.99  
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)

```

```
$ lshw -C video
WARNING: you should run this program as super-user.
  *-display                 
       description: VGA compatible controller
       product: GP104BM [GeForce GTX 1070 Mobile]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:140 memory:db000000-dbffffff memory:90000000-9fffffff memory:a0000000-a1ffffff ioport:e000(size=128) memory:c0000-dffff
```

Other than a mild annoyance when computer wakes up from suspension the message seems to be harmless as everything functions normally. Is there a way to get rid of it if fails to diagnose the underlying issue?

Ubuntu 20.04, graphic card is Nvidia GTX 1070 with Nividia driver 460

---

