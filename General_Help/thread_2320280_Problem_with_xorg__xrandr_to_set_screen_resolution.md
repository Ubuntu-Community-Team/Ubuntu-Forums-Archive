---
title: "Problem with xorg / xrandr to set screen resolution"
date: 2016-04-12
forum: General Help
---

### Post by alias2 on 2016-04-12
Hello, i'm searching on the web, but canno't found how to specify my screen resolution to 1680x1050.

I read the doc [https://doc.ubuntu-fr.org/xrandr](https://doc.ubuntu-fr.org/xrandr)

```
xrandr
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1360x768      59.96*   59.80  
   1152x864      60.00  
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
DP-5 disconnected (normal left inverted right x axis y axis)
  1680x1050_60.00 (0x1f5) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz


```

and then make manipulations:
```

:/usr/share/X11/xorg.conf.d# xrandr --newmode "1680x1050_60.00"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
:/usr/share/X11/xorg.conf.d# xrandr --addmode DVI-I-0 1680x1050_60.00X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  45
  Current serial number in output stream:  46
```

Then, i found a solution here:
[http://askubuntu.com/questions/235507/xconfig-xrandr-badmatch/380817#380817](http://askubuntu.com/questions/235507/xconfig-xrandr-badmatch/380817#380817)

I don't have any /etc/X11/xorg.conf file, i found that they are some xorg.conf in /usr/share/X11/xorg.conf.d
I put a new file named 60-xorg.conf and set values to :
```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
        HorizSync    30-82
        VertRefresh  56-76
EndSection

```

But it's steel doesn't working... 
It feels really more complicated in the new ubuntu versions than before... If I can have some help i will be thanksfull...

```
cat /etc/issue
Ubuntu 15.10
```
 
the xorg.conf.new file generate from X -configure (but not used here):
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection

Section "Device"
    Identifier  "Card0"
    Driver      "nvidia"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

And i don't know why, crtl+alt+ f1-f6 doesn't work anymore... 
Thank you

---

### Post by deadflowr on 2016-04-12
Was addmode suppose to go to a disconnected connection:

```
:/usr/share/X11/xorg.conf.d# xrandr --addmode **DVI-I-0** 1680x1050_60.00X Error of failed request:  BadMatch (invalid parameter attributes)
```

```
**DVI-I-0** disconnected (normal left inverted right x axis y axis)
```

---

### Post by alias2 on 2016-04-20
Thank you, you're right, I've tried both (and path here bad code), that's was not the problem:

```
xrandr --newmode "1680x1050"  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync
xrandr --addmode DVI-I-1 1680x1050
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  140 (RANDR)
  Minor opcode of failed request:  18 (RRAddOutputMode)
  Serial number of failed request:  45
  Current serial number in output stream:  46

```

But i just realize, that all mode that i tried to create to DVI are set to DP-5:

```
xrandr
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 connected 1360x768+0+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00 +
   1360x768      59.96*   59.80  
   1152x864      60.00  
   800x600       72.19    60.32    56.25  
   680x384       59.96    59.80  
   640x480       59.94  
   512x384       60.00  
   400x300       72.19  
   320x240       60.05  
HDMI-0 disconnected (normal left inverted right x axis y axis)
DP-0 disconnected (normal left inverted right x axis y axis)
DP-1 disconnected (normal left inverted right x axis y axis)
DP-2 disconnected (normal left inverted right x axis y axis)
DP-3 disconnected (normal left inverted right x axis y axis)
DP-4 disconnected (normal left inverted right x axis y axis)
**DP-5 **disconnected (normal left inverted right x axis y axis)
  1680x1050_60.00 (0x1fb) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  plouf (0x210) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1680x1050 (0x216) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz
  1680x1050_plouf (0x220) 146.250MHz
        h: width  1680 start 1784 end 1960 total 2240 skew    0 clock  65.29KHz
        v: height 1050 start 1053 end 1059 total 1089           clock  59.95Hz


```

---

### Post by alias2 on 2016-05-22
Hello, still have the problem, i reinstall last version of ubuntu but got the same problem...

---

