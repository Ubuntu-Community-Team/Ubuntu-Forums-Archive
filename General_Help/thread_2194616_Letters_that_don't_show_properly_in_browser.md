---
title: "Letters that don't show properly in browser"
date: 2013-12-19
forum: General Help
---

### Post by franciscojhh on 2013-12-19
I have a problem that it is a bit difficult to explain. After updating to the most recent release of xubuntu I have problems when browsing with Firefox. Sometimes, some letters (up to 3 or so per page) fail to display properly, and instead the browser shows a small point, an empty space, or a small black symbol. When realoading or when scrolling down until the text dissappears and then scrolling upwards again, the letters that were not displayed correctly appear and some of the ones displayed correctly are substituted by these points or small symbols. In fact, while I am writing this lines, some of the letters are turned into the points/symbols and back again to normal. It is very annoying!! 

What could be causing this behaviour?

Best,

Fran

---

### Post by philinux on 2013-12-19
You are not alone.

[http://ubuntuforums.org/showthread.php?t=2183584&highlight=smirched](http://ubuntuforums.org/showthread.php?t=2183584&highlight=smirched)

---

### Post by Toz on 2013-12-19
If you have an intel graphics card and are using 13.10, the default acceleration method was changed from uxa to sna. On some systems, sna acceleration causes graphic "artefacts". The solution (workaround?) is to revert to uxa acceleration.

To find out which acceleration method you are using:
```
cat /var/log/Xorg.0.log | grep -i accelmethod
```
...example result:
> [     4.104] (**) intel(0): Option "AccelMethod" "sna"

To revert to uxa acceleration, with root privileges, create a **/usr/share/X11/xorg.conf.d/20-intel.conf** file with the following content:
```
Section "Device"
	Identifier 	"Intel Graphics"
	Driver 		"intel"
	Option		"AccelMethod"		"uxa"
	Option		"TearFree"		"true"
EndSection
```
...save the file, log out and log in again.

On reboot, check whether its properly enabled with:
```
cat /var/log/Xorg.0.log | grep -i accelmethod
```
...and check for the artifacts again.

***Remember, this will only work with intel graphics cards.

---

### Post by franciscojhh on 2013-12-19
The code
```

cat /var/log/Xorg.0.log | grep -i accelmethod

```

does not return anything

```
lspci | grep VGA
```

returns:

```
>00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
```

Do you think the workaround would work in my system?

---

### Post by Toz on 2013-12-19
You do have an intel card.

What version of ubuntu are you running and what kernel is active?
```
uname -r
```

Can you post back your complete /var/log/Xorg.0.log file?

---

### Post by vasa1 on 2013-12-19
Hi Toz, I'm having the same problem but not as severe as the OP has. In my case, these malformed letters appear quite infrequently. My hardware is a Dell Inspiron 1545 laptop.

The /var/log/Xorg.0.log details are here: 
[http://paste.ubuntu.com/6603101/](http://paste.ubuntu.com/6603101/)
because grepping for accelmethod didn't return anything.

And uname -r  gives
```
3.11.0-14-generic
```

Edit: I understand that my graphics is "integrated" and incapable of hardware acceleration.

---

### Post by Toz on 2013-12-19
Looks like I goofed again. The command should be:
```
cat /var/log/Xorg.0.log | grep -i sna
```
...to see if SNA is enabled and:
```
cat /var/log/Xorg.0.log | grep -i uxa
```
...to see if UXA is enabled.

Vasa1, in your case:
> [    25.176] (II) intel(0): SNA initialized with Eaglelake (gen4.5) backend
...yes, sna is enabled. You can try using uxa instead with the file above.

I have the same problem on my laptop (not severe at all) and disabling SNA gets rid of it but I notice that graphics performance is better with SNA.

---

### Post by SantaFe on 2013-12-19
First of all, I would like to thank Toz for showing what's up with the funny letters problem.  My Dell Studio 1745 was doing the same thing so after seeing I indeed had sna instead of uxa I added the 20-intel.conf file as you suggested.  

Hilarity ensued, as the funniest graphics problems occurred during boot up.  First, the KDM Login menu graphic grew 3 sizes too big.  Then the KDE splash screen spinning indicator showed up 3 sizes too small (guess KDE was having a Grinch moment there).  Then it starts showing the desktop, but in slices far right, then a second later the middle then finally the left.   I tried rebooting, same thing.  Removed the 20-intel.conf file, rebooted, everything's back to normal.  Hmmmmm........ :D

To be honest, I have NO Idea what went wrong there, but sure hope Intel gets a working display driver out soon. :D

Of course, other peoples experiences will probably be different, but gosh I wish I had a Cell Phone or Digital camers so I could have filmed it, it was pretty funny (scary at first, but funny).  :)

Oh Snap, I forgot to say this was all going on on the external monitor, as the primary laptop screen is broken.  Lucky for me I had rearranged the grub2 menu to have Kubuntu first & Windows 7 second in the order so all I have to do is wait a couple of seconds & hit enter.

---

### Post by vasa1 on 2013-12-19
> **Toz said:**
> ...
I have the same problem on my laptop (not severe at all) and disabling SNA gets rid of it but I notice that graphics performance is better with SNA.

Thank you for mentioning the trade-off. In that case, I'll stay with the infrequent deformed letters (and keep this in mind in case things get unbearable). But if you know of a bug to "me too", please let us know.

---

### Post by Toz on 2013-12-19
@SantaFe, really weird, I've never heard of an issue like that. I wouldn't mind seeing your Xorg.0.log file from that boot (Xorg.0.log.old?)

@Vasa1, [here is an article]("http://www.phoronix.com/scan.php?page=news_item&px=MTM4MTI") from Phoronix about UXA/SNA performance benchmarks.

---

### Post by vasa1 on 2013-12-19
> **Toz said:**
> ...
@Vasa1, [here is an article]("http://www.phoronix.com/scan.php?page=news_item&px=MTM4MTI") from Phoronix about UXA/SNA performance benchmarks.
Some of the differences are amazing: even if a little bit trickles down to older systems, that'll be good.

---

### Post by VinDSL on 2013-12-19
This seems to have taken care of the smirched characters on my Dell Latitude ATG D630 laptop.

** /usr/share/X11/xorg.conf.d/20-intel.conf **
```
Section "Device"
 Identifier "Intel Graphics"
 Driver "intel"
 Option "AccelMethod" "sna"
 Option "DRI" "False"
EndSection
```

I retained SNA acceleration, but disabled 3D acceleration...

---

### Post by SantaFe on 2013-12-19
> **Toz said:**
> @SantaFe, really weird, I've never heard of an issue like that. I wouldn't mind seeing your Xorg.0.log file from that boot (Xorg.0.log.old?)

@Vasa1, [here is an article]("http://www.phoronix.com/scan.php?page=news_item&px=MTM4MTI") from Phoronix about UXA/SNA performance benchmarks.

```

[    36.069] 
X.Org X Server 1.14.5
Release Date: 2013-12-12
[    36.069] X Protocol Version 11, Revision 0
[    36.069] Build Operating System: Linux 3.2.0-54-generic i686 Ubuntu
[    36.069] Current Operating System: Linux santafe-Studio-1745 3.11.0-15-generic #23-Ubuntu SMP Mon Dec 9 18:16:27 UTC 2013 i686
[    36.069] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.11.0-15-generic root=UUID=2e324293-900f-4321-8b12-42bb5bded9da ro quiet splash vt.handoff=7
[    36.069] Build Date: 17 December 2013  10:03:52AM
[    36.069] xorg-server 2:1.14.5-1ubuntu2~saucy1 (For technical support please see http://www.ubuntu.com/support) 
[    36.069] Current version of pixman: 0.30.2
[    36.069]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    36.069] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    36.069] (==) Log file: "/var/log/Xorg.0.log", Time: Thu Dec 19 21:01:41 2013
[    36.123] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    36.190] (==) No Layout section.  Using the first Screen section.
[    36.190] (==) No screen section available. Using defaults.
[    36.190] (**) |-->Screen "Default Screen Section" (0)
[    36.190] (**) |   |-->Monitor "<default monitor>"
[    36.190] (==) No device specified for screen "Default Screen Section".
    Using the first device section listed.
[    36.190] (**) |   |-->Device "Intel Graphics"
[    36.190] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    36.190] (==) Automatically adding devices
[    36.190] (==) Automatically enabling devices
[    36.190] (==) Automatically adding GPU devices
[    36.190] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    36.190]     Entry deleted from font path.
[    36.190] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/100dpi/:unscaled,
    /usr/share/fonts/X11/75dpi/:unscaled,
    /usr/share/fonts/X11/Type1,
    /usr/share/fonts/X11/100dpi,
    /usr/share/fonts/X11/75dpi,
    built-ins
[    36.190] (==) ModulePath set to "/usr/lib/i386-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    36.190] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    36.190] (II) Loader magic: 0xb77dd6a0
[    36.190] (II) Module ABI versions:
[    36.190]     X.Org ANSI C Emulation: 0.4
[    36.190]     X.Org Video Driver: 14.1
[    36.190]     X.Org XInput driver : 19.1
[    36.190]     X.Org Server Extension : 7.0
[    36.191] (II) xfree86: Adding drm device (/dev/dri/card0)
[    36.193] (--) PCI:*(0:0:2:0) 8086:2a42:1028:02ea rev 7, Mem @ 0xf2400000/4194304, 0xd0000000/268435456, I/O @ 0x00001800/8
[    36.193] (--) PCI: (0:0:2:1) 8086:2a43:1028:02ea rev 7, Mem @ 0xf2100000/1048576
[    36.194] (II) Open ACPI successful (/var/run/acpid.socket)
[    36.194] Initializing built-in extension Generic Event Extension
[    36.194] Initializing built-in extension SHAPE
[    36.194] Initializing built-in extension MIT-SHM
[    36.194] Initializing built-in extension XInputExtension
[    36.194] Initializing built-in extension XTEST
[    36.194] Initializing built-in extension BIG-REQUESTS
[    36.194] Initializing built-in extension SYNC
[    36.194] Initializing built-in extension XKEYBOARD
[    36.194] Initializing built-in extension XC-MISC
[    36.194] Initializing built-in extension SECURITY
[    36.194] Initializing built-in extension XINERAMA
[    36.194] Initializing built-in extension XFIXES
[    36.194] Initializing built-in extension RENDER
[    36.194] Initializing built-in extension RANDR
[    36.194] Initializing built-in extension COMPOSITE
[    36.194] Initializing built-in extension DAMAGE
[    36.194] Initializing built-in extension MIT-SCREEN-SAVER
[    36.194] Initializing built-in extension DOUBLE-BUFFER
[    36.194] Initializing built-in extension RECORD
[    36.194] Initializing built-in extension DPMS
[    36.194] Initializing built-in extension X-Resource
[    36.194] Initializing built-in extension XVideo
[    36.194] Initializing built-in extension XVideo-MotionCompensation
[    36.194] Initializing built-in extension SELinux
[    36.194] Initializing built-in extension XFree86-VidModeExtension
[    36.194] Initializing built-in extension XFree86-DGA
[    36.194] Initializing built-in extension XFree86-DRI
[    36.194] Initializing built-in extension DRI2
[    36.194] (II) "glx" will be loaded by default.
[    36.194] (WW) "xmir" is not to be loaded by default. Skipping.
[    36.194] (II) LoadModule: "dri2"
[    36.194] (II) Module "dri2" already built-in
[    36.194] (II) LoadModule: "glamoregl"
[    36.307] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[    36.875] (II) Module glamoregl: vendor="X.Org Foundation"
[    36.875]     compiled for 1.14.3, module version = 0.5.1
[    36.875]     ABI class: X.Org ANSI C Emulation, version 0.4
[    36.875] (II) LoadModule: "glx"
[    36.875] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    36.875] (II) Module glx: vendor="X.Org Foundation"
[    36.875]     compiled for 1.14.5, module version = 1.0.0
[    36.875]     ABI class: X.Org Server Extension, version 7.0
[    36.875] (==) AIGLX enabled
[    36.875] Loading extension GLX
[    36.875] (II) LoadModule: "intel"
[    36.876] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    36.925] (II) Module intel: vendor="X.Org Foundation"
[    36.925]     compiled for 1.14.3, module version = 2.99.904
[    36.925]     Module class: X.Org Video Driver
[    36.925]     ABI class: X.Org Video Driver, version 14.1
[    36.925] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43, HD Graphics,
    HD Graphics 2000, HD Graphics 3000, HD Graphics 2500,
    HD Graphics 4000, HD Graphics P4000, HD Graphics 4600,
    HD Graphics 5000, HD Graphics P4600/P4700, Iris(TM) Graphics 5100,
    HD Graphics 4400, HD Graphics 4200, Iris(TM) Pro Graphics 5200
[    36.925] (++) using VT number 8

[    36.931] (II) intel(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    36.931] (==) intel(0): Depth 24, (--) framebuffer bpp 32
[    36.931] (==) intel(0): RGB weight 888
[    36.931] (==) intel(0): Default visual is TrueColor
[    36.931] (**) intel(0): Option "AccelMethod" "uxa"
[    36.931] (**) intel(0): Option "TearFree" "true"
[    36.931] (--) intel(0): Integrated Graphics Chipset: Intel(R) GM45
[    36.931] (**) intel(0): Relaxed fencing enabled
[    36.931] (**) intel(0): Wait on SwapBuffers? enabled
[    36.931] (**) intel(0): Triple buffering? enabled
[    36.931] (**) intel(0): Framebuffer tiled
[    36.931] (**) intel(0): Pixmaps tiled
[    36.931] (**) intel(0): 3D buffers tiled
[    36.931] (**) intel(0): SwapBuffers wait enabled
[    36.931] (==) intel(0): video overlay key set to 0x101fe
[    36.931] (II) intel(0): Output LVDS1 has no monitor section
[    36.932] (--) intel(0): found backlight control interface /sys/class/backlight/acpi_video0
[    36.956] (II) intel(0): Output VGA1 has no monitor section
[    36.964] (II) intel(0): Output HDMI1 has no monitor section
[    37.012] (II) intel(0): Output DP1 has no monitor section
[    37.328] (II) intel(0): Output HDMI2 has no monitor section
[    37.380] (II) intel(0): Output DP2 has no monitor section
[    37.380] (II) intel(0): Output DP3 has no monitor section
[    37.380] (II) intel(0): EDID for output LVDS1
[    37.380] (II) intel(0): Manufacturer: LGD  Model: 21d  Serial#: 0
[    37.380] (II) intel(0): Year: 2009  Week: 0
[    37.380] (II) intel(0): EDID Version: 1.3
[    37.380] (II) intel(0): Digital Display Input
[    37.380] (II) intel(0): Max Image Size [cm]: horiz.: 38  vert.: 21
[    37.380] (II) intel(0): Gamma: 2.20
[    37.380] (II) intel(0): No DPMS capabilities specified
[    37.380] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    37.380] (II) intel(0): First detailed timing is preferred mode
[    37.380] (II) intel(0): redX: 0.618 redY: 0.348   greenX: 0.312 greenY: 0.598
[    37.380] (II) intel(0): blueX: 0.150 blueY: 0.110   whiteX: 0.313 whiteY: 0.329
[    37.380] (II) intel(0): Manufacturer's mask: 0
[    37.380] (II) intel(0): Supported detailed timing:
[    37.380] (II) intel(0): clock: 100.0 MHz   Image Size:  382 x 215 mm
[    37.380] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1824 h_border: 0
[    37.380] (II) intel(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
[    37.380] (II) intel(0): Supported detailed timing:
[    37.380] (II) intel(0): clock: 100.0 MHz   Image Size:  382 x 215 mm
[    37.380] (II) intel(0): h_active: 1600  h_sync: 1648  h_sync_end 1696 h_blank_end 1824 h_border: 0
[    37.380] (II) intel(0): v_active: 900  v_sync: 902  v_sync_end 905 v_blanking: 912 v_border: 0
[    37.380] (II) intel(0):  MC13K&#8364;173WD1
[    37.380] (II) intel(0): Unknown vendor-specific block 0
[    37.380] (II) intel(0): EDID (in hex):
[    37.380] (II) intel(0):     00ffffffffffff0030e41d0200000000
[    37.380] (II) intel(0):     00130103902615780a4c959e594f9926
[    37.380] (II) intel(0):     1c505400000001010101010101010101
[    37.380] (II) intel(0):     0101010101010b2740e060840c303030
[    37.380] (II) intel(0):     23007ed71000001a0b2740e060840c30
[    37.380] (II) intel(0):     303023007ed71000001a000000fe004d
[    37.380] (II) intel(0):     4331334b803137335744310a00000000
[    37.380] (II) intel(0):     000059012d0100000002010a202000ce
[    37.380] (II) intel(0): Not using default mode "320x240" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "400x300" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "512x384" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "640x480" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "640x512" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "800x600" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "896x672" (doublescan mode not supported)
[    37.380] (II) intel(0): Not using default mode "928x696" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "960x720" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "576x432" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "680x384" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "700x525" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "720x450" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "800x512" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "840x525" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "960x540" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "960x600" (doublescan mode not supported)
[    37.381] (II) intel(0): Not using default mode "1024x768" (doublescan mode not supported)
[    37.381] (II) intel(0): Printing probed modes for output LVDS1
[    37.381] (II) intel(0): Modeline "1600x900"x60.1   99.95  1600 1648 1696 1824  900 902 905 912 +hsync -vsync (54.8 kHz eP)
[    37.381] (II) intel(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz d)
[    37.381] (II) intel(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    37.381] (II) intel(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    37.381] (II) intel(0): Modeline "1152x864"x60.0   81.62  1152 1216 1336 1520  864 865 868 895 -hsync +vsync (53.7 kHz d)
[    37.381] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    37.381] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    37.381] (II) intel(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    37.381] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    37.404] (II) intel(0): EDID for output VGA1
[    37.412] (II) intel(0): EDID for output HDMI1
[    37.460] (II) intel(0): EDID for output DP1
[    37.772] (II) intel(0): EDID for output HDMI2
[    37.772] (II) intel(0): Manufacturer: VIZ  Model: 95  Serial#: 16843009
[    37.772] (II) intel(0): Year: 2012  Week: 41
[    37.772] (II) intel(0): EDID Version: 1.3
[    37.772] (II) intel(0): Digital Display Input
[    37.772] (II) intel(0): Max Image Size [cm]: horiz.: 70  vert.: 39
[    37.772] (II) intel(0): Gamma: 2.20
[    37.772] (II) intel(0): No DPMS capabilities specified
[    37.772] (II) intel(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    37.772] (II) intel(0): First detailed timing is preferred mode
[    37.772] (II) intel(0): redX: 0.630 redY: 0.340   greenX: 0.300 greenY: 0.630
[    37.772] (II) intel(0): blueX: 0.148 blueY: 0.068   whiteX: 0.280 whiteY: 0.290
[    37.772] (II) intel(0): Supported established timings:
[    37.772] (II) intel(0): 720x400@70Hz
[    37.772] (II) intel(0): 640x480@60Hz
[    37.772] (II) intel(0): 640x480@75Hz
[    37.772] (II) intel(0): 800x600@60Hz
[    37.772] (II) intel(0): 800x600@72Hz
[    37.772] (II) intel(0): 800x600@75Hz
[    37.772] (II) intel(0): 1024x768@60Hz
[    37.772] (II) intel(0): 1024x768@70Hz
[    37.772] (II) intel(0): 1024x768@75Hz
[    37.772] (II) intel(0): Manufacturer's mask: 0
[    37.772] (II) intel(0): Supported detailed timing:
[    37.772] (II) intel(0): clock: 85.5 MHz   Image Size:  697 x 392 mm
[    37.772] (II) intel(0): h_active: 1366  h_sync: 1494  h_sync_end 1624 h_blank_end 1798 h_border: 0
[    37.772] (II) intel(0): v_active: 768  v_sync: 770  v_sync_end 776 v_blanking: 795 v_border: 0
[    37.772] (II) intel(0): Ranges: V min: 50 V max: 77 Hz, H min: 31 H max: 70 kHz, PixClock max 155 MHz
[    37.772] (II) intel(0): Serial No: LAUFNLCP01000
[    37.772] (II) intel(0): Monitor name: E320-A0
[    37.772] (II) intel(0): Supported detailed timing:
[    37.772] (II) intel(0): clock: 148.5 MHz   Image Size:  697 x 392 mm
[    37.772] (II) intel(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    37.772] (II) intel(0): v_active: 1080  v_sync: 1085  v_sync_end 1090 v_blanking: 1125 v_border: 0
[    37.772] (II) intel(0): Supported detailed timing:
[    37.772] (II) intel(0): clock: 74.2 MHz   Image Size:  697 x 392 mm
[    37.772] (II) intel(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    37.772] (II) intel(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    37.772] (II) intel(0): Number of EDID sections to follow: 1
[    37.772] (II) intel(0): EDID (in hex):
[    37.772] (II) intel(0):     00ffffffffffff00593a950001010101
[    37.772] (II) intel(0):     29160103804627780a4d2da1574ca126
[    37.772] (II) intel(0):     11474aa5ce0001010101010101010101
[    37.772] (II) intel(0):     010101010101662156b051001b308082
[    37.772] (II) intel(0):     2600b9882100001e000000fd00324d1f
[    37.772] (II) intel(0):     460f000a202020202020000000ff004c
[    37.772] (II) intel(0):     4155464e4c43503031303030000000fc
[    37.772] (II) intel(0):     00453332302d41300a2020202020018f
[    37.772] (II) intel(0):     020324714b010384051020151213141f
[    37.772] (II) intel(0):     29090705155750000700830100006503
[    37.772] (II) intel(0):     0c001000023a801871382d40582c5500
[    37.772] (II) intel(0):     b9882100001e011d007251d01e206e28
[    37.772] (II) intel(0):     5500b9882100001e0000000000000000
[    37.772] (II) intel(0):     00000000000000000000000000000000
[    37.772] (II) intel(0):     00000000000000000000000000000000
[    37.772] (II) intel(0):     0000000000000000000000000000004b
[    37.772] (II) intel(0): Printing probed modes for output HDMI2
[    37.772] (II) intel(0): Modeline "1366x768"x59.8   85.50  1366 1494 1624 1798  768 770 776 795 +hsync +vsync (47.6 kHz eP)
[    37.772] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1085 1090 1125 +hsync +vsync (67.5 kHz e)
[    37.772] (II) intel(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    37.772] (II) intel(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    37.772] (II) intel(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    37.772] (II) intel(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    37.772] (II) intel(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    37.772] (II) intel(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    37.772] (II) intel(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    37.773] (II) intel(0): Modeline "1920x1080"x24.0   74.18  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    37.773] (II) intel(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    37.773] (II) intel(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    37.773] (II) intel(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    37.773] (II) intel(0): Modeline "1440x576i"x50.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    37.773] (II) intel(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[    37.773] (II) intel(0): Modeline "1024x768"x70.1   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    37.773] (II) intel(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    37.773] (II) intel(0): Modeline "800x600"x72.2   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    37.773] (II) intel(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    37.773] (II) intel(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    37.773] (II) intel(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    37.773] (II) intel(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    37.773] (II) intel(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    37.773] (II) intel(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    37.773] (II) intel(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.773] (II) intel(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    37.773] (II) intel(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    37.820] (II) intel(0): EDID for output DP2
[    37.820] (II) intel(0): EDID for output DP3
[    37.820] (II) intel(0): Output LVDS1 connected
[    37.820] (II) intel(0): Output VGA1 disconnected
[    37.820] (II) intel(0): Output HDMI1 disconnected
[    37.820] (II) intel(0): Output DP1 disconnected
[    37.820] (II) intel(0): Output HDMI2 connected
[    37.820] (II) intel(0): Output DP2 disconnected
[    37.820] (II) intel(0): Output DP3 disconnected
[    37.820] (II) intel(0): Using fuzzy aspect match for initial modes
[    37.820] (II) intel(0): Output LVDS1 using initial mode 1024x768
[    37.820] (II) intel(0): Output HDMI2 using initial mode 1024x768
[    37.820] (II) intel(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    37.820] (II) intel(0): Kernel page flipping support detected, enabling
[    37.820] (==) intel(0): DPI set to (96, 96)
[    37.820] (II) Loading sub module "fb"
[    37.820] (II) LoadModule: "fb"
[    37.820] (II) Loading /usr/lib/xorg/modules/libfb.so
[    38.168] (II) Module fb: vendor="X.Org Foundation"
[    38.168]     compiled for 1.14.5, module version = 1.0.0
[    38.168]     ABI class: X.Org ANSI C Emulation, version 0.4
[    38.168] (II) Loading sub module "dri2"
[    38.168] (II) LoadModule: "dri2"
[    38.168] (II) Module "dri2" already built-in
[    38.168] (==) Depth 24 pixmap format is 32 bpp
[    38.169] (II) intel(0): [DRI2] Setup complete
[    38.169] (II) intel(0): [DRI2]   DRI driver: i965
[    38.169] (II) intel(0): Allocated new frame buffer 1024x768 stride 4096, tiled
[    38.180] (II) UXA(0): Driver registered support for the following operations:
[    38.180] (II)         solid
[    38.180] (II)         copy
[    38.180] (II)         composite (RENDER acceleration)
[    38.180] (II)         put_image
[    38.180] (II)         get_image
[    38.180] (==) intel(0): Backing store disabled
[    38.180] (==) intel(0): Silken mouse enabled
[    38.180] (II) intel(0): Initializing HW Cursor
[    38.180] (II) intel(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    38.192] (==) intel(0): DPMS enabled
[    38.192] (==) intel(0): Intel XvMC decoder enabled
[    38.192] (II) intel(0): Set up textured video
[    38.192] (II) intel(0): [XvMC] xvmc_vld driver initialized.
[    38.192] (II) intel(0): direct rendering: DRI2 Enabled
[    38.192] (==) intel(0): hotplug detection: "enabled"
[    39.308] (--) RandR disabled
[    39.316] (II) SELinux: Disabled on system
[    39.408] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    39.408] (II) AIGLX: enabled GLX_INTEL_swap_event
[    39.408] (II) AIGLX: enabled GLX_ARB_create_context
[    39.408] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    39.408] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    39.408] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    39.408] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    39.408] (II) AIGLX: Loaded and initialized i965
[    39.408] (II) GLX: Initialized DRI2 GL provider for screen 0
[    39.408] (II) intel(0): Setting screen physical size to 270 x 203
[    39.432] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    39.436] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    39.436] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.436] (II) LoadModule: "evdev"
[    39.436] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    39.445] (II) Module evdev: vendor="X.Org Foundation"
[    39.445]     compiled for 1.14.1, module version = 2.7.3
[    39.445]     Module class: X.Org XInput Driver
[    39.445]     ABI class: X.Org XInput driver, version 19.1
[    39.445] (II) Using input driver 'evdev' for 'Power Button'
[    39.446] (**) Power Button: always reports core events
[    39.446] (**) evdev: Power Button: Device: "/dev/input/event2"
[    39.446] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.446] (--) evdev: Power Button: Found keys
[    39.446] (II) evdev: Power Button: Configuring as keyboard
[    39.446] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    39.446] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    39.446] (**) Option "xkb_rules" "evdev"
[    39.446] (**) Option "xkb_model" "pc105"
[    39.446] (**) Option "xkb_layout" "us"
[    39.446] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    39.446] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    39.446] (II) Using input driver 'evdev' for 'Video Bus'
[    39.446] (**) Video Bus: always reports core events
[    39.446] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    39.446] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    39.446] (--) evdev: Video Bus: Found keys
[    39.446] (II) evdev: Video Bus: Configuring as keyboard
[    39.446] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input6/event6"
[    39.446] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    39.446] (**) Option "xkb_rules" "evdev"
[    39.446] (**) Option "xkb_model" "pc105"
[    39.446] (**) Option "xkb_layout" "us"
[    39.447] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[    39.447] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    39.447] (II) Using input driver 'evdev' for 'Power Button'
[    39.447] (**) Power Button: always reports core events
[    39.447] (**) evdev: Power Button: Device: "/dev/input/event1"
[    39.447] (--) evdev: Power Button: Vendor 0 Product 0x1
[    39.447] (--) evdev: Power Button: Found keys
[    39.447] (II) evdev: Power Button: Configuring as keyboard
[    39.447] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/device:00/PNP0C0C:00/input/input1/event1"
[    39.447] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    39.447] (**) Option "xkb_rules" "evdev"
[    39.447] (**) Option "xkb_model" "pc105"
[    39.447] (**) Option "xkb_layout" "us"
[    39.448] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    39.448] (II) No input driver specified, ignoring this device.
[    39.448] (II) This device may have been added with another device file.
[    39.448] (II) config/udev: Adding drm device (/dev/dri/card0)
[    39.448] (II) config/udev: Ignoring already known drm device (/dev/dri/card0)
[    39.448] (II) config/udev: Adding input device Laptop_Integrated_Webcam_2M (/dev/input/event7)
[    39.448] (**) Laptop_Integrated_Webcam_2M: Applying InputClass "evdev keyboard catchall"
[    39.448] (II) Using input driver 'evdev' for 'Laptop_Integrated_Webcam_2M'
[    39.448] (**) Laptop_Integrated_Webcam_2M: always reports core events
[    39.448] (**) evdev: Laptop_Integrated_Webcam_2M: Device: "/dev/input/event7"
[    39.448] (--) evdev: Laptop_Integrated_Webcam_2M: Vendor 0xc45 Product 0x6406
[    39.448] (--) evdev: Laptop_Integrated_Webcam_2M: Found keys
[    39.448] (II) evdev: Laptop_Integrated_Webcam_2M: Configuring as keyboard
[    39.448] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.7/usb1/1-6/1-6:1.0/input/input7/event7"
[    39.448] (II) XINPUT: Adding extended input device "Laptop_Integrated_Webcam_2M" (type: KEYBOARD, id 9)
[    39.448] (**) Option "xkb_rules" "evdev"
[    39.448] (**) Option "xkb_model" "pc105"
[    39.448] (**) Option "xkb_layout" "us"
[    39.449] (II) config/udev: Adding input device HDA Intel Line Out (/dev/input/event10)
[    39.449] (II) No input driver specified, ignoring this device.
[    39.449] (II) This device may have been added with another device file.
[    39.449] (II) config/udev: Adding input device HDA Intel Mic (/dev/input/event11)
[    39.449] (II) No input driver specified, ignoring this device.
[    39.449] (II) This device may have been added with another device file.
[    39.449] (II) config/udev: Adding input device HDA Intel HDMI/DP,pcm=3 (/dev/input/event8)
[    39.449] (II) No input driver specified, ignoring this device.
[    39.450] (II) This device may have been added with another device file.
[    39.450] (II) config/udev: Adding input device HDA Intel Headphone (/dev/input/event9)
[    39.450] (II) No input driver specified, ignoring this device.
[    39.450] (II) This device may have been added with another device file.
[    39.450] (II) config/udev: Adding input device Dell Dell USB Keyboard (/dev/input/event4)
[    39.450] (**) Dell Dell USB Keyboard: Applying InputClass "evdev keyboard catchall"
[    39.450] (II) Using input driver 'evdev' for 'Dell Dell USB Keyboard'
[    39.450] (**) Dell Dell USB Keyboard: always reports core events
[    39.450] (**) evdev: Dell Dell USB Keyboard: Device: "/dev/input/event4"
[    39.450] (--) evdev: Dell Dell USB Keyboard: Vendor 0x413c Product 0x2003
[    39.450] (--) evdev: Dell Dell USB Keyboard: Found keys
[    39.450] (II) evdev: Dell Dell USB Keyboard: Configuring as keyboard
[    39.450] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1:1.0/input/input4/event4"
[    39.450] (II) XINPUT: Adding extended input device "Dell Dell USB Keyboard" (type: KEYBOARD, id 10)
[    39.450] (**) Option "xkb_rules" "evdev"
[    39.450] (**) Option "xkb_model" "pc105"
[    39.450] (**) Option "xkb_layout" "us"
[    39.451] (II) config/udev: Adding input device Logitech Trackball (/dev/input/event5)
[    39.451] (**) Logitech Trackball: Applying InputClass "evdev pointer catchall"
[    39.451] (II) Using input driver 'evdev' for 'Logitech Trackball'
[    39.451] (**) Logitech Trackball: always reports core events
[    39.451] (**) evdev: Logitech Trackball: Device: "/dev/input/event5"
[    39.451] (--) evdev: Logitech Trackball: Vendor 0x46d Product 0xc404
[    39.451] (--) evdev: Logitech Trackball: Found 3 mouse buttons
[    39.451] (--) evdev: Logitech Trackball: Found scroll wheel(s)
[    39.451] (--) evdev: Logitech Trackball: Found relative axes
[    39.451] (--) evdev: Logitech Trackball: Found x and y relative axes
[    39.451] (II) evdev: Logitech Trackball: Configuring as mouse
[    39.451] (II) evdev: Logitech Trackball: Adding scrollwheel support
[    39.451] (**) evdev: Logitech Trackball: YAxisMapping: buttons 4 and 5
[    39.451] (**) evdev: Logitech Trackball: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    39.451] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1d.1/usb7/7-1/7-1:1.0/input/input5/event5"
[    39.451] (II) XINPUT: Adding extended input device "Logitech Trackball" (type: MOUSE, id 11)
[    39.451] (II) evdev: Logitech Trackball: initialized for relative axes.
[    39.451] (**) Logitech Trackball: (accel) keeping acceleration scheme 1
[    39.451] (**) Logitech Trackball: (accel) acceleration profile 0
[    39.451] (**) Logitech Trackball: (accel) acceleration factor: 2.000
[    39.451] (**) Logitech Trackball: (accel) acceleration threshold: 4
[    39.452] (II) config/udev: Adding input device Logitech Trackball (/dev/input/mouse0)
[    39.452] (II) No input driver specified, ignoring this device.
[    39.452] (II) This device may have been added with another device file.
[    39.452] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    39.452] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    39.452] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    39.452] (**) AT Translated Set 2 keyboard: always reports core events
[    39.452] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    39.452] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    39.452] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    39.452] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    39.452] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    39.452] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    39.452] (**) Option "xkb_rules" "evdev"
[    39.452] (**) Option "xkb_model" "pc105"
[    39.452] (**) Option "xkb_layout" "us"
[    39.453] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event13)
[    39.453] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    39.453] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    39.453] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    39.453] (II) LoadModule: "synaptics"
[    39.453] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    39.453] (II) Module synaptics: vendor="X.Org Foundation"
[    39.453]     compiled for 1.14.2, module version = 1.7.1
[    39.453]     Module class: X.Org XInput Driver
[    39.453]     ABI class: X.Org XInput driver, version 19.1
[    39.453] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    39.453] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    39.453] (**) Option "Device" "/dev/input/event13"
[    39.624] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    39.624] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5430 (res 43)
[    39.624] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4614 (res 69)
[    39.624] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    39.624] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    39.624] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    39.624] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    39.624] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    39.624] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    39.811] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input13/event13"
[    39.811] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    39.811] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    39.811] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    39.811] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.039
[    39.811] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    39.811] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    39.811] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    39.811] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    39.811] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    39.811] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    39.811] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    39.814] (II) config/udev: Adding input device Dell WMI hotkeys (/dev/input/event12)
[    39.814] (**) Dell WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    39.814] (II) Using input driver 'evdev' for 'Dell WMI hotkeys'
[    39.814] (**) Dell WMI hotkeys: always reports core events
[    39.814] (**) evdev: Dell WMI hotkeys: Device: "/dev/input/event12"
[    39.814] (--) evdev: Dell WMI hotkeys: Vendor 0 Product 0
[    39.814] (--) evdev: Dell WMI hotkeys: Found keys
[    39.814] (II) evdev: Dell WMI hotkeys: Configuring as keyboard
[    39.814] (**) Option "config_info" "udev:/sys/devices/virtual/input/input12/event12"
[    39.814] (II) XINPUT: Adding extended input device "Dell WMI hotkeys" (type: KEYBOARD, id 14)
[    39.814] (**) Option "xkb_rules" "evdev"
[    39.814] (**) Option "xkb_model" "pc105"
[    39.814] (**) Option "xkb_layout" "us"
[    56.977] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    59.389] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    59.403] (II) intel(0): EDID vendor "LGD", prod id 541
[    59.403] (II) intel(0): Printing DDC gathered Modelines:
[    59.403] (II) intel(0): Modeline "1600x900"x0.0   99.95  1600 1648 1696 1824  900 902 905 912 +hsync -vsync (54.8 kHz eP)
[    59.861] (II) intel(0): Allocated new frame buffer 1408x768 stride 5632, tiled
[    68.713] (II) intel(0): EDID vendor "LGD", prod id 541
[    68.713] (II) intel(0): Printing DDC gathered Modelines:
[    68.713] (II) intel(0): Modeline "1600x900"x0.0   99.95  1600 1648 1696 1824  900 902 905 912 +hsync -vsync (54.8 kHz eP)
[    71.560] (II) intel(0): EDID vendor "VIZ", prod id 149
[    71.560] (II) intel(0): Using hsync ranges from config file
[    71.560] (II) intel(0): Using vrefresh ranges from config file
[    71.560] (II) intel(0): Printing DDC gathered Modelines:
[    71.560] (II) intel(0): Modeline "1366x768"x0.0   85.50  1366 1494 1624 1798  768 770 776 795 +hsync +vsync (47.6 kHz eP)
[    71.560] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1085 1090 1125 +hsync +vsync (67.5 kHz e)
[    71.560] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    71.560] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    71.560] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    71.560] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    71.560] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    71.560] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    71.560] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    71.560] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    71.560] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    71.560] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    71.560] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    71.560] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    71.560] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    71.560] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    71.560] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    71.560] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    71.560] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    71.560] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    71.560] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    81.444] (II) XKB: reuse xkmfile /var/lib/xkb/server-CB537B66032B0DBE0AE956F537017A59DB020654.xkm
[    81.856] (II) intel(0): EDID vendor "VIZ", prod id 149
[    81.856] (II) intel(0): Using hsync ranges from config file
[    81.856] (II) intel(0): Using vrefresh ranges from config file
[    81.856] (II) intel(0): Printing DDC gathered Modelines:
[    81.856] (II) intel(0): Modeline "1366x768"x0.0   85.50  1366 1494 1624 1798  768 770 776 795 +hsync +vsync (47.6 kHz eP)
[    81.856] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1085 1090 1125 +hsync +vsync (67.5 kHz e)
[    81.856] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    81.856] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    81.856] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    81.856] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    81.856] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    81.856] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    81.856] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    81.856] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    81.856] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    81.856] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    81.856] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    81.856] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    81.856] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    81.856] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    81.856] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    81.856] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    81.856] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    81.856] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    81.856] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    82.740] (II) intel(0): EDID vendor "VIZ", prod id 149
[    82.740] (II) intel(0): Using hsync ranges from config file
[    82.740] (II) intel(0): Using vrefresh ranges from config file
[    82.740] (II) intel(0): Printing DDC gathered Modelines:
[    82.740] (II) intel(0): Modeline "1366x768"x0.0   85.50  1366 1494 1624 1798  768 770 776 795 +hsync +vsync (47.6 kHz eP)
[    82.740] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1085 1090 1125 +hsync +vsync (67.5 kHz e)
[    82.740] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    82.740] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    82.740] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[    82.740] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    82.740] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[    82.740] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[    82.740] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[    82.740] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    82.740] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[    82.740] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[    82.740] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    82.740] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    82.740] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[    82.740] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    82.740] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    82.740] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[    82.740] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[    82.740] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    82.740] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   212.932] (II) intel(0): EDID vendor "VIZ", prod id 149
[   212.932] (II) intel(0): Using hsync ranges from config file
[   212.932] (II) intel(0): Using vrefresh ranges from config file
[   212.932] (II) intel(0): Printing DDC gathered Modelines:
[   212.932] (II) intel(0): Modeline "1366x768"x0.0   85.50  1366 1494 1624 1798  768 770 776 795 +hsync +vsync (47.6 kHz eP)
[   212.932] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1085 1090 1125 +hsync +vsync (67.5 kHz e)
[   212.932] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   212.932] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   212.933] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   212.933] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   212.933] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   212.933] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   212.933] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   212.933] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   212.933] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   212.933] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   212.933] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   212.933] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   212.933] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   212.933] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   212.933] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[   212.933] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   212.933] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   212.933] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   212.933] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   213.396] (II) intel(0): EDID vendor "VIZ", prod id 149
[   213.396] (II) intel(0): Using hsync ranges from config file
[   213.396] (II) intel(0): Using vrefresh ranges from config file
[   213.396] (II) intel(0): Printing DDC gathered Modelines:
[   213.396] (II) intel(0): Modeline "1366x768"x0.0   85.50  1366 1494 1624 1798  768 770 776 795 +hsync +vsync (47.6 kHz eP)
[   213.396] (II) intel(0): Modeline "1920x1080"x0.0  148.50  1920 2008 2052 2200  1080 1085 1090 1125 +hsync +vsync (67.5 kHz e)
[   213.396] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[   213.396] (II) intel(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   213.396] (II) intel(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   213.396] (II) intel(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   213.396] (II) intel(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   213.396] (II) intel(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   213.396] (II) intel(0): Modeline "1024x768"x0.0   75.00  1024 1048 1184 1328  768 771 777 806 -hsync -vsync (56.5 kHz e)
[   213.396] (II) intel(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   213.396] (II) intel(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   213.396] (II) intel(0): Modeline "800x600"x0.0   50.00  800 856 976 1040  600 637 643 666 +hsync +vsync (48.1 kHz e)
[   213.396] (II) intel(0): Modeline "720x480"x0.0   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[   213.396] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[   213.397] (II) intel(0): Modeline "1440x480i"x0.0   27.00  1440 1478 1602 1716  480 488 494 525 interlace -hsync -vsync (15.7 kHz e)
[   213.397] (II) intel(0): Modeline "720x576"x0.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[   213.397] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[   213.397] (II) intel(0): Modeline "1440x576i"x0.0   27.00  1440 1464 1590 1728  576 580 586 625 interlace -hsync -vsync (15.6 kHz e)
[   213.397] (II) intel(0): Modeline "1280x720"x0.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz e)
[   213.397] (II) intel(0): Modeline "1920x1080i"x0.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[   213.397] (II) intel(0): Modeline "1920x1080"x0.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[   225.528] (II) evdev: Dell WMI hotkeys: Close
[   225.528] (II) UnloadModule: "evdev"
[   225.528] (II) UnloadModule: "synaptics"
[   225.529] (II) evdev: AT Translated Set 2 keyboard: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Logitech Trackball: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Dell Dell USB Keyboard: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Laptop_Integrated_Webcam_2M: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Power Button: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Video Bus: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Power Button: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.706] (EE) Server terminated successfully (0). Closing log file.


```

There it is.  ;)

Have no idea where these lines came from though.
```

[   225.528] (II) evdev: Dell WMI hotkeys: Close
[   225.528] (II) UnloadModule: "evdev"
[   225.528] (II) UnloadModule: "synaptics"
[   225.529] (II) evdev: AT Translated Set 2 keyboard: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Logitech Trackball: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Dell Dell USB Keyboard: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Laptop_Integrated_Webcam_2M: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Power Button: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Video Bus: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.529] (II) evdev: Power Button: Close
[   225.529] (II) UnloadModule: "evdev"
[   225.706] (EE) Server terminated successfully (0). Closing log file.

```  

Usually the log stops at the line just above the extra lines.  Hmmmmm.... :o

---

### Post by brainwash on 2013-12-20
It has been a known issue since several months:

[https://launchpad.net/bugs/1098334](https://launchpad.net/bugs/1098334)

---

### Post by franciscojhh on 2013-12-20
I attach the otput of cat /var/log/Xorg.0.log

uname -r gives:

```
3.11.0-14-generic
```

I also discovered that cometimes I have the same problem in other programs (e.g. the terminal).

---

### Post by Toz on 2013-12-20
> **franciscojhh said:**
> I attach the otput of cat /var/log/Xorg.0.log

uname -r gives:

```
3.11.0-14-generic
```

I also discovered that cometimes I have the same problem in other programs (e.g. the terminal).

Yes, you have SNA enabled. Have you tried the file from post #3 to revert back to UXA?

---

