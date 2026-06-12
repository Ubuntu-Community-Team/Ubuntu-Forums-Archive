---
title: "Login screen resolution different from desktop resolution"
date: 2007-06-29
forum: General Help
---

### Post by ciphermonk on 2007-06-29
Weird issue the more that I look at it. The desktop is using the entire screen 1440x900 but the login screen is only using what appears to be 1024x768. When I look at the Display config under System, Administration, Display it's showing the resolution is 1024x768. This seems to be what the login screen is going but, but the gnome desktop appears to be running at 1440x900. Any of you seen this kind of issue before?

---

### Post by MCSE_Crossover on 2007-06-29
Perhaps this is related...

[http://ubuntuforums.org/showthread.php?p=2935061#post2935061](http://ubuntuforums.org/showthread.php?p=2935061#post2935061)

Otherwise, can you post the output from your /etc/X11/xorg.conf file?

---

### Post by ciphermonk on 2007-06-29
Section "ServerLayout"
        Identifier     "single head configuration"
        Screen      0  "Screen0" 0 0
        InputDevice    "Keyboard0" "CoreKeyboard"
        InputDevice    "Synaptics" "CorePointer"
EndSection

Section "InputDevice"
        Identifier  "Keyboard0"
        Driver      "kbd"
        Option      "XkbModel" "pc105"
        Option      "XkbLayout" "us"
EndSection

Section "InputDevice"
        Identifier  "Synaptics"
        Driver      "synaptics"
        Option      "Device" "/dev/input/mice"
        Option      "Protocol" "auto-dev"
        Option      "Emulate3Buttons" "yes"
EndSection

Section "Monitor"
        Identifier   "Monitor0"
        ModelName    "LCD Panel 1440x900"
        HorizSync    31.5 - 100.0
        VertRefresh  59.0 - 75.0
        Option      "dpms"
        Modeline "1440x900"  106.47  1440 1520 1672 1904  900 901 904 932  -HSync +Vsync
EndSection

Section "Device"
        Identifier  "Videocard0"
        Driver      "intel"
EndSection

Section "Screen"
        Identifier "Screen0"
        Device     "Videocard0"
        Monitor    "Monitor0"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
                Modes "1440x900" 
        EndSubSection
EndSection

---

### Post by Undertak2000 on 2007-07-25
I had that problem, and I have since reinstalled Ubuntu Feisty.

To fix the issue, you must find an original xorg.conf file and revert to that, instead of the one that nvidia-glx makes for you in the nvidia settings.  Then, click save to xorg.conf, but instead of saving it, only copy the new resolutions to the monitor section of xorg.conf.

Something that nvidia-settings does in xorg.conf messes everything up.  Now that I've reverted back, my graphics are running smoothly.

Remember to backup xorg.conf before changing it!

---

