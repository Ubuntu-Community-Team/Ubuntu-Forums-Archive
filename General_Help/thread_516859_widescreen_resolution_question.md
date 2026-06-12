---
title: "widescreen resolution question"
date: 2007-08-03
forum: General Help
---

### Post by Lepht on 2007-08-03
Can Wubi support widescreen resolutions like 1440X900? I have Wubi installed and running, however, the max screen reso is at 1024X768.

I have tried    cat /etc/X11/xorg.conf, and modified it into by only adding the 1440x900 after the modes, like this:

SubSection "Display"
Depth 1
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1024x768" "800x600" "640x480"
EndSubSection

Still, the 1440X900 still does not show up under screen resolution.

Any ideas? please help out...

---

### Post by Lepht on 2007-08-03
Here are some specs:

30-81 Horizontal Sync
56-75 Vertical Refresh
1440x900 @ 60 Preferred resolution
VESA 75 modes compliant

---

### Post by dougfractal on 2007-08-03
(your 2nd post came when writing this)

I think for some reason ubuntu is not detecting you monitor model

google search your monitor spec and add in the HorizSync and  VertRefresh  values.

backup
```

sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.`date +%Y%m%d`
```

so ```
sudo gedit /etc/X11/xorg.conf
```
```
Section "Monitor"
   Identifier   "monitor0"

   HorizSync    30 - 81
   VertRefresh  56 - 75
   Option       "DPMS"
EndSection
```


also change in the Section "Screen"

   >  Monitor        "monitor0"

restart X
```
sudo /etc/init.d/gdm restart
```


There is always a risk of X not starting if a setting is wrong.

**troubleshoot**
[ctrl+alt+f1] 
```
sudo cp /etc/X11/xorg.conf.`date +%Y%m`* /etc/X11/xorg.conf
```
sudo /etc/init.d/gdm restart[/CODE]

---

### Post by dougfractal on 2007-08-03
Assuming you have the right graphic drivers installed.

Your  specs:
30-81 Horizontal Sync
56-75 Vertical Refresh
seem low, they are the same as mine which is 1280x1024

so check you monitor specs again!


here someone's 1440x900 xorg stuff
[http://ubuntuforums.org/showthread.php?t=280683](http://ubuntuforums.org/showthread.php?t=280683)

```
Section "Monitor"
Identifier "SyncMaster"
VendorName "Samsung" 
ModelName "SyncMaster 940BW" 
HorizSync 25-100
VertRefresh 30-90 
Option "DPMS"
Modeline "1440x900@60" 108.84 1440 1472 1880 1912 900 918 927 946
EndSection
```

```
Section "Screen"
Identifier "Default Screen"
Device "Default Device"
Monitor "SyncMaster"
DefaultDepth 24
SubSection "Display"
Depth 1
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 4
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 8
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 15
Modes "1440x900" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 16
Modes "1440x900" "1440x864" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
SubSection "Display"
Depth 24
Modes "1440x900" "1400x800" "1220x768" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
EndSubSection
EndSection
```

---

### Post by Lepht on 2007-08-03
Before I do anything, let me just post my code here:

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
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
        Load    "vbe"
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
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "nVidia Corporation G71 [GeForce 7300 GS]"
        Driver          "nv"
        BusID           "PCI:1:0:0"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        HorizSync       28-51
        VertRefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation G71 [GeForce 7300 GS]"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1440x900" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

and here is the mon: [http://www.samsung.com/ph/products/monitor/lcdmonitor/931bw.asp?page=Specifications](http://www.samsung.com/ph/products/monitor/lcdmonitor/931bw.asp?page=Specifications)

---

### Post by tuxcantfly on 2007-08-03
Also, if you're using an nvidia card, make sure to install the nvidia driver (use the restricted-manager); the nv one supports only a very limited amount of resolutions; the same applies to ati and the fgrlx drivers.

---

### Post by Lepht on 2007-08-03
Thanks doug it worked! you the man!

Also, tuxcantfly, thanks for the reply as well.

---

### Post by dougfractal on 2007-08-03
Never found out the model of your monitor?
was it HorizSync 25-100 VertRefresh 30-90 ?

It's good to post the values as google will find it later.

---

### Post by Lepht on 2007-08-03
The Specs and the model name/# were inside this link:

[http://www.samsung.com/ph/products/monitor/lcdmonitor/931bw.asp?page=Specifications](http://www.samsung.com/ph/products/monitor/lcdmonitor/931bw.asp?page=Specifications)

---

### Post by carlsberg on 2008-02-03
i'm having the same problem but i really don't understand what i need to do

i have just installed ubuntu using Wubi - really good, it installed like a dream but i'm stuck with a 640x480 resolution whereas my screen has a 1440 width like the earlier post in this thread 

i have absolutely no experience with ubuntu

i see i need to modify a config file but i did a search and couldn't find it - is there a simpler way ?

thanks

---

