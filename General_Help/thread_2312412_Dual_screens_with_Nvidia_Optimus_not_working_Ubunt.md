---
title: "Dual screens with Nvidia Optimus not working Ubuntu 15.10"
date: 2016-02-04
forum: General Help
---

### Post by Joaqun_Jos_Con on 2016-02-04
Hello there!
 
New ubuntu user, coming right from windows and the boredom of its BSODS. But I'm having issues trying to set up my MSI GS70 2OD dual screen with its Nvidia 765M optimus card. 

Whenever I connect the second monitor, it works properly only on mirrored mode (both screens have the same). Whenever I try to use expanded desktop it all goes to crap.

xrandr gives me the proper sizes and resolutions (which are 1080p on both screens) but the screen shows like zoomed in, as if I'd have the whole 2x1920 wide desktop on the external screen and just a tiny bit on the internal one. In fact if I set up the external monitor on the left in the system's monitor preferences when I move over the mouse to the right the "zoom" moves with it until it reaches the end and then moves to the other screen but everything is messed up and even the buttons are not clickable where they appear, I have to figure out where it actually is. Arandr gives me the same behaviour.

I've tried everything, I know it works with the nouveau driver but apparently it has a bug and crashes making the screen freeze which gives me more problems then. So I know it is something related with the Nvidia driver but can't figure out what or why.

The nvidia X settings doesn't detect the integrated monitor on it, because apparently it is hardwired to the intel card so I tried with the modesetting driver as I've read around with no success.

Also tried to install bumblebee on my current configuration but then the desktop manager won't start at all.

Which is more strange than anything is that it worked at some point but without me trying anything. For example when i was toying with arandr it worked once. The xorg didn't change and xrandr either but it got back to wrong state upon a reboot. Also yesterday I tried swapping the HDMI cable, just in case, and as soon as I connected it, it started working but got screwed upon reboot again.
 
I really, really need help because I don't want to be dragged back to windows.

Any ideas?


Here's the xrandr -q output when I have the issue:

```
j$ xrandr -qScreen 0: minimum 8 x 8, current 3840 x 1080, maximum 16384 x 16384
HDMI-0 connected primary 1920x1080+1920+0 (normal left inverted right x axis y axis) 509mm x 286mm
   1920x1080     60.00*+  59.94    50.00    60.00    50.04  
   1680x1050     59.95  
   1440x900      59.89  
   1280x1024     75.02    60.02  
   1280x960      60.00  
   1280x720      60.00    59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32    56.25  
   720x576       50.00  
   720x480       59.94  
   640x480       75.00    72.81    59.94    59.93  
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
eDP-1-0 connected 1920x1080+0+0 382mm x 215mm
   1920x1080     60.02*+  59.93  
   1680x1050     59.95    59.88  
   1600x1024     60.17  
   1400x1050     59.98  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1360x768      59.80    59.96  
   1152x864      60.00  
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
VGA-1-0 disconnected
  1680x1050 (0x47) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1280x1024 (0x4b) 108.000MHz
        h: width  1280 start 1328 end 1440 total 1688 skew    0 clock  63.98KHz
        v: height 1024 start 1025 end 1028 total 1066           clock  60.02Hz
  1440x900 (0x4c) 106.500MHz
        h: width  1440 start 1520 end 1672 total 1904 skew    0 clock  55.93KHz
        v: height  900 start  903 end  909 total  934           clock  59.89Hz
  1280x960 (0x4d) 108.000MHz
        h: width  1280 start 1376 end 1488 total 1800 skew    0 clock  60.00KHz
        v: height  960 start  961 end  964 total 1000           clock  60.00Hz
  1024x768 (0x52) 65.000MHz
        h: width  1024 start 1048 end 1184 total 1344 skew    0 clock  48.36KHz
        v: height  768 start  771 end  777 total  806           clock  60.00Hz
  800x600 (0x59) 40.000MHz
        h: width   800 start  840 end  968 total 1056 skew    0 clock  37.88KHz
        v: height  600 start  601 end  605 total  628           clock  60.32Hz
  800x600 (0x5a) 36.000MHz
        h: width   800 start  824 end  896 total 1024 skew    0 clock  35.16KHz
        v: height  600 start  601 end  603 total  625           clock  56.25Hz
  640x480 (0x62) 25.175MHz
        h: width   640 start  656 end  752 total  800 skew    0 clock  31.47KHz
        v: height  480 start  490 end  492 total  525           clock  59.94Hz
```

and my current xorg.conf which is the same Nvidia-settings tries to configure:

```
$ cat /etc/X11/xorg.confSection "ServerLayout"
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

---

### Post by Ronald_hume on 2016-02-05
you can try system setting> screen> and uncheck the mirror displays box and check the detect displays box at the bottom for the first tim then the detect box can also be unchecked. if this does not work you may need the linux drivers to be downloaded from nvidiaa for your board. good luck.

---

### Post by miltonh26 on 2016-02-13
Try this setup by Rajat Pandita which worked great from me on an Asus U44S. I'm still having occasional issues with the Intel card freezing momentarily when a second monitor is plugged in, after which it recovers, but on the it has been much better overall. 

[http://rajat-osgyan.blogspot.com/2015/10/how-to-install-bumblebee-and-latest.html](http://rajat-osgyan.blogspot.com/2015/10/how-to-install-bumblebee-and-latest.html)

---

