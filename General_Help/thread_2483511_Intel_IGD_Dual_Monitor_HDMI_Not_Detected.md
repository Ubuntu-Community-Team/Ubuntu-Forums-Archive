---
title: "Intel IGD Dual Monitor HDMI Not Detected"
date: 2023-02-01
forum: General Help
---

### Post by surahman on 2023-02-01
Hello,

I am running into an issue where my second monitor, attached to HDMI, is not being detected by Ubuntu. The primary display plugged into the DP is working great. If I boot with the HDMI cable unplugged and then plug it in once booted the secondary display tends to flicker on/off. If I boot with the HDMI cable plugged in the display stays in standby mode. This makes me believe there is a signal being sent from the HDMI port on the motherboard. I have also tried setting the BIOS to use the IGD and disabling secure boot. My motherboard does support dual displays through the IGD DP and HDMI ports.

Any thoughts on how I can correct this issue?


Thank you,


> 
> lsb_release -a
No LSB modules are available.
Distributor ID: Ubuntu
Description: Ubuntu 22.10
Release: 22.10
Codename: kinetic


> 
> uname -r
5.19.0-29-generic


> 
> lspci | grep VGA
00:02.0 VGA compatible controller: Intel Corporation Raptor Lake-S UHD Graphics (rev 04)


> 
> sudo lshw -C display
*-display
description: VGA compatible controller
product: Raptor Lake-S UHD Graphics
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
logical name: /dev/fb0
version: 04
width: 64 bits
clock: 33MHz
capabilities: pciexpress msi pm vga_controller bus_master cap_list rom fb
configuration: depth=32 driver=i915 latency=0 mode=3840x2160 resolution=3840,2160 visual=truecolor xres=3840 yres=2160
resources: iomemory:600-5ff iomemory:400-3ff irq:174 memory:6000000000-6000ffffff memory:4000000000-400fffffff ioport:4000(size=64) memory:c0000-dffff memory:4010000000-4016ffffff memory:4020000000-40ffffffff

> 
xrandr
Screen 0: minimum 16 x 16, current 3840 x 2160, maximum 32767 x 32767
XWAYLAND0 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 700mm x 400mm
   3840x2160     59.98*+
   2048x1536     59.95  
   1920x1440     59.90  
   1600x1200     59.87  
   1440x1080     59.99  
   1400x1050     59.98  
   1280x1024     59.89  
   1280x960      59.94  
   1152x864      59.96  
   1024x768      59.92  
   800x600       59.86  
   640x480       59.38  
   320x240       59.52  
   2560x1600     59.94  
   1920x1200     59.88  
   1680x1050     59.95  
   1440x900      59.89  
   1280x800      59.81  
   720x480       59.71  
   640x400       59.95  
   320x200       58.96  
   3200x1800     59.96  
   2880x1620     59.96  
   2560x1440     59.96  
   2048x1152     59.90  
   1920x1080     59.96  
   1600x900      59.95  
   1368x768      59.88  
   1280x720      59.86  
   1024x576      59.90  
   864x486       59.92  
   720x400       59.55  
   640x350       59.77 


---

