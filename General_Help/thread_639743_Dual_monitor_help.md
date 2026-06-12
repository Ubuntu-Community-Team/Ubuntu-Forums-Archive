---
title: "Dual monitor help"
date: 2007-12-13
forum: General Help
---

### Post by shavvo on 2007-12-13
I just set up dual monitors. The second monitor works however it does not use the correct resolution. No matter what i do it will not take and just stays at 640x480. 

What im using:

2nd video card is: ATI Rage 128 Pro Ultra TR

2nd monitor type is: V7

I think I need a different driver for the video card but for the life of me I cant find which one to use. Here is a copy of my xorg.conf


Section "ServerLayout"
        Identifier     "X.org Configured"
        Screen      0  "Screen0" 0 0
        Screen      1  "Screen1" RightOf "Screen0"
        InputDevice    "Mouse0" "CorePointer"
        InputDevice    "Keyboard0" "CoreKeyboard"
        Option         "Xinerama" "true"
EndSection

Section "Files"
        RgbPath      "/etc/X11/rgb"
        ModulePath   "/usr/lib/xorg/modules"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/usr/X11R6/lib/X11/fonts/misc"
        FontPath     "/usr/share/fonts/X11/cyrillic"
        FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath     "/usr/share/fonts/X11/Type1"
        FontPath     "/usr/X11R6/lib/X11/fonts/Type1"
        FontPath     "/usr/share/fonts/X11/100dpi"
        FontPath     "/usr/share/fonts/X11/75dpi"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "GLcore"
        Load  "glx"
        Load  "record"
        Load  "xtrap"
        Load  "dbe"
        Load  "extmod"
        Load  "dri"
        Load  "type1"
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
        #DisplaySize      340   270     # mm
        Identifier   "Monitor0"
        VendorName   "DEL"
        ModelName    "DELL E196FP"
 ### Comment all HorizSync and VertRefresh values to use DDC:
        HorizSync    31.0 - 80.0
        VertRefresh  56.0 - 75.0
Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "Monitor1"
        VendorName   "Monitor Vendor"
        ModelName    "Monitor Model"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "ColorKey"                  # <i>
        #Option     "CacheLines"                # <i>
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "DRI"                       # [<bool>]
        #Option     "NoDDC"                     # [<bool>]
        #Option     "ShowCache"                 # [<bool>]
        #Option     "XvMCSurfaces"              # <i>
        #Option     "PageFlip"                  # [<bool>]
        Identifier  "Card0"
        Driver      "i810"
        VendorName  "Intel Corporation"
        BoardName   "82945G/GZ Integrated Graphics Controller"
        BusID       "PCI:0:2:0"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"                   # [<bool>]
        #Option     "SWcursor"                  # [<bool>]
        #Option     "Dac6Bit"                   # [<bool>]
        #Option     "Dac8Bit"                   # [<bool>]
        #Option     "DMAForXv"                  # [<bool>]
        #Option     "ForcePCIMode"              # [<bool>]
        #Option     "CCEPIOMode"                # [<bool>]
        #Option     "CCENoSecurity"             # [<bool>]
        #Option     "CCEusecTimeout"            # <i>
        #Option     "AGPMode"                   # <i>
        #Option     "AGPSize"                   # <i>
        #Option     "RingSize"                  # <i>
        #Option     "BufferSize"                # <i>
        #Option     "EnablePageFlip"            # [<bool>]
        #Option     "Display"                   # <str>
        #Option     "PanelWidth"                # <i>
        #Option     "PanelHeight"               # <i>
        #Option     "ProgramFPRegs"             # [<bool>]
        #Option     "UseFBDev"                  # [<bool>]
        #Option     "VideoKey"                  # <i>

  #Option     "ShowCache"                 # [<bool>]
        #Option     "VGAAccess"                 # [<bool>]
        Identifier  "Card1"
        Driver      "ati"
        VendorName  "ATI Technologies Inc"
        BoardName   "Rage 128 Pro Ultra TR"
        BusID       "PCI:4:0:0"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Card0"
        Monitor    "Monitor0"
        DefaultDepth 24
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes           "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "Screen1"
        Device     "Card1"
        Monitor    "Monitor1"
        DefaultDepth 24
        SubSection "Display"
                Viewport   0 0
                Depth     16
                Modes          "1280x1024"
        EndSubSection
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes          "1280x1024"
        EndSubSection
EndSection


Any help would be greatly appreciated

TY
-Shavvo

---

### Post by public_void on 2007-12-26
I've had the same problem, try setting the HorizSync and VertRefresh in the second Monitor section

---

