---
title: "Ubuntu 20.04 upgrade Laptop Latitude E5500 External Monitor Issue"
date: 2020-05-23
forum: General Help
---

### Post by lidanny on 2020-05-23
I had 17.04 on my Dell Latitude E5500 and all was well but it was out of support. So I upgraded in stages and when I got to 18 I noticed that I lost my display after the reboot. My external monitor and laptop display would come to life and then the external would loose the input signal. On the laptop the screen was dark with some mouse flicker. So I unplugged the external VGA cable and the laptop display came back. After a few more reboots the external display still would not work. If I plug it in the laptop display goes out and the display keeps trying to start up and then looses signal. I then upgraded to 19 with the same issue still present. I then went to 20.04 and all is well but the display issue remains.

This is just a plain old laptop. No gaming or high end graphics needed on this machine. Just email and web.

I ran a couple of commands from other video display issue posts and here is the output. I would appreciate any advice.

Mobile Intel® GM45 Express Chipset (CTG)
Screen 0: minimum 320 x 200, current 1280 x 800, maximum 8192 x 8192
LVDS-1 connected primary 1280x800+0+0 (normal left inverted right x axis y axis) 330mm x 210mm
   1280x800      59.98 +  59.97    59.81    59.91    40.00* 
   1280x720      60.00    59.99    59.86    59.74  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   1024x576      59.95    59.96    59.90    59.82  
   960x600       59.93    60.00  
   960x540       59.96    59.99    59.63    59.82  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   864x486       59.92    59.57  
   800x512       60.17  
   700x525       59.98  
   800x450       59.95    59.82  
   640x512       60.02  
   720x450       59.89  
   700x450       59.96    59.88  
   640x480       60.00    59.94  
   720x405       59.51    58.99  
   684x384       59.88    59.85  
   680x384       59.80    59.96  
   640x400       59.88    59.98  
   576x432       60.06  
   640x360       59.86    59.83    59.84    59.32  
   512x384       60.00  
   512x288       60.00    59.92  
   480x270       59.63    59.82  
   400x300       60.32    56.34  
   432x243       59.92    59.57  
   320x240       60.05  
   360x202       59.51    59.13  
   320x180       59.84    59.32  
VGA-1 disconnected (normal left inverted right x axis y axis)
HDMI-1 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
HDMI-2 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
SVIDEO-1 disconnected (normal left inverted right x axis y axis)

lspci -k | grep -A 2 -i "vga"
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
    Subsystem: Dell Mobile 4 Series Chipset Integrated Graphics Controller
    Kernel driver in use: i915

---

