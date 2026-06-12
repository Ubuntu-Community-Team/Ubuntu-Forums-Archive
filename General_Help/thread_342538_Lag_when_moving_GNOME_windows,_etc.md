---
title: "Lag when moving GNOME windows, etc"
date: 2007-01-20
forum: General Help
---

### Post by CharlesM on 2007-01-20
I'm using a fresh install of Ubuntu Edgy Eft and I'm experiencing a sort of lag when scrolling, resizing windows, etc. Any ideas of what it could be?

Thank you.

---

### Post by JamieC on 2007-01-20
What are your computer specifications? Approximately how long is the lag time?

---

### Post by CharlesM on 2007-01-20
Oops, sorry, I should of said. They're something along the lines of: Core 2 Duo E6600, ATi X1950XT, 2GB RAM.

I couldn't tell you how long it is, but it's a noticeable difference from previous installations and Windows on my old PC.

---

### Post by rocknrolf77 on 2007-01-20
I think you need to install graphics driver for your ati card : [http://www.albertomilone.com/driver.html](http://www.albertomilone.com/driver.html)

Open up a terminal and copy this code in to it ```
cat /etc/X11/xorg.conf
```

Then copy it and paste what you get here. :D

---

### Post by CharlesM on 2007-01-20
Here you go:

> Section "Files"
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
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "type1"
        Load    "vbe"
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
        Identifier      "ATI Technologies, Inc. ATI Default Card"
        Driver          "vesa"
        BusID           "PCI:5:0:0"
EndSection

Section "Monitor"
        Identifier      "MD17"
        Option          "DPMS"
        HorizSync       28-64
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. ATI Default Card"
        Monitor         "MD17"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus" "SendCoreEvents"
        InputDevice     "cursor" "SendCoreEvents"
        InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

---

### Post by rocknrolf77 on 2007-01-20
I don't have an ati card anymore but the lag I think you can first fix with replacing 

Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
Driver "vesa"
BusID "PCI:5:0:0"
EndSection

with :

Section "Device"
Identifier "ATI Technologies, Inc. ATI Default Card"
Driver "ati"
BusID "PCI:5:0:0"
EndSection

for doing that write this in the terminal : ```
gksudo gedit /etc/X11/xorg.conf
```

Give your password and edit this by hand. After that log out of your session and then hit ctrl-alt-backspace to restart the x-server. Then log back in. If for some reason this should go wrong and the x-server will not work.

Hit Ctrl-F1 and log in and type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then select the vesa driver again. then you can restart again.

---

### Post by CharlesM on 2007-01-20
I have tried both the method you suggested and the ATi driver but I'm afraid it did not work, I'm also stuck in 1024x768 now. Any suggestions?

---

### Post by CharlesM on 2007-01-20
Oops! I was at fault here when installing the driver, I didn't correctly run aticonfig after installing the ATi driver. It's working perfectly now!

Thanks for the help.

---

### Post by rocknrolf77 on 2007-01-20
Good to hear . Welcome to ubuntu. 


:guitar:  ON

---

