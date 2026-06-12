---
title: "xorg.conf question: How to choose which dvi port goes with which monitor"
date: 2007-01-21
forum: General Help
---

### Post by Sureshot324 on 2007-01-21
I was playing with getting dual monitors working but for now I am going back to just one monitor, a viewsonic 20 inch widescreen.  My video card has dual dvi.  I set up my xorg.conf file for just one monitor, but when I start X server, it sends the video signal to the wrong DVI port.  My monitor is blank because the signal is going to the empty DVI port.  I can of course fix this by physically switching the cable to the other DVI port, but I should not have to do this.

Is there any way in the xorg.conf to tell it which dvi port to use for the monitor?  For example in the Monitor section for the viewsonic, specify an option that tells it to use DVI port 0.  Is there any way to make it autodetect this?  Windows XP autodetects it no problem.

When I was trying to set up dual monitors (20" and 17"), it would get the DVI ports backwards as well, which meant the 20" could only go to a max of 1280x1024, since it thought the 17" was on that port.

---

### Post by tomBorgia on 2007-01-22
Sorry for dumping a config file here, but its late and I think it'll help -

> # Xorg configuration created by system-config-display

Section "ServerLayout"
    Identifier     "Multihead layout"
    Screen      0  "Screen0" LeftOf "Screen1"
    Screen      1  "Screen1" 0 0
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
    Option         "Xinerama" "on"
    Option         "Clone" "off"
EndSection

#Section "Files"

# RgbPath is the location of the RGB database.  Note, this is the name of the 
# file minus the extension (like ".txt" or ".db").  There is normally
# no need to change the default.
# Multiple FontPath entries are allowed (they are concatenated together)
# By default, Red Hat 6.0 and later now use a font server independent of
# the X server to render fonts.
#    RgbPath         "/usr/X11R6/lib/X11/rgb"
#    FontPath        "unix/:7100"
#EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "fbdevhw"
    Load           "glx"
    Load           "record"
    Load           "freetype"
    Load           "type1"
EndSection

Section "InputDevice"

# Specify which keyboard LEDs can be user-controlled (eg, with xset(1))
#       Option  "Xleds"         "1 2 3"
# To disable the XKEYBOARD extension, uncomment XkbDisable.
#       Option  "XkbDisable"
# To customise the XKB settings to suit your keyboard, modify the
# lines below (which are the defaults).  For example, for a non-U.S.
# keyboard, you will probably want to use:
#       Option  "XkbModel"      "pc102"
# If you have a US Microsoft Natural keyboard, you can use:
#       Option  "XkbModel"      "microsoft"
#
# Then to change the language, change the Layout setting.
# For example, a german layout can be obtained with:
#       Option  "XkbLayout"     "de"
# or:
#       Option  "XkbLayout"     "de"
#       Option  "XkbVariant"    "nodeadkeys"
#
# If you'd like to switch the positions of your capslock and
# control keys, use:
#       Option  "XkbOptions"    "ctrl:swapcaps"
# Or if you just want both to be control, use:
#       Option  "XkbOptions"    "ctrl:nocaps"
#
    Identifier     "Keyboard0"
    Driver         "kbd"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "IMPS/2"
    Option         "Device" "/dev/input/mice"
    Option         "Buttons" "10"
    Option         "ZAxisMapping" "4 5"
#    Option         "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Monitor Vendor"
    ModelName      "ViewSonic E92f+"
    DisplaySize     360    270
    HorizSync       30.0 - 97.0
    VertRefresh     50.0 - 180.0
    Option         "dpms"
EndSection

Section "Monitor"
    Identifier     "Monitor1"
    VendorName     "Monitor Vendor"
    ModelName      "Samsung SyncMaster 750s(T)"
    HorizSync       30.0 - 70.0
    VertRefresh     50.0 - 160.0
    Option         "dpms"
EndSection

Section "Monitor"
Identifier "Multiscan400ps"
Option "DPMS"
HorizSync 30-94
VertRefresh 48-160
# Modeline "1152x864@60" 83.91 1280 1312 1624 1656 800 816 824 841
Modeline "1280x1024@85" 159.36 1280 1376 1512 1744 1024 1025 1028 1075 -HSync +Vsync
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "Videocard vendor"
    BoardName      "NVIDIA GeForce 4 MX (generic)"
    Option         "RenderAccel"        "true"
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "Videocard Vendor"
    BoardName      "NVIDIA GeForce 4 MX (generic)"
    BusID          "PCI:1:0:0"
    Option         "RenderAccel"        "true"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
#    Monitor        "Monitor0"
        Monitor     "Multiscan400ps"
    DefaultDepth    24
    SubSection     "Display"
        Viewport    0 0
        Depth       16
        Modes      "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1152x864" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen1"
    Device         "Videocard1"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Viewport    0 0
        Depth       24
        Modes      "1152x864"
    EndSubSection
EndSection

Section "Extensions"
    Option "Composite" "true"
EndSection
tom@earth:/etc/X11$ 


If you ignore the nvidia specific bits - using the "serverlayout" section you can arrange your screens, its seems you need to have 2 entries for the graphics card (device) and set up a screen for each of them (your DVI outputs) - for a single monitor you can just have the line 

    Screen      0  "Screen0" 0 0

(leave out:
     Screen      0  "Screen0" LeftOf "Screen1")
or 
    Screen      0  "Screen1" 0 0
to use your other output.

Hope this helps, Tom.

---

