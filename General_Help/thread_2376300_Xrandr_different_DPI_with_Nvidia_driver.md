---
title: "Xrandr different DPI with Nvidia driver"
date: 2017-11-01
forum: General Help
---

### Post by alsto on 2017-11-01
Hello everyone,

I have spend most of today trying to finally get my external screen (Asus ZenScreen) set up with my laptop (Dell XPS-15 running Ubuntu 16.04). It is running a Nvidia GeForce GTX 960M/PCIe/SSE2 just in case that is relevant. The obvious problem being that the second screen is full HD while the laptop has a 4k screen.

After a lot of googeling I managed to get it to work while using the Nouveau open source driver. However the performance was not the greatest and the flickering pointer drove me nuts within minutes. So now I am trying to achieve the same result using Nvidias proprietary driver (v384.90).

First of all, here is xrandr --current after booting:

```
Screen 0: minimum 8 x 8, current 5760 x 2160, maximum 16384 x 16384
eDP-1-1 connected primary 3840x2160+0+0 (normal left inverted right x axis y axis) 346mm x 194mm
   3840x2160     60.00*+
   2048x1536     60.00  
   1920x1440     60.00  
   1856x1392     60.01  
   1792x1344     60.01  
   1920x1200     59.95  
   1920x1080     59.93  
   1600x1200     60.00  
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
DP-1-1 connected 1920x1080+3840+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1920x1080     60.00*+  59.94  
   1680x1050     59.95  
   1280x1024     60.02  
   1440x900      59.89  
   1280x960      60.00  
   1280x720      60.00    59.94  
   1024x768      60.00  
   800x600       60.32  
   640x480       60.00    59.94  
   720x400       70.08  
HDMI-1-1 disconnected (normal left inverted right x axis y axis)
DP-1-2 disconnected (normal left inverted right x axis y axis)
HDMI-1-2 disconnected (normal left inverted right x axis y axis)
```

The following worked using the open source driver:

```
xrandr --verbose --output eDP-1-1 --scale 1x1 --fb 7680x2160 --pos 0x0 --output DP-1-1 --scale 2x2 --mode 1920x1080 --pos 3840x0 --fb 7680x2160 --panning 3840x2160+3840+0
```

Traing to apply the same with the Nvidia driver only gets me the follwing error:

```
crtc 0:    3840x2160  60.00 +0+0 "eDP-1-1"
crtc 1:    1920x1080  60.00 +3840+0 "DP-1-1"
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  29 (RRSetPanning)
  Serial number of failed request:  40
  Current serial number in output stream:  40
```

The few threads I found recommended setting up a xorg.conf file and messing around with that. So I started by creating a new one using:

```
sudo nvidia-xconfig
```

This messed everything up, after the restart my main display had its resolution limited to 640x480. So I fell back to the backup version in the same folder.

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

So now where do I go from here? I don't think changing random values will get me very far.

I appreaciate any help.

---

