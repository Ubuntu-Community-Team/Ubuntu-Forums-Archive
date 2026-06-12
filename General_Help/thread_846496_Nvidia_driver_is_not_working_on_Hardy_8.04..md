---
title: "Nvidia driver is not working on Hardy 8.04."
date: 2008-07-01
forum: General Help
---

### Post by berserkpi on 2008-07-01
Hi, I'm new here, so, if I'm not respecting some kind of posting-protocol, plz let me know it.

I'm running a Hardy 8.04 (2.6.24-19-generic) with a graphic card: nVidia Corporation GeForce 8400M GS.

I installed the driver from NVIDIA (NVIDIA-Linux-x86-173.14.05-pkg1). Exactly what I did is:

1. Log-out
2. Ctrl-Alt-F1 (just-console-mode)
3. Login as root
4. sudo /etc/init.d/gdm stop
5. Execute the installation. This changed automatically the /etc/X11/xorg.conf. Wich looks ok (look out below).
6. After the Install, I executed : /etc/init.d/gdm start
7. reboot.

That's all. But Ubuntu is booting in low resolution and if I execute nvidia-settings it says something like: "You do not appear to be using the NVIDIA X driver."

The strangest thing is that I followed the same procedure the first time I installed Ubuntu 8.04 (2.6.24-[COLOR="Red"]16[/COLOR]-generic). The problem came when I updated the kernel.

Any help is welcome. :) Thanks in advanced.

My xorg.conf:

> 
Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0"
    InputDevice    "Keyboard0" "CoreKeyboard"
    InputDevice    "Mouse0" "CorePointer"
EndSection

Section "Files"
    RgbPath         "/usr/X11R6/lib/X11/rgb"
EndSection

Section "Module"
    Load           "dbe"
    Load           "extmod"
    Load           "type1"
    Load           "freetype"
    Load           "glx"
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
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Unknown"
    HorizSync       30.0 - 110.0
    VertRefresh     50.0 - 150.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

---

### Post by sdennie on 2008-07-01
Try the suggestion in this post: [http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2](http://ge.ubuntuforums.com/showpost.php?p=4970051&postcount=2).  Then reinstall the nvidia driver and reboot.  If that doesn't work then try this post: [http://ubuntuforums.org/showthread.php?t=797270](http://ubuntuforums.org/showthread.php?t=797270)

---

### Post by berserkpi on 2008-07-01
I've already tried the first one. The second link looks helpfull, I'll try it.

Thanks a lot.

---

