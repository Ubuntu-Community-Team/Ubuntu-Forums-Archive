---
title: "Unable to change 1024x768 resolution with radeon 6520g"
date: 2013-09-29
forum: General Help
---

### Post by skoraw on 2013-09-29
Hi, 

After upgrading my kernel to: linux-headers-3.5.0.41-generic (in my update-manager), My resolution on my acer Aspire 5560-7414 has changed to a 1024x768 resolution and I'm unable to change it back to a larger resolution which it was in the past. 

My video card is a AMD radeon 6520G, which is supported see [http://www.ubuntu.com/certification/catalog/component/pci/1002:9647/](http://www.ubuntu.com/certification/catalog/component/pci/1002:9647/) and [http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware) SUMO,SUMO2  Radeon HD 6370/6380/6400/6410/6480/6520/6530/6550/6620

I had been using the default open-source drivers for some time and I've rebooted and switched to older kernels at boot, like 3.5.0-39-generic and my resolution is still stuck at 1024x768. 

Following [https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure](https://help.ubuntu.com/community/GraphicsTroubleshootingProcedure),

Here is my output according to: 
```
lspci -nnk | grep -iA2 aphics; Xorg -version; sudo apt-get update; sudo apt-get install hwinfo mesa-utils hardinfo;  apt-cache show xserver-xorg | grep Version; xrandr; fglrxinfo; nvidia-settings -g |head -n 30 ; lspci -nnk | grep -iA2 VGA; sudo lshw -short; sudo lshw -C display; sudo hwinfo --gfxcard; dpkg -l | egrep 'fgl|intel|mesa|mesa-utils|nvidia|NVIDIA|nouveau|radeon|video-ati'; cat /etc/lsb-release; dmesg | egrep 'abort|ailed|error|fail|fgl|GLX|GPU|intel|issing|nouveau|nvidia|NVIDIA|radeon|segment|VESA|VGA|wfb|\(EE\)|\(WW\)'; cat /proc/cpuinfo | grep -I model; cat /var/log/Xorg.0.log | egrep 'abort|ailed|error|fail|fgl|GLX|GPU|intel|issing|nouveau|nvidia|NVIDIA|radeon|segment|VESA|VGA|wfb|\(EE\)|\(WW\)'; sudo dmidecode|egrep 'anufact|roduct|erial|elease'; cat /etc/X11/xorg.conf; /usr/lib/nux/unity_support_test -p; ubuntu-support-status ; sudo lsmod
``` 
```
X.Org X Server 1.13.0
Release Date: 2012-09-05
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-37-generic x86_64 Ubuntu
Current Operating System: Linux limonade 3.5.0-39-generic #60~precise1-Ubuntu SMP Wed Aug 14 15:38:41 UTC 2013 x86_64
Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.5.0-39-generic root=UUID=b99ff469-e48c-4cc6-9c1d-28758f294363 ro nomodeset
Build Date: 11 April 2013  11:49:23PM
xorg-server 2:1.13.0-0ubuntu6.1~precise3 (For technical support please see http://www.ubuntu.com/support) 
Current version of pixman: 0.24.4
    Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
(I removed the apt-sources that were hit...) 
Hit http://us.archive.ubuntu.com precise Release.gpgltiverse Translation-en                               
Hit http://security.ubuntu.com precise-security/restricted Translation-en                               
Hit http://security.ubuntu.com precise-security/universe Translation-en                                 
Fetched 1,019 kB in 6s (158 kB/s)                                                                       
Reading package lists... Done
Reading package lists... Done
Building dependency tree       
Reading state information... Done
hardinfo is already the newest version.
hwinfo is already the newest version.
mesa-utils is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-23-generic linux-headers-3.5.0-23 thunderbird-globalmenu libqgis1.8.0
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Version: 1:7.6+12ubuntu2
Version: 1:7.6+12ubuntu1
xrandr: Failed to get size of gamma for output default
Screen 0: minimum 800 x 600, current 1024 x 768, maximum 1024 x 768
default connected 1024x768+0+0 0mm x 0mm
   1024x768        0.0* 
   800x600        61.0  
fglrxinfo: command not found
nvidia-settings: command not found
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] BeaverCreek [Radeon HD 6520G] [1002:9647]
    Subsystem: Acer Incorporated [ALI] Device [1025:059f]
    Kernel modules: radeon
H/W path      Device      Class       Description
=================================================
                          system      Aspire 5560 (System SKU Number Unknown)
/0                        bus         Aspire 5560
/0/0                      memory      128KiB BIOS
/0/2d                     memory      8GiB System Memory
/0/2d/0                   memory      4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/2d/1                   memory      4GiB SODIMM DDR3 Synchronous 1333 MHz (0.8 ns)
/0/33                     processor   AMD A6-3420M APU with Radeon(tm) HD Graphics
/0/33/34                  memory      512KiB L1 cache
/0/33/35                  memory      4MiB L2 cache
/0/100                    bridge      Family 12h Processor Root Complex
/0/100/1                  display     BeaverCreek [Radeon HD 6520G]
/0/100/1.1                multimedia  BeaverCreek HDMI Audio [Radeon HD 6500D and 6400G-6600G series]
/0/100/4                  bridge      Family 12h Processor Root Port
/0/100/4/0    eth0        network     NetLink BCM57785 Gigabit Ethernet PCIe
/0/100/4/0.1              generic     BCM57765/57785 SDXC/MMC Card Reader
/0/100/4/0.2              generic     BCM57765/57785 MS Card Reader
/0/100/4/0.3              generic     BCM57765/57785 xD-Picture Card Reader
/0/100/6                  bridge      Family 12h Processor Root Port
/0/100/6/0    wlan0       network     AR9287 Wireless Network Adapter (PCI-Express)
/0/100/11                 storage     FCH SATA Controller [AHCI mode]
/0/100/12                 bus         FCH USB OHCI Controller
/0/100/12.2               bus         FCH USB EHCI Controller
/0/100/13                 bus         FCH USB OHCI Controller
/0/100/13.2               bus         FCH USB EHCI Controller
/0/100/14                 bus         FCH SMBus Controller
/0/100/14.2               multimedia  FCH Azalia Controller
/0/100/14.3               bridge      FCH LPC Bridge
/0/100/14.4               bridge      FCH PCI Bridge
/0/100/16                 bus         FCH USB OHCI Controller
/0/100/16.2               bus         FCH USB EHCI Controller
/0/101                    bridge      Family 12h/14h Processor Function 0
/0/102                    bridge      Family 12h/14h Processor Function 1
/0/103                    bridge      Family 12h/14h Processor Function 2
/0/104                    bridge      Family 12h/14h Processor Function 3
/0/105                    bridge      Family 12h/14h Processor Function 4
/0/106                    bridge      Family 12h/14h Processor Function 6
/0/107                    bridge      Family 12h/14h Processor Function 5
/0/108                    bridge      Family 12h/14h Processor Function 7
/0/1          scsi0       storage     
/0/1/0.0.0    /dev/sda    disk        1TB ST1000LM014-1EJ1
/0/1/0.0.0/1  /dev/sda1   volume      93MiB Windows FAT volume
/0/1/0.0.0/2  /dev/sda2   volume      39GiB EXT4 volume
/0/1/0.0.0/3  /dev/sda3   volume      114GiB EXT4 volume
/0/1/0.0.0/4  /dev/sda4   volume      7628MiB Linux swap volume
/0/1/0.0.0/5  /dev/sda5   volume      769GiB EXT4 volume
/0/2          scsi1       storage     
/0/2/0.0.0    /dev/cdrom  disk        DVD-RAM UJ8B0AW
  *-display UNCLAIMED     
       description: VGA compatible controller
       product: BeaverCreek [Radeon HD 6520G]
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list
       configuration: latency=0
       resources: memory:e0000000-efffffff ioport:2000(size=256) memory:f0200000-f023ffff
> hal.1: read hal dataprocess 5860: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
09: PCI 01.0: 0300 VGA compatible controller (VGA)              
  [Created at pci.318]
  Unique ID: vSkL.7YCSWqKsGU0
  SysFS ID: /devices/pci0000:00/0000:00:01.0
  SysFS BusID: 0000:00:01.0
  Hardware Class: graphics card
  Model: "ATI VGA compatible controller"
  Vendor: pci 0x1002 "ATI Technologies Inc"
  Device: pci 0x9647 
  SubVendor: pci 0x1025 "Acer Incorporated [ALI]"
  SubDevice: pci 0x059f 
  Memory Range: 0xe0000000-0xefffffff (ro,non-prefetchable)
  I/O Ports: 0x2000-0x20ff (rw)
  Memory Range: 0xf0200000-0xf023ffff (rw,non-prefetchable)
  IRQ: 18 (385128 events)
  Module Alias: "pci:v00001002d00009647sv00001025sd0000059Fbc03sc00i00"
  Driver Info #0:
    Driver Status: radeon is active
    Driver Activation Cmd: "modprobe radeon"
  Config Status: cfg=new, avail=yes, need=no, active=unknown

Primary display adapter: #9
ii  intel-gpu-tools                              1.2-1                                               tools for debugging the Intel graphics driver
ii  libdrm-intel1                                2.4.43-0ubuntu0.0.2                                 Userspace interface to intel-specific kernel DRM services -- runtime
ii  libdrm-nouveau1a                             2.4.43-0ubuntu0.0.2                                 Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-nouveau2                              2.4.43-0ubuntu0.0.2                                 Userspace interface to nouveau-specific kernel DRM services -- runtime
ii  libdrm-radeon1                               2.4.43-0ubuntu0.0.2                                 Userspace interface to radeon-specific kernel DRM services -- runtime
ii  libgl1-mesa-dri-lts-quantal                  9.0.3-0ubuntu0.4~precise1                           free implementation of the OpenGL API -- DRI modules
ii  libgl1-mesa-glx-lts-quantal                  9.0.3-0ubuntu0.4~precise1                           free implementation of the OpenGL API -- GLX runtime
ii  libglapi-mesa-lts-quantal                    9.0.3-0ubuntu0.4~precise1                           free implementation of the GL API -- shared library
ii  libglu1-mesa                                 8.0.4-0ubuntu0.6                                    Mesa OpenGL utility library (GLU)
ii  mesa-utils                                   8.0.1+git20110129+d8f7d6b-0ubuntu2                  Miscellaneous Mesa GL utilities
ii  nvidia-common                                1:0.2.44.2                                          Find obsolete NVIDIA drivers
ii  radeontool                                   1.6.2-1.1                                           utility to control ATI Radeon backlight functions on laptops
ii  whois                                        5.0.15ubuntu2                                       intelligent WHOIS client
ii  xserver-xorg-video-ati-lts-quantal           1:6.99.99~git20120913.8637f772-0ubuntu1~precise2    X.Org X server -- AMD/ATI display driver wrapper
ii  xserver-xorg-video-intel-lts-quantal         2:2.20.9-0ubuntu2.2~precise1                        X.Org X server -- Intel i8xx, i9xx display driver
ii  xserver-xorg-video-nouveau-lts-quantal       1:1.0.2-0ubuntu3~precise2                           X.Org X server -- Nouveau display driver
ii  xserver-xorg-video-radeon-lts-quantal        1:6.99.99~git20120913.8637f772-0ubuntu1~precise2    X.Org X server -- AMD/ATI Radeon display driver
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=12.04
DISTRIB_CODENAME=precise
DISTRIB_DESCRIPTION="Ubuntu 12.04.3 LTS"
[    0.008000] Marking TSC unstable due to check_tsc_sync_source failed
[    0.382487] fb0: EFI VGA frame buffer device
[    1.387877] [drm] VGACON disable radeon kernel modesetting.
[    1.397805] [drm] Initialized radeon 1.33.0 20080528 for 0000:00:01.0 on minor 0
[    1.444896] ACPI: Video Device [VGA1] (multi-head: yes  rom: no  post: no)
[    2.432104] usb 6-2: device descriptor read/64, error -62
[    2.676074] usb 6-2: device descriptor read/64, error -62
[    3.056275] usb 6-2: device descriptor read/64, error -62
[    3.300124] usb 6-2: device descriptor read/64, error -62
[    3.948268] usb 6-2: device not accepting address 4, error -62
[    4.492280] usb 6-2: device not accepting address 5, error -62
[    4.787094] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[    7.490021] snd_hda_intel 0000:00:01.1: irq 43 for MSI/MSI-X
[   22.907894] init: failsafe main process (861) killed by TERM signal
[   29.520099] usb 6-2: device descriptor read/64, error -62
[   29.764151] usb 6-2: device descriptor read/64, error -62
[   30.144149] usb 6-2: device descriptor read/64, error -62
[   30.388099] usb 6-2: device descriptor read/64, error -62
[   31.036044] usb 6-2: device not accepting address 8, error -62
[   31.580230] usb 6-2: device not accepting address 9, error -62
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
model        : 1
model name    : AMD A6-3420M APU with Radeon(tm) HD Graphics
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.176] (==) Automatically adding GPU devices
[    24.242] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.242] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.242] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.242] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.242] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.242] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[    24.256] (==) AIGLX enabled
[    24.257] Loading extension GLX
[    24.257] (==) Matched fglrx as autoconfigured driver 0
[    24.257] (==) Matched fglrx as autoconfigured driver 2
[    24.257] (II) LoadModule: "fglrx"
[    24.258] (WW) Warning, couldn't open module fglrx
[    24.258] (II) UnloadModule: "fglrx"
[    24.259] (II) Unloading fglrx
[    24.259] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    24.259] (II) LoadModule: "radeon"
[    24.260] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[    24.265] (II) Module radeon: vendor="X.Org Foundation"
[    24.269] (==) Matched fglrx as autoconfigured driver 0
[    24.269] (==) Matched fglrx as autoconfigured driver 2
[    24.269] (II) LoadModule: "fglrx"
[    24.269] (WW) Warning, couldn't open module fglrx
[    24.269] (II) UnloadModule: "fglrx"
[    24.269] (II) Unloading fglrx
[    24.269] (EE) Failed to load module "fglrx" (module does not exist, 0)
[    24.270] (II) Failed to load module "vesa" (already loaded, 0)
[    24.270] (II) Failed to load module "modesetting" (already loaded, 0)
[    24.270] (II) Failed to load module "fbdev" (already loaded, 0)
[    24.275] (II) VESA: driver for VESA chipsets: vesa
[    24.276] (WW) Falling back to old probe method for modesetting
[    24.280] (WW) Falling back to old probe method for fbdev
[    24.282] (EE) Screen 0 deleted because of no matching config section.
[    24.282] (II) UnloadModule: "radeon"
[    24.282] (EE) Screen 0 deleted because of no matching config section.
[    24.282] (II) UnloadModule: "radeon"
[    24.282] (EE) Screen 0 deleted because of no matching config section.
[    24.282] (II) UnloadModule: "radeon"
[    24.282] (EE) Screen 0 deleted because of no matching config section.
[    24.282] (II) UnloadModule: "radeon"
[    24.286] (II) VESA(0): initializing int10
[    25.290] (II) VESA(0): VESA BIOS detected
[    25.290] (II) VESA(0): VESA VBE Version 3.0
[    25.290] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    25.290] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    25.290] (II) VESA(0): VESA VBE OEM Software Rev: 12.43
[    25.290] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    25.290] (II) VESA(0): VESA VBE OEM Product: SUMO
[    25.290] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    25.303] (II) VESA(0): Creating default Display subsection in Screen section
[    25.303] (==) VESA(0): Depth 24, (--) framebuffer bpp 32
[    25.303] (==) VESA(0): RGB weight 888
[    25.303] (==) VESA(0): Default visual is TrueColor
[    25.303] (==) VESA(0): Using gamma correction (1.0, 1.0, 1.0)
[    25.303] (II) VESA(0): VESA VBE DDC supported
[    25.303] (II) VESA(0): VESA VBE DDC Level 2
[    25.303] (II) VESA(0): VESA VBE DDC transfer in appr. 1 sec.
[    25.429] (II) VESA(0): VESA VBE DDC read successfully
[    25.429] (II) VESA(0): Manufacturer: LGD  Model: 2dc  Serial#: 0
[    25.429] (II) VESA(0): Year: 2010  Week: 0
[    25.429] (II) VESA(0): EDID Version: 1.3
[    25.429] (II) VESA(0): Digital Display Input
[    25.429] (II) VESA(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    25.429] (II) VESA(0): Gamma: 2.20
[    25.429] (II) VESA(0): No DPMS capabilities specified
[    25.429] (II) VESA(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    25.429] (II) VESA(0): First detailed timing is preferred mode
[    25.429] (II) VESA(0): redX: 0.623 redY: 0.369   greenX: 0.346 greenY: 0.610
[    25.429] (II) VESA(0): blueX: 0.148 blueY: 0.098   whiteX: 0.313 whiteY: 0.329
[    25.429] (II) VESA(0): Manufacturer's mask: 0
[    25.429] (II) VESA(0): Supported detailed timing:
[    25.430] (II) VESA(0): clock: 70.0 MHz   Image Size:  344 x 194 mm
[    25.430] (II) VESA(0): h_active: 1366  h_sync: 1402  h_sync_end 1450 h_blank_end 1492 h_border: 0
[    25.430] (II) VESA(0): v_active: 768  v_sync: 771  v_sync_end 776 v_blanking: 782 v_border: 0
[    25.430] (II) VESA(0):  LG Display
[    25.430] (II) VESA(0):  LP156WH4-TLA1
[    25.430] (II) VESA(0): EDID (in hex):
[    25.430] (II) VESA(0):     00ffffffffffff0030e4dc0200000000
[    25.430] (II) VESA(0):     00140103802213780aa9059f5e589c26
[    25.430] (II) VESA(0):     19505400000001010101010101010101
[    25.430] (II) VESA(0):     010101010101581b567e50000e302430
[    25.430] (II) VESA(0):     350058c2100000190000000000000000
[    25.430] (II) VESA(0):     00000000000000000000000000fe004c
[    25.430] (II) VESA(0):     4720446973706c61790a2020000000fe
[    25.430] (II) VESA(0):     004c503135365748342d544c41310079
[    25.430] (II) VESA(0): EDID vendor "LGD", prod id 732
[    25.430] (II) VESA(0): Printing DDC gathered Modelines:
[    25.430] (II) VESA(0): Modeline "1366x768"x0.0   70.00  1366 1402 1450 1492  768 771 776 782 -hsync -vsync (46.9 kHz eP)
[    25.430] (II) VESA(0): Searching for matching VESA mode(s):
[    25.460] (II) VESA(0): Total Memory: 256 64KB banks (16384kB)
[    25.460] (II) VESA(0): <default monitor>: Using hsync value of 46.92 kHz
[    25.460] (II) VESA(0): <default monitor>: Using vrefresh value of 60.00 Hz
[    25.460] (WW) VESA(0): Unable to estimate virtual size
[    25.460] (II) VESA(0): Not using built-in mode "1024x768" (no mode of this name)
[    25.460] (II) VESA(0): Not using built-in mode "800x600" (no mode of this name)
[    25.460] (II) VESA(0): Not using built-in mode "640x480" (no mode of this name)
[    25.460] (II) VESA(0): Not using built-in mode "720x400" (no mode of this name)
[    25.460] (II) VESA(0): Not using built-in mode "640x350" (no mode of this name)
[    25.460] (II) VESA(0): Not using built-in mode "512x384" (no mode of this name)
[    25.460] (II) VESA(0): Not using built-in mode "320x240" (no mode of this name)
[    25.460] (II) VESA(0): Not using built-in mode "320x200" (no mode of this name)
[    25.460] (WW) VESA(0): No valid modes left. Trying less strict filter...
[    25.460] (II) VESA(0): <default monitor>: Using hsync value of 46.92 kHz
[    25.460] (II) VESA(0): <default monitor>: Using vrefresh value of 60.00 Hz
[    25.460] (WW) VESA(0): Unable to estimate virtual size
[    25.461] (II) VESA(0): Not using built-in mode "1024x768" (hsync out of range)
[    25.461] (II) VESA(0): Not using built-in mode "800x600" (hsync out of range)
[    25.461] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    25.461] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[    25.461] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[    25.461] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[    25.461] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    25.461] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    25.461] (WW) VESA(0): No valid modes left. Trying aggressive sync range...
[    25.461] (II) VESA(0): <default monitor>: Using hsync range of 31.50-46.92 kHz
[    25.461] (II) VESA(0): <default monitor>: Using vrefresh range of 50.00-60.00 Hz
[    25.461] (WW) VESA(0): Unable to estimate virtual size
[    25.461] (II) VESA(0): Not using built-in mode "640x480" (hsync out of range)
[    25.462] (II) VESA(0): Not using built-in mode "720x400" (hsync out of range)
[    25.462] (II) VESA(0): Not using built-in mode "640x350" (hsync out of range)
[    25.462] (II) VESA(0): Not using built-in mode "512x384" (hsync out of range)
[    25.462] (II) VESA(0): Not using built-in mode "320x240" (illegal horizontal timings)
[    25.462] (II) VESA(0): Not using built-in mode "320x200" (illegal horizontal timings)
[    25.462] (--) VESA(0): Virtual size is 1024x768 (pitch 1024)
[    25.462] (**) VESA(0): *Built-in mode "1024x768"
[    25.462] (**) VESA(0): *Built-in mode "800x600"
[    25.462] (**) VESA(0): Display dimensions: (340, 190) mm
[    25.462] (**) VESA(0): DPI set to (76, 102)
[    25.462] (II) VESA(0): Attempting to use 60Hz refresh for mode "800x600" (122)
[    25.462] (**) VESA(0): Using "Shadow Framebuffer"
[    25.466] (II) UnloadModule: "radeon"
[    25.467] (II) VESA(0): initializing int10
[    26.390] (II) VESA(0): VESA BIOS detected
[    26.390] (II) VESA(0): VESA VBE Version 3.0
[    26.390] (II) VESA(0): VESA VBE Total Mem: 16384 kB
[    26.390] (II) VESA(0): VESA VBE OEM: AMD ATOMBIOS
[    26.390] (II) VESA(0): VESA VBE OEM Software Rev: 12.43
[    26.390] (II) VESA(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[    26.390] (II) VESA(0): VESA VBE OEM Product: SUMO
[    26.390] (II) VESA(0): VESA VBE OEM Product Rev: 01.00
[    26.391] (II) VESA(0): virtual address = 0x7f66550d7000,
[    26.402] (II) VESA(0): Setting up VESA Mode 0x123 (1024x768)
[    27.007] (==) VESA(0): Default visual is TrueColor
[    27.010] (==) VESA(0): Backing store disabled
[    27.011] (==) VESA(0): DPMS enabled
[    27.019] (II) AIGLX: Screen 0 is not DRI2 capable
[    27.019] (II) AIGLX: Screen 0 is not DRI capable
[    27.107] (II) AIGLX: Loaded and initialized swrast
[    27.107] (II) GLX: Initialized DRISWRAST GL provider for screen 0
    Release Date: 12/05/2011
        Serial services are supported (int 14h)
    Manufacturer: Acer
    Product Name: Aspire 5560
    Serial Number: LXRNW0205922000B826600
    Manufacturer: Acer
    Product Name: Aspire 5560
    Serial Number: LXRNW0205922000B826600
    Manufacturer: Acer
    Serial Number: LXRNW0205922000B826600
    Manufacturer: Not Specified
    Serial Number: 03000000
    Manufacturer: Not Specified
    Serial Number: 03000000
    Manufacturer: AMD
    Serial Number: Not Specified
cat: /etc/X11/xorg.conf: No such file or directory
OpenGL vendor string:   VMware, Inc.
OpenGL renderer string: Gallium 0.4 on llvmpipe (LLVM 0x301)
OpenGL version string:  2.1 Mesa 9.0.3

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
Support status summary of 'limonade':

You have 92 packages (4.3%) supported until October 2013 (18m)
You have 58 packages (2.7%) supported until March 2015 (18m)
You have 1662 packages (76.8%) supported until April 2017 (5y)

You have 2 packages (0.1%) that can not/no-longer be downloaded
You have 350 packages (16.2%) that are unsupported

Run with --show-unsupported, --show-supported or --show-all to see more details


```

After some google searching, I know that 
*-display UNCLAIMED in the output of  sudo lshw -C display means that my video driver is not loaded... I had been using the open-source one, sumo (I think it's called), without any problems until yesterday after I upgraded the kernel. 

Any help to fix my resolution back to its original state (I believe it was 1280x800) would be appreciated.

---

### Post by skoraw on 2013-09-29
It's definitely a software configuration issue. 

I've loaded a livecd of ubuntu 12.04 (64bit) on the same system and I have no problems - my resolution is  1366x768, 

I noticed my output of 
 sudo lshw -C display is different than that of my system. 


  *-display               
       description: VGA compatible controller
       product: Advanced Micro Devices [AMD] nee ATI
       vendor: Hynix Semiconductor (Hyundai Electronics)
       physical id: 1
       bus info: pci@0000:00:01.0
       version: 00
       width: 32 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0
       resources: irq:43 memory:e0000000-efffffff ioport:2000(size=256) memory:f0200000-f023ffff

and my xrandr input is different than my system as well: 

```
ubuntu@ubuntu:~$ xrandr
Screen 0: minimum 320 x 200, current 1366 x 768, maximum 8192 x 8192
VGA-0 disconnected (normal left inverted right x axis y axis)
eDP connected 1366x768+0+0 (normal left inverted right x axis y axis) 344mm x 194mm
   1366x768       60.0*+
   1280x720       59.9  
   1152x768       59.8  
   1024x768       59.9  
   800x600        59.9  
   848x480        59.7  
   720x480        59.7  
   640x480        59.4  
HDMI-0 disconnected (normal left inverted right x axis y axis)
```

---

### Post by skoraw on 2013-09-30
While inspecting my /var/log/Xorg.0.log ; 

this looks to be the culprit but I have not figured out how to fix it. 

```
[     5.672] (EE) Screen 0 deleted because of no matching config section.
[     5.672] (II) UnloadModule: "radeon"
```

---

### Post by Yellow Pasque on 2013-09-30
Hmm. Try making a really basic /etc/X11/xorg.conf:
```
Section "Device"
        Identifier      "Configured Video Device"
        Driver          "radeon"
#       BusID	        "PCI:0:1:0"
EndSection

Section "Monitor"
        Identifier      "Configured Monitor"
EndSection

Section "Screen"
        Identifier      "Default Screen"
        Monitor         "Configured Monitor"
        Device          "Configured Video Device"
EndSection
```

---

### Post by skoraw on 2013-09-30
An hour or 2 before I updated the kernel, I had been troubleshooting why my ubuntu system was hanging at shutdown and followed the advice at [http://askubuntu.com/a/291856/37037](http://askubuntu.com/a/291856/37037)

I had changed my /etc/default/grub , specifically the line: 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash"
to 
GRUB_CMDLINE_LINUX_DEFAULT="nomodeset" 
As a result, this, to my surprise prevented the radeon driver from being loaded at boot.

I ended up resolving this thanks to some users from #radeon (freenode).
According to chithead in #radeon (Freenode), nomodeset is apparently also a telltale sign that the proprietary graphics driver was loaded. 

After removing the nomodeset line, my graphics now display as I intended. My system still hangs at shutdown however, a separate issue.

---

