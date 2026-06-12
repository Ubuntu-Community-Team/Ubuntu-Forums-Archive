---
title: "Another xorg.conf"
date: 2007-10-27
forum: General Help
---

### Post by Luuse on 2007-10-27
Hi

I've been trying to configure xorg.conf on my own for the first time because i got a really old tv which I want to display movies and such stuff on and the gui program can't do that for me...

Anyway, I've more or less just been doing some formating according to me. But when i try to reboot with it it tries to start a few times but gives up after that and launches some backup/failsafe config which i believe is the section bellow. Also at this point it shows some gui tool which says that my screen/graphics card could not be found and helps me to get back some working options.

```
# Begin failsafe screen
Section "Device"
    Identifier    "Failsafe Device"
    Boardname    "vesa"
    Busid        "PCI:1:0:0"
    Driver        "nvidia"
    Screen    0
EndSection

Section "Monitor"
    Identifier    "Failsafe Monitor"
    Vendorname    "Samsung"
    Modelname    "Samsung SyncMaster 700NF"
    Horizsync    30-96
    Vertrefresh    50-160
    modeline    "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
    modeline    "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
    modeline    "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
    modeline    "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
    modeline    "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
    modeline    "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
    modeline    "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
    modeline    "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
    modeline    "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
    modeline    "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
    modeline    "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
    modeline    "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
    modeline    "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
    modeline    "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
    modeline    "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
    modeline    "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
    Gamma        1.0
EndSection

Section "Screen"
    Identifier    "Default Screen"
    Device        "Failsafe Device"
    Monitor        "Failsafe Monitor"
    Defaultdepth    24
    SubSection "Display"
        Depth    24
Modes        "1280x1024@60"    "1280x1024@85"    "1280x1024@75"    "1024x768@43"    "1024x768@60"    "1024x768@70"    "1024x768@75"    "1024x768@85"    "800x600@60"    "800x600@85"    "800x600@75"    "800x600@72"    "800x600@56"
    EndSubSection
EndSection
# End failsafe screen
```I'm totally lost after trying to figure this out for two days so I've probably just stared myself blind and there's just some simple syntax error...

The entire xorg.conf can be found [here]("http://www.thelucifer.net/tmp/xorg_conf.txt").

Glad for **any** ideas and/or directions :)

I got a NVidia GeForce 7600 GS with the prop drivers installed by the way.

// Luuse

---

### Post by PmDematagoda on 2007-10-27
Post your proper xorg.conf file using:-

```
gedit /etc/X11/xorg.conf
```

---

### Post by Luuse on 2007-10-27
Already up [here]("http://www.thelucifer.net/tmp/xorg_conf.txt"). Might have been a bit unclear about that in my first post... Just thought it was a bit too big to post it as text in the post.

---

### Post by PmDematagoda on 2007-10-27
Ok, try this:-

1) Download the latest Nvidia driver for Linux from the website. The installation instructions are given there as well.

2) You may install the drivers through Recovery Mode or by killing the X-server, but I'm not sure about killing X-server and Recovery Mode is more reliable.

3) Then reconfigure the X-server using:-

```
sudo dpkg-reconfigure xserver-xorg
```

Then try to see if the GUI works properly.

---

### Post by Luuse on 2007-10-27
So there's nothing wrong with the config file?

Because I doubt that the drivers that I installed through the proprietary driver manager tool doesn't work. I tried to run "glxinfo | grep rendering" which says yes and glxgears works fine which have never happened before I installed the drivers.on earlier ubuntu releases. Even the included desktop effects works like a charm (just tried them to check if it worked, I don't have them activated now).

---

### Post by PmDematagoda on 2007-10-27
If the desktop effects work then you must be using the Nvidia drivers properly.

---

### Post by Luuse on 2007-10-27
> **PmDematagoda said:**
> ... then you must be using the Nvidia drivers properly.

Hehe yea.

I wish it would have been that easy but I'm not that lucky ;)

---

