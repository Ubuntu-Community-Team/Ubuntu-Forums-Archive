---
title: "XOrg CPU usage spikes every 3 seconds"
date: 2007-02-28
forum: General Help
---

### Post by daou on 2007-02-28
I attached a screenshot of my gnome-system-monitor in action. It shows quite well what is happening: CPU usage spikes every 3 seconds which causes choppiness on the whole desktop. I believe the XOrg process is causing it (its the only process raking in huge CPU time).

I'm using Edgy on an AMD64 3000+, XFX Geforce 6600 GT, 1024 MB OCZ dual channel DDR, and hd space up the wazoo.

I did recently install Compiz. I have been on and off Compiz and Beryl for the past 7 months and I have not seen anything like this before. It started doing this while I was away from my computer, no updates, no nothing. Rebooted, did not help.

Any suggestions?

EDIT: I have tried turning GL desktop off and killing the compiz process. No cigar.

---

### Post by Bagboy23 on 2007-02-28
If you run the command 'top' it will give you a better indication of what is causing this 'spike'. It'll then bring you one step closer to eliminating the culprit. 

Post your top results.

---

### Post by daou on 2007-02-28
Top output

```

  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND       
 4329 root      15   0 63896  40m  13m S  4.0  4.0   1:23.15 Xorg               
 5724 daou      16   0 87164  15m  10m R  1.7  1.6   0:02.36 gnome-terminal     
 5543 daou      15   0 69400  17m  12m S  0.7  1.7   0:57.64 gnome-system-mo    
 5764 daou      15   0 15300 8964 6528 S  0.7  0.9   0:03.81 metacity           
 5034 root      15   0  5876 1472 1028 S  0.3  0.1   0:00.84 nmbd                      
 6871 daou      16   0  2252 1140  844 R  0.3  0.1   0:00.20 top                
    1 root      16   0  1632  536  448 S  0.0  0.1   0:01.00 init      
```

---

### Post by raul_ on 2007-02-28
I'm posting here because i didn't want to create another thread. Anyway, my problem is similar. I have been using Beryl for a LONG time, with the proprietary ATI drivers and my cpu was normally on 2-3%, maybe not even that much. In these past weeks, when my computer is idle, it just uses like 21%. I tried changing from the fglrx drivers to the radeon driver and this didn't changes, so it's not a driver issue. I tried several xorg.conf tweaks, some of them even broke it, but nothing a Live CD won't solve :mrgreen: 

Honestly i don't know why this started happening. It started bothering me some time ago, but i can't tell when. My computer doesn't slow down, but i don't think it's good to stress the CPU that much. 

The only things i've done, that i can remember, were the kernel update and the Beryl update. I tried downgrading Beryl and the problem persists, so maybe this is a kernel bug? 

NOTE: When i use metacity the problem persists

---

### Post by fragos on 2007-02-28
I also get rythmic spikes in CPU usage with xorg.  This however only occurs when I running tvtime.

---

### Post by daou on 2007-03-01
I played around with a bunch of settings and got rid of it. I'm not sure which one of these fixed it because I made all the changes at once:

[LIST]
[*]turned off subpixel smoothing on fonts
[*]made changes to xorg.conf:
[*]---removed "RenderAccel" option
[*]---removed "AllowGLXWithComposite" option
[*]---removed "DisableGLXRootClipping" option
[*]restarted X
[*]started a KDE session, logged out, and went back into GNOME
[/LIST]

after doing these steps xorg no longer does the CPU spikes. It was probably one of the xorg.conf options that was the problem.

---

### Post by fragos on 2007-03-01
Subpixel smoothing is frequently used with LCDs and I'm not using it.  The xorg options you mention I cant't find in my xorg.conf so I assume they are removed.  I have no doubt that they solved your problem.  Perhaps tvtime exposes another problem or perhaps a fact of life with TV viewing.

---

### Post by daou on 2007-03-01
> Subpixel smoothing is frequently used with LCDs and I'm not using it. The xorg options you mention I cant't find in my xorg.conf so I assume they are removed. I have no doubt that they solved your problem. Perhaps tvtime exposes another problem or perhaps a fact of life with TV viewing.
__________________

I'm using dual monitor display (22" 1680x1050 + 19" 1280x1024) on a gfx card that supports much less. I wouldn't be surprised if some xserver related options were involved. Your CPU spikes are probably caused by video computation in relation to tvtime. Most likely, it calculates a certain block of video decompression to your memory and waits until the next block needs to be decompressed. I would'nt say this is a problem unless your hardware is decent (this involves many opinions) and video streaming is choppy.

---

### Post by daou on 2007-03-01
> I'm posting here because i didn't want to create another thread. Anyway, my problem is similar. I have been using Beryl for a LONG time, with the proprietary ATI drivers and my cpu was normally on 2-3%, maybe not even that much. In these past weeks, when my computer is idle, it just uses like 21%.

You don't have much to worry about your CPU. I've run Intel and AMD CPUs at 100% (or 150% in overclocked cases) for months without failures or physical damage. They are just a cluster of transistors, after all. However, a 21% idle CPU usage is not normal or acceptable to anyone beyond a computer illiterate...

---

### Post by fragos on 2007-03-01
I've been running 512KB of memory and decided to see if going to 1GB would make any difference.  The spikes are still there but the % of CPU has dropped.  There are two factors that might be in play.  The first is that the needto swap memory has been reduced.  The second is by adding a second and equal memory module I may have sped up memory access by 10%.  My CPU is an AMD Sempron 2800+ and not a real barn burner like an X2.  I do find my performance with Ubuntu 6.10 quite good.  I haven't experimented with overclocking yet.

---

### Post by citizen_k on 2008-04-27
Just chiming in to say that I also am experiencing this problem.  I upgraded to 8.04 two days ago, and ever since my desktop has had a 2 1/2 to 3 second cycle where CPU usage spikes from 5-8% up to 100%.  This happens regardless of what programs are running - from a fresh reboot the system will not spike at all for about 30 seconds, then a crash icon will flash momentarily in the header bar and the spikes will begin.  Running top in terminal tells me that the spikes are caused by Xorg jumping momentarily to take up all available system resources.  

It's kind of pretty, like my computer has a heartbeat, but I would prefer that she doesn't have to work so hard.  Aside from the spiking, the system is relatively stable, and I can run multiple applications (amarok, firefox, evince, etc) without it freezing or lagging.  However, when the CPU load is already high, the spikes push it to the limit and I see mouse and screen lag in pulses corresponding with each spike.

Hopefully someone has a better idea of what's going on here than I, because I am at a loss.  Thanks in advance!

Here's my specs:  
Intel P4 3.0 Ghz
NVIDIA Geforce 7600GT (NVIDIA drivers)
4 gigs ram, I forget what bus speed
19" Viewsonic monitor, running 1240x1080

Here is my xorg:
> # nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildd@vernadsky)  Tue Mar  4 20:24:34 UTC 2008

# xorg.conf (X.Org X Window System server configuration file)
#
# This file was generated by failsafeDexconf, using
# values from the debconf database and some overrides to use vesa mode.
#
# You should use dexconf or another such tool for creating a "real" xorg.conf
# For example:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen      0  "Screen0" 0 0
EndSection

Section "Module"
    Load           "glx"
    Load           "v4l"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
EndSection

Section "Monitor"
    Identifier     "Configured Monitor"
    VendorName     "ViewSonic"
    ModelName      "ViewSonic VA702b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
    Gamma           1
    ModeLine       "640x480@60" 25.2 640 656 752 800 480 490 492 525 -hsync -vsync
    ModeLine       "640x480@72" 31.5 640 664 704 832 480 489 491 520 -hsync -vsync
    ModeLine       "640x480@75" 31.5 640 656 720 840 480 481 484 500 -hsync -vsync
    ModeLine       "640x480@85" 36.0 640 696 752 832 480 481 484 509 -hsync -vsync
    ModeLine       "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    ModeLine       "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    ModeLine       "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    ModeLine       "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    ModeLine       "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    ModeLine       "832x624@75" 57.3 832 864 928 1152 624 625 628 667 -hsync -vsync
    ModeLine       "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    ModeLine       "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    ModeLine       "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -hsync -vsync
    ModeLine       "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -hsync -vsync
    ModeLine       "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
    ModeLine       "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    ModeLine       "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    ModeLine       "1280x960@75" 129.9 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
    ModeLine       "1400x1050@60" 122.6 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
    ModeLine       "1400x1050@75" 155.8 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
    ModeLine       "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
    ModeLine       "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "ViewSonic VA712b"
    HorizSync       30.0 - 82.0
    VertRefresh     50.0 - 85.0
EndSection

Section "Device"
    Identifier     "Configured Video Device"
    Driver         "nvidia"
    VendorName     "NVIDIA"
    BoardName      "NVIDIA GeForce 7 Series"
    Option         "NoLogo" "True"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7600 GT"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Configured Video Device"
    Monitor        "Configured Monitor"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1600 1200
        Depth       24
        Modes      "1280x1024@60" "1280x960@75" "1280x960@60" "1400x1050@60" "1280x1024@75" "1400x1050@75" "1152x864@75" "1600x1200@65" "1024x768@60" "1600x1200@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
    EndSubSection
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Videocard0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024@75 +0+0; 1280x1024@60 +0+0; 1280x960@75 +0+0; 1280x960@60 +0+0; 1152x864@75 +0+0; 1024x768@60 +0+0; 1024x768@70 +0+0; 1024x768@75 +0+0; 1024x768@85 +0+0; 832x624@75 +0+0; 800x600@60 +0+0; 800x600@85 +0+0; 800x600@75 +0+0; 800x600@72 +0+0; 800x600@56 +0+0; 640x480@85 +0+0; 640x480@75 +0+0; 640x480@72 +0+0; 640x480@60 +0+0"
EndSection


One last note:  When I installed Hardy, it was a royal bitch to get NVIDIA drivers running, and I had to spend a lot of time mucking around in Xorg.  It wouldn't surprise me in the least if I just screwed up something minor, and it is causing repeated errors.

---

### Post by fragos on 2008-04-27
You do have a very complicated xorg. I've a somewhat comporable machine with an FX5200. It came up fine 1440x900 with the open source driver. I ran "Hardware Drivers" to install the proprietary Nvidia driver. I made no changes to xorg other than for my Wacom Graphire4 and have no problems. There is a CPU spike about every 35 seconds for up to 70% but Linux is multi-tasking and there's a lot going on behind the scenes. Letting Ubuntu install the video driver it chooses from it's official repositories has alway worked flawlessly for me. I only edit config files when the GUI won't do what I need.

---

### Post by citizen_k on 2008-04-27
Yeah, I'm not thrilled with what I have thus far, but I was kind of forced into it.  When I upgraded to Hardy my box wouldn't recognize my graphics card, or any resolution above 800x600.  The xorg above is what NVIDIA's drivers put into place, and given how much it took just to get that running, I'm a bit hesitant about starting over.  Out of curiosity, what does a "normal" xorg.conf file look like?

---

### Post by citizen_k on 2008-04-28
So, I found some more time to mess around with this today.  I haven't yet gotten rid of the CPU spiking, and top still shows xorg as the culprit, but I did manage to find [this thread]("http://ubuntuforums.org/showthread.php?p=4755062") and used it to rewrite my xorg.conf into something less ridiculous.  Baby steps...

Anyhow, I'm kind of at a loss as to what my next course of action ought be.  I guess I'll just keep monitoring the threads and see if anything else pops up.

---

### Post by fragos on 2008-04-29
The following xorg was generated during install. Much shorter with 8.04 than it was with older releases. My video is Nvidia and my 1440x900 Viewsonic was automatically set up.

Section "InputDevice"
	Identifier	"Generic Keyboard"
	Driver		"kbd"
	Option		"XkbRules"	"xorg"
	Option		"XkbModel"	"pc105"
	Option		"XkbLayout"	"us"
EndSection

Section "InputDevice"
	Identifier	"Configured Mouse"
	Driver		"mouse"
	Option		"CorePointer"
EndSection

Section "Device"
	Identifier	"Configured Video Device"
	Driver		"nvidia"
	Option		"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier	"Configured Monitor"
EndSection

Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
	Defaultdepth	24
EndSection

Section "ServerLayout"
	Identifier	"Default Layout"
	Screen		"Default Screen"
EndSection

---

### Post by mdelfede on 2008-04-30
Well, I solved all my Xorg problems (Ubuntu Hardy 64, NVidia GeForce 8600M GS) adding just a line to Xorg.conf :

```


Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"UseEvents"	"On"     <=== THIS LINE ADDED !!!
EndSection


```

Xorg CPU usage, that used to go up to 60%-100% with PC idle dropped to 1-2-5%.

Ciao

Max

---

### Post by citizen_k on 2008-04-30
> **mdelfede said:**
> Well, I solved all my Xorg problems (Ubuntu Hardy 64, NVidia GeForce 8600M GS) adding just a line to Xorg.conf :

```


Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"UseEvents"	"On"     <=== THIS LINE ADDED !!!
EndSection


```

Xorg CPU usage, that used to go up to 60%-100% with PC idle dropped to 1-2-5%.

Ciao

Max

This fixed mine temporarily, but as soon as I open Firefox, it comes back. I wonder if my problem is flash-related, or perhaps is tied into one of my extensions/plugins...

---

### Post by fragos on 2008-04-30
> **mdelfede said:**
> Well, I solved all my Xorg problems (Ubuntu Hardy 64, NVidia GeForce 8600M GS) adding just a line to Xorg.conf :

```


Section "Device"
	Identifier	"nVidia Corporation G80 [GeForce 8600M GS]"
	Driver		"nvidia"
	Busid		"PCI:1:0:0"
	Option		"AddARGBVisuals"	"True"
	Option		"AddARGBGLXVisuals"	"True"
	Option		"NoLogo"	"True"
	Option		"UseEvents"	"On"     <=== THIS LINE ADDED !!!
EndSection


```

Xorg CPU usage, that used to go up to 60%-100% with PC idle dropped to 1-2-5%.

Ciao

Max

I'd be very interested in what Option "UseEvents" does. There may be a downside to using it. If less CPU is used there might be an increase in battery life on laptops.

---

### Post by mdelfede on 2008-05-01
> **citizen_k said:**
> This fixed mine temporarily, but as soon as I open Firefox, it comes back. I wonder if my problem is flash-related, or perhaps is tied into one of my extensions/plugins...

Nope, you're right.... my fix was also temporary.
With compiz enabled, xorg jumps again on 60-90% cpu usare in a random way.
I don't know if it depends on firefox, but I guess not... 

Max

---

