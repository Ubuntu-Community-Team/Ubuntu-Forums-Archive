---
title: "Desktop Effect Could Not Be Enabled"
date: 2008-05-09
forum: General Help
---

### Post by kmb`` on 2008-05-09
hey wats up guys, i have a problem and cant solve it, if anybody could find a threat or tell me how to fix this problem that would be great, i have a hp laptop dv6500 
once this is problem can be fixed can somebody tell me how i can enable compiz fusion.

if somebody can help please do!! thanks

---

### Post by macaholic on 2008-05-09
First off, what graphics card do you have? Do you have the correct drivers installed and enabled?

---

### Post by Exsecrabilus on 2008-05-09
Do you have your graphics driver enabled?

Go **System** >> **Administration** >> **Hardware Drivers**.

If it detected your graphics card, just click on the checkbox and you will get a choice whether or not to enable the graphics card.

Proceed and let it finish downloading the proper package to enable the driver.

If you're running Ubuntu 8.04 (Hardy Heron) effects should be enabled automatically after the above step.

Now go to Terminal and type:

```
sudo apt-get install compizconfig-settings-manager simple-ccsm
```

To change desktop effects settings, now go **System** >> **Preferences** >> **Advanced Desktop Effects Settings** or **System** >> **Preferences** >> **CompizConfig Settings Manager** or Alt+F2 and type in *ccsm*. For a simpler way, go **System** >> **Preferences** >> **Simple CompizConfig Settings Manager** or Alt+F2 and type in *simple-ccsm*.

---

### Post by kmb`` on 2008-05-13
hey sorry for the late reply, but i dont see the option of hardware drivers in my admin.
dunno why

---

### Post by herger on 2008-05-13
Hi all!
I have a similar problem, I can't enable desktop effetcs.
My video card is the nVidia GeForce 8600 GT, I have the latest drivers installed and the proprietary driver manager works correctly.
I post You my xorg.conf file:

```

Section "ServerLayout"
        Identifier      "Default Layout"
  screen 0 "Default Screen" 0 0
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "Synaptics Touchpad"
EndSection

Section "Files"
EndSection

Section "Module"
        Load            "glx"
        Load            "v4l"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"        "/dev/psaux"
        Option          "Protocol"      "auto-dev"
        Option          "HorizScrollDelta"      "0"
EndSection

Section "Monitor"
        Identifier      "Failsafe Monitor"
        Vendorname      "Dell"
        Modelname       "Dell 1280x1024 Laptop Display Panel"
        Horizsync       31.5-90.0
        Vertrefresh     59.0-75.0
        #  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
        #  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
        #  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
        #  modeline  "1280x768@60" 80.14 1280 1344 1480 1680 768 769 772 795 -hsync +vsync
        #  modeline  "1280x720@60" 74.48 1280 1336 1472 1664 720 721 724 746 -hsync +vsync
        #  modeline  "1280x800@75" 107.21 1280 1360 1496 1712 800 801 804 835 -hsync +vsync
        #  modeline  "1280x768@75" 102.98 1280 1360 1496 1712 768 769 772 802 -hsync +vsync
  modeline  "1280x800@60" 83.46 1280 1344 1480 1680 800 801 804 828 -hsync +vsync
        #  modeline  "1440x900@75" 136.49 1440 1536 1688 1936 900 901 904 940 -hsync +vsync
        #  modeline  "1440x900@60" 106.47 1440 1520 1672 1904 900 901 904 932 -hsync +vsync
        #  modeline  "1600x1024@60" 136.36 1600 1704 1872 2144 1024 1025 1028 1060 -hsync +vsync
        #  modeline  "1680x1050@60" 147.14 1680 1784 1968 2256 1050 1051 1054 1087 -hsync +vsync
        #  modeline  "1680x1050@75" 188.07 1680 1800 1984 2288 1050 1051 1054 1096 -hsync +vsync
        #  modeline  "1920x1200@60" 193.16 1920 2048 2256 2592 1200 1201 1204 1242 -hsync +vsync
        Gamma   1.0
EndSection

Section "Monitor"
        Identifier      "monitor1"
        Vendorname      "Plug 'n' Play"
        Modelname       "Plug 'n' Play"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
        Gamma   1.0
EndSection

Section "Device"
        Identifier      "Failsafe Device"
        Boardname       "NVIDIA GeForce 8 Series"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  0
        Vendorname      "NVIDIA"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Device"
        Identifier      "device1"
        Boardname       "NVIDIA GeForce 8 Series"
        Busid           "PCI:1:0:0"
        Driver          "nvidia"
        Screen  1
        Vendorname      "NVIDIA"
EndSectionSection "Screen"
        Identifier      "Default Screen"
        Device          "Failsafe Device"
        Monitor         "Failsafe Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1920    1200
                Modes           "1280x800@60"   "1440x900@75"   "1280x768@75"   "1440x900@60"   "1280x800@75"   "1600x1024@60"  "1280x720@60"   "1680x1050@60"  "1280x768@60"   "1680x1050@75"  "800x600@60"    "1920x1200@60"  "800x600@75"    "800x600@72"
        EndSubSection
EndSection

Section "Screen"
        #   
        Identifier      "screen1"
        Device          "device1"
        Monitor         "monitor1"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Modes           "1280x800@60"
        EndSubSection
EndSection

Section "ServerFlags"
EndSection

Section "Extensions"
        Option     "Composite"  "Enable"
EndSection

                                                                                                                                                                                                                                                                                    

```

if I try to restart compiz, it says

```

Checking for Xgl: not present. 
Detected PCI ID for VGA: 01:00.0 0300: 10de:0427 (rev a1) (prog-if 00 [VGA])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: not present. 
aborting and using fallback: /usr/bin/metacity 

```

but if I try to install xserver-xgl the x-session BRAKES and I have to remove the package and restore x from shell...

What can I do? :confused:

If I post

```


glxinfo |grep rendering


```

it says

```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".


```

Thanks in advance for Your help and best regards

Herger

---

### Post by Exsecrabilus on 2008-05-13
> **kmb`` said:**
> hey sorry for the late reply, but i dont see the option of hardware drivers in my admin.
dunno why
Press Alt+F2. Type in:
```
gksu -D /usr/share/applications/jockey-gtk.desktop /usr/bin/jockey-gtk
```
And press **Run**.

Then do what I said in my previous reply.

---

### Post by kmb`` on 2008-05-17
hey, i did what you told me, i looked back at my admin options, and did not find the option
you have a clue what it might be ?

---

### Post by Exsecrabilus on 2008-05-17
Apparently it hasn't detected your graphics card.....
Hmm, I wonder why.....?

---

### Post by devilscemo on 2008-05-18
hello... i have the same problems... but they begin at startup... the desktop doesn't load even though everything else works fine... i have graphics card installed and working... 
when i give the command: glxinfo |grep rendering it says direct rendering :yes.
When i try 2 start effects (compiz) the screen goes black.. and nothing happens...
Can any1 help?? thank you

---

### Post by jekscar on 2008-05-18
My compiz correctly set doesn't start up by itself. Everytime require to go through Application/System Tool/compiz.

I've added to Session/Start up the following command:

compiz --replace

but nothing has changed!

---

### Post by babylon2233 on 2008-05-18
For Nvidia 8600 users, all you need is Envyng-gtk. I've the same problem before but now everything solved with this fantastic tools. Thanks to Alberto Milone.

[http://albertomilone.com/nvidia_scripts1.html]("http://albertomilone.com/nvidia_scripts1.html")

---

### Post by kmb`` on 2008-05-18
oh i c, then do you know or can show me a website that can tell me how to install Intel Graphics Media Accelerator X3100 on a dv6626ca hp
ive been looking and found nothing so far
thanks in advance btw i really do appreciate the help!!!

---

