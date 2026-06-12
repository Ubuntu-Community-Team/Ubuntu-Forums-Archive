---
title: "X server crashes in edgy"
date: 2006-11-07
forum: General Help
---

### Post by Ramses de Norre on 2006-11-07
It seems my x server keeps crashing every now and then on edgy, it just happened again with no apparent reason..
There are no serious errors in ~/.xsession-errors and /var/log/Xorg.0.log.old only contains this relevant info: ```
Backtrace:
0: /usr/X11R6/bin/X(xf86SigHandler+0x81) [0x80c3971]
1: [0xffffe420]
2: /usr/X11R6/bin/X(ProcFreeGC+0x98) [0x8081038]
3: /usr/X11R6/bin/X(Dispatch+0x18f) [0x808693f]
4: /usr/X11R6/bin/X(main+0x485) [0x806e715]
5: /lib/tls/i686/cmov/libc.so.6(__libc_start_main+0xdc) [0xb7d6a8cc]
6: /usr/X11R6/bin/X(FontFileCompleteXLFD+0xa1) [0x806da51]

Fatal server error:
Caught signal 11.  Server aborting
```

I'm not sure what to think about it..
I have an ati x600 with the fglrx driver, this is my xorg.conf:
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
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "be"
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

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "stylus"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "eraser"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

#Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "cursor"
#  Option        "Device"        "/dev/wacom"          # Change to 
#                                                      # /dev/input/event
#                                                      # for USB
#  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"               # Tablet PC ONLY
#EndSection

Section "Device"
        Identifier      "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
        Driver          "fglrx"
        Option          "UseFBDev" "true"
        Option          "VideoOverlay" "on"
        Option          "OpenGLOverlay" "off"
        Option          "DesktopSetup"  "0x00000000"    #single
        BusID           "PCI:1:0:0"
##Enable following line if XGL locks up
#       Option          "KernelModuleParm"      "agplock=0"
EndSection

Section "Extensions"
        Option  "Composite"     "0"
#       Option  "RENDER"        "Enable"
EndSection



#Section "Extensions"
#       Option          "Composite"     "Enable"
##      Option          "RENDER"        "Enable"
#EndSection

Section "Monitor"
        Identifier      "LM17A"
        Option          "DPMS"
        Modeline "1280x1024" 109.62  1280 1336 1472 1720  1024 1024 1026 1062
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "ATI Technologies, Inc. RV370 5B62 [Radeon X600 (PCIE)]"
        Monitor         "LM17A"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "832x624" "800x600" "720x400" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
#       InputDevice     "stylus" "SendCoreEvents"
#       InputDevice     "cursor" "SendCoreEvents"
#       InputDevice     "eraser" "SendCoreEvents"
EndSection

Section "ServerFlags"
        Option  "AIGLX" "off"
EndSection

Section "DRI"
        Mode    0666
EndSection
```

I also have kernel panics sometimes, no idea whether these could be related to the x crashes, I haven't been able to backtrace the panics yet.
(I'll watch them carefully if they appear again..)


Oh another X related issue: when I either restart X (ctrl-alt-backspace or logout and kill gdm) or just log out from gdm, gnome-session wont start again.., not through gdm and neither through startx. It gets to the coloured background but the splash image never appears and the machine shows no activity..
Only thing I can do then is reboot..

Very rarely I am able to login again but mostly it goes as above..

---

### Post by makhand on 2006-11-11
I have pretty much the same problems and the same errors. I've tried doing all kinds of things. This is very very frustrating. I did a full reinstall to try to fix the problem but nothing. There seem to be a bunch of irregularities. 

i can sort of get a working system if i change the session to X-terminal in gdm, then start metacity and gnome-panel.

however, I've just discovered that i cant use OpenOffice. it makes X crash upon starting.

like i said, this is incredibly frustrating. 
I'm using i810

someone, please help.

---

### Post by Ramses de Norre on 2006-11-11
I'm now using the i386 kernel after a lot of kernel panics with the generic one and I haven't got any panics nor X crashes yet, so I hope the problem is solved for me..
I guess there is so much bloat in the generic kernel that it's just a lot less stable then the much lighter i386 one.

You might want to try the same thing, I don't now whether the X crashes are really related but they didn't occur again..

---

### Post by makhand on 2006-11-11
Did you uninstall the generic then? When I click on 686 (which is what I've used with prev versions of linux), it says its obsoleted by generic.

---

### Post by Ramses de Norre on 2006-11-11
i686 and k7 are replaced by generic, I'm using i386 now, that's the only other kernel besides the generic and the server one.

---

### Post by n8bounds on 2006-11-19
> **Ramses de Norre said:**
> i686 and k7 are replaced by generic, I'm using i386 now, that's the only other kernel besides the generic and the server one.

Yeah I noticed.  I have the same problems.  I installed the 386 kernel and X would never start, claiming ignorance of my nvidia driver.  I reboot off the "generic" kernel and X is fine....you know..aside from the random hard locking...

---

### Post by Ramses de Norre on 2006-11-19
You need to reinstall the nvidia drivers for the 386 kernel, you need to do this for every kernel change. Make also sure that you've got the restricted-modules for the 386.
I've got a few locks ever since but definitely less then when I used the generic kernel.

---

