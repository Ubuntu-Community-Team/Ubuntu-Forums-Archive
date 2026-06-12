---
title: "Need hel with graphic card setting"
date: 2007-02-13
forum: General Help
---

### Post by Xmanster on 2007-02-13
I instaled my graphic card Geforce 7600 GS, but there a probleme in the screen frequnecy it set as default 75 Hz i want to change it to 70 coz i have light waves in my screen and it's hurting my eyes, before instaling the card i can change the frequemcy but after with the new Nvidia , cant

thanks

---

### Post by renzokuken on 2007-02-13
open the xorg.conf

```
sudo gedit /etc/X11/xorg.conf
```

scroll down to near the bottom and look for the frequency setting, change it to 70, save the file and exit, then press Ctrl+Alt+backspace to restart X

---

### Post by Xmanster on 2007-02-13
Thanks for your quick respond .
i look up but i dont found it, this is my xorg.conf

```
Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
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
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc105"
    Option         "XkbLayout" "us"
    Option         "XkbOptions" "lv3:ralt_switch"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "stylus"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "stylus"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "InputDevice"

                                                      # /dev/input/event
                                                      # for USB
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/wacom"          # Change to 
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"               # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "DELL E173FP"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DELL E173FP"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection


```

---

### Post by renzokuken on 2007-02-13
hehe, oops, thought i saw i saw it in my xorg.conf..........

i think you can change the resolutions to say

```

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "DELL E173FP"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024[color=red]@70[/color]" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024[color=red]@70[/color]" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024[color=red]@70[/color]" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024[color=red]@70[/color]" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024[color=red]@70[/color]" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024[color=red]@70[/color]" "1152x864" "1024x768" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

```

but dont quote me on it do some research first, i may have the syntax wrong...........if you do want to try it backup your current xorg.conf first

```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf_backup
```
then if it fucks up simply do 
```
sudo cp /etc/X11/xorg.conf_backup /etc/X11/xorg.conf
```
to restore the old one

you could also try

```
sudo dpkg-reconfigure xserver-xorg
```

and see if that gives you any frequency options

---

### Post by Xmanster on 2007-02-13
i did and ctrl+alt+backspace, and the resolution 1280x1024 was removed from the Screen Resolution Preference , and was set as 1152x864 Frequency still 75.

---

### Post by renzokuken on 2007-02-13
ok so that didnt work..........

open up your xorg.confg again and remove all the "@70" you just put in, then try this

go to the Section Monitor bit and change it from this

```

Section "Monitor"
    Identifier     "DELL E173FP"
    Option         "DPMS"
EndSection

```

to this

```

Section "Monitor"
    Identifier     "DELL E173FP"
    Option         "DPMS"
    [color=red]HorizSync     31.5 - 57.0[/color]
    [color=red]VertRefresh  50.0 - 70.0[/color]
EndSection

```

those are fairly standard values for refresh rates but you should check with your monitors manual the correct values..........using the wrong ones can potentially damage it

EDIT: i just found this [http://ubuntuforums.org/showthread.php?t=176998](http://ubuntuforums.org/showthread.php?t=176998) it may help.......its basically what i said above but using the _ instead of an @ ....... said i probably had the syntax wrong

.

---

### Post by Xmanster on 2007-02-13
Thansk you very much , it work at mode : 60 as default , its much better, 
70 cant be i  try it only 60,but as i said much better
thank u for the help

take care

---

### Post by renzokuken on 2007-02-13
no trubs, good luck

---

