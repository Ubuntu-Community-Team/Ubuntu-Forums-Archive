---
title: "HDMI works only when using Ubuntu live on USB stick"
date: 2015-10-24
forum: General Help
---

### Post by gaetano5 on 2015-10-24
Hello all,
I have a strange issue I'm not able to solve, even after hours of Google searching.


I have a Compaq CQ60, 64 bit AMD cpu; My HDMI port works perfectly if I start Ubuntu Mate 15.04 from an USB stick: I can connect with my Panasonic Viera 42" plasma TV trough HDMI cable and I'm able to mirror my laptop screen on the TV.


Problems arise as soon as I install permanently on the hard disk our beloved distro: once installed, Ubuntu can still see my HDMI port, it detects a new display as soon as I connect my HDMI cable between my laptop and the TV but:


1) It detects a Panasonic 58" display instead of the correct 42" one
2)My TV displays stays black, meaning that data seem not being transmitted at all trough the HDMI port/cable.


Moreover, I would like to point out that the same issue happens with other distro I tried: Ubuntu 14.04, Ubuntu 15.04, Kubuntu 15.04, Elementary OS, KXstudio and others that I honestly don't remember right now..


The Laptop video card is an Nvidia (it should be a GeForce8200M if my memory doesn't fool me) and I've also tried to install proprietary up-to-date drivers, but things haven't changed, instead this worsen the situation: apart from the TV still with a black screen, proprietary drivers seems to cause also the instability of the system, because the laptop screen starts to flicker and/or the system froze.


I will be grateful to anyone who will try to help me ):P

---

### Post by tgalati4 on 2015-10-24
Welcome to the forums.  The Live Session uses open drivers and generally safe settings.  Once installed, you get a custom set of settings specific for your hardware.  Then you are offered proprietary drivers which you can install afterwards.

Boot the Live Session and open a terminal.  Post the output:

```
lsmod
```

Boot into your 15.04 install and post:

```
lsmod
```

Look in /var/log/Xorg.0.log for errors.



And your graphics:

```
lspci | grep VGA
```

---

### Post by gaetano5 on 2015-10-26
[SIZE=5]**_BOOT FROM LIVE USB (KUBUNTU):_**[/SIZE]


_**Output of lsmod command:**_

```

kubuntu@kubuntu:~$ lsmod 
Module                  Size  Used by 
ctr                        16384  2  
ccm                      20480  2  
snd_hda_codec_hdmi     53248  1  
snd_hda_codec_conexant    24576  1  
snd_hda_codec_generic    69632  1 
snd_hda_codec_conexant arc4                   16384  2  
hp_wmi                 16384  0  
sparse_keymap          16384  1 
hp_wmi snd_hda_intel          32768  3  
snd_hda_controller     32768  1 
snd_hda_intel snd_hda_codec         143360  5 
snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller snd_hwdep              20480  1 
snd_hda_codec snd_pcm               106496  4 
snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller snd_seq_midi           16384  0  
snd_seq_midi_event     16384  1 
snd_seq_midi ath5k                 151552  0  
dm_multipath           24576  0  
snd_rawmidi            32768  1 
snd_seq_midi scsi_dh                16384  1 
dm_multipath ath                    32768  1 
ath5k kvm                   483328  0  
mac80211              720896  1 
ath5k cfg80211              540672  3 
ath,ath5k,mac80211 snd_seq                69632  2 
snd_seq_midi_event,snd_seq_midi joydev                 20480  0  
uvcvideo               90112  0  
videobuf2_vmalloc      16384  1 
uvcvideo videobuf2_memops       16384  1           videobuf2_vmalloc                                                                                                                                               
serio_raw              16384  0                                                                                                                                                                  
k10temp                16384  0                                                                                                                                                                  
videobuf2_core         49152  1                                    uvcvideo                                                                                                                                                         
v4l2_common            16384  1                                     videobuf2_core                                                                                                                                                   
videodev              159744  3                                          uvcvideo,v4l2_common,videobuf2_core                                                                                                                              
snd_seq_device         16384  3                                    snd_seq,snd_rawmidi,snd_seq_midi                                                                                                                                 
media                  24576  2                                              uvcvideo,videodev                                                                                                                                                
snd_timer              32768  2                                          snd_pcm,snd_seq                                                                                                                                                  
shpchp                 40960  0                                                                                                                                                                  
snd                    90112  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device     
soundcore              16384  2                                        snd,snd_hda_codec                                                                                                                                                
i2c_nforce2            16384  0                                                                                                                                                                  
mac_hid                16384  0                                                                                                                                                                  
parport_pc             32768  0                                                                                                                                                                  
ppdev                  20480  0                                                                                                                                                                  
lp                     20480  0                                                                                                                                                                  
parport                45056  3 
lp,ppdev,parport_pc autofs4                40960  2  
squashfs               49152  1 
overlay                45056  1  
nls_iso8859_1          16384  1  
dm_mirror              24576  0  
dm_region_hash         24576  1 
dm_mirror dm_log                 20480  2 
dm_region_hash,dm_mirror hid_generic            16384  0  
usbhid                 53248  0  
hid                   110592  2 
hid_generic,usbhid pata_acpi              16384  0  
ums_realtek            20480  0  
uas                    24576  0  
usb_storage            69632  3 
uas,ums_realtek nouveau              1400832  7  
mxm_wmi                16384  1 
nouveau psmouse               118784  0  
i2c_algo_bit           16384  1 
nouveau ttm                    98304  1 
nouveau drm_kms_helper        122880  1 
nouveau drm                   344064  10 
ttm,drm_kms_helper,nouveau forcedeth              69632  0  
ahci                   36864  2  
pata_amd               20480  0  
libahci                32768  1 
ahci wmi                    20480  3 
hp_wmi,mxm_wmi,nouveau video                  20480  1                    nouveau 
kubuntu@kubuntu:~$                                                                                                                                                                                                  

```



_**Output of lspci | grep VGA :**_


```

kubuntu@kubuntu:~$ lspci | grep VGA
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200M G] (rev a2)
kubuntu@kubuntu:~$ 

```


[B][U]This is the content of Xorg.o.log file:
[/U][/B]
```

[    26.106] 
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    26.106] X Protocol Version 11, Revision 0
[    26.106] Build Operating System: Linux 3.2.0-61-generic x86_64 Ubuntu
[    26.106] Current Operating System: Linux kubuntu 3.19.0-15-generic #15-Ubuntu SMP Thu Apr 16 23:32:37 UTC 2015 x86_64
[    26.106] Kernel command line: initrd=/casper/initrd.lz file=/cdrom/preseed/kubuntu.seed boot=casper maybe-ubiquity  quiet splash --- BOOT_IMAGE=/casper/vmlinuz.efi 
[    26.106] Build Date: 19 March 2015  09:26:59AM
[    26.106] xorg-server 2:1.17.1-0ubuntu3 (For technical support please see http://www.ubuntu.com/support) 
[    26.106] Current version of pixman: 0.32.6
[    26.106]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    26.106] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    26.106] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 26 19:01:02 2015
[    26.108] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    26.113] (==) No Layout section.  Using the first Screen section.
[    26.113] (==) No screen section available. Using defaults.
[    26.113] (**) |-->Screen "Default Screen Section" (0)
[    26.113] (**) |   |-->Monitor "<default monitor>"
[    26.113] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    26.113] (==) Automatically adding devices
[    26.113] (==) Automatically enabling devices
[    26.113] (==) Automatically adding GPU devices
[    26.116] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    26.116]     Entry deleted from font path.
[    26.116] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    26.116]     Entry deleted from font path.
[    26.116] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    26.116]     Entry deleted from font path.
[    26.117] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    26.117]     Entry deleted from font path.
[    26.117] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    26.117]     Entry deleted from font path.
[    26.117] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    26.117] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    26.117] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    26.117] (II) Loader magic: 0x7fc7f5d45d80
[    26.117] (II) Module ABI versions:
[    26.117]     X.Org ANSI C Emulation: 0.4
[    26.117]     X.Org Video Driver: 19.0
[    26.117]     X.Org XInput driver : 21.0
[    26.117]     X.Org Server Extension : 9.0
[    26.117] (II) xfree86: Adding drm device (/dev/dri/card0)
[    26.119] (--) PCI:*(0:2:0:0) 10de:0845:103c:360a rev 162, Mem @ 0xc1000000/16777216, 0xd0000000/268435456, 0xc4000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/131072
[    26.119] (II) LoadModule: "glx"
[    26.121] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    26.177] (II) Module glx: vendor="X.Org Foundation"
[    26.177]     compiled for 1.17.1, module version = 1.0.0
[    26.177]     ABI class: X.Org Server Extension, version 9.0
[    26.177] (==) AIGLX enabled
[    26.177] (==) Matched nvidia as autoconfigured driver 0
[    26.177] (==) Matched nouveau as autoconfigured driver 1
[    26.177] (==) Matched nvidia as autoconfigured driver 2
[    26.177] (==) Matched nouveau as autoconfigured driver 3
[    26.177] (==) Matched modesetting as autoconfigured driver 4
[    26.177] (==) Matched fbdev as autoconfigured driver 5
[    26.177] (==) Matched vesa as autoconfigured driver 6
[    26.177] (==) Assigned the driver to the xf86ConfigLayout
[    26.177] (II) LoadModule: "nvidia"
[    26.178] (WW) Warning, couldn't open module nvidia
[    26.178] (II) UnloadModule: "nvidia"
[    26.178] (II) Unloading nvidia
[    26.178] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    26.178] (II) LoadModule: "nouveau"
[    26.178] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    26.192] (II) Module nouveau: vendor="X.Org Foundation"
[    26.192]     compiled for 1.17.1, module version = 1.0.11
[    26.192]     Module class: X.Org Video Driver
[    26.192]     ABI class: X.Org Video Driver, version 19.0
[    26.192] (II) LoadModule: "modesetting"
[    26.192] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.197] (II) Module modesetting: vendor="X.Org Foundation"
[    26.197]     compiled for 1.17.1, module version = 1.17.1
[    26.197]     Module class: X.Org Video Driver
[    26.197]     ABI class: X.Org Video Driver, version 19.0
[    26.197] (II) LoadModule: "fbdev"
[    26.197] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.201] (II) Module fbdev: vendor="X.Org Foundation"
[    26.201]     compiled for 1.17.1, module version = 0.4.4
[    26.201]     Module class: X.Org Video Driver
[    26.201]     ABI class: X.Org Video Driver, version 19.0
[    26.201] (II) LoadModule: "vesa"
[    26.201] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.206] (II) Module vesa: vendor="X.Org Foundation"
[    26.206]     compiled for 1.17.1, module version = 2.3.3
[    26.206]     Module class: X.Org Video Driver
[    26.206]     ABI class: X.Org Video Driver, version 19.0
[    26.206] (==) Matched nvidia as autoconfigured driver 0
[    26.206] (==) Matched nouveau as autoconfigured driver 1
[    26.206] (==) Matched nvidia as autoconfigured driver 2
[    26.206] (==) Matched nouveau as autoconfigured driver 3
[    26.206] (==) Matched modesetting as autoconfigured driver 4
[    26.206] (==) Matched fbdev as autoconfigured driver 5
[    26.206] (==) Matched vesa as autoconfigured driver 6
[    26.206] (==) Assigned the driver to the xf86ConfigLayout
[    26.206] (II) LoadModule: "nvidia"
[    26.207] (WW) Warning, couldn't open module nvidia
[    26.207] (II) UnloadModule: "nvidia"
[    26.207] (II) Unloading nvidia
[    26.207] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    26.207] (II) LoadModule: "nouveau"
[    26.207] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    26.207] (II) Module nouveau: vendor="X.Org Foundation"
[    26.207]     compiled for 1.17.1, module version = 1.0.11
[    26.207]     Module class: X.Org Video Driver
[    26.207]     ABI class: X.Org Video Driver, version 19.0
[    26.207] (II) UnloadModule: "nouveau"
[    26.207] (II) Unloading nouveau
[    26.207] (II) Failed to load module "nouveau" (already loaded, 0)
[    26.207] (II) LoadModule: "modesetting"
[    26.207] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    26.208] (II) Module modesetting: vendor="X.Org Foundation"
[    26.208]     compiled for 1.17.1, module version = 1.17.1
[    26.208]     Module class: X.Org Video Driver
[    26.208]     ABI class: X.Org Video Driver, version 19.0
[    26.208] (II) UnloadModule: "modesetting"
[    26.208] (II) Unloading modesetting
[    26.208] (II) Failed to load module "modesetting" (already loaded, 0)
[    26.208] (II) LoadModule: "fbdev"
[    26.208] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    26.208] (II) Module fbdev: vendor="X.Org Foundation"
[    26.208]     compiled for 1.17.1, module version = 0.4.4
[    26.208]     Module class: X.Org Video Driver
[    26.208]     ABI class: X.Org Video Driver, version 19.0
[    26.208] (II) UnloadModule: "fbdev"
[    26.208] (II) Unloading fbdev
[    26.208] (II) Failed to load module "fbdev" (already loaded, 0)
[    26.208] (II) LoadModule: "vesa"
[    26.208] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    26.208] (II) Module vesa: vendor="X.Org Foundation"
[    26.208]     compiled for 1.17.1, module version = 2.3.3
[    26.208]     Module class: X.Org Video Driver
[    26.208]     ABI class: X.Org Video Driver, version 19.0
[    26.208] (II) UnloadModule: "vesa"
[    26.208] (II) Unloading vesa
[    26.208] (II) Failed to load module "vesa" (already loaded, 0)
[    26.208] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    26.208] (II) NOUVEAU driver for NVIDIA chipset families :
[    26.208]     RIVA TNT        (NV04)
[    26.208]     RIVA TNT2       (NV05)
[    26.208]     GeForce 256     (NV10)
[    26.208]     GeForce 2       (NV11, NV15)
[    26.208]     GeForce 4MX     (NV17, NV18)
[    26.208]     GeForce 3       (NV20)
[    26.208]     GeForce 4Ti     (NV25, NV28)
[    26.208]     GeForce FX      (NV3x)
[    26.208]     GeForce 6       (NV4x)
[    26.208]     GeForce 7       (G7x)
[    26.208]     GeForce 8       (G8x)
[    26.208]     GeForce GTX 200 (NVA0)
[    26.208]     GeForce GTX 400 (NVC0)
[    26.208] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    26.208] (II) FBDEV: driver for framebuffer: fbdev
[    26.208] (II) VESA: driver for VESA chipsets: vesa
[    26.208] (++) using VT number 7

[    26.210] (II) [drm] nouveau interface version: 1.2.1
[    26.210] (WW) Falling back to old probe method for modesetting
[    26.210] (WW) Falling back to old probe method for fbdev
[    26.210] (II) Loading sub module "fbdevhw"
[    26.210] (II) LoadModule: "fbdevhw"
[    26.211] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    26.212] (II) Module fbdevhw: vendor="X.Org Foundation"
[    26.212]     compiled for 1.17.1, module version = 0.0.2
[    26.212]     ABI class: X.Org Video Driver, version 19.0
[    26.213] (WW) Falling back to old probe method for vesa
[    26.213] (II) Loading sub module "dri2"
[    26.213] (II) LoadModule: "dri2"
[    26.213] (II) Module "dri2" already built-in
[    26.213] (--) NOUVEAU(0): Chipset: "NVIDIA NVAA"
[    26.213] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    26.213] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    26.213] (==) NOUVEAU(0): RGB weight 888
[    26.213] (==) NOUVEAU(0): Default visual is TrueColor
[    26.213] (==) NOUVEAU(0): Using HW cursor
[    26.213] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[    26.213] (==) NOUVEAU(0): Page flipping enabled
[    26.213] (==) NOUVEAU(0): Swap limit set to 1 [Max allowed 2]
[    26.213] (==) NOUVEAU(0): Page flipping synced to vblank by kernel.
[    26.213] (II) NOUVEAU(0): Initializing outputs ...
[    26.244] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[    26.265] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    26.322] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[    26.322] (II) NOUVEAU(0): 3 crtcs needed for screen.
[    26.649] (II) NOUVEAU(0): Allocated crtc nr. 0 to this screen.
[    26.649] (II) NOUVEAU(0): Allocated crtc nr. 1 to this screen.
[    26.681] (II) NOUVEAU(0): EDID for output LVDS-1
[    26.681] (II) NOUVEAU(0): Manufacturer: SEC  Model: 3451  Serial#: 0
[    26.681] (II) NOUVEAU(0): Year: 2008  Week: 0
[    26.681] (II) NOUVEAU(0): EDID Version: 1.3
[    26.681] (II) NOUVEAU(0): Digital Display Input
[    26.681] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    26.681] (II) NOUVEAU(0): Gamma: 2.20
[    26.681] (II) NOUVEAU(0): No DPMS capabilities specified
[    26.681] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.681] (II) NOUVEAU(0): First detailed timing is preferred mode
[    26.681] (II) NOUVEAU(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    26.681] (II) NOUVEAU(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    26.681] (II) NOUVEAU(0): Manufacturer's mask: 0
[    26.681] (II) NOUVEAU(0): Supported detailed timing:
[    26.681] (II) NOUVEAU(0): clock: 69.3 MHz   Image Size:  344 x 194 mm
[    26.681] (II) NOUVEAU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1480 h_border: 0
[    26.681] (II) NOUVEAU(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 780 v_border: 0
[    26.681] (II) NOUVEAU(0): Unknown vendor-specific block f
[    26.681] (II) NOUVEAU(0):  SAMSUNG
[    26.681] (II) NOUVEAU(0):  156AT01-H01
[    26.681] (II) NOUVEAU(0): EDID (in hex):
[    26.681] (II) NOUVEAU(0):     00ffffffffffff004ca3513400000000
[    26.681] (II) NOUVEAU(0):     00120103802213780a87f594574f8c27
[    26.681] (II) NOUVEAU(0):     27505400000001010101010101010101
[    26.681] (II) NOUVEAU(0):     010101010101121b567250000c303020
[    26.681] (II) NOUVEAU(0):     250058c2100000190000000f00000000
[    26.681] (II) NOUVEAU(0):     00000000001eb4027400000000fe0053
[    26.681] (II) NOUVEAU(0):     414d53554e470a2020202020000000fe
[    26.681] (II) NOUVEAU(0):     00313536415430312d4830310a20001b
[    26.681] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[    26.681] (II) NOUVEAU(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    26.682] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz e)
[    26.682] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[    26.682] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[    26.682] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[    26.682] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[    26.682] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[    26.703] (II) NOUVEAU(0): EDID for output VGA-1
[    26.760] (II) NOUVEAU(0): EDID for output HDMI-1
[    26.760] (II) NOUVEAU(0): Manufacturer: MEI  Model: a296  Serial#: 16843009
[    26.760] (II) NOUVEAU(0): Year: 2013  Week: 0
[    26.760] (II) NOUVEAU(0): EDID Version: 1.3
[    26.760] (II) NOUVEAU(0): Digital Display Input
[    26.760] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 128  vert.: 72
[    26.760] (II) NOUVEAU(0): Gamma: 2.20
[    26.760] (II) NOUVEAU(0): No DPMS capabilities specified
[    26.760] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[    26.760] (II) NOUVEAU(0): First detailed timing is preferred mode
[    26.760] (II) NOUVEAU(0): redX: 0.640 redY: 0.345   greenX: 0.291 greenY: 0.635
[    26.760] (II) NOUVEAU(0): blueX: 0.163 blueY: 0.093   whiteX: 0.288 whiteY: 0.296
[    26.760] (II) NOUVEAU(0): Supported established timings:
[    26.760] (II) NOUVEAU(0): 640x480@60Hz
[    26.760] (II) NOUVEAU(0): 800x600@60Hz
[    26.760] (II) NOUVEAU(0): 1024x768@60Hz
[    26.760] (II) NOUVEAU(0): Manufacturer's mask: 0
[    26.760] (II) NOUVEAU(0): Supported standard timings:
[    26.760] (II) NOUVEAU(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
[    26.760] (II) NOUVEAU(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    26.760] (II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    26.760] (II) NOUVEAU(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    26.760] (II) NOUVEAU(0): Supported detailed timing:
[    26.760] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    26.760] (II) NOUVEAU(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    26.760] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    26.760] (II) NOUVEAU(0): Supported detailed timing:
[    26.760] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    26.760] (II) NOUVEAU(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    26.760] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    26.760] (II) NOUVEAU(0): Monitor name: Panasonic-TV
[    26.760] (II) NOUVEAU(0): Ranges: V min: 23 V max: 61 Hz, H min: 15 H max: 68 kHz, PixClock max 155 MHz
[    26.760] (II) NOUVEAU(0): Supported detailed timing:
[    26.760] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  698 x 392 mm
[    26.760] (II) NOUVEAU(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    26.760] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    26.760] (II) NOUVEAU(0): Supported detailed timing:
[    26.760] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  698 x 392 mm
[    26.760] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    26.760] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    26.760] (II) NOUVEAU(0): Supported detailed timing:
[    26.760] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    26.760] (II) NOUVEAU(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    26.760] (II) NOUVEAU(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    26.760] (II) NOUVEAU(0): Supported detailed timing:
[    26.760] (II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  698 x 392 mm
[    26.760] (II) NOUVEAU(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[    26.760] (II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[    26.760] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[    26.760] (II) NOUVEAU(0): EDID (in hex):
[    26.760] (II) NOUVEAU(0):     00ffffffffffff0034a996a201010101
[    26.760] (II) NOUVEAU(0):     00170103808048780adaffa3584aa229
[    26.760] (II) NOUVEAU(0):     17494b21080031404540614081800101
[    26.760] (II) NOUVEAU(0):     010101010101011d00bc52d01e20b828
[    26.760] (II) NOUVEAU(0):     5540ba882100001e011d007251d01e20
[    26.760] (II) NOUVEAU(0):     6e285500ba882100001e000000fc0050
[    26.760] (II) NOUVEAU(0):     616e61736f6e69632d54560a000000fd
[    26.760] (II) NOUVEAU(0):     00173d0f440f000a2020202020200129
[    26.760] (II) NOUVEAU(0):     020326f24d93841f1014052021221203
[    26.760] (II) NOUVEAU(0):     16072309070168030c001000b8260fe2
[    26.760] (II) NOUVEAU(0):     004be3051f01023a80d072382d40102c
[    26.760] (II) NOUVEAU(0):     4580ba882100001e023a801871382d40
[    26.760] (II) NOUVEAU(0):     582c4500ba882100001e011d80d0721c
[    26.760] (II) NOUVEAU(0):     1620102c2580ba882100009e662156aa
[    26.760] (II) NOUVEAU(0):     51001e30468f3300ba882100001e0000
[    26.760] (II) NOUVEAU(0):     000000000000000000000000000000a9
[    26.760] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    26.760] (II) NOUVEAU(0): Printing probed modes for output HDMI-1
[    26.760] (II) NOUVEAU(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz eP)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x30.0   74.18  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.7 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1920x1080"x24.0   74.18  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1366x768"x59.8   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    26.760] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    26.760] (II) NOUVEAU(0): Output LVDS-1 connected
[    26.760] (II) NOUVEAU(0): Output VGA-1 disconnected
[    26.760] (II) NOUVEAU(0): Output HDMI-1 connected
[    26.760] (II) NOUVEAU(0): Using exact sizes for initial modes
[    26.760] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1366x768
[    26.760] (II) NOUVEAU(0): Output HDMI-1 using initial mode 1366x768
[    26.760] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    26.760] (--) NOUVEAU(0): Virtual size is 1366x768 (pitch 0)
[    26.760] (**) NOUVEAU(0):  Driver mode "1366x768": 69.3 MHz (scaled from 0.0 MHz), 46.8 kHz, 60.0 Hz
[    26.760] (II) NOUVEAU(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    26.760] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[    26.760] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz e)
[    26.760] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[    26.760] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[    26.760] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[    26.760] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[    26.760] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[    26.760] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[    26.760] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[    26.761] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[    26.761] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[    26.761] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[    26.761] (==) NOUVEAU(0): DPI set to (96, 96)
[    26.761] (II) Loading sub module "fb"
[    26.761] (II) LoadModule: "fb"
[    26.761] (II) Loading /usr/lib/xorg/modules/libfb.so
[    26.763] (II) Module fb: vendor="X.Org Foundation"
[    26.763]     compiled for 1.17.1, module version = 1.0.0
[    26.763]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.763] (II) Loading sub module "shadowfb"
[    26.763] (II) LoadModule: "shadowfb"
[    26.764] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    26.765] (II) Module shadowfb: vendor="X.Org Foundation"
[    26.765]     compiled for 1.17.1, module version = 1.0.0
[    26.765]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.765] (II) UnloadModule: "modesetting"
[    26.765] (II) Unloading modesetting
[    26.765] (II) UnloadModule: "fbdev"
[    26.765] (II) Unloading fbdev
[    26.765] (II) UnloadSubModule: "fbdevhw"
[    26.765] (II) Unloading fbdevhw
[    26.765] (II) UnloadModule: "vesa"
[    26.765] (II) Unloading vesa
[    26.765] (--) Depth 24 pixmap format is 32 bpp
[    26.880] (II) NOUVEAU(0): Channel setup complete.
[    26.898] (EE) NOUVEAU(0): [COPY] failed to allocate class.
[    26.906] (II) NOUVEAU(0): [DRI2] Setup complete
[    26.906] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    26.906] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    26.931] (II) Loading sub module "exa"
[    26.931] (II) LoadModule: "exa"
[    26.931] (II) Loading /usr/lib/xorg/modules/libexa.so
[    26.932] (II) Module exa: vendor="X.Org Foundation"
[    26.932]     compiled for 1.17.1, module version = 2.6.0
[    26.932]     ABI class: X.Org Video Driver, version 19.0
[    26.932] (II) EXA(0): Driver allocated offscreen pixmaps
[    26.932] (II) EXA(0): Driver registered support for the following operations:
[    26.932] (II)         Solid
[    26.932] (II)         Copy
[    26.932] (II)         Composite (RENDER acceleration)
[    26.932] (II)         UploadToScreen
[    26.932] (II)         DownloadFromScreen
[    26.932] (==) NOUVEAU(0): Backing store enabled
[    26.932] (==) NOUVEAU(0): Silken mouse enabled
[    26.932] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    26.932] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    26.932] (==) NOUVEAU(0): DPMS enabled
[    26.932] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.932] (--) RandR disabled
[    26.940] (II) SELinux: Disabled on system
[    27.475] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    27.475] (II) AIGLX: enabled GLX_ARB_create_context
[    27.475] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    27.475] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    27.475] (II) AIGLX: enabled GLX_INTEL_swap_event
[    27.475] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    27.475] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    27.475] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    27.475] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    27.476] (II) AIGLX: Loaded and initialized nouveau
[    27.476] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.479] (II) NOUVEAU(0): NVEnterVT is called.
[    27.572] (II) NOUVEAU(0): Setting screen physical size to 361 x 203
[    27.572] resize called 1366 768
[    27.618] (II) XKB: generating xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.713] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    27.714] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.714] (II) LoadModule: "evdev"
[    27.714] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.724] (II) Module evdev: vendor="X.Org Foundation"
[    27.724]     compiled for 1.16.0, module version = 2.9.0
[    27.724]     Module class: X.Org XInput Driver
[    27.724]     ABI class: X.Org XInput driver, version 21.0
[    27.724] (II) Using input driver 'evdev' for 'Power Button'
[    27.724] (**) Power Button: always reports core events
[    27.724] (**) evdev: Power Button: Device: "/dev/input/event3"
[    27.724] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.724] (--) evdev: Power Button: Found keys
[    27.724] (II) evdev: Power Button: Configuring as keyboard
[    27.724] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    27.724] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.724] (**) Option "xkb_rules" "evdev"
[    27.724] (**) Option "xkb_model" "pc105"
[    27.724] (**) Option "xkb_layout" "us"
[    27.725] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    27.725] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.725] (II) Using input driver 'evdev' for 'Video Bus'
[    27.725] (**) Video Bus: always reports core events
[    27.725] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    27.725] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.725] (--) evdev: Video Bus: Found keys
[    27.725] (II) evdev: Video Bus: Configuring as keyboard
[    27.725] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input11/event5"
[    27.725] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    27.725] (**) Option "xkb_rules" "evdev"
[    27.725] (**) Option "xkb_model" "pc105"
[    27.725] (**) Option "xkb_layout" "us"
[    27.726] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.726] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.726] (II) Using input driver 'evdev' for 'Power Button'
[    27.726] (**) Power Button: always reports core events
[    27.726] (**) evdev: Power Button: Device: "/dev/input/event2"
[    27.726] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.726] (--) evdev: Power Button: Found keys
[    27.726] (II) evdev: Power Button: Configuring as keyboard
[    27.726] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2/event2"
[    27.726] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    27.726] (**) Option "xkb_rules" "evdev"
[    27.726] (**) Option "xkb_model" "pc105"
[    27.726] (**) Option "xkb_layout" "us"
[    27.727] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    27.727] (II) No input driver specified, ignoring this device.
[    27.727] (II) This device may have been added with another device file.
[    27.727] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    27.727] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    27.727] (II) Using input driver 'evdev' for 'Sleep Button'
[    27.727] (**) Sleep Button: always reports core events
[    27.727] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    27.727] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    27.727] (--) evdev: Sleep Button: Found keys
[    27.727] (II) evdev: Sleep Button: Configuring as keyboard
[    27.727] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    27.727] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    27.728] (**) Option "xkb_rules" "evdev"
[    27.728] (**) Option "xkb_model" "pc105"
[    27.728] (**) Option "xkb_layout" "us"
[    27.728] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event6)
[    27.728] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    27.728] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    27.728] (**) Logitech USB Optical Mouse: always reports core events
[    27.728] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event6"
[    27.784] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    27.784] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    27.784] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    27.784] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    27.784] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    27.784] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    27.784] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    27.784] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    27.784] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    27.784] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/0003:046D:C05A.0001/input/input12/event6"
[    27.784] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 10)
[    27.784] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    27.784] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    27.784] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    27.784] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    27.784] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    27.785] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    27.785] (II) No input driver specified, ignoring this device.
[    27.785] (II) This device may have been added with another device file.
[    27.785] (II) config/udev: Adding input device CNF7047 (/dev/input/event8)
[    27.785] (**) CNF7047: Applying InputClass "evdev keyboard catchall"
[    27.785] (II) Using input driver 'evdev' for 'CNF7047'
[    27.785] (**) CNF7047: always reports core events
[    27.785] (**) evdev: CNF7047: Device: "/dev/input/event8"
[    27.785] (--) evdev: CNF7047: Vendor 0x4f2 Product 0xb091
[    27.785] (--) evdev: CNF7047: Found keys
[    27.785] (II) evdev: CNF7047: Configuring as keyboard
[    27.785] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input15/event8"
[    27.785] (II) XINPUT: Adding extended input device "CNF7047" (type: KEYBOARD, id 11)
[    27.785] (**) Option "xkb_rules" "evdev"
[    27.785] (**) Option "xkb_model" "pc105"
[    27.785] (**) Option "xkb_layout" "us"
[    27.786] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event10)
[    27.786] (II) No input driver specified, ignoring this device.
[    27.786] (II) This device may have been added with another device file.
[    27.786] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event11)
[    27.786] (II) No input driver specified, ignoring this device.
[    27.786] (II) This device may have been added with another device file.
[    27.787] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 Phantom (/dev/input/event12)
[    27.787] (II) No input driver specified, ignoring this device.
[    27.787] (II) This device may have been added with another device file.
[    27.787] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    27.787] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.787] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.787] (**) AT Translated Set 2 keyboard: always reports core events
[    27.787] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    27.788] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.788] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.788] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.788] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    27.788] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    27.788] (**) Option "xkb_rules" "evdev"
[    27.788] (**) Option "xkb_model" "pc105"
[    27.788] (**) Option "xkb_layout" "us"
[    27.788] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    27.788] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    27.788] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    27.788] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    27.788] (II) LoadModule: "synaptics"
[    27.789] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.790] (II) Module synaptics: vendor="X.Org Foundation"
[    27.790]     compiled for 1.16.0, module version = 1.8.99
[    27.790]     Module class: X.Org XInput Driver
[    27.790]     ABI class: X.Org XInput driver, version 21.0
[    27.790] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    27.790] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.790] (**) Option "Device" "/dev/input/event7"
[    27.804] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5592 (res 55)
[    27.804] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4916 (res 107)
[    27.804] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.804] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    27.804] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    27.804] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    27.804] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.804] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.820] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event7"
[    27.820] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    27.820] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    27.820] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    27.820] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[    27.820] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.820] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    27.820] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.820] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.820] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.821] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    27.821] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    27.823] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event9)
[    27.823] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.823] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    27.823] (**) HP WMI hotkeys: always reports core events
[    27.823] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event9"
[    27.823] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    27.823] (--) evdev: HP WMI hotkeys: Found keys
[    27.823] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    27.823] (**) Option "config_info" "udev:/sys/devices/virtual/input/input16/event9"
[    27.823] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 14)
[    27.823] (**) Option "xkb_rules" "evdev"
[    27.823] (**) Option "xkb_model" "pc105"
[    27.824] (**) Option "xkb_layout" "us"
[    29.658] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    29.658] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    29.658] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    29.736] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    29.769] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    29.769] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    29.769] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    29.848] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    29.879] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    29.879] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    29.879] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    29.958] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    30.357] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    30.357] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    30.357] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    30.452] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    30.497] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    30.497] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    30.497] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    30.575] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    30.608] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    30.608] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    30.608] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    30.715] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    30.761] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    30.761] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    30.761] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    30.847] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    30.996] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    30.996] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    30.996] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    31.079] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    31.112] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    31.112] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    31.112] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    31.204] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    31.241] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    31.241] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    31.241] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    31.332] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    31.501] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    31.501] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    31.501] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    31.583] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    31.614] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    31.615] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    31.615] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    31.693] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    31.744] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    31.745] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    31.745] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    31.837] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    32.082] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    32.082] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    32.082] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    32.161] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    32.197] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    32.197] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    32.197] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    32.289] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    32.322] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    32.322] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    32.322] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    32.409] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    32.513] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    32.513] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    32.513] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    32.593] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    32.626] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    32.626] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    32.626] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    32.710] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    32.743] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    32.743] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    32.743] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    32.821] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    34.230] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    34.230] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    34.230] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    34.309] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    53.843] (II) XKB: generating xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    56.245] (II) config/udev: removing device Power Button
[    56.264] (II) evdev: Power Button: Close
[    56.264] (II) UnloadModule: "evdev"
[    56.264] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    56.264] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    56.264] (II) Using input driver 'evdev' for 'Power Button'
[    56.264] (**) Power Button: always reports core events
[    56.264] (**) evdev: Power Button: Device: "/dev/input/event2"
[    56.280] (--) evdev: Power Button: Vendor 0 Product 0x1
[    56.280] (--) evdev: Power Button: Found keys
[    56.280] (II) evdev: Power Button: Configuring as keyboard
[    56.280] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2/event2"
[    56.280] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    56.280] (**) Option "xkb_rules" "evdev"
[    56.280] (**) Option "xkb_model" "pc105"
[    56.280] (**) Option "xkb_layout" "it"
[    56.282] (II) XKB: reuse xkmfile /var/lib/xkb/server-3781FECB9CB8D26EE03343DB2C93394EA704B98F.xkm
[    56.285] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse0)
[    56.285] (II) No input driver specified, ignoring this device.
[    56.285] (II) This device may have been added with another device file.
[    56.285] (II) config/udev: removing device CNF7047
[    56.344] (II) evdev: CNF7047: Close
[    56.344] (II) UnloadModule: "evdev"
[    56.344] (II) config/udev: Adding input device CNF7047 (/dev/input/event8)
[    56.344] (**) CNF7047: Applying InputClass "evdev keyboard catchall"
[    56.344] (II) Using input driver 'evdev' for 'CNF7047'
[    56.344] (**) CNF7047: always reports core events
[    56.344] (**) evdev: CNF7047: Device: "/dev/input/event8"
[    56.344] (--) evdev: CNF7047: Vendor 0x4f2 Product 0xb091
[    56.344] (--) evdev: CNF7047: Found keys
[    56.344] (II) evdev: CNF7047: Configuring as keyboard
[    56.344] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input15/event8"
[    56.344] (II) XINPUT: Adding extended input device "CNF7047" (type: KEYBOARD, id 11)
[    56.344] (**) Option "xkb_rules" "evdev"
[    56.344] (**) Option "xkb_model" "pc105"
[    56.344] (**) Option "xkb_layout" "it"
[    56.346] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse1)
[    56.346] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    56.346] (II) config/udev: removing device Video Bus
[    56.380] (II) evdev: Video Bus: Close
[    56.380] (II) UnloadModule: "evdev"
[    56.380] (II) config/udev: Adding input device Video Bus (/dev/input/event5)
[    56.380] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    56.380] (II) Using input driver 'evdev' for 'Video Bus'
[    56.380] (**) Video Bus: always reports core events
[    56.380] (**) evdev: Video Bus: Device: "/dev/input/event5"
[    56.380] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    56.380] (--) evdev: Video Bus: Found keys
[    56.380] (II) evdev: Video Bus: Configuring as keyboard
[    56.380] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input11/event5"
[    56.380] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    56.380] (**) Option "xkb_rules" "evdev"
[    56.380] (**) Option "xkb_model" "pc105"
[    56.380] (**) Option "xkb_layout" "it"
[    56.382] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    56.382] (II) No input driver specified, ignoring this device.
[    56.382] (II) This device may have been added with another device file.
[    56.382] (II) config/udev: removing device Power Button
[    56.392] (II) evdev: Power Button: Close
[    56.392] (II) UnloadModule: "evdev"
[    56.392] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    56.392] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    56.392] (II) Using input driver 'evdev' for 'Power Button'
[    56.392] (**) Power Button: always reports core events
[    56.392] (**) evdev: Power Button: Device: "/dev/input/event3"
[    56.392] (--) evdev: Power Button: Vendor 0 Product 0x1
[    56.392] (--) evdev: Power Button: Found keys
[    56.392] (II) evdev: Power Button: Configuring as keyboard
[    56.392] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    56.392] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    56.392] (**) Option "xkb_rules" "evdev"
[    56.392] (**) Option "xkb_model" "pc105"
[    56.392] (**) Option "xkb_layout" "it"
[    56.393] (II) config/udev: removing device Logitech USB Optical Mouse
[    56.468] (II) evdev: Logitech USB Optical Mouse: Close
[    56.468] (II) UnloadModule: "evdev"
[    56.468] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event6)
[    56.468] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    56.468] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    56.468] (**) Logitech USB Optical Mouse: always reports core events
[    56.468] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event6"
[    56.524] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    56.524] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    56.524] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    56.524] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    56.524] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    56.524] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    56.524] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    56.524] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    56.524] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    56.524] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/0003:046D:C05A.0001/input/input12/event6"
[    56.524] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 10)
[    56.524] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    56.524] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    56.524] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    56.524] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    56.524] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    56.525] (II) config/udev: removing device Sleep Button
[    56.536] (II) evdev: Sleep Button: Close
[    56.536] (II) UnloadModule: "evdev"
[    56.536] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    56.536] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    56.536] (II) Using input driver 'evdev' for 'Sleep Button'
[    56.536] (**) Sleep Button: always reports core events
[    56.536] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    56.536] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    56.536] (--) evdev: Sleep Button: Found keys
[    56.536] (II) evdev: Sleep Button: Configuring as keyboard
[    56.536] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    56.536] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    56.536] (**) Option "xkb_rules" "evdev"
[    56.536] (**) Option "xkb_model" "pc105"
[    56.536] (**) Option "xkb_layout" "it"
[    56.537] (II) config/udev: removing device SynPS/2 Synaptics TouchPad
[    56.560] (II) UnloadModule: "synaptics"
[    56.560] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event7)
[    56.560] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    56.560] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    56.560] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    56.560] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    56.560] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    56.560] (**) Option "Device" "/dev/input/event7"
[    56.596] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5592 (res 55)
[    56.596] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4916 (res 107)
[    56.596] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    56.596] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    56.596] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    56.596] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    56.596] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    56.596] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    56.628] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event7"
[    56.628] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 13)
[    56.628] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    56.628] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    56.628] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[    56.628] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    56.628] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    56.628] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    56.628] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    56.628] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    56.629] (II) config/udev: removing device HP WMI hotkeys
[    56.664] (II) evdev: HP WMI hotkeys: Close
[    56.664] (II) UnloadModule: "evdev"
[    56.664] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event9)
[    56.664] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    56.664] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    56.664] (**) HP WMI hotkeys: always reports core events
[    56.664] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event9"
[    56.664] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    56.664] (--) evdev: HP WMI hotkeys: Found keys
[    56.664] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    56.664] (**) Option "config_info" "udev:/sys/devices/virtual/input/input16/event9"
[    56.664] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 14)
[    56.664] (**) Option "xkb_rules" "evdev"
[    56.664] (**) Option "xkb_model" "pc105"
[    56.664] (**) Option "xkb_layout" "it"
[    56.666] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event10)
[    56.666] (II) No input driver specified, ignoring this device.
[    56.666] (II) This device may have been added with another device file.
[    56.666] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event11)
[    56.666] (II) No input driver specified, ignoring this device.
[    56.666] (II) This device may have been added with another device file.
[    56.666] (II) config/udev: removing device AT Translated Set 2 keyboard
[    56.700] (II) evdev: AT Translated Set 2 keyboard: Close
[    56.700] (II) UnloadModule: "evdev"
[    56.700] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    56.700] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    56.700] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    56.700] (**) AT Translated Set 2 keyboard: always reports core events
[    56.700] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    56.700] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    56.700] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    56.700] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    56.700] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    56.700] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[    56.700] (**) Option "xkb_rules" "evdev"
[    56.700] (**) Option "xkb_model" "pc105"
[    56.700] (**) Option "xkb_layout" "it"
[    56.702] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 Phantom (/dev/input/event12)
[    56.702] (II) No input driver specified, ignoring this device.
[    56.702] (II) This device may have been added with another device file.

``` 


[SIZE=6]
[SIZE=5]_**Boot from HD installation(Ubuntu MATE):**_[/SIZE][/SIZE]

_**Output of lsmod command:**_

```
antonio@antonio-Compaq-Presario-CQ60-Notebook-PC:~$ lsmod
Module                  Size  Used by
hid_generic            16384  0
usbhid                 53248  0
hid                   110592  2 hid_generic,usbhid
ctr                    16384  2
ccm                    20480  2
snd_hda_codec_hdmi     53248  1
snd_hda_codec_conexant    24576  1
snd_hda_codec_generic    69632  1 snd_hda_codec_conexant
arc4                   16384  2
uvcvideo               90112  0
hp_wmi                 16384  0
videobuf2_vmalloc      16384  1 uvcvideo
sparse_keymap          16384  1 hp_wmi
nouveau              1400832  2
ath5k                 151552  0
snd_hda_intel          36864  4 snd_hda_codec_hdmi
videobuf2_memops       16384  1 videobuf2_vmalloc
ath                    32768  1 ath5k
mxm_wmi                16384  1 nouveau
snd_hda_controller     32768  1 snd_hda_intel
mac80211              724992  1 ath5k
videobuf2_core         49152  1 uvcvideo
v4l2_common            16384  1 videobuf2_core
cfg80211              540672  3 ath,ath5k,mac80211
videodev              159744  3 uvcvideo,v4l2_common,videobuf2_core
ttm                    98304  1 nouveau
drm_kms_helper        131072  1 nouveau
snd_hda_codec         143360  5 snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_hda_codec_generic,snd_hda_intel,snd_hda_controller
media                  24576  2 uvcvideo,videodev
drm                   348160  5 ttm,drm_kms_helper,nouveau
snd_hwdep              20480  1 snd_hda_codec
i2c_algo_bit           16384  1 nouveau
snd_pcm               106496  4 snd_hda_codec_hdmi,snd_hda_codec,snd_hda_intel,snd_hda_controller
snd_seq_midi           16384  0
snd_seq_midi_event     16384  1 snd_seq_midi
kvm                   483328  0
snd_rawmidi            32768  1 snd_seq_midi
snd_seq                69632  2 snd_seq_midi_event,snd_seq_midi
joydev                 20480  0
serio_raw              16384  0
shpchp                 40960  0
snd_seq_device         16384  3 snd_seq,snd_rawmidi,snd_seq_midi
snd_timer              32768  2 snd_pcm,snd_seq
snd                    90112  17 snd_hwdep,snd_timer,snd_hda_codec_hdmi,snd_hda_codec_conexant,snd_pcm,snd_seq,snd_rawmidi,snd_hda_codec_generic,snd_hda_codec,snd_hda_intel,snd_seq_device
soundcore              16384  2 snd,snd_hda_codec
video                  20480  1 nouveau
k10temp                16384  0
wmi                    20480  3 hp_wmi,mxm_wmi,nouveau
i2c_nforce2            16384  0
mac_hid                16384  0
parport_pc             32768  0
ppdev                  20480  0
lp                     20480  0
parport                45056  3 lp,ppdev,parport_pc
autofs4                40960  2
pata_acpi              16384  0
ums_realtek            20480  0
uas                    24576  0
usb_storage            69632  2 uas,ums_realtek
psmouse               118784  0
forcedeth              69632  0
ahci                   36864  2
libahci                32768  1 ahci
pata_amd               20480  0
antonio@antonio-Compaq-Presario-CQ60-Notebook-PC:~$


```


**_Output of lspci | grep VGA:_**

```
antonio@antonio-Compaq-Presario-CQ60-Notebook-PC:~$ lspci | grep VGA
02:00.0 VGA compatible controller: NVIDIA Corporation C77 [GeForce 8200M G] (rev a2)
antonio@antonio-Compaq-Presario-CQ60-Notebook-PC:~$


```


**_This is the content of Xorg.0.log files:_**

```
[    24.351]
X.Org X Server 1.17.1
Release Date: 2015-02-10
[    24.351] X Protocol Version 11, Revision 0
[    24.351] Build Operating System: Linux 3.19.0-28-generic x86_64 Ubuntu
[    24.351] Current Operating System: Linux antonio-Compaq-Presario-CQ60-Notebook-PC 3.19.0-31-generic #36-Ubuntu SMP Wed Oct 7 15:04:02 UTC 2015 x86_64
[    24.352] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.19.0-31-generic root=UUID=74099468-69f8-40a4-bc18-8c92ff037383 ro persistent quiet splash vt.handoff=7
[    24.352] Build Date: 11 September 2015  10:30:58AM
[    24.352] xorg-server 2:1.17.1-0ubuntu3.1 (For technical support please see http://www.ubuntu.com/support)
[    24.352] Current version of pixman: 0.32.6
[    24.352]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    24.352] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    24.352] (==) Log file: "/var/log/Xorg.0.log", Time: Mon Oct 26 19:47:24 2015
[    24.468] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    24.868] (==) No Layout section.  Using the first Screen section.
[    24.869] (==) No screen section available. Using defaults.
[    24.869] (**) |-->Screen "Default Screen Section" (0)
[    24.869] (**) |   |-->Monitor "<default monitor>"
[    24.869] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    24.869] (==) Automatically adding devices
[    24.869] (==) Automatically enabling devices
[    24.869] (==) Automatically adding GPU devices
[    24.939] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    24.939]     Entry deleted from font path.
[    24.939] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    24.939]     Entry deleted from font path.
[    24.939] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    24.939]     Entry deleted from font path.
[    24.939] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    24.939]     Entry deleted from font path.
[    24.939] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    24.939]     Entry deleted from font path.
[    24.939] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    24.939] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    24.939] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    24.984] (II) Loader magic: 0x7f0ef92f0d80
[    24.984] (II) Module ABI versions:
[    24.984]     X.Org ANSI C Emulation: 0.4
[    24.984]     X.Org Video Driver: 19.0
[    24.984]     X.Org XInput driver : 21.0
[    24.984]     X.Org Server Extension : 9.0
[    24.985] (II) xfree86: Adding drm device (/dev/dri/card0)
[    24.987] (--) PCI:*(0:2:0:0) 10de:0845:103c:360a rev 162, Mem @ 0xc1000000/16777216, 0xd0000000/268435456, 0xc4000000/33554432, I/O @ 0x00004000/128, BIOS @ 0x????????/131072
[    24.989] (II) LoadModule: "glx"
[    25.183] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    25.305] (II) Module glx: vendor="X.Org Foundation"
[    25.305]     compiled for 1.17.1, module version = 1.0.0
[    25.305]     ABI class: X.Org Server Extension, version 9.0
[    25.305] (==) AIGLX enabled
[    25.305] (==) Matched nvidia as autoconfigured driver 0
[    25.305] (==) Matched nouveau as autoconfigured driver 1
[    25.305] (==) Matched nvidia as autoconfigured driver 2
[    25.305] (==) Matched nouveau as autoconfigured driver 3
[    25.305] (==) Matched modesetting as autoconfigured driver 4
[    25.305] (==) Matched fbdev as autoconfigured driver 5
[    25.305] (==) Matched vesa as autoconfigured driver 6
[    25.305] (==) Assigned the driver to the xf86ConfigLayout
[    25.305] (II) LoadModule: "nvidia"
[    25.313] (WW) Warning, couldn't open module nvidia
[    25.314] (II) UnloadModule: "nvidia"
[    25.314] (II) Unloading nvidia
[    25.314] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    25.314] (II) LoadModule: "nouveau"
[    25.314] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    25.344] (II) Module nouveau: vendor="X.Org Foundation"
[    25.344]     compiled for 1.17.1, module version = 1.0.11
[    25.344]     Module class: X.Org Video Driver
[    25.344]     ABI class: X.Org Video Driver, version 19.0
[    25.344] (II) LoadModule: "modesetting"
[    25.344] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.370] (II) Module modesetting: vendor="X.Org Foundation"
[    25.370]     compiled for 1.17.1, module version = 1.17.1
[    25.370]     Module class: X.Org Video Driver
[    25.370]     ABI class: X.Org Video Driver, version 19.0
[    25.370] (II) LoadModule: "fbdev"
[    25.370] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.394] (II) Module fbdev: vendor="X.Org Foundation"
[    25.394]     compiled for 1.17.1, module version = 0.4.4
[    25.394]     Module class: X.Org Video Driver
[    25.394]     ABI class: X.Org Video Driver, version 19.0
[    25.394] (II) LoadModule: "vesa"
[    25.394] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.403] (II) Module vesa: vendor="X.Org Foundation"
[    25.403]     compiled for 1.17.1, module version = 2.3.3
[    25.403]     Module class: X.Org Video Driver
[    25.403]     ABI class: X.Org Video Driver, version 19.0
[    25.403] (==) Matched nvidia as autoconfigured driver 0
[    25.403] (==) Matched nouveau as autoconfigured driver 1
[    25.403] (==) Matched nvidia as autoconfigured driver 2
[    25.403] (==) Matched nouveau as autoconfigured driver 3
[    25.403] (==) Matched modesetting as autoconfigured driver 4
[    25.403] (==) Matched fbdev as autoconfigured driver 5
[    25.403] (==) Matched vesa as autoconfigured driver 6
[    25.403] (==) Assigned the driver to the xf86ConfigLayout
[    25.403] (II) LoadModule: "nvidia"
[    25.404] (WW) Warning, couldn't open module nvidia
[    25.404] (II) UnloadModule: "nvidia"
[    25.404] (II) Unloading nvidia
[    25.405] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    25.405] (II) LoadModule: "nouveau"
[    25.405] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    25.405] (II) Module nouveau: vendor="X.Org Foundation"
[    25.405]     compiled for 1.17.1, module version = 1.0.11
[    25.405]     Module class: X.Org Video Driver
[    25.405]     ABI class: X.Org Video Driver, version 19.0
[    25.405] (II) UnloadModule: "nouveau"
[    25.405] (II) Unloading nouveau
[    25.405] (II) Failed to load module "nouveau" (already loaded, 0)
[    25.405] (II) LoadModule: "modesetting"
[    25.405] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    25.406] (II) Module modesetting: vendor="X.Org Foundation"
[    25.406]     compiled for 1.17.1, module version = 1.17.1
[    25.406]     Module class: X.Org Video Driver
[    25.406]     ABI class: X.Org Video Driver, version 19.0
[    25.406] (II) UnloadModule: "modesetting"
[    25.406] (II) Unloading modesetting
[    25.406] (II) Failed to load module "modesetting" (already loaded, 0)
[    25.406] (II) LoadModule: "fbdev"
[    25.406] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    25.406] (II) Module fbdev: vendor="X.Org Foundation"
[    25.406]     compiled for 1.17.1, module version = 0.4.4
[    25.406]     Module class: X.Org Video Driver
[    25.406]     ABI class: X.Org Video Driver, version 19.0
[    25.406] (II) UnloadModule: "fbdev"
[    25.406] (II) Unloading fbdev
[    25.406] (II) Failed to load module "fbdev" (already loaded, 0)
[    25.406] (II) LoadModule: "vesa"
[    25.407] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    25.407] (II) Module vesa: vendor="X.Org Foundation"
[    25.407]     compiled for 1.17.1, module version = 2.3.3
[    25.407]     Module class: X.Org Video Driver
[    25.407]     ABI class: X.Org Video Driver, version 19.0
[    25.407] (II) UnloadModule: "vesa"
[    25.407] (II) Unloading vesa
[    25.407] (II) Failed to load module "vesa" (already loaded, 0)
[    25.407] (II) NOUVEAU driver Date:   Thu Aug 28 03:57:48 2014 +0200
[    25.407] (II) NOUVEAU driver for NVIDIA chipset families :
[    25.407]     RIVA TNT        (NV04)
[    25.407]     RIVA TNT2       (NV05)
[    25.407]     GeForce 256     (NV10)
[    25.407]     GeForce 2       (NV11, NV15)
[    25.407]     GeForce 4MX     (NV17, NV18)
[    25.407]     GeForce 3       (NV20)
[    25.407]     GeForce 4Ti     (NV25, NV28)
[    25.407]     GeForce FX      (NV3x)
[    25.407]     GeForce 6       (NV4x)
[    25.408]     GeForce 7       (G7x)
[    25.408]     GeForce 8       (G8x)
[    25.408]     GeForce GTX 200 (NVA0)
[    25.408]     GeForce GTX 400 (NVC0)
[    25.408] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    25.408] (II) FBDEV: driver for framebuffer: fbdev
[    25.408] (II) VESA: driver for VESA chipsets: vesa
[    25.408] (++) using VT number 7

[    25.409] (II) [drm] nouveau interface version: 1.2.1
[    25.409] (WW) Falling back to old probe method for modesetting
[    25.409] (WW) Falling back to old probe method for fbdev
[    25.409] (II) Loading sub module "fbdevhw"
[    25.409] (II) LoadModule: "fbdevhw"
[    25.410] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    25.428] (II) Module fbdevhw: vendor="X.Org Foundation"
[    25.428]     compiled for 1.17.1, module version = 0.0.2
[    25.428]     ABI class: X.Org Video Driver, version 19.0
[    25.428] (WW) Falling back to old probe method for vesa
[    25.429] (II) Loading sub module "dri2"
[    25.429] (II) LoadModule: "dri2"
[    25.429] (II) Module "dri2" already built-in
[    25.429] (--) NOUVEAU(0): Chipset: "NVIDIA NVAA"
[    25.429] (II) NOUVEAU(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    25.429] (==) NOUVEAU(0): Depth 24, (--) framebuffer bpp 32
[    25.429] (==) NOUVEAU(0): RGB weight 888
[    25.429] (==) NOUVEAU(0): Default visual is TrueColor
[    25.429] (==) NOUVEAU(0): Using HW cursor
[    25.429] (==) NOUVEAU(0): GLX sync to VBlank enabled.
[    25.429] (==) NOUVEAU(0): Page flipping enabled
[    25.429] (==) NOUVEAU(0): Swap limit set to 1 [Max allowed 2]
[    25.429] (==) NOUVEAU(0): Page flipping synced to vblank by kernel.
[    25.429] (II) NOUVEAU(0): Initializing outputs ...
[    25.460] (II) NOUVEAU(0): Output LVDS-1 has no monitor section
[    25.481] (II) NOUVEAU(0): Output VGA-1 has no monitor section
[    25.539] (II) NOUVEAU(0): Output HDMI-1 has no monitor section
[    25.539] (II) NOUVEAU(0): 3 crtcs needed for screen.
[    25.871] (II) NOUVEAU(0): Allocated crtc nr. 0 to this screen.
[    25.871] (II) NOUVEAU(0): Allocated crtc nr. 1 to this screen.
[    25.903] (II) NOUVEAU(0): EDID for output LVDS-1
[    25.903] (II) NOUVEAU(0): Manufacturer: SEC  Model: 3451  Serial#: 0
[    25.903] (II) NOUVEAU(0): Year: 2008  Week: 0
[    25.903] (II) NOUVEAU(0): EDID Version: 1.3
[    25.903] (II) NOUVEAU(0): Digital Display Input
[    25.903] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 34  vert.: 19
[    25.903] (II) NOUVEAU(0): Gamma: 2.20
[    25.903] (II) NOUVEAU(0): No DPMS capabilities specified
[    25.903] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    25.903] (II) NOUVEAU(0): First detailed timing is preferred mode
[    25.903] (II) NOUVEAU(0): redX: 0.580 redY: 0.340   greenX: 0.310 greenY: 0.550
[    25.903] (II) NOUVEAU(0): blueX: 0.155 blueY: 0.155   whiteX: 0.313 whiteY: 0.329
[    25.903] (II) NOUVEAU(0): Manufacturer's mask: 0
[    25.903] (II) NOUVEAU(0): Supported detailed timing:
[    25.903] (II) NOUVEAU(0): clock: 69.3 MHz   Image Size:  344 x 194 mm
[    25.903] (II) NOUVEAU(0): h_active: 1366  h_sync: 1414  h_sync_end 1446 h_blank_end 1480 h_border: 0
[    25.903] (II) NOUVEAU(0): v_active: 768  v_sync: 770  v_sync_end 775 v_blanking: 780 v_border: 0
[    25.904] (II) NOUVEAU(0): Unknown vendor-specific block f
[    25.904] (II) NOUVEAU(0):  SAMSUNG
[    25.904] (II) NOUVEAU(0):  156AT01-H01
[    25.904] (II) NOUVEAU(0): EDID (in hex):
[    25.904] (II) NOUVEAU(0):     00ffffffffffff004ca3513400000000
[    25.904] (II) NOUVEAU(0):     00120103802213780a87f594574f8c27
[    25.904] (II) NOUVEAU(0):     27505400000001010101010101010101
[    25.904] (II) NOUVEAU(0):     010101010101121b567250000c303020
[    25.904] (II) NOUVEAU(0):     250058c2100000190000000f00000000
[    25.904] (II) NOUVEAU(0):     00000000001eb4027400000000fe0053
[    25.904] (II) NOUVEAU(0):     414d53554e470a2020202020000000fe
[    25.904] (II) NOUVEAU(0):     00313536415430312d4830310a20001b
[    25.904] (II) NOUVEAU(0): Printing probed modes for output LVDS-1
[    25.904] (II) NOUVEAU(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    25.904] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz e)
[    25.904] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[    25.904] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[    25.904] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[    25.904] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[    25.904] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[    25.925] (II) NOUVEAU(0): EDID for output VGA-1
[    25.983] (II) NOUVEAU(0): EDID for output HDMI-1
[    25.984] (II) NOUVEAU(0): Manufacturer: MEI  Model: a296  Serial#: 16843009
[    25.984] (II) NOUVEAU(0): Year: 2013  Week: 0
[    25.984] (II) NOUVEAU(0): EDID Version: 1.3
[    25.984] (II) NOUVEAU(0): Digital Display Input
[    25.984] (II) NOUVEAU(0): Max Image Size [cm]: horiz.: 128  vert.: 72
[    25.984] (II) NOUVEAU(0): Gamma: 2.20
[    25.984] (II) NOUVEAU(0): No DPMS capabilities specified
[    25.984] (II) NOUVEAU(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4
[    25.984] (II) NOUVEAU(0): First detailed timing is preferred mode
[    25.984] (II) NOUVEAU(0): redX: 0.640 redY: 0.345   greenX: 0.291 greenY: 0.635
[    25.984] (II) NOUVEAU(0): blueX: 0.163 blueY: 0.093   whiteX: 0.288 whiteY: 0.296
[    25.984] (II) NOUVEAU(0): Supported established timings:
[    25.984] (II) NOUVEAU(0): 640x480@60Hz
[    25.984] (II) NOUVEAU(0): 800x600@60Hz
[    25.984] (II) NOUVEAU(0): 1024x768@60Hz
[    25.984] (II) NOUVEAU(0): Manufacturer's mask: 0
[    25.984] (II) NOUVEAU(0): Supported standard timings:
[    25.984] (II) NOUVEAU(0): #0: hsize: 640  vsize 480  refresh: 60  vid: 16433
[    25.984] (II) NOUVEAU(0): #1: hsize: 800  vsize 600  refresh: 60  vid: 16453
[    25.984] (II) NOUVEAU(0): #2: hsize: 1024  vsize 768  refresh: 60  vid: 16481
[    25.984] (II) NOUVEAU(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[    25.984] (II) NOUVEAU(0): Supported detailed timing:
[    25.984] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    25.984] (II) NOUVEAU(0): h_active: 1280  h_sync: 1720  h_sync_end 1760 h_blank_end 1980 h_border: 0
[    25.984] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    25.984] (II) NOUVEAU(0): Supported detailed timing:
[    25.984] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    25.984] (II) NOUVEAU(0): h_active: 1280  h_sync: 1390  h_sync_end 1430 h_blank_end 1650 h_border: 0
[    25.984] (II) NOUVEAU(0): v_active: 720  v_sync: 725  v_sync_end 730 v_blanking: 750 v_border: 0
[    25.984] (II) NOUVEAU(0): Monitor name: Panasonic-TV
[    25.984] (II) NOUVEAU(0): Ranges: V min: 23 V max: 61 Hz, H min: 15 H max: 68 kHz, PixClock max 155 MHz
[    25.984] (II) NOUVEAU(0): Supported detailed timing:
[    25.984] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  698 x 392 mm
[    25.984] (II) NOUVEAU(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    25.984] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    25.984] (II) NOUVEAU(0): Supported detailed timing:
[    25.985] (II) NOUVEAU(0): clock: 148.5 MHz   Image Size:  698 x 392 mm
[    25.985] (II) NOUVEAU(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[    25.985] (II) NOUVEAU(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[    25.985] (II) NOUVEAU(0): Supported detailed timing:
[    25.985] (II) NOUVEAU(0): clock: 74.2 MHz   Image Size:  698 x 392 mm
[    25.985] (II) NOUVEAU(0): h_active: 1920  h_sync: 2448  h_sync_end 2492 h_blank_end 2640 h_border: 0
[    25.985] (II) NOUVEAU(0): v_active: 540  v_sync: 542  v_sync_end 547 v_blanking: 562 v_border: 0
[    25.985] (II) NOUVEAU(0): Supported detailed timing:
[    25.985] (II) NOUVEAU(0): clock: 85.5 MHz   Image Size:  698 x 392 mm
[    25.985] (II) NOUVEAU(0): h_active: 1366  h_sync: 1436  h_sync_end 1579 h_blank_end 1792 h_border: 0
[    25.985] (II) NOUVEAU(0): v_active: 768  v_sync: 771  v_sync_end 774 v_blanking: 798 v_border: 0
[    25.985] (II) NOUVEAU(0): Number of EDID sections to follow: 1
[    25.985] (II) NOUVEAU(0): EDID (in hex):
[    25.985] (II) NOUVEAU(0):     00ffffffffffff0034a996a201010101
[    25.985] (II) NOUVEAU(0):     00170103808048780adaffa3584aa229
[    25.985] (II) NOUVEAU(0):     17494b21080031404540614081800101
[    25.985] (II) NOUVEAU(0):     010101010101011d00bc52d01e20b828
[    25.985] (II) NOUVEAU(0):     5540ba882100001e011d007251d01e20
[    25.985] (II) NOUVEAU(0):     6e285500ba882100001e000000fc0050
[    25.985] (II) NOUVEAU(0):     616e61736f6e69632d54560a000000fd
[    25.985] (II) NOUVEAU(0):     00173d0f440f000a2020202020200129
[    25.985] (II) NOUVEAU(0):     020326f24d93841f1014052021221203
[    25.985] (II) NOUVEAU(0):     16072309070168030c001000b8260fe2
[    25.985] (II) NOUVEAU(0):     004be3051f01023a80d072382d40102c
[    25.985] (II) NOUVEAU(0):     4580ba882100001e023a801871382d40
[    25.985] (II) NOUVEAU(0):     582c4500ba882100001e011d80d0721c
[    25.985] (II) NOUVEAU(0):     1620102c2580ba882100009e662156aa
[    25.985] (II) NOUVEAU(0):     51001e30468f3300ba882100001e0000
[    25.985] (II) NOUVEAU(0):     000000000000000000000000000000a9
[    25.985] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    25.985] (II) NOUVEAU(0): Printing probed modes for output HDMI-1
[    25.985] (II) NOUVEAU(0): Modeline "1280x720"x50.0   74.25  1280 1720 1760 1980  720 725 730 750 +hsync +vsync (37.5 kHz eP)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x50.0  148.50  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (56.2 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080i"x60.0   74.25  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.8 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080i"x50.0   74.25  1920 2448 2492 2640  1080 1084 1094 1125 interlace +hsync +vsync (28.1 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x30.0   74.25  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.8 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x25.0   74.25  1920 2448 2492 2640  1080 1084 1089 1125 +hsync +vsync (28.1 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x24.0   74.25  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080i"x59.9   74.18  1920 2008 2052 2200  1080 1084 1094 1125 interlace +hsync +vsync (33.7 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x30.0   74.18  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (33.7 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1920x1080"x24.0   74.18  1920 2558 2602 2750  1080 1084 1089 1125 +hsync +vsync (27.0 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1366x768"x59.8   85.50  1366 1436 1579 1792  768 771 774 798 +hsync +vsync (47.7 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1280x720"x60.0   74.25  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1280x720"x59.9   74.18  1280 1390 1430 1650  720 725 730 750 +hsync +vsync (45.0 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "720x576"x50.0   27.00  720 732 796 864  576 581 586 625 -hsync -vsync (31.2 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "720x480"x60.0   27.03  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "720x480"x59.9   27.00  720 736 798 858  480 489 495 525 -hsync -vsync (31.5 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 489 492 525 -hsync -vsync (31.5 kHz e)
[    25.986] (II) NOUVEAU(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[    25.986] (II) NOUVEAU(0): Output LVDS-1 connected
[    25.986] (II) NOUVEAU(0): Output VGA-1 disconnected
[    25.986] (II) NOUVEAU(0): Output HDMI-1 connected
[    25.986] (II) NOUVEAU(0): Using exact sizes for initial modes
[    25.986] (II) NOUVEAU(0): Output LVDS-1 using initial mode 1366x768
[    25.986] (II) NOUVEAU(0): Output HDMI-1 using initial mode 1366x768
[    25.986] (II) NOUVEAU(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[    25.986] (--) NOUVEAU(0): Virtual size is 1366x768 (pitch 0)
[    25.986] (**) NOUVEAU(0):  Driver mode "1366x768": 69.3 MHz (scaled from 0.0 MHz), 46.8 kHz, 60.0 Hz
[    25.987] (II) NOUVEAU(0): Modeline "1366x768"x60.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    25.987] (**) NOUVEAU(0):  Driver mode "1024x768": 63.5 MHz (scaled from 0.0 MHz), 47.8 kHz, 59.9 Hz
[    25.987] (II) NOUVEAU(0): Modeline "1024x768"x59.9   63.50  1024 1072 1176 1328  768 771 775 798 -hsync +vsync (47.8 kHz e)
[    25.987] (**) NOUVEAU(0):  Driver mode "800x600": 38.2 MHz (scaled from 0.0 MHz), 37.4 kHz, 59.9 Hz
[    25.987] (II) NOUVEAU(0): Modeline "800x600"x59.9   38.25  800 832 912 1024  600 603 607 624 -hsync +vsync (37.4 kHz e)
[    25.987] (**) NOUVEAU(0):  Driver mode "640x480": 23.8 MHz (scaled from 0.0 MHz), 29.7 kHz, 59.4 Hz
[    25.987] (II) NOUVEAU(0): Modeline "640x480"x59.4   23.75  640 664 720 800  480 483 487 500 -hsync +vsync (29.7 kHz e)
[    25.987] (**) NOUVEAU(0):  Driver mode "720x400": 22.2 MHz (scaled from 0.0 MHz), 24.8 kHz, 59.6 Hz
[    25.987] (II) NOUVEAU(0): Modeline "720x400"x59.6   22.25  720 744 808 896  400 403 413 417 -hsync +vsync (24.8 kHz e)
[    25.987] (**) NOUVEAU(0):  Driver mode "640x400": 20.0 MHz (scaled from 0.0 MHz), 25.0 kHz, 60.0 Hz
[    25.987] (II) NOUVEAU(0): Modeline "640x400"x60.0   20.00  640 664 720 800  400 403 409 417 -hsync +vsync (25.0 kHz e)
[    25.987] (**) NOUVEAU(0):  Driver mode "640x350": 17.5 MHz (scaled from 0.0 MHz), 21.9 kHz, 59.8 Hz
[    25.987] (II) NOUVEAU(0): Modeline "640x350"x59.8   17.50  640 664 720 800  350 353 363 366 -hsync +vsync (21.9 kHz e)
[    25.987] (==) NOUVEAU(0): DPI set to (96, 96)
[    25.987] (II) Loading sub module "fb"
[    25.987] (II) LoadModule: "fb"
[    25.987] (II) Loading /usr/lib/xorg/modules/libfb.so
[    25.999] (II) Module fb: vendor="X.Org Foundation"
[    25.999]     compiled for 1.17.1, module version = 1.0.0
[    25.999]     ABI class: X.Org ANSI C Emulation, version 0.4
[    25.999] (II) Loading sub module "shadowfb"
[    25.999] (II) LoadModule: "shadowfb"
[    26.000] (II) Loading /usr/lib/xorg/modules/libshadowfb.so
[    26.001] (II) Module shadowfb: vendor="X.Org Foundation"
[    26.001]     compiled for 1.17.1, module version = 1.0.0
[    26.001]     ABI class: X.Org ANSI C Emulation, version 0.4
[    26.001] (II) UnloadModule: "modesetting"
[    26.001] (II) Unloading modesetting
[    26.001] (II) UnloadModule: "fbdev"
[    26.001] (II) Unloading fbdev
[    26.001] (II) UnloadSubModule: "fbdevhw"
[    26.002] (II) Unloading fbdevhw
[    26.002] (II) UnloadModule: "vesa"
[    26.002] (II) Unloading vesa
[    26.002] (--) Depth 24 pixmap format is 32 bpp
[    26.121] (II) NOUVEAU(0): Channel setup complete.
[    26.140] (EE) NOUVEAU(0): [COPY] failed to allocate class.
[    26.191] (II) NOUVEAU(0): [DRI2] Setup complete
[    26.191] (II) NOUVEAU(0): [DRI2]   DRI driver: nouveau
[    26.191] (II) NOUVEAU(0): [DRI2]   VDPAU driver: nouveau
[    26.215] (II) Loading sub module "exa"
[    26.215] (II) LoadModule: "exa"
[    26.216] (II) Loading /usr/lib/xorg/modules/libexa.so
[    26.230] (II) Module exa: vendor="X.Org Foundation"
[    26.230]     compiled for 1.17.1, module version = 2.6.0
[    26.230]     ABI class: X.Org Video Driver, version 19.0
[    26.230] (II) EXA(0): Driver allocated offscreen pixmaps
[    26.230] (II) EXA(0): Driver registered support for the following operations:
[    26.230] (II)         Solid
[    26.230] (II)         Copy
[    26.230] (II)         Composite (RENDER acceleration)
[    26.230] (II)         UploadToScreen
[    26.230] (II)         DownloadFromScreen
[    26.230] (==) NOUVEAU(0): Backing store enabled
[    26.230] (==) NOUVEAU(0): Silken mouse enabled
[    26.231] (II) NOUVEAU(0): [XvMC] Associated with Nouveau GeForce 8/9 Textured Video.
[    26.231] (II) NOUVEAU(0): [XvMC] Extension initialized.
[    26.231] (==) NOUVEAU(0): DPMS enabled
[    26.231] (II) NOUVEAU(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    26.233] (--) RandR disabled
[    26.245] (II) SELinux: Disabled on system
[    27.151] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[    27.151] (II) AIGLX: enabled GLX_ARB_create_context
[    27.151] (II) AIGLX: enabled GLX_ARB_create_context_profile
[    27.151] (II) AIGLX: enabled GLX_EXT_create_context_es2_profile
[    27.151] (II) AIGLX: enabled GLX_INTEL_swap_event
[    27.151] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[    27.151] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[    27.151] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[    27.151] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[    27.153] (II) AIGLX: Loaded and initialized nouveau
[    27.153] (II) GLX: Initialized DRI2 GL provider for screen 0
[    27.242] (II) NOUVEAU(0): NVEnterVT is called.
[    27.600] (II) NOUVEAU(0): Setting screen physical size to 361 x 203
[    27.600] resize called 1366 768
[    27.779] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[    27.791] (II) config/udev: Adding input device Power Button (/dev/input/event3)
[    27.791] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.791] (**) Power Button: Applying InputClass "keyboard defaults"
[    27.791] (II) LoadModule: "evdev"
[    27.791] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[    27.821] (II) Module evdev: vendor="X.Org Foundation"
[    27.821]     compiled for 1.16.0, module version = 2.9.0
[    27.821]     Module class: X.Org XInput Driver
[    27.821]     ABI class: X.Org XInput driver, version 21.0
[    27.821] (II) Using input driver 'evdev' for 'Power Button'
[    27.821] (**) Power Button: always reports core events
[    27.821] (**) evdev: Power Button: Device: "/dev/input/event3"
[    27.821] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.821] (--) evdev: Power Button: Found keys
[    27.821] (II) evdev: Power Button: Configuring as keyboard
[    27.821] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input3/event3"
[    27.821] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[    27.821] (**) Option "xkb_rules" "evdev"
[    27.821] (**) Option "xkb_model" "pc105"
[    27.821] (**) Option "xkb_layout" "it"
[    27.821] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    27.824] (II) XKB: reuse xkmfile /var/lib/xkb/server-CE9E112D708AAFA2376E65C27974ED1D649E43E2.xkm
[    27.842] (II) config/udev: Adding input device Video Bus (/dev/input/event6)
[    27.842] (**) Video Bus: Applying InputClass "evdev keyboard catchall"
[    27.842] (**) Video Bus: Applying InputClass "keyboard defaults"
[    27.842] (II) Using input driver 'evdev' for 'Video Bus'
[    27.842] (**) Video Bus: always reports core events
[    27.842] (**) evdev: Video Bus: Device: "/dev/input/event6"
[    27.842] (--) evdev: Video Bus: Vendor 0 Product 0x6
[    27.842] (--) evdev: Video Bus: Found keys
[    27.842] (II) evdev: Video Bus: Configuring as keyboard
[    27.842] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:0f/LNXVIDEO:00/input/input13/event6"
[    27.842] (II) XINPUT: Adding extended input device "Video Bus" (type: KEYBOARD, id 7)
[    27.842] (**) Option "xkb_rules" "evdev"
[    27.842] (**) Option "xkb_model" "pc105"
[    27.842] (**) Option "xkb_layout" "it"
[    27.842] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    27.844] (II) config/udev: Adding input device Power Button (/dev/input/event2)
[    27.844] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[    27.844] (**) Power Button: Applying InputClass "keyboard defaults"
[    27.844] (II) Using input driver 'evdev' for 'Power Button'
[    27.844] (**) Power Button: always reports core events
[    27.844] (**) evdev: Power Button: Device: "/dev/input/event2"
[    27.844] (--) evdev: Power Button: Vendor 0 Product 0x1
[    27.844] (--) evdev: Power Button: Found keys
[    27.844] (II) evdev: Power Button: Configuring as keyboard
[    27.844] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input2/event2"
[    27.844] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 8)
[    27.844] (**) Option "xkb_rules" "evdev"
[    27.844] (**) Option "xkb_model" "pc105"
[    27.844] (**) Option "xkb_layout" "it"
[    27.844] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    27.846] (II) config/udev: Adding input device Lid Switch (/dev/input/event0)
[    27.846] (II) No input driver specified, ignoring this device.
[    27.846] (II) This device may have been added with another device file.
[    27.846] (II) config/udev: Adding input device Sleep Button (/dev/input/event1)
[    27.846] (**) Sleep Button: Applying InputClass "evdev keyboard catchall"
[    27.846] (**) Sleep Button: Applying InputClass "keyboard defaults"
[    27.846] (II) Using input driver 'evdev' for 'Sleep Button'
[    27.846] (**) Sleep Button: always reports core events
[    27.846] (**) evdev: Sleep Button: Device: "/dev/input/event1"
[    27.846] (--) evdev: Sleep Button: Vendor 0 Product 0x3
[    27.847] (--) evdev: Sleep Button: Found keys
[    27.847] (II) evdev: Sleep Button: Configuring as keyboard
[    27.847] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input1/event1"
[    27.847] (II) XINPUT: Adding extended input device "Sleep Button" (type: KEYBOARD, id 9)
[    27.847] (**) Option "xkb_rules" "evdev"
[    27.847] (**) Option "xkb_model" "pc105"
[    27.847] (**) Option "xkb_layout" "it"
[    27.847] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    27.848] (II) config/udev: Adding input device CNF7047 (/dev/input/event8)
[    27.848] (**) CNF7047: Applying InputClass "evdev keyboard catchall"
[    27.848] (**) CNF7047: Applying InputClass "keyboard defaults"
[    27.848] (II) Using input driver 'evdev' for 'CNF7047'
[    27.848] (**) CNF7047: always reports core events
[    27.848] (**) evdev: CNF7047: Device: "/dev/input/event8"
[    27.848] (--) evdev: CNF7047: Vendor 0x4f2 Product 0xb091
[    27.848] (--) evdev: CNF7047: Found keys
[    27.848] (II) evdev: CNF7047: Configuring as keyboard
[    27.848] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.1/usb2/2-2/2-2:1.0/input/input15/event8"
[    27.848] (II) XINPUT: Adding extended input device "CNF7047" (type: KEYBOARD, id 10)
[    27.848] (**) Option "xkb_rules" "evdev"
[    27.848] (**) Option "xkb_model" "pc105"
[    27.848] (**) Option "xkb_layout" "it"
[    27.848] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    27.849] (II) config/udev: Adding input device HDA NVidia Mic (/dev/input/event9)
[    27.849] (II) No input driver specified, ignoring this device.
[    27.849] (II) This device may have been added with another device file.
[    27.849] (II) config/udev: Adding input device HDA NVidia Headphone (/dev/input/event10)
[    27.849] (II) No input driver specified, ignoring this device.
[    27.849] (II) This device may have been added with another device file.
[    27.850] (II) config/udev: Adding input device HDA NVidia HDMI/DP,pcm=3 Phantom (/dev/input/event11)
[    27.850] (II) No input driver specified, ignoring this device.
[    27.850] (II) This device may have been added with another device file.
[    27.850] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event4)
[    27.850] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[    27.851] (**) AT Translated Set 2 keyboard: Applying InputClass "keyboard defaults"
[    27.851] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[    27.851] (**) AT Translated Set 2 keyboard: always reports core events
[    27.851] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event4"
[    27.851] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[    27.851] (--) evdev: AT Translated Set 2 keyboard: Found keys
[    27.851] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[    27.851] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input4/event4"
[    27.851] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 11)
[    27.851] (**) Option "xkb_rules" "evdev"
[    27.851] (**) Option "xkb_model" "pc105"
[    27.851] (**) Option "xkb_layout" "it"
[    27.851] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    27.852] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/event5)
[    27.852] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "evdev touchpad catchall"
[    27.852] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "touchpad catchall"
[    27.852] (**) SynPS/2 Synaptics TouchPad: Applying InputClass "Default clickpad buttons"
[    27.852] (II) LoadModule: "synaptics"
[    27.852] (II) Loading /usr/lib/xorg/modules/input/synaptics_drv.so
[    27.874] (II) Module synaptics: vendor="X.Org Foundation"
[    27.875]     compiled for 1.16.0, module version = 1.8.99
[    27.875]     Module class: X.Org XInput Driver
[    27.875]     ABI class: X.Org XInput driver, version 21.0
[    27.875] (II) Using input driver 'synaptics' for 'SynPS/2 Synaptics TouchPad'
[    27.875] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.875] (**) Option "Device" "/dev/input/event5"
[    27.888] (--) synaptics: SynPS/2 Synaptics TouchPad: x-axis range 1472 - 5592 (res 55)
[    27.888] (--) synaptics: SynPS/2 Synaptics TouchPad: y-axis range 1408 - 4916 (res 107)
[    27.888] (--) synaptics: SynPS/2 Synaptics TouchPad: pressure range 0 - 255
[    27.888] (--) synaptics: SynPS/2 Synaptics TouchPad: finger width range 0 - 15
[    27.888] (--) synaptics: SynPS/2 Synaptics TouchPad: buttons: left right
[    27.888] (--) synaptics: SynPS/2 Synaptics TouchPad: Vendor 0x2 Product 0x7
[    27.888] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.888] (**) SynPS/2 Synaptics TouchPad: always reports core events
[    27.904] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio2/input/input10/event5"
[    27.904] (II) XINPUT: Adding extended input device "SynPS/2 Synaptics TouchPad" (type: TOUCHPAD, id 12)
[    27.904] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MinSpeed is now constant deceleration 2.5
[    27.904] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) MaxSpeed is now 1.75
[    27.904] (**) synaptics: SynPS/2 Synaptics TouchPad: (accel) AccelFactor is now 0.037
[    27.905] (**) SynPS/2 Synaptics TouchPad: (accel) keeping acceleration scheme 1
[    27.905] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration profile 1
[    27.905] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration factor: 2.000
[    27.905] (**) SynPS/2 Synaptics TouchPad: (accel) acceleration threshold: 4
[    27.905] (--) synaptics: SynPS/2 Synaptics TouchPad: touchpad found
[    27.906] (II) config/udev: Adding input device SynPS/2 Synaptics TouchPad (/dev/input/mouse0)
[    27.906] (**) SynPS/2 Synaptics TouchPad: Ignoring device from InputClass "touchpad ignore duplicates"
[    27.911] (II) config/udev: Adding input device HP WMI hotkeys (/dev/input/event7)
[    27.911] (**) HP WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[    27.911] (**) HP WMI hotkeys: Applying InputClass "keyboard defaults"
[    27.911] (II) Using input driver 'evdev' for 'HP WMI hotkeys'
[    27.911] (**) HP WMI hotkeys: always reports core events
[    27.911] (**) evdev: HP WMI hotkeys: Device: "/dev/input/event7"
[    27.911] (--) evdev: HP WMI hotkeys: Vendor 0 Product 0
[    27.911] (--) evdev: HP WMI hotkeys: Found keys
[    27.911] (II) evdev: HP WMI hotkeys: Configuring as keyboard
[    27.911] (**) Option "config_info" "udev:/sys/devices/virtual/input/input14/event7"
[    27.911] (II) XINPUT: Adding extended input device "HP WMI hotkeys" (type: KEYBOARD, id 13)
[    27.911] (**) Option "xkb_rules" "evdev"
[    27.911] (**) Option "xkb_model" "pc105"
[    27.911] (**) Option "xkb_layout" "it"
[    27.911] (**) Option "xkb_options" "terminate:ctrl_alt_bksp"
[    38.024] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[    38.024] (II) No input driver specified, ignoring this device.
[    38.024] (II) This device may have been added with another device file.
[    38.095] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event12)
[    38.095] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[    38.095] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[    38.095] (**) Logitech USB Optical Mouse: always reports core events
[    38.095] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event12"
[    38.148] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[    38.148] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[    38.148] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[    38.148] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[    38.148] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[    38.148] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[    38.148] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[    38.148] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[    38.148] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[    38.148] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/0003:046D:C05A.0001/input/input19/event12"
[    38.148] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 14)
[    38.148] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[    38.149] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[    38.149] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[    38.149] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[    38.149] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
[    45.042] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    45.042] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    45.042] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    45.120] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    45.243] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    45.243] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    45.243] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    45.322] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    45.499] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    45.500] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    45.500] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    45.580] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    45.712] resize called 2732 768
[    47.176] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    47.176] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    47.176] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    47.255] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    70.099] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    70.100] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    70.100] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    70.185] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    75.790] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    75.790] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    75.790] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    75.869] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    76.008] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    76.008] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    76.008] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    76.087] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    76.192] resize called 1366 768
[    83.603] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    83.604] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    83.604] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    83.683] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    83.815] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    83.815] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    83.815] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    83.894] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    83.995] resize called 1366 768
[    88.470] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    88.470] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    88.470] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    88.549] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[    90.438] (II) NOUVEAU(0): EDID vendor "SEC", prod id 13393
[    90.438] (II) NOUVEAU(0): Printing DDC gathered Modelines:
[    90.438] (II) NOUVEAU(0): Modeline "1366x768"x0.0   69.30  1366 1414 1446 1480  768 770 775 780 -hsync -vsync (46.8 kHz eP)
[    90.517] (--) NOUVEAU(0): HDMI max TMDS frequency 190000KHz
[   388.909] (II) config/udev: removing device Logitech USB Optical Mouse
[   388.936] (II) evdev: Logitech USB Optical Mouse: Close
[   388.936] (II) UnloadModule: "evdev"
[   392.963] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/mouse1)
[   392.963] (II) No input driver specified, ignoring this device.
[   392.963] (II) This device may have been added with another device file.
[   393.039] (II) config/udev: Adding input device Logitech USB Optical Mouse (/dev/input/event12)
[   393.040] (**) Logitech USB Optical Mouse: Applying InputClass "evdev pointer catchall"
[   393.040] (II) Using input driver 'evdev' for 'Logitech USB Optical Mouse'
[   393.040] (**) Logitech USB Optical Mouse: always reports core events
[   393.040] (**) evdev: Logitech USB Optical Mouse: Device: "/dev/input/event12"
[   393.096] (--) evdev: Logitech USB Optical Mouse: Vendor 0x46d Product 0xc05a
[   393.096] (--) evdev: Logitech USB Optical Mouse: Found 12 mouse buttons
[   393.096] (--) evdev: Logitech USB Optical Mouse: Found scroll wheel(s)
[   393.096] (--) evdev: Logitech USB Optical Mouse: Found relative axes
[   393.096] (--) evdev: Logitech USB Optical Mouse: Found x and y relative axes
[   393.096] (II) evdev: Logitech USB Optical Mouse: Configuring as mouse
[   393.096] (II) evdev: Logitech USB Optical Mouse: Adding scrollwheel support
[   393.096] (**) evdev: Logitech USB Optical Mouse: YAxisMapping: buttons 4 and 5
[   393.096] (**) evdev: Logitech USB Optical Mouse: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   393.096] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:04.0/usb4/4-4/4-4:1.0/0003:046D:C05A.0002/input/input20/event12"
[   393.096] (II) XINPUT: Adding extended input device "Logitech USB Optical Mouse" (type: MOUSE, id 14)
[   393.097] (II) evdev: Logitech USB Optical Mouse: initialized for relative axes.
[   393.097] (**) Logitech USB Optical Mouse: (accel) keeping acceleration scheme 1
[   393.098] (**) Logitech USB Optical Mouse: (accel) acceleration profile 0
[   393.098] (**) Logitech USB Optical Mouse: (accel) acceleration factor: 2.000
[   393.098] (**) Logitech USB Optical Mouse: (accel) acceleration threshold: 4
```


I'm sorry to be using Kubuntu for Live USB instead of Ubuntu MATE, but, at the moment, I have that on my USB stick, so I used it to give you a rapid feedback; Hoping it isn't a problem I would like to thank you in advance, thanks!

---

### Post by gaetano5 on 2015-10-28
...Still desperately google searching with poor results :(

Suggestions? 

Thanks :-)

---

### Post by tgalati4 on 2015-10-28
So you are running the *nouveau* module in both cases.  I presume that the *nvidia* module is still giving you trouble.

Start playing with switches for the *nouveau* module:

> parm:           tv_norm:Default TV norm.
		Supported: PAL, PAL-M, PAL-N, PAL-Nc, NTSC-M, NTSC-J,
			hd480i, hd480p, hd576i, hd576p, hd720p, hd1080i.
		Default: PAL
		*NOTE* Ignored for cards with external TV encoders. (charp)
parm:           tv_disable:Disable TV-out detection (int)
parm:           ignorelid:Ignore ACPI lid status (int)
parm:           duallink:Allow dual-link TMDS (default: enabled) (int)
parm:           nofbaccel:Disable fbcon acceleration (int)
parm:           agpmode:AGP mode (0 to disable AGP) (int)
parm:           vram_pushbuf:Create DMA push buffers in VRAM (int)
parm:           config:option string to pass to driver core (charp)
parm:           debug:debug string to pass to driver core (charp)
parm:           noaccel:disable kernel/abi16 acceleration (int)
parm:           modeset:enable driver (default: auto, 0 = disabled, 1 = enabled, 2 = headless) (int)
parm:           runpm:disable (0), force enable (1), optimus only default (-1) (int)


Some reading:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau](http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau)

---

### Post by Geoffrey_Arndt on 2015-10-28
Sometimes it doesn't matter if you try several distros IF they all require higher end drivers for default 3d accelerated graphics via compiz.

Perhaps that's why Live media works as you've described.     One way to test this out is to install a solid but light distro such as Xubuntu on the hdd . . . might be worth a shot.

---

### Post by gaetano5 on 2015-10-31
> **Geoffrey_Arndt said:**
> Sometimes it doesn't matter if you try several distros IF they all require higher end drivers for default 3d accelerated graphics via compiz.

Perhaps that's why Live media works as you've described.     One way to test this out is to install a solid but light distro such as Xubuntu on the hdd . . . might be worth a shot.

Hi,
tried also with Lubuntu and Xubuntu...same results...HDMI works when live from USB and stops working when Xubuntu/Lubuntu are permanently installed...


> **tgalati4 said:**
> So you are running the *nouveau* module in both cases. I presume that the *nvidia* module is still giving you trouble.

Start playing with switches for the *nouveau* module:



Some reading:

[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

[http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau](http://askubuntu.com/questions/481414/install-nvidia-driver-instead-nouveau)

Thank you for trying to help me but, honestly, I didn't understand how to play with nouveau switches...


...about the links: I already know how to install nvidia proprietary drivers but, as I've already said, also after having installed them, I have the same issues already listed.

..it seems I have to give up... :-(

---

### Post by tgalati4 on 2015-10-31
Do you have an xorg.conf file?  Try deleting it?

```
cat /etc/X11/xorg.conf
sudo mv /etc/X11/xorg.conf /etc/x11/xorg_bad.conf
```

Reboot.



Linux is based on not giving up.

---

### Post by trag on 2015-11-01
You might have to use a HDMI to VGA adapter and use in VGA. A totally crappy solution I admit.
Good Lucl
Tragic

---

### Post by pqwoerituytrueiwoq on 2015-11-01
have you checked the display settings? you may just need to turn the screen on in he gui
i know the geforce 8200m is a older laptop gpu so that means if you use hdmi you have 2 displays connected
* have had stability issues with nvidia's recent drivers on your gpu
edit: would that be a cq60-215dx laptop (full model on sticker under laptop)
i dont think mine has a hdmi port

---

### Post by Nibblyn on 2016-09-20
You may also want to consider using Grub Legacy instead of Grub2 if your case is similar to that reported here:

HDMI works with Live Iso but not with installed OS:
[https://ubuntuforums.org/showthread.php?t=2334805](https://ubuntuforums.org/showthread.php?t=2334805)

HDMI works with Grub Legacy but not with Grub2:
[https://ubuntuforums.org/showthread.php?t=2335950](https://ubuntuforums.org/showthread.php?t=2335950)

Please report back if this solves the issue for you. Thanks.

---

