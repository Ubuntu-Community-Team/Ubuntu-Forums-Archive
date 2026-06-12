---
title: "2 problems - help please"
date: 2007-05-17
forum: General Help
---

### Post by headcronie on 2007-05-17
I'm having difficulty with Feisty.  If I do a direct fresh install of Feisty on my machine, at the login screen instead of hearing the login drum sound, I get the system beep from the internal pezzio buzzer.  Upon logging in, I can use my regular sound.  Odd.. 
If I install Edgy first, and then upgrade to Feisty, my sound works fine.  My problem below exists no matter what I do.

What do I do?

2nd problem.
I've ditched my ATI Rage 128 card for a Nvidia Vanta card.  It should be covered in the Nvidia-Glx-Legacy drivers package I think.  The Vanta card is listed as Nvidia Vanta / Vanta LT.

So, upon initial install, it's using the opensource nv drivers.  It works, though  3d acceleration is slow.  I try to enable the Nvidia drivers, and I lose all 3d rendering.  All screen savers besides Deco stop working.

What do I need to do?

---

### Post by headcronie on 2007-05-18
Bump.

Anyone?

---

### Post by headcronie on 2007-05-19
Bump again..

---

### Post by headcronie on 2007-05-20
Bump...

---

### Post by headcronie on 2007-05-22
Here's a joke for you.

How many bumps does it take to get a starting point for a fix?

Tune in next post to find out...


BUMP!

---

### Post by CocoAUS on 2007-05-22
The open source nv driver should not provide ANY 3D acceleration.  How do you know that it was, and how do you know that the legacy driver is not allowing you any 3D acceleration?  What method did you use to install and enable your legacy driver?

If acceleration is working the output of the following command should yield "direct rendering: Yes":

```
glxinfo |grep rendering
```

What does it show with your legacy driver?

---

### Post by headcronie on 2007-05-23
> **CocoAUS said:**
> The open source nv driver should not provide ANY 3D acceleration.  

Yep, I realize that.  :)

> How do you know that it was, and how do you know that the legacy driver is not allowing you any 3D acceleration?


It was, as my Open GL screensavers worked, and worked at full speed, compared to what they did using the nv drivers.  Currently, none of the Open GL screensavers work at all.  Deco is the only one that I know of that is working.

>   What method did you use to install and enable your legacy driver? 
This time, I went to Nvidia's website, and downloaded the driver for the Vanta / Vanta LT which is listed under the 1.7.xx drivers.  I installed this after stopping the xfce desktop, and then restarted my computer.

I have previously used the Restricted Drivers tool, with the same result.

> 
If acceleration is working the output of the following command should yield "direct rendering: Yes":

```
glxinfo |grep rendering
```

What does it show with your legacy driver?

Here's what I'm getting right now:
```

Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Error: couldn't find RGB GLX visual
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".
Xlib:  extension "GLX" missing on display ":0.0".

```

I truly appreciate your stopping by and offering help.  Support with older computers is hard to find around here.

---

### Post by headcronie on 2007-05-23
I should add that once upon a time, I did manage to have it working correctly.  I started with my ATI Rage 128 card, and swapped it out for the Vanta card.  I tried to get Beryl to work, but couldn't figure it out.  3D acceleration was working just fine.  I managed to mess up my system, and did a reinstall.  Now, I'm unable to get the Nvidia card working correctly.

---

### Post by CocoAUS on 2007-05-23
Installing the driver from the nVidia website is an iffy process, especially if you're not extremely well-versed in all the technicalities of doing so.  I would suggest just re-installing using the method here: [http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#nvidia](http://othello.alma.edu/~07tmhopk/ubuntuhowto.html#nvidia)

Just make sure to change the nvidia-glx driver to the nvidia-glx-legacy driver.

---

### Post by cmost on 2007-05-23
I had no luck getting 3D acceleration with any nvidia driver on the nvidia Vanta card.  This card has some issues, apparently.  If I were you, I'd go back to your ATI card and work with the drivers available for it.  Good luck.

---

### Post by headcronie on 2007-05-23
LOL, that ATI card has issues too.   Good grief.  If it weren't for my stupid mobo, I'd put in my older Diamond Stealth III PCI card and be done with it.

Thing is, it tries to run off the integrated video which is beyond pathetic, even when I specify PCI for the video in BIOS.  

I'll hang around a bit more in hopes of getting the Vanta card working.

---

### Post by der_joachim on 2007-05-24
Re your nvidia driver:  make sure that the package nvidia-glx-legacy is properly installed. Also, the glx module must be enabled in your xorg.conf. Look in hthe [Module] section and add hde following line iif it's not already there:
```

    Load           "glx"

```

Having done that, could you post the contents of /var/log/xorg.0.log? It may contain hints.

Another option may be to try envy. This automagically installs and configures nvidia drivers.

---

### Post by headcronie on 2007-05-24
Thank you.  I'll fetch your request shortly.  :)

---

### Post by der_joachim on 2007-05-25
An additional advice: have you tried using [envy]("http://www.albertomilone.com/nvidia_scripts1.html")?

---

### Post by headcronie on 2007-05-25
Ok guys, sorry it took so long, I wasn't able to get back to my machine as fast as I thought.

Here's the contents of the log file requested.

```

garfield@odie:/var/log$ cat Xorg.0.log

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux odie 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Wed May 23 00:39:51 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "IBM E74"
(**) |   |-->Device "nVidia Corporation NV6 [Vanta/Vanta LT]"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
        Entry deleted from font path.
(**) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType,
        /usr/share/fonts/X11/misc,
        /usr/X11R6/lib/X11/fonts/misc,
        /usr/share/fonts/X11/cyrillic,
        /usr/share/fonts/X11/100dpi/:unscaled,
        /usr/share/fonts/X11/75dpi/:unscaled,
        /usr/share/fonts/X11/Type1,
        /usr/X11R6/lib/X11/fonts/Type1,
        /usr/share/fonts/X11/100dpi,
        /usr/share/fonts/X11/75dpi,
        /var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType
(==) RgbPath set to "/etc/X11/rgb"
(==) ModulePath set to "/usr/lib/xorg/modules"
(II) Open ACPI successful (/var/run/acpid.socket)
(II) Loader magic: 0x81c92e0
(II) Module ABI versions:
        X.Org ANSI C Emulation: 0.3
        X.Org Video Driver: 1.1
        X.Org XInput driver : 0.7
        X.Org Server Extension : 0.3
        X.Org Font Renderer : 0.5
(II) Loader running on linux
(II) LoadModule: "pcidata"
(II) Loading /usr/lib/xorg/modules//libpcidata.so
(II) Module pcidata: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(++) using VT number 7

(II) PCI: PCI scan (all values are in hex)
(II) PCI: 00:00:0: chip 8086,1130 card 8086,4532 rev 02 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1131 card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 02 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 02 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 8086,4532 rev 02 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 8086,4532 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 8086,4532 rev 02 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 8086,4532 rev 02 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 8086,4656 rev 02 class 04,01,00 hdr 00
(II) PCI: 01:08:0: chip 8086,2449 card 8086,3013 rev 01 class 02,00,00 hdr 00
(II) PCI: 02:00:0: chip 10de,002c card 10de,0072 rev 15 class 03,00,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
        [0] -1  0       0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
        [0] -1  0       0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:1:0), (0,2,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 2 non-prefetchable memory range:
        [0] -1  0       0xfca00000 - 0xfeafffff (0x2100000) MX[B]
(II) Bus 2 prefetchable memory range:
        [0] -1  0       0xf0700000 - 0xf47fffff (0x4100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:30:0), (0,1,1), BCTRL: 0x0002 (VGA_EN is cleared)
(II) Bus 1 I/O range:
        [0] -1  0       0x0000d000 - 0x0000dfff (0x1000) IX[B]
(II) Bus 1 non-prefetchable memory range:
        [0] -1  0       0xfc900000 - 0xfc9fffff (0x100000) MX[B]
(II) Bus 1 prefetchable memory range:
        [0] -1  0       0xf0600000 - 0xf06fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(2:0:0) nVidia Corporation NV6 [Vanta/Vanta LT] rev 21, Mem @ 0xfd000000/24, 0xf2000000/25, BIOS @ 0xfeaf0000/16
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
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
        [0] -1  0       0xfc9ff000 - 0xfc9fffff (0x1000) MX[B]
        [1] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [2] -1  0       0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
        [3] -1  0       0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
        [4] -1  0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [5] -1  0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [6] -1  0       0x0000ef00 - 0x0000ef3f (0x40) IX[B]
        [7] -1  0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [8] -1  0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [9] -1  0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [10] -1 0       0x0000ef40 - 0x0000ef5f (0x20) IX[B]
        [11] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
        [0] -1  0       0xfc9ff000 - 0xfc9fffff (0x1000) MX[B]
        [1] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [2] -1  0       0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
        [3] -1  0       0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
        [4] -1  0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [5] -1  0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [6] -1  0       0x0000ef00 - 0x0000ef3f (0x40) IX[B]
        [7] -1  0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [8] -1  0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [9] -1  0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [10] -1 0       0x0000ef40 - 0x0000ef5f (0x20) IX[B]
        [11] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
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
        [4] -1  0       0xfc9ff000 - 0xfc9fffff (0x1000) MX[B]
        [5] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [6] -1  0       0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
        [7] -1  0       0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
        [8] -1  0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [9] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [10] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [11] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [12] -1 0       0x0000ef00 - 0x0000ef3f (0x40) IX[B]
        [13] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [14] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [15] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [16] -1 0       0x0000ef40 - 0x0000ef5f (0x20) IX[B]
        [17] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "dri"
(II) Loading /usr/lib/xorg/modules/extensions//libdri.so
(II) Module dri: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Server Extension, version 0.3
(II) Loading extension XFree86-DRI
(II) LoadModule: "extmod"
(II) Loading /usr/lib/xorg/modules/extensions//libextmod.so
(II) Module extmod: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
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
(II) LoadModule: "freetype"
(II) Loading /usr/lib/xorg/modules//fonts/libfreetype.so
(II) Module freetype: vendor="X.Org Foundation & the After X-TT Project"
        compiled for 7.2.0, module version = 2.1.0
        Module class: X.Org Font Renderer
        ABI class: X.Org Font Renderer, version 0.5
(II) Loading font FreeType
(II) LoadModule: "glx"
(II) Loading /usr/lib/xorg/modules/extensions//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.7185
        Module class: XFree86 Server Extension
        ABI class: XFree86 Server Extension, version 0.1
(II) Loading extension GLX
(II) LoadModule: "int10"
(II) Loading /usr/lib/xorg/modules//libint10.so
(II) Module int10: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "vbe"
(II) Loading /usr/lib/xorg/modules//libvbe.so
(II) Module vbe: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "nvidia"
(II) Loading /usr/lib/xorg/modules/drivers//nvidia_drv.so
(II) Module nvidia: vendor="NVIDIA Corporation"
        compiled for 4.0.2, module version = 1.0.7185
        Module class: XFree86 Video Driver
(II) LoadModule: "kbd"
(II) Loading /usr/lib/xorg/modules/input//kbd_drv.so
(II) Module kbd: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "mouse"
(II) Loading /usr/lib/xorg/modules/input//mouse_drv.so
(II) Module mouse: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.1.1
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) LoadModule: "wacom"
(II) Loading /usr/lib/xorg/modules/input//wacom_drv.so
(II) Module wacom: vendor="X.Org Foundation"
        compiled for 4.3.99.902, module version = 1.0.0
        Module class: X.Org XInput Driver
        ABI class: X.Org XInput driver, version 0.7
(II) Wacom driver level: 47-0.7.7-7 $
(II) NVIDIA dlloader X Driver  1.0-7185  Mon Apr  2 18:31:01 PDT 2007
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 02:00:0
(--) Chipset NVIDIA GPU found
(II) resource ranges after xf86ClaimFixedResources() call:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfc9ff000 - 0xfc9fffff (0x1000) MX[B]
        [5] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [6] -1  0       0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
        [7] -1  0       0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
        [8] -1  0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [9] -1  0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [10] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [11] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [12] -1 0       0x0000ef00 - 0x0000ef3f (0x40) IX[B]
        [13] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [14] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [15] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [16] -1 0       0x0000ef40 - 0x0000ef5f (0x20) IX[B]
        [17] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
        [0] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [1] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [2] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [3] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [4] -1  0       0xfc9ff000 - 0xfc9fffff (0x1000) MX[B]
        [5] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [6] -1  0       0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
        [7] -1  0       0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
        [8] -1  0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [9] 0   0       0x000a0000 - 0x000affff (0x10000) MS[B]
        [10] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B]
        [11] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B]
        [12] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [13] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [14] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [15] -1 0       0x0000ef00 - 0x0000ef3f (0x40) IX[B]
        [16] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [17] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [18] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [19] -1 0       0x0000ef40 - 0x0000ef5f (0x20) IX[B]
        [20] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [21] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B]
        [22] 0  0       0x000003c0 - 0x000003df (0x20) IS[B]
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(--) NVIDIA(0): Linear framebuffer at 0xF2000000
(--) NVIDIA(0): MMIO registers at 0xFD000000
(II) NVIDIA(0): NVIDIA GPU detected as: Vanta/Vanta LT
(--) NVIDIA(0): VideoBIOS: 03.05.00.10.45
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): VideoRAM: 16384 kBytes
(II) NVIDIA(0): Connected display device(s): CRT-0
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at  8 bpp: 250 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 16 bpp: 250 MHz
(--) NVIDIA(0): Display device CRT-0: maximum pixel clock at 32 bpp: 215 MHz
(II) Loading sub module "ddc"
(II) LoadModule: "ddc"
(II) Reloading /usr/lib/xorg/modules//libddc.so
(II) NVIDIA(0): IBM E74: Using hsync range of 30.00-70.00 kHz
(II) NVIDIA(0): IBM E74: Using vrefresh range of 50.00-120.00 Hz
(II) NVIDIA(0): Clock range:  12.00 to 215.00 MHz
(II) NVIDIA(0): Not using default mode "1280x960" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x480" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1280x1024" (hsync out of range)
(II) NVIDIA(0): Not using default mode "640x512" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1600x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "800x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1792x1344" (hsync out of range)
(II) NVIDIA(0): Not using default mode "896x672" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1856x1392" (hsync out of range)
(II) NVIDIA(0): Not using default mode "928x696" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1152x864" (hsync out of range)
(II) NVIDIA(0): Not using default mode "576x432" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1400x1050" (hsync out of range)
(II) NVIDIA(0): Not using default mode "700x525" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1200" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x600" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1920x1440" (hsync out of range)
(II) NVIDIA(0): Not using default mode "960x720" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "2048x1536" (width requires unsupported line pitch)
(II) NVIDIA(0): Not using default mode "1024x768" (hsync out of range)
(II) NVIDIA(0): Not using default mode "1680x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1400x1050" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x1024" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1440x900" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x960" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x800" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x864" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1280x768" (width too large for virtual size)
(II) NVIDIA(0): Not using default mode "1152x768" (width too large for virtual size)
(WW) NVIDIA(0): Not using mode "840x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "700x525" (height 1050 is larger than
(WW) NVIDIA(0):      EDID-specified maximum 1024)
(WW) NVIDIA(0): Not using mode "576x384":
(WW) NVIDIA(0):   horizontal sync start (589) not a multiple of 8
(WW) NVIDIA(0): Not using mode "360x200":
(WW) NVIDIA(0):   horizontal sync start (378) not a multiple of 8
(**) NVIDIA(0): Validated modes for display device CRT-0:
(**) NVIDIA(0):      Default mode "1024x768": 94.5 MHz, 68.7 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 56.3 MHz, 53.7 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x480": 36.0 MHz, 43.3 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 78.8 MHz, 60.0 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 75.0 MHz, 56.5 kHz, 70.1 Hz
(**) NVIDIA(0):      Default mode "1024x768": 65.0 MHz, 48.4 kHz, 60.0 Hz
(**) NVIDIA(0):      Default mode "1024x768": 44.9 MHz, 35.5 kHz, 87.0 Hz (I)
(**) NVIDIA(0):      Default mode "832x624": 57.3 MHz, 49.7 kHz, 74.6 Hz
(**) NVIDIA(0):      Default mode "800x600": 49.5 MHz, 46.9 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "800x600": 50.0 MHz, 48.1 kHz, 72.2 Hz
(**) NVIDIA(0):      Default mode "800x600": 40.0 MHz, 37.9 kHz, 60.3 Hz
(**) NVIDIA(0):      Default mode "800x600": 36.0 MHz, 35.2 kHz, 56.2 Hz
(**) NVIDIA(0):      Default mode "640x512": 54.0 MHz, 64.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "720x450": 54.4 MHz, 56.9 kHz, 60.2 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.5 kHz, 75.0 Hz
(**) NVIDIA(0):      Default mode "640x480": 31.5 MHz, 37.9 kHz, 72.8 Hz
(**) NVIDIA(0):      Default mode "640x480": 54.0 MHz, 60.0 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x480": 25.2 MHz, 31.5 kHz, 59.9 Hz
(**) NVIDIA(0):      Default mode "720x400": 35.5 MHz, 37.9 kHz, 85.0 Hz
(**) NVIDIA(0):      Default mode "640x400": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "640x400": 41.7 MHz, 49.7 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "576x432": 54.0 MHz, 67.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "640x384": 40.1 MHz, 47.7 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "640x350": 31.5 MHz, 37.9 kHz, 85.1 Hz
(**) NVIDIA(0):      Default mode "512x384": 47.2 MHz, 68.7 kHz, 85.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 39.4 MHz, 60.0 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 37.5 MHz, 56.5 kHz, 70.1 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 32.5 MHz, 48.4 kHz, 60.0 Hz (D)
(**) NVIDIA(0):      Default mode "512x384": 22.4 MHz, 35.5 kHz, 86.9 Hz (D)
(**) NVIDIA(0):      Default mode "416x312": 28.6 MHz, 49.7 kHz, 74.7 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 28.1 MHz, 53.7 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 24.8 MHz, 46.9 kHz, 75.1 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 25.0 MHz, 48.1 kHz, 72.2 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 20.0 MHz, 37.9 kHz, 60.3 Hz (D)
(**) NVIDIA(0):      Default mode "400x300": 18.0 MHz, 35.2 kHz, 56.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 18.0 MHz, 43.3 kHz, 85.2 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.5 kHz, 75.0 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 15.8 MHz, 37.9 kHz, 72.8 Hz (D)
(**) NVIDIA(0):      Default mode "320x240": 12.6 MHz, 31.5 kHz, 60.1 Hz (D)
(**) NVIDIA(0):      Default mode "320x200": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(**) NVIDIA(0):      Default mode "320x175": 15.8 MHz, 37.9 kHz, 85.3 Hz (D)
(II) NVIDIA(0): Virtual screen size determined to be 1024 x 768
(--) NVIDIA(0): Display dimensions: (320, 240) mm
(--) NVIDIA(0): DPI set to (81, 81)
(II) Loading sub module "fb"
(II) LoadModule: "fb"
(II) Loading /usr/lib/xorg/modules//libfb.so
(II) Module fb: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 1.0.0
        ABI class: X.Org ANSI C Emulation, version 0.3
(II) Loading sub module "ramdac"
(II) LoadModule: "ramdac"
(II) Loading /usr/lib/xorg/modules//libramdac.so
(II) Module ramdac: vendor="X.Org Foundation"
        compiled for 7.2.0, module version = 0.1.0
        ABI class: X.Org Video Driver, version 1.1
(--) Depth 24 pixmap format is 32 bpp
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
        [0] 0   0       0xf2000000 - 0xf3ffffff (0x2000000) MX[B]
        [1] 0   0       0xfd000000 - 0xfdffffff (0x1000000) MX[B]
        [2] -1  0       0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
        [3] -1  0       0x000f0000 - 0x000fffff (0x10000) MX[B]
        [4] -1  0       0x000c0000 - 0x000effff (0x30000) MX[B]
        [5] -1  0       0x00000000 - 0x0009ffff (0xa0000) MX[B]
        [6] -1  0       0xfc9ff000 - 0xfc9fffff (0x1000) MX[B]
        [7] -1  0       0xf8000000 - 0xf7ffffff (0x0) MX[B]O
        [8] -1  0       0xfeaf0000 - 0xfeafffff (0x10000) MX[B](B)
        [9] -1  0       0xf2000000 - 0xf3ffffff (0x2000000) MX[B](B)
        [10] -1 0       0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
        [11] 0  0       0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
        [12] 0  0       0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
        [13] 0  0       0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
        [14] -1 0       0x0000ffff - 0x0000ffff (0x1) IX[B]
        [15] -1 0       0x00000000 - 0x000000ff (0x100) IX[B]
        [16] -1 0       0x0000df00 - 0x0000df3f (0x40) IX[B]
        [17] -1 0       0x0000ef00 - 0x0000ef3f (0x40) IX[B]
        [18] -1 0       0x0000e800 - 0x0000e8ff (0x100) IX[B]
        [19] -1 0       0x0000ef80 - 0x0000ef9f (0x20) IX[B]
        [20] -1 0       0x0000efa0 - 0x0000efaf (0x10) IX[B]
        [21] -1 0       0x0000ef40 - 0x0000ef5f (0x20) IX[B]
        [22] -1 0       0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
        [23] 0  0       0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
        [24] 0  0       0x000003c0 - 0x000003df (0x20) IS[B](OprU)
(II) NVIDIA(0): Setting mode "1024x768"
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(==) RandR enabled
(II) Initializing built-in extension MIT-SHM
(II) Initializing built-in extension XInputExtension
(II) Initializing built-in extension XTEST
(II) Initializing built-in extension XKEYBOARD
(II) Initializing built-in extension XC-APPGROUP
(II) Initializing built-in extension XAccessControlExtension
(II) Initializing built-in extension SECURITY
(II) Initializing built-in extension XINERAMA
(II) Initializing built-in extension XFIXES
(II) Initializing built-in extension XFree86-Bigfont
(II) Initializing built-in extension RENDER
(II) Initializing built-in extension RANDR
(II) Initializing built-in extension COMPOSITE
(II) Initializing built-in extension DAMAGE
(II) Initializing built-in extension XEVIE
(EE) GLX is not supported with the Composite extension
(**) Option "CoreKeyboard"
(**) Generic Keyboard: Core Keyboard
(**) Option "Protocol" "standard"
(**) Generic Keyboard: Protocol: standard
(**) Option "AutoRepeat" "500 30"
(**) Option "XkbRules" "xorg"
(**) Generic Keyboard: XkbRules: "xorg"
(**) Option "XkbModel" "pc105"
(**) Generic Keyboard: XkbModel: "pc105"
(**) Option "XkbLayout" "us"
(**) Generic Keyboard: XkbLayout: "us"
(**) Option "XkbOptions" "lv3:ralt_switch"
(**) Generic Keyboard: XkbOptions: "lv3:ralt_switch"
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Emulate3Buttons" "true"
(**) Configured Mouse: Emulate3Buttons, Emulate3Timeout: 50
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Configured Mouse: Buttons: 9
(**) Option "SendCoreEvents"
(**) stylus: always reports core events
(**) stylus device is /dev/input/wacom
(**) stylus is in absolute mode
(**) stylus: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) stylus: serial speed 9600
(**) Option "SendCoreEvents"
(**) cursor: always reports core events
(**) cursor device is /dev/input/wacom
(**) cursor is in relative mode
(**) cursor: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) cursor: serial speed 9600
(**) Option "SendCoreEvents"
(**) eraser: always reports core events
(**) eraser device is /dev/input/wacom
(**) eraser is in absolute mode
(**) eraser: forcing TabletPC ISD V4 protocol
(**) WACOM: suppress value is 2
(**) Option "BaudRate" "9600"
(**) eraser: serial speed 9600
(II) XINPUT: Adding extended input device "eraser" (type: Wacom Eraser)
(II) XINPUT: Adding extended input device "cursor" (type: Wacom Cursor)
(II) XINPUT: Adding extended input device "stylus" (type: Wacom Stylus)
(II) XINPUT: Adding extended input device "Configured Mouse" (type: MOUSE)
(II) XINPUT: Adding extended input device "Generic Keyboard" (type: KEYBOARD)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
        No such file or directory.
Error opening /dev/input/wacom : Invalid argument
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
garfield@odie:/var/log$ 


```

I have not tried envy yet, as this is the first I've heard of it.  If you don't see the problem in my log, I may try that next.

Here is a copy of my xorg.conf:

```

garfield@odie:/etc/X11$ cat xorg.conf
# /etc/X11/xorg.conf (xorg X Window System server configuration file)
#
# This file was generated by dexconf, the Debian X Configuration tool, using
# values from the debconf database.
#
# Edit this file with caution, and see the xorg.conf(5) manual page.
# (Type "man xorg.conf" at the shell prompt.)
#
# This file is automatically updated on xserver-xorg package upgrades *only*
# if it has not been modified since the last upgrade of the xserver-xorg
# package.
#
# If you have edited this file but would like it to be automatically updated
# again, run the following command:
#   sudo dpkg-reconfigure -phigh xserver-xorg

Section "Files"
        FontPath        "/usr/share/fonts/X11/misc"
        FontPath        "/usr/share/fonts/X11/cyrillic"
        FontPath        "/usr/share/fonts/X11/100dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/75dpi/:unscaled"
        FontPath        "/usr/share/fonts/X11/Type1"
        FontPath        "/usr/share/fonts/X11/100dpi"
        FontPath        "/usr/share/fonts/X11/75dpi"
        # path to defoma fonts
        FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
        Load    "bitmap"
        Load    "ddc"
        Load    "dri"
        Load    "extmod"
        Load    "freetype"
        Load    "glx"
        Load    "int10"
        Load    "vbe"
EndSection

Section "InputDevice"
        Identifier      "Generic Keyboard"
        Driver          "kbd"
        Option          "CoreKeyboard"
        Option          "XkbRules"      "xorg"
        Option          "XkbModel"      "pc105"
        Option          "XkbLayout"     "us"
        Option          "XkbOptions"    "lv3:ralt_switch"
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
        Identifier      "nVidia Corporation NV6 [Vanta/Vanta LT]"
        Driver          "nvidia"
        BusID           "PCI:2:0:0"
EndSection

Section "Monitor"
        Identifier      "IBM E74"
        Option          "DPMS"
        HorizSync       30-70
        VertRefresh     50-120
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Device          "nVidia Corporation NV6 [Vanta/Vanta LT]"
        Monitor         "IBM E74"
        DefaultDepth    24
        SubSection "Display"
                Depth           1
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           4
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           8
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           15
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           16
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
        SubSection "Display"
                Depth           24
                Modes           "1024x768" "800x600" "640x480"
        EndSubSection
EndSection

Section "ServerLayout"
        Identifier      "Default Layout"
        Screen          "Default Screen"
        InputDevice     "Generic Keyboard"
        InputDevice     "Configured Mouse"
        InputDevice     "stylus"        "SendCoreEvents"
        InputDevice     "cursor"        "SendCoreEvents"
        InputDevice     "eraser"        "SendCoreEvents"
EndSection

Section "DRI"
        Mode    0666
EndSection
garfield@odie:/etc/X11$ 


```

Thanks for the help so far everybody.  The help is appreciated.  :)

---

### Post by der_joachim on 2007-05-25
Neither your log nor your xorg.conf show any strange entries. I do have a few suggestions left, but I am really guessing here, so I may be completely and utterly wrong...

Here's my xorg.conf, which works perfectly with my 7600. Note the extra **extensions** section and my elaborate **device** section. Using these settings may work for you as well, but beware: I have a different version of the nvidia drivers, so there is a big chance that copy/pasting won't do any good. 

```

Section "ServerLayout"
    Identifier     "Default Layout"
    Screen         "Default Screen" 0 0
    InputDevice    "Generic Keyboard"
    InputDevice    "Configured Mouse"
    Option         "BlankTime" "10"
    Option         "StandbyTime" "30"
    Option         "OffTime" "60"
EndSection

Section "Files"
	# path to defoma fonts
    FontPath        "/usr/share/X11/fonts/misc"
    FontPath        "/usr/share/X11/fonts/cyrillic"
    FontPath        "/usr/share/X11/fonts/100dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/75dpi/:unscaled"
    FontPath        "/usr/share/X11/fonts/Type1"
    FontPath        "/usr/share/X11/fonts/100dpi"
    FontPath        "/usr/share/X11/fonts/75dpi"
    FontPath        "/usr/share/fonts/X11/misc"
    FontPath        "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType"
EndSection

Section "Module"
    Load           "bitmap"
    Load           "ddc"
    Load           "extmod"
    Load           "freetype"
    Load           "glx"
    Load           "int10"
    Load           "type1"
    Load           "vbe"
    Load           "dbe"
EndSection

Section "InputDevice"
    Identifier     "Generic Keyboard"
    Driver         "kbd"
    Option         "CoreKeyboard"
    Option         "XkbRules" "xorg"
    Option         "XkbModel" "pc104"
    Option         "XkbLayout" "us(intl),us(dvorak)"
	Option         "XkbOptions" "grp:alt_shift_toggle"
EndSection

Section "InputDevice"
    Identifier     "Configured Mouse"
    Driver         "mouse"
    Option         "CorePointer"
    Option         "Device" "/dev/input/mice"
    Option         "Protocol" "ExplorerPS/2"
    Option         "ZAxisMapping" "4 5"
    Option         "Emulate3Buttons" "true"
EndSection

Section "Monitor"
    Identifier     "SyncMaster"
    HorizSync       28.0 - 51.0
    VertRefresh     43.0 - 60.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "NVIDIA Corporation NVIDIA Default Card"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "NVIDIA Corporation NVIDIA Default Card"
    Monitor        "SyncMaster"
    DefaultDepth    24
    Option         "TripleBuffer" "true"
    Option         "AllowGLXWithComposite" "True"
    Option         "NoLogo" "False"
    Option         "RenderAccel" "true"
    Option         "NvAGP" "3"
    Option         "AddARGBGLXVisuals" "True"
    SubSection     "Display"
        Depth       1
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1680x1050" "1280x1024" "1280x960" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection

Section "Extensions"
    Option         "Composite" "Enable"
EndSection

```

If that does not help, try installing the package nvidia-xconfig. IIRC, that package contains a configuration tool for older nvidia cards.

BTW: you can safely remove all wacom stuff from your xorg.conf. All it does is put errors in your xorg logs.

Good luck.

---

### Post by headcronie on 2007-05-27
No go on pasting your xorg into mine.  Dang.

I'll try Envy now, if I can find it.  I may need to reinstall, as I've installed so many drivers and / or hacked up the system so bad, it may not install properly.

---

### Post by headcronie on 2007-05-27
No package named nvidia-xconfig.  :(

Envy, here I come.

---

### Post by der_joachim on 2007-05-28
nvidia-xconfig is apparently in universe. Are you sure that you havve enabled all repos?

[Link to envy]("http://www.albertomilone.com/nvidia_scripts1.html").

---

### Post by headcronie on 2007-05-28
I could have sworn I did.  I'll have to check again.  I might have done it incorrectly.

---

### Post by headcronie on 2007-05-29
My sources.lst file was borked.

I could not even get the nv drivers working correctly after all the messing I did.  

I'm now running on a fresh install of Xubuntu Feisty.

I'm off to try envy before I do anything else.

I'll report back on my findings.

---

### Post by headcronie on 2007-05-29
ARGH!

Why... why... why... does my integrated video try to take over the damn graphics control!!!

Envy ran, I restarted my computer, and got dumped to the console.  Appears the built in video is now set to primary.  I ran envy in text mode, uninstalled the Nvidia drivers, and was able to startx. 

I think I'm going to lose my mind.

If this is the case, how do I find out for sure, and how do I fix it?

---

### Post by der_joachim on 2007-05-29
Hmmm stupid question: can you disable your built-in video card in your BIOS and is it actually disabled? 

BTW: If the Nvidia driver works, and X is configured correctly,  you should be seeing a Nvidia logo when X starts up.

---

### Post by headcronie on 2007-05-29
In my BIOS, I can set it to PCI, or AGP, or if nothing is installed, it sets itself to onboard.  
Unfortunately, there is no option to disable the onboard video.  Grrrrrr!

Yeah, I've previously gotten the Nvidia logo when booting.  Not currently though.  I get the Xubuntu loading screen, and then am dumped to the console.

If I start dpkg-reconfigure xserver-xorg, it detects my onboard video 'vesa' generic video.    That's while my monitor is plugged into the Nvidia card.    That is what is making me think the priority of video devices is backwards.  If I could get Nvidia first, and put the generic second, or better yet, just remove the generic from booting, it would be alot better.

---

