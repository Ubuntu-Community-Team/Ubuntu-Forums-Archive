---
title: "can't change refresh rate"
date: 2007-01-22
forum: General Help
---

### Post by neomi on 2007-01-22
help! my screen resolution preference doesn't work

I've just installed my NVIDIA driver as usuall, but after that I can't change my refresh rate

It feels that the refresh rate has fixed on 85hz, and the drop down list only shows between 52hz ~ 67hz

what's wrong?

I use offical driver from NVIDIA all the time, this is the first time such thing happen

---

### Post by renzokuken on 2007-01-22
you could always edit the xorg.conf and manually enter the correct refresh rate there

```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Moloko on 2007-01-26
Try this:

[http://doc.gwos.org/index.php/ChangeResolution](http://doc.gwos.org/index.php/ChangeResolution)
[http://www.sh.nu/nvidia/gtf.php](http://www.sh.nu/nvidia/gtf.php)
[http://www.bohne-lang.de/spec/linux/modeline/](http://www.bohne-lang.de/spec/linux/modeline/)

Good luck.

---

### Post by aPello on 2007-01-26
```

sudo gedit /etc/X11/xorg.conf

```
find the line that says this:

```

Section "Monitor"

```
And the lines that look somethine like this:
```

	HorizSync	28-57
	VertRefresh	43-60

```

Set to be the high and low of what your monitor needs like so:
```

	HorizSync	LOW-HIGH
	VertRefresh	LOW-HIGH

```

Becareful tho, you can possibly damage your monitor if you set it to high.

---

### Post by CowzRule on 2007-01-26
I have the same problem. Here's what I do to fix it.
Go to the website of the company that makes your monitor. Mine is a Viewsonic, so I Googled viewsonic and got their website. I then looked up the model (E70f) of my monitor and found the spec for its Horizontal (30.0 - 70.0) and Vertical (50.0 - 150.0) refresh ranges.
Now I opened my xorg.conf file```
sudo gedit /etc/X11/xorg.conf
```and put those values in the "Monitor" section.
```
Section "Monitor"
	Identifier   "E70f"
	[color=red]HorizSync    30.0 - 70.0
	VertRefresh  50.0 - 150.0[/color]
	Option	    "DPMS"
EndSection
```Then I just rebooted and was able to select the refresh rate I wanted. I run my monitor at 1024x768 @ 85hz, however, if I want to go to 1280x1024, I can, but I only get 60hz and can't select anything else because my monitor doesn't support that refresh at that resolution.

---

### Post by Moloko on 2007-01-26
Using the links that posted before, I changed the **/etc/X11/xorg.conf** file to get 1400x1050@85Hz, the original settings only allow 60Hz and 75Hz, the relevant parts are in bold:

```

Section "Monitor"
  identifier "CPD-E430"
  [B]DisplaySize 365 274
  HorizSync 30-96 
  VertRefresh 48-170 [/B]
  modelname "Custom 1"
  modeline  "640x480@60" 25.2 640 656 752 800 480 490 492 525 -vsync -hsync
  modeline  "640x480@72" 31.5 640 664 704 832 480 489 491 520 -vsync -hsync
  modeline  "640x480@75" 31.5 640 656 720 840 480 481 484 500 -vsync -hsync
  modeline  "640x480@85" 36.0 640 696 752 832 480 481 484 509 -vsync -hsync
  modeline  "800x600@56" 36.0 800 824 896 1024 600 601 603 625 +hsync +vsync
  modeline  "800x600@72" 50.0 800 856 976 1040 600 637 643 666 +hsync +vsync
  modeline  "800x600@75" 49.5 800 816 896 1056 600 601 604 625 +hsync +vsync
  modeline  "800x600@85" 56.3 800 832 896 1048 600 601 604 631 +hsync +vsync
  modeline  "800x600@60" 40.0 800 840 968 1056 600 601 605 628 +hsync +vsync
  modeline  "832x624@75" 57.284 832 864 928 1152 624 625 628 667 -vsync -hsync
  modeline  "1024x768@85" 94.5 1024 1072 1168 1376 768 769 772 808 +hsync +vsync
  modeline  "1024x768@75" 78.8 1024 1040 1136 1312 768 769 772 800 +hsync +vsync
  modeline  "1024x768@70" 75.0 1024 1048 1184 1328 768 771 777 806 -vsync -hsync
  modeline  "1024x768@60" 65.0 1024 1048 1184 1344 768 771 777 806 -vsync -hsync
  modeline  "1024x768@43" 44.9 1024 1032 1208 1264 768 768 776 817 +hsync interlace +vsync
  modeline  "1152x864@75" 108.0 1152 1216 1344 1600 864 865 868 900 +hsync +vsync
  modeline  "1152x768@54" 64.995 1152 1178 1314 1472 768 771 777 806 +hsync +vsync
  modeline  "1280x854" 80.0 1280 1309 1460 1636 854 857 864 896 +hsync +vsync
  modeline  "1280x1024@75" 135.0 1280 1296 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@60" 102.1 1280 1360 1496 1712 960 961 964 994 -hsync +vsync
  modeline  "1280x960@85" 148.5 1280 1344 1504 1728 960 961 964 1011 +hsync +vsync
  modeline  "1280x1024@85" 157.5 1280 1344 1504 1728 1024 1025 1028 1072 +hsync +vsync
  modeline  "1280x1024@60" 108.0 1280 1328 1440 1688 1024 1025 1028 1066 +hsync +vsync
  modeline  "1280x960@75" 129.86 1280 1368 1504 1728 960 961 964 1002 -hsync +vsync
  modeline  "1400x1050@60" 122.61 1400 1488 1640 1880 1050 1051 1054 1087 -hsync +vsync
  modeline  "1400x1050@75" 155.85 1400 1496 1648 1896 1050 1051 1054 1096 -hsync +vsync
  **modeline  "1400x1050@85" 179.26 1400 1504 1656 1912 1050 1051 1054 1103 -hsync +vsync**
  modeline  "1600x1200@65" 175.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@60" 162.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@75" 202.5 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1600x1200@70" 189.0 1600 1664 1856 2160 1200 1201 1204 1250 +hsync +vsync
  modeline  "1792x1344@60" 204.8 1792 1920 2120 2448 1344 1345 1348 1394 -hsync +vsync
  modeline  "1856x1392@60" 218.3 1856 1952 2176 2528 1392 1393 1396 1439 -hsync +vsync
  modeline  "1920x1440@60" 234.0 1920 2048 2256 2600 1440 1441 1444 1500 -hsync +vsync
  modeline  "2048x1536@60" 266.95 2048 2200 2424 2800 1536 1537 1540 1589 -hsync +vsync
  gamma 1.0
EndSection

Section "Device"
  identifier "NVIDIA Corporation NV440A [GeForce 6200A nVidia Card]"
  boardname "NVIDIA GeForce 6 Series"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 0
  vendorname "NVIDIA"
  Option "BackingStore" "on"
EndSection

Section "Screen"
  Identifier "Default Screen"
  Device "NVIDIA Corporation NV440A [GeForce 6200A nVidia Card]"
  Monitor "CPD-E430"
  DefaultDepth 24
  SubSection "Display"
    depth 24
    virtual 2048 1536
    modes "1600x1200@75" "1600x1200@70" "1600x1200@65" "1400x1050@75" **"1400x1050@85"** "1920x1440@60" "1400x1050@60" "2048x1536@60" "1280x960@75" "1280x1024@60" "1280x1024@85" "1280x960@85" "1280x960@60" "1280x1024@75" "1280x854" "1152x768@54" "1152x864@75" "1024x768@43" "1024x768@60" "1024x768@70" "1024x768@75" "1024x768@85" "832x624@75" "800x600@60" "800x600@85" "800x600@75" "800x600@72" "800x600@56" "640x480@85" "640x480@75" "640x480@72" "640x480@60"
  EndSubSection
EndSection

Section "device" # 
  identifier "device1"
  boardname "NVIDIA GeForce 6 Series"
  busid "PCI:1:0:0"
  driver "nvidia"
  screen 1
  vendorname "NVIDIA"
EndSection
Section "screen" # 
  identifier "screen1"
  device "device1"
  defaultdepth 24
  monitor "monitor1"
EndSection
Section "monitor" # 
  identifier "monitor1"
  gamma 1.0
EndSection
Section "ServerFlags"
EndSection


```

---

