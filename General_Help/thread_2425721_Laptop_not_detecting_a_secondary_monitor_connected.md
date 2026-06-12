---
title: "Laptop not detecting a secondary monitor connected via HDMI"
date: 2019-08-29
forum: General Help
---

### Post by deejayjohn on 2019-08-29
Hi, 

My laptop has stopped detecting my secondary monitor via HDMI (it used to work before). I can connect to my secondary monitor via VGA still. 

xrandr doesn't show any HDMI. 

```

**$ xrandr**
Screen 0: minimum 320 x 200, current 3840 x 1080, maximum 8192 x 8192
XWAYLAND0 connected 1920x1080+1920+0 (normal left inverted right x axis y axis) 340mm x 190mm
   1920x1080     59.96*+
XWAYLAND3 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 530mm x 300mm
   1920x1080     59.96*+

```


I am running Ubuntu SMP with lightdm. 

```

** #lshw -c video**
  *-display                 
       description: VGA compatible controller
       product: Intel Corporation
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 04
       width: 64 bits
       clock: 33MHz
       capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:129 memory:db000000-dbffffff memory:80000000-9fffffff ioport:f000(size=64) memory:c0000-dffff

```

I am not really sure how to check if its a hardware or a driver issue? It would be great if someone could help me figure it out.

Thanks

---

