---
title: "Feisty screen resolution mis-match"
date: 2007-04-20
forum: General Help
---

### Post by Dave54 on 2007-04-20
There seems to be some sort of miscommunication between my monitor, graphics card, and ubuntu. My screen resolution is currently set to 1152x864 @ 52Hz. I have a CRT monitor, and it claims that it's actually displaying 1152x864 @ **85Hz** (77.4KHz horizontal and 85.0Hz vertical). Judging by the fact that my screen isn't blinking, I think it's at 85Hz.

Before I get much further into this problem, here's some information.
OS: Ubuntu 7.04 Feisty Fawn
Monitor: ViewSonic UltraBrite A90f+ ([http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/]("http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/"))
Graphics card: nVidia GeForce FX 5200 ([http://www.nvidia.com/page/fx_5200.html]("http://www.nvidia.com/page/fx_5200.html"))
Graphics driver: I went to Restricted Drivers Manager and enabled the proprietary nVidia driver.

So if I go to System > Preferences > Screen Resolution, I have a **long** list of some rather interesting choices, including **EVERY** Hz between 50 and  94, each once. (so that's 1600x1200@50Hz, 1280x1024@51Hz, 1152x864@52Hz, etc, etc, etc.)

When I select a resolution, I get a resolution different from what I had selected. (sometimes I just get a black screen and **Feisty crashes**)

I tried every given solution in [https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto"). Not one worked. To bring you up to speed on the major things I tried:
I tried running the autodetect script again. (sudo dpkg-reconfigure xserver-xorg)
I tried putting the horizontal sync frequency and the vertical refresh rate in the xorg.conf file
I tried lowering my DefaultDepth in the xorg.conf file
I tried adding "Option "UseEdidFreqs" "false"" to the xorg.conf file

If you want to see it, here's the important part of my xorg.conf file.
```
Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "A90f+"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseEdidFreqs" "false"
    SubSection     "Display"
        Depth       1
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       4
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       8
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       15
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       16
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
    SubSection     "Display"
        Depth       24
        Modes      "1600x1200" "1280x1024" "1152x864" "1024x768" "832x624" "800x600" "720x400" "640x480"
    EndSubSection
EndSection
```

In the Screen Resolution dialog, I have many strange resolution options (like 1440x900) which **are not in my xorg.conf file**.

The resolutions my monitor can handle:
1792x1344 @ 61Hz
1600x1200 @ 68Hz
1280x1024 @ 80Hz
1152x870 @ 94Hz
1024x768 @ 105Hz
800x600 @ 132Hz

Horizontal sync frequency: 30~86kHz
Vertical refresh rate: 50~150Hz

If I can't get my monitor to display all its resolutions correctly then I at least want it to display **1280x1024 @ 80Hz even if that will be the only resolution it can display**. Does anyone know a way to "force" my computer to use that resolution **no matter what?**

Please post any ideas, thanks.
-Dave

---

### Post by matigol on 2007-04-20
I am not understand all but when i have a problem with my resolution, i tape :

sudo dpkg-reconfigure -phigh xserver-xorg


And i choose ma resolution.

:confused:

---

### Post by barmazal on 2007-04-20
my solution work with the best suiting solution for you NOW, and wait for proper Envy or Automatix release for Festy.
It wouldn't take more than few weeks or even less, who knows.

same problem btw with GT6600

---

### Post by Dave54 on 2007-04-20
I already tried dpkg-reconfigure, and it (surprisingly) didn't change anything (as for the resolutions).
Also, although there's a lot of resolution options there, it doesn't include some of my monitor's supported "nonstandard" resolutions, like 1152x870.

Anymore ideas, anyone?

---

### Post by dnns on 2007-04-21
I'm assuming you are using the restricted drivers from NVIDIA.

In my case, it was very easy, I just typed "nvidia-settings" in the terminal and a GUI will pop up in which you can adjust all your screen settings. Seemingly it circumvents xorg.conf, which also fudges up the readout that xorg gives you in system->preferences-screen resolution

The GUI even has an option to write out a new xorg.conf

Hope it works

---

### Post by Dave54 on 2007-04-21
Very interesting.

The nvidia-settings GUI offers me more (better) resolutions. However, it does not offer 1280x1024 @ 80Hz (it only allows 60Hz or 75Hz) and it doesn't allow 1152x870 at all.

I have never seen 1152x870 be used, but my monitor says that's a supported resolution. Does anyone know how to use a nonstandard screen resolution?

Also, after applying a resolution via the nVidia settings gui, they revert after a reboot. Is there a way to make them stick?

---

### Post by jimbean on 2007-04-21
it worked thanks

---

### Post by Dave54 on 2007-04-21
I've been trying to change my xorg to make it use 1280x1024@80Hz. It currently looks like this:
```
Section "Monitor"
    Identifier     "A90f+"
    Option         "DPMS"
    HorizSync      30-86
    VertRefresh    50-150
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "A90f+"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseEdidFreqs" "false"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80"
    EndSubSection
EndSection
```

The xorg log prints out this:
```
(II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.27.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic A90f+ (CRT-0)
(--) NVIDIA(0): ViewSonic A90f+ (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
[COLOR="Red"](WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.
(WW) NVIDIA(0): No valid modes for "1280x1024_80"; removing.[/COLOR]
(WW) NVIDIA(0): 
(WW) NVIDIA(0): Unable to validate any modes; falling back to the default mode
(WW) NVIDIA(0):     "nvidia-auto-select".
(WW) NVIDIA(0): 
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "nvidia-auto-select"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (90, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
```

So, why isn't 1280x1024_80 a valid mode?

I started looking into modelines, perhaps to make my own mode? I've reached many warnings that it's easy to damage the monitor this way.

My monitor specs are here: [http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/#specs]("http://www.viewsonic.com/support/desktopdisplays/crtmonitors/aseries/a90fplus/#specs")

So I found a modeline calculator on the net ([http://www.bohne-lang.de/spec/linux/modeline/]("http://www.bohne-lang.de/spec/linux/modeline/")) and put in 1280x1024 @ 80 Hz. It says the horizontal refresh rate will be 86.05 KHz. My monitor supports 30~86kHz. Could this be why ubuntu refuses to use 1280x1024@80Hz?

So I'm thinking about adding this modeline to my xorg:
```
Modeline "1280x1024" 167.97  1280 1368 1576 1952  1024 1024 1027 1075
```
But I have one more question. Could my graphics card not be able to display this? Could it damage my graphics card?

---

### Post by Dave54 on 2007-04-21
I found a command called "gtf". It seems to be able to create modelines. this is what it printed:
```
dave@ubuntu:~$ gtf 1280 1024 80

  # 1280x1024 @ 80.00 Hz (GTF) hsync: 85.76 kHz; pclk: 149.57 MHz
  Modeline "1280x1024_80.00"  149.57  1280 1376 1512 1744  1024 1025 1028 1072  -HSync +Vsync

```
Should I use that instead? it looks to be a little more within the bounds of my monitor's abilities.

On another note, I found some other threads with people experiencing the same problem as me.
[http://ubuntuforums.org/showthread.php?t=417716]("http://ubuntuforums.org/showthread.php?t=417716")
[http://ubuntuforums.org/showthread.php?t=416679]("http://ubuntuforums.org/showthread.php?t=416679")
[http://ubuntuforums.org/showthread.php?t=414287]("http://ubuntuforums.org/showthread.php?t=414287")
No solutions yet.

---

### Post by samwyse on 2007-04-21
I've used gtf for a resolution that another calculator gave an out of bounds pclk value. Before that I thought I needed to get a better graphics card, but the gtf modeline worked.

---

### Post by Dave54 on 2007-04-21
OK, I think I'll brave the modeline. I've seen my monitor complain about an out of bounds input before, so I doubt I'll break it.

EDIT:
I added the modeline, so (the important part of) my xorg looks like this:
```
Section "Monitor"
    Identifier     "A90f+"
    Option         "DPMS"
    HorizSync      30-86
    VertRefresh    50-150
  # 1280x1024 @ 80.00 Hz (GTF) hsync: 85.76 kHz; pclk: 149.57 MHz
    Modeline       "1280x1024_80"  149.57  1280 1376 1512 1744  1024 1025 1028 1072  -HSync +Vsync
EndSection

Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
EndSection

Section "Screen"
    Identifier     "Default Screen"
    Device         "nVidia Corporation NV34 [GeForce FX 5200]"
    Monitor        "A90f+"
    DefaultDepth    24
    Option         "AddARGBVisuals" "True"
    Option         "NoLogo" "True"
    Option         "AddARGBGLXVisuals" "True"
    Option         "UseEdidFreqs" "false"
    SubSection     "Display"
        Depth       24
        Modes      "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80" "1280x1024_80"
    EndSubSection
EndSection
```
Then I restarted ubuntu. It seemed to use the correct resolution for a second, but then it abandoned it and went back to a safer one. Currently, System > Preferences > Screen Resolution reports that it's at 1152x864@64Hz, and my monitor says it's at 1152x864@85Hz.

Here's what my xorg log had to say about the incident:
```
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic A90f+ (CRT-0)
(--) NVIDIA(0): ViewSonic A90f+ (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
[COLOR="Green"](II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"[/COLOR]
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (90, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp
```
I'm still searching for why it abandoned it though.

---

### Post by Dave54 on 2007-04-21
Here's the entire log:

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux ubuntu 2.6.20-15-generic #2 SMP Sun Apr 15 07:36:31 UTC 2007 i686
Build Date: 04 April 2007
	Before reporting problems, check http://wiki.x.org
	to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
	(++) from command line, (!!) notice, (II) informational,
	(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Apr 21 22:38:54 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "A90f+"
(**) |   |-->Device "nVidia Corporation NV34 [GeForce FX 5200]"
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
(II) PCI: 00:00:0: chip 8086,1a30 card 0000,0000 rev 04 class 06,00,00 hdr 00
(II) PCI: 00:01:0: chip 8086,1a31 card 0000,0000 rev 04 class 06,04,00 hdr 01
(II) PCI: 00:1e:0: chip 8086,244e card 0000,0000 rev 05 class 06,04,00 hdr 01
(II) PCI: 00:1f:0: chip 8086,2440 card 0000,0000 rev 05 class 06,01,00 hdr 80
(II) PCI: 00:1f:1: chip 8086,244b card 8086,5054 rev 05 class 01,01,80 hdr 00
(II) PCI: 00:1f:2: chip 8086,2442 card 8086,5054 rev 05 class 0c,03,00 hdr 00
(II) PCI: 00:1f:3: chip 8086,2443 card 8086,5054 rev 05 class 0c,05,00 hdr 00
(II) PCI: 00:1f:4: chip 8086,2444 card 8086,5054 rev 05 class 0c,03,00 hdr 00
(II) PCI: 00:1f:5: chip 8086,2445 card 8086,7074 rev 05 class 04,01,00 hdr 00
(II) PCI: 01:00:0: chip 10de,0322 card 0000,0000 rev a1 class 03,00,00 hdr 00
(II) PCI: 02:0a:0: chip 0e11,ae32 card 0000,0000 rev 10 class 02,80,00 hdr 00
(II) PCI: End of PCI scan
(II) Intel Bridge workaround enabled
(II) Host-to-PCI bridge:
(II) Bus 0: bridge is at (0:0:0), (0,0,2), BCTRL: 0x0008 (VGA_EN is set)
(II) Bus 0 I/O range:
	[0] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) Bus 0 non-prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) Bus 0 prefetchable memory range:
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
(II) PCI-to-PCI bridge:
(II) Bus 1: bridge is at (0:1:0), (0,1,1), BCTRL: 0x000a (VGA_EN is set)
(II) Bus 1 non-prefetchable memory range:
	[0] -1	0	0xfc900000 - 0xfe9fffff (0x2100000) MX[B]
(II) Bus 1 prefetchable memory range:
	[0] -1	0	0xe4600000 - 0xf46fffff (0x10100000) MX[B]
(II) Subtractive PCI-to-PCI bridge:
(II) Bus 2: bridge is at (0:30:0), (0,2,2), BCTRL: 0x0006 (VGA_EN is cleared)
(II) Bus 2 I/O range:
	[0] -1	0	0x0000d000 - 0x0000d0ff (0x100) IX[B]
	[1] -1	0	0x0000d400 - 0x0000d4ff (0x100) IX[B]
	[2] -1	0	0x0000d800 - 0x0000d8ff (0x100) IX[B]
	[3] -1	0	0x0000dc00 - 0x0000dcff (0x100) IX[B]
(II) Bus 2 non-prefetchable memory range:
	[0] -1	0	0xfea00000 - 0xfeafffff (0x100000) MX[B]
(II) Bus 2 prefetchable memory range:
	[0] -1	0	0xf4700000 - 0xf47fffff (0x100000) MX[B]
(II) PCI-to-ISA bridge:
(II) Bus -1: bridge is at (0:31:0), (0,-1,-1), BCTRL: 0x0008 (VGA_EN is set)
(--) PCI:*(1:0:0) nVidia Corporation NV34 [GeForce FX 5200] rev 161, Mem @ 0xfd000000/24, 0xe8000000/27, BIOS @ 0xfe9e0000/17
(II) Addressable bus resource ranges are
	[0] -1	0	0x00000000 - 0xffffffff (0x0) MX[B]
	[1] -1	0	0x00000000 - 0x0000ffff (0x10000) IX[B]
(II) OS-reported resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) PCI Memory resource overlap reduced 0xf8000000 from 0xfbffffff to 0xf7ffffff
(II) Active PCI resource ranges:
	[0] -1	0	0xfeafec00 - 0xfeafec0f (0x10) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[3] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[4] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[6] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[9] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[10] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[11] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) Active PCI resource ranges after removing overlaps:
	[0] -1	0	0xfeafec00 - 0xfeafec0f (0x10) MX[B]
	[1] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[2] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[3] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[4] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[5] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[6] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[7] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[8] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[9] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[10] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[11] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) OS-reported resource ranges after removing overlaps with PCI:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[5] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
(II) All system resource ranges:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafec00 - 0xfeafec0f (0x10) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[12] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[15] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[16] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) LoadModule: "i2c"
(II) Loading /usr/lib/xorg/modules//libi2c.so
(II) Module i2c: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.2.0
	ABI class: X.Org Video Driver, version 1.1
(II) LoadModule: "ddc"
(II) Loading /usr/lib/xorg/modules//libddc.so
(II) Module ddc: vendor="X.Org Foundation"
	compiled for 7.2.0, module version = 1.0.0
	ABI class: X.Org Video Driver, version 1.1
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
(II) Loading /usr/lib/xorg/modules//libglx.so
(II) Module glx: vendor="NVIDIA Corporation"
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Server Extension
	ABI class: X.Org Server Extension, version 0.1
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
	compiled for 4.0.2, module version = 1.0.9631
	Module class: X.Org Video Driver
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
(II) NVIDIA dlloader X Driver  1.0-9631  Thu Nov  9 17:39:58 PST 2006
(II) NVIDIA Unified Driver for all Supported NVIDIA GPUs
(II) Primary Device is: PCI 01:00:0
(--) Assigning device section with no busID to primary device
(--) Chipset NVIDIA GPU found
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
(II) resource ranges after xf86ClaimFixedResources() call:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafec00 - 0xfeafec0f (0x10) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[10] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[11] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[12] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[13] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[14] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[15] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[16] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[17] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
(II) resource ranges after probing:
	[0] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[1] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[2] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[3] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[4] -1	0	0xfeafec00 - 0xfeafec0f (0x10) MX[B]
	[5] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[6] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[7] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[8] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[9] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B]
	[10] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B]
	[11] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B]
	[12] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[13] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[14] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[15] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[16] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[17] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[18] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[19] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[20] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[21] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B]
	[22] 0	0	0x000003c0 - 0x000003df (0x20) IS[B]
[COLOR="DarkGreen"](II) Setting vga for screen 0.
(**) NVIDIA(0): Depth 24, (--) framebuffer bpp 32
(==) NVIDIA(0): RGB weight 888
(==) NVIDIA(0): Default visual is TrueColor
(==) NVIDIA(0): Using gamma correction (1.0, 1.0, 1.0)
(**) NVIDIA(0): Option "NoLogo" "True"
(**) NVIDIA(0): Option "UseEdidFreqs" "false"
(**) NVIDIA(0): Option "AddARGBGLXVisuals" "True"
(**) NVIDIA(0): Enabling RENDER acceleration
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
(II) NVIDIA(0): Support for GLX with the Damage and Composite X extensions is
(II) NVIDIA(0):     enabled.
(II) NVIDIA(0): NVIDIA GPU GeForce FX 5200 at PCI:1:0:0 (GPU-0)
(--) NVIDIA(0): Memory: 131072 kBytes
(--) NVIDIA(0): VideoBIOS: 04.34.20.27.00
(II) NVIDIA(0): Detected AGP rate: 4X
(--) NVIDIA(0): Interlaced video modes are supported on this GPU
(--) NVIDIA(0): Connected display device(s) on GeForce FX 5200 at PCI:1:0:0:
(--) NVIDIA(0):     ViewSonic A90f+ (CRT-0)
(--) NVIDIA(0): ViewSonic A90f+ (CRT-0): 350.0 MHz maximum pixel clock
(II) NVIDIA(0): Assigned Display Device: CRT-0
(II) NVIDIA(0): Validated modes:
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0):     "1280x1024_80"
(II) NVIDIA(0): Virtual screen size determined to be 1280 x 1024
(--) NVIDIA(0): DPI set to (90, 96); computed from "UseEdidDpi" X config
(--) NVIDIA(0):     option
(--) Depth 24 pixmap format is 32 bpp[/COLOR]
(II) do I need RAC?  No, I don't.
(II) resource ranges after preInit:
	[0] 0	0	0xe8000000 - 0xefffffff (0x8000000) MX[B]
	[1] 0	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B]
	[2] -1	0	0x00100000 - 0x3fffffff (0x3ff00000) MX[B]E(B)
	[3] -1	0	0x000f0000 - 0x000fffff (0x10000) MX[B]
	[4] -1	0	0x000c0000 - 0x000effff (0x30000) MX[B]
	[5] -1	0	0x00000000 - 0x0009ffff (0xa0000) MX[B]
	[6] -1	0	0xfeafec00 - 0xfeafec0f (0x10) MX[B]
	[7] -1	0	0xf8000000 - 0xf7ffffff (0x0) MX[B]O
	[8] -1	0	0xfe9e0000 - 0xfe9fffff (0x20000) MX[B](B)
	[9] -1	0	0xe8000000 - 0xefffffff (0x8000000) MX[B](B)
	[10] -1	0	0xfd000000 - 0xfdffffff (0x1000000) MX[B](B)
	[11] 0	0	0x000a0000 - 0x000affff (0x10000) MS[B](OprD)
	[12] 0	0	0x000b0000 - 0x000b7fff (0x8000) MS[B](OprD)
	[13] 0	0	0x000b8000 - 0x000bffff (0x8000) MS[B](OprD)
	[14] -1	0	0x0000ffff - 0x0000ffff (0x1) IX[B]
	[15] -1	0	0x00000000 - 0x000000ff (0x100) IX[B]
	[16] -1	0	0x0000dfa0 - 0x0000dfaf (0x10) IX[B]
	[17] -1	0	0x0000ef00 - 0x0000ef3f (0x40) IX[B]
	[18] -1	0	0x0000e800 - 0x0000e8ff (0x100) IX[B]
	[19] -1	0	0x0000ef80 - 0x0000ef9f (0x20) IX[B]
	[20] -1	0	0x0000efa0 - 0x0000efaf (0x10) IX[B]
	[21] -1	0	0x0000ef40 - 0x0000ef5f (0x20) IX[B]
	[22] -1	0	0x0000ffa0 - 0x0000ffaf (0x10) IX[B]
	[23] 0	0	0x000003b0 - 0x000003bb (0xc) IS[B](OprU)
	[24] 0	0	0x000003c0 - 0x000003df (0x20) IS[B](OprU)
[COLOR="DarkGreen"](II) NVIDIA(0): Setting mode "1280x1024_80"[/COLOR]
(II) Loading extension NV-GLX
(II) NVIDIA(0): NVIDIA 3D Acceleration Architecture Initialized
(II) NVIDIA(0): Using the NVIDIA 2D acceleration architecture
(==) NVIDIA(0): Backing store disabled
(==) NVIDIA(0): Silken mouse enabled
(**) Option "dpms"
(**) NVIDIA(0): DPMS enabled
(II) Loading extension NV-CONTROL
(WW) NVIDIA(0): Option "AddARGBVisuals" is not used
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
(II) Initializing extension GLX
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
(**) Option "CustomKeycodes" "off"
(**) Generic Keyboard: CustomKeycodes disabled
(**) Option "Protocol" "ImPS/2"
(**) Configured Mouse: Device: "/dev/input/mice"
(**) Configured Mouse: Protocol: "ImPS/2"
(**) Option "CorePointer"
(**) Configured Mouse: Core Pointer
(**) Option "Device" "/dev/input/mice"
(**) Option "Buttons" "5"
(**) Option "Emulate3Buttons" "false"
(**) Option "ZAxisMapping" "4 5"
(**) Configured Mouse: ZAxisMapping: buttons 4 and 5
(**) Option "ButtonMapping" "1 2 3 6 7"
(**) Configured Mouse: Buttons: 11
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
(II) XINPUT: Adding extended input device "NVIDIA Damage Notification Manager" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Kernel RC Handler" (type: Other)
(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(**) Option "Device" "/dev/input/wacom"
(EE) xf86OpenSerial: Cannot open device /dev/input/wacom
	No such file or directory.
Error opening /dev/input/wacom : Success
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from list!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from list!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from list!
[COLOR="Red"](II) NVIDIA(0): Setting mode "1152x864"[/COLOR]
```

Scroll to the VERY bottom line, and you'll notice something interesting. It's fine, but then it "poof" changes the mode to "1152x864" (which isn't even supported by my monitor!) Why does it do this???

---

### Post by Dave54 on 2007-04-21
It works!!!! :guitar: \\:D/ 

System > Preferences > Screen Resolution is **still** messed up as ever, but that doesn't really matter because **I got 1280x1024 @ 80Hz to work!**

I ran
```
nvidia-settings
```
and selected 1280x1024, and looked at the refresh rates. It had listed (as usual) Auto, 75 Hz (1), 75 Hz (2), and 60 Hz. (Pretty messed up, I know). But there under them all a new one appeared: 80 Hz! Selecting it works perfectly!

I just realized it may not stick after a reboot though. Be right back 8-)

Edit:
I restarted and the settings didn't stick So I went to System > Preferences > Screen Resolution and chose 1280x1024 @ 57 Hz. (every hz from 50 to 59 was available, so I had to try quite a few.) This happened to actually be 80 hz (which is new since I added the modeline). So, after setting that, the settings now stick. :)

Oh, and sorry for posting so many times in a row.

---

### Post by rumli on 2007-04-23
Try 
```
Option "UseEdid" "false"
```
instead of 
```
Option "UseEdidFreqs" "false"
```

---

### Post by Dave54 on 2007-04-23
Thanks for the idea, but I found no change.

Before, the xorg log said:
```
(**) NVIDIA(0): Using HorizSync/VertRefresh ranges from the EDID has been
(**) NVIDIA(0):     disabled on all display devices.
```
Now, it says:
```
(**) NVIDIA(0): Ignoring EDIDs
```
:confused: 

I guess I like the way it's worded now better, but what's the diffrence between ```
Option "UseEdidFreqs" "false"
``` and ```
Option "UseEdid" "false"
```?

---

### Post by rumli on 2007-04-23
I think
```

    Option "UseEdid" "false"

```
is the same as 
```

    Option "UseEDIDFreqs" "FALSE"
    Option "UseEDIDDpi" "FALSE"
    Option "ModeValidation" "NoEdidModes"

```

See [here]("http://http.download.nvidia.com/XFree86/Linux-x86/1.0-8774/README/appendix-d.html") for more info.

---

### Post by al_sharpe on 2007-04-23
I am also frustrated by the same lack of nvidia and xorg playing well together in Ubuntu.

The strange thing to me is that Simply Mepis 6.5 a derivative of Ubuntu installs the nvidia drivers and

the xorg file correctly and the screen resolutions are supported properly.

The Ubuntu team should talk to the 1 man team. or better yet HIRE him.

Frustrated also,

Al Sharpe

---

### Post by Dave54 on 2007-04-24
The solution has been found!

I think the solution only works for nvidia cards, but the problem only occurs if you have an nvidia card ;-) 

Backup your xorg.conf:
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
```

Edit your xorg.conf:
```
sudo gedit /etc/X11/xorg.conf
```

Scroll down to "Section "Device"". Within that section, it should have "Driver "nvidia"". Add the following to that section:
```
    Option "DynamicTwinView" "false"
```

So mine looks like this:
```
Section "Device"
    Identifier     "nVidia Corporation NV34 [GeForce FX 5200]"
    Driver         "nvidia"
    Option         "DynamicTwinView" "false"
EndSection
```

Save and reboot. (or log out and hit ctrl+alt+backspace)

Post if it works :) 

Where this solution came from:
[http://ubuntuforums.org/showthread.php?t=417716]("http://ubuntuforums.org/showthread.php?t=417716")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/108775")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/104105")
[https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292]("https://bugs.launchpad.net/ubuntu/+source/linux-restricted-modules-2.6.20/+bug/91292")

---

### Post by deroby on 2007-04-30
Sadly, it did not work for me :( 

I played around a bit with the "nvidia-settings" program, but it seems to insist that the native resolution of my DFP is 1400x1050, while it clearly is 1600x1200 (Inspiron 8500), the bottom & right are filled with a combination of gibberish stripes and a copy of the top / left part of the screen.

I tried lowering the colors as I presumed it might be because it only has 32Mb (GeForce 4 440Go), but that didn't change anything... so far, the only way to work on the full resolution of my portable is by disabling the nvidia restricted driver...

I did see something about "import EDID", not sure if that might help me out ?

---

### Post by Dave54 on 2007-04-30
> **deroby said:**
> Sadly, it did not work for me :( 

Open Applications > Accessories > Terminal.
Run:
```
sudo gedit /etc/X11/xorg.conf
```
Copy and paste the file here.

When you post the file, be sure to hit the little "#" sign above the text box and paste the xorg within the [****CODE] and [****/CODE] tags.

---

