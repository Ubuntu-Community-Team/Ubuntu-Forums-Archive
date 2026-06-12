---
title: "Screen res &amp; nvidia driver"
date: 2008-05-20
forum: General Help
---

### Post by Bailey321 on 2008-05-20
My query is not totally related to this but instead of making a new thread....

Basically i have made the switch to ubuntu and everything is pretty much running fine, one problem is my screen resolution it has no option to select 1280x1024 the highest i can go is 1280x768. I also kinda get the feeling my graphic card is not being utilissed correctly, i have installed the nvidia driver that came up in the toolbar i have also used this thread [http://ubuntuforums.org/showthread.php?t=183132](http://ubuntuforums.org/showthread.php?t=183132) to edit /etc/X11/xorg.conf as follows...

```
Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "gb"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
EndSection

Section "Device"
        Identifier      "Configured Video Device"
        Driver          "nvidia"
        Option          "NoLogo"        "True"
EndSection
Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
        Defaultdepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480" "640x350"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
EndSection
Section "Module"
        Load            "glx"
EndSection
```

This has not fixed the problem, my graphic card is Leadtek WinFast GeForce 7600 GS...Any ideas are welcome.....

---

