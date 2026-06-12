---
title: "Fiesty and Google Earth nVidia GeForce2 driver problem"
date: 2007-04-30
forum: General Help
---

### Post by fable on 2007-04-30
I used Google Earth on Ubuntu Dapper (6.06) without any problem for over a year.  My video card is a nVidia GeForce2 MX.  I installed the nVidia video driver on this platform using Synaptic.

Couple of days I set up same computer, using a second hard dirve, to run Ubuntu Fiesty (7.04).  The nVidia video card is the same, i.e. GeForece2 MX.  I stalled the new nVidia legacy driver using Synaptic.  Everything on my Fiesty platform runs fine with the exception of Google Earth.  When I double click on Google Earth, it tried to contact the Google server and there is an error message saying Google Earth does not recognize the video driver.

Anyone knows why Fiesty has this problem with Google Earth?

:confused:


------------------------------Problem Resolved----------------------------------------------

The Google Earth "not recognize the video card" problem was solved adding in /etc/X11/xorg.conf, "Device" section, the lines:

```
Option  "AddARGBVisuals"  "True"
Option  "AddARGBLXVisuals"  "True"
```

and in the "Screen" section, the line:

```
Option  "AllowGLXWithComposite"  "True"
```

The low resolution problem is cause by using an old monitor that does not support DDC/EDID.  
The problem was resolved by adding in /etc/X11/xorg.conf, "monitor" section, the line:

```
Option "DDC" "False"
```

Now I can use high resolution 1280x1024 to view Google Earth.

---

### Post by threegremlins on 2007-04-30
Nvidia seems to present problems, and some programs unfortunately won't work. Eh. First see if you have the nvidia driver running properly like trying various things that require a lot of video memory and some gl applications. 
Check out this thread

[http://ubuntuforums.org/showthread.php?t=425584&highlight=nvdia+geforce+fx](http://ubuntuforums.org/showthread.php?t=425584&highlight=nvdia+geforce+fx)

If they aren't here's a good place to start

[http://ubuntuguide.org/wiki/Ubuntu:Feisty](http://ubuntuguide.org/wiki/Ubuntu:Feisty)

Use Ctrl+F to search for nvidia and that will get you started. I'm really using Fiesty not Edgy, just to lazy to change my profile. I downloaded the Nvidia driver from Nvidia

[http://www.nvidia.com/object/unix.html](http://www.nvidia.com/object/unix.html)

It works just fine with Edgy and now with Fiesty
Check to make sure your getting the right one if you go this route ;)

Hope this helps

---

### Post by dcstar on 2007-05-01
> **fable said:**
> I used Google Earth on Ubuntu Dapper (6.06) without any problem for over a year.  My video card is a nVidia GeForce2 MX.  I installed the nVidia video driver on this platform using Synaptic.

Couple of days I set up same computer, using a second hard dirve, to run Ubuntu Fiesty (7.04).  The nVidia video card is the same, i.e. GeForece2 MX.  I stalled the new nVidia legacy driver using Synaptic.  Everything on my Fiesty platform runs fine with the exception of Google Earth.  When I double click on Google Earth, it tried to contact the Google server and there is an error message saying Google Earth does not recognize the video driver.

Anyone knows why Fiesty has this problem with Google Earth?

:confused:

I'm using an old GeoForce and Google Earth works fine for me, make sure you have the highlighted line in your /etc/X11/xorg.conf file:

```
Section "Screen"
	Identifier	"Default Screen"
	Device		"nVidia Corporation NV34 [GeForce FX 5200]"
	Monitor		"BenQ FP92W"
	DefaultDepth	24
**	Option		"AllowGLXWithComposite" "1"**
```

---

### Post by fable on 2007-05-01
I am using the 'new' legacy nVidia driver installed using Synaptic.  The driver name is 'nv' not 'nvidia'.  For some reason I cannot add the 3D driver with 'nv'.  This might be the cause of the problem because I understand that Google Earth needs 3D. 

When I have time I'll go to the nVidia site and down load the latest driver to see it that helps.

---

### Post by fable on 2007-05-01
I forgot to mention that I did add the following line but still have the same problem.
Option 	"AllowGLXWithComposite" "1"

The Google Earth error message is 

"Unknown Graphics Card....Google Earth is unable to identify your graphics card.  This is most likely because the driver for your graphics card has not been installed.  You may continue but the Google Earth is unlikely to work until you upgrade your driver....."

---

### Post by fable on 2007-05-01
I finally got Google Earth to work.

I have to fall back to the old legacy "nvidia" driver and then add the line "Option  "AllowGLXWithComposite" "1".  

I re-installed the old legacy "nvidia" driver using Synaptic and then edit the xorg.conf file to add the Option.

The drawback in going back to the old legacy driver is that it only allow resolution up to 1024x768 at 60Hz.

---

### Post by threegremlins on 2007-05-01
In your xorg.conf file the driver should be nvidia not nv, but at least you got it going.

---

### Post by dcstar on 2007-05-01
> **fable said:**
> I finally got Google Earth to work.

I have to fall back to the old legacy "nvidia" driver and then add the line "Option  "AllowGLXWithComposite" "1".  

I re-installed the old legacy "nvidia" driver using Synaptic and then edit the xorg.conf file to add the Option.

The drawback in going back to the old legacy driver is that it only allow resolution up to 1024x768 at 60Hz.

I use the legacy driver with 1440 x 900 resolution (to match my LCD widescreen) - there are many forum posts with details on how to set things like this up.

---

### Post by fable on 2007-05-02
I am interested to find out how you get the higher resolution.
Are you using the "old" or "new" legacy driver?
My "legacy" driver's name is 'nvidia", not 'nv'.  Are you using the 'nividia' driver?
Do you mind showing me a copy of your xorg.conf file for the video driver and the screen so that I can see what options you selected?
I would love to use the higher resolution to run Google Earth.

---

### Post by threegremlins on 2007-05-02
Choosing the right driver is a bit of a problem and you'll have to do some researching to pick the right one. For instance I'm using the geforce fx 5500, i bought it a few years back when it came out as a line of their cheaper, er less expensive drivers. However it uses the old legacy driver even though it's new. Somewhere I came across the driver compatability page following links from Ubuntu's howto's, your just going to have to put your nose to the ground and sniff it out because I don't remember how to get there anymore. I use the driver downloaded from Nvidia and here are some of the concerns I had with it.

[http://ubuntuforums.org/showthread.php?t=401690](http://ubuntuforums.org/showthread.php?t=401690)

Since then running edgy I did a few updates without a hitch or having to reinstall the Nvidia driver, I did however have problems after installing my graphire4 pen tablet. Install your pen tablet first or any other device that will change your xorg.conf file, before installing the Nvidia driver. Eh. I'm inclined to think when the driver installs it examines your system then selects the right kernel module or coding needed for your system. i use xrandr change my screen running fluxbox(runs faster but only marginally) 
in a terminal "xrandr -q" will list your available  screens
example
threegremlins@last:~$ xrandr -q to pick one,
 SZ:    Pixels          Physical       Refresh
 0   1280 x 1024   ( 331mm x 240mm )   50  
*1   1152 x 864    ( 298mm x 203mm )   51  *60  
 2   1024 x 768    ( 265mm x 180mm )   52   62   63   64   65  
 3    832 x 624    ( 215mm x 146mm )   53  
 4    800 x 600    ( 207mm x 141mm )   54   67   68   69   70   71  
 5    720 x 400    ( 186mm x  94mm )   55  
 6    640 x 480    ( 165mm x 112mm )   56   75   76   77   78  
 7   1280 x 960    ( 331mm x 225mm )   57  
 8   1280 x 800    ( 331mm x 188mm )   58  
 9   1280 x 768    ( 331mm x 180mm )   59  
 10  1152 x 768    ( 298mm x 180mm )   61  
 11   840 x 525    ( 217mm x 123mm )   66  
 12   800 x 512    ( 207mm x 120mm )   72  

I use "xrander -s 2 -r 62" for running fluxbox
which gives me a screen  of 1024x768 with a refresh rate of 62, conversely you can also select a screen with higher resolution.

You asked, now here's the pertinent part of my xorg.conf as configured by the Nvidia install program.

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    InputDevice    "stylus" "SendCoreEvents"
    InputDevice    "cursor" "SendCoreEvents"
    InputDevice    "eraser" "SendCoreEvents"
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
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "eraser"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "eraser"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "InputDevice"
    Identifier     "cursor"
    Driver         "wacom"
    Option         "Device" "/dev/input/wacom"
    Option         "Type" "cursor"
    Option         "ForceDevice" "ISDV4"        # Tablet PC ONLY
EndSection

Section "Monitor"
    Identifier     "AccuSync 70"
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5500]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5500]"
    Monitor        "AccuSync 70"
    DefaultDepth    24
    SubSection     "Display"
        Depth       1
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

---

### Post by fable on 2007-05-03
Thanks for the very detailed information.

Your xorg.conf is very similar to mine, exept mu xorg.conf includes the monitor horizontal and vertical frequency range.  The driver name is the same, i.e. 'nvidia'.  Therefore, I think the main difference is the nVidia kernel.

I downloaded the nVidia driver from the nVidia.com site. I ran the nVidia installer per instruction but the installation failed. I tried to go back to the nVidia legacy driver with Synpatic but I got the following error message 'E: /var/cache/apt/archives/nvidia-glx-legacy_1.0.7184+2.6.20.5-15.20_i386.deb: subprocess pre-installation script returned error exit status 2".  

I don't know how to rebuild the nVidia kernel manually.  So I use Automatix2 to re-install a new nvidia driver because I think Automatix2 does rebuild the nVidia kernel.  Automatix2 was able to install a new driver without error but the new driver still does not allow me to start X.  

At console mode, I was able to manually re-install the legacy driver using 'sudo apt-get install nvidia-glx-legacy'.  This time I don't have the above error message.  When I reboot all I have to do is to reconfigure xorg.conf using 'sudo dpkg-reconfigure xserver-xorg'.  My PC is working with the nVidia card again but still maximum resolution limited to 1024x768.

I'll continue to explore and hopefully I''ll find a driver that will give me the higher resolution and compatible with Google Earth.

---

### Post by threegremlins on 2007-05-03
Perhaps instead of changing or reconfiguring the driver, you could find something to reconfigure the monitor setting so Nvidia will let you use a higher resolution.

Did a quick search "monitor resolution" and came across this thread it should help you

[http://ubuntuforums.org/showthread.php?t=424165&highlight=monitor+resolution](http://ubuntuforums.org/showthread.php?t=424165&highlight=monitor+resolution)

---

### Post by fable on 2007-05-04
The suggestion in the link did not work for me.

I edited the xorg.conf file to leave only 1280x1024 resolution.  I reboot the computer.  The resolution remains the same as 1024x768.  It looks like xorg.conf is not the only config file that determines the screen resolution.

Thanks for your suggestion anyway.  I'll continue my search.  This search process help me learn so much more about Linux and Ubuntu.

---

### Post by fable on 2007-05-04
After reading up on many forum articles on resolution problem, I finally resolved the problem.  Now I can use my nVidia GeForce card with  high resolution 1280x1024 to view Google Earth.

The Google Earth "not recognize the video card" problem was solved by adding in /etc/X11/xorg.conf, "Device" section, the lines:

```
Option  "AddARGBVisuals"  "True"
Option  "AddARGBLXVisuals"  "True"
```

and in the "Screen" section, the line:

```
Option  "AllowGLXWithComposite"  "True"
```

The low resolution problem is cause by using an old monitor that does not support DDC/EDID.  
The problem was resolved by adding in /etc/X11/xorg.conf, "monitor" section, the line:

```
Option "DDC" "False"
```

---

