---
title: "[SOLVED] login/greeter window"
date: 2007-09-11
forum: General Help
---

### Post by Damanther on 2007-09-11
This is not a huge deal, I'm mostly just curious. When my login/greeter screen comes up, the screen it displays is "bigger" than my monitor. I can move my mouse around and have it scroll to see all of the background and such, and when I log in my desktop is my normal 1024x768 display which fits entirely on my monitor screen.

I have a feeling there might be a setting in my Xorg.conf that is making it do this, but I hate playing with my xorg.conf if I'm not really sure what I'm supposed to be changing. So if anyone can help point me in the right direction I would appreciate it.

Damanther

---

### Post by dreadlord_chris on 2007-09-11
could you post the contents of your xorg.conf please?

---

### Post by Damanther on 2007-09-11
xorg.conf here:

Section "ServerLayout"

  #    InputDevice    "stylus" "SendCoreEvents"
  #    InputDevice    "cursor" "SendCoreEvents"
  #    InputDevice    "eraser" "SendCoreEvents"
    Identifier     "Default Layout"
    Screen      0  "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
EndSection

Section "Files"

  # path to defoma fonts
    FontPath    "/usr/share/fonts/X11/misc"
    FontPath    "/usr/share/fonts/X11/100dpi:unscaled"
    FontPath    "/usr/share/fonts/X11/75dpi:unscaled"
    FontPath    "/usr/share/fonts/X11/Type1"
    FontPath    "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
    FontPath    "/usr/local/share/fonts"
EndSection

Section "Module"
    Load           "i2c"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "int10"
    Load           "vbe"
    Load           "glx"
    Load           "v4l"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
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

Section "Monitor"
    Identifier     "GVision"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Monitor"
    Identifier     "monitor1"
    VendorName     "Plug 'n' Play"
    ModelName      "Plug 'n' Play"
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV17 [GeForce4 MX 440]"
    Driver         "nvidia"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "device1"
    Driver         "nv"
    BoardName      "nv"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"

  #    Option "TwinView"
  #    Option "SecondMonitorHorizSync" "30-50"
  #    Option "SecondMonitorVertRefresh" "60"
  #    Option "MetaModes" "1024x768,800x600;800x600,800x600;640x480,800x600"
  #    Option "TwinViewOrientation" "RightOf"
  #    Option "TVOutFormat" "Composite"
  #    Option "Connected Monitor" "CRT,TV"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV17 [GeForce4 MX 440]"
    Monitor        "GVision"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1440 900
        Depth       24
        Modes      "1440x900@60" "1024x768@60" "800x600@60" "800x600@56" "640x480@60"
    EndSubSection
EndSection

Section "Screen"

  #
    Identifier     "screen1"
    Device         "device1"
    Monitor        "monitor1"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
        Modes      "1024x768x480@60"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection



I

---

### Post by dreadlord_chris on 2007-09-11
are you using 2 monitors and 2 GPU's?

---

### Post by Damanther on 2007-09-11
No, just one monitor and one video card. Its the nvidia 440.  I did recently change monitors, but I am still only using the new one. I usually don't edit the xorg.conf by hand. Most of those video settings should be from the nvidia-settings tool.

Oh, the driver entries were probably done by ENVY. I used it because I couldn't get the nvidia driver working by hand.

Damanther

---

### Post by dreadlord_chris on 2007-09-12
your xorg.conf is **horribly** messed up - I'm actually kinda surprised that it works at all. You have entries for both the open-source (**nv**) _and_ the propietary (**nvidia**) drivers in it - and I'm really not entirely sure which one is being used.

What you really need to do is just start over with a clean xorg.conf:
```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.old
sudo dpkg-reconfigure xserver-xorg

```
go through the options...
for the driver I'm reasonably sure you want _nvidia_ rather then _nv_
when you get to the resolution section - choose only the resolutions that your monitor/GPU can use & that you want available
i.e. the max resolution that my monitor will support is 1024x768, the min I want my res to be is 800x600 - so I only choose 1024x768 & 800x600

You should be able to accept the defaults for the rest...
remember to save at the end...
restart X - control-alt-backspace
if all goes well you should see the NVIDIA logo

---

### Post by Damanther on 2007-09-14
Gonna try rebuilding this xorg.conf file like you state. *crosses fingers*

I did find out that the virtual entry in the display section is what the login/greeter screen uses. So I changed it to 1024x768 and it looks much better now.

I'm going to mark this as solved since that actual posted issue is resolved. But I will update this thread when I try the general xorg.conf cleanup and post how it went. I do see the nvidia logo on boot as it is now though. I'm just curious to see what the end result is with the reconfigure.

---

