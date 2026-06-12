---
title: "Xine/Kaffeine using Xv crashes playing DVD &amp; xorg.conf help"
date: 2006-12-19
forum: General Help
---

### Post by LadFromWales85 on 2006-12-19
Hello all! (again)

My (K)Ubuntu system still appears to be functioning normally while on the desktop, not having any serious problems, apart from the sudden inability to use Xv in Xine to play DVD's.  Xine will quite happily use Xv to play AVI's and Quicktime movies, but crashes as soon as the DVD spins up.  In the console I see this:-
```

libdvdread: Attempting to retrieve all CSS keys
libdvdread: This can take a _long_ time, please be patient
.......
received X error event: BadMatch (invalid parameter attributes)
X Error: BadMatch (invalid parameter attributes) 8
  Major opcode:  141
  Minor opcode:  17
  Resource id:  0x2e0000d
kaffeine: Fatal IO error: client killed
ICE default IO error handler doing an exit(), pid = 7834, errno = 9
Unable to start Dr. Konqi

```

The DVD will play if I select the opengl driver, but I sometimes have issues with scaling the image up to full screen.  It did work fine before, but a recent aptitude upgrade caused among other things, my xorg.conf to be re-written.  I do not have a copy of this re-written xorg.conf, as I replaced it with my backup, as the re-written one dropped my resolution and broke fglrx.

I want to correct my xorg.conf file, but I don't think I'm man enough to do it alone (yet!).  I am very happy working in a Linux environment, but I don't really know what to do with my xorg.conf file.  I've modified bits here and there to get my mouse working, but thats it:-
```

Section "ServerLayout"
        Identifier     "Default Layout"
        Screen      0  "aticonfig-Screen[0]" 0 0
        InputDevice    "Keyboard[0]"
        InputDevice    "Mouse[1]"
EndSection

Section "Files"

        # path to defoma fonts
        FontPath     "/usr/share/X11/fonts/misc"
        FontPath     "/usr/share/X11/fonts/cyrillic"
        FontPath     "/usr/share/X11/fonts/100dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/75dpi/:unscaled"
        FontPath     "/usr/share/X11/fonts/Type1"
        FontPath     "/usr/share/X11/fonts/100dpi"
        FontPath     "/usr/share/X11/fonts/75dpi"
        FontPath     "/usr/share/fonts/X11/misc"
        FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load  "i2c"
        Load  "bitmap"
        Load  "ddc"
        Load  "dri"
        Load  "extmod"
        Load  "freetype"
        Load  "glx"
        Load  "int10"
        Load  "type1"
        Load  "vbe"
EndSection

Section "InputDevice"
        Identifier  "Keyboard[0]"
        Driver      "kbd"
        Option      "CoreKeyboard"
        Option      "XkbRules" "xorg"
        Option      "XkbModel" "logidmd"
        Option      "XkbLayout" "gb"
EndSection

Section "InputDevice"
        Identifier  "Mouse[1]"
        Driver      "mouse"
        Option      "CorePointer"
        Option      "Protocol" "auto"
        Option      "Device" "/dev/input/mice"
        Option      "Resolution" "1200"
        Option      "Buttons" "12"
        Option      "ZAxisMapping" "4 5 7 6"
EndSection

Section "Monitor"
        Identifier   "DELL 2405FPW"
        Option      "DPMS"
EndSection

Section "Monitor"
        Identifier   "aticonfig-Monitor[0]"
        Option      "VendorName" "ATI Proprietary Driver"
        Option      "ModelName" "Generic Autodetecting Monitor"
        Option      "DPMS" "true"
EndSection

Section "Device"
        Identifier  "ATI Technologies, Inc. ATI Default Card"
        Driver      "vesa"
        BusID       "PCI:5:0:0"
EndSection

Section "Device"
        Identifier  "aticonfig-Device[0]"
        Driver      "fglrx"
        Option      "VideoOverlay" "on"
        Option      "OpenGLOverlay" "off"
EndSection

Section "Screen"
        Identifier "Default Screen"
        Device     "ATI Technologies, Inc. ATI Default Card"
        Monitor    "DELL 2405FPW"
        DefaultDepth     24
        SubSection "Display"
                Depth     1
                Modes    "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     4
                Modes    "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     8
                Modes    "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     15
                Modes    "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     16
                Modes    "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth     24
                Modes    "1680x1680" "1600x1200" "1280x1024" "1152x864" "1024x768" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "Screen"
        Identifier "aticonfig-Screen[0]"
        Device     "aticonfig-Device[0]"
        Monitor    "aticonfig-Monitor[0]"
        DefaultDepth     24
        SubSection "Display"
                Viewport   0 0
                Depth     24
        EndSubSection
EndSection

Section "DRI"
        Mode         0666
EndSection

Section "Extensions"
        Option      "Composite" "Disable"
EndSection

```

I have a Dell 2405FPW 24" Widescreen monitor, which works fine at 1920x1200 at the moment, but I think thats because xorg is autodetecting.  Does anything need to be done to tell xorg that my monitor is widescreen...I'm sure I read that xorg likes to know things like how large the screen is etc.

Any help would be appreciated!  Hopefully some day I'll be helping too! :D

---

### Post by LadFromWales85 on 2006-12-20
Anyone? :)

---

### Post by LadFromWales85 on 2006-12-22
No one at all!? :(

I experience texture rip when using the opengl driver, so i'd really like to get back to using Xv to play DVD's :)

---

### Post by LadFromWales85 on 2006-12-28
:( :( Someone?

---

