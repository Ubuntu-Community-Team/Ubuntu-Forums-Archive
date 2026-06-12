---
title: "XServer crash"
date: 2007-05-27
forum: General Help
---

### Post by rishabh on 2007-05-27
Hi there,

I'm using UbuntuStudio 7.04 on a 160Gig HDD running on 1Gb RAM with a MSI K8NGM2 motherboard (onboard GeForce 6150)

Today I observed that every five minutes or so, there were freezes, some long, some short. And after one of these freezes, I get the grey box on blue background saying that the X Server had crashed.
So what do I do? Go to tty1 and try re-installing the "nvidia-glx" driver package. 
Only to be informed that "/var/lib/dpkg/lock" and a few other similar files were read-only! I tried the same thing while chrooting from the Breezy LiveCD, and it works fine there! I even installed elinks while chrooting, and it says that I don't have privileges to write to my Home directory!
(And the X server still doesn't work)

Also, for some reason, chmodding isn't working. When I chmod 755 "/var/lib/dpkg", it keeps saying "Changing permissions... :Read only".

Any idea what's gone wrong?

---

### Post by bung33 on 2007-05-28
You are obviously having trouble with permissions right now, so until you can fix the x server, I would sudo everything or just login as root to begin with. As to the x server crashing, reinstalling the graphics driver may or may not help. Post the contents of your x configuration file so I can check for changes...

```
sudo cat /etc/X11/xorg.conf
```

---

### Post by rishabh on 2007-05-28
Here:


--------------------------------------------------------------------------

Section "Files"
        Fontpath        "/usr/share/fonts/X11/misc"
        Fontpath        "/usr/share/fonts/X11/cyrillic"
        Fontpath        "/usr/share/fonts/X11/100dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/75dpi/:unscaled"
        Fontpath        "/usr/share/fonts/X11/Type1"
        Fontpath        "/usr/share/fonts/X11/100dpi"
        Fontpath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        Fontpath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load            "i2c"
        Load            "bitmap"
        Load            "ddc"
        Load            "extmod"
        Load            "freetype"
        Load            "glx"
        Load            "int10"
        Load            "vbe"
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
        Option          "Device"        "/dev/input/mice"
        Option          "Protocol"      "ImPS/2"
        Option          "ZAxisMapping"  "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "stylus"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "eraser"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"  "cursor"
        Option          "ForceDevice"   "ISDV4"# Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "Generic Video Card"
        Driver          "nvidia"
        Busid           "PCI:0:5:0"
        Option          "AddARGBVisuals"        "True"
        Option          "AddARGBGLXVisuals"     "True"
        Option          "NoLogo"        "True"
EndSection

Section "Monitor"
        Identifier      "Generic Monitor"
        Option          "DPMS"
        Horizsync       28-51
        Vertrefresh     43-60
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "Generic Video Card"
        Monitor         "Generic Monitor"
        Defaultdepth    24
        SubSection "Display"
                Depth   1
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   4
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   8
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   15
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   16
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
        SubSection "Display"
                Depth   24
                Modes           "1024x768"      "800x600"       "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
  screen "Default Screen"
        Inputdevice     "Generic Keyboard"
        Inputdevice     "Configured Mouse"
        Inputdevice     "stylus"        "SendCoreEvents"
        Inputdevice     "cursor"        "SendCoreEvents"
        Inputdevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection

--------------------------------------------------------------------------


Find anything?

---

### Post by rishabh on 2007-05-28
And here's my fstab. Does the "ro" part signify "Read-Only"?

```
# /etc/fstab: static file system information.
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc                                       /proc           proc         defaults                      0  0
# /dev/sda1
UUID=b52d8691-100c-4135-9ffa-2a2c8b867bfb  /               ext3         defaults,errors=remount-ro    0  1
# /dev/sda3
UUID=9cba5774-adf1-49f1-b6b0-ef54b997b5a7  none            swap         sw                            0  0
/dev/hda                                   /media/cdrom0   udf,iso9660  user,noauto                   0  0
/dev/hdb                                   /media/cdrom1   udf,iso9660  user,noauto                   0  0
/dev/fd0                                   /media/floppy0  auto         rw,user,noauto                0  0
/dev/sda5                                  /media/Storage  ext2         owner,errors=remount-ro,user  0  0
/dev/sda6                                  /media/Media    ext2         owner,errors=remount-ro,user  0  0
```

---

### Post by rishabh on 2007-05-29
I've identified the problem. Apparently the root fs was being mounted in Read-only mode. ;)
Thanks for the help anyway. :D

:popcorn:

---

### Post by bung33 on 2007-05-29
Glad you found the solution. Your x configuration file looks fine by the way...

---

### Post by rishabh on 2007-05-29
The X is fine, my topic name was wrong. There was an option in fstab that said "errors=remount-ro". I just removed that line. :D

---

