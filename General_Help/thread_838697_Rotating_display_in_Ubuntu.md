---
title: "Rotating display in Ubuntu"
date: 2008-06-23
forum: General Help
---

### Post by revolutio on 2008-06-23
I'm currently using Ubuntu 8.04 and would like to rotate my screen vertically as my Samsung SyncMaster 204B is able to do physically.  In Windows there was a simple program called MagicRotation that with one click I could go from my usual 1600x1200 to a 1200x1600 with everything appropriately oriented.

This is a rather key thing for me since I got quite used to reading documents and browsing the web that way.  Unfortunately I haven't found any way to do this in Linux.  The only solutions I saw were only for NVIDIA video cards and I have a Radeon 9800 Pro.

So, how would I go about rotating my screen back and forth? What additional information is needed about my computer before this can be answered?

Thanks for your help.

---

### Post by psyopper on 2008-06-23
Have you tried rotating it through:

System > Preferences > Screen Resolution

---

### Post by revolutio on 2008-06-24
> **psyopper said:**
> Have you tried rotating it through:

System > Preferences > Screen Resolution

ATI drivers, ergo...

> The X Server does not support the XRandR extension.  Runtime resolution changes to the display size are not available.

And when I do a sudo displayconfig-gtk there are no options regarding rotation that I can see.

---

### Post by revolutio on 2008-06-25
Bumping for a solution.

---

### Post by revolutio on 2008-06-26
Is there another forum I should post this in to get an answer?

---

### Post by stldirty on 2008-06-26
try the general help section

---

### Post by Forlong on 2008-06-26
The fgrlx driver doesn't support xrandr.

If you un-install it and go back to the open radeon driver you will be able to use xrandr to rotate your screen.

---

### Post by revolutio on 2008-06-28
> **Forlong said:**
> The fgrlx driver doesn't support xrandr.

If you un-install it and go back to the open radeon driver you will be able to use xrandr to rotate your screen.
I've gone back to the open ati drivers now and indeed the rotation options appeared.  After fixing the virtual desktop size in xorg.conf I was able to successfully rotate the screen.  Before throwing a minor party though I found the screen to be refreshing horrifyingly slowly. It was completely unusable.

Running glxgears while vertical produced a completely normal fps. 

Thank you for your advice, any thoughts on this development?

Here's my xorg.conf:
```
Section "ServerLayout"
	Identifier     "Default Layout"
	Screen      0  "aticonfig-Screen[0]-0" 0 0
        Option          "AIGLX"         "true"
EndSection

Section "Files"
EndSection

Section "Module"
EndSection

Section "InputDevice"
	Identifier  "Generic Keyboard"
	Driver      "kbd"
	Option	    "XkbRules" "xorg"
	Option	    "XkbModel" "pc105"
	Option	    "XkbLayout" "us"
EndSection

Section "InputDevice"
	Identifier  "Configured Mouse"
	Driver      "mouse"
	Option	    "CorePointer"
	Option	    "Emulate3Buttons" "true"
EndSection

Section "Monitor"
	Identifier   "aticonfig-Monitor[0]-0"
	Option	    "VendorName" "ATI Proprietary Driver"
	Option	    "ModelName" "Generic Autodetecting Monitor"
	Option	    "DPMS" "true"
        HorizSync       30-81
        VertRefresh     56-75
EndSection

Section "Device"
	Identifier  "aticonfig-Device[0]-0"
	Driver      "ati"
	BusID       "PCI:1:0:0"
        Option		"XAANoOffscreenPixmaps"

EndSection

Section "Screen"
	Identifier "aticonfig-Screen[0]-0"
	Device     "aticonfig-Device[0]-0"
	Monitor    "aticonfig-Monitor[0]-0"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
           	# ADD A VIRTUAL LINE TO PROVIDE FOR THE LARGEST SCREENS YOU WILL HOTPLUG 
           	Virtual    1600 1600 
	EndSubSection
EndSection

Section "DRI"
        Mode 0666
EndSection
        
Section "Extensions"
        Option "Composite" "Enable"
EndSection
```

---

### Post by revolutio on 2008-07-02
Hopeful bump. :(

---

### Post by psyopper on 2008-07-02
Have you tried adding "Option" "XRandR" "True" to your xorg.conf under the device section? I know that enables it for nvidia cards, I think it's an X option, not and nvidia option.

Back up your xorg.conf first, save all your work and be prepared for a hard reboot if it fails.

---

### Post by daehenoc on 2008-07-02
I have bad news for you: [fglrx 'features' and screen rotation [wiki.cchtml.com]](http://wiki.cchtml.com/index.php/Features#Screen_Rotation)

I'm ditching my ATI card and getting an nVidia one!  God-damn I hate ATI cards!

---

### Post by revolutio on 2008-07-04
> **daehenoc said:**
> I have bad news for you: [fglrx 'features' and screen rotation [wiki.cchtml.com]](http://wiki.cchtml.com/index.php/Features#Screen_Rotation)

I'm ditching my ATI card and getting an nVidia one!  God-damn I hate ATI cards!
I want to desperately but I am also horribly broke.  Plus I have an AGP motherboard and who makes the only decent AGP cards?  ATI!

Rage.  You shouldn't have to get new hardware to enjoy basic operating system features.  So far I *almost* have Ubuntu working on par with Windows XP.

---

### Post by Plasma_NZ on 2008-07-04
> **revolutio said:**
> I want to desperately but I am also horribly broke.  Plus I have an AGP motherboard and who makes the only decent AGP cards?  ATI!

Rage.  You shouldn't have to get new hardware to enjoy basic operating system features.  So far I *almost* have Ubuntu working on par with Windows XP.

My ubuntu has surpassed XP - and made it look dull and useless.. Hope u manage to surpass XP with your setup and uninstall it :P

---

### Post by chalewa on 2008-07-04
> **Plasma_NZ said:**
> My ubuntu has surpassed XP - and made it look dull and useless.. Hope u manage to surpass XP with your setup and uninstall it :P

as has mine...

i am forced to use windows at work and can't tell you how much it frustrates me. 

the littlest things in the world make the biggest difference. the 'always on top' feature in ubuntu is something that i have taken for granted. for me, it is one of the simplest most useful features found in ubuntu.

---

### Post by Plasma_NZ on 2008-07-06
> **chalewa said:**
> as has mine...

i am forced to use windows at work and can't tell you how much it frustrates me. 

the littlest things in the world make the biggest difference. the 'always on top' feature in ubuntu is something that i have taken for granted. for me, it is one of the simplest most useful features found in ubuntu.

Hey man kinda curious as to your setup...

Mine goes like this....

Primary screen 19" LCD - running compiz with 5 virtual-desktops, in expo mode (cube is gay)
Second LCD 17" on my left is a seperate Xsession that runs Movies 24/7, a 32" tv in my bedroom clones the 17" LCD, to my right is my sons room, he has his own 19" tv which also runs its own xession and plays toon's 24/7...

In total i ALWAYS have running,

Virtual-Desktop-1 / 4 conkys, gkrellm

Virtual-Desktop-2 / top (terminal system monitor), a terminal window, Pidgin

Virtual-Desktop-3 / Firefox

Virtual-Desktop-4 / Evolution

Virtual-Desktop-5 / LinuxDC++

2 instances of VLC player (read above re-which screens they are on).

With all that going full-tilt, it use's 1.17ghz of my 3ghz duo-core 64bit (6ghz if u want to count both core speeds) 680mb ram..

What's yours like..

---

### Post by chalewa on 2008-07-07
> **Plasma_NZ said:**
> Hey man kinda curious as to your setup...

Mine goes like this....

Primary screen 19" LCD - running compiz with 5 virtual-desktops, in expo mode (cube is gay)
Second LCD 17" on my left is a seperate Xsession that runs Movies 24/7, a 32" tv in my bedroom clones the 17" LCD, to my right is my sons room, he has his own 19" tv which also runs its own xession and plays toon's 24/7...

In total i ALWAYS have running,

Virtual-Desktop-1 / 4 conkys, gkrellm

Virtual-Desktop-2 / top (terminal system monitor), a terminal window, Pidgin

Virtual-Desktop-3 / Firefox

Virtual-Desktop-4 / Evolution

Virtual-Desktop-5 / LinuxDC++

2 instances of VLC player (read above re-which screens they are on).

With all that going full-tilt, it use's 1.17ghz of my 3ghz duo-core 64bit (6ghz if u want to count both core speeds) 680mb ram..

What's yours like..


damn that is intense. 

i wish that i could have that kinda organization. i used to do something similar when i was at school, but now that i am at home, my setup is rather vanilla, the only exciting thing being compiz. sometimes i get adventurous and throw up another monitor or something like that if i feel like impressing friends but that is rare. 

my major issue is that i am constantly changing what my desktop setup is. one week i will feel like using gnome, and the next i will go back to xfce. it is tough for me to keep any sort of regularity with my desktops and what is running on each.

---

### Post by Ulrich Scholz on 2008-07-07
Hi everybody,

I have the same problem - kubuntu 8.04 does not rotate the screen.  I've added
         Option "XRandR" "True"
to my xorg.conf.  My graphics card is a NVIDIA GeForce 8 Series.  But it does not work.

Is there hope?

Ulrich

```
[scholzuh@emld-desktop:Ftp] >more /etc/X11/xorg.conf
# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildd@palmer)  Tue Jan 22 12:05:14 UTC 2008

Section "ServerLayout"
        Identifier      "Layout0"
  screen 0 "Screen0" 0 0
        Inputdevice     "Keyboard0"     "CoreKeyboard"
        Inputdevice     "Mouse0"        "CorePointer"
EndSection

Section "Files"
        Rgbpath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
        Load            "extmod"
        Load            "type1"
        Load            "freetype"
        Load            "glx"
        Load            "GLcore"
        Load            "v4l"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Mouse0"
        Driver          "mouse"
        Option          "Protocol"      "auto"
        Option          "Device"        "/dev/psaux"
        Option          "Emulate3Buttons"       "no"
        Option          "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Keyboard0"
        Driver          "keyboard"
EndSection

        Option          "Device"        "/dev/psaux"
        Option          "Emulate3Buttons"       "no"
        Option          "ZAxisMapping"  "4 5"
EndSection

Section "InputDevice"
        # generated from default
        Identifier      "Keyboard0"
        Driver          "keyboard"
EndSection

Section "Monitor"
        Identifier      "Monitor0"
        Vendorname      "Samsung"
        Modelname       "Samsung SyncMaster 204T/204Ts/214T,SyncMaster Magic CX201Ts(Digital)"
        Horizsync       30-81
        Vertrefresh     56-75
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
        Gamma   1.0
EndSection

Section "Device"
        Identifier      "Device0"
        Boardname       "nv"
        Busid           "PCI:2:0:0"
        Driver          "nv"
        Option "XRandR" "True"
        Screen  0
EndSection

Section "Screen"
        Identifier      "Screen0"
        Device          "Device0"
        Monitor         "Monitor0"
        Defaultdepth    24
        SubSection "Display"
                Depth   24
                Virtual 1600    1200
                Modes           "1600x1200@60"  "1600x1200@65"  "1400x1050@60"  "1280x960@75"   "1280x1024@60"  "1280x960@60"
   "1280x1024@75"  "1152x864@75"   "1024x768@60"   "1024x768@70"   "1024x768@75"   "832x624@75"    "800x600@60"    "800x600@75"    "800x600@72"    "800x600@56"    "640x480@75"    "640x480@72"    "640x480@60"
        EndSubSection
EndSection

Section "ServerFlags"
EndSection

```

---

