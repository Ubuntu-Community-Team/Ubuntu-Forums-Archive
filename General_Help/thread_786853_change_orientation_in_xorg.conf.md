---
title: "change orientation in xorg.conf"
date: 2008-05-08
forum: General Help
---

### Post by mikef_542 on 2008-05-08
Hi:

I read this post, [  ]("http://ubuntuforums.org/showthread.php?t=763912&highlight=orientation") and understand how to use xrandr to change display settings.

What I am looking for is the syntax for the xorg.conf file that will tell my second montor to display a left orientation.

```
Section "Device"
    Identifier     "Videocard0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    BusID          "PCI:1:0:0"
    Screen          0
EndSection

Section "Device"
    Identifier     "Videocard1"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 7300 SE/7200 GS"
    Option         "RandRRotation" "on"
    BusID          "PCI:1:0:0"
    Screen          1
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "Generic Video Card"
    Monitor        "DELL 2405FPW"
    DefaultDepth    24
    SubSection     "Display"
        Virtual     1920 1200
        Depth       24
        Modes      "1920x1200@60" "1680x1050@75" "1680x1050@60" "1600x1024@60" "1440x900@60" "1440x900@75" "1280x800@60" "1280x768@75" "1280x800@75" "1280x720@60" "1280x768@60" "800x600@60" "800x600@75" "800x600@72" "800x600@56"
    EndSubSection
EndSection

Section "Screen"

 #              
    Identifier     "screen1"
    Device         "Videocard0"
    Monitor        "Monitor1"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "DFP: nvidia-auto-select +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection
```


Thank you for your help.

Mike

---

### Post by mikef_542 on 2008-05-08
Bump

---

### Post by unutbu on 2008-05-08
Perhaps try one of these:

[http://www.ubuntugeek.com/dual-monitors-with-nvidia.html](http://www.ubuntugeek.com/dual-monitors-with-nvidia.html)
[http://gentoo-wiki.com/HOWTO_Dual_Monitors](http://gentoo-wiki.com/HOWTO_Dual_Monitors)

These xorg.conf's are a little old, but if you're impatient and just want to try something: here are two examples:

[http://lists.freebsd.org/pipermail/freebsd-questions/2005-May/087929.html](http://lists.freebsd.org/pipermail/freebsd-questions/2005-May/087929.html)
[http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf](http://wiki.osuosl.org/display/howto/Set+Up+Dual+Monitors+-+xorg.conf)

The critical line seems to be 

```
Section "ServerLayout"
    Identifier  "Default Layout"
    Screen      "screen0"
**    Screen      "screen1" RightOf "screen0"**
    InputDevice "Generic Keyboard"
    InputDevice "Configured Mouse"

    # Don't forget xinerama!!!111oneoneone11!eleven!!11
    Option "xinerama" "on"
    Option "clone" "off"
EndSection
```

---

### Post by mikef_542 on 2008-05-08
Thank you for your reply.

I have the dual monitors running np.

The issue I am having is I want the second monitor to be rotated 90 degrees.
Some call it Landscape view, others don't but I like one of my wide screens long ways to read lengthly web pages or spec docs from PM's.

My monitor is LeftOf and that works great.

And PS xinerama has been deprecated for xrandr, [http://en.wikipedia.org/wiki/Xinerama]("http://en.wikipedia.org/wiki/Xinerama")

I think I need an option in either the section monitor, device, or screen.
I am just not sure what option and where to put it.

Thanks for all help.

---

### Post by unutbu on 2008-05-09
Maybe you'll find an answer here:
[http://ubuntuforums.org/showthread.php?t=587686&page=3](http://ubuntuforums.org/showthread.php?t=587686&page=3)

---

### Post by Zorael on 2008-05-09
With [FONT="Courier New"]RandRRotation[/FONT] enabled, can't you just use xrandr to rotate it at will?
```
$ xrandr -screen 1 -o left
```

That said, I think you should get what you want by adding this into a screen section.
```
Option "Rotate" "CCW"
```

---

### Post by ryanhaigh on 2008-05-09
[This page]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html") has all the available options for the nvidia driver.

> Option "Rotate" "string"

    Enable static rotation support. Unlike the RandRRotation option above, this option takes effect as soon as the X server is started and will work with older versions of X. This feature is supported on GeForce2 or better hardware using depth 24. This feature does not work with hardware overlays, and emulated overlays will be used instead at a substantial performance penalty. This option is not compatible with the RandR extension. Valid rotations are "normal", "left", "inverted", and "right". Default: off.


---

### Post by mikef_542 on 2008-05-14
Thanks to ryanhaigh, and Zorael for their posts. 

I used the Option "Rotate" "left" and that worked great.

This doc,
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html")
and this 
[ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-g.html]("ftp://download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-g.html")

are great resources for configuring your monitors when using the Nvidia video card.

Thanks for all your help.

---

