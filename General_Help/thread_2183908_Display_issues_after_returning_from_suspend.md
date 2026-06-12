---
title: "Display issues after returning from suspend"
date: 2013-10-26
forum: General Help
---

### Post by Jackson024 on 2013-10-26
I'm having issues with dual display on my laptop running 10.13 x64 after returning from suspend.  I am using the built in display on the laptop as the primary display, and an Acer monitor connected via HDIM.  I close the lid of the laptop, and when I open it back up it turns it's purplish hue and shows some animation, then goes back and the Acer gets the display and ask me to log on.  Once I log in I get an error message saying:

```
Could not switch the monitor configuration
could not set the configuration for CRTC 634
```

Prior to this one, I was getting the same message but with the code number, 635.  I set on the NVidia software the resolution and refresh rate, and that stopped.  But now this one has started.

```
$ lshw -c video
  *-display               
       description: VGA compatible controller
       product: GF106M [GeForce GT 555M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:16 memory:d4000000-d4ffffff memory:c0000000-cfffffff memory:d0000000-d1ffffff ioport:4000(size=128) memory:d2000000-d207ffff




```
```
$ xrandr
Screen 0: minimum 8 x 8, current 3520 x 1080, maximum 16384 x 16384
HDMI-0 connected 1600x900+1920+0 (normal left inverted right x axis y axis) 442mm x 249mm
   1600x900       60.0*+
   1280x800       59.8  
   1280x720       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 382mm x 215mm
   1920x1080      60.0*+  120.0    110.0    100.0  
DP-2 disconnected (normal left inverted right x axis y axis)

```

---

