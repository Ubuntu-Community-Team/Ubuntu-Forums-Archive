---
title: "Unable to boot on Monitor - Cannot display this video mode -"
date: 2014-02-09
forum: General Help
---

### Post by damien4 on 2014-02-09
Hello,
I just installed Ubuntu 12.04 LTS 32 bits version on an HP Slimline S3348.
Video  card is a Sapphire HD5450 512 MB. I installed it using an old LG  monitor and everything worked fine. My aim is to link this desktop to my  TV (Philips32PF7422) via the Dual Link DVI.

When I boot with the TV plugged to the desktop, the startup process comes to a stop (after I see  the Ubuntu logo) and the TV shows : "Cannot display this video mode".

The  strange thing is that if I boot with my old monitor, Ubuntu starts normally  and when I unplug the old monitor and plug my TV the display works fine.

After  some research, I run Compiz and unticked the "Detect Refresh Rate", set  the refresh rate to 60Hz, unticked "Detect Output".
I tried booting on the TV an it didn't work.

 I then modified the /etc/X11/xorg.conf as follow:
> Section "Screen"
    Identifier "Screen0"
    Device "CRT1"
    Monitor "Monitor0"
    DefaultDepth 24
    
EndSection

Section "Monitor"
 Identifier "Monitor0"
Modeline "1024x768_60.00"  64.11  1024 1080 1184 1344  768 769 772 795  -HSync +Vsync
EndSection

Section "Module"
    Load    "glx"
EndSection


The result of running xrandr when the TV is plugged is:

> Screen 0: minimum 320 x 200, current 1024 x 768, maximum 1600 x 1600
DFP1 disconnected (normal left inverted right x axis y axis)
DFP2 disconnected (normal left inverted right x axis y axis)
CRT1 connected 1024x768+0+0 (normal left inverted right x axis y axis) 406mm x 229mm
   1600x1200      60.0 +
   1400x1050      60.0  
   1600x900       60.0  
   1360x1024      60.0  
   1280x1024      60.0  
   1440x900       59.9  
   1280x960       60.0  
   1366x768       59.8  
   1360x768       60.0  
   1280x800       59.8  
   1152x864       60.0  
   1280x768       59.9  
   1280x720       60.0  
   1024x768       60.0* 
   800x600        60.3  
   720x480        60.0  
   640x480        59.9  
CRT2 disconnected (normal left inverted right x axis y axis)


I checked on the forums and I really don't know what to try next.
Does anyone have an idea?
Thanks in advance for your help!

---

