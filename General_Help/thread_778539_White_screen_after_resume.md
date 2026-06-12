---
title: "White screen after resume"
date: 2008-05-02
forum: General Help
---

### Post by jazzgossen on 2008-05-02
Since upgdrading to 8.04, I get a white screen with a visible cursor after resuming from hibernate, if I use compiz. If I type in my password (blindly) my desktop appears, so it's not a critical failure, but confusing for some users. It worked well in 7.10. I have an Nvidia card (6600) using driver version 169.12. I saw one post that suggested to disable "sync to vblank" in nvidia-settings. I did that, but it didn't help. Any other ideas?

---

### Post by brigux on 2008-05-02
Can you post your xorg.conf?

---

### Post by jazzgossen on 2008-05-02
Sure can:
```

Section "Files"


    #FontPath	"/usr/share/fonts/local/"
    FontPath	"/usr/share/fonts/misc/"
    FontPath	"/usr/share/fonts/Type1/"
    FontPath    "/usr/share/fonts/TTF/"
    FontPath	"/usr/share/fonts/75dpi/"
    FontPath	"/usr/share/fonts/100dpi/"
    FontPath 	"/usr/share/fonts/corefonts"

EndSection

# **********************************************************************
# Module section -- this is an optional section which is used to specify
# which run-time loadable modules to load when the X server starts up.
# **********************************************************************

Section "Module"

    Load	"dbe"
    Load	"i2c"
    Load	"glx"
    Load	"ddc"
    Load	"type1"
    Load	"freetype"
    Load	"extmod"
    Load	"synaptics"
    Load	"vbe"
#   Load        "dri"

EndSection


# **********************************************************************
# Server flags section.  This contains various server-wide Options.
# **********************************************************************

Section "ServerFlags"

     Option 	"AllowMouseOpenFail" "true"

EndSection

# **********************************************************************
# Input devices
# **********************************************************************

# **********************************************************************
# Core keyboard's InputDevice section
# **********************************************************************

Section "InputDevice"
    Identifier		"Synaptics1"
    Driver		"synaptics"
    Option		"SendCoreEvents"	"true"
    Option		"Device"		"/dev/psaux"
    Option		"Protocol"		"auto-dev"
    Option		"HorizScrollDelta"	"0"
    Option		"SHMConfig"		"on"
    # For ALPS/MacBook TouchPads
    #Option		"MaxSpeed"		"0.7"
    #Option		"MinSpeed"		"0.18"
    #Option		"AccelFactor"		"0.08"
    #Option		"TopEdge"		"120"
    #Option		"LeftEdge"		"120"
    #Option		"BottomEdge"		"830"
    #Option		"RightEdge"		"650"
    #Option		"FingerLow"		"25"
    #Option		"FingerHigh"		"30"
    # MacBook touchpad
    #Option		"MaxTapTime"		"180"
    #Option		"MaxTapMove"		"220"
    #Option		"MaxDoubleTapTime"	"180"
    #Option		"VertScrollDelta"	"20"
    #Option		"HorizScrollDelta"	"50" 
    #Option		"TapButton2"		"3"
    #Option		"TapButton3"		"2"
    #Option		"VertTwoFingerScroll"	"1"

    # Do you keep moving the mouse while typing? Try this trick.
    #synclient TouchpadOff=1 disable your synaptics touchpad
    #synclient TouchpadOff=0 enable your synaptics touchpad
EndSection


Section "InputDevice"

    Identifier	"Keyboard1"
    Driver	"kbd"
    
    Option	"AutoRepeat"	"500 5"
    Option      "XkbModel"      "pc105"
    Option	"XkbLayout"	"us"
    Option      "XkbRules"      "xorg"
    # Macintosh keyboard
    #Option	"XkbOptions"	"lv3:rwin_switch"

EndSection


Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom1"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "stylus"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom2"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "eraser"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "wacom3"
  Option        "Device"        "/dev/wacom"          # Change to 
                                                      # /dev/input/event
                                                      # for USB
  Option        "Type"          "cursor"
  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
EndSection


# **********************************************************************
# Core Pointer's InputDevice section
# **********************************************************************

Section "InputDevice"

# Identifier and driver

    Identifier	"Mouse1"
    Driver	"mouse"

    Option	"Device"	"/dev/psaux"
    Option	"Protocol"	"ImPS/2"
    Option	"ZAxisMapping"	"4 5"
     
EndSection

# Section "InputDevice"
#     Identifier	"Mouse2"
#     Driver	"mouse"
#     Option	"Protocol"	"ImPS/2"
#     Option	"Device"	"/dev/input/mice"
#     Option 	"ZAxisMapping" "4 5"
# EndSection


# **********************************************************************
# Monitor section
# **********************************************************************

# Any number of monitor sections may be present

Section "Monitor"

    Identifier	"Generic Monitor"
    #Option      "DPMS"

    VertRefresh 48-170
    HorizSync 30-137
	
EndSection

# **********************************************************************
# Graphics device section
# **********************************************************************

# Any number of graphics device sections may be present

Section "Device"
    Identifier  "VESA"
    Driver      "nvidia" # do not remove vesa
    #Option "RenderAccel" "on"
    Option "XAANoOffscreenPixmaps"
    #Option "BusType" "PCI"
    #Option "ColorTiling" "on"
    #Option "EnablePageFlip" "on"
    Option  "NvAGP" "1"
    Option  "NoLogo" "true"
EndSection


# **********************************************************************
# Screen sections.
# **********************************************************************

Section "Screen"

# The Identifier, Device and Monitor lines must be present

    Identifier	"Screen 1"
    Device	"VESA"
    Monitor	"Generic Monitor"
    Option "AddARGBGLXVisuals" "true"

# The favoured Depth and/or Bpp may be specified here

    DefaultDepth 24

    SubSection "Display"
        Depth		8
        ViewPort	0 0
        Modes "1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           16
        ViewPort        0 0
        Modes "1024x768" "800x600" "640x480"
    EndSubsection

    SubSection "Display"
        Depth           24
        ViewPort        0 0
        Modes  "1600x1200" "1280x960" "1152x864" "1024x768" "800x600" "640x480"
    EndSubsection


EndSection


Section "ServerLayout"
# The Identifier line must be present

    Identifier	"Main Layout"
    Screen 0 	"Screen 1"
    InputDevice	"Mouse1" "CorePointer"
#    InputDevice	"Mouse2" "SendCoreEvents"
    #InputDevice "Synaptics1" "SendCoreEvents"
    #InputDevice "wacom1" "SendCoreEvents"
    #InputDevice "wacom2" "SendCoreEvents"
    #InputDevice "wacom3" "SendCoreEvents"
    InputDevice "Keyboard1" "CoreKeyboard"

EndSection

Section "DRI"
    Mode 0666
EndSection

Section "Extensions"
   Option "Composite" "Enable"
EndSection

```

---

### Post by brigux on 2008-05-02
sorry nothing I can pinpoint in your file.

However, look at this bug report:
[https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/219388](https://bugs.launchpad.net/ubuntu/+source/xscreensaver/+bug/219388)
Looks like your issue.. Sorry they dont seem to have any solution yet (apart from disabling your desktop effects).

---

### Post by rupali_4 on 2008-05-02
You can do everything you want to do in a day on [www.baajaa.com](www.baajaa.com). You can look at job openings, find a date, rent an apartment, sell your bike and buy used items. And if you are interested in showbiz you can post your profile along with pics and your video as well. Also Balaji Telefilms is conducting auditions on [www.baajaa.com](www.baajaa.com) . All this and lots more on [www.baajaa.com](www.baajaa.com) !

One of the new features added on [www.baajaa.com](www.baajaa.com) is Yellow Pages. You can create a simple listing of your business for free. But what is really interesting is that you can Create Your Own Website (with your Logo, 5 pics, Company Profile, List of Products & Services, Video) and you get a Free Premium Yellow Page listing. For just Rs.3999/- !
 
Thanks,

---

### Post by HDave on 2008-05-02
The bug previously shown is a duplicate.  Always go to the original bug for the latest information.  I have been tracking this one closely because I get the white screen with fast user switching and compiz.

While the problem is an known nVidia bug, they just published a workaround-fix for it today...check it out:

[https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264]("https://bugs.launchpad.net/ubuntu/+source/compiz/+bug/160264")

If you want, you can download the patch from the developers repo.  Gotta love this open source eh?

---

### Post by locohygynx on 2008-05-02
I'm having this same exact problem. I've been looking thru this post and links provided for the fix and from what I can tell I download compiz-core_0.7.4-0ubuntu6+ppa1_i386.deb file and run it? I'm on Ubuntu 8.04, i386, Nvidia 5200 FX. Is that correct? (sorry for my newbness ](*,))

---

### Post by HDave on 2008-05-02
I just tried the fix myself and it works.  Here's what I did:

1) Edit your source.list file to add the test repo from the developer:

```
sudo gedit /etc/apt/sources.list
```

then add the following line:

```
deb http://ppa.launchpad.net/superm1/ubuntu hardy main
```

save and exit.

2) Start synaptic and hit "reload"...exit

3) The update manager will start telling you you have updates.  Tell it to go ahead and upgrade the packages.

4) Log out...log in...

Enjoy the fix.

I plan to remote the line from my sources.list right away.  It's not good to have a test repo always updating your system.  The developer hasn't stated when a permanent fix will be available.  My guess...October.

---

### Post by jazzgossen on 2008-05-06
That's it. Great, thanks.

---

