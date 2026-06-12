---
title: "How to modify, test, and debug xorg.conf for using multiple video devices. (egpu)"
date: 2015-08-23
forum: General Help
---

### Post by Paul_Jewell on 2015-08-23
Hello, I have been struggling on and off to get a second video card to work on ubuntu. While I have not had success with this on many setups, my current attempted usage is with a laptop computer and an external desktop GPU. The laptop is a lenovo x220 tablet, and for the gpu I have tried an old ATI card (forgot model), an AMD HD6950, and a nvidia 8800GT. I use one of the many available pci-express > pciex16 risers/adapters available, using a standard atx power supply to provide the required wattage. I have confirmed that all three mentioned video cards work correctly under windows 7 in the described setup. 


I would like to be able to either swap from the external video card to intel onboard (for docked or undocked usage), or just use both gpus and enable/disable the external gpu. I would prefer to switch displays without having to close all open programs, though I understand that this is considered generally unsupported at this time. 


So far, I have been told by many sources (mainly on ubuntu IRC) that I should be able to be able to make the switch by modifying xorg.conf and restarting lightdm. This stratagy seems like an ideal starting point. So far, none of my manual xorg.conf changes have been remotely successful. Each time I get a black screen and I just revert and restart lightdm again. (if I am lucky enough that ctrl+alt+fX still switches to another TTY) I will post one example I have attempted below, but I doubt it is any good, as it consists of various copy+pasted examples put together, and no one on IRC has stepped up to point me to a good, current, and comprehensive resource for writing an xorg.conf for this purpose after I asked directly. I also can not get a good starting point for writing the file, as what is usually suggested, "$ X --configure", fails with the following error, with or without the external card attached: "Xorg: Number of created screens does not match number of detected devices". Searching for information on this specific error brings results from unrelated situations which have not helped me. 


When trying to work with the various video cards, driver wise things seem to work well: all of the cards show up immedietly in lspci, however beyond that things get flakey: the amd/ati cards I could not get to output anything at all, even with fglrx. With the nvidia card, using the closed-source driver managed to get one monitor working (disabled intel chip completely), but caused many other graphical glitches in the desktop environment - I would prefer to use the open-source driver if possible. It took many tutorials and a long time to completely uninstall the glitchy closed-source driver and restore usual functionality. 


I hope I have not been too descriptive and long winded in my post. I am looking for help to do the following:


-automatically configure a second video card, if possible, OR, 
-write an xorg.conf file correctly, and properly debug the configuration, so that I do not just get a black screen, but a specific error which I can fix. 


Thank you for reading. 

```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "Screen0" 0 0
    Screen      1  "Screen1" RightOf "Screen0"
    InputDevice    "Mouse0" "CorePointer"
    InputDevice    "Keyboard0" "CoreKeyboard"
EndSection


Section "Files"
    ModulePath   "/usr/lib/xorg/modules"
    FontPath     "/usr/share/fonts/X11/misc"
    FontPath     "/usr/share/fonts/X11/cyrillic"
    FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
    FontPath     "/usr/share/fonts/X11/Type1"
    FontPath     "/usr/share/fonts/X11/100dpi"
    FontPath     "/usr/share/fonts/X11/75dpi"
    FontPath     "built-ins"
EndSection


Section "Module"
    Load  "glx"
EndSection


Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection


Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection


Section "Monitor"
    Identifier   "Monitor0"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection


Section "Monitor"
    Identifier   "Monitor1"
    VendorName   "Monitor Vendor"
    ModelName    "Monitor Model"
EndSection




Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz",
        ### <percent>: "<f>%"
        ### [arg]: arg optional
        #Option     "SWcursor"               # [<bool>]
        #Option     "kmsdev"                 # <str>
        #Option     "ShadowFB"               # [<bool>]
    Identifier  "Card0"
    Driver      "modesetting"
    BusID       "PCI:0:2:0"
EndSection




Section "Device"
    Identifier     "Card1"
    Driver "nouveau"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 8800 GT"
    BusID          "PCI:5:0:0"
    Option         "NoLogo" "1"
    Option         "Coolbits" "13"
EndSection




Section "Screen"
    Identifier "Screen0"
    Device     "Card0"
    Monitor    "Monitor0"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


Section "Screen"
    Identifier "Screen1"
    Device     "Card1"
    Monitor    "Monitor1"
    SubSection "Display"
        Viewport   0 0
        Depth     1
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     4
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     8
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     15
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     16
    EndSubSection
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection

```

---

### Post by Bashing-om on 2015-08-30
Paul_Jewell; Hello;

Mind you, upfront, I am not too well versed in what you want to do. But I do think that to switch between graphic sets; one at the least will have to swap between xorg.conf files.

MAFoElffen has a mega thread on graphics sets. and in this thread is a tutorial to set up alternate xorg.conf files.

A long informative read:
[http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86](http://ubuntuforums.org/showthread.php?t=1743535&highlight=i915&page=86)

[INDENT][INDENT]not much help
[INDENT][INDENT][INDENT]a push in the right direction
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

