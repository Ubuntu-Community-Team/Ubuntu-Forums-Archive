---
title: "Got nvidia driver working in 7.04... just no 3d suporrt..."
date: 2007-04-28
forum: General Help
---

### Post by noenter1 on 2007-04-28
As the title says. I got it working with 2 different ways but for some reason neither has 3d support. The 3d desktop effects work(default ones under the sys preference) but the 3d test in cedega fail and any 3d games wont start. Used Envy and installed manually. I have a geforce 8800 GTX and its hooked up to a 40 inch LCD tv via VGA cable. Here is my xorg.conf:
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
    Load           "i2c"
    Load           "bitmap"
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
    Identifier     "Generic Monitor"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation G80 [GeForce 8800 GTX]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation G80 [GeForce 8800 GTX]"
    Monitor        "Generic Monitor"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1360x768" "1024x768" "800x600" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection 
```
Sorry if this is posted elsewhere i searched before i posted. Any help appreciated.

---

### Post by fragos on 2007-04-28
What does "glxinfo |grep rendering" say?

---

### Post by noenter1 on 2007-04-29
direct rendering: Yes
However when i type in glxgears my computer freezes then restarts.

Edit: I already tried installing the nvidia driver thru the restricted drivers manager, however it keeps wanting to install the legacy drivers

---

### Post by fragos on 2007-04-29
Very strange.  The only thing I can think of is the version of Nvidia driver you're running.  I prefer to use the drivers from the Ubuntu repositories.  I use nvidia-glx for my FX5200.  You might need nvidia-glx-new but I'm not sure.  Synaptic notes did mention Geforce4 needs nvidia-glx.  I don't remember where in the Ubuntu site but there is a detailed list that matched driver version to chip set.  I suggest to research that angle.

---

### Post by Nythain on 2007-04-29
not sure how new that card is, but it sounds pretty new, try the nvidia-glx-new driver... 
as for cedega... HAHA... i have NEVER passed the 3d test... aparently its very picky... i know my 3d works, and my games run, but that test will forever tell me they shouldnt.

---

### Post by Churnd on 2007-04-29
Did you edit the xorg.conf manually?  Some of the lines look out of place to me... more specifically these:

    Option         "AddARGBVisuals" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "NoLogo" "True"

I'm pretty sure they're supposed to be under "device" and not "screen", but I may be wrong, or that may not matter.

---

### Post by noenter1 on 2007-04-29
Got it almost working now Those options were in the wrong plae. I didnt even notice that till you said somethong thanks. glxgears works now without freezing my comp up. Now its trying to tell me that my graphics card doesn't have dual-TMU support.

---

### Post by spankymasterc on 2007-04-29
mine also fails the 3d support in cedega but i could still launch my games....

---

### Post by noenter1 on 2007-04-29
Ok got it fixed, there were a few lines missing from the xorg file. Go figure the installer did configure it correctly.

---

### Post by RobinOfSweden on 2007-05-06
What lines was missing? it sure would help me that has the same error yet cant seem to find how to fix it :P

Thank you.

---

### Post by noenter1 on 2007-05-08
First all the options should be under the device section, second lines these were missing:
```
Option         "RenderAccel"		"true"
Option         "TripleBuffer"               "true"
```

---

