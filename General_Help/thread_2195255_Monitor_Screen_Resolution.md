---
title: "Monitor Screen Resolution"
date: 2013-12-23
forum: General Help
---

### Post by thongpounder on 2013-12-23
Hello,

Firstly, sorry if this has been answered somewhere. If it is feel free to just point me in that direction. I just installed Ubuntu 12.04 and I'm having issue with screen resolutions for my Samsung SyncMaster 2032 NW. It's native resolution is 1680x1050 (16:10) but I can't seem to get beyond 1600x1200. I've tried forcing it by using xrandr, and it adds the mode successfully, but the image comes out scrunched into 4:3 for some unknown reason. I have AMD's recommended drivers for my Radeon HD 6xxx series, they are installed correctly. I'm sort of at a loss here. Why can't I get my monitors resolution? I know my card supports it. Any help with this would be most apprieceated. 

System Specs
OS: Ubuntu Precise Pangolin
CPU: AMD FX AMD FX(tm)-6100 Six-Core Processor × 6 3.3GHz
GPU: [SIZE=2]SAPPHIRE Radeon HD 6850 1GB 256-bit GDDR5 PCI Express 2.1 x16[/SIZE]
RAM: GSKILL G.SKILL Ripjaws Series DDR3 1333
Motherboard: ASUS M5A97 AM3+ AMD 970
PSU: Rosewill BRONZE Series RBR1000-M 1000W 

[PHP]pierre@pierre-pc:~$ fglrxinfo
display: :0.0  screen: 0
OpenGL vendor string: Advanced Micro Devices, Inc.
OpenGL renderer string: AMD Radeon HD 6800 Series  
OpenGL version string: 4.3.12618 Compatibility Profile Context 13.101[/PHP]

Thanks,
Pierre

---

### Post by ajgreeny on 2013-12-23
Can we see the output of the command ```
cat /etc/X11/xorg.conf
``` to see firstly if you have such a file, and secondly, if so, what it contains.

A simple edit of that file may be needed to give you the required resolution.

---

### Post by thongpounder on 2013-12-23
Hello

Thank you for the reply. Here is my xorgs.conf

```
pierre@pierre-pc:/# cat etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "amdcccle Layout"
    Screen      0  "amdcccle-Screen[1]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "0-DFP1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "Disable" "false"
    Option        "PreferredMode" "1024x768"
    Option        "TargetRefresh" "75"
    Option        "Position" "1440 0"
    Option        "Rotate" "normal"
EndSection

Section "Monitor"
    Identifier   "0-CRT1"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
    Option        "PreferredMode" "1440x900"
    Option        "TargetRefresh" "60"
    Option        "Position" "0 0"
    Option        "Rotate" "normal"
    Option        "Disable" "false"
EndSection

Section "Device"
    Identifier  "amdcccle-Device[1]-0"
    Driver      "fglrx"
    Option        "Monitor-DFP1" "0-DFP1"
    Option        "Monitor-CRT1" "0-CRT1"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "Default Screen"
    DefaultDepth     24
EndSection

Section "Screen"
    Identifier "amdcccle-Screen[1]-0"
    Device     "amdcccle-Device[1]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Virtual   2624 2624
        Depth     24
    EndSubSection
EndSection
```

I did try editing the preferred mode for CRT1 to 1680x1050 but it didn't seem to make much difference. I do have a second monitor and some of the settings seem to have skewed because of that. I've unplugged it as I was only planning on using it for a terminal screen. Thanks for the help!

Pierre

---

### Post by thongpounder on 2013-12-23
So I decided to try a reinstall of everything without the second monitor plugged in and now the issue is a little diffirent. xorg.conf now has no preferred resolution setting which I find odd. 

```
pierre@pierre-pc:/$ sudo cat etc/X11/xorg.conf
Section "ServerLayout"
    Identifier     "aticonfig Layout"
    Screen      0  "aticonfig-Screen[0]-0" 0 0
EndSection

Section "Module"
    Load  "glx"
EndSection

Section "Monitor"
    Identifier   "aticonfig-Monitor[0]-0"
    Option        "VendorName" "ATI Proprietary Driver"
    Option        "ModelName" "Generic Autodetecting Monitor"
    Option        "DPMS" "true"
EndSection

Section "Device"
    Identifier  "aticonfig-Device[0]-0"
    Driver      "fglrx"
    BusID       "PCI:1:0:0"
EndSection

Section "Screen"
    Identifier "aticonfig-Screen[0]-0"
    Device     "aticonfig-Device[0]-0"
    Monitor    "aticonfig-Monitor[0]-0"
    DefaultDepth     24
    SubSection "Display"
        Viewport   0 0
        Depth     24
    EndSubSection
EndSection


```

Furthermore, I went ahead and added the output to xrandr but now I get this error, when I try to set the resolution.

"GDBus.Error:org.gtk.GDBus.UnmappedGError.Quark._gnome_2drr_2derror_2dquark.Code2: could not set the configuration for CRTC 147"

Thanks,
Pierre.

---

### Post by thongpounder on 2013-12-26
Still no luck at all, I've now fubard several linux installs trying to figure this out. One thing I have noticed about my xorg.conf compaired to everyone else's I've seen is Option in front of most of the lines for Monitor on mine, yet the examples don't have that in front of anything.

---

### Post by tgalati4 on 2013-12-26
I have a similar monitor.  If you are using VGA, resolution is limited.  If you use DVI or HDMI then you can get full resolution.

---

