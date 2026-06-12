---
title: "second monitor not recognized : cropped and low resolution"
date: 2019-02-02
forum: General Help
---

### Post by intraline on 2019-02-02
Hello,

I'm posting my first post here, a bit desperate. Here what's happening :

I've just got an external 27" monitor that I want to use for IDE, because my laptop's one is very small.
Once plugged via mini-DP to DP, the monitor displays the desktop _largely cropped_, see attached picture : 

[ATTACH=CONFIG]282389[/ATTACH] 

Displays settings shows "Unknown Display", with these two resolutions available : _1024x768 (4:3) _and 800x600 (4:3).

[COLOR=#000080][FONT=courier new]xrandr[/FONT][/COLOR] shows :

```

LVDS1 connected primary 1366x768+0+768 (normal left inverted right x axis y axis) 280mm x 160mm
   1366x768      60.02*+
   1360x768      59.96  
   1280x720      59.86    60.00    59.74  
   1024x768      60.00  
   1024x576      60.00    59.90    59.82  
   960x540       60.00    59.63    59.82  
   800x600       60.32    56.25  
   864x486       60.00    59.92    59.57  
   640x480       59.94  
   720x405       59.51    60.00    58.99  
   680x384       60.00  
   640x360       59.84    59.32    60.00

DP1 connected 1024x768+184+0 (normal left inverted right x axis y axis) 0mm x 0mm
   1024x768      60.00* 
   800x600       60.32    56.25  
   848x480       60.00  
   640x480       59.94

```


I tried to force the resolution using ```
cvt 1920 1080
``` to get this modeline :
```

# 1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

```

Then :
```

xrandr --newmode "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
xrandr --addmode DP1 "1920x1080_60.00"

```

The new resolution is available through settings, if I change it via GUI, it's rolling back to 1024. If I force it with [COLOR=#000080][FONT=courier new]xrandr --output DP1 --mode 1920x1080_60.00[/FONT][/COLOR], it turns off. In both cases, following message appears in [COLOR=#000080][FONT=courier new]syslog[/FONT][/COLOR] :

```

gsd-color[3092]: unable to get EDID for xrandr-DP1: unable to get EDID for output
gsd-color[3092]: message repeated 8 times: [ unable to get EDID for xrandr-DP1: unable to get EDID for output]

```[FONT=arial]

I've no idea how to get the right EDID. I cannot find it online.[/FONT][FONT=Verdana][FONT=arial]
[/FONT]
[/FONT][COLOR=#000080][FONT=courier new]xrandr --props[/FONT][/COLOR] returns only EDID of the integrated monitor : [https://pastebin.com/nQ606aQh](https://pastebin.com/nQ606aQh)

[COLOR=#000080][FONT=courier new]sudo get-edid | parse-edid[/FONT][/COLOR] returns "[FONT=arial][COLOR=#333333]Bus 0 doesn't really have an EDID...[/COLOR]"[/FONT] :  [https://pastebin.com/MZHT8i5t](https://pastebin.com/MZHT8i5t)
[FONT=Verdana] [FONT=arial]
I tried to set a xorg.conf file, but I'm not sure if it is the right way to do, because I'm missing the EDID file, and setting the modeline seems the same as using xrandr in command line...

**By the way, the monitor works well on Windows, with the same computer.**
[/FONT]
[/FONT][HR][/HR][FONT=arial]
_Now here are the specifications :_

Monitor : [Acer XB270H]("https://www.displayspecifications.com/en/model/a90f98b") 
Laptops : [Lenovo Thinkpad x230 type 2325-78G]("http://psref.lenovo.com/syspool/Sys/PDF/withdrawnbook/ThinkPad_X230_WE.pdf")[/FONT][FONT=Verdana]

[/FONT]
```
Linux 4.18.0-13-generic #14-Ubuntu SMP x86_64 GNU/Linux
```

[COLOR=#000080][FONT=courier new]lspci -v | grep VGA[/FONT][/COLOR]

```
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09) (prog-if 00 [VGA controller])
```

[COLOR=#000080][FONT=courier new]inxi -Gxx[/FONT] :[/COLOR]
```

Graphics:  Device-1: Intel 3rd Gen Core processor Graphics driver: i915 v: kernel bus ID: 00:02.0 
           chip ID: 8086:0166 
           Display: x11 server: X.Org 1.20.1 driver: intel compositor: gnome-shell 
           resolution: 1366x768~60Hz, 1024x768~60Hz 
           OpenGL: renderer: Mesa DRI Intel Ivybridge Mobile v: 4.2 Mesa 18.2.2 compat-v: 3.0 
           direct render: Yes

```

[HR][/HR]
This monitor made me loose so much time trying various things from old posts, that I now feel lost, and don't know what to do next. I will appreciate any kind of support.

---

### Post by intraline on 2019-02-02
[B]UPDATE: 

[/B]I managed to get the EDID from the Windows computer, using moninfo.exe tool.

And I tried to follow some Xorg guides, so here is the xorg.conf file : 

```

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    Screen      1  "Screen1" RightOf "Screen0"
    #InputDevice    "Keyboard0" "CoreKeyboard"
    #InputDevice    "Mouse0" "CorePointer"
    #InputDevice    "Touchpad0" "SendCoreEvents"
EndSection


Section "Module"
	Load  "glx"
EndSection


Section "Monitor"
    Identifier  "MonitorLVDS1"
    VendorName  "Monitor Vendor"
    ModelName   "Monitor Model"
    Option      "DPMS"
EndSection


Section "Monitor"
    Identifier  "MonitorDP1"
    VendorName  "Acer"
    ModelName   "XB270H"    
    DisplaySize 598 336
    Option      "DPMS"
# "true"
#    Horizsync   30-160
#    VertRefresh 55-144
   #Modeline    "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
   #HorizSync   30.0 - 75.0
   #VertRefresh 60.0
   #Option    "TopOf"   "LVDS1"
   #Option   "DPMS"
EndSection


Section "Device"
    Identifier  "Device0"
    Option      "MonitorLVDS1"
    Option      "MonitorDP1"
#    Option      "DynamicTwinView" "false"
    Driver      "intel"
#   Option      "ConnectedMonitor" "LVDS1, DP1"
    Option      "CustomEDID" "DP1:/etc/X11/edid.bin"
    Option      "IgnoreEDID" "false"
    Option      "UseEDID" "true"
#    Option      "DPI"    "150x155"
EndSection


Section "Screen"
    Identifier "Screen0"
    Device     "Device0"
    Monitor    "MonitorLVDS1"
EndSection


Section "Screen"
    Identifier "Screen1"
    Device     "Device0"
    Monitor    "MonitorDP1"
#    DefaultDepth  24
#    Option        "metamodes" "1920x1080 +0+0"
#    SubSection "Display"
#      Depth 24
#      Modes "1920x1080_60.00"
#    EndSubSection
EndSection

```

Now, it seems to work fine, because I've the second monitor with a good resolution, and it is not anymore cropped, so fullscreen.

[B]BUT: moving any window, opening a second application get me back to the login screen
AND: monitor now does not work anymore on my Windows computer, WTF![/B]**?****!!**

---

