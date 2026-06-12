---
title: "Ubuntu 20.04 No Display on 2nd monitor after 1st reboot"
date: 2020-07-09
forum: General Help
---

### Post by thomathy007 on 2020-07-09
Greetings, thank you for taking the time to read this post.

After trying to resolve the problem on my own for 6 hours, I thought I would try posting here and maybe some knowledgeable genius could help me out.

Here are some system details:
OS: Ubuntu 20.04
CPU: Intel Core i3-9350KF
GPU: Turks XT [Radeon HD 6670/7670]
MoBo: Gigabyte B365M DS3H

My problem is that I cannot display to my living room TV, but I can display through DVI to a desktop monitor. The issue arose after the first reboot. I was initially able to get a display, but now anymore. My guess is that some driver was updated when everything was initially being patched, and this caused the second display to stop being recognized.

The TV is not detected under Display Settings. I've tried connected it through HDMI and DVI via an HDMI to DVI converter, still not detected. I think the issue might also be related to the TV itself. The TV seems to indicate that there is "activity" by showing the HDMI connection as highlighted. I believe there needs to be some sort of handshake between the TV and the device. I had this issue with my Switch. I would need to boot up the Switch around the same time the TV was turned on in order for them to recognize each other. This is not the only possible cause though, as my desktop monitor also does not get display through HDMI. I've only been able to get display to my desktop monitor through DVI after the first boot up.

Since the TV worked initially, I tried uninstalling the video driver, which took me a while to figure out what it was called. lshw says the driver is "radeon", but I figured out I actually needed to uninstall "xf86-video-ati". This did not resolve the problem, then I reinstalled "xf86-video-ati". I'm not sure what else to try. This is very much a mystery to me as to what would be the problem. I wish there was an easy way to list and install different driver versions, so I could try different display drivers, but I've been pulling my hair out trying to find any info regarding this AMD driver and how to configure it or install different versions. Any info or suggestions would be greatly appreciated. I'll provide whatever info you want, just ask.

GPU info:
```

sudo lshw -c video
  *-display                 
       description: VGA compatible controller
       product: Turks XT [Radeon HD 6670/7670]
       vendor: Advanced Micro Devices, Inc. [AMD/ATI]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:136 memory:e0000000-efffffff memory:f7e20000-f7e3ffff ioport:e000(size=256) memory:c0000-dffff

```

Output of xrandr:
```

xrandr -q
Screen 0: minimum 320 x 200, current 1920 x 1080, maximum 16384 x 16384
DisplayPort-0 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-0 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 598mm x 336mm
   1920x1080     60.00*+
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1280x720      60.00  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   640x480       75.00    72.81    66.67    59.94  
   720x400       70.08 

```

---

