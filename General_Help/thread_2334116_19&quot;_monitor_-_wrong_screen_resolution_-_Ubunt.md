---
title: "19&quot; monitor - wrong screen resolution - Ubuntu 16.04.1"
date: 2016-08-16
forum: General Help
---

### Post by rezs on 2016-08-16
Problem: 19” 1280 X 1024 native resolution Samsung LCD monitor is showing up as “Unknown Display” with a new installation of Ubuntu 16.04.1.  Result:  I can only get Ubuntu to deliver non-native resolutions of 1024 X 768 or 1152x864, which result in magnified blurry non-native images.

 Is there some way to delve into the Ubuntu software and switch to the native monitor resolution of 1280 X 1024?

 Monitor:  Samsung Synchmaster model 913N 19” VGA (no monitor DVI connector) LCD 4:3 ratio (non-widescreen) monitor with a native resolution of 1280 X 1024, pixel pitch of 0.294, max V-synch rate 75 Hz,  max H-synch rate 81 Hz, video bandwidth 140 MHz – other specs available on request.

 Over the years this monitor has worked automagically at that native ratio on different linux computers with different linux distributions and different video drivers: both Intel and nVidia.  I never had to give it a thought.  This monitor has outlived several computers - I would like to keep it going if I can.

 Currently, however:
 
(1) When using the Intel drivers on this computer (onboard motherboard VGA Intel GMA X4500 graphics controller), I am offered a maximum resolution of 1024 X 768, resulting in a blurry, non-native magnified image.

 (2) When switching over to a PCIex16 nVidia 7600GT card using the open source nouveau driver, I am offered a maximum resolution of 1024 X 768 resulting in a blurry, non-native magnified image.

(3) The Vesa driver: same.
 
 (4) When using the proprietary legacy 304.131 nVidia driver (appropriate to this circa 2008 video card), I am offered some unusual options: in addition to the usual 1024 X 768, I now have the option of 1152x864 – closer, but still not the native 1280 X 1024.

 Looking at Ubuntu Settings, my Samsung monitor is listed as an “Unknown Display.”  I think that it was recognized as a Samsung in earlier years, but memory is imperfect and I am not certain.  Perhaps the monitor is no longer identifying itself properly – or perhaps the circa 2005 monitor driver is no longer available in current linux distros.

 Is there any way I can delve into the Ubuntu software and fix this matter?
 
 Thank you,

rezs

 $ xrandr
 Screen 0: minimum 8 x 8, current 1152 x 864, maximum 4096 x 4096
 DVI-I-0 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
    1024x768      60.00 +
    1360x768      59.96    59.80   
    1152x864      60.00*  
    800x600       72.19    60.32    56.25   
    680x384       59.96    59.80   
    640x480       59.94   
    576x432       60.06   
    512x384       60.00   
    400x300       72.19    60.32    56.34   
    320x240       60.05   
 DVI-I-1 disconnected (normal left inverted right x axis y axis)
 TV-0 disconnected (normal left inverted right x axis y axis)
 DVI-I-2 disconnected (normal left inverted right x axis y axis)
 DVI-I-3 disconnected (normal left inverted right x axis y axis)
 
 *Note: when plugged into the onboard motherboard graphics, I just use a regular VGA-VGA cable.  When plugged into the PCIeX16 nVidia 7600GT card, which has two DVI-I connectors and no VGA connector, I use a DVI-I<->VGA converter – so it shows up as DVI with xrandr, but it is really VGA into the monitor.  The same problem with wrong resolutions occurs in all the hardware setups I am using – different computers - both pure VGA, and also DVI-I <–> VGA converter.
 
 $ lspci -nnk | grep -i vga -A3
 01:00.0 VGA compatible controller [0300]: NVIDIA Corporation G73 [GeForce 7600 GT] [10de:0391] (rev a1)
     Subsystem: Gigabyte Technology Co., Ltd G73 [GeForce 7600 GT] [1458:3417]
     Kernel driver in use: nvidia
     Kernel modules: nvidiafb, nouveau, nvidia_304

 Samsung Synchmaster model 913N Monitor Specs:
[http://www.manualmonitor.com/manuals/samsung/Samsung_SyncMaster_913N.pdf](http://www.manualmonitor.com/manuals/samsung/Samsung_SyncMaster_913N.pdf)

---

### Post by Hirak Mehta on 2016-08-16
see this discussion it worked on my PC

[https://ubuntuforums.org/showthread.php?t=1638895](https://ubuntuforums.org/showthread.php?t=1638895)

---

### Post by rezs on 2016-08-16
Hirak,

Thank you for your help!

I gave it a whirl but I probably did something wrong.  If you could take a look, I would appreciate it:

$ xrandr
 Screen 0: minimum 8 x 8, current 1152 x 864, maximum 4096 x 4096
 DVI-I-0 connected primary 1152x864+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
    1024x768      60.00 +
    1360x768      59.96    59.80   
    1152x864      60.00*  
    800x600       72.19    60.32    56.25   
    680x384       59.96    59.80   
    640x480       59.94   
    576x432       60.06   
    512x384       60.00   
    400x300       72.19    60.32    56.34   
    320x240       60.05   
 DVI-I-1 disconnected (normal left inverted right x axis y axis)
 TV-0 disconnected (normal left inverted right x axis y axis)
 DVI-I-2 disconnected (normal left inverted right x axis y axis)
 DVI-I-3 disconnected (normal left inverted right x axis y axis)

   $ cvt 1024 768
 # 1024x768 59.92 Hz (CVT 0.79M3) hsync: 47.82 kHz; pclk: 63.50 MHz
 Modeline "1024x768_60.00"   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync
 
 $ cvt 1280 1024
 # 1280x1024 59.89 Hz (CVT 1.31M4) hsync: 63.67 kHz; pclk: 109.00 MHz
 Modeline "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
 
 $ xrandr --newmode "1280x1024_60.00"  109.00  1280 1368 1496 1712  1024 1027 1034 1063 -hsync +vsync
 
 $ xrandr --addmode VGA1 1280x1024_60.00
 xrandr: cannot find output "VGA1"


(Should "VGA1" at the last command instead be "Screen 0?"  Or something else?)


Thanks again,

rezs

---

