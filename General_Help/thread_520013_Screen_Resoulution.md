---
title: "Screen Resoulution"
date: 2007-08-07
forum: General Help
---

### Post by OmegaMB on 2007-08-07
I recently installed Ubuntu using Wubi, and I can only choose screen resoulutions of 800x600 when I normally use 1024x768. my graphics card model is nVidia Geforce MX.

---

### Post by PurposeOfReason on 2007-08-07
You'll have to edit you xorg.conf file to show those resolutions. In the terminal type, "sudo gedit /etc/X11/xorg.conf". Then in the display section change each depth to show the resolutions you want. Here is mine as an example. But of course make a backup first. "sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.bak". Just in case.

```
Section "ServerLayout"
   Identifier     "Default Layout"
   Screen         "Default Screen"
   InputDevice    "Generic Keyboard"
   InputDevice    "Configured Mouse"
EndSection

Section "Files"

   # path to defoma fonts
   FontPath        "/usr/share/fonts/X11/misc"
   FontPath        "/usr/share/fonts/X11/cyrillic"
   FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
   FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
   FontPath        "/usr/share/fonts/X11/Type1"
   FontPath        "/usr/share/fonts/X11/100dpi"
   FontPath        "/usr/share/fonts/X11/75dpi"
   FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
   Load           "bitmap"
   Load           "dbe"
   Load           "ddc"
   Load           "extmod"
   Load           "freetype"
   Load           "glx"
   Load           "int10"
   Load           "vbe"
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
   Option         "Protocol" "ExplorerPS/2"
   Option         "ZAxisMapping" "4 5"
   Option         "Emulate3Buttons" "true"
   Option         "Buttons" "7"
   Option         "ButtonMapping" "1 2 3 6 7"
EndSection

Section "Monitor"
   Identifier     "HW173D"
   HorizSync       30.0 - 75.0
   VertRefresh     50.0 - 85.0
   Option         "DPMS"
EndSection

Section "Device"
   Identifier     "NVIDIA GeForce 7600"
   Driver         "nvidia"
   Option         "AddARGBGLXVisuals" "True"
EndSection

Section "Screen"
   Identifier     "Default Screen"
   Device         "NVIDIA GeForce 7600"
   Monitor        "HW173D"
   DefaultDepth    24
   SubSection     "Display"
       Depth       1
       Modes      "1600x1200" "1440x900" "1280x1024" "1280x960"
"12s00x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
       Depth       4
       Modes      "1600x1200" "1440x900" "1280x1024" "1280x960"
"1200x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
       Depth       8
       Modes      "1600x1200" "1440x900" "1280x1024" "1280x960"
"1200x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
       Depth       15
       Modes      "1600x1200" "1440x900" "1280x1024" "1280x960"
"1200x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
       Depth       16
       Modes      "1600x1200" "1440x900" "1280x1024" "1280x960"
"1200x800" "1024x768" "800x600" "640x480"
   EndSubSection
   SubSection     "Display"
       Depth       24
       Modes       "1200x800"
   EndSubSection
EndSection

```

---

### Post by OmegaMB on 2007-08-10
I've edited that file, yet those resoulutions are still not available.

---

### Post by Billy the Kid on 2007-08-10
You should be able to set your screen resolution by running: sudo dpkg-reconfigure xserver-xorg

---

### Post by Troubled on 2007-08-10
OmegaDB:
I have had the *exact* same problem and had the *exact* same solution suggested to me.
Needless to say, it was time-consuming and ineffective.

However, after some searching, I managed to find a solution that was extremely simple and wondered why nobody told me that in the first place.
[SIZE="2"][b]
Simply open Synaptic and look at the list of packages that shows up immediately.
Install "915resolution" and voila, you're done![/b][/SIZE]

You can also do this via the command line by typing:
```
sudo apt-get install 915resolution
```

---

