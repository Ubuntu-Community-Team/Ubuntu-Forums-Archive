---
title: "nVidia update disabled desired resolution"
date: 2013-04-10
forum: General Help
---

### Post by kansasnoob on 2013-04-10
Today there was a security update to 'nvidia-current' in Precise:

> nvidia-graphics-drivers-updates (304.88-0ubuntu0.0.1) precise-security; urgency=low

  * SECURITY UPDATE: ARGB Cursor Buffer Overflow in "NoScanout" Mode
    - CVE-2013-0131

  * New upstream release
    - Fixed CVE-2013-0131:
      NVIDIA UNIX GPU Driver ARGB Cursor Buffer Overflow in
      "NoScanout" Mode. This buffer overflow, which occurred
      when an X client installed a large ARGB cursor on an
      X server running in NoScanout mode, could cause a denial
      of service (e.g., an X server segmentation fault), or
      could be exploited to achieve arbitrary code execution.

  [ Alberto Milone ]
  * debian/dkms.conf{.in}:
    - Drop all the patches.
  * debian/substvars:
    - Add support for xorg-video-abi-14.

 -- Alberto Milone <alberto.milone@canonical.com>  Thu, 04 Apr 2013 13:40:29 +0200


But along with that they dropped other patches and in my case it removed my desired resolution of 1440x900. This is the xrandr with the old driver:

```
lance@lance-AMD-desktop:~$ xrandr
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 320 x 240, current 1440 x 900, maximum 1680 x 1050
default connected 1440x900+0+0 0mm x 0mm
   1680x1050      50.0     51.0     52.0     53.0     54.0  
   1600x1024      55.0  
   **1440x900       56.0*** 
   1400x1050      57.0     58.0     59.0     60.0     61.0  
   1360x768       62.0     63.0  
   1280x1024      64.0     65.0  
   1280x960       66.0  
   1152x864       67.0     68.0     69.0     70.0  
   1024x768       71.0     72.0     73.0  
   960x720        74.0  
   960x600        75.0  
   960x540        76.0  
   928x696        77.0  
   896x672        78.0  
   840x525        79.0     80.0     81.0     82.0  
   832x624        83.0  
   800x600        84.0     85.0     86.0     87.0     88.0     89.0     90.0     91.0  
   800x512        92.0  
   720x450        93.0  
   680x384        94.0     95.0  
   640x512        96.0     97.0  
   640x480        98.0     99.0    100.0    101.0    102.0    103.0  
   576x432       104.0    105.0    106.0    107.0  
   512x384       108.0    109.0    110.0  
   416x312       111.0  
   400x300       112.0    113.0    114.0    115.0  
   320x240       116.0    117.0    118.0  
```

And here's the xrandr with the new driver:

```
lance@lance-AMD-desktop:~$ xrandr
Screen 0: minimum 8 x 8, current 1680 x 1050, maximum 4096 x 4096
VGA-0 connected 1680x1050+0+0 (normal left inverted right x axis y axis) 474mm x 297mm
   **1680x1050      60.6*+   74.9**  
   1600x1200      75.0     60.0  
   1400x1050      74.9     60.0  
   1280x1024      75.0     60.0  
   1280x960       60.0  
   1152x864       75.0  
   1024x768       75.0     70.1     60.0  
   800x600        75.0     72.2     60.3     56.2  
   640x480        75.0     72.8     59.9  
```

Any thoughts on how I can get the desired mode back in the updated driver?

The xorg.conf has very little in it:

```

Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection
```

A long time ago I used this same monitor with Intel graphics and I'd have to use this xorg.conf:

```
Section "ServerLayout"
	Identifier     "X.org Configured"
	Screen      0  "Screen0" 0 0
	InputDevice    "Mouse0" "CorePointer"
	InputDevice    "Keyboard0" "CoreKeyboard"
EndSection

Section "Files"
	ModulePath   "/usr/lib/xorg/modules"
	FontPath     "/usr/share/fonts/X11/misc"
	FontPath     "/usr/share/fonts/X11/cyrillic"
	FontPath     "/usr/share/fonts/X11/100dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/75dpi/:unscaled"
	FontPath     "/usr/share/fonts/X11/Type1"
	FontPath     "/usr/share/fonts/X11/100dpi"
	FontPath     "/usr/share/fonts/X11/75dpi"
	FontPath     "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
	FontPath     "built-ins"
EndSection

Section "Module"
	Load  "dbe"
	Load  "dri"
	Load  "dri2"
	Load  "extmod"
	Load  "record"
	Load  "glx"
EndSection

Section "InputDevice"
	Identifier  "Keyboard0"
	Driver      "kbd"
EndSection

Section "InputDevice"
	Identifier  "Mouse0"
	Driver      "mouse"
	Option	    "Protocol" "auto"
	Option	    "Device" "/dev/input/mice"
	Option	    "ZAxisMapping" "4 5 6 7"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        Modeline     "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
        Option       "PreferredMode" "1440x900_60.00"
EndSection

Section "Device"
        ### Available Driver options are:-
        ### Values: <i>: integer, <f>: float, <bool>: "True"/"False",
        ### <string>: "String", <freq>: "<f> Hz/kHz/MHz"
        ### [arg]: arg optional
        #Option     "NoAccel"            	# [<bool>]
        #Option     "SWcursor"           	# [<bool>]
        #Option     "ColorKey"           	# <i>
        #Option     "CacheLines"         	# <i>
        #Option     "Dac6Bit"            	# [<bool>]
        #Option     "DRI"                	# [<bool>]
        #Option     "NoDDC"              	# [<bool>]
        #Option     "ShowCache"          	# [<bool>]
        #Option     "XvMCSurfaces"       	# <i>
        #Option     "PageFlip"           	# [<bool>]
	Identifier  "Card0"
	Driver      "intel"
	VendorName  "Intel Corporation"
	BoardName   "82945G/GZ Integrated Graphics Controller"
	BusID       "PCI:0:2:0"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes    "1440x900@60"
	EndSubSection
EndSection
```

So I sort of think I could just add the "Monitor" and "Screen" sections of that to my xorg.conf like this but I'm not sure:

```
Section "Device"
	Identifier	"Default Device"
	Option	"NoLogo"	"True"
EndSection

Section "Monitor"
	Identifier   "Monitor0"
	VendorName   "Monitor Vendor"
	ModelName    "Monitor Model"
        Modeline     "1440x900_60.00"  106.50  1440 1528 1672 1904  900 903 909 934 -hsync +vsync
        Option       "PreferredMode" "1440x900_60.00"
EndSection

Section "Screen"
	Identifier "Screen0"
	Device     "Card0"
	Monitor    "Monitor0"
	SubSection "Display"
		Viewport   0 0
		Depth     1
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     4
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     8
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     15
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     16
                Modes    "1440x900@60"
	EndSubSection
	SubSection "Display"
		Viewport   0 0
		Depth     24
                Modes    "1440x900@60"
	EndSubSection
EndSection
```

I've been lucky enough that I haven't had to mess with an xorg.conf in a very, very long time:)

---

### Post by kansasnoob on 2013-04-10
It took a while but I found that old Intel graphics thread of mine:

[http://ubuntuforums.org/showthread.php?t=1462350](http://ubuntuforums.org/showthread.php?t=1462350)

I'm cross-testing Quantal on that box now to see if it's also effected. If so I'll check out Raring too.

---

### Post by mikewhatever on 2013-04-11
How about nvidia-settings? Can you add the correct resolution there?

---

### Post by kansasnoob on 2013-04-11
> **mikewhatever said:**
> How about nvidia-settings? Can you add the correct resolution there?

It did before this update but not now. I haven't figured it out yet so I just keep reverting to the old driver.

I think it's actually a bug but apport refused to let me file it as such :(

With read-edid installed parse-edid shows the 1440x900 resolution.

---

### Post by Locus Kiesselbachi on 2013-04-11
...just passing through!
I had a lot problems with nVidia.
[LOL]("http://www.youtube.com/watch?v=_36yNWw_07g")

---

### Post by kansasnoob on 2013-04-11
> **Locus Kiesselbachi said:**
> ...just passing through!
I had a lot problems with nVidia.
[LOL]("http://www.youtube.com/watch?v=_36yNWw_07g")

That's how I feel about them dropping this garbage into what should have been only a security fix:

> * debian/dkms.conf{.in}:
- Drop all the patches.
* debian/substvars:
- Add support for xorg-video-abi-14.

I'll figure this out soon I'm sure, but an LTS should never be dealt a regression like this!

---

### Post by kansasnoob on 2013-04-12
This is turning out to be a real nightmare :mad:

I decided to start from scratch so I blew away the old xorg.conf and created a new one using NVIDIA-settings:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.88  (buildd@roseapple)  Tue Apr  9 12:24:47 UTC 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HannStar Display Corp Hanns.G Hi221"
    HorizSync       24.0 - 94.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

This is really making me crazy!

And it does effect Precise, Quantal, and Raring.

---

### Post by kansasnoob on 2013-04-12
OK, after creating that new xorg.conf I had to add a line which I highlighted in red here:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.88  (buildd@roseapple)  Tue Apr  9 12:24:47 UTC 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HannStar Display Corp Hanns.G Hi221"
    HorizSync       24.0 - 94.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
    **[COLOR="#FF0000"]Option         "ModeValidation" "AllowNonEdidModes"[/COLOR]**
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Then I had to reboot -** just restarting X is not sufficient!**

Then I had to open Display Settings in System Settings after the reboot and set the desired resolution!

It's quite a convoluted process :(

I owe a debt of gratitude to *nerd65536* for this post:

[http://ubuntuforums.org/showthread.php?t=2072181&p=12304338#post12304338](http://ubuntuforums.org/showthread.php?t=2072181&p=12304338#post12304338)

Of course I've only done this once in Precise so I need to rinse-n-repeat in Quantal and Raring also ;^)

---

### Post by efflandt on 2013-04-12
if your video card and monitor have DVI and/or HDMI (or possibly DVI to HDMI cable in either direction), in other words digital video, the system might have better odds of selecting the proper native resolution than VGA (which generally has a generic default list).

My system updated to the 304.88 drivers, but not that I would notice, since I am using 310.14 experimental drivers that Steam recommends for its games (I forget if I am using HDMI or DVI to HDMI for my 1080p HDTV).
```
efflandt@XPS8100-1204:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-current                         304.88-0ubuntu0.0.2                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-experimental-310                310.14-0ubuntu0.3                       Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        304.88-0ubuntu0.0.2                     Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-experimental-310       310.14-0ubuntu0.1                       Tool for configuring the NVIDIA graphics driver
```

---

### Post by kansasnoob on 2013-04-12
> **efflandt said:**
> if your video card and monitor have DVI and/or HDMI (or possibly DVI to HDMI cable in either direction), in other words digital video, the system might have better odds of selecting the proper native resolution than VGA (which generally has a generic default list).

My system updated to the 304.88 drivers, but not that I would notice, since I am using 310.14 experimental drivers that Steam recommends for its games (I forget if I am using HDMI or DVI to HDMI for my 1080p HDTV).
```
efflandt@XPS8100-1204:~$ dpkg-query -l nvidia* | grep ii
ii  nvidia-common                          1:0.2.44.2                              Find obsolete NVIDIA drivers
ii  nvidia-current                         304.88-0ubuntu0.0.2                     NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-experimental-310                310.14-0ubuntu0.3                       Experimental NVIDIA binary Xorg driver, kernel module and VDPAU library
ii  nvidia-settings                        304.88-0ubuntu0.0.2                     Tool of configuring the NVIDIA graphics driver
ii  nvidia-settings-experimental-310       310.14-0ubuntu0.1                       Tool for configuring the NVIDIA graphics driver
```

I did try the experimental driver and it is also a no-go for my desired resolution :(

Regardless this **IS A BUG!**

Using 'read-edid' the resolution I want is supported but some *bone-head* at Canonical decided to include non-related updates in a security update. Sadly the same *bone-head* is evidently secure enough in his position at Canonical that he feels he can just disregard any real-life issues regarding his bone-headed decisions :(

---

### Post by kansasnoob on 2013-04-13
OK, the method described in posts #7 and #8 does work in Precise, Quantal, and Raring. Just a quick recap;

First open the NVIDIA settings GUI and select Save to X config file as shown here:

[ATTACH=CONFIG]241282[/ATTACH]

DO NOT select "merge with existing file" when asked!

When that is complete just Quit the NVIDIA settings GUI and open /etc/X11/xorg.conf as root with your desired text editor, eg;

```
sudo gedit /etc/X11/xorg.conf
```

Then add the following line to the Device section:

```
    Option         "ModeValidation" "AllowNonEdidModes"
```

Here's my edited Raring xorg.conf with the added line highlighted in red:

```
# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 304.88  (buildd@komainu)  Wed Apr 10 16:15:17 UTC 2013

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
    Option         "Xinerama" "0"
EndSection

Section "Files"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"
    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    # HorizSync source: edid, VertRefresh source: edid
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "HannStar Display Corp Hanns.G Hi221"
    HorizSync       24.0 - 94.0
    VertRefresh     56.0 - 76.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7025 / nForce 630a"
    **[COLOR="#FF0000"]Option         "ModeValidation" "AllowNonEdidModes"[/COLOR]**
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "Stereo" "0"
    Option         "nvidiaXineramaInfoOrder" "CRT-0"
    Option         "metamodes" "nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

```

Then be sure to save the change and just quit gedit or your preferred text editor.

Next just reboot, restarting X only seems not to be adequate!

After the reboot just open the Display settings GUI, eg: in Ubuntu or Ubuntu GNOME - System Settings -> Displays, and hopefully you'll find that the desired resolution is now included in the list:

[ATTACH=CONFIG]241283[/ATTACH]

Hope that may help someone else :)

---

### Post by kansasnoob on 2013-04-13
Dumb question. how do I mark this Solved?

---

### Post by kansasnoob on 2013-04-13
I found the answer:

[http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730](http://ubuntuforums.org/showthread.php?t=2121377&p=12536730#post12536730)

---

### Post by Matthew_Lang on 2013-09-28
Thank you SO MUCH! I've been trying to find a forum to help me all day. 

I've been looking in xrandr doing --addmode --newmode, etc., and that never worked. Doing this worked like a charm.

~Matt.

---

