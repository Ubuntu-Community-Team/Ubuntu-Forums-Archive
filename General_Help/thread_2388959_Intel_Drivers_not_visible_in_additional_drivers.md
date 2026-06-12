---
title: "Intel Drivers not visible in additional drivers"
date: 2018-04-09
forum: General Help
---

### Post by tomaszmur on 2018-04-09
Hello,

Im running Lubuntu 17.10.1 on a machine with intel i7 core 8700. I got vmware workstation installed and basically use it as a host for VMs.
The issue Im having is, I dont have 3d acceleration:

tomasz@host:~$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 5.0, 256 bits)
OpenGL version string:  3.0 Mesa 17.2.8

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no

tomasz@host:~$ sudo lspci | grep -i vga
[sudo] password for tomasz: 
00:02.0 VGA compatible controller: Intel Corporation Device 3e92


I installed intel drivers:
sudo apt-get install xserver-xorg-video-intel

also additionally this microcode package:
[https://downloadcenter.intel.com/download/27591/Linux-Processor-Microcode-Data-File?product=126686](https://downloadcenter.intel.com/download/27591/Linux-Processor-Microcode-Data-File?product=126686)

Unfortunately I still dont see these drivers in additional drivers to be enabled 

tomasz@host:~$ dmesg | grep microcode
[    0.000000] microcode: microcode updated early to revision 0x84, date = 2018-01-21
[    1.032149] microcode: sig=0x906ea, pf=0x2, revision=0x84
[    1.032719] microcode: Microcode Update Driver: v2.2.



Any ideas please how to proceed?

Thanks in advance

---

### Post by SeijiSensei on 2018-04-09
I don't use VMWare, but if you're running in a VM the chances are good you're using an emulated video adapter, not the hardware one.

---

### Post by monkeybrain20122 on 2018-04-09
> **tomaszmur said:**
> Hello,

Im running Lubuntu 17.10.1 on a machine with intel i7 core 8700. I got vmware workstation installed and basically use it as a host for VMs.
The issue Im having is, I dont have 3d acceleration:

tomasz@host:~$ /usr/lib/nux/unity_support_test -p
**OpenGL vendor string:   VMware, Inc.**
**OpenGL renderer string: llvmpipe **(LLVM 5.0, 256 bits)



Did you mean you run Ubuntu as a VM guest instead of a host?

I could be wrong but I don't think 3d acceleration works in VM.

---

### Post by tomaszmur on 2018-04-09
> **monkeybrain20122 said:**
> Did you mean you run Ubuntu as a VM guest instead of a host?

I could be wrong but I don't think 3d acceleration works in VM.

I run Lubuntu on physical HW, and bunch of other stuff virtualized on VMware, hosted on that Lubuntu. I needed to improve video quality on one of win10 VMs, but Vmware workstation complains I cannot accelerate graphics, and as it looks from the output from Lubuntu, thats correct. 

$ /usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 5.0, 256 bits)
OpenGL version string:  3.0 Mesa 17.2.8

Not software rendered:    no
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

Unity 3D supported:       no


I installed all drivers for intel I found on various internet forums etc, still they dont get detected..:(

---

### Post by Frogs Hair on 2018-04-09
[COLOR=#000000]I see xserver-xorg-video-intel is installed on my computer though it does not show in additional drivers. I don't remember installing this driver manually either. ??  [/COLOR]

---

### Post by kerry_s on 2018-04-09
on mine i install beignet from software center, other wise vm's are sluggish.

---

### Post by Yellow Pasque on 2018-04-09
Need to boot with i915.alpha_support=1
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)

---

### Post by tomaszmur on 2018-04-10
> **Temüjin said:**
> Need to boot with i915.alpha_support=1
[https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1](https://www.phoronix.com/scan.php?page=article&item=coffee-uhd-graphics&num=1)

I did it and it is still the same:

cat /etc/default/grub
# If you change this file, run 'update-grub' afterwards to update
# /boot/grub/grub.cfg.
# For full documentation of the options in this file, see:
#   info -f grub -n 'Simple configuration'

GRUB_DEFAULT=0
#GRUB_HIDDEN_TIMEOUT=0
GRUB_HIDDEN_TIMEOUT_QUIET=true
GRUB_TIMEOUT=10
GRUB_DISTRIBUTOR=`lsb_release -i -s 2> /dev/null || echo Debian`
GRUB_CMDLINE_LINUX_DEFAULT="**quiet splash i915.alpha_support=1**"
GRUB_CMDLINE_LINUX=""


-------

/usr/lib/nux/unity_support_test -p
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 5.0, 256 bits)
OpenGL version string:  3.0 Mesa 17.2.8

**Not software rendered:    no**
Not blacklisted:          yes
GLX fbconfig:             yes
GLX texture from pixmap:  yes
GL npot or rect textures: yes
GL vertex program:        yes
GL fragment program:      yes
GL vertex buffer object:  yes
GL framebuffer object:    yes
GL version is 1.4+:       yes

[B]Unity 3D supported:       no
[/B]

---

### Post by Yellow Pasque on 2018-04-10
You did run 'sudo update-grub' afterwards and reboot, correct?

> I installed all drivers for intel I found on various internet forums etc

Statements like that make me cringe. There's no telling what you did to your system. Please share your /var/log/Xorg.0.log
Be sure to use code tags or pastebin as it's a large file.

---

### Post by tomaszmur on 2018-04-10
> **Temüjin said:**
> You did run 'sudo update-grub' afterwards and reboot, correct?



Statements like that make me cringe. There's no telling what you did to your system. Please share your /var/log/Xorg.0.log
Be sure to use code tags or pastebin as it's a large file.

Here is the log:

```
cat /var/log/Xorg.0.log
[     2.963]
X.Org X Server 1.19.5
Release Date: 2017-10-12
[     2.963] X Protocol Version 11, Revision 0
[     2.963] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[     2.963] Current Operating System: Linux host 4.13.0-38-generic #43-Ubuntu SMP Wed Mar 14 15:20:44 UTC 2018 x86_64
[     2.963] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-38-generic root=UUID=a4c2d4b0-3ddd-41ac-9801-4c5c50ade033 ro quiet splash i915.alpha_support=1 vt.handoff=7
[     2.963] Build Date: 15 October 2017  05:51:19PM
[     2.963] xorg-server 2:1.19.5-0ubuntu2 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support))
[     2.963] Current version of pixman: 0.34.0
[     2.963]    Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
        to make sure that you have the latest version.
[     2.963] Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[     2.963] (==) Log file: "/var/log/Xorg.0.log", Time: Tue Apr 10 11:11:10 2018
[     2.964] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[     2.964] (==) No Layout section.  Using the first Screen section.
[     2.964] (==) No screen section available. Using defaults.
[     2.964] (**) |-->Screen "Default Screen Section" (0)
[     2.964] (**) |   |-->Monitor "<default monitor>"
[     2.964] (==) No monitor specified for screen "Default Screen Section".
        Using a default monitor configuration.
[     2.964] (==) Automatically adding devices
[     2.964] (==) Automatically enabling devices
[     2.964] (==) Automatically adding GPU devices
[     2.964] (==) Automatically binding GPU devices
[     2.964] (==) Max clients allowed: 256, resource mask: 0x1fffff
[     2.964] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[     2.964]    Entry deleted from font path.
[     2.964] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[     2.964]    Entry deleted from font path.
[     2.964] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[     2.964]    Entry deleted from font path.
[     2.964] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[     2.964]    Entry deleted from font path.
[     2.964] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[     2.964]    Entry deleted from font path.
[     2.964] (==) FontPath set to:
        /usr/share/fonts/X11/misc,
        /usr/share/fonts/X11/Type1,
        built-ins
[     2.964] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[     2.964] (II) The server relies on udev to provide the list of input devices.
        If no devices become available, reconfigure udev or disable AutoAddDevices.
[     2.964] (II) Loader magic: 0x55e8e6e29020
[     2.964] (II) Module ABI versions:
[     2.964]    X.Org ANSI C Emulation: 0.4
[     2.964]    X.Org Video Driver: 23.0
[     2.964]    X.Org XInput driver : 24.1
[     2.964]    X.Org Server Extension : 10.0
[     2.964] (++) using VT number 7

[     2.964] (II) systemd-logind: logind integration requires -keeptty and -keeptty was not provided, disabling logind integration
[     2.965] (II) xfree86: Adding drm device (/dev/dri/card0)
[     2.976] (--) PCI:*(0:0:2:0) 8086:3e92:1462:7b48 rev 0, Mem @ 0xde000000/16777216, 0xc0000000/268435456, I/O @ 0x0000f000/64, BIOS @ 0x????????/131072
[     2.976] (II) LoadModule: "glx"
[     2.977] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[     2.981] (II) Module glx: vendor="X.Org Foundation"
[     2.981]    compiled for 1.19.5, module version = 1.0.0
[     2.981]    ABI class: X.Org Server Extension, version 10.0
[     2.981] (==) Matched modesetting as autoconfigured driver 0
[     2.981] (==) Matched fbdev as autoconfigured driver 1
[     2.981] (==) Matched vesa as autoconfigured driver 2
[     2.981] (==) Assigned the driver to the xf86ConfigLayout
[     2.981] (II) LoadModule: "modesetting"
[     2.981] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[     2.981] (II) Module modesetting: vendor="X.Org Foundation"
[     2.981]    compiled for 1.19.5, module version = 1.19.5
[     2.981]    Module class: X.Org Video Driver
[     2.981]    ABI class: X.Org Video Driver, version 23.0
[     2.981] (II) LoadModule: "fbdev"
[     2.981] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[     2.981] (II) Module fbdev: vendor="X.Org Foundation"
[     2.981]    compiled for 1.19.3, module version = 0.4.4
[     2.981]    Module class: X.Org Video Driver
[     2.981]    ABI class: X.Org Video Driver, version 23.0
[     2.981] (II) LoadModule: "vesa"
[     2.981] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[     2.981] (II) Module vesa: vendor="X.Org Foundation"
[     2.981]    compiled for 1.19.3, module version = 2.3.4
[     2.981]    Module class: X.Org Video Driver
[     2.981]    ABI class: X.Org Video Driver, version 23.0
[     2.981] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[     2.981] (II) FBDEV: driver for framebuffer: fbdev
[     2.981] (II) VESA: driver for VESA chipsets: vesa
[     2.992] (II) modeset(0): using drv /dev/dri/card0
[     2.992] (WW) Falling back to old probe method for fbdev
[     2.992] (II) Loading sub module "fbdevhw"
[     2.992] (II) LoadModule: "fbdevhw"
[     2.992] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[     2.992] (II) Module fbdevhw: vendor="X.Org Foundation"
[     2.992]    compiled for 1.19.5, module version = 0.0.2
[     2.992]    ABI class: X.Org Video Driver, version 23.0
[     2.992] (WW) Falling back to old probe method for vesa
[     2.992] (II) modeset(0): Creating default Display subsection in Screen section
        "Default Screen Section" for depth/fbbpp 24/32
[     2.992] (==) modeset(0): Depth 24, (==) framebuffer bpp 32
[     2.992] (==) modeset(0): RGB weight 888
[     2.992] (==) modeset(0): Default visual is TrueColor
[     2.992] (II) Loading sub module "glamoregl"
[     2.992] (II) LoadModule: "glamoregl"
[     2.992] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[     2.997] (II) Module glamoregl: vendor="X.Org Foundation"
[     2.997]    compiled for 1.19.5, module version = 1.0.0
[     2.997]    ABI class: X.Org ANSI C Emulation, version 0.4
[     2.997] (II) glamor: OpenGL accelerated X.org driver based.
[     3.022] (II) glamor: EGL version 1.4 (DRI2):
[     3.028] (II) modeset(0): glamor initialized
[     3.028] (II) modeset(0): Output DP-1 has no monitor section
[     3.036] (II) modeset(0): Output HDMI-1 has no monitor section
[     3.044] (II) modeset(0): Output HDMI-2 has no monitor section
[     3.049] (II) modeset(0): Output DP-2 has no monitor section
[     3.058] (II) modeset(0): Output HDMI-3 has no monitor section
[     3.058] (II) modeset(0): EDID for output DP-1
[     3.066] (II) modeset(0): EDID for output HDMI-1
[     3.075] (II) modeset(0): EDID for output HDMI-2
[     3.081] (II) modeset(0): EDID for output DP-2
[     3.081] (II) modeset(0): Manufacturer: ITE  Model: 6516  Serial#: 0
[     3.081] (II) modeset(0): Year: 2015  Week: 3
[     3.081] (II) modeset(0): EDID Version: 1.4
[     3.081] (II) modeset(0): Analog Display Input,  Input Voltage Level: 0.700/0.300 V
[     3.081] (II) modeset(0): Sync:
[     3.081] (II) modeset(0): Max Image Size [cm]: horiz.: 60  vert.: 34
[     3.081] (II) modeset(0): Gamma: 2.20
[     3.081] (II) modeset(0): No DPMS capabilities specified; RGB/Color Display
[     3.081] (II) modeset(0): First detailed timing is preferred mode
[     3.081] (II) modeset(0): Preferred mode is native pixel format and refresh rate
[     3.081] (II) modeset(0): redX: 0.637 redY: 0.351   greenX: 0.319 greenY: 0.626
[     3.081] (II) modeset(0): blueX: 0.145 blueY: 0.061   whiteX: 0.313 whiteY: 0.329
[     3.081] (II) modeset(0): Supported established timings:
[     3.081] (II) modeset(0): 640x480@60Hz
[     3.081] (II) modeset(0): 800x600@60Hz
[     3.081] (II) modeset(0): 1024x768@60Hz
[     3.081] (II) modeset(0): Manufacturer's mask: 0
[     3.081] (II) modeset(0): Supported standard timings:
[     3.081] (II) modeset(0): #0: hsize: 1280  vsize 720  refresh: 60  vid: 49281
[     3.081] (II) modeset(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[     3.081] (II) modeset(0): #2: hsize: 1600  vsize 1200  refresh: 60  vid: 16553
[     3.081] (II) modeset(0): #3: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[     3.081] (II) modeset(0): #4: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[     3.081] (II) modeset(0): #5: hsize: 1400  vsize 1050  refresh: 60  vid: 16528
[     3.081] (II) modeset(0): #6: hsize: 1440  vsize 900  refresh: 60  vid: 149
[     3.081] (II) modeset(0): #7: hsize: 1600  vsize 900  refresh: 60  vid: 49321
[     3.081] (II) modeset(0): Supported detailed timing:
[     3.081] (II) modeset(0): clock: 65.0 MHz   Image Size:  256 x 192 mm
[     3.081] (II) modeset(0): h_active: 1024  h_sync: 1048  h_sync_end 1184 h_blank_end 1344 h_border: 0
[     3.081] (II) modeset(0): v_active: 768  v_sync: 771  v_sync_end 777 v_blanking: 806 v_border: 0
[     3.081] (II) modeset(0): Supported detailed timing:
[     3.081] (II) modeset(0): clock: 85.5 MHz   Image Size:  341 x 192 mm
[     3.081] (II) modeset(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[     3.081] (II) modeset(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[     3.081] (II) modeset(0): Monitor name: DP2VGA V226
[     3.081] (II) modeset(0): Supported detailed timing:
[     3.081] (II) modeset(0): clock: 108.0 MHz   Image Size:  320 x 240 mm
[     3.081] (II) modeset(0): h_active: 1280  h_sync: 1376  h_sync_end 1488 h_blank_end 1800 h_border: 0
[     3.081] (II) modeset(0): v_active: 960  v_sync: 961  v_sync_end 964 v_blanking: 1000 v_border: 0
[     3.081] (II) modeset(0): EDID (in hex):
[     3.081] (II) modeset(0):   00ffffffffffff002685166500000000
[     3.081] (II) modeset(0):   03190104003c22780a3d25a35951a025
[     3.081] (II) modeset(0):   0f505421080081c08180a940d1c0b300
[     3.081] (II) modeset(0):   90409500a9c064190040410026301888
[     3.081] (II) modeset(0):   360000c010000018662156aa51001e30
[     3.081] (II) modeset(0):   468f330055c01000001e000000fc0044
[     3.081] (II) modeset(0):   503256474120563232360a20302a0008
[     3.081] (II) modeset(0):   52c028306070130040f01000001e00e8
[     3.081] (II) modeset(0): Printing probed modes for output DP-2
[     3.081] (II) modeset(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz eP)
[     3.081] (II) modeset(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 -hsync -vsync (67.5 kHz e)
[     3.081] (II) modeset(0): Modeline "1600x1200"x60.0  162.00  1600 1664 1856 2160  1200 1201 1204 1250 +hsync +vsync (75.0 kHz e)
[     3.081] (II) modeset(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[     3.081] (II) modeset(0): Modeline "1400x1050"x60.0  121.75  1400 1488 1632 1864  1050 1053 1057 1089 -hsync +vsync (65.3 kHz e)
[     3.081] (II) modeset(0): Modeline "1600x900"x60.0  108.00  1600 1624 1704 1800  900 901 904 1000 +hsync +vsync (60.0 kHz e)
[     3.081] (II) modeset(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[     3.081] (II) modeset(0): Modeline "1440x900"x59.9  106.50  1440 1520 1672 1904  900 903 909 934 -hsync +vsync (55.9 kHz e)
[     3.081] (II) modeset(0): Modeline "1280x960"x60.0  108.00  1280 1376 1488 1800  960 961 964 1000 +hsync +vsync (60.0 kHz e)
[     3.081] (II) modeset(0): Modeline "1366x768"x59.8   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
[     3.081] (II) modeset(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[     3.081] (II) modeset(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[     3.081] (II) modeset(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[     3.090] (II) modeset(0): EDID for output HDMI-3
[     3.090] (II) modeset(0): Output DP-1 disconnected
[     3.090] (II) modeset(0): Output HDMI-1 disconnected
[     3.090] (II) modeset(0): Output HDMI-2 disconnected
[     3.090] (II) modeset(0): Output DP-2 connected
[     3.090] (II) modeset(0): Output HDMI-3 disconnected
[     3.090] (II) modeset(0): Using exact sizes for initial modes
[     3.090] (II) modeset(0): Output DP-2 using initial mode 1024x768 +0+0
[     3.090] (==) modeset(0): Using gamma correction (1.0, 1.0, 1.0)
[     3.090] (==) modeset(0): DPI set to (96, 96)
[     3.090] (II) Loading sub module "fb"
[     3.090] (II) LoadModule: "fb"
[     3.090] (II) Loading /usr/lib/xorg/modules/libfb.so
[     3.090] (II) Module fb: vendor="X.Org Foundation"
[     3.090]    compiled for 1.19.5, module version = 1.0.0
[     3.090]    ABI class: X.Org ANSI C Emulation, version 0.4
[     3.090] (II) UnloadModule: "fbdev"
[     3.090] (II) Unloading fbdev
[     3.090] (II) UnloadSubModule: "fbdevhw"
[     3.090] (II) Unloading fbdevhw
[     3.090] (II) UnloadModule: "vesa"
[     3.090] (II) Unloading vesa
[     3.090] (==) Depth 24 pixmap format is 32 bpp
[     3.131] (==) modeset(0): Backing store enabled
[     3.131] (==) modeset(0): Silken mouse enabled
[     3.131] (II) modeset(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[     3.175] (==) modeset(0): DPMS enabled
[     3.175] (II) modeset(0): [DRI2] Setup complete
[     3.175] (II) modeset(0): [DRI2]   DRI driver: i965
[     3.175] (II) modeset(0): [DRI2]   VDPAU driver: i965
[     3.175] (--) RandR disabled
[     3.178] (II) SELinux: Disabled on system
[     3.181] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[     3.181] (II) AIGLX: enabled GLX_ARB_create_context
[     3.181] (II) AIGLX: enabled GLX_ARB_create_context_profile
[     3.181] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[     3.181] (II) AIGLX: enabled GLX_INTEL_swap_event
[     3.181] (II) AIGLX: enabled GLX_SGI_swap_control
[     3.181] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[     3.181] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[     3.181] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[     3.181] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[     3.181] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[     3.181] (II) AIGLX: Loaded and initialized i965
[     3.181] (II) GLX: Initialized DRI2 GL provider for screen 0
[     3.183] (II) modeset(0): Damage tracking initialized
[     3.183] (II) modeset(0): Setting screen physical size to 270 x 203
[     3.202] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[     3.202] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     3.202] (II) LoadModule: "libinput"
[     3.202] (II) Loading /usr/lib/xorg/modules/input/libinput_drv.so
[     3.204] (II) Module libinput: vendor="X.Org Foundation"
[     3.204]    compiled for 1.19.3, module version = 0.25.0
[     3.204]    Module class: X.Org XInput Driver
[     3.204]    ABI class: X.Org XInput driver, version 24.1
[     3.204] (II) Using input driver 'libinput' for 'Power Button'
[     3.204] (**) Power Button: always reports core events
[     3.204] (**) Option "Device" "/dev/input/event2"
[     3.204] (**) Option "_source" "server/udev"
[     3.204] (II) event2  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     3.204] (II) event2  - (II) Power Button: (II) device is a keyboard
[     3.204] (II) event2  - (II) Power Button: (II) device removed
[     3.224] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[     3.224] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[     3.224] (**) Option "xkb_model" "pc105"
[     3.224] (**) Option "xkb_layout" "us"
[     3.224] (II) event2  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     3.224] (II) event2  - (II) Power Button: (II) device is a keyboard
[     3.224] (II) config/udev: Adding input device Video Bus (/dev/input/event3)
[     3.224] (**) Video Bus: Applying InputClass "libinput keyboard catchall"
[     3.224] (II) Using input driver 'libinput' for 'Video Bus'
[     3.224] (**) Video Bus: always reports core events
[     3.224] (**) Option "Device" "/dev/input/event3"
[     3.224] (**) Option "_source" "server/udev"
[     3.224] (II) event3  - (II) Video Bus: (II) is tagged by udev as: Keyboard
[     3.224] (II) event3  - (II) Video Bus: (II) device is a keyboard
[     3.224] (II) event3  - (II) Video Bus: (II) device removed
[     3.244] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input3/event3"
[     3.244] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[     3.244] (**) Option "xkb_model" "pc105"
[     3.244] (**) Option "xkb_layout" "us"
[     3.244] (II) event3  - (II) Video Bus: (II) is tagged by udev as: Keyboard
[     3.244] (II) event3  - (II) Video Bus: (II) device is a keyboard
[     3.244] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[     3.244] (**) Power Button: Applying InputClass "libinput keyboard catchall"
[     3.244] (II) Using input driver 'libinput' for 'Power Button'
[     3.244] (**) Power Button: always reports core events
[     3.244] (**) Option "Device" "/dev/input/event1"
[     3.244] (**) Option "_source" "server/udev"
[     3.244] (II) event1  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     3.244] (II) event1  - (II) Power Button: (II) device is a keyboard
[     3.244] (II) event1  - (II) Power Button: (II) device removed
[     3.260] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1/event1"
[     3.260] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[     3.260] (**) Option "xkb_model" "pc105"
[     3.260] (**) Option "xkb_layout" "us"
[     3.260] (II) event1  - (II) Power Button: (II) is tagged by udev as: Keyboard
[     3.260] (II) event1  - (II) Power Button: (II) device is a keyboard
[     3.260] (II) config/udev: Adding input device Sleep Button (/dev/input/event0)
[     3.260] (**) Sleep Button: Applying InputClass "libinput keyboard catchall"
[     3.260] (II) Using input driver 'libinput' for 'Sleep Button'
[     3.260] (**) Sleep Button: always reports core events
[     3.260] (**) Option "Device" "/dev/input/event0"
[     3.260] (**) Option "_source" "server/udev"
[     3.260] (II) event0  - (II) Sleep Button: (II) is tagged by udev as: Keyboard
[     3.260] (II) event0  - (II) Sleep Button: (II) device is a keyboard
[     3.260] (II) event0  - (II) Sleep Button: (II) device removed
[     3.276] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input0/event0"
[     3.276] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[     3.276] (**) Option "xkb_model" "pc105"
[     3.276] (**) Option "xkb_layout" "us"
[     3.276] (II) event0  - (II) Sleep Button: (II) is tagged by udev as: Keyboard
[     3.276] (II) event0  - (II) Sleep Button: (II) device is a keyboard
[     3.276] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event10)
[     3.276] (II) No input driver specified, ignoring this device.
[     3.276] (II) This device may have been added with another device file.
[     3.276] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event11)
[     3.276] (II) No input driver specified, ignoring this device.
[     3.276] (II) This device may have been added with another device file.
[     3.276] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event12)
[     3.276] (II) No input driver specified, ignoring this device.
[     3.276] (II) This device may have been added with another device file.
[     3.276] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=7 (/dev/input/event13)
[     3.276] (II) No input driver specified, ignoring this device.
[     3.276] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=8 (/dev/input/event14)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=9 (/dev/input/event15)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=10 (/dev/input/event16)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event4)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event5)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event6)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event7)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.277] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event8)
[     3.277] (II) No input driver specified, ignoring this device.
[     3.277] (II) This device may have been added with another device file.
[     3.278] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event9)
[     3.278] (II) No input driver specified, ignoring this device.
[     3.278] (II) This device may have been added with another device file.
```

---

### Post by Yellow Pasque on 2018-04-10
Thanks for that (and using code tags)
Strangely enough, everything looks good there. The next place I would look at is:
```
LIBGL_DEBUG=verbose glxinfo
dmesg | grep -i i915
```

---

### Post by tomaszmur on 2018-04-10
> **Temüjin said:**
> Thanks for that (and using code tags)
Strangely enough, everything looks good there. The next place I would look at is:
```
LIBGL_DEBUG=verbose glxinfo
dmesg | grep -i i915
```

Thanks for advice. I'm quite new to this forum and ubuntu itself

here are the outputs:

```

$ LIBGL_DEBUG=verbose glxinfo
name of display: :10.0
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/tls/swrast_dri.so
libGL: OpenDriver: trying /usr/lib/x86_64-linux-gnu/dri/swrast_dri.so
libGL: Can't open configuration file /home/tomasz/.drirc: No such file or directory.
libGL: Can't open configuration file /home/tomasz/.drirc: No such file or directory.
display: :10  screen: 0
direct rendering: Yes
server glx vendor string: SGI
server glx version string: 1.4
server glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB, GLX_ARB_multisample,
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB,
    GLX_EXT_import_context, GLX_EXT_libglvnd, GLX_EXT_texture_from_pixmap,
    GLX_EXT_visual_info, GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_make_current_read
client glx vendor string: Mesa Project and SGI
client glx version string: 1.4
client glx extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_ARB_create_context_robustness, GLX_ARB_fbconfig_float,
    GLX_ARB_framebuffer_sRGB, GLX_ARB_get_proc_address, GLX_ARB_multisample,
    GLX_EXT_buffer_age, GLX_EXT_create_context_es2_profile,
    GLX_EXT_create_context_es_profile, GLX_EXT_fbconfig_packed_float,
    GLX_EXT_framebuffer_sRGB, GLX_EXT_import_context,
    GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info, GLX_EXT_visual_rating,
    GLX_INTEL_swap_event, GLX_MESA_copy_sub_buffer,
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
    GLX_MESA_swap_control, GLX_OML_swap_method, GLX_OML_sync_control,
    GLX_SGIS_multisample, GLX_SGIX_fbconfig, GLX_SGIX_pbuffer,
    GLX_SGIX_visual_select_group, GLX_SGI_make_current_read,
    GLX_SGI_swap_control, GLX_SGI_video_sync
GLX version: 1.4
GLX extensions:
    GLX_ARB_create_context, GLX_ARB_create_context_profile,
    GLX_ARB_fbconfig_float, GLX_ARB_framebuffer_sRGB,
    GLX_ARB_get_proc_address, GLX_ARB_multisample,
    GLX_EXT_create_context_es2_profile, GLX_EXT_create_context_es_profile,
    GLX_EXT_fbconfig_packed_float, GLX_EXT_framebuffer_sRGB,
    GLX_EXT_import_context, GLX_EXT_texture_from_pixmap, GLX_EXT_visual_info,
    GLX_EXT_visual_rating, GLX_MESA_copy_sub_buffer,
    GLX_MESA_multithread_makecurrent, GLX_MESA_query_renderer,
    GLX_OML_swap_method, GLX_SGIS_multisample, GLX_SGIX_fbconfig,
    GLX_SGIX_pbuffer, GLX_SGIX_visual_select_group, GLX_SGI_make_current_read
Extended renderer info (GLX_MESA_query_renderer):
    Vendor: VMware, Inc. (0xffffffff)
    Device: llvmpipe (LLVM 5.0, 256 bits) (0xffffffff)
    Version: 17.2.8
    Accelerated: no
    Video memory: 15926MB
    Unified memory: no
    Preferred profile: core (0x1)
    Max core profile version: 3.3
    Max compat profile version: 3.0
    Max GLES1 profile version: 1.1
    Max GLES[23] profile version: 3.0
OpenGL vendor string: VMware, Inc.
OpenGL renderer string: llvmpipe (LLVM 5.0, 256 bits)
OpenGL core profile version string: 3.3 (Core Profile) Mesa 17.2.8
OpenGL core profile shading language version string: 3.30
OpenGL core profile context flags: (none)
OpenGL core profile profile mask: core profile
OpenGL core profile extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend,
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export,
    GL_AMD_shader_trinary_minmax, GL_AMD_vertex_shader_layer,
    GL_AMD_vertex_shader_viewport_index, GL_ARB_ES2_compatibility,
    GL_ARB_ES3_compatibility, GL_ARB_arrays_of_arrays, GL_ARB_base_instance,
    GL_ARB_blend_func_extended, GL_ARB_buffer_storage,
    GL_ARB_clear_buffer_object, GL_ARB_clear_texture, GL_ARB_clip_control,
    GL_ARB_compressed_texture_pixel_storage,
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth,
    GL_ARB_copy_buffer, GL_ARB_copy_image, GL_ARB_cull_distance,
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp,
    GL_ARB_direct_state_access, GL_ARB_draw_buffers,
    GL_ARB_draw_buffers_blend, GL_ARB_draw_elements_base_vertex,
    GL_ARB_draw_indirect, GL_ARB_draw_instanced, GL_ARB_enhanced_layouts,
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location,
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_layer_viewport,
    GL_ARB_fragment_shader, GL_ARB_framebuffer_object,
    GL_ARB_framebuffer_sRGB, GL_ARB_get_program_binary,
    GL_ARB_get_texture_sub_image, GL_ARB_gpu_shader_fp64,
    GL_ARB_gpu_shader_int64, GL_ARB_half_float_pixel,
    GL_ARB_half_float_vertex, GL_ARB_instanced_arrays,
    GL_ARB_internalformat_query, GL_ARB_internalformat_query2,
    GL_ARB_invalidate_subdata, GL_ARB_map_buffer_alignment,
    GL_ARB_map_buffer_range, GL_ARB_multi_bind, GL_ARB_multi_draw_indirect,
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object, GL_ARB_point_sprite,
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex,
    GL_ARB_robustness, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map,
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects,
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects,
    GL_ARB_shader_stencil_export, GL_ARB_shader_subroutine,
    GL_ARB_shader_texture_lod, GL_ARB_shading_language_420pack,
    GL_ARB_shading_language_packing, GL_ARB_stencil_texturing, GL_ARB_sync,
    GL_ARB_texture_buffer_object, GL_ARB_texture_buffer_object_rgb32,
    GL_ARB_texture_buffer_range, GL_ARB_texture_compression_rgtc,
    GL_ARB_texture_cube_map_array, GL_ARB_texture_float,
    GL_ARB_texture_gather, GL_ARB_texture_mirror_clamp_to_edge,
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_query_levels, GL_ARB_texture_rectangle, GL_ARB_texture_rg,
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_stencil8,
    GL_ARB_texture_storage, GL_ARB_texture_storage_multisample,
    GL_ARB_texture_swizzle, GL_ARB_texture_view, GL_ARB_timer_query,
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3,
    GL_ARB_transform_feedback_instanced, GL_ARB_uniform_buffer_object,
    GL_ARB_vertex_array_bgra, GL_ARB_vertex_array_object,
    GL_ARB_vertex_attrib_64bit, GL_ARB_vertex_attrib_binding,
    GL_ARB_vertex_shader, GL_ARB_vertex_type_10f_11f_11f_rev,
    GL_ARB_vertex_type_2_10_10_10_rev, GL_ARB_viewport_array,
    GL_ATI_blend_equation_separate, GL_ATI_texture_float,
    GL_ATI_texture_mirror_once, GL_EXT_abgr, GL_EXT_blend_equation_separate,
    GL_EXT_draw_buffers2, GL_EXT_draw_instanced, GL_EXT_framebuffer_blit,
    GL_EXT_framebuffer_multisample, GL_EXT_framebuffer_multisample_blit_scaled,
    GL_EXT_framebuffer_sRGB, GL_EXT_packed_depth_stencil, GL_EXT_packed_float,
    GL_EXT_pixel_buffer_object, GL_EXT_polygon_offset_clamp,
    GL_EXT_provoking_vertex, GL_EXT_shader_integer_mix, GL_EXT_texture_array,
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_integer,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_sRGB,
    GL_EXT_texture_sRGB_decode, GL_EXT_texture_shared_exponent,
    GL_EXT_texture_snorm, GL_EXT_texture_swizzle, GL_EXT_timer_query,
    GL_EXT_transform_feedback, GL_EXT_vertex_array_bgra,
    GL_IBM_multimode_draw_arrays, GL_KHR_context_flush_control, GL_KHR_debug,
    GL_KHR_no_error, GL_MESA_pack_invert, GL_MESA_shader_integer_functions,
    GL_MESA_texture_signed_rgba, GL_MESA_ycbcr_texture,
    GL_NV_conditional_render, GL_NV_depth_clamp, GL_NV_packed_depth_stencil,
    GL_OES_EGL_image

OpenGL version string: 3.0 Mesa 17.2.8
OpenGL shading language version string: 1.30
OpenGL context flags: (none)
OpenGL extensions:
    GL_AMD_conservative_depth, GL_AMD_draw_buffers_blend,
    GL_AMD_seamless_cubemap_per_texture, GL_AMD_shader_stencil_export,
    GL_AMD_shader_trinary_minmax, GL_APPLE_packed_pixels,
    GL_ARB_ES2_compatibility, GL_ARB_ES3_compatibility,
    GL_ARB_arrays_of_arrays, GL_ARB_base_instance, GL_ARB_blend_func_extended,
    GL_ARB_buffer_storage, GL_ARB_clear_buffer_object, GL_ARB_clear_texture,
    GL_ARB_clip_control, GL_ARB_color_buffer_float,
    GL_ARB_compressed_texture_pixel_storage,
    GL_ARB_conditional_render_inverted, GL_ARB_conservative_depth,
    GL_ARB_copy_buffer, GL_ARB_copy_image, GL_ARB_cull_distance,
    GL_ARB_debug_output, GL_ARB_depth_buffer_float, GL_ARB_depth_clamp,
    GL_ARB_depth_texture, GL_ARB_draw_buffers, GL_ARB_draw_buffers_blend,
    GL_ARB_draw_elements_base_vertex, GL_ARB_draw_instanced,
    GL_ARB_explicit_attrib_location, GL_ARB_explicit_uniform_location,
    GL_ARB_fragment_coord_conventions, GL_ARB_fragment_program,
    GL_ARB_fragment_program_shadow, GL_ARB_fragment_shader,
    GL_ARB_framebuffer_object, GL_ARB_framebuffer_sRGB,
    GL_ARB_get_program_binary, GL_ARB_get_texture_sub_image,
    GL_ARB_half_float_pixel, GL_ARB_half_float_vertex,
    GL_ARB_instanced_arrays, GL_ARB_internalformat_query,
    GL_ARB_internalformat_query2, GL_ARB_invalidate_subdata,
    GL_ARB_map_buffer_alignment, GL_ARB_map_buffer_range, GL_ARB_multi_bind,
    GL_ARB_multisample, GL_ARB_multitexture, GL_ARB_occlusion_query,
    GL_ARB_occlusion_query2, GL_ARB_pixel_buffer_object,
    GL_ARB_point_parameters, GL_ARB_point_sprite,
    GL_ARB_program_interface_query, GL_ARB_provoking_vertex,
    GL_ARB_robustness, GL_ARB_sampler_objects, GL_ARB_seamless_cube_map,
    GL_ARB_seamless_cubemap_per_texture, GL_ARB_separate_shader_objects,
    GL_ARB_shader_bit_encoding, GL_ARB_shader_objects,
    GL_ARB_shader_stencil_export, GL_ARB_shader_texture_lod,
    GL_ARB_shading_language_100, GL_ARB_shading_language_420pack,
    GL_ARB_shading_language_packing, GL_ARB_shadow, GL_ARB_stencil_texturing,
    GL_ARB_sync, GL_ARB_texture_border_clamp, GL_ARB_texture_compression,
    GL_ARB_texture_compression_rgtc, GL_ARB_texture_cube_map,
    GL_ARB_texture_cube_map_array, GL_ARB_texture_env_add,
    GL_ARB_texture_env_combine, GL_ARB_texture_env_crossbar,
    GL_ARB_texture_env_dot3, GL_ARB_texture_float, GL_ARB_texture_gather,
    GL_ARB_texture_mirror_clamp_to_edge, GL_ARB_texture_mirrored_repeat,
    GL_ARB_texture_multisample, GL_ARB_texture_non_power_of_two,
    GL_ARB_texture_query_levels, GL_ARB_texture_rectangle, GL_ARB_texture_rg,
    GL_ARB_texture_rgb10_a2ui, GL_ARB_texture_stencil8,
    GL_ARB_texture_storage, GL_ARB_texture_storage_multisample,
    GL_ARB_texture_swizzle, GL_ARB_texture_view, GL_ARB_timer_query,
    GL_ARB_transform_feedback2, GL_ARB_transform_feedback3,
    GL_ARB_transform_feedback_instanced, GL_ARB_transpose_matrix,
    GL_ARB_uniform_buffer_object, GL_ARB_vertex_array_bgra,
    GL_ARB_vertex_array_object, GL_ARB_vertex_attrib_binding,
    GL_ARB_vertex_buffer_object, GL_ARB_vertex_program, GL_ARB_vertex_shader,
    GL_ARB_vertex_type_10f_11f_11f_rev, GL_ARB_vertex_type_2_10_10_10_rev,
    GL_ARB_window_pos, GL_ATI_blend_equation_separate, GL_ATI_draw_buffers,
    GL_ATI_fragment_shader, GL_ATI_separate_stencil,
    GL_ATI_texture_compression_3dc, GL_ATI_texture_env_combine3,
    GL_ATI_texture_float, GL_ATI_texture_mirror_once, GL_EXT_abgr,
    GL_EXT_bgra, GL_EXT_blend_color, GL_EXT_blend_equation_separate,
    GL_EXT_blend_func_separate, GL_EXT_blend_minmax, GL_EXT_blend_subtract,
    GL_EXT_compiled_vertex_array, GL_EXT_copy_texture, GL_EXT_draw_buffers2,
    GL_EXT_draw_instanced, GL_EXT_draw_range_elements, GL_EXT_fog_coord,
    GL_EXT_framebuffer_blit, GL_EXT_framebuffer_multisample,
    GL_EXT_framebuffer_multisample_blit_scaled, GL_EXT_framebuffer_object,
    GL_EXT_framebuffer_sRGB, GL_EXT_gpu_program_parameters,
    GL_EXT_multi_draw_arrays, GL_EXT_packed_depth_stencil,
    GL_EXT_packed_float, GL_EXT_packed_pixels, GL_EXT_pixel_buffer_object,
    GL_EXT_point_parameters, GL_EXT_polygon_offset,
    GL_EXT_polygon_offset_clamp, GL_EXT_provoking_vertex,
    GL_EXT_rescale_normal, GL_EXT_secondary_color,
    GL_EXT_separate_specular_color, GL_EXT_shader_integer_mix,
    GL_EXT_shadow_funcs, GL_EXT_stencil_two_side, GL_EXT_stencil_wrap,
    GL_EXT_subtexture, GL_EXT_texture, GL_EXT_texture3D,
    GL_EXT_texture_array, GL_EXT_texture_compression_latc,
    GL_EXT_texture_compression_rgtc, GL_EXT_texture_cube_map,
    GL_EXT_texture_edge_clamp, GL_EXT_texture_env_add,
    GL_EXT_texture_env_combine, GL_EXT_texture_env_dot3,
    GL_EXT_texture_integer, GL_EXT_texture_lod_bias,
    GL_EXT_texture_mirror_clamp, GL_EXT_texture_object,
    GL_EXT_texture_rectangle, GL_EXT_texture_sRGB, GL_EXT_texture_sRGB_decode,
    GL_EXT_texture_shared_exponent, GL_EXT_texture_snorm,
    GL_EXT_texture_swizzle, GL_EXT_timer_query, GL_EXT_transform_feedback,
    GL_EXT_vertex_array, GL_EXT_vertex_array_bgra,
    GL_IBM_multimode_draw_arrays, GL_IBM_rasterpos_clip,
    GL_IBM_texture_mirrored_repeat, GL_INGR_blend_func_separate,
    GL_KHR_context_flush_control, GL_KHR_debug, GL_KHR_no_error,
    GL_MESA_pack_invert, GL_MESA_shader_integer_functions,
    GL_MESA_texture_signed_rgba, GL_MESA_window_pos, GL_MESA_ycbcr_texture,
    GL_NV_blend_square, GL_NV_conditional_render, GL_NV_depth_clamp,
    GL_NV_fog_distance, GL_NV_light_max_exponent, GL_NV_packed_depth_stencil,
    GL_NV_primitive_restart, GL_NV_texgen_reflection,
    GL_NV_texture_env_combine4, GL_NV_texture_rectangle, GL_OES_EGL_image,
    GL_OES_read_format, GL_SGIS_generate_mipmap, GL_SGIS_texture_border_clamp,
    GL_SGIS_texture_edge_clamp, GL_SGIS_texture_lod, GL_SUN_multi_draw_arrays

OpenGL ES profile version string: OpenGL ES 3.0 Mesa 17.2.8
OpenGL ES profile shading language version string: OpenGL ES GLSL ES 3.00
OpenGL ES profile extensions:
    GL_APPLE_texture_max_level, GL_EXT_base_instance,
    GL_EXT_blend_func_extended, GL_EXT_blend_minmax,
    GL_EXT_clip_cull_distance, GL_EXT_color_buffer_float,
    GL_EXT_compressed_ETC1_RGB8_sub_texture, GL_EXT_copy_image,
    GL_EXT_discard_framebuffer, GL_EXT_draw_buffers,
    GL_EXT_draw_buffers_indexed, GL_EXT_draw_elements_base_vertex,
    GL_EXT_frag_depth, GL_EXT_map_buffer_range, GL_EXT_multi_draw_arrays,
    GL_EXT_polygon_offset_clamp, GL_EXT_read_format_bgra,
    GL_EXT_separate_shader_objects, GL_EXT_shader_integer_mix,
    GL_EXT_texture_border_clamp, GL_EXT_texture_format_BGRA8888,
    GL_EXT_texture_rg, GL_EXT_texture_sRGB_decode,
    GL_EXT_texture_type_2_10_10_10_REV, GL_EXT_unpack_subimage,
    GL_KHR_context_flush_control, GL_KHR_debug, GL_KHR_no_error,
    GL_MESA_shader_integer_functions, GL_NV_draw_buffers,
    GL_NV_fbo_color_attachments, GL_NV_read_buffer, GL_NV_read_depth,
    GL_NV_read_depth_stencil, GL_NV_read_stencil, GL_OES_EGL_image,
    GL_OES_EGL_image_external, GL_OES_EGL_sync,
    GL_OES_compressed_ETC1_RGB8_texture, GL_OES_copy_image, GL_OES_depth24,
    GL_OES_depth_texture, GL_OES_depth_texture_cube_map,
    GL_OES_draw_buffers_indexed, GL_OES_draw_elements_base_vertex,
    GL_OES_element_index_uint, GL_OES_fbo_render_mipmap,
    GL_OES_get_program_binary, GL_OES_mapbuffer, GL_OES_packed_depth_stencil,
    GL_OES_rgb8_rgba8, GL_OES_standard_derivatives, GL_OES_stencil8,
    GL_OES_surfaceless_context, GL_OES_texture_3D,
    GL_OES_texture_border_clamp, GL_OES_texture_float,
    GL_OES_texture_float_linear, GL_OES_texture_half_float,
    GL_OES_texture_half_float_linear, GL_OES_texture_npot,
    GL_OES_texture_stencil8, GL_OES_vertex_array_object,
    GL_OES_vertex_half_float

3 GLX Visuals
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat
----------------------------------------------------------------------------
0x04e 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x021 32 tc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None
0x022 32 dc  0  32  0 r  y .   8  8  8  8 .  .  0 24  8  0  0  0  0  0 0 None

300 GLXFBConfigs:
    visual  x   bf lv rg d st  colorbuffer  sr ax dp st accumbuffer  ms  cav
  id dep cl sp  sz l  ci b ro  r  g  b  a F gb bf th cl  r  g  b  a ns b eat



```

```

$ dmesg | grep -i i915
[    0.000000] Command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-38-generic root=UUID=a4c2d4b0-3ddd-41ac-9801-4c5c50ade033 ro quiet splash i915.alpha_support=1 vt.handoff=7
[    0.000000] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.13.0-38-generic root=UUID=a4c2d4b0-3ddd-41ac-9801-4c5c50ade033 ro quiet splash i915.alpha_support=1 vt.handoff=7
[    1.161887] WARNING: CPU: 2 PID: 216 at /build/linux-cg_do7/linux-4.13.0/drivers/gpu/drm/i915/i915_drv.c:230 i915_driver_load+0x11da/0x14c0 [i915]
[    1.161887] Modules linked in: mxm_wmi i915(+) i2c_algo_bit drm_kms_helper syscopyarea sysfillrect sysimgblt fb_sys_fops r8169 ahci drm mii libahci wmi video i2c_hid hid
[    1.161908] RIP: 0010:i915_driver_load+0x11da/0x14c0 [i915]
[    1.161933]  i915_pci_probe+0x42/0x70 [i915]
[    1.161965]  i915_init+0x57/0x5a [i915]
[    1.175362] [drm] Finished loading DMC firmware i915/kbl_dmc_ver1_01.bin (v1.1)
[    1.175731] i915 0000:00:02.0: vgaarb: changed VGA decodes: olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.449817] [drm] Initialized i915 1.6.0 20170619 for 0000:00:02.0 on minor 0
[    1.509722] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.148037] snd_hda_intel 0000:00:1f.3: bound 0000:00:02.0 (ops i915_audio_component_bind_ops [i915])



```

Any ideas what I can do to ger 3D graphics acceleration enabled? To me it looks like it doesnt really use the CPU integrated graphics for some reason...

---

### Post by Yellow Pasque on 2018-04-10
I will admit I'm stumped. I would try a Lubuntu 18.04 USB stick and look at glxinfo there.

---

