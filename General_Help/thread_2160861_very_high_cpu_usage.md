---
title: "very high cpu usage"
date: 2013-07-08
forum: General Help
---

### Post by angstrom79 on 2013-07-08
I facing cpu usage issues (up to 99%) under 12.04 with no user tasks whatsoever. So this causes weird behavior like update problems and all the performance related issues u can imagine... I'm kind of a noob but I believe atd is the culprit. At least that what top says...


The laptop is a samsung np350v5c-s07pt
Intel® Core&#8482; i5-3210M (2,50 GHz) , 3 MB Cache (3,1 Ghz Turbo Boost)
Intel® HM76
Intel hd 4000 + AMD Radeon&#8482; HD7670M 1 GB gDDR3
6 GB (1 x 4 GB + 1 x 2 GB) DDR3 1 600 MHz 2 x SODIMM
So it installed with no issues having 4% 5% cpu usage.


Then some update went wrong and I couldn't boot 4 out of 5 times, so I enabled unity 2d and managed to login again with no issues and updated and all went fine, then I installed gnome 3 just in case something would go wrong again. And then noticed I was having 99% cpu usage all the time and conky wasn't starting (I'm running a delay conky script in the startup).

I already went through the steps of 

[https://wiki.ubuntu.com/X/Troubleshooting/HighCPU](https://wiki.ubuntu.com/X/Troubleshooting/HighCPU)

to no avail...

worth mentioning that I could not go through step 2 it  wont let me install the packages needed to run glxinfo. 
 
So this is the story...

And these are the logs 


**top**

```


top - 17:27:46 up 6 min,  2 users,  load average: 9.52, 7.65, 3.66
Tasks: 211 total,   5 running, 205 sleeping,   1 stopped,   0 zombie
Cpu(s): 23.5%us, 71.8%sy,  0.0%ni,  4.5%id,  0.1%wa,  0.0%hi,  0.1%si,  0.0%st
Mem:   6002968k total,  2360864k used,  3642104k free,    73128k buffers
Swap:  6348796k total,        0k used,  6348796k free,   892124k cached


  PID USER      PR  NI  VIRT  RES  SHR S %CPU %MEM    TIME+  COMMAND                                                                                   
 1172 daemon    20   0 16908  548  380 R   94  0.0   5:24.98 atd                                                                                       
  959 syslog    20   0  244m 6212 1132 S   24  0.1   1:22.01 rsyslogd                                                                                  
 7593 root      20   0  349m 119m  99m S    4  2.0   0:17.24 Xorg                                                                                      
   10 root      20   0     0    0    0 S    1  0.0   0:04.48 ksoftirqd/1                                                                               
   14 root      20   0     0    0    0 S    1  0.0   0:04.57 ksoftirqd/2                                                                               
17657 hugo      20   0 1184m  73m  33m S    1  1.3   0:04.38 unity-2d-shell                                                                            
    3 root      20   0     0    0    0 S    1  0.0   0:04.34 ksoftirqd/0                                                                               
   18 root      20   0     0    0    0 S    1  0.0   0:04.59 ksoftirqd/3                                                                               
 3069 hugo      20   0  577m  27m  11m S    1  0.5   0:02.08 gnome-terminal                                                                            
   32 root      20   0     0    0    0 S    0  0.0   0:00.39 kworker/0:1                                                                               
  239 root      20   0     0    0    0 S    0  0.0   0:00.58 kworker/u:4                                                                               
  779 root      20   0     0    0    0 S    0  0.0   0:00.99 rts5139-polling                                                                           
  870 root      20   0     0    0    0 S    0  0.0   0:00.46 kworker/3:2                                                                               
13846 hugo      20   0 17456 1388  952 R    0  0.0   0:00.21 top                                                                                       
27606 hugo      20   0 27828 3500  624 S    0  0.1   0:01.37 dbus-daemon                                                                               
    1 root      20   0 24672 2640 1368 S    0  0.0   0:00.55 init                                                                                      
    2 root      20   0     0    0    0 S    0  0.0   0:00.00 kthreadd                                                                                  
    6 root      RT   0     0    0    0 S    0  0.0   0:00.05 migration/0                                                                               
    7 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/0                                                                                
    8 root      RT   0     0    0    0 S    0  0.0   0:00.18 migration/1                                                                               
    9 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/1:0                                                                               
   11 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/1                                                                                
   12 root      RT   0     0    0    0 S    0  0.0   0:00.00 migration/2                                                                               
   13 root      20   0     0    0    0 S    0  0.0   0:00.00 kworker/2:0                                                                               
   15 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/2                                                                                
   16 root      RT   0     0    0    0 S    0  0.0   0:00.21 migration/3                                                                               
   19 root      RT   0     0    0    0 S    0  0.0   0:00.00 watchdog/3                                                                                
   20 root       0 -20     0    0    0 S    0  0.0   0:00.00 cpuset                                                                                    
   21 root       0 -20     0    0    0 S    0  0.0   0:00.00 khelper                                                                                   
   22 root      20   0     0    0    0 S    0  0.0   0:00.00 kdevtmpfs                                                                                 
   23 root       0 -20     0    0    0 S    0  0.0   0:00.00 netns                                                                                     
   25 root      20   0     0    0    0 S    0  0.0   0:00.00 sync_supers                                                                               
   26 root      20   0     0    0    0 S    0  0.0   0:00.00 bdi-default                                                                               
   27 root       0 -20     0    0    0 S    0  0.0   0:00.00 kintegrityd  p



```


**Xorg.0.log**

```


[    20.632] 
X.Org X Server 1.13.0
Release Date: 2012-09-05
[    20.632] X Protocol Version 11, Revision 0
[    20.632] Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
[    20.632] Current Operating System: Linux hugo-pc 3.5.0-36-generic #57~precise1-Ubuntu SMP Thu Jun 20 18:21:09 UTC 2013 x86_64
[    20.632] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-36-generic root=UUID=8da36b11-e30d-4d90-8636-32b95509e861 ro quiet splash vt.handoff=7
[    20.632] Build Date: 11 April 2013  11:49:23PM
[    20.632] xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see http://www.ubuntu.com/support) 
[    20.632] Current version of pixman: 0.24.4
[    20.633]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    20.633] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    20.633] (==) Log file: "/var/log/Xorg.0.log", Time: Sun Jul  7 08:21:49 2013
[    20.699] (==) Using config file: "/etc/X11/xorg.conf"
[    20.699] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    20.819] (==) ServerLayout "aticonfig Layout"
[    20.819] (**) |-->Screen "aticonfig-Screen[0]-0" (0)
[    20.819] (**) |   |-->Monitor "aticonfig-Monitor[0]-0"
[    20.901] (**) |   |-->Device "aticonfig-Device[0]-0"
[    20.901] (==) Automatically adding devices
[    20.901] (==) Automatically enabling devices
[    20.901] (==) Automatically adding GPU devices
[    20.982] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    20.982]     Entry deleted from font path.
[    20.982] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    20.982]     Entry deleted from font path.
[    20.982] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    20.982]     Entry deleted from font path.
[    20.983] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    20.983]     Entry deleted from font path.
[    20.983] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    20.983]     Entry deleted from font path.
[    20.983] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    20.983]     Entry deleted from font path.
[    20.983] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    20.983] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    20.983] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    20.985] (II) Loader magic: 0x7f2ea4149c20
[    20.985] (II) Module ABI versions:
[    20.985]     X.Org ANSI C Emulation: 0.4
[    20.985]     X.Org Video Driver: 13.0
[    20.985]     X.Org XInput driver : 18.0
[    20.985]     X.Org Server Extension : 7.0
[    20.985] (II) config/udev: Adding drm device (/dev/dri/card0)
[    20.986] (--) PCI:*(0:0:2:0) 8086:0166:144d:c0d8 rev 9, Mem @ 0xbfc00000/4194304, 0xd0000000/268435456, I/O @ 0x00004000/64
[    20.986] (--) PCI: (0:1:0:0) 1002:6840:144d:c0d8 rev 0, Mem @ 0xe0000000/268435456, 0xc0220000/131072, I/O @ 0x00003000/256, BIOS @ 0x????????/131072
[    20.986] (II) Open ACPI successful (/var/run/acpid.socket)
[    20.988] Initializing built-in extension Generic Event Extension
[    20.988] Initializing built-in extension SHAPE
[    20.988] Initializing built-in extension MIT-SHM
[    20.988] Initializing built-in extension XInputExtension
[    20.988] Initializing built-in extension XTEST
[    20.988] Initializing built-in extension BIG-REQUESTS
[    20.988] Initializing built-in extension SYNC
[    20.988] Initializing built-in extension XKEYBOARD
[    20.988] Initializing built-in extension XC-MISC
[    20.988] Initializing built-in extension SECURITY
[    20.988] Initializing built-in extension XINERAMA
[    20.988] Initializing built-in extension XFIXES
[    20.988] Initializing built-in extension RENDER
[    20.988] Initializing built-in extension RANDR
[    20.988] Initializing built-in extension COMPOSITE
[    20.988] Initializing built-in extension DAMAGE
[    20.988] Initializing built-in extension MIT-SCREEN-SAVER
[    20.988] Initializing built-in extension DOUBLE-BUFFER
[    20.988] Initializing built-in extension RECORD
[    20.988] Initializing built-in extension DPMS
[    20.988] Initializing built-in extension X-Resource
[    20.988] Initializing built-in extension XVideo
[    20.988] Initializing built-in extension XVideo-MotionCompensation
[    20.988] Initializing built-in extension XFree86-VidModeExtension
[    20.988] Initializing built-in extension XFree86-DGA
[    20.988] Initializing built-in extension XFree86-DRI
[    20.988] Initializing built-in extension DRI2
[    20.988] (II) "glx" will be loaded by default.
[    20.988] (II) LoadModule: "glx"
[    21.136] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[    21.228] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[    21.228]     compiled for 6.9.0, module version = 1.0.0
[    21.228] Loading extension GLX
[    21.228] (II) LoadModule: "fglrx"
[    21.228] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[    22.021] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[    22.021]     compiled for 1.4.99.906, module version = 12.10.5
[    22.021]     Module class: X.Org Video Driver
[    22.021] (II) Loading sub module "fglrxdrm"
[    22.021] (II) LoadModule: "fglrxdrm"
[    22.021] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    22.100] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    22.100]     compiled for 1.4.99.906, module version = 12.10.5
[    22.100] (II) AMD Proprietary Linux Driver Version Identifier:12.10.05
[    22.100] (II) AMD Proprietary Linux Driver Release Identifier: 12.104                               
[    22.100] (II) AMD Proprietary Linux Driver Build Date: Mar 28 2013 21:07:25
[    22.100] (++) using VT number 7


[    22.100] (WW) Falling back to old probe method for fglrx
[    22.424] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[    22.452] ukiDynamicMajor: found major device number 250
[    22.452] ukiDynamicMajor: found major device number 250
[    22.452] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    22.452] ukiOpenDevice: node name is /dev/ati/card0
[    22.452] ukiOpenDevice: open result is 10, (OK)
[    25.335] ukiOpenByBusid: ukiOpenMinor returns 10
[    25.335] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    25.427] (--) Chipset Supported AMD Graphics Processor (0x6840) found
[    25.447] (II) fglrx: intel VGA device detected, load intel driver.
[    25.447] (II) LoadModule: "intel"
[    25.480] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    25.539] (II) Module intel: vendor="X.Org Foundation"
[    25.539]     compiled for 1.13.0, module version = 2.20.9
[    25.539]     Module class: X.Org Video Driver
[    25.539]     ABI class: X.Org Video Driver, version 13.0
[    25.540] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[    25.559] (II) AMD Video driver is signed
[    25.559] (II) fglrx(0): pEnt->device->identifier=0x7f2ea45403f0
[    25.560] (II) intel(1): pEnt->device->identifier=(nil)
[    25.560] (EE) Screen 1 deleted because of no matching config section.
[    25.560] (II) UnloadModule: "intel"
[    25.560] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[    25.560] (II) fglrx(0): PowerXpress: Discrete GPU is selected.
[    28.573] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    28.573] (==) fglrx(0): RGB weight 888
[    28.573] (==) fglrx(0): Default visual is TrueColor
[    28.573] (**) fglrx(0): Option "Tiling" "off"
[    28.573] (**) fglrx(0): Option "LinearFramebuffer" "on"
[    28.573] (**) fglrx(0): ChipID override: 0x0166
[    28.573] (**) fglrx(0): Integrated Graphics Chipset: Intel(R) Ivybridge Mobile (GT2)
[    28.573] (**) fglrx(0): Relaxed fencing enabled
[    28.573] (**) fglrx(0): Wait on SwapBuffers? enabled
[    28.573] (**) fglrx(0): Triple buffering? enabled
[    28.573] (**) fglrx(0): Framebuffer linear
[    28.573] (**) fglrx(0): Pixmaps linear
[    28.573] (**) fglrx(0): 3D buffers tiled
[    28.584] (**) fglrx(0): SwapBuffers wait enabled
[    28.584] (==) fglrx(0): video overlay key set to 0x101fe
[    28.584] (II) fglrx(0): Output LVDS1 using monitor section aticonfig-Monitor[0]-0
[    28.585] (--) fglrx(0): found backlight control interface /sys/class/backlight/acpi_video1
[    28.585] (II) fglrx(0): Output VGA1 has no monitor section
[    28.585] (II) fglrx(0): Output HDMI1 has no monitor section
[    28.636] (II) fglrx(0): Output DP1 has no monitor section
[    28.636] (II) fglrx(0): EDID for output LVDS1
[    28.636] (II) fglrx(0): Manufacturer: CMO  Model: 15a3  Serial#: 0
[    28.636] (II) fglrx(0): Year: 2010  Week: 31
[    28.636] (II) fglrx(0): EDID Version: 1.3
[    28.636] (II) fglrx(0): Digital Display Input
[    28.636] (II) fglrx(0): Max Image Size [cm]: horiz.: 35  vert.: 19
[    28.636] (II) fglrx(0): Gamma: 2.20
[    28.636] (II) fglrx(0): No DPMS capabilities specified
[    28.636] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    28.636] (II) fglrx(0): First detailed timing is preferred mode
[    28.636] (II) fglrx(0): redX: 0.617 redY: 0.340   greenX: 0.320 greenY: 0.598
[    28.636] (II) fglrx(0): blueX: 0.160 blueY: 0.084   whiteX: 0.313 whiteY: 0.329
[    28.636] (II) fglrx(0): Manufacturer's mask: 0
[    28.636] (II) fglrx(0): Supported detailed timing:
[    28.636] (II) fglrx(0): clock: 70.7 MHz   Image Size:  344 x 193 mm
[    28.636] (II) fglrx(0): h_active: 1366  h_sync: 1406  h_sync_end 1432 h_blank_end 1498 h_border: 0
[    28.636] (II) fglrx(0): v_active: 768  v_sync: 772  v_sync_end 778 v_blanking: 786 v_border: 0
[    28.636] (II) fglrx(0):  N156BGE-L11
[    28.636] (II) fglrx(0):  CMO
[    28.636] (II) fglrx(0):  N156BGE-L11
[    28.636] (II) fglrx(0): EDID (in hex):
[    28.636] (II) fglrx(0):     00ffffffffffff000dafa31500000000
[    28.636] (II) fglrx(0):     1f140103802313780a00259e57529929
[    28.636] (II) fglrx(0):     15505400000001010101010101010101
[    28.636] (II) fglrx(0):     0101010101019e1b568450001230281a
[    28.636] (II) fglrx(0):     460058c110000018000000fe004e3135
[    28.636] (II) fglrx(0):     364247452d4c31310a20000000fe0043
[    28.636] (II) fglrx(0):     4d4f0a202020202020202020000000fe
[    28.636] (II) fglrx(0):     004e3135364247452d4c31310a2000c1
[    28.636] (II) fglrx(0): Not using default mode "320x240" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "400x300" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "512x384" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "640x480" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "640x512" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "800x600" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "896x672" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "928x696" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "960x720" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "576x432" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "680x384" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "700x525" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "720x450" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "800x512" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "840x525" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "960x540" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "960x600" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Not using default mode "1024x768" (doublescan mode not supported)
[    28.636] (II) fglrx(0): Printing probed modes for output LVDS1
[    28.636] (II) fglrx(0): Modeline "1366x768"x60.0   70.70  1366 1406 1432 1498  768 772 778 786 -hsync -vsync (47.2 kHz eP)
[    28.636] (II) fglrx(0): Modeline "1360x768"x59.8   84.75  1360 1432 1568 1776  768 771 781 798 -hsync +vsync (47.7 kHz d)
[    28.636] (II) fglrx(0): Modeline "1360x768"x60.0   72.00  1360 1408 1440 1520  768 771 781 790 +hsync -vsync (47.4 kHz d)
[    28.636] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz d)
[    28.636] (II) fglrx(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz d)
[    28.636] (II) fglrx(0): Modeline "800x600"x56.2   36.00  800 824 896 1024  600 601 603 625 +hsync +vsync (35.2 kHz d)
[    28.636] (II) fglrx(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz d)
[    28.636] (II) fglrx(0): EDID for output VGA1
[    28.637] (II) fglrx(0): EDID for output HDMI1
[    28.688] (II) fglrx(0): EDID for output DP1
[    28.688] (II) fglrx(0): Output LVDS1 connected
[    28.688] (II) fglrx(0): Output VGA1 disconnected
[    28.688] (II) fglrx(0): Output HDMI1 disconnected
[    28.688] (II) fglrx(0): Output DP1 disconnected
[    28.688] (II) fglrx(0): Using exact sizes for initial modes
[    28.688] (II) fglrx(0): Output LVDS1 using initial mode 1366x768
[    28.688] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    28.688] (II) fglrx(0): Kernel page flipping support detected, enabling
[    28.688] (==) fglrx(0): DPI set to (96, 96)
[    28.688] (II) Loading sub module "fb"
[    28.688] (II) LoadModule: "fb"
[    28.688] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.698] (II) Module fb: vendor="X.Org Foundation"
[    28.698]     compiled for 1.13.0, module version = 1.0.0
[    28.698]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.698] (II) Loading sub module "dri2"
[    28.698] (II) LoadModule: "dri2"
[    28.698] (II) Module "dri2" already built-in
[    28.698] (**) fglrx(0): Depth 24, (--) framebuffer bpp 32
[    28.698] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[    28.698] (==) fglrx(0): Default visual is TrueColor
[    28.699] (**) fglrx(0): Option "DPMS" "true"
[    28.699] (==) fglrx(0): RGB weight 888
[    28.699] (II) fglrx(0): Using 8 bits per RGB 
[    28.699] (==) fglrx(0): Buffer Tiling is ON
[    28.699] (II) Loading sub module "fglrxdrm"
[    28.699] (II) LoadModule: "fglrxdrm"
[    28.699] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[    28.699] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[    28.699]     compiled for 1.4.99.906, module version = 12.10.5
[    28.700] ukiDynamicMajor: found major device number 250
[    28.700] ukiDynamicMajor: found major device number 250
[    28.700] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    28.700] ukiOpenDevice: node name is /dev/ati/card0
[    28.700] ukiOpenDevice: open result is 15, (OK)
[    28.700] ukiOpenByBusid: ukiOpenMinor returns 15
[    28.700] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    28.700] (**) fglrx(0): NoAccel = NO
[    28.700] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[    28.700] (--) fglrx(0): Chipset: "AMD Radeon HD 7600M Series" (Chipset = 0x6840)
[    28.701] (--) fglrx(0): (PciSubVendor = 0x144d, PciSubDevice = 0xc0d8)
[    28.701] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[    28.701] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[    28.701] (--) fglrx(0): MMIO registers at 0xc0220000
[    28.701] (--) fglrx(0): I/O port at 0x00003000
[    28.701] (==) fglrx(0): ROM-BIOS at 0x000c0000
[    28.716] (II) fglrx(0): AC Adapter is used
[    28.716] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[    28.716] (--) fglrx(0): Video RAM: 1048576 kByte, Type: DDR3
[    28.716] (II) fglrx(0): PCIE card detected
[    28.716] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[    28.716] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[    28.729] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[    28.729] (II) fglrx(0): RandR 1.2 support is enabled!
[    28.729] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[    28.729] (==) fglrx(0): Center Mode is disabled 
[    28.729] (II) Loading sub module "fb"
[    28.729] (II) LoadModule: "fb"
[    28.730] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.730] (II) Module fb: vendor="X.Org Foundation"
[    28.730]     compiled for 1.13.0, module version = 1.0.0
[    28.730]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.730] (II) Loading sub module "ddc"
[    28.730] (II) LoadModule: "ddc"
[    28.730] (II) Module "ddc" already built-in
[    28.794] (II) fglrx(0): Eyefinity capable adapter detected.
[    28.794] (II) fglrx(0): Adapter AMD Radeon HD 7600M Series has 6 configurable heads and 0 displays connected.
[    28.794] (==) fglrx(0):  PseudoColor visuals disabled
[    28.794] (II) Loading sub module "ramdac"
[    28.794] (II) LoadModule: "ramdac"
[    28.794] (II) Module "ramdac" already built-in
[    28.794] (==) fglrx(0): NoDRI = NO
[    28.794] (==) fglrx(0): Capabilities: 0x00000000
[    28.794] (==) fglrx(0): CapabilitiesEx: 0x00000000
[    28.794] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[    28.794] (==) fglrx(0): UseFastTLS=0
[    28.794] (II) fglrx(0): TearFreeDesktop is not supported on PowerXpress systems currently.
[    28.794] (--) Depth 24 pixmap format is 32 bpp
[    28.794] (II) LoadModule: "glesx"
[    28.794] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[    28.950] (II) Module glesx: vendor="X.Org Foundation"
[    28.950]     compiled for 1.4.99.906, module version = 1.0.0
[    28.950] Loading extension GLESX
[    28.976] (II) fglrx(0): [DRI2] Setup complete
[    28.976] (II) fglrx(0): [DRI2]   DRI driver: i965
[    28.976] (II) fglrx(0): Allocated new frame buffer 1408x768 stride 5632, untiled
[    28.977] (II) UXA(0): Driver registered support for the following operations:
[    28.977] (II)         solid
[    28.977] (II)         copy
[    28.977] (II)         composite (RENDER acceleration)
[    28.977] (II)         put_image
[    28.977] (II)         get_image
[    28.977] (==) fglrx(0): Backing store disabled
[    28.977] (==) fglrx(0): Silken mouse enabled
[    28.977] (II) fglrx(0): Initializing HW Cursor
[    28.977] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.979] (**) fglrx(0): DPMS enabled
[    28.979] (==) fglrx(0): Intel XvMC decoder enabled
[    28.979] (II) fglrx(0): Set up textured video
[    28.979] (II) fglrx(0): [XvMC] xvmc_vld driver initialized.
[    28.979] (II) fglrx(0): direct rendering: DRI2 Enabled
[    28.979] (WW) fglrx(0): Option "VendorName" is not used
[    28.979] (WW) fglrx(0): Option "ModelName" is not used
[    28.979] (WW) fglrx(0): Option "Shadow" is not used
[    28.979] (WW) fglrx(0): Option "Tiling" is not used
[    28.979] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[    28.979] (==) fglrx(0): hotplug detection: "enabled"
[    29.004] Loading extension ATIFGLRXDRI
[    29.004] (II) fglrx(0): doing swlDriScreenInit
[    29.004] (II) fglrx(0): swlDriScreenInit for fglrx driver
[    29.004] ukiDynamicMajor: found major device number 250
[    29.004] ukiDynamicMajor: found major device number 250
[    29.004] ukiDynamicMajor: found major device number 250
[    29.004] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.004] ukiOpenDevice: node name is /dev/ati/card0
[    29.004] ukiOpenDevice: open result is 17, (OK)
[    29.004] ukiOpenByBusid: ukiOpenMinor returns 17
[    29.004] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.004] (II) fglrx(0): [uki] DRM interface version 1.0
[    29.004] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[    29.004] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[    29.004] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f2e9ecbe000
[    29.004] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[    29.004] (II) fglrx(0): [uki] added 1 reserved context for kernel
[    29.004] (II) fglrx(0): swlDriScreenInit done
[    29.004] (II) fglrx(0): Kernel Module Version Information:
[    29.004] (II) fglrx(0):     Name: fglrx
[    29.004] (II) fglrx(0):     Version: 12.10.5
[    29.004] (II) fglrx(0):     Date: Mar 28 2013
[    29.004] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[    29.004] (II) fglrx(0): Kernel Module version matches driver.
[    29.004] (II) fglrx(0): Kernel Module Build Time Information:
[    29.004] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.5.0-36-generic
[    29.004] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[    29.004] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[    29.004] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[    29.004] (II) fglrx(0): [uki] register handle = 0x00004000
[    29.020] (II) fglrx(0): DRI initialization successfull
[    29.020] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01028000
[    29.021] (II) fglrx(0): Intel display surface mc addr for AMD: 9fce0000
[    29.021] (==) fglrx(0): Backing store disabled
[    29.021] Loading extension FGLRXEXTENSION
[    29.021] (**) fglrx(0): DPMS enabled
[    29.021] (II) fglrx(0): Initialized in-driver Xinerama extension
[    29.021] (**) fglrx(0): Textured Video is enabled.
[    29.021] (II) fglrx(0): GLESX enableFlags = 848
[    29.021] (II) fglrx(0): GLESX is enabled
[    29.021] (II) LoadModule: "amdxmm"
[    29.021] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[    29.030] (II) Module amdxmm: vendor="X.Org Foundation"
[    29.030]     compiled for 1.4.99.906, module version = 2.0.0
[    29.030] Loading extension AMDXVOPL
[    29.030] Loading extension AMDXVBA
[    29.030] XvScreenInit: screen devPrivates ptr non-NULL before init
[    29.038] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[    29.040] (II) fglrx(0): Enable composite support successfully
[    29.040] (WW) fglrx(0): Option "VendorName" is not used
[    29.040] (WW) fglrx(0): Option "ModelName" is not used
[    29.040] (WW) fglrx(0): Option "Shadow" is not used
[    29.040] (WW) fglrx(0): Option "Tiling" is not used
[    29.040] (WW) fglrx(0): Option "LinearFramebuffer" is not used
[    29.040] (II) fglrx(0): X context handle = 0x1
[    29.040] (II) fglrx(0): [DRI] installation complete
[    29.042] (WW) fglrx(0): Framebuffer compression is disabled by the driver: Video Ram = 262144 kByte
[    29.042] (--) RandR disabled
[    29.047] ukiDynamicMajor: found major device number 250
[    29.047] ukiDynamicMajor: found major device number 250
[    29.047] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.047] ukiOpenDevice: node name is /dev/ati/card0
[    29.047] ukiOpenDevice: open result is 18, (OK)
[    29.047] ukiOpenByBusid: ukiOpenMinor returns 18
[    29.047] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.289] ukiDynamicMajor: found major device number 250
[    29.289] ukiDynamicMajor: found major device number 250
[    29.289] ukiDynamicMajor: found major device number 250
[    29.289] ukiOpenDevice: node name is /dev/ati/card0
[    29.289] ukiOpenDevice: open result is 19, (OK)
[    29.289] ukiGetBusid returned 'PCI:1:0:0'
[    29.289] ukiOpenDevice: node name is /dev/ati/card1
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card2
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card3
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card4
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card5
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card6
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card7
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card8
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card9
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card10
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card11
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card12
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card13
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card14
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: open result is -1, (No such device)
[    29.289] ukiOpenDevice: Open failed
[    29.289] ukiOpenDevice: node name is /dev/ati/card15
[    29.290] ukiOpenDevice: open result is -1, (No such device)
[    29.290] ukiOpenDevice: open result is -1, (No such device)
[    29.290] ukiOpenDevice: Open failed
[    29.290] ukiDynamicMajor: found major device number 250
[    29.290] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.290] ukiOpenDevice: node name is /dev/ati/card0
[    29.290] ukiOpenDevice: open result is 19, (OK)
[    29.290] ukiOpenByBusid: ukiOpenMinor returns 19
[    29.290] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.736] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[    29.736] ukiDynamicMajor: found major device number 250
[    29.736] ukiDynamicMajor: found major device number 250
[    29.736] ukiDynamicMajor: found major device number 250
[    29.736] ukiOpenDevice: node name is /dev/ati/card0
[    29.736] ukiOpenDevice: open result is 20, (OK)
[    29.736] ukiGetBusid returned 'PCI:1:0:0'
[    29.736] ukiOpenDevice: node name is /dev/ati/card1
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: Open failed
[    29.736] ukiOpenDevice: node name is /dev/ati/card2
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: Open failed
[    29.736] ukiOpenDevice: node name is /dev/ati/card3
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: Open failed
[    29.736] ukiOpenDevice: node name is /dev/ati/card4
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: Open failed
[    29.736] ukiOpenDevice: node name is /dev/ati/card5
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: Open failed
[    29.736] ukiOpenDevice: node name is /dev/ati/card6
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: Open failed
[    29.736] ukiOpenDevice: node name is /dev/ati/card7
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.736] ukiOpenDevice: Open failed
[    29.736] ukiOpenDevice: node name is /dev/ati/card8
[    29.736] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiOpenDevice: node name is /dev/ati/card9
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiOpenDevice: node name is /dev/ati/card10
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiOpenDevice: node name is /dev/ati/card11
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiOpenDevice: node name is /dev/ati/card12
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiOpenDevice: node name is /dev/ati/card13
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiOpenDevice: node name is /dev/ati/card14
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiOpenDevice: node name is /dev/ati/card15
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: open result is -1, (No such device)
[    29.737] ukiOpenDevice: Open failed
[    29.737] ukiDynamicMajor: found major device number 250
[    29.737] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[    29.737] ukiOpenDevice: node name is /dev/ati/card0
[    29.737] ukiOpenDevice: open result is 20, (OK)
[    29.737] ukiOpenByBusid: ukiOpenMinor returns 20
[    29.737] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[    29.831] (II) fglrx(0): Setting screen physical size to 361 x 203
[    29.919] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    29.932] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    29.932] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.932] (II) LoadModule: "evdev"
[    29.932] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    29.952] (II) Module evdev: vendor="X.Org Foundation"
[    29.952]     compiled for 1.13.0, module version = 2.7.3
[    29.952]     Module class: X.Org XInput Driver
[    29.952]     ABI class: X.Org XInput driver, version 18.0
[    29.952] (II) Using input driver 'evdev' for 'Power Button'
[    29.952] (**) Power Button: always reports core events
[    29.952] (**) evdev: Power Button: Device: "/dev/input/event2"
[    29.952] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.952] (--) evdev: Power Button: Found keys
[    29.952] (II) evdev: Power Button: Configuring as keyboard
[    29.952] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input2/event2"
[    29.952] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    29.952] (**) Option "xkb_rules" "evdev"
[    29.952] (**) Option "xkb_model" "pc105"
[    29.952] (**) Option "xkb_layout" "pt"
[    29.954] (II) XKB: reuse xkmfile /var/lib/xkb/server-8F12297C8ADF2DCAF94655EF02F153CE34CF92F1.xkm
[    29.955] (II) config/udev: Adding input device Video Bus (/dev/input/event7)
[    29.955] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.955] (II) Using input driver 'evdev' for 'Video Bus'
[    29.955] (**) Video Bus: always reports core events
[    29.955] (**) evdev: Video Bus: Device: "/dev/input/event7"
[    29.955] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.955] (--) evdev: Video Bus: Found keys
[    29.955] (II) evdev: Video Bus: Configuring as keyboard
[    29.955] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7/event7"
[    29.955] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    29.955] (**) Option "xkb_rules" "evdev"
[    29.955] (**) Option "xkb_model" "pc105"
[    29.955] (**) Option "xkb_layout" "pt"
[    29.955] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    29.955] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    29.955] (II) Using input driver 'evdev' for 'Video Bus'
[    29.955] (**) Video Bus: always reports core events
[    29.955] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    29.955] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    29.955] (--) evdev: Video Bus: Found keys
[    29.955] (II) evdev: Video Bus: Configuring as keyboard
[    29.955] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:1f/LNXVIDEO:00/input/input6/event6"
[    29.955] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 8)
[    29.955] (**) Option "xkb_rules" "evdev"
[    29.955] (**) Option "xkb_model" "pc105"
[    29.955] (**) Option "xkb_layout" "pt"
[    29.956] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[    29.956] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    29.956] (II) Using input driver 'evdev' for 'Power Button'
[    29.956] (**) Power Button: always reports core events
[    29.956] (**) evdev: Power Button: Device: "/dev/input/event0"
[    29.956] (--) evdev: Power Button: Vendor 0 Product 0x1
[    29.956] (--) evdev: Power Button: Found keys
[    29.956] (II) evdev: Power Button: Configuring as keyboard
[    29.956] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[    29.956] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 9)
[    29.956] (**) Option "xkb_rules" "evdev"
[    29.956] (**) Option "xkb_model" "pc105"
[    29.956] (**) Option "xkb_layout" "pt"
[    29.956] (II) config/udev: Adding input device Lid Switch (/dev/input/event1)
[    29.956] (II) No input driver specified, ignoring this device.
[    29.956] (II) This device may have been added with another device file.
[    29.957] (II) config/udev: Adding drm device (/dev/dri/card0)
[    29.957] (II) config/udev: Adding input device GiGa HiD (/dev/input/event4)
[    29.957] (**) GiGa HiD: Applying InputClass "evdev pointer catchall"
[    29.957] (II) Using input driver 'evdev' for 'GiGa HiD'
[    29.957] (**) GiGa HiD: always reports core events
[    29.957] (**) evdev: GiGa HiD: Device: "/dev/input/event4"
[    29.957] (--) evdev: GiGa HiD: Vendor 0x40b Product 0x2011
[    29.957] (--) evdev: GiGa HiD: Found 12 mouse buttons
[    29.957] (--) evdev: GiGa HiD: Found scroll wheel(s)
[    29.957] (--) evdev: GiGa HiD: Found relative axes
[    29.957] (--) evdev: GiGa HiD: Found x and y relative axes
[    29.957] (--) evdev: GiGa HiD: Found absolute axes
[    29.957] (II) evdev: GiGa HiD: Forcing absolute x/y axes to exist.
[    29.957] (II) evdev: GiGa HiD: Configuring as mouse
[    29.957] (II) evdev: GiGa HiD: Adding scrollwheel support
[    29.957] (**) evdev: GiGa HiD: YAxisMapping: buttons 4 and 5
[    29.957] (**) evdev: GiGa HiD: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    29.957] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input4/event4"
[    29.957] (II) XINPUT: Adding extended input device "GiGa HiD" (type: MOUSE, id 10)
[    29.957] (II) evdev: GiGa HiD: initialized for relative axes.
[    29.957] (WW) evdev: GiGa HiD: ignoring absolute axes.
[    29.958] (**) GiGa HiD: (accel) keeping acceleration scheme 1
[    29.958] (**) GiGa HiD: (accel) acceleration profile 0
[    29.958] (**) GiGa HiD: (accel) acceleration factor: 2.000
[    29.958] (**) GiGa HiD: (accel) acceleration threshold: 4
[    29.958] (II) config/udev: Adding input device GiGa HiD (/dev/input/mouse0)
[    29.958] (II) No input driver specified, ignoring this device.
[    29.958] (II) This device may have been added with another device file.
[    29.958] (II) config/udev: Adding input device WebCam SC-13HDL12639P (/dev/input/event8)
[    29.958] (**) WebCam SC-13HDL12639P: Applying InputClass "evdev keyboard catchall"
[    29.958] (II) Using input driver 'evdev' for 'WebCam SC-13HDL12639P'
[    29.958] (**) WebCam SC-13HDL12639P: always reports core events
[    29.958] (**) evdev: WebCam SC-13HDL12639P: Device: "/dev/input/event8"
[    29.958] (--) evdev: WebCam SC-13HDL12639P: Vendor 0xc45 Product 0xc35a
[    29.958] (--) evdev: WebCam SC-13HDL12639P: Found keys
[    29.958] (II) evdev: WebCam SC-13HDL12639P: Configuring as keyboard
[    29.958] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input8/event8"
[    29.958] (II) XINPUT: Adding extended input device "WebCam SC-13HDL12639P" (type: KEYBOARD, id 11)
[    29.958] (**) Option "xkb_rules" "evdev"
[    29.958] (**) Option "xkb_model" "pc105"
[    29.958] (**) Option "xkb_layout" "pt"
[    29.959] (II) config/udev: Adding input device HDA Intel PCH Mic (/dev/input/event10)
[    29.959] (II) No input driver specified, ignoring this device.
[    29.959] (II) This device may have been added with another device file.
[    29.959] (II) config/udev: Adding input device HDA Intel PCH Headphone (/dev/input/event11)
[    29.959] (II) No input driver specified, ignoring this device.
[    29.959] (II) This device may have been added with another device file.
[    29.959] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event9)
[    29.959] (II) No input driver specified, ignoring this device.
[    29.959] (II) This device may have been added with another device file.
[    29.959] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event3)
[    29.960] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    29.960] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    29.960] (**) AT Translated Set 2 keyboard: always reports core events
[    29.960] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event3"
[    29.960] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    29.960] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    29.960] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    29.960] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input3/event3"
[    29.960] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    29.960] (**) Option "xkb_rules" "evdev"
[    29.960] (**) Option "xkb_model" "pc105"
[    29.960] (**) Option "xkb_layout" "pt"
[    29.960] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    29.960] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    29.960] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    29.960] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    29.960] (II) LoadModule: "synaptics"
[    29.960] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    29.967] (II) Module synaptics: vendor="X.Org Foundation"
[    29.967]     compiled for 1.13.0, module version = 1.6.2
[    29.967]     Module class: X.Org XInput Driver
[    29.967]     ABI class: X.Org XInput driver, version 18.0
[    29.967] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    29.967] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    29.967] (**) Option "Device" "/dev/input/event5"
[    30.026] (II) synaptics: SynPS/2 Synaptics TouchPad: ignoring touch events for semi-multitouch device
[    30.026] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1210 - 5738
[    30.026] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 986 - 4886
[    30.026] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    30.026] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    30.026] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right double triple
[    30.026] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    30.026] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.026] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    30.044] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio1/input/input5/event5"
[    30.044] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    30.044] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    30.044] (**) synaptics: SynPS/2 Synaptics TouchPad: MaxSpeed is now 1.75
[    30.044] (**) synaptics: SynPS/2 Synaptics TouchPad: AccelFactor is now 0.033
[    30.044] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    30.044] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    30.044] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    30.044] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    30.044] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    30.044] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    30.044] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    30.086] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[    32.417] (II) fglrx(0): EDID vendor "CMO", prod id 5539
[    32.417] (II) fglrx(0): Printing DDC gathered Modelines:
[    32.417] (II) fglrx(0): Modeline "1366x768"x0.0   70.70  1366 1406 1432 1498  768 772 778 786 -hsync -vsync (47.2 kHz eP)
[    38.570] (II) fglrx(0): EDID vendor "CMO", prod id 5539
[    38.570] (II) fglrx(0): Printing DDC gathered Modelines:
[    38.570] (II) fglrx(0): Modeline "1366x768"x0.0   70.70  1366 1406 1432 1498  768 772 778 786 -hsync -vsync (47.2 kHz eP)
[    58.519] (II) fglrx(0): EDID vendor "CMO", prod id 5539
[    58.519] (II) fglrx(0): Printing DDC gathered Modelines:
[    58.519] (II) fglrx(0): Modeline "1366x768"x0.0   70.70  1366 1406 1432 1498  768 772 778 786 -hsync -vsync (47.2 kHz eP)
[    59.145] (II) fglrx(0): EDID vendor "CMO", prod id 5539
[    59.145] (II) fglrx(0): Printing DDC gathered Modelines:
[    59.145] (II) fglrx(0): Modeline "1366x768"x0.0   70.70  1366 1406 1432 1498  768 772 778 786 -hsync -vsync (47.2 kHz eP)
[    59.852] (II) XKB: reuse xkmfile /var/lib/xkb/server-7F5EE83D34244475884FD664613050C1C331EFCB.xkm
[    82.272] (II) fglrx(0): EDID vendor "CMO", prod id 5539
[    82.272] (II) fglrx(0): Printing DDC gathered Modelines:
[    82.272] (II) fglrx(0): Modeline "1366x768"x0.0   70.70  1366 1406 1432 1498  768 772 778 786 -hsync -vsync (47.2 kHz eP)
[  1141.976] (II) AIGLX: Suspending AIGLX clients for VT switch
[  1141.985] (II) fglrx(0): Backup framebuffer data.
[  1141.995] (II) fglrx(0): Backup complete.
[  1196.224] (II) AIGLX: Resuming AIGLX clients after VT switch
[  1196.240] (II) fglrx(0): Intel display surface mc addr for AMD: 9fce0000
[  1196.280] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[  1196.359] (II) XKB: reuse xkmfile /var/lib/xkb/server-7F5EE83D34244475884FD664613050C1C331EFCB.xkm




```

Dunno which other logs to look for... 

If any of you could be of help...

Thanks...

---

### Post by oldos2er on 2013-07-08
I've changed the thread prefix to 'Kubuntu' since it appears that's the OS you're running, not Lubuntu. If this is incorrect, please advise.

---

### Post by angstrom79 on 2013-07-08
No sorry it's neither sry for that it's regular ubuntu, please re-categorize it...

---

### Post by BreezyBrooke on 2013-07-08
Open the system monitor and see how many cores/cpu's does it say you have. Might have to click through the topmost tabs to find that info.

---

### Post by dino99 on 2013-07-08
is that a standard installation ?
[http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221](http://ubuntuforums.org/showthread.php?t=2112995&p=12495221#post12495221)

you have that crazy daemon endlessly crunching; meaning that something is not installed as it might : exotic app installed by yourself ? searching for wrong path ?

---

### Post by sandyd on 2013-07-08
are you running anything with atd? (atd is a job scheduler)
What is the output of
```
atq
```?

---

### Post by oldos2er on 2013-07-08
> **angstrom79 said:**
> No sorry it's neither sry for that it's regular ubuntu, please re-categorize it...

Done.

---

### Post by angstrom79 on 2013-07-08
BreezyBrooke


4 cores  all running in the upper 90's  


dino99


nothing I could point, it's a pretty standard installation except for being efi boot.

out of the standard repositories I have sublime text, mysql workbench, xampp, spotify, chrome,
 pycharm and phpstorm both of which I did copy to out of my home folder...   

I can't remember more, there some broken ppa's which I disabled... 

sandyd

```


147    Thu Jul  4 21:25:00 2013 = hugo
147    Thu Jul  4 21:31:00 2013 a hugo
147    Thu Jul  4 21:25:00 2013 a hugo
147    Thu Jul  4 21:26:00 2013 a hugo
147    Thu Jul  4 21:26:00 2013 = hugo



```

thanks for your replies

---

### Post by angstrom79 on 2013-07-08
ok update 

so I looked at /var/log/syslog

and this was what was in there

```
Jul  7 08:28:49 hugo-pc atd[3176]: File a00093015d2a09 is in wrong format - abortingJul  7 08:28:49 hugo-pc atd[3163]: File a00093015d2a0f is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3177]: File a00093015d2a0f is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3181]: File a00093015d2a0f is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3178]: File a00093015d2a0a is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3182]: File a00093015d2a0a is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3179]: File a00093015d2a09 is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3173]: File a00093015d2a09 is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3190]: File a00093015d2a09 is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3174]: File a00093015d2a0f is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3193]: File a00093015d2a0a is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3170]: File a00093015d2a09 is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3073]: File a00093015d2a09 is in wrong format - aborting
Jul  7 08:28:49 hugo-pc atd[3171]: File a00093015d2a0f is in wrong format - aborting
```

this loop was running ad infinitum

so i managed to kill atd using 

```
service atd stop
```

and bam 

```
top - 02:14:35 up 29 min,  4 users,  load average: 0.26, 0.64, 2.42
Tasks: 228 total,   2 running, 221 sleeping,   5 stopped,   0 zombie
Cpu(s):  2.7%us,  2.0%sy,  0.0%ni, 95.2%id,  0.2%wa,  0.0%hi,  0.0%si,  0.0%st
Mem:   6002968k total,  3566896k used,  2436072k free,   125960k buffers
Swap:  6348796k total,    14628k used,  6334168k free,  1505856k cached



```


still can u guys help me figure out what the hell is atd trying to do and how to prevent it from doing that...

also I haven't mentioned it before but every now and then when I boot I get a lightdm glitch of red dots on the left side instead of ubuntu loading  splash ...

---

### Post by BreezyBrooke on 2013-07-08
This may take a while, but open the file manager and go to the root folder, then search for "a00093015d2a0f" without quotes. Let's see this file. Or better yet, boot a live cd/usb and mount the hard drive and search that way. S you won't have to stress the computer or break scheduled jobs by AT.

By the way, I was wondering about the number of cores because occasionally Linux can have a botched boot up where it only enables the first cpu core it sees therefore rendering the remaining unused. that of course puts stress on the only running core making it slow and hot.

---

### Post by sandyd on 2013-07-09
> **angstrom79 said:**
> BreezyBrooke


4 cores  all running in the upper 90's  


dino99


nothing I could point, it's a pretty standard installation except for being efi boot.

out of the standard repositories I have sublime text, mysql workbench, xampp, spotify, chrome,
 pycharm and phpstorm both of which I did copy to out of my home folder...   

I can't remember more, there some broken ppa's which I disabled... 

sandyd

```


147    Thu Jul  4 21:25:00 2013 = hugo
147    Thu Jul  4 21:31:00 2013 a hugo
147    Thu Jul  4 21:25:00 2013 a hugo
147    Thu Jul  4 21:26:00 2013 a hugo
147    Thu Jul  4 21:26:00 2013 = hugo



```

thanks for your replies
try
```

atrm 147
```
might need sudo in front of that, ive never tried it

---

### Post by angstrom79 on 2013-07-09
[SIZE=2][COLOR=#000000]thanks BreezyBrooke and sandyd...

I went to [/COLOR]/var/spool/cron/atjobs/ as root and deleted the files in there (the same ones appearing in syslog) and it worked no more atd resource draining, I'm guessing atrm would do the trick as well, as sandyd pointed out...[/SIZE]So the thread can be marked as solved,
 I'm having other unrelated issues related to apt-get sources that I'm troubleshooting right now.

Anyway thanks again people.

---

