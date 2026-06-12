---
title: "Help Installing X Window"
date: 2008-04-30
forum: General Help
---

### Post by fdanderson on 2008-04-30
Hi All,

I'm very new to Linux and I've got Ubuntu installed on my desktop at home. I've been trying for days to install X Window but haven't been having any luck at all. :confused:

Whenever I try to start X (from shell using 'startx') I keep getting the following error message:

[PHP](EE) No devices detected.

Fatal server error:
no screens found
XIO:  fatal IO error 104 (Connection reset by peer) on X server ":0.0"
      after 0 requests (0 known processed) with 0 events remaining.
xauth:  error in locking authority file /home/administrator/.Xauthority[/PHP]

I've tried running dpkg-reconfigure xserver-xorg with no success. I've trawled through heaps of forum pages to try to find an answer and none of them work for me. I have noticed that a lot of problems seem to be caused by NVIDIA cards, which I have, but I've downloaded the latest drivers for them using the following commands:

[B][I]aptitude update
aptitude install module-assistant build-essentail
m-a prepare
m-a update
m-a a-i nvidia
aptitude install nvidia-glx[/I][/B]

I'm at a loss of what to do. Here's my Xorg.0.log after I try to start X:

[PHP]X Window System Version 1.3.0
Release Date: 19 April 2007
X Protocol Version 11, Revision 0, Release 1.3
Build Operating System: Linux Ubuntu (xorg-server 2:1.3.0.0.dfsg-12ubuntu8.3)
Current Operating System: Linux ubuntu 2.6.22-14-386 #1 Tue Feb 12 07:12:19 UTC 2008 i686
Build Date: 18 January 2008
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Thu May  1 01:09:47 2008
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Norcent"
(**) |   |-->Device "NVIDIA GeForce 7300"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(WW) Open ACPI failed (/var/run/acpid.socket) (No such file or directory)
(II) No APM support in BIOS or kernel
(II) Loader magic: 0x81e9800
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.2
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.2
(--) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,7190 card 15ad,1976 rev 01 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,7191 card 0000,0000 rev 01 class 06,04,00 hdr 01
(II) PCI: 00:07:0: chip 8086,7110 card 15ad,1976 rev 08 class 06,01,00 hdr 80
(II) PCI: 00:07:1: chip 8086,7111 card 15ad,1976 rev 01 class 01,01,8a hdr 00
(II) PCI: 00:07:3: chip 8086,7113 card 15ad,1976 rev 08 class 06,80,00 hdr 80
(II) PCI: 00:0f:0: chip 15ad,0405 card 15ad,0405 rev 00 class 03,00,00 hdr 00
(II) PCI: 00:10:0: chip 8086,100f card 15ad,0750 rev 01 class 02,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,1), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x0080 (VGA_EN is cleared)
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:7:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(0:15:0) VMware Inc [VMware SVGA II] PCI Display Adapter rev 0, Mem @ 0xf0000000/27, 0xe8000000/23, I/O @ 0x1060/4
(II) Addressable bus resource ranges are
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
        [1] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) Active PCI resource ranges:
        [0] -1  0       0xe8800000 - 0xe880ffff (0x10000) MX[B]
        [1] -1  0       0xe8820000 - 0xe883ffff (0x20000) MX[B]
        [2] -1  0       0xe8000000 - 0xe87fffff (0x800000) MX[B](B)
        [3] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [4] -1  0       0x00001070 - 0x00001077 (0x8) IX[B]
        [5] -1  0       0x00001050 - 0x0000105f (0x10) IX[B]
        [6] -1  0       0x00001060 - 0x0000106f (0x10) IX[B](B)
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xe8800000 - 0xe880ffff (0x10000) MX[B]
        [1] -1  0       0xe8820000 - 0xe883ffff (0x20000) MX[B]
        [2] -1  0       0xe8000000 - 0xe87fffff (0x800000) MX[B](B)
        [3] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [4] -1  0       0x00001070 - 0x00001077 (0x8) IX[B]
        [5] -1  0       0x00001050 - 0x0000105f (0x10) IX[B]
        [6] -1  0       0x00001060 - 0x0000106f (0x10) IX[B](B)
(II) OS-reported resource ranges after removing overlaps with PCI:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [5] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xe8800000 - 0xe880ffff (0x10000) MX[B]
        [5] -1  0       0xe8820000 - 0xe883ffff (0x20000) MX[B]
        [6] -1  0       0xe8000000 - 0xe87fffff (0x800000) MX[B](B)
        [7] -1  0       0xf0000000 - 0xf7ffffff (0x8000000) MX[B](B)
        [8] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [9] -1  0       0x00000000 - 0x000000ff (0x100) IX[B]
        [10] -1 0       0x00001070 - 0x00001077 (0x8) IX[B]
        [11] -1 0       0x00001050 - 0x0000105f (0x10) IX[B]
        [12] -1 0       0x00001060 - 0x0000106f (0x10) IX[B](B)
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension SHAPE
(II) Loading extension MIT-SUNDRY-NONSTANDARD
(II) Loading extension BIG-REQUESTS
(II) Loading extension SYNC
(II) Loading extension MIT-SCREEN-SAVER
(II) Loading extension XC-MISC
(II) Loading extension XFree86-VidModeExtension
(II) Loading extension XFree86-Misc
(II) Loading extension XFree86-DGA
(II) Loading extension DPMS
(II) Loading extension TOG-CUP
(II) Loading extension Extended-Visual-Information
(II) Loading extension XVideo
(II) Loading extension XVideo-MotionCompensation
(II) Loading extension X-Resource
(II) LoadModule: "dbe"
(II) Loading /usr/lib/xorg/modules/extensions//libdbe.so
(II) Module dbe: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension DOUBLE-BUFFER
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9639
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 1.3.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "record"
(II) Loading /usr/lib/xorg/modules/extensions//librecord.so
(II) Module record: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.13.0
        Module class: X.Org Server Extension
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension RECORD
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.9639
        Module class: X.Org Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 1.3.0, module version = 1.2.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) NVIDIA dlloader X Driver  1.0-9639  Mon Apr 16 20:21:54 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 00:0f:0
(EE) No devices detected.

Fatal server error:
no screens found[/PHP]

Here's my *xorg.conf* file:

[PHP]Section "Files"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc104"
        Option          "XkbLayout"     "us"
EndSection

Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "ZAxisMapping"          "4 5"
        Option          "Emulate3Buttons"       "true"
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "stylus"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "stylus"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "eraser"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "eraser"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "InputDevice"
        Driver          "wacom"
        Identifier      "cursor"
        Option          "Device"        "/dev/input/wacom"
        Option          "Type"          "cursor"
        Option          "ForceDevice"   "ISDV4"         # Tablet PC ONLY
EndSection

Section "Device"
        Identifier      "NVIDIA GeForce 7300"
        Driver          "nvidia"
        Option          "UseFBDev"              "true"
EndSection

Section "Monitor"
        Identifier      "Norcent"
        Option          "DPMS"
        HorizSync       30-100
        VertRefresh     50-160
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "NVIDIA GeForce 7300"
        Monitor         "Norcent"
        DefaultDepth    24
        SubSection "Display"
                Modes           "1440x900"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"

# Uncomment if you have a wacom tablet
#       InputDevice     "stylus"        "SendCoreEvents"
#       InputDevice     "cursor"        "SendCoreEvents"
#       InputDevice     "eraser"        "SendCoreEvents"
EndSection[/PHP]

If anyone could help it would be greatly appeciated - I'm about to give up on Linux and go back to Windows.....:(
Thanks in advance....

---

### Post by warp99 on 2008-04-30
Did you install Ubuntu Server? If you did server does not come with a GUI and the kernel doesn't include the various modules for desktop operations. Also it appears you do not have the restricted driver modules installed. 

Now we can correct these problems, but I need more information beginning with what version of Ubuntu are you running (6.06, 7.10, 8.04)? Also is this a virtual install (Vmware/Virtualbox)?

---

### Post by fdanderson on 2008-04-30
Hey Warp,

Thanks for getting back to me so quickly. I am using version 7.10 and it is a virtual install using VMWare. I'm not too sure about Ubuntu server - the version I installed was an image I downloaded from a friend.

I have installed X server though, I used apt-get for the following installs:

[B]xinit
xserver-xorg-core
xorg[/B]

I'm pretty much at a loss of what to do at the moment, so it's great to hear you know what's going on. I've been trawling forums and plugging away for about 3 days with no luck so far. I've only been using Linux for 3 months and have no back ground in MSDOS, writing script or code, so I didn't want to do away with MS Windows completely.

Thanks heaps for getting back to me so quickly.

Cheers

---

### Post by warp99 on 2008-04-30
> **fdanderson said:**
> Hey Warp,

Thanks for getting back to me so quickly. I am using version 7.10 and it is a virtual install using VMWare. I'm not too sure about Ubuntu server - the version I installed was an image I downloaded from a friend.

I have installed X server though, I used apt-get for the following installs:

[B]xinit
xserver-xorg-core
xorg[/B]

I'm pretty much at a loss of what to do at the moment, so it's great to hear you know what's going on. I've been trawling forums and plugging away for about 3 days with no luck so far. I've only been using Linux for 3 months and have no back ground in MSDOS, writing script or code, so I didn't want to do away with MS Windows completely.

Thanks heaps for getting back to me so quickly.

Cheers

You don't need to mess with an install especially with a Vmware image. You can download a virtual appliance from Vmware with Ubuntu already installed.

[http://www.vmware.com/appliances/](http://www.vmware.com/appliances/)

You can get any version with various applications already pre-installed. I counted 102 different hits when doing a search for 'Ubuntu'. This is going to be much easier because I suspect that you have a server install which doesn't include the desktop. Since you need to download a desktop anyway you may as well download one of the appliances already configured with Vmware tools.

Edit:
You can add/remove any apps, change anything you want, change the desktop from Gnome to KDE or to XFCE if you like and if you make a mistake just use a copy of the original image. It's a perfect way to dip your toes into Ubuntu.

---

### Post by fdanderson on 2008-04-30
Thanks for those, I wasn't aware they existed. But I'm a bit hesitant to use one of those as my main goal is to become competent with Linux and then switch completely across, so I rather try to sort out the problem I have to learn more about how Linux (and Ubuntu) work.

My plan was to get X up and running and then add a window manager (I was going to use Enlightenment) and then add a desktop manager (GNOME) afterwards. I wanted to do this so I could see what each of them looks like.

I'm currently doing some IT studies at University and Linux is part of that, and because I'm going to be working in the IT industry later (hoping), I'm trying to learn as much as I can.

Are you still able to help?

---

### Post by forrestcupp on 2008-04-30
Your problem is that you set it for nvidia.  In a virtual machine, it doesn't use your actual hardware.  It uses virtual hardware, which is not nvidia.

I would suggest downloading the latest desktop version and reinstalling it in your virtual machine.  You need to just accept the hardware it automatically detects.  Also, VM's don't really support hardware accelerated 3D.

---

### Post by fdanderson on 2008-04-30
Hi Forrest,

Is there anyway I can reconfigure it to work? The reason I configured it for NVIDIA is that when I initially installed X and tried to run it, it kept giving me a DRI compatibility error. When I researched what that problem was it indicated that I had the wrong drivers for my video card.

---

### Post by warp99 on 2008-04-30
> **fdanderson said:**
> Thanks for those, I wasn't aware they existed. But I'm a bit hesitant to use one of those as my main goal is to become competent with Linux and then switch completely across, so I rather try to sort out the problem I have to learn more about how Linux (and Ubuntu) work.

My plan was to get X up and running and then add a window manager (I was going to use Enlightenment) and then add a desktop manager (GNOME) afterwards. I wanted to do this so I could see what each of them looks like.

I'm currently doing some IT studies at University and Linux is part of that, and because I'm going to be working in the IT industry later (hoping), I'm trying to learn as much as I can.

Are you still able to help?

I would still use one of the Vmware appliances first because that will give you a base to start with. No offense but telling me that you don't know if the install is a sever or not is a red flag since a simple 'uname -a' would have told me this. You need to walk before you run.

Linux is a component OS so you can add any desktop you want, strip it down to the CLI if you feel like it and rebuild it even with the appliances. You can install multiple appliances tear them down and build them up as much as you want.

If you're goal is IT I would suggest using Gentoo since this is a very hands on distro that going to teach you the inner working since it's a "source-only' based distro. Also look into using Fedora since it seems that everyone and everything in the corporate sector is using Red Hat these days.

---

### Post by fdanderson on 2008-04-30
No problems, I'll keep looking around to see if I can solve the issues. Thanks for your time.

---

### Post by forrestcupp on 2008-04-30
> **fdanderson said:**
> Hi Forrest,

Is there anyway I can reconfigure it to work? The reason I configured it for NVIDIA is that when I initially installed X and tried to run it, it kept giving me a DRI compatibility error. When I researched what that problem was it indicated that I had the wrong drivers for my video card.

Usually what research turns up is for a full install, not something installed in a virtual machine.  The virtual video card that vmware uses doesn't support DRI.  

I really think if you aren't going to use a preinstalled image, you need to get your hands on the latest desktop LiveCD and try to install it again.  We have no idea what it was that you installed, and whatever it is, it's obviously not working.  Installing Ubuntu with a desktop CD shouldn't act this way.

---

### Post by fdanderson on 2008-04-30
I did a bit of research and manually redefined my graphics card as Vesa and bingo she works. I check the Xorg.0.log out and I now receive a different error:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

But I am not worry about this too much as I have her working....

---

### Post by forrestcupp on 2008-04-30
> **fdanderson said:**
> I did a bit of research and manually redefined my graphics card as Vesa and bingo she works. I check the Xorg.0.log out and I now receive a different error:

(EE) Failed to initialize GLX extension (Compatible NVIDIA X driver not found)

But I am not worry about this too much as I have her working....

In your /etc/X11/xorg.conf file, remove the line that says
```
Load    "glx"
```It's because the virtual video card doesn't support dri or glx or any other 3D stuff.

---

