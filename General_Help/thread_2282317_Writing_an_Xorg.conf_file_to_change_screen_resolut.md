---
title: "Writing an Xorg.conf file to change screen resolution"
date: 2015-06-13
forum: General Help
---

### Post by patrickjamesmorton on 2015-06-13
Hi guys, this is my first time posting so go easy on me!

My issue is that I cannot get my laptop monitor adopt any resolution other than 1280x1024, which I wish to change to 1920x1080. I have tried using xrandr to force the screen resolution to its native one by running cvt 1920 1080 60 and then using the xrandr --newmode, xrandr --addmode commands but these have been unsuccessful as I just get the "xrandr failed to get size of gamma output" error message for which there doesn't appear to be a direct solution.

I think that my best bet for resolving this issue is write an xorg.conf file. I have had a couple of goes of doing this by using templates I have taken from the internet and changing some of the values, but to no avail. I have also tried using the manpage unsuccessfully as it's a little out of my depth. So far each time I created a file using the command

sudo nano /etc/X11/xorg.conf

and then rebooted there has been no noticeable change.

It there anyone who could give me a concise guide on how to write a basic xorg.conf file for the purpose I require? Or who could direct me to a simple guide on how to do this?

Here is the output of xvidtune:

Vendor: (null), Model: (null)
Num hsync: 1, Num vsync: 1
hsync range 0:  28.00 -  72.00
vsync range 0:  43.00 -  60.00

the output of cvt 1920 1080 60:

1920x1080 59.96 Hz (CVT 2.07M9) hsync: 67.16 kHz; pclk: 173.00 MHz
Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync

the output from ddcprobe:

vbe: VESA 3.0 detected.
oem: Intel(R)Sandybridge Mobile Graphics Chipset Accelerated VGA BIOS
vendor: Intel Corporation
product: Intel(R)Sandybridge Mobile Graphics Controller Hardware Version 0.0
memory: 65472kb
mode: 1280x1024x256
mode: 1280x1024x64k
mode: 1280x1024x16m
mode: 1024x768x256
mode: 1024x768x64k
mode: 1024x768x16m
mode: 640x480x16m
mode: 800x600x64k
mode: 800x600x16m
mode: 640x480x256
mode: 800x600x256
mode: 640x480x64k
edid: 
edid: 1 3
id: 314c
eisa: SEC314c
serial: 00000000
manufacture: 0 2011
input: analog signal.
screensize: 34 19
gamma: 2.200000
dpms: RGB, active off, suspend, standby
dtiming: 1920x1080@59
monitorid: SAMSUNG
monitorid: 156HT01-201

---

### Post by patrickjamesmorton on 2015-06-13
Oh yes and here is the output when I generate an xorg.conf file using

sudo Xorg -configure:

```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
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
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection


Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "AccelMethod"               # <str>
        #Option     "Backlight"                 # <str>
        #Option     "DRI"                       # <str>
        #Option     "ColorKey"                  # <i>
        #Option     "VideoKey"                  # <i>
        #Option     "Tiling"                    # [<bool>]
        #Option     "LinearFramebuffer"         # [<bool>]
        #Option     "VSync"                     # [<bool>]
        #Option     "PageFlip"                  # [<bool>]
        #Option     "SwapbuffersWait"           # [<bool>]
        #Option     "TripleBuffer"              # [<bool>]
        #Option     "XvPreferOverlay"           # [<bool>]
        #Option     "HotPlug"                   # [<bool>]
        #Option     "ReprobeOutputs"            # [<bool>]
        #Option     "XvMC"                      # [<bool>]
        #Option     "ZaphodHeads"               # <str>
        #Option     "VirtualHeads"              # <i>
        #Option     "TearFree"                  # [<bool>]
        #Option     "PerCrtcPixmaps"            # [<bool>]
        #Option     "FallbackDebug"             # [<bool>]
 #Option     "DebugFlushBatches"         # [<bool>]
        #Option     "DebugFlushCaches"          # [<bool>]
        #Option     "DebugWait"                 # [<bool>]
        #Option     "BufferCache"               # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "kmsdev"                    # <str>
        #Option     "ShadowFB"                  # [<bool>]
        Identifier  "Card1"
        Driver      "modesetting"
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

Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
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



My question is, how can I succesfully edit this to get a 1920x1080 resolution using the information I have found in my original post?

---

### Post by patrickjamesmorton on 2015-06-13
Ok so I've been doing some more fiddling. I have used the information found at [http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html](http://manpages.ubuntu.com/manpages/lucid/man5/xorg.conf.5.html) to configure my own xorg.conf file. And yet still, when I reboot my computer it displays in the same awful screen resolution and everything is the same.

Could someone have a go at attempting to explain to me why this file doesn't work?

```
Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
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
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "SAMSUNG"
        ModelName    "156HT01-201"
        HorizSync       28.00 - 72.00
        VertRefresh     43.00 - 60.00
        Option       "DPMS"
        Modeline "1920x1080_60.00" 173.00 1920 2048 2248 2576 1080 1083 1088 $
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "AccelMethod"               # <str>
        #Option     "Backlight"                 # <str>
        #Option     "DRI"                       # <str>
        #Option     "ColorKey"                  # <i>
        #Option     "VideoKey"                  # <i>
        #Option     "Tiling"                    # [<bool>]
        #Option     "LinearFramebuffer"         # [<bool>]
        #Option     "VSync"                     # [<bool>]
        #Option     "PageFlip"                  # [<bool>]
        #Option     "SwapbuffersWait"           # [<bool>]
        #Option     "TripleBuffer"              # [<bool>]
        #Option     "XvPreferOverlay"           # [<bool>]
        #Option     "HotPlug"                   # [<bool>]
        #Option     "ReprobeOutputs"            # [<bool>]
        #Option     "XvMC"                      # [<bool>]
        #Option     "ZaphodHeads"               # <str>
        #Option     "VirtualHeads"              # <i>
        #Option     "TearFree"                  # [<bool>]
        #Option     "PerCrtcPixmaps"            # [<bool>]
        #Option     "FallbackDebug"             # [<bool>]
        #Option     "DebugFlushBatches"         # [<bool>]
        #Option     "DebugFlushCaches"          # [<bool>]
        #Option     "DebugWait"                 # [<bool>]
        #Option     "BufferCache"               # [<bool>]
        Identifier  "Card0"
        Driver      "intel"
        BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"                  # [<bool>]
        #Option     "kmsdev"                    # <str>
        #Option     "ShadowFB"                  # [<bool>]
        Identifier  "Card1"
        Driver      "modesetting"
        BusID       "PCI:1:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
       SubSection "Display"
                Viewport   0 0
                Depth     1
                Modes   "1920x1080@60.00"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     4
                Modes   "1920x1080@60.00"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     8
                Modes   "1920x1080@60.00"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     15
                Modes   "1920x1080@60.00"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes   "1920x1080@60.00"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes   "1920x1080@60.00"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
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

As you can see I have added the modeline for "1920x1080_60.00" to the display section and the relevant modes to the screen section. I've also added values for HorizSync and VertRefresh, as well as the vendor and model names.

Seems like it should do something, right?

---

### Post by cariboo on 2015-06-13
It may help if you let us know what graphics adapter you are using.

---

### Post by QDR06VV9 on 2015-06-13
> **cariboo said:**
> It may help if you let us know what graphics adapter you are using.
+1
You can install inxi to get the info.
```
sudo apt-get install inxi
```
Then paste back the output of 
```
inxi -G
```
This is the return for mine
```
me@me-Aspire-M3300:~$ inxi -G
Graphics:  Card: NVIDIA GF119 [GeForce GT 520]
           Display Server: X.Org 1.17.1 drivers: nvidia (unloaded: fbdev,vesa,nouveau)
           Resolution: 1920x1080@60.0hz
           GLX Renderer: GeForce GT 520/PCIe/SSE2
           GLX Version: 4.5.0 NVIDIA 352.09
```
Hope that Helps

---

