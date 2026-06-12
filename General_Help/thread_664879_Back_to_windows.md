---
title: "Back to windows"
date: 2008-01-11
forum: General Help
---

### Post by timboellis on 2008-01-11
Well I have tried and tried but cannot get my Nvidia 7300 GT 512 to work on this distro so off back to windows its a shame its a great system, checked all the other posts and most 7300 are having the same issue.

However just a note as I am a windows user looking to come to linux the things I found very confusion is the lack of instructions or F.A.Q I know they are all here somewhere but just a quick guide for us newbies fom how to install Nvidia card/ ATI through to install Beryl etc.

---

### Post by overdrank on 2008-01-11
> **timboellis said:**
> Well I have tried and tried but cannot get my Nvidia 7300 GT 512 to work on this distro so off back to windows its a shame its a great system, checked all the other posts and most 7300 are having the same issue.

However just a note as I am a windows user looking to come to linux the things I found very confusion is the lack of instructions or F.A.Q I know they are all here somewhere but just a quick guide for us newbies fom how to install Nvidia card/ ATI through to install Beryl etc.

Hi and my son's system just install feisty with a pny 7300 and all is great with dual monitors and all. Have you tried Envy to install the graphics driver? You may try Feisty if you are using Gutsy. Good luck!

---

### Post by timboellis on 2008-01-11
Never heard of envy I am on Gutsy, will have a look around to see what i can find

---

### Post by PeterJS on 2008-01-11
Envy is best avoided unless you really need to use it. Have you tried the restricted drivers manager(System > Administration > Restricted Driver Manager)?

---

### Post by stchman on 2008-01-11
> **timboellis said:**
> Well I have tried and tried but cannot get my Nvidia 7300 GT 512 to work on this distro so off back to windows its a shame its a great system, checked all the other posts and most 7300 are having the same issue.

However just a note as I am a windows user looking to come to linux the things I found very confusion is the lack of instructions or F.A.Q I know they are all here somewhere but just a quick guide for us newbies fom how to install Nvidia card/ ATI through to install Beryl etc.

Envy is a great program.  I have a 7600GT and just enabling the restricted driver was enough to get the card going.

Go to Alberto Milone's website.

[http://www.albertomilone.com/](http://www.albertomilone.com/)

---

### Post by PeterJS on 2008-01-11
The big warning on this page is why we don't reccomend using Envy.
[http://www.albertomilone.com/nvidia_scripts1.html](http://www.albertomilone.com/nvidia_scripts1.html)
The restricted drivers manager does a pretty good job of identifying the card and getting it configured properly without needing to uninstall the driver to upgrade.

---

### Post by timboellis on 2008-01-11
Put it this way, i do nto get the Nvidia splash screen what if any is a good way to confirm that the card is installed correctly?

Some type of bench mark

I can do a glxgears that gives me 2440.625FPS

And GLX info

server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:

---

### Post by overdrank on 2008-01-11
> **timboellis said:**
> Put it this way, i do nto get the Nvidia splash screen what if any is a good way to confirm that the card is installed correctly?

Some type of bench mark

I can do a glxgears that gives me 2440.625FPS

And GLX info

server glx vendor string: NVIDIA Corporation
server glx version string: 1.4
server glx extensions:
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_SGIX_fbconfig, 
    GLX_SGIX_pbuffer, GLX_SGI_video_sync, GLX_SGI_swap_control, 
    GLX_EXT_texture_from_pixmap, GLX_ARB_multisample, GLX_NV_float_buffer, 
    GLX_ARB_fbconfig_float
client glx vendor string: NVIDIA Corporation
client glx version string: 1.4
client glx extensions:

Hi and you can use either of this commands
```
cat /etc/X11/xorg.conf
cat < /etc/X11/xorg.conf |grep Driver
```
The first command you will look for the device section in the xorg
The second command will list all the drivers in the xorg

---

### Post by timboellis on 2008-01-11
I get this

 Driver         "kbd"
    Driver         "mouse"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "wacom"
    Driver         "nvidia"


[PHP]# Edit this file with caution, and see the xorg.conf manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"

        # Uncomment if you have a wacom tablet
        #       InputDevice     "stylus"        "SendCoreEvents"
        #       InputDevice     "cursor"        "SendCoreEvents"
        #       InputDevice     "eraser"        "SendCoreEvents"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"
EndSection

Section "Module"
    Load           "glx"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "gb"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ImPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"# Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Generic Video Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       24
        Modes      "1920 x 1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
[/PHP]

---

### Post by overdrank on 2008-01-11
@ timboellis Ok it looks good, so what is the issue you seem to be having with the graphics?

---

### Post by PeterJS on 2008-01-11
Looks like it's loaded and working. Is something not working?

---

### Post by timboellis on 2008-01-11
Well i tried 1 game and 3d graphic app seemed to be struggling a bit, however downloading urban terror to see how that is

---

