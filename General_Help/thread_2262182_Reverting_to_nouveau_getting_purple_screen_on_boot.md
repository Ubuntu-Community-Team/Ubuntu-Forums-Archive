---
title: "Reverting to nouveau getting purple screen on boot"
date: 2015-01-23
forum: General Help
---

### Post by sye737 on 2015-01-23
After a failed installation of nvidia proprietary drivers, I managed to successfully reinstall it, but I ran into problems with video playback (I have a 750 ti) probably due to vdpau. So then I tried to revert back to nouveau, which I did with all the usual guides of purging any nvidia packages and making sure nouveau isn't blacklisted in /etc/modprobe.d/. On boot I get a purple screen, no response from keyboard or mouse to access virtual terminals. When booting with grub parameter nomodeset everything works, but the resolution is stuck at 1024x768.

Here's the excerpt from syslog and Xorg log when booting without the nomodeset parameter:

/var/log/syslog:

```
Jan 23 11:49:30 carbon kernel: [    3.959447] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input10Jan 23 11:49:30 carbon kernel: [    3.959564] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
Jan 23 11:49:30 carbon kernel: [    3.959601] snd_hda_intel 0000:00:03.0: enabling device (0000 -> 0002)
Jan 23 11:49:30 carbon kernel: [    3.959655] snd_hda_intel 0000:00:1b.0: enabling device (0000 -> 0002)
Jan 23 11:49:30 carbon kernel: [    3.959756] mei_me 0000:00:16.0: irq 51 for MSI/MSI-X
Jan 23 11:49:30 carbon kernel: [    3.960027] snd_hda_intel 0000:00:03.0: irq 52 for MSI/MSI-X
Jan 23 11:49:30 carbon kernel: [    3.960058] snd_hda_intel 0000:00:1b.0: irq 53 for MSI/MSI-X
Jan 23 11:49:30 carbon kernel: [    3.960665] nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x117000a2
Jan 23 11:49:30 carbon kernel: [    3.960667] nouveau  [  DEVICE][0000:01:00.0] Chipset: GM107 (NV117)
Jan 23 11:49:30 carbon kernel: [    3.960668] nouveau  [  DEVICE][0000:01:00.0] Family : NV110
Jan 23 11:49:30 carbon kernel: [    3.960682] nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
Jan 23 11:49:30 carbon kernel: [    3.960687] nouveau  [   VBIOS][0000:01:00.0] ... signature not found
Jan 23 11:49:30 carbon kernel: [    3.960688] nouveau  [   VBIOS][0000:01:00.0] checking PROM for image...
Jan 23 11:49:30 carbon kernel: [    3.990593] sound hdaudioC1D2: autoconfig: line_outs=3 (0x14/0x15/0x16/0x0/0x0) type:line
Jan 23 11:49:30 carbon kernel: [    3.990595] sound hdaudioC1D2:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
Jan 23 11:49:30 carbon kernel: [    3.990596] sound hdaudioC1D2:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
Jan 23 11:49:30 carbon kernel: [    3.990596] sound hdaudioC1D2:    mono: mono_out=0x0
Jan 23 11:49:30 carbon kernel: [    3.990597] sound hdaudioC1D2:    dig-out=0x11/0x1e
Jan 23 11:49:30 carbon kernel: [    3.990598] sound hdaudioC1D2:    inputs:
Jan 23 11:49:30 carbon kernel: [    3.990599] sound hdaudioC1D2:      Front Mic=0x19
Jan 23 11:49:30 carbon kernel: [    3.990600] sound hdaudioC1D2:      Rear Mic=0x18
Jan 23 11:49:30 carbon kernel: [    3.990601] sound hdaudioC1D2:      Line=0x1a
Jan 23 11:49:30 carbon kernel: [    4.001143] nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
Jan 23 11:49:30 carbon kernel: [    4.001144] nouveau  [   VBIOS][0000:01:00.0] using image from PROM
Jan 23 11:49:30 carbon kernel: [    4.001194] nouveau  [   VBIOS][0000:01:00.0] BIT signature found
Jan 23 11:49:30 carbon kernel: [    4.001196] nouveau  [   VBIOS][0000:01:00.0] version 82.07.25.00.53
Jan 23 11:49:30 carbon kernel: [    4.001429] nouveau 0000:01:00.0: irq 54 for MSI/MSI-X
Jan 23 11:49:30 carbon kernel: [    4.001435] nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
Jan 23 11:49:30 carbon kernel: [    4.001454] nouveau  [     PFB][0000:01:00.0] RAM type: GDDR5
Jan 23 11:49:30 carbon kernel: [    4.001455] nouveau  [     PFB][0000:01:00.0] RAM size: 2048 MiB
Jan 23 11:49:30 carbon kernel: [    4.001456] nouveau  [     PFB][0000:01:00.0]    ZCOMP: 0 tags
Jan 23 11:49:30 carbon kernel: [    4.002607] nouveau  [     CLK][0000:01:00.0] 07: core 405 MHz memory 810 MHz
Jan 23 11:49:30 carbon kernel: [    4.002671] nouveau  [     CLK][0000:01:00.0] 0f: core 270-1333 MHz memory 5400 MHz
Jan 23 11:49:30 carbon kernel: [    4.002736] nouveau  [     CLK][0000:01:00.0] --: core 405 MHz memory 810 MHz
Jan 23 11:49:30 carbon kernel: [    4.003885] nouveau  [  PGRAPH][0000:01:00.0] using external firmware
Jan 23 11:49:30 carbon kernel: [    4.004580] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Jan 23 11:49:30 carbon kernel: [    4.004582] nouveau 0000:01:00.0: Falling back to user helper
Jan 23 11:49:30 carbon kernel: [    4.004964] nouveau 0000:01:00.0: Direct firmware load failed with error -2
Jan 23 11:49:30 carbon kernel: [    4.004966] nouveau 0000:01:00.0: Falling back to user helper
Jan 23 11:49:30 carbon kernel: [    4.005239] nouveau E[  PGRAPH][0000:01:00.0] failed to load fuc409c
Jan 23 11:49:30 carbon kernel: [    4.005241] nouveau E[  DEVICE][0000:01:00.0] failed to create 0x18000717, -22
Jan 23 11:49:30 carbon kernel: [    4.005244] nouveau E[     DRM] failed to create 0x80000080, -22
Jan 23 11:49:30 carbon kernel: [    4.005859] nouveau: probe of 0000:01:00.0 failed with error -22
Jan 23 11:49:30 carbon kernel: [    4.005906] snd_hda_intel 0000:01:00.1: Disabling MSI
Jan 23 11:49:30 carbon kernel: [    4.005910] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
```

/var/log/Xorg.0.log.old:
```
[    28.392] X.Org X Server 1.16.1.901 (1.16.2 RC 1)
Release Date: 2014-11-02
[    28.392] X Protocol Version 11, Revision 0
[    28.392] Build Operating System: Linux 3.13.0-39-generic x86_64 Ubuntu
[    28.392] Current Operating System: Linux carbon 3.16.0-29-generic #39-Ubuntu SMP Mon Dec 15 22:27:29 UTC 2014 x86_64
[    28.392] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.16.0-29-generic.efi.signed root=UUID=810a6d07-99e5-4511-8766-6740f11eeda5 ro quiet splash vt.handoff=7
[    28.393] Build Date: 20 November 2014  09:55:19PM
[    28.393] xorg-server 2:1.16.1.901-1ubuntu1~utopic1 (For technical support please see http://www.ubuntu.com/support) 
[    28.393] Current version of pixman: 0.32.4
[    28.393]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[    28.393] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[    28.393] (==) Log file: "/var/log/Xorg.0.log", Time: Fri Jan 23 11:49:55 2015
[    28.393] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[    28.393] (==) No Layout section.  Using the first Screen section.
[    28.393] (==) No screen section available. Using defaults.
[    28.393] (**) |-->Screen "Default Screen Section" (0)
[    28.393] (**) |   |-->Monitor "<default monitor>"
[    28.393] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[    28.393] (==) Automatically adding devices
[    28.393] (==) Automatically enabling devices
[    28.393] (==) Automatically adding GPU devices
[    28.393] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[    28.393]     Entry deleted from font path.
[    28.393] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[    28.393]     Entry deleted from font path.
[    28.393] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[    28.393]     Entry deleted from font path.
[    28.393] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[    28.393]     Entry deleted from font path.
[    28.393] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[    28.393]     Entry deleted from font path.
[    28.393] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[    28.393] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[    28.393] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[    28.393] (II) Loader magic: 0x7f31ea7f4d80
[    28.393] (II) Module ABI versions:
[    28.393]     X.Org ANSI C Emulation: 0.4
[    28.393]     X.Org Video Driver: 18.0
[    28.393]     X.Org XInput driver : 21.0
[    28.393]     X.Org Server Extension : 8.0
[    28.393] (II) xfree86: Adding drm device (/dev/dri/card0)
[    28.394] (--) PCI: (0:0:2:0) 8086:0412:1458:d000 rev 6, Mem @ 0xf7400000/4194304, 0xd0000000/268435456, I/O @ 0x0000f000/64
[    28.394] (--) PCI:*(0:1:0:0) 10de:1380:1462:3102 rev 162, Mem @ 0xf6000000/16777216, 0xe0000000/268435456, 0xf0000000/33554432, I/O @ 0x0000e000/128, BIOS @ 0x????????/524288
[    28.394] (II) LoadModule: "glx"
[    28.394] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[    28.394] (II) Module glx: vendor="X.Org Foundation"
[    28.394]     compiled for 1.16.1.901, module version = 1.0.0
[    28.394]     ABI class: X.Org Server Extension, version 8.0
[    28.394] (==) AIGLX enabled
[    28.394] (==) Matched intel as autoconfigured driver 0
[    28.394] (==) Matched nvidia as autoconfigured driver 1
[    28.394] (==) Matched nouveau as autoconfigured driver 2
[    28.394] (==) Matched modesetting as autoconfigured driver 3
[    28.394] (==) Matched fbdev as autoconfigured driver 4
[    28.394] (==) Matched vesa as autoconfigured driver 5
[    28.394] (==) Assigned the driver to the xf86ConfigLayout
[    28.394] (II) LoadModule: "intel"
[    28.394] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.395] (II) Module intel: vendor="X.Org Foundation"
[    28.395]     compiled for 1.16.1.901, module version = 2.99.916
[    28.395]     Module class: X.Org Video Driver
[    28.395]     ABI class: X.Org Video Driver, version 18.0
[    28.395] (II) LoadModule: "nvidia"
[    28.395] (WW) Warning, couldn't open module nvidia
[    28.395] (II) UnloadModule: "nvidia"
[    28.395] (II) Unloading nvidia
[    28.395] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    28.395] (II) LoadModule: "nouveau"
[    28.395] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.395] (II) Module nouveau: vendor="X.Org Foundation"
[    28.395]     compiled for 1.16.0, module version = 1.0.11
[    28.395]     Module class: X.Org Video Driver
[    28.395]     ABI class: X.Org Video Driver, version 18.0
[    28.395] (II) LoadModule: "modesetting"
[    28.395] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.395] (II) Module modesetting: vendor="X.Org Foundation"
[    28.395]     compiled for 1.16.0, module version = 0.9.0
[    28.395]     Module class: X.Org Video Driver
[    28.395]     ABI class: X.Org Video Driver, version 18.0
[    28.395] (II) LoadModule: "fbdev"
[    28.395] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.395] (II) Module fbdev: vendor="X.Org Foundation"
[    28.395]     compiled for 1.16.0, module version = 0.4.4
[    28.395]     Module class: X.Org Video Driver
[    28.395]     ABI class: X.Org Video Driver, version 18.0
[    28.395] (II) LoadModule: "vesa"
[    28.395] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.395] (II) Module vesa: vendor="X.Org Foundation"
[    28.395]     compiled for 1.16.0, module version = 2.3.3
[    28.395]     Module class: X.Org Video Driver
[    28.395]     ABI class: X.Org Video Driver, version 18.0
[    28.395] (==) Matched intel as autoconfigured driver 0
[    28.395] (==) Matched nvidia as autoconfigured driver 1
[    28.395] (==) Matched nouveau as autoconfigured driver 2
[    28.395] (==) Matched modesetting as autoconfigured driver 3
[    28.395] (==) Matched fbdev as autoconfigured driver 4
[    28.395] (==) Matched vesa as autoconfigured driver 5
[    28.395] (==) Assigned the driver to the xf86ConfigLayout
[    28.395] (II) LoadModule: "intel"
[    28.395] (II) Loading /usr/lib/xorg/modules/drivers/intel_drv.so
[    28.395] (II) Module intel: vendor="X.Org Foundation"
[    28.395]     compiled for 1.16.1.901, module version = 2.99.916
[    28.395]     Module class: X.Org Video Driver
[    28.395]     ABI class: X.Org Video Driver, version 18.0
[    28.395] (II) UnloadModule: "intel"
[    28.395] (II) Unloading intel
[    28.395] (II) Failed to load module "intel" (already loaded, 32561)
[    28.395] (II) LoadModule: "nvidia"
[    28.395] (WW) Warning, couldn't open module nvidia
[    28.395] (II) UnloadModule: "nvidia"
[    28.395] (II) Unloading nvidia
[    28.395] (EE) Failed to load module "nvidia" (module does not exist, 0)
[    28.395] (II) LoadModule: "nouveau"
[    28.395] (II) Loading /usr/lib/xorg/modules/drivers/nouveau_drv.so
[    28.395] (II) Module nouveau: vendor="X.Org Foundation"
[    28.395]     compiled for 1.16.0, module version = 1.0.11
[    28.395]     Module class: X.Org Video Driver
[    28.395]     ABI class: X.Org Video Driver, version 18.0
[    28.395] (II) UnloadModule: "nouveau"
[    28.395] (II) Unloading nouveau
[    28.395] (II) Failed to load module "nouveau" (already loaded, 0)
[    28.395] (II) LoadModule: "modesetting"
[    28.396] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[    28.396] (II) Module modesetting: vendor="X.Org Foundation"
[    28.396]     compiled for 1.16.0, module version = 0.9.0
[    28.396]     Module class: X.Org Video Driver
[    28.396]     ABI class: X.Org Video Driver, version 18.0
[    28.396] (II) UnloadModule: "modesetting"
[    28.396] (II) Unloading modesetting
[    28.396] (II) Failed to load module "modesetting" (already loaded, 0)
[    28.396] (II) LoadModule: "fbdev"
[    28.396] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[    28.396] (II) Module fbdev: vendor="X.Org Foundation"
[    28.396]     compiled for 1.16.0, module version = 0.4.4
[    28.396]     Module class: X.Org Video Driver
[    28.396]     ABI class: X.Org Video Driver, version 18.0
[    28.396] (II) UnloadModule: "fbdev"
[    28.396] (II) Unloading fbdev
[    28.396] (II) Failed to load module "fbdev" (already loaded, 0)
[    28.396] (II) LoadModule: "vesa"
[    28.396] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[    28.396] (II) Module vesa: vendor="X.Org Foundation"
[    28.396]     compiled for 1.16.0, module version = 2.3.3
[    28.396]     Module class: X.Org Video Driver
[    28.396]     ABI class: X.Org Video Driver, version 18.0
[    28.396] (II) UnloadModule: "vesa"
[    28.396] (II) Unloading vesa
[    28.396] (II) Failed to load module "vesa" (already loaded, 0)
[    28.396] (II) intel: Driver for Intel(R) Integrated Graphics Chipsets:
    i810, i810-dc100, i810e, i815, i830M, 845G, 854, 852GM/855GM, 865G,
    915G, E7221 (i915), 915GM, 945G, 945GM, 945GME, Pineview GM,
    Pineview G, 965G, G35, 965Q, 946GZ, 965GM, 965GME/GLE, G33, Q35, Q33,
    GM45, 4 Series, G45/G43, Q45/Q43, G41, B43
[    28.396] (II) intel: Driver for Intel(R) HD Graphics: 2000-6000
[    28.396] (II) intel: Driver for Intel(R) Iris(TM) Graphics: 5100, 6100
[    28.396] (II) intel: Driver for Intel(R) Iris(TM) Pro Graphics: 5200, 6200, P6300
[    28.396] (II) NOUVEAU driver 
[    28.396] (II) NOUVEAU driver for NVIDIA chipset families :
[    28.396]     RIVA TNT        (NV04)
[    28.396]     RIVA TNT2       (NV05)
[    28.396]     GeForce 256     (NV10)
[    28.396]     GeForce 2       (NV11, NV15)
[    28.396]     GeForce 4MX     (NV17, NV18)
[    28.396]     GeForce 3       (NV20)
[    28.396]     GeForce 4Ti     (NV25, NV28)
[    28.396]     GeForce FX      (NV3x)
[    28.396]     GeForce 6       (NV4x)
[    28.396]     GeForce 7       (G7x)
[    28.396]     GeForce 8       (G8x)
[    28.396]     GeForce GTX 200 (NVA0)
[    28.396]     GeForce GTX 400 (NVC0)
[    28.396] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[    28.396] (II) FBDEV: driver for framebuffer: fbdev
[    28.396] (II) VESA: driver for VESA chipsets: vesa
[    28.396] (++) using VT number 7


[    28.396] (II) intel(G0): Using Kernel Mode Setting driver: i915, version 1.6.0 20080730
[    28.396] (II) intel(G0): SNA compiled: xserver-xorg-video-intel 2:2.99.916+git20141215.99537089-0ubuntu0sarvatt~utopic (Robert Hooker <sarvatt@ubuntu.com>)
[    28.396] (II) intel(G0): SNA compiled for use with valgrind
[    28.396] (EE) [drm] KMS not enabled
[    28.396] (EE) [drm] KMS not enabled
[    28.396] (WW) Falling back to old probe method for modesetting
[    28.396] (II) Loading sub module "fbdevhw"
[    28.396] (II) LoadModule: "fbdevhw"
[    28.396] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[    28.396] (II) Module fbdevhw: vendor="X.Org Foundation"
[    28.396]     compiled for 1.16.1.901, module version = 0.0.2
[    28.396]     ABI class: X.Org Video Driver, version 18.0
[    28.396] (**) FBDEV(2): claimed PCI slot 1@0:0:0
[    28.396] (II) FBDEV(2): using default device
[    28.396] (WW) Falling back to old probe method for vesa
[    28.396] (EE) Screen 0 deleted because of no matching config section.
[    28.396] (II) UnloadModule: "modesetting"
[    28.397] (EE) Screen 0 deleted because of no matching config section.
[    28.397] (II) UnloadModule: "modesetting"
[    28.397] (II) FBDEV(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[    28.397] (==) FBDEV(0): Depth 24, (==) framebuffer bpp 32
[    28.397] (==) FBDEV(0): RGB weight 888
[    28.397] (==) FBDEV(0): Default visual is TrueColor
[    28.397] (==) FBDEV(0): Using gamma correction (1.0, 1.0, 1.0)
[    28.397] (II) FBDEV(0): hardware: inteldrmfb (video memory: 3072kB)
[    28.397] (II) FBDEV(0): checking modes against framebuffer device...
[    28.397] (II) FBDEV(0): checking modes against monitor...
[    28.397] (--) FBDEV(0): Virtual size is 1024x768 (pitch 1024)
[    28.397] (**) FBDEV(0):  Built-in mode "current"
[    28.397] (==) FBDEV(0): DPI set to (96, 96)
[    28.397] (II) Loading sub module "fb"
[    28.397] (II) LoadModule: "fb"
[    28.397] (II) Loading /usr/lib/xorg/modules/libfb.so
[    28.397] (II) Module fb: vendor="X.Org Foundation"
[    28.397]     compiled for 1.16.1.901, module version = 1.0.0
[    28.397]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.397] (**) FBDEV(0): using shadow framebuffer
[    28.397] (II) Loading sub module "shadow"
[    28.397] (II) LoadModule: "shadow"
[    28.397] (II) Loading /usr/lib/xorg/modules/libshadow.so
[    28.397] (II) Module shadow: vendor="X.Org Foundation"
[    28.397]     compiled for 1.16.1.901, module version = 1.1.0
[    28.397]     ABI class: X.Org ANSI C Emulation, version 0.4
[    28.397] (--) intel(G0): Integrated Graphics Chipset: Intel(R) HD Graphics 4600
[    28.397] (--) intel(G0): CPU: x86-64, sse2, sse3, ssse3, sse4.1, sse4.2, avx, avx2
[    28.397] (==) intel(G0): Depth 24, (--) framebuffer bpp 32
[    28.397] (==) intel(G0): RGB weight 888
[    28.397] (==) intel(G0): Default visual is TrueColor
[    28.397] (II) intel(G0): Output VGA1 has no monitor section
[    28.397] (II) intel(G0): Enabled output VGA1
[    28.397] (II) intel(G0): Output HDMI1 has no monitor section
[    28.397] (II) intel(G0): Enabled output HDMI1
[    28.397] (II) intel(G0): Output HDMI2 has no monitor section
[    28.397] (II) intel(G0): Enabled output HDMI2
[    28.397] (II) intel(G0): Output HDMI3 has no monitor section
[    28.397] (II) intel(G0): Enabled output HDMI3
[    28.397] (--) intel(G0): Using a maximum size of 256x256 for hardware cursors
[    28.397] (II) intel(G0): Output VIRTUAL1 has no monitor section
[    28.397] (II) intel(G0): Enabled output VIRTUAL1
[    28.397] (==) intel(G0): TearFree disabled
[    28.397] (==) intel(G0): DPI set to (96, 96)
[    28.397] (II) Loading sub module "dri2"
[    28.397] (II) LoadModule: "dri2"
[    28.397] (II) Module "dri2" already built-in
[    28.397] (II) Loading sub module "present"
[    28.397] (II) LoadModule: "present"
[    28.397] (II) Module "present" already built-in
[    28.397] (II) UnloadModule: "vesa"
[    28.397] (II) Unloading vesa
[    28.397] (==) Depth 24 pixmap format is 32 bpp
[    28.397] (II) intel(G0): SNA initialized with Haswell (gen7.5, gt2) backend
[    28.397] (==) intel(G0): Backing store enabled
[    28.397] (==) intel(G0): Silken mouse enabled
[    28.397] (II) intel(G0): HW Cursor enabled
[    28.397] (II) intel(G0): RandR 1.2 enabled, ignore the following RandR disabled message.
[    28.397] (==) intel(G0): DPMS enabled
[    28.397] (==) intel(G0): display hotplug detection enabled
[    28.397] (II) intel(G0): [DRI2] Setup complete
[    28.397] (II) intel(G0): [DRI2]   DRI driver: i965
[    28.397] (II) intel(G0): [DRI2]   VDPAU driver: i965
[    28.397] (II) intel(G0): direct rendering: DRI2 enabled
[    28.397] (II) intel(G0): hardware support for Present enabled
[    28.398] (==) FBDEV(0): Backing store enabled
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (EE) FBDEV(0): FBIOPUTCMAP: Device or resource busy
[    28.398] (==) FBDEV(0): DPMS enabled
[    28.398] (--) RandR disabled
[    28.401] (II) SELinux: Disabled on system
[    28.402] (II) AIGLX: Screen 0 is not DRI2 capable
[    28.402] (EE) AIGLX: reverting to software rendering
[    28.408] (II) AIGLX: Loaded and initialized swrast
[    28.408] (II) GLX: Initialized DRISWRAST GL provider for screen 0
[    28.408] (EE) 
[    28.408] (EE) Backtrace:
[    28.409] (EE) 0: /usr/bin/X (xorg_backtrace+0x56) [0x7f31ea56d986]
[    28.409] (EE) 1: /usr/bin/X (0x7f31ea3b7000+0x1bab69) [0x7f31ea571b69]
[    28.409] (EE) 2: /lib/x86_64-linux-gnu/libc.so.6 (0x7f31e80eb000+0x36eb0) [0x7f31e8121eb0]
[    28.409] (EE) 3: /usr/bin/X (RRSetChanged+0x50) [0x7f31ea4cf510]
[    28.409] (EE) 4: /usr/bin/X (RRScreenSetSizeRange+0x54) [0x7f31ea4d3c84]
[    28.409] (EE) 5: /usr/bin/X (xf86RandR12CreateScreenResources+0x2a5) [0x7f31ea4908d5]
[    28.409] (EE) 6: /usr/bin/X (0x7f31ea3b7000+0xcc400) [0x7f31ea483400]
[    28.409] (EE) 7: /usr/bin/X (0x7f31ea3b7000+0x5b0f4) [0x7f31ea4120f4]
[    28.409] (EE) 8: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f31e810cec5]
[    28.409] (EE) 9: /usr/bin/X (0x7f31ea3b7000+0x456ae) [0x7f31ea3fc6ae]
[    28.409] (EE) 
[    28.409] (EE) Segmentation fault at address 0xa0
[    28.409] (EE) 
Fatal server error:
[    28.409] (EE) Caught signal 11 (Segmentation fault). Server aborting
[    28.409] (EE) 
[    28.409] (EE) 
```

---

### Post by Derrick_Katula on 2015-01-23
[TABLE]
[TR]
[TD="class: votecell"]     

              [/TD]
                [TD="class: answercell"]      Try removing your freshly installed Nvidia driver and go back to the open-source driver, Nouveau. Log in to the command line interface of Ubuntu, launch sudo apt-get install nouveau-firmware (just in case) then follow the instructions at [http://askubuntu.com/a/12941/5592](http://askubuntu.com/a/12941/5592):
  [INDENT]   To reconfigure xorg.conf, type the following command:
      sudo dpkg-reconfigure xserver-xorg
      Go following the screen steps, answering the wizard questions and you   should able to restore or reconfigure to previous **Nouveau** state.
 [/INDENT]  After that, if this solved your problem, you will probably have a  very low resolution. So launch the "Displays" utility from the Dash home  and adjust your resolution accordingly to fit your screen the best.
     
[/TD]
[/TR]
[/TABLE]

---

### Post by Bashing-om on 2015-01-23
sye737; Hello'

The 750ti is new hardware, and the support for it has not filtered down to our software repository to this time.
There are options .
see:
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)

[INDENT][INDENT]my bit to try and help
[/INDENT][/INDENT]

---

### Post by sye737 on 2015-01-23
Looks like nouveau support for 750ti is still not ready in Ubuntu 14.10. [http://www.phoronix.com/scan.php?page=news_item&px=MTc4ODA](http://www.phoronix.com/scan.php?page=news_item&px=MTc4ODA)

I ended up reinstalling the nvidia binary driver, but the nomodeset flag was still required to boot - otherwise booting leads to no video output being detected.


```
sudo add-apt-repository ppa:xorg-edgers/ppa
sudo apt-get update
sudo apt-get install nvidia-346

```

---

### Post by Bashing-om on 2015-01-23
sye737; Humm ...

Rebooted, and now all is good ?

Else try and purge the ppa and all Nvidia drivers and try again .

[INDENT][INDENT]just my thought 
[/INDENT][/INDENT]

---

