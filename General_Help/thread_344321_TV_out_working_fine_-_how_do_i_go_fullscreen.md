---
title: "TV out working fine - how do i go fullscreen?"
date: 2007-01-22
forum: General Help
---

### Post by yezzer on 2007-01-22
Hey people!

I'm new to ubuntu. I've been able to do a few things such as install FTP, web, SSH servers, mount hdds, set up filesharing, and get Nvidia Twinview to work - so i'm not *completely* new... just.. quite a **bit** new. :D

Anyway - here's the situation:

My ubuntu box is connected to my LCD monitor (1280x1024), and also my tv in another room. 
The picture on my TV  seems to be an area of my LCD desktop.. If i move my mouse cursor to the right, my entire desktop scrolls, and I can use the 'extra' space added by my 640x480 TV screen. 
The TV shows this extra space. [i can upload some pics if needed?]

How can I get the LCD and the TV to be separate? They are different resolutions - all i want to do is play full screen video on the TV, and not the LCD! :D

Thanks for any help :)

---

### Post by yezzer on 2007-01-22
ah, before i sound like a complete newbie, [ahem] i just noticed that the whole 'scrolling' thing is actually VNC allowing me to scroll to the other bit of the desktop.. ;) :D

So - when i play a movie in VLC, and move VLC to the right, so it appears on the TV, and then go fullscreen, the video appears on my LCD. I want it to appear on the TV. How do I do this - anyone? :)

Thanks!



edit: i've just read something about multiple x-screens and twinview. I don't really know that X is :( so i dont know if it's what i'm looking for or not... help!! (i'll google in the morning, getting late now!)

---

### Post by Torajima on 2007-01-22
Not sure about the Linux version of VLC, but I belive on the Mac you can change which monitor VLC displays on when you enter fullscreen mode.

---

### Post by fenian on 2007-01-22
Yes  I think you need to set up seperate x-screens.This wiki shows you how assuming you have nvidia drivers.
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)

---

### Post by yezzer on 2007-01-23
> **fenian said:**
> Yes  I think you need to set up seperate x-screens.This wiki shows you how assuming you have nvidia drivers.
[https://help.ubuntu.com/community/NvidiaTVOut](https://help.ubuntu.com/community/NvidiaTVOut)



Thanks for that, multiple X-screens looks exactly what i want.

I've followed the wiki, but - well - i dont think its working..
When ubuntu boots, should i be able to see something on the TV? All i see is the normal boot sequence on both the LCD and TV, and then nothing once ubuntu loads the gui.

Once ubuntu has booted, do i need to run something to get output on the TV?
i've tried randomly pressing buttons such as ctrl+alt and all the F keys..

i've attached my xorg.conf, i tried to attach my log, but.... - i've just noticed some weird problems.. i cant open new applications. it says 'opening terminal' - then. it disappears and....no new application. i'm gonna try restarting :D

---

### Post by yezzer on 2007-01-23
ok, rebooted, and now my applications have stopped disappearing :)

attached is my log.. i had to snip a small amount of text off the top (some stuff about fonts, dont think it's important!)

---

### Post by fenian on 2007-01-24
I think you may need to uncomment the ConnectedMonitors option in the screens section.Also I'm not sure if the BusID's in the Devices section should be different in my config they are both the same.Here is my xorg.conf which works on my Geforce 6200.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen 0       "Screen0"
    Screen 1       "Screen1" rightof "Screen0"
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
        Identifier      "Monitor" #CRT
        HorizSync       31.0-115.0
        VertRefresh     50.0-180.0
        Option          "DPMS"
EndSection

Section "Monitor"
        Identifier "Television" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Device"
        Identifier      "Device0"
        Driver          "nvidia"
        Screen 0
        Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"
        BusID   "PCI:01:00:0"
EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Screen 1
        BusID   "PCI:01:00:0"
EndSection


Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor"
        DefaultDepth    24
        Option  "UseDisplayDevice" "CRT"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "COMPOSITE"
        Option  "TVStandard" "NTSC-M"
        Option  "UseDisplayDevice" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection

---

### Post by yezzer on 2007-01-24
Thanks for your help. I'll try playing around with my xorg.conf to see what I can achieve.

A question for anyone - which might seem stupid.. how will i know it's working correctly?
My TV is on - will it just automatically show SOMETHING on the TV, like it did with TwinView? Or do I need to do *something* in terminal etc to make it work?

Cheers!

---

### Post by yezzer on 2007-01-24
YEY it works :D:D

Thanks for your help everyone!

For google i'll paste the interesting bit of my xorg.conf

I have another related question to ask now - but i'll post it in a new thread.

Thanks again!

> 
Section "ServerLayout"
        Identifier      "Basic Layout"
        Screen 0        "Screen0"
        Screen 1        "Screen1" rightof "Screen0"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
EndSection

Section "Monitor"
	Identifier	"Generic Monitor"
	Option		"DPMS"
	HorizSync	28-64
	VertRefresh	43-60
EndSection

Section "Monitor"
        Identifier "Television" #TV
        HorizSync 30-50
        VertRefresh 60
EndSection

Section "Device"
	Identifier	"Device0"
	Driver		"nvidia"
	Screen 0
	Option  "NoLogo"        "true"
        Option  "RenderAccel"   "true"
	BusID		"PCI:1:0:0"
	Option "UseEdidFreqs" "false"
	Option "IgnoreEDID" "true"

EndSection

Section "Device"
        Identifier      "Device1"
        Driver "nvidia"
        Screen 1
        #BusID   "PCI:02:09:0"
	BusID   "PCI:1:0:0"
	Option "TVOutFormat" "SVIDEO"
	Option "TVStandard" "PAL-I
#	Option "UseEdidFreqs" "false"
#	Option "IgnoreEDID" "true"
EndSection





Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Generic Monitor"
        DefaultDepth    24
        Option  "UseDisplayDevice" "CRT"
        SubSection "Display"
                Depth           24
                Modes           "1280x1024" "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "Extensions"
	Option "Composite" "Enable"
EndSection

Section "Screen"
        Identifier      "Screen1"
        Device          "Device1"
        Monitor         "Television"
        DefaultDepth    24
        Option  "TVOutFormat" "SVIDEO"
        Option  "TVStandard" "PAL-I"
        Option  "UseDisplayDevice" "TV"
        SubSection "Display"
                Depth 24
                Modes "640x480"
        EndSubSection
EndSection

Section "DRI"
	Mode	0666
EndSection



---

