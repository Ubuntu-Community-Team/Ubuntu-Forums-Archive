---
title: "Beryl giging white background."
date: 2006-10-28
forum: General Help
---

### Post by davidfield on 2006-10-28
I have installed the Edgy update, and decided that i wanted the compwiz installed, so i followed the isntructions on the page..

[http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

And I got it all installed, however when i invoke the 

beryl-manager

Command, it starts, a Beyrl logo pops up, then the background/wallpaper goes white..

Well i say the background/wallpaper, but its not really, because its like another layer lying ontop of the wallpaper, because i cant see the desktop icons..

What ami doing wrong?

The Sections i have edited in /etc/X11/xorg.conf look like this

> Section "Device"
    Identifier     "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Driver         "nvidia"
   ** Option          "TripleBuffer" "true"**
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NV17 [GeForce4 420 Go]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "TwinView" "True"
    Option         "TwinViewOrientation" "LeftOf"
    Option         "UseEdidFreqs" "True"
    Option         "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
# Enable 32-bit ARGB GLX Visuals
    **Option "AddARGBGLXVisuals" "True"**

[B]# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
    Option "DisableGLXRootClipping" "True"[/B]



Any help or guidence would be appreciated

---

### Post by mingster on 2006-11-01
i get exactly the same thing running on a twin head geforce 2

if i figure out a fix for it i'll let you know.](*,)

---

### Post by Kateikyoushi on 2006-11-01
Okay I join the club with the same problem...

---

### Post by Kateikyoushi on 2006-11-01
I did an nvidia-xconfig and then my desktop show up, well no windows frames but I changed it in veryl settings so now at least back up and running metacity.

```
sudo nvidia-xconfig
```

---

### Post by chaumurky on 2006-11-09
I'll throw my hat in the ring with this one as well. White background on screen one and on 2/3 of screen two. The last third shows trailing when I drag windows over it.

---

### Post by turbojugend_gr on 2006-11-09
@Davidfield: Comment this line * Option "DisableGLXRootClipping" "True"* restart X and post back here.

P.S.: Comment means put an **#** in front of it so it won't bew considered.

---

### Post by mbeierl on 2006-11-09
I get a similar effect with my Intel 945gm chipset unless I tell the driver to allocate more video memory with the

VideoRam 71680

option.  This tells the driver to allocate 70mb of memory, and then beryl works fine.

Don't know if that's related...

---

### Post by davidfield on 2006-11-10
Hi there, I commented out the line, and it made no difference..

Strange, but true..

---

### Post by davidfield on 2006-11-11
Does Beryl actually work with Twinview? Could it be that, that is causing the problem?

---

### Post by chaumurky on 2006-11-13
On the whole it does work with twinview for me - rotating the cube treats my 2 screens as a single 2560x1024 'face'. Even the 5/6 white and trailing rotates. I'm sure this minor glitch will be worked out down the line.

---

### Post by SisterChristian on 2006-11-17
Anyone figure out what's going on with this?  I am having the same issue...

---

### Post by kunjan1029 on 2006-11-24
me too. 

Edgy, Nvidia 9629, beryl 1.2 (latest) NV17, geforce4 MX 400 go, 64 M video ram. 

white background + 2/3 of the second screen with twinview and the windows in that empty blank space flicker.

any ideas?

---

### Post by davidfield on 2006-11-24
Found one forum, that suggests that the build in the CVS might resolve the problem.. but it didn't,..

---

### Post by davidfield on 2006-11-26
Interesting, i have diverted my laptop to Sabayon 3.1 and hey presto, out of the box, Twinview, AIGLX and Beryl  no tweaks, no config. So i guess this isn't a specific issue with Beryl. I'm sure i will be back running Edgy soon enough, i just want to see how the other half lives for a week or so, and see if i can figure out whats causing the problem..

---

### Post by kunjan1029 on 2006-11-27
can you post the xorg.conf from Sabayon here?

---

### Post by davidfield on 2006-11-27
They say hopme is where the heart is, and having got Sabayon working, the wife (who usually badgers me to put XP on my laptop) has Insisted i go back to edgy.. So An install of Edgy and Automatix in progress...

As requested the xorg.conf i used in Sabayon

> Section "Files"


    #FontPath    "/usr/share/fonts/local/"
    FontPath    "/usr/share/fonts/misc/"
    FontPath    "/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath    "/usr/share/fonts/75dpi/"
    FontPath    "/usr/share/fonts/100dpi/"
    FontPath     "/usr/share/fonts/corefonts"

EndSection

# **********************************************************************
# Module section -- this is an optional section which is used to specify
# which run-time loadable modules to load when the X server starts up.
# **********************************************************************

Section "Module"

    Load    "dbe"
    Load    "glx"
#    Load    "ddc"
    Load    "type1"
    Load    "freetype"
    Load    "extmod"
    Load    "synaptics"

# Load "dri"

EndSection


# **********************************************************************
# Server flags section.  This contains various server-wide Options.
# **********************************************************************

Section "ServerFlags"

     Option     "AllowMouseOpenFail" "true"
     #Option     "AIGLX" "true"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier      "Mouse3"
    Driver          "synaptics"
    Option          "SendCoreEvents"        "true"
    Option          "Device"                "/dev/psaux"
    Option          "Protocol"              "auto-dev"
    Option          "HorizScrollDelta"      "0"
    Option          "SHMConfig"             "on"
    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection


Section "InputDevice"

    Identifier    "Keyboard1"
    Driver    "kbd"
    
    Option    "AutoRepeat"    "500 5"
    Option      "XkbModel"      "pc105"
    Option    "XkbLayout"    "uk"
    Option      "XkbRules"      "xorg"

EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier    "Mouse1"
    Driver    "mouse"

    Option    "Device"    "/dev/psaux"
    Option    "Protocol"    "ImPS/2"
    Option "ZAxisMapping" "4 5"
     
EndSection

Section "InputDevice"
    Identifier    "Mouse2"
    Driver    "mouse"
    Option    "Protocol"    "ImPS/2"
    Option    "Device"    "/dev/input/mice"
    Option     "ZAxisMapping" "4 5"
EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier    "Generic Monitor"
    #Option      "DPMS"

    VertRefresh    50 - 75        # multisync
    HorizSync    28 - 110
    
    ModeLine "1280x800" 83.91 1280 1312 1624 1656 800 816 824 841
    ModeLine "1600x900" 173.86 1600 1672 2032 2176 900 902 914 940 +hsync +vsync    
    Modeline "1280x720" 75 1280 1336 1472 1664 720 725 730 751
    Modeline "1920x1080" 172.798 1920 2040 2248 2576 1080 1081 1084 1118 -hsync -vsync
    Modeline "1920x1200" 193.156 1920 2048 2256 2592 1200 1201 1203 1242 +hsync +vsync
    ModeLine "1366x768" 88.03 1366 1424 1680 1816 768 770 782 808
    ModeLine "848x480" 31.5 848 864 952 1056 480 481 484 497
    Modeline "720x576" 14.881 720 781 829 960 576 606 610 646 interlace +hsync +vsync
    ModeLine "856x480" 31.7 856 872 960 1064 480 481 484 497
    ModeLine "1024x512" 41.3 1024 1056 1160 1296 512 513 516 531
    ModeLine "960x600" 60 960 968 1048 1264 600 601 603 625 +HSync +VSync
    ModeLine "1088x612" 81.57 1088 1136 1376 1472 612 614 626 652 +hsync +vsync
    ModeLine "1792x1344" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
    ModeLine "1792x1344" 261.0 1792 1888 2104 2456 1344 1345 1348 1417 -hsync +vsync
    ModeLine "1856x1392" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
    ModeLine "1856x1392" 288.0 1856 1984 2208 2560 1392 1393 1396 1500 -hsync +vsync
    ModeLine "1920x1440" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
    ModeLine "1920x1440" 297.0 1920 2064 2288 2640 1440 1441 1444 1500 -hsync +vsync
    ModeLine "1800x1440" 230 1800 1896 2088 2392 1440 1441 1444 1490 +HSync +VSync
    ModeLine "1800x1440" 250 1800 1896 2088 2392 1440 1441 1444 1490 +HSync +VSync
    Modeline "1280x768" 81.59 1280 1280 1384 1688 768 769 774 791 

EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver      "nvidia" # do not remove vesa
    #Option "XAANoOffscreenPixmaps"
Option "HWCursor" "on"
Option "NvAGP" "2"
Option "RenderAccel" "0"
Option "Coolbits" "1"
Option "ConnectedMonitor" "DFP-0, CRT-0"
Option "NoPowerConnectorCheck"
Option "TwinView" "1"
Option "TwinViewOrientation" "DFP-0 LeftOf CRT-0"
Option "Metamodes" "DFP-0: 1920x1200, CRT-0: 1280x1024"
Option "TwinViewXineramaInfoOrder" "DFP-0, CRT-0" 
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier    "Screen 1"
    Device    "VESA"
    Monitor    "Generic Monitor"
    #Option "AddARGBGLXVisuals" "true"

# The favoured Depth and/or Bpp may be specified here

    DefaultDepth 24

    SubSection "Display"
        Depth        8
        ViewPort    0 0
        #Modes        "1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           16
        ViewPort        0 0
        #Modes        "1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           24
        ViewPort        0 0
        #Modes        "1024x768" "800x600" "640x480"
    EndSubsection


EndSection


Section "ServerLayout"
# The Identifier line must be present

    Identifier    "Main Layout"
    Screen 0     "Screen 1"
    InputDevice    "Mouse1" "CorePointer"
    InputDevice    "Mouse2" "SendCoreEvents"
    InputDevice "Mouse3" "SendCoreEvents"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   #Option "Composite" "Enable"
EndSection



---

### Post by desimo on 2006-11-30
I have a dual-head setup with Beryl under Edgy. 

I was having some difficulties with the "whitescreen" problem on initially running the cmd "beryl-xgl" 

This seems to "avoid" the problem for me.

I added in xorg.conf:
```

Section "ServerFlags"
        # an experiment
        Option "AIGLX" "true"
EndSection

```

killed X and gdm using "sudo killall gdm"

then from a console ran beryl-xgl && emerald

This doesn't seem like a concrete solution, but it seems to avoid the whitescreen problem, and I've been running beryl dual-head on Edgy for the past week or so...

Xorg.conf

```

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder3)  Wed Nov  1 19:47:17 PST 2006

# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
Identifier     "Default Layout"
Screen         "screen0" 0 0
#InputDevice    "joystick0"
InputDevice    "keyboard0"
InputDevice    "mouse0"
#InputDevice    "stylus" "SendCoreEvents"
#InputDevice    "cursor" "SendCoreEvents"
#InputDevice    "eraser" "SendCoreEvents"
EndSection

Section "Files"
    # path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
   #  Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "ServerFlags"
        # an experiment
        Option "AIGLX" "true"
EndSection

Section "InputDevice"
    Identifier     "keyboard0"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "mouse0"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

#Section "InputDevice"
#        Identifier   "joystick0"
#        Driver      "mouse"
#        Option      "Protocol"       "ExplorerPS/2"
#        Option      "Dev Name"       "joystick0"
#        Option      "Dev Phys"       "usb-0000:00:10.0-2/input0"
#        Option      "Device"         "event3 js0"
#        Option      "Buttons"        "12"
#        Option      "ZAxisMapping"   "4 5"
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
#    Identifier     "stylus"
#       Driver         "wacom"
#       Option         "Device" "/dev/wacom"          # Change to 
#       Option         "Type" "stylus"
#       Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#   EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
#    Identifier     "eraser"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "eraser"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
#    Identifier     "cursor"
#    Driver         "wacom"
#    Option         "Device" "/dev/wacom"          # Change to 
#    Option         "Type" "cursor"
#    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Monitor"
    Identifier     "HP f1905"
    Option         "DPMS"
EndSection

Section "Device"
        Identifier     "NVIDIA Corporation NV40 [GeForce 6800]"
        Driver         "nvidia"
        Option "TwinView" "True"
        Option "TwinViewOrientation" "RightOf"
        Option "RenderAccel" "1" 
        Option "UseEdidFreqs" "True"
        Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
        Option "NoPowerConnectorCheck"
        # Option "UseDisplayDevice" "LCD"
        # Option "ConnectedMonitor" "LCD, LCD"
EndSection

Section "Screen"
    Identifier     "screen0"
    Device         "NVIDIA Corporation NV40 [GeForce 6800]"
    Monitor        "HP f1905"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection

        ## Enable 32-bit ARGB GLX Visuals
               Option "AddARGBGLXVisuals" "True"
EndSection

```

---

### Post by davidfield on 2006-12-03
Thanks for that update, i gave it a try, and also made some of the same changes that you have made in your xorg.conf, and still no joy. 

I am running Beryl, 0.1.2 (well this is the version number which pops up when the Bryle manager loads) Maybe this is the problem, i noticed on Sabayon Linux its using 1.0 version of Beryl, and on some of the Beryle forums it stats that there was a version in CVS which may have resolved this issue?


How can i downgrade/upgrade the version of Beryl? And would i be better off going to Compiz? if i'm running Compiz?

For the record, i have enclosed my xorg.con which i'm running right now below.. just incase i'm being a right goon, and missing something...

> 
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the /etc/X11/xorg.conf manual page.
# (Type "man /etc/X11/xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
        FontPath        "/usr/share/fonts/X11/misc"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "i2c"
        Load    "bitmap"
#       Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
EndSection

Section "ServerFlags"
        # an experiment
        Option "AIGLX" "true"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
        Option          "XkbOptions"    "lv3:ralt_switch"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA Corporation NV17 [GeForce4 420 Go]"
        Driver          "nvidia"
        BusID           "PCI:1:0:0"
Option "TwinView" "True"
Option "TwinViewOrientation" "LeftOf"   
Option "UseEdidFreqs" "True"
Option "RenderAccel" "1"
Option "MetaModes" "1280x1024,1280x1024; 1024x768,1024x768"
# Option "UseDisplayDevice" "DFP" 
Option "ConnectedMonitor" "DFP, CRT"
Option          "TripleBuffer" "true"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA Corporation NV17 [GeForce4 420 Go]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
# Enable 32-bit ARGB GLX Visuals
    Option "AddARGBGLXVisuals" "True"

# If you are using an older version of compiz that
# does not support rendering into the Composite
# Overlay Window, you will need to disable clipping
# of GLX rendering to the X Root window with this
# option, or you will get a blank screen after
# starting compiz:
   Option "DisableGLXRootClipping" "True"
        SubSection "Display"
                Depth           1
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"0 0
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
        InputDevice     "Synaptics Touchpad"
EndSection

# Section "DRI"
#       Mode    0666
# EndSection

Section "Extensions"
Option "Composite" "Enable"
EndSection


and the sources.list is

> 
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse univers
e
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy main restricted multiverse uni
verse

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiverse
 universe
deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-updates main restricted multiv
erse universe

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted univer
se multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) edgy-backports main restricted un
iverse multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiverse u
niverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted multiver
se universe
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiverse u
niverse
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) edgy-proposed restricted main multiver
se universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

#AUTOMATIX REPOS START

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe mul
tiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multi
verse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe mult
iverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
#AUTOMATIX REPOS END

 deb [http://wine.budgetdedicated.com/apt](http://wine.budgetdedicated.com/apt) edgy main
deb [http://beryl-mirror.lupine.me.uk/](http://beryl-mirror.lupine.me.uk/) edgy main

deb [http://seerofsouls.com/](http://seerofsouls.com/) edgy contrib



---

### Post by desimo on 2006-12-04
Think about commenting out the dri module.  I've heard that there can be conflicts, there...

Then I just use
```
beryl --replace && beryl-manager
```

---

### Post by davidfield on 2006-12-22
Sorry for the delay, spent a week testing out Suse 10.2 (Personal opinion, its slow, yast sucks, and nothing works properly) Tried the above, and indeed used the latest version of Beryl, what appears to be causing the problem, is the Window borders, if i turn off the Beryl splash screen, the white background doesn't appear until the windows borders are drawn..? If that makes sense..?

---

### Post by Azakus on 2006-12-22
There's an option in the Newest Beryl (0.1.3) called "Disable GL Yield" in the advanced options under beryl-manager. It is supposed to fix some redraw bugs. Turn that option on and see if it fixes your white screen.

---

### Post by kunjan1029 on 2006-12-28
Ok so i updated to the latest beryl 0.1.4 still the same issue. the rendering does seem a bit faster though.

I made a video of the problem. Point any devs you talk to here, so that they can get a better idea.

[http://www.youtube.com/watch?v=0NPmsAPQm9g](http://www.youtube.com/watch?v=0NPmsAPQm9g)

---

### Post by mnorayr on 2007-01-22
I have got exactly the same problem on Nvidia Quadro4 580 XGL, ubuntu edgy, beryl 1.4:( 
I have found that when I open an image in gimp, it just shows black space, anb more over when I rotate the cube, the white part stays, but the right edge , which shows the wallpaper with some window trails smeared over it, refreshes and comes back to normal. So overall it seems like a strange redraw problem...

---

### Post by mnorayr on 2007-01-23
Ok, bad news, I just found somewhere on the beryl forums that this is a limitation of some older- slower cards, they do not allow more than 2040x 2040 (ore something close) 3D acceleration. 
So, THE CASE IS SOLVED :)

---

