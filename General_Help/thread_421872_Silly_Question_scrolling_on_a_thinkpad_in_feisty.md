---
title: "Silly Question: scrolling on a thinkpad in feisty"
date: 2007-04-24
forum: General Help
---

### Post by Tomshaq on 2007-04-24
I recently upgraded to 7.04 on a t41p thinkpad and now scrolling using the side of the touchpad does not work. It was working before and it seems odd that it would not work now. any suggestions?

---

### Post by jputman01 on 2007-04-24
I had this issue too, it was working fine then i switched to feisty beta and it no longer worked, then when full version of feisty came out it didnt work until i installed my nvidia driver thru the restricted drivers manager. Have you installed any restricted drivers? 

also in your xorg.conf what does it list for your pointing device? when mine wasn't working it listed 
```
device "configured mouse"
driver "mouse" (or something to that effect)
```

when it was fixed (and what is says now) it said
```
device "synaptic touchpad"
driver "synaptics"
```

check your xorg.conf and paste the output if you can

---

### Post by Tomshaq on 2007-04-24
Thanks for your response.

I have not installed any restricted drivers.

here is what my xorg.conf file reads:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

I definitely think that needs to be changed. Is there a way to do this automatically or should I just back it up and try and copy what you have?

Thanks,
Tomshaq

---

### Post by jputman01 on 2007-04-24
> **Tomshaq said:**
> Thanks for your response.

I have not installed any restricted drivers.

here is what my xorg.conf file reads:
```

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ExplorerPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

```

I definitely think that needs to be changed. Is there a way to do this automatically or should I just back it up and try and copy what you have?

Thanks,
Tomshaq

if you feel comfortable you could back it up and try changing it, i did this and it killed my xorg.conf but i just changed it back and was fine. have you downloaded the synaptics gui? it would be under system->preferences i believe, and would say something about the "touchpad" (sorry im not at my laptop). 

anyways if you go to system-> preferences and dont see anything about the touchpad where you can change settings try downloading gsynaptics via package manager or apt-get first

---

### Post by jputman01 on 2007-04-24
im about to get off work in a sec and i can post my xorg when i get home later if you want to see it compaired to yours

---

### Post by 50words on 2007-04-24
My scrolling on my ThinkPad using the touchpad works fine, but I can't scroll using the middle button for the pointing stick. Any idea how to engage that?

---

### Post by strabes on 2007-04-24
> I can't scroll using the middle button for the pointing stick

Care to explain what you mean by that? I don't exactly understand.

Tomshaq: Post the output of this command: ```
cat /etc/X11/xorg.conf
```

---

### Post by 50words on 2007-04-24
Here is a picture: [http://www.laptopworld.dk/assets/images/ThinkPad%20T60/Trackpoint.jpg](http://www.laptopworld.dk/assets/images/ThinkPad%20T60/Trackpoint.jpg)

The middle button, when pressed, lets you scroll with the trackpoint pointing stick. As far as I can tell, Ubuntu doesn't recognize the existence of that button. (Actually, no, I just realized it uses it as a "paste" button. Weird.)

I also tried switching the trackpad to left-handed use, but Ubuntu then changes a pad tap to a context-menu click, which is annoying. I want it to be the primary click. Is there a way to get more details options for trackpoint/trackpad controls?

---

### Post by 50words on 2007-04-24
Aha! Here are some solutions!
[http://www.linux.org.mt/node/82#AEN222](http://www.linux.org.mt/node/82#AEN222)

Edit: Nevermind; didn't work.

---

### Post by Tomshaq on 2007-04-27
I though I had fixed it, but apparantly not. here is my entire xorg.conf now:

```

Section "Files"
        FontPath        "/usr/share/X11/fonts/misc"
        FontPath        "/usr/share/X11/fonts/cyrillic"
        FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath        "/usr/share/X11/fonts/Type1"
        FontPath        "/usr/share/X11/fonts/100dpi"
        FontPath        "/usr/share/X11/fonts/75dpi"
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
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
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
        Identifier      "Synaptics Touchpad"
        Driver          "synaptics"
        Option          "SendCoreEvents"        "true"
        Option          "Device"                "/dev/psaux"
        Option          "Protocol"              "auto-dev"
        Option          "HorizScrollDelta"      "0"
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
        Identifier      "ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
        Driver          "ati"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. M10 NT [FireGL Mobility T2]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1400x1050"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1400x1050"
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
        InputDevice     "Synaptics Touchpad"
EndSection

Section "DRI"
        Mode    0666
EndSection

```

Any other suggestions?

BTW, I did get gsynaptics, but it won't run, telling me something about SHMconfig. I tried to add this to the code, but it still wouldn't run.:lolflag:

---

