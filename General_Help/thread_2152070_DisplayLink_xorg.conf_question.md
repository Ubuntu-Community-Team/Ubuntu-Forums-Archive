---
title: "DisplayLink xorg.conf question"
date: 2013-06-06
forum: General Help
---

### Post by gnuoogle on 2013-06-06
I currently have a DisplayLink usb2.0 -> HDMI adapter working (giving the 'green screen of triumph')  but I do not know how to add entry to xorg.conf such that I can use this screen...

currently my xorg looks as-follows: 
```

Section "ServerLayout"
    Identifier     "X.org Configured"
    Screen      0  "DisplayLinkScreen" 0 0
    Screen      1  "Intel-Screen-HDMI" LeftOf "DisplayLinkScreen"
    Screen      2  "Intel-Screen-LVDS1" RightOf "DisplayLinkScreen"
    Option     "Xinerama" "on"
    Option  "clone" "off"
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

Section "InputDevice"
    Identifier  "Keyboard0"
    Driver      "kbd"
EndSection

Section "InputDevice"
    Identifier  "Mouse0"
    Driver      "mouse"
    Option        "Protocol" "auto"
    Option        "Device" "/dev/input/mice"
    Option        "ZAxisMapping" "4 5 6 7"
EndSection

Section "Device"
    Identifier  "IntelDevice"
    Driver      "intel"
    Option      "monitor-LVDS1" "LCD-Monitor"
    Option        "monitor-HDMI1" "HDMI-Monitor"
    VendorName  "Intel Corporation"
#    BusID       "PCI:0:2:0"
EndSection

Section "Screen"
    Identifier    "Intel-Screen-HDMI"
    Monitor        "HDMI-Monitor"
    Device        "IntelDevice"
    Subsection    "Display"
        DefaultDepth    24
        Modes    "1920x1080" "1600x1200" "1200x1024" "1280x960"
    EndSubsection
EndSection

Section "Screen"
    Identifier    "Intel-Screen-LVDS1"
    Monitor        "LCD-Monitor"
    Device        "IntelDevice"
    Subsection    "Display"
        DefaultDepth    24
        Modes    "1366x768" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection
################ DisplayLink Stuff ###################
Section "Device"
    Identifier      "DisplayLinkDevice"
    Driver          "fbdev"
    BusID           "USB"               # needed to use multiple DisplayLink devices 
    Option          "fbdev" "/dev/fb1"  # change to whatever device you want to use
#      Option          "rotate" "CCW"      # uncomment for rotation
EndSection

Section "Monitor"
    Identifier      "DisplayLink"
    Modeline "1920x1080_60.00"  173.00  1920 2048 2248 2576  1080 1083 1088 1120 -hsync +vsync
    Option "PreferredMode" "1920x1080_60.00"
    Option "DPMS" "true"
EndSection

Section "Screen"
    Identifier      "DisplayLinkScreen"
    Device          "DisplayLinkDevice"
    Monitor         "DisplayLink"
    Subsection    "Display"
        DefaultDepth    24
        Modes    "1920x1080" "1600x1200" "1200x1024" "1280x960"
    EndSubsection
EndSection

```

where my dmesg finds my display link as:
```

~$ dmesg | grep udlfb:
[  826.427511] udlfb: DisplayLink Plugable UGA-2K-A - serial #719084
[  826.427515] udlfb: vid_17e9&pid_0378&rev_0106 driver's dlfb_data struct at ffff8800a276f800
[  826.427516] udlfb: console enable=1
[  826.427517] udlfb: fb_defio enable=1
[  826.427518] udlfb: shadow enable=1
[  826.427607] udlfb: vendor descriptor length:22 data:22 5f 01 0020 05 00 01 03 00 04
[  826.427609] udlfb: DL chip limited to 2360000 pixel modes
[  826.427629] udlfb: allocated 4 65024 byte urbs
[  826.515140] udlfb: 1920x1080 @ 60 Hz valid mode
[  826.515150] udlfb: 720x400 @ 70 Hz valid mode
[  826.515154] udlfb: 640x480 @ 60 Hz valid mode
[  826.515157] udlfb: 640x480 @ 67 Hz valid mode
[  826.515161] udlfb: 640x480 @ 72 Hz valid mode
[  826.515164] udlfb: 640x480 @ 75 Hz valid mode
[  826.515167] udlfb: 800x600 @ 56 Hz valid mode
[  826.515172] udlfb: 800x600 @ 60 Hz valid mode
[  826.515176] udlfb: 800x600 @ 72 Hz valid mode
[  826.515179] udlfb: 800x600 @ 75 Hz valid mode
[  826.515183] udlfb: 832x624 @ 75 Hz valid mode
[  826.515186] udlfb: 1024x768 @ 60 Hz valid mode
[  826.515189] udlfb: 1024x768 @ 70 Hz valid mode
[  826.515193] udlfb: 1024x768 @ 75 Hz valid mode
[  826.515196] udlfb: 1280x1024 @ 75 Hz valid mode
[  826.515200] udlfb: 1152x864 @ 75 Hz valid mode
[  826.515203] udlfb: 1680x1050 @ 60 Hz valid mode
[  826.515207] udlfb: 1600x1200 @ 60 Hz valid mode
[  826.515211] udlfb: 1440x900 @ 60 Hz valid mode
[  826.515214] udlfb: 1400x1050 @ 60 Hz valid mode
[  826.515217] udlfb: 1280x1024 @ 60 Hz valid mode
[  826.515221] udlfb: 1280x960 @ 60 Hz valid mode
[  826.515224] udlfb: 1152x864 @ 75 Hz valid mode
[  826.515227] udlfb: 640x400 @ 70 Hz valid mode
[  826.515231] udlfb: Reallocating framebuffer. Addresses will change!
[  826.517168] udlfb: 1920x1080 @ 60 Hz valid mode
[  826.517175] udlfb: set_par mode 1920x1080
[  826.529838] udlfb: DisplayLink USB device /dev/fb1 attached. 1920x1080 resolution. Using 8104K framebuffer memory

```

and where my other monitors are as follows:
```

Screen 0: minimum 320 x 200, current 3286 x 1080, maximum 32767 x 32767
LVDS1 connected 1366x768+1920+157 (normal left inverted right x axis y axis) 309mm x 174mm
HDMI1 connected 1920x1080+0+0 (normal left inverted right x axis y axis) 597mm x 336mm

```


I want to get these three screens working -- I'm not sure how to proceed... currently the xorg.conf I have provided seems to freeze up my computer on boot.

Anybody got some good step-by-step tips on how to xorg.conf?  I see lots of people on here saying "I added a configuration to xorg.conf and it worked"  but I'd love to see what you mean by that... thanks in advance!

(PS: running ubuntu 13.04, 3.8.5-030805-generic #201303281651 SMP Thu Mar 28 20:52:32 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux)

---

### Post by celluloid on 2013-06-30
Hi there!

Try upgrading your kernel to the 3.10rc series from the Mainline PPA.
This kernel allows my DisplayLink adapter to work out of the box! (with the occasional tweaking of my display settings, and then logging out and back in!)

Also, the device seems to slow down my whole Ubuntu session - the only way around this for me was to use either KDE or XFCE (I guess it's to do with Compiz & different compositing)

---

### Post by userfriendly on 2013-07-04
> **celluloid said:**
> Hi there!

Try upgrading your kernel to the 3.10rc series from the Mainline PPA.
This kernel allows my DisplayLink adapter to work out of the box! (with the occasional tweaking of my display settings, and then logging out and back in!)

Also, the device seems to slow down my whole Ubuntu session - the only way around this for me was to use either KDE or XFCE (I guess it's to do with Compiz & different compositing)

Trying to get a "Plugable UGA-165" to work here. I'm on a Lenovo X220, with a Dell 24" connected to the DisplayPort output, and the USB VGA adapter connected to a wee 17" Dell next to it.

Installed the 3.10 kernel from the mainline ppa, getting a green screen on the 17" Dell when plugging it in, but it's not appearing in the display settings at all.

Which DisplayLink adapter are you using that works out of the box for you?

***Edited to add:***

If I put an xorg.conf into /etc/X11 which *only* has the DisplayLink device and screen in it, it works - only that screen though, no X on the 24" Dell and the built-in screen.

As soon as I try to add the integrated graphics device and the two other screens to the xorg.conf, the DisplayLink screen freezes and the other two screens look weird (X kind of works, even though with wrong resolutions, ratio, and colour depth).

Bit frustrating, as this implies that the device is working perfectly fine and I'm hitting 'merely' a configuration roadblock...

---

### Post by joel3 on 2013-08-04
Hi,

I am building kernel 3.10.5 and trying to get displaylink to work with X on Ubuntu 12.04 but just get a black screen with the udl drm driver, or a green screen with udlfb.

Could you provide some clarification with your post below, if its ok,

1. Did you use the udl drm driver or the old udlfb driver?
2. Did the display working without *any* requirements to have a custom xorg.conf (in other words by out of the box do you mean you just plugged in and it works? almost everyone seems to need to hack an xorg.conf of some sort for this to work)
3. Did you see the Display detect in the Settings->Displays window, or xrandr?

I am also seeing some peculiar behavior based on some experiments.

The display does show the splash or console (ctrl+alt+f1) if I set the nomodeset kernel boot arg, but still X just shows black screen even with nomodeset.

Did you experiment with the nomodeset bootarg to get it working for you?

Thanks in advance for sharing your experiences with displaylink usb adapter.

Regards,

-Joel

> **celluloid said:**
> Hi there!

Try upgrading your kernel to the 3.10rc series from the Mainline PPA.
This kernel allows my DisplayLink adapter to work out of the box! (with the occasional tweaking of my display settings, and then logging out and back in!)

Also, the device seems to slow down my whole Ubuntu session - the only way around this for me was to use either KDE or XFCE (I guess it's to do with Compiz & different compositing)

---

### Post by thephi2 on 2013-08-31
This is my first post here so first thing first Hi to all!
I'm trying too (since 4 days) to connect an USB external monitor (my AOC E1659Fwu) to my Ubuntu 13.04.
My kernel has been upgraded to 3.10.10-031010-generic since apparently it's working better with this upgraded version.

Now, apparently, there's the problem of configuring /etc/X11/xorg.conf... and I am very new to that in fact. How to find the right configuration?
Here's my config file :
> 
Section "Device"
              Identifier "DisplayLinkDevice"
              driver "displaylink"         # Or fbdev depending on what you installed
              Option "fbdev" "/dev/fb0"    # You have to use the correct framebuffer device here
EndSection

Section "Monitor"
               Identifier "DisplayLinkMonitor"
           EndSection

Section "Screen"
              Identifier "Default Screen"
              Device "DisplayLinkDevice"
              Monitor "DisplayLinkMonitor"
              SubSection "Display"
                  Depth 16         # 24bit works fine but for USB 2.0 a lot of data
                   Modes "1280x1024"
    EndSubSection
EndSection

Section "ServerLayout"
                 Identifier "Server Layout"
                 Screen 0 "Default Screen" 0 0
                 Option "AllowMouseOpenFail" "True"
                 InputDevice "Keyboard0" "CoreKeyboard"
                  InputDevice "Mouse0" "CorePointer"
EndSection

Section "ServerFlags"
                   Option "AllowEmptyInput" "false"
                   Option "AutoAddDevices" "false"
                   Option "AutoEnableDevices" "false"
EndSection

Section "InputDevice"
                 Identifier "Keyboard0"
                 Driver "void"
EndSection

Section "InputDevice"
                  Identifier "Mouse0"
                  Driver "void"
EndSection
The result of my DMESG command is :
```
  435.503867] usb 2-3: USB disconnect, device number 4
[  461.369523] usbcore: registered new interface driver udlfb
[  465.916140] usb 2-3: new high-speed USB device number 5 using ehci-pci
[  466.049308] usb 2-3: New USB device found, idVendor=17e9, idProduct=ff05
[  466.049319] usb 2-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[  466.049327] usb 2-3: Product: E1659Fwu
[  466.049335] usb 2-3: Manufacturer: DisplayLink
[  466.049341] usb 2-3: SerialNumber: GHND7JA000527
[  468.504933] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  468.507179] sd 6:0:0:0: [sdb] Asking for cache data failed
[  468.507185] sd 6:0:0:0: [sdb] Assuming drive cache: write through


```
and the result of cat /proc/fb :
```
0 inteldrmfb


```
and from lsusb :
```
0 inteldrmfb


```

Thanks!

---

### Post by thephi2 on 2013-09-01
Okay, I've understood the problem.
In fact, DisplayLink didn't make the effort to release a USB 3.0 version  of the driver. When the USB 2.0 Displaylink was working very easily  (even "out of the "box" with the 3.10 kernel), the USB 3.0 (which is on  more and more devices) is stuck. 
What a shame! It's one year now and they didn't provide any solution. Only for windows (and not even for MAC) :sad:
[http://www.displaylink.org/forum/showthread.php?t=1748](http://www.displaylink.org/forum/showthread.php?t=1748)

---

