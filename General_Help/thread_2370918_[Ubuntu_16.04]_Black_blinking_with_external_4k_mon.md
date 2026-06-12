---
title: "[Ubuntu 16.04] Black blinking with external 4k monitor"
date: 2017-09-08
forum: General Help
---

### Post by paweluser0 on 2017-09-08
I bought a new 4k monitor Acer S277HK, and was hoping to work with  2560x1440 resolution at 60Hz, as the specification of my current laptop  says it should be possible. I will be changing my laptop to a new one,  in about a year - so I thought that the usage of 4k would happen then. 

  I have encountered a few problems with this monitor. The main one is  it flickering once every 30 seconds, or sometimes flickering briefly a  few times in a row. Even if I use it only 1920x1080 or 1680x1050 on  60Hz.

  **System:** I have just switched from Ubuntu 12.04 to  Ubuntu 16.04.3 LTS 64-bit, and it is a new installation with kernel  4.10.0-33-generic.
  [B]
Computer:[/B] Laptop: Asus X53SV, Graphics: Geforce GT  540M (I know it is old), Processor: Intel® Core™ i7-2670QM CPU @ 2.20GHz  × 8, Memory: 8GB. It has HDMI 1.3a port, and has no displayport.
[URL="https://www.geforce.com/hardware/notebook-gpus/geforce-gt-540m/features"]
[/URL]Specification of the graphic card says it allows for 2560x1400 at 60Hz (I have seen it somewhere). Not sure if it is over HDMI.
[B]
Connection:[/B] HDMI Cable: Reinston EK015 - on the box, it says it is compatible with even HDMI 2.0.
  [B]
Drivers:[/B] I am using Nvidia v 384.69 as it is compatible with GT 540M. I have also tried older ones, like v 375, 340, 304 and nouveau (everything with **Additional Drivers**), and the same result.
[B]
Resolution attempts:[/B] Ubuntu by default allows 3840x2160 at 24Hz or 1920x1080 at 60Hz. Bu using xrandr, I managed to set 2560x1440 at 43Hz, 45 did not work with result: xrandr: Configure crtc 0 failed. 
  [B]
Goal:[/B] I am hoping to get 1920x1080 at 60Hz, or 2560x1440 at 43Hz, but without black flickering. 
[B]
If "game over" happens:[/B] Maybe my graphics card is so  slow, that it won't be possible to set it - not sure if that is the  reason. Then, I will replace this monitor for some cheaper 25", with 2k.  For now, let's try to make it work.

xrandr:

```


Screen 0: minimum 8 x 8, current 1920 x 1080, maximum 16384 x 16384
LVDS-1-1 connected (normal left inverted right x axis y axis)
   1366x768      60.00 +
   1360x768      59.80    59.96  
   1024x768      60.04    60.00  
   960x720       60.00  
   928x696       60.05  
   896x672       60.01  
   960x600       60.00  
   960x540       59.99  
   800x600       60.00    60.32    56.25  
   840x525       60.01    59.88  
   800x512       60.17  
   700x525       59.98  
   640x512       60.02  
   720x450       59.89  
   640x480       60.00    59.94  
   680x384       59.80    59.96  
   576x432       60.06  
   512x384       60.00  
   400x300       60.32    56.34  
   320x240       60.05  
VGA-1-1 disconnected (normal left inverted right x axis y axis)
HDMI-1-1 connected primary 1920x1080+0+0 (normal left inverted right x axis y axis) 596mm x 335mm
   3840x2160     24.00  
   1920x1080     60.00    50.00    59.94*   24.00    23.98  
   1920x1080i    60.00    50.00    59.94  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.90  
   1280x960      60.00  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    70.07    60.00  
   832x624       74.55  
   800x600       72.19    75.00    60.32    56.25  
   720x576       50.00  
   720x576i      50.00  
   720x480       60.00    59.94  
   720x480i      60.00    59.94  
   640x480       75.00    72.81    66.67    60.00    59.94  
   720x400       70.08  
DP-1-1 disconnected (normal left inverted right x axis y axis)


```


/etc/X11/xorg.conf:

```


Section "ServerLayout"
    Identifier "layout"
    Screen 0 "nvidia"
    Inactive "intel"
EndSection

Section "Device"
    Identifier "intel"
    Driver "modesetting"
    BusID "PCI:0@0:2:0"
    Option "AccelMethod" "None"
EndSection

Section "Screen"
    Identifier "intel"
    Device "intel"
EndSection

Section "Device"
    Identifier "nvidia"
    Driver "nvidia"
    BusID "PCI:1@0:0:0"
    Option "ConstrainCursor" "off"
EndSection

Section "Screen"
    Identifier "nvidia"
    Device "nvidia"
    Option "AllowEmptyInitialConfiguration" "on"
    Option "IgnoreDisplayDevices" "CRT"
EndSection


```


dpkg --get-selections | grep nvidia:
```

nvidia-384                    install
nvidia-opencl-icd-384                install
nvidia-prime                    install
nvidia-settings                    install
```

lspci -vnn | grep VGA:

```
00:02.0 VGA compatible controller [0300]: Intel Corporation 2nd Generation Core Processor Family Integrated Graphics Controller [8086:0116] (rev 09) (prog-if 00 [VGA controller])
01:00.0 VGA compatible controller [0300]: NVIDIA Corporation GF108M [GeForce GT 540M] [10de:0df4] (rev a1) (prog-if 00 [VGA controller])


```

Any ideas? Thanks!

---

### Post by Bashing-om on 2017-09-08
paweluser0; Hello;

Maybe:
HiDPI (High Dots Per Inch) displays, ->
[https://wiki.archlinux.org/index.php/HiDPI](https://wiki.archlinux.org/index.php/HiDPI)

will give ya some pointers .

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by paweluser0 on 2017-09-08
Hi,

I didn't find a solution there. It is shown on this page, how to manage monitor setting, i.e. scale monitor etc, as far as I understand which is useful in 4k. 

At this moment, my main goal is to disable blinking. When I go to 1920x1080 at 24Hz, there is no blinking, and when I go 50Hz, or 60Hz (ntsc), it blinks.

I will be reinstalling my ubuntu once again to see if it helps, and  looking for a HiDPI friendly distributions/versions of ubuntu - I am  opened for new things. You meant Archlinux?

---

### Post by paweluser0 on 2017-09-09
I have got into the point that I was willing to change my graphic card. But as far as understand Asus X53SV is soldered into my laptop's motherboard. It is left to return the monitor back, and get something cheaper like Dell U2515H, changing the old one, not feeling I wasted the money, and hope that lower resolution will be fine there.

---

