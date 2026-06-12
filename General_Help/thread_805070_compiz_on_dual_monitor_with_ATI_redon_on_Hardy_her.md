---
title: "compiz on dual monitor with ATI redon on Hardy heron"
date: 2008-05-23
forum: General Help
---

### Post by m_kk on 2008-05-23
Hi,

I got problem with compiz and dual monitor. I have tried all the tricks on internet but could get successful. It worked when I edited the xorg.conf file to enable AIGLX and Composite but when i restart the x server I get two different monitors instead of one big monitor over 2 screens. 

Otherwise when I type compiz on terminal this is the error I get

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 1002:5b62 (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: present. 
Comparing resolution (2560x1024) to maximum 3D texture size (2048 ): Failed.
aborting and using fallback: /usr/bin/metacity 

Is there any way I could get one big monitor and Compiz working at same time? Below is my xorg.conf file.

Section "ServerLayout"

Identifier     "Default Layout"

Screen      0  "aticonfig-Screen[0]" 0 0

InputDevice    "Generic Keyboard"

InputDevice    "Configured Mouse"

InputDevice    "stylus" "SendCoreEvents"

InputDevice    "cursor" "SendCoreEvents"

InputDevice    "eraser" "SendCoreEvents"

EndSection



Section "Files"



# path to defoma fonts

FontPath     "/usr/share/fonts/X11/misc"

FontPath     "/usr/share/fonts/X11/cyrillic"

FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"

FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"

FontPath     "/usr/share/fonts/X11/Type1"

FontPath     "/usr/share/fonts/X11/100dpi"

FontPath     "/usr/share/fonts/X11/75dpi"

FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"

EndSection



Section "Module"

Load  "i2c"

Load  "bitmap"

Load  "ddc"

Load  "dri"

Load  "extmod"

Load  "freetype"

Load  "glx"

Load  "int10"

Load  "vbe"

EndSection



Section "ServerFlags"

Option     "AIGLX" "on"

EndSection



Section "InputDevice"

Identifier  "Generic Keyboard"

Driver      "kbd"

Option     "CoreKeyboard"

Option     "XkbRules" "xorg"

Option     "XkbModel" "pc105"

Option     "XkbLayout" "us"

EndSection



Section "InputDevice"

Identifier  "Configured Mouse"

Driver      "mouse"

Option     "CorePointer"

Option     "Device" "/dev/input/mice"

Option     "Protocol" "ImPS/2"

Option     "ZAxisMapping" "4 5"

Option     "Emulate3Buttons" "true"

EndSection



Section "InputDevice"

Identifier  "stylus"

Driver      "wacom"

Option     "Device" "/dev/input/wacom"

Option     "Type" "stylus"

Option     "ForceDevice" "ISDV4"  # Tablet PC ONLY

EndSection



Section "InputDevice"

Identifier  "eraser"

Driver      "wacom"

Option     "Device" "/dev/input/wacom"

Option     "Type" "eraser"

Option     "ForceDevice" "ISDV4"  # Tablet PC ONLY

EndSection



Section "InputDevice"

Identifier  "cursor"

Driver      "wacom"

Option     "Device" "/dev/input/wacom"

Option     "Type" "cursor"

Option     "ForceDevice" "ISDV4"  # Tablet PC ONLY

EndSection



Section "Monitor"

Identifier   "Generic Monitor"

HorizSync    28.0 - 57.0

VertRefresh  43.0 - 60.0

Option     "DPMS"

EndSection



Section "Monitor"

Identifier   "aticonfig-Monitor[0]"

Option     "VendorName" "ATI Proprietary Driver"

Option     "ModelName" "Generic Autodetecting Monitor"

Option     "DPMS" "true"

EndSection



Section "Monitor"

Identifier   "aticonfig-Monitor[1]"

Option     "VendorName" "ATI Proprietary Driver"

Option     "ModelName" "Generic Autodetecting Monitor"

Option     "DPMS" "true"

EndSection



Section "Device"

Identifier  "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"

Driver      "ati"

Option     "MonitorLayout" "LCD, CRT"

Option     "CRT2Position" "RightOf"

Option     "MetaModes" "1024x768-1024x768"

# Option     "MergedXinerama" "on"

Option     "MergedNonRectangular" "true"

Option     "MergedFB" "true"

BusID       "PCI:1:0:0"

Option "RenderAccel" "true"

EndSection



Section "Device"

Identifier  "aticonfig-Device[0]"

Driver      "fglrx"

Option     "DesktopSetup" "horizontal"

Option     "OverlayOnCRTC2" "1"

Option     "VideoOverlay" "on"

Option     "OpenGLOverlay" "off"

BusID       "PCI:1:0:0"

Option "AddARGBGLXVisuals" "True"

Option "RenderAccel" "true"

EndSection



Section "Device"

Identifier  "aticonfig-Device[1]"

Driver      "fglrx"

BusID       "PCI:1:0:0"

Screen      1

Option "AddARGBGLXVisuals" "True"

Option "RenderAccel" "true"

EndSection



Section "Screen"

Identifier "Default Screen"

Device     "ATI Technologies Inc RV380 [Radeon X600 (PCIE)]"

Monitor    "Generic Monitor"

DefaultDepth     24

SubSection "Display"

 Depth     1

 Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection

SubSection "Display"

 Depth     4

 Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection

SubSection "Display"

 Depth     8

 Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection

SubSection "Display"

 Depth     15

 Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection

SubSection "Display"

 Depth     16

 Modes    "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection

SubSection "Display"

 Depth     24

 Modes    "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"

EndSubSection

EndSection



Section "Screen"

Identifier "aticonfig-Screen[0]"

Device     "aticonfig-Device[0]"

Monitor    "aticonfig-Monitor[0]"

DefaultDepth     24

SubSection "Display"

 Viewport   0 0

 Depth     24

 Modes    "1280x1024" "1024x768"

EndSubSection

EndSection



Section "Screen"

Identifier "aticonfig-Screen[1]"

Device     "aticonfig-Device[1]"

Monitor    "aticonfig-Monitor[1]"

DefaultDepth     24

SubSection "Display"

 Viewport   0 0

 Depth     24

EndSubSection

EndSection



Section "DRI"

Mode         0666

EndSection



Section "Extensions"

Option     "Composite"
 "Enable"


EndSection

---

### Post by m_kk on 2008-05-23
I used Compiz-Check and this is the explanation. 

[LEFT]Your resolution is 2560x1024 but the maximum 3D texture size that your
graphics card is capable of is 2048x2048. Thus Compiz won't be able to run
 on this setup. You have to decrease the resolution first (in case you are
 using a dual-head setup, try disabling one monitor and run the script again).
[/LEFT]

Where do I have to edit the conf file to get a total resolution of 2048X1024?

---

### Post by m_kk on 2008-05-23
never mind got it fixed

---

### Post by The Recorder on 2008-06-01
Can you please tell me how you fixed this.  I don't know what to do to get 2048x768 as a choice in "Screen Resolutions".

Thanks,

Art

---

### Post by The Recorder on 2008-06-01
I figured it out...  Thanks, anyway...

sudo aticonfig --add-pairmode=1024x768+1024x768

---

