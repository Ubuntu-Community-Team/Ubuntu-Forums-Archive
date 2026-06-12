---
title: "No login screen"
date: 2018-06-12
forum: General Help
---

### Post by archi2 on 2018-06-12
I have different systems in my PC, installed by someone else and I am no expert. 
I believe I have Ubuntu 16.04.4 installed. Couple of days ago after some updates and reboot I got just black screen instead of login. I have followed some googled instructions, no joy. After this one:
```
[COLOR=#808080][FONT=Roboto]s[/FONT][/COLOR]udo apt-get purge xorg "xserver-*"
sudo apt-get purge lightdm plymouthsudo 
rm -rf /etc/X11/xorg
sudo apt-get autoremove

sudo apt-get install xauth xorg openbox lightdm plymouth
sudo apt-get install ubuntu-desktop 
reboot

sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade -y
reboot
```[COLOR=#808080][FONT=Roboto][COLOR=#222222][FONT=Verdana]
Instead of black screen I have following error: "/dev/sdc1: clean, *somenumbers* files, *somenumbers* blocks" and nothing is happening.
There was some warning after running [/FONT][/COLOR]```
[COLOR=#C7254E][FONT=Monaco]sudo apt-get purge lightdm plymouth[/FONT][/COLOR]
```[COLOR=#222222][FONT=Verdana] but I don't remember what it said.

No idea what to do next[/FONT][/COLOR][/FONT][/COLOR]

---

### Post by rtimai on 2018-06-13
@archi2:  The current version of Ubuntu is 18.04, but the following information is not version-specific.

I don't know if this is too late to ask, but did you try forcing a hardware shutdown by holding down the power button for 5 seconds? Next time, try doing that, instead of removing and reinstalling anything, especially your display server. Every linux distro is gradually transitioning from X11 to the Wayland display server, which is an extremely delicate process, as it involves the ability to see error feedback. The display server is the LAST thing I would ever fiddle with.

A somewhat more thorough restart procedure is to disconnect the power cord, and remove the battery (if notebook,) and holding down for 5-10 seconds the power button to discharge any residual charge holding saved hardware states (not sure of proper terminology,) before putting everything back and restarting.

I experienced the halt at black-screen on two computers at home about the time kernel updates were installed (which can affect the display as well.) Actually, this happened on two separate occasions after system updates -- on both computers. After shutting down, both laptops recovered gracefully (well, more or less) and started up normally. No guarantees, of course, but you should ALWAYS try restarting before trying anything else -- it must might save you a lot of work. (I am running Ubuntu 18.04 Gnome-X11)

UPDATE !!! : The startup halt at black-screen occurred AGAIN (a THIRD time) after I wrote the above (but delayed posting -- so I now decided to post this after all.) In the case of my wife's laptop, SIX forced hardware shutdowns were required (on mine, only once,) then startup proceeded normally -- and on checking, both computers had *additional* software updates still pending (which I then ran.) I don't have a clue to what the mechanics of this glitch are, but I hope that this information about repeating the forced restarts might be helpful, for both Archi2 and others.

BTW, FYI, in Terminal,
  less /var/log/apt/history.log
#VIEW MOST RECENT UPDATES, ESC TO RETURN TO COMMAND PROMPT

Good luck, all.

---

### Post by Impavidus on 2018-06-14
A black screen after an upgrade is most common after a kernel upgrade that doesn't play too well with your graphics hardware. The first thing to try is booting an older kernel via the grub menu.

BTW, the "/dev/sdc1: clean, ..." message is no error. It indicates your file system is fine. The message should be hidden by the boot splash screen, but this hasn't worked properly for some time.

---

### Post by archi2 on 2018-06-14
Hi @rtimai, thank you for reply. I did reboot PC a lot. I have seen the history.log but I do not know how to revert changes. I almost never used command line... feel stupid using linux now. I am trying to figure out how to paste error messages here without GUI and browser. I have internet connection though.

---

### Post by archi2 on 2018-06-14
@Impavidus
I does not work with 4.4.0-128-generic and 127 generic. I have tried 3.13.0-101-generic and got following error:
[I]Failed to enable subscription: Launch helper exited with unknown return code 1
Failed to fully start up daemon: Input/output error


[/I]btw. I have AMD graphics

edit.
startx, result from xorg log:
```

[   257.341] 
X.Org X Server 1.18.4
Release Date: 2016-07-19
[   257.342] X Protocol Version 11, Revision 0
[   257.342] Build Operating System: Linux 4.4.0-97-generic x86_64 Ubuntu
[   257.342] Current Operating System: Linux apollo 4.4.0-128-generic #154-Ubuntu SMP Fri May 25 14:15:18 UTC 2018 x86_64
[   257.342] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-4.4.0-128-generic.efi.signed root=UUID=6b486fd1-9e84-42b9-b676-66ab55943aac ro quiet splash vt.handoff=7
[   257.343] Build Date: 13 October 2017  01:57:05PM
[   257.344] xorg-server 2:1.18.4-0ubuntu0.7 (For technical support please see http://www.ubuntu.com/support) 
[   257.344] Current version of pixman: 0.33.6
[   257.346]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   257.346] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   257.348] (==) Log file: "/home/artur/.local/share/xorg/Xorg.0.log", Time: Thu Jun 14 16:13:23 2018
[   257.349] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   257.349] (==) No Layout section.  Using the first Screen section.
[   257.349] (==) No screen section available. Using defaults.
[   257.349] (**) |-->Screen "Default Screen Section" (0)
[   257.349] (**) |   |-->Monitor "<default monitor>"
[   257.349] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   257.349] (==) Automatically adding devices
[   257.349] (==) Automatically enabling devices
[   257.349] (==) Automatically adding GPU devices
[   257.349] (==) Max clients allowed: 256, resource mask: 0x1fffff
[   257.349] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   257.349]     Entry deleted from font path.
[   257.349] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   257.349]     Entry deleted from font path.
[   257.349] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   257.349]     Entry deleted from font path.
[   257.349] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   257.349]     Entry deleted from font path.
[   257.349] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   257.349]     Entry deleted from font path.
[   257.349] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   257.349] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   257.349] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   257.349] (II) Loader magic: 0x55c07fc88dc0
[   257.349] (II) Module ABI versions:
[   257.349]     X.Org ANSI C Emulation: 0.4
[   257.349]     X.Org Video Driver: 20.0
[   257.349]     X.Org XInput driver : 22.1
[   257.349]     X.Org Server Extension : 9.0
[   257.350] (++) using VT number 2


[   257.352] (II) systemd-logind: took control of session /org/freedesktop/login1/session/_31
[   257.353] (II) xfree86: Adding drm device (/dev/dri/card0)
[   257.353] (II) systemd-logind: got fd for /dev/dri/card0 226:0 fd 8 paused 0
[   257.354] (--) PCI:*(0:1:0:0) 1002:6798:1787:3001 rev 0, Mem @ 0xe0000000/268435456, 0xf7e00000/262144, I/O @ 0x0000e000/256, BIOS @ 0x????????/131072
[   257.354] (II) LoadModule: "glx"
[   257.354] (II) Loading /usr/lib/xorg/modules/extensions/libglx.so
[   257.355] (II) Module glx: vendor="X.Org Foundation"
[   257.355]     compiled for 1.18.4, module version = 1.0.0
[   257.355]     ABI class: X.Org Server Extension, version 9.0
[   257.355] (==) AIGLX enabled
[   257.355] (II) Applying OutputClass "Radeon" to /dev/dri/card0
[   257.355]     loading driver: radeon
[   257.355] (==) Matched radeon as autoconfigured driver 0
[   257.355] (==) Matched ati as autoconfigured driver 1
[   257.355] (==) Matched ati as autoconfigured driver 2
[   257.355] (==) Matched modesetting as autoconfigured driver 3
[   257.355] (==) Matched fbdev as autoconfigured driver 4
[   257.355] (==) Matched vesa as autoconfigured driver 5
[   257.355] (==) Assigned the driver to the xf86ConfigLayout
[   257.355] (II) LoadModule: "radeon"
[   257.356] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   257.356] (II) Module radeon: vendor="X.Org Foundation"
[   257.356]     compiled for 1.18.4, module version = 18.0.1
[   257.356]     Module class: X.Org Video Driver
[   257.356]     ABI class: X.Org Video Driver, version 20.0
[   257.356] (II) LoadModule: "ati"
[   257.356] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   257.356] (II) Module ati: vendor="X.Org Foundation"
[   257.356]     compiled for 1.18.4, module version = 18.0.1
[   257.356]     Module class: X.Org Video Driver
[   257.356]     ABI class: X.Org Video Driver, version 20.0
[   257.412] (II) LoadModule: "modesetting"
[   257.412] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   257.412] (II) Module modesetting: vendor="X.Org Foundation"
[   257.412]     compiled for 1.18.4, module version = 1.18.4
[   257.412]     Module class: X.Org Video Driver
[   257.412]     ABI class: X.Org Video Driver, version 20.0
[   257.412] (II) LoadModule: "fbdev"
[   257.412] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   257.412] (II) Module fbdev: vendor="X.Org Foundation"
[   257.412]     compiled for 1.18.1, module version = 0.4.4
[   257.412]     Module class: X.Org Video Driver
[   257.412]     ABI class: X.Org Video Driver, version 20.0
[   257.412] (II) LoadModule: "vesa"
[   257.412] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   257.412] (II) Module vesa: vendor="X.Org Foundation"
[   257.412]     compiled for 1.18.1, module version = 2.3.4
[   257.412]     Module class: X.Org Video Driver
[   257.412]     ABI class: X.Org Video Driver, version 20.0
[   257.412] (II) RADEON: Driver for ATI/AMD Radeon chipsets:
    ATI Radeon Mobility X600 (M24), ATI FireMV 2400,
    ATI Radeon Mobility X300 (M24), ATI FireGL M24 GL,
    ATI Radeon X600 (RV380), ATI FireGL V3200 (RV380),
    ATI Radeon IGP320 (A3), ATI Radeon IGP330/340/350 (A4),
    ATI Radeon 9500, ATI Radeon 9600TX, ATI FireGL Z1, ATI Radeon 9800SE,
    ATI Radeon 9800, ATI FireGL X2, ATI Radeon 9600, ATI Radeon 9600SE,
    ATI Radeon 9600XT, ATI FireGL T2, ATI Radeon 9650, ATI FireGL RV360,
    ATI Radeon 7000 IGP (A4+), ATI Radeon 8500 AIW,
    ATI Radeon IGP320M (U1), ATI Radeon IGP330M/340M/350M (U2),
    ATI Radeon Mobility 7000 IGP, ATI Radeon 9000/PRO, ATI Radeon 9000,
    ATI Radeon X800 (R420), ATI Radeon X800PRO (R420),
    ATI Radeon X800SE (R420), ATI FireGL X3 (R420),
    ATI Radeon Mobility 9800 (M18), ATI Radeon X800 SE (R420),
    ATI Radeon X800XT (R420), ATI Radeon X800 VE (R420),
    ATI Radeon X850 (R480), ATI Radeon X850 XT (R480),
    ATI Radeon X850 SE (R480), ATI Radeon X850 PRO (R480),
    ATI Radeon X850 XT PE (R480), ATI Radeon Mobility M7,
    ATI Mobility FireGL 7800 M7, ATI Radeon Mobility M6,
    ATI FireGL Mobility 9000 (M9), ATI Radeon Mobility 9000 (M9),
    ATI Radeon 9700 Pro, ATI Radeon 9700/9500Pro, ATI FireGL X1,
    ATI Radeon 9800PRO, ATI Radeon 9800XT,
    ATI Radeon Mobility 9600/9700 (M10/M11),
    ATI Radeon Mobility 9600 (M10), ATI Radeon Mobility 9600 (M11),
    ATI FireGL Mobility T2 (M10), ATI FireGL Mobility T2e (M11),
    ATI Radeon, ATI FireGL 8700/8800, ATI Radeon 8500, ATI Radeon 9100,
    ATI Radeon 7500, ATI Radeon VE/7000, ATI ES1000,
    ATI Radeon Mobility X300 (M22), ATI Radeon Mobility X600 SE (M24C),
    ATI FireGL M22 GL, ATI Radeon X800 (R423), ATI Radeon X800PRO (R423),
    ATI Radeon X800LE (R423), ATI Radeon X800SE (R423),
    ATI Radeon X800 XTP (R430), ATI Radeon X800 XL (R430),
    ATI Radeon X800 SE (R430), ATI Radeon X800 (R430),
    ATI FireGL V7100 (R423), ATI FireGL V5100 (R423),
    ATI FireGL unknown (R423), ATI Mobility FireGL V5000 (M26),
    ATI Mobility Radeon X700 XL (M26), ATI Mobility Radeon X700 (M26),
    ATI Radeon X550XTX, ATI Radeon 9100 IGP (A5),
    ATI Radeon Mobility 9100 IGP (U3), ATI Radeon XPRESS 200,
    ATI Radeon XPRESS 200M, ATI Radeon 9250, ATI Radeon 9200,
    ATI Radeon 9200SE, ATI FireMV 2200, ATI Radeon X300 (RV370),
    ATI Radeon X600 (RV370), ATI Radeon X550 (RV370),
    ATI FireGL V3100 (RV370), ATI FireMV 2200 PCIE (RV370),
    ATI Radeon Mobility 9200 (M9+), ATI Mobility Radeon X800 XT (M28),
    ATI Mobility FireGL V5100 (M28), ATI Mobility Radeon X800 (M28),
    ATI Radeon X850, ATI unknown Radeon / FireGL (R480),
    ATI Radeon X800XT (R423), ATI FireGL V5000 (RV410),
    ATI Radeon X700 XT (RV410), ATI Radeon X700 PRO (RV410),
    ATI Radeon X700 SE (RV410), ATI Radeon X700 (RV410),
    ATI Radeon X1800, ATI Mobility Radeon X1800 XT,
    ATI Mobility Radeon X1800, ATI Mobility FireGL V7200,
    ATI FireGL V7200, ATI FireGL V5300, ATI Mobility FireGL V7100,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1550 64-bit,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI FireGL V3300,
    ATI FireGL V3350, ATI Mobility Radeon X1450,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1650, ATI Mobility FireGL V5200,
    ATI Mobility Radeon X1600, ATI Radeon X1300 XT/X1600 Pro,
    ATI FireGL V3400, ATI Mobility FireGL V5250,
    ATI Mobility Radeon X1700, ATI Mobility Radeon X1700 XT,
    ATI FireGL V5200, ATI Radeon X2300HD, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI AMD Stream Processor,
    ATI RV560, ATI Mobility Radeon X1900, ATI Radeon X1950 GT, ATI RV570,
    ATI FireGL V7400, ATI Radeon 9100 PRO IGP,
    ATI Radeon Mobility 9200 IGP, ATI Radeon X1200, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro,
    ATI Radeon HD 2900 GT, ATI FireGL V8650, ATI FireGL V8600,
    ATI FireGL V7600, ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon HD 4850 x2, ATI FirePro V8750 (FireGL),
    ATI FirePro V7760 (FireGL), ATI Mobility RADEON HD 4850,
    ATI Mobility RADEON HD 4850 X2, ATI FirePro RV770,
    AMD FireStream 9270, AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI FirePro M7750, ATI M98, ATI Mobility Radeon HD 4650,
    ATI Radeon RV730 (AGP), ATI Mobility Radeon HD 4670,
    ATI FirePro M5750, ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI RV610,
    ATI Radeon HD 2400 XT, ATI Radeon HD 2400 Pro,
    ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000, ATI Radeon HD 2350,
    ATI Mobility Radeon HD 2400 XT, ATI Mobility Radeon HD 2400,
    ATI RADEON E2400, ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI Mobility Radeon HD 3870,
    ATI Mobility Radeon HD 3870 X2, ATI Radeon HD3870 X2,
    ATI FireGL V7700, ATI Radeon HD3690, AMD Firestream 9170,
    ATI Radeon HD 4550, ATI Radeon RV710, ATI Radeon HD 4350,
    ATI Mobility Radeon 4300 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3430, ATI FirePro V3700,
    ATI FireMV 2450, ATI Radeon HD 3600 Series, ATI Radeon HD 3650 AGP,
    ATI Radeon HD 3600 PRO, ATI Radeon HD 3600 XT,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon 3000 Graphics, SUMO, SUMO2,
    ATI Radeon HD 4200, ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI Radeon HD 5670, ATI Radeon HD 5570, ATI Radeon HD 5500 Series,
    REDWOOD, ATI Mobility Radeon Graphics, CEDAR, ATI FirePro 2270,
    ATI Radeon HD 5450, CAYMAN, AMD Radeon HD 6900 Series,
    AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6700 Series, TURKS, CAICOS,
    ARUBA, TAHITI, PITCAIRN, VERDE, OLAND, HAINAN, BONAIRE, KABINI,
    MULLINS, KAVERI, HAWAII
[   257.414] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   257.414] (II) FBDEV: driver for framebuffer: fbdev
[   257.414] (II) VESA: driver for VESA chipsets: vesa
[   257.414] xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
[   257.414] (II) [KMS] Kernel modesetting enabled.
[   257.414] (WW) Falling back to old probe method for modesetting
[   257.414] (WW) Falling back to old probe method for fbdev
[   257.414] (II) Loading sub module "fbdevhw"
[   257.414] (II) LoadModule: "fbdevhw"
[   257.414] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   257.414] (II) Module fbdevhw: vendor="X.Org Foundation"
[   257.414]     compiled for 1.18.4, module version = 0.0.2
[   257.414]     ABI class: X.Org Video Driver, version 20.0
[   257.414] (EE) open /dev/fb0: Permission denied
[   257.414] (WW) Falling back to old probe method for vesa
[   257.414] (WW) VGA arbiter: cannot open kernel arbiter, no multi-card support
[   257.414] (II) RADEON(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   257.414] (==) RADEON(0): Depth 24, (--) framebuffer bpp 32
[   257.414] (II) RADEON(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   257.414] (==) RADEON(0): Default visual is TrueColor
[   257.414] (==) RADEON(0): RGB weight 888
[   257.414] (II) RADEON(0): Using 8 bits per RGB (8 bit DAC)
[   257.414] (--) RADEON(0): Chipset: "TAHITI" (ChipID = 0x6798)
[   257.414] (II) Loading sub module "fb"
[   257.414] (II) LoadModule: "fb"
[   257.414] (II) Loading /usr/lib/xorg/modules/libfb.so
[   257.414] (II) Module fb: vendor="X.Org Foundation"
[   257.414]     compiled for 1.18.4, module version = 1.0.0
[   257.414]     ABI class: X.Org ANSI C Emulation, version 0.4
[   257.414] (II) Loading sub module "dri2"
[   257.414] (II) LoadModule: "dri2"
[   257.414] (II) Module "dri2" already built-in
[   257.414] (II) Loading sub module "glamoregl"
[   257.414] (II) LoadModule: "glamoregl"
[   257.415] (II) Loading /usr/lib/xorg/modules/libglamoregl.so
[   257.418] (II) Module glamoregl: vendor="X.Org Foundation"
[   257.418]     compiled for 1.18.4, module version = 1.0.0
[   257.418]     ABI class: X.Org ANSI C Emulation, version 0.4
[   257.418] (II) glamor: OpenGL accelerated X.org driver based.
[   257.439] (II) glamor: EGL version 1.5 (DRI2):
[   257.440] (II) RADEON(0): glamor detected, initialising EGL layer.
[   257.440] (II) RADEON(0): KMS Color Tiling: enabled
[   257.440] (II) RADEON(0): KMS Color Tiling 2D: enabled
[   257.440] (==) RADEON(0): TearFree property default: auto
[   257.440] (II) RADEON(0): KMS Pageflipping: enabled
[   257.448] (II) RADEON(0): Output DisplayPort-0 has no monitor section
[   257.456] (II) RADEON(0): Output DisplayPort-1 has no monitor section
[   257.457] (II) RADEON(0): Output HDMI-0 has no monitor section
[   257.515] (II) RADEON(0): Output DVI-0 has no monitor section
[   257.520] (II) RADEON(0): EDID for output DisplayPort-0
[   257.528] (II) RADEON(0): EDID for output DisplayPort-1
[   257.529] (II) RADEON(0): EDID for output HDMI-0
[   257.587] (II) RADEON(0): EDID for output DVI-0
[   257.587] (II) RADEON(0): Manufacturer: BNQ  Model: 7f2d  Serial#: 21573
[   257.587] (II) RADEON(0): Year: 2014  Week: 3
[   257.587] (II) RADEON(0): EDID Version: 1.3
[   257.587] (II) RADEON(0): Digital Display Input
[   257.587] (II) RADEON(0): Max Image Size [cm]: horiz.: 53  vert.: 30
[   257.587] (II) RADEON(0): Gamma: 2.20
[   257.587] (II) RADEON(0): DPMS capabilities: Off
[   257.587] (II) RADEON(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   257.587] (II) RADEON(0): Default color space is primary color space
[   257.587] (II) RADEON(0): First detailed timing is preferred mode
[   257.587] (II) RADEON(0): redX: 0.650 redY: 0.329   greenX: 0.331 greenY: 0.622
[   257.587] (II) RADEON(0): blueX: 0.151 blueY: 0.053   whiteX: 0.312 whiteY: 0.329
[   257.587] (II) RADEON(0): Supported established timings:
[   257.587] (II) RADEON(0): 720x400@70Hz
[   257.587] (II) RADEON(0): 640x480@60Hz
[   257.587] (II) RADEON(0): 640x480@75Hz
[   257.587] (II) RADEON(0): 800x600@60Hz
[   257.587] (II) RADEON(0): 800x600@75Hz
[   257.587] (II) RADEON(0): 832x624@75Hz
[   257.587] (II) RADEON(0): 1024x768@60Hz
[   257.587] (II) RADEON(0): 1024x768@75Hz
[   257.587] (II) RADEON(0): 1280x1024@75Hz
[   257.587] (II) RADEON(0): 1152x864@75Hz
[   257.587] (II) RADEON(0): Manufacturer's mask: 0
[   257.587] (II) RADEON(0): Supported standard timings:
[   257.587] (II) RADEON(0): #0: hsize: 1920  vsize 1080  refresh: 60  vid: 49361
[   257.587] (II) RADEON(0): #1: hsize: 800  vsize 600  refresh: 120  vid: 31813
[   257.587] (II) RADEON(0): #2: hsize: 1024  vsize 768  refresh: 120  vid: 31841
[   257.587] (II) RADEON(0): #3: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   257.587] (II) RADEON(0): #4: hsize: 1280  vsize 1024  refresh: 120  vid: 48257
[   257.587] (II) RADEON(0): #5: hsize: 1440  vsize 900  refresh: 120  vid: 15509
[   257.587] (II) RADEON(0): #6: hsize: 640  vsize 480  refresh: 120  vid: 31793
[   257.587] (II) RADEON(0): Supported detailed timing:
[   257.587] (II) RADEON(0): clock: 148.5 MHz   Image Size:  531 x 298 mm
[   257.587] (II) RADEON(0): h_active: 1920  h_sync: 2008  h_sync_end 2052 h_blank_end 2200 h_border: 0
[   257.587] (II) RADEON(0): v_active: 1080  v_sync: 1084  v_sync_end 1089 v_blanking: 1125 v_border: 0
[   257.587] (II) RADEON(0): Serial No: R1E01129SL0
[   257.587] (II) RADEON(0): Ranges: V min: 56 V max: 144 Hz, H min: 30 H max: 160 kHz, PixClock max 335 MHz
[   257.587] (II) RADEON(0): Monitor name: BenQ XL2420Z
[   257.587] (II) RADEON(0): Supported detailed timing:
[   257.587] (II) RADEON(0): clock: 235.5 MHz   Image Size:  531 x 298 mm
[   257.587] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[   257.587] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1133 v_border: 0
[   257.587] (II) RADEON(0): Supported detailed timing:
[   257.587] (II) RADEON(0): clock: 285.5 MHz   Image Size:  531 x 298 mm
[   257.587] (II) RADEON(0): h_active: 1920  h_sync: 1968  h_sync_end 2000 h_blank_end 2080 h_border: 0
[   257.587] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1144 v_border: 0
[   257.587] (II) RADEON(0): Supported detailed timing:
[   257.587] (II) RADEON(0): clock: 325.1 MHz   Image Size:  531 x 298 mm
[   257.587] (II) RADEON(0): h_active: 1920  h_sync: 1944  h_sync_end 1976 h_blank_end 2056 h_border: 0
[   257.587] (II) RADEON(0): v_active: 1080  v_sync: 1083  v_sync_end 1088 v_blanking: 1098 v_border: 0
[   257.587] (II) RADEON(0): Number of EDID sections to follow: 1
[   257.587] (II) RADEON(0): EDID (in hex):
[   257.587] (II) RADEON(0):     00ffffffffffff0009d12d7f45540000
[   257.587] (II) RADEON(0):     0318010380351e782e9de1a654549f26
[   257.587] (II) RADEON(0):     0d5054a56b80d1c0457c617c818081bc
[   257.587] (II) RADEON(0):     953c317c0101023a801871382d40582c
[   257.587] (II) RADEON(0):     4500132a2100001e000000ff00523145
[   257.587] (II) RADEON(0):     3031313239534c300a20000000fd0038
[   257.587] (II) RADEON(0):     901ea021000a202020202020000000fc
[   257.587] (II) RADEON(0):     0042656e5120584c323432305a0a01e3
[   257.587] (II) RADEON(0):     02010400fe5b80a07038354030203500
[   257.587] (II) RADEON(0):     132a2100001a866f80a0703840403020
[   257.587] (II) RADEON(0):     3500132a2100001afc7e808870381240
[   257.587] (II) RADEON(0):     18203500132a2100001e000000000000
[   257.587] (II) RADEON(0):     00000000000000000000000000000000
[   257.587] (II) RADEON(0):     00000000000000000000000000000000
[   257.587] (II) RADEON(0):     00000000000000000000000000000000
[   257.587] (II) RADEON(0):     000000000000000000000000000000c7
[   257.587] (II) RADEON(0): Printing probed modes for output DVI-0
[   257.587] (II) RADEON(0): Modeline "1920x1080"x60.0  148.50  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.5 kHz eP)
[   257.587] (II) RADEON(0): Modeline "1920x1080"x144.0  325.08  1920 1944 1976 2056  1080 1083 1088 1098 +hsync +vsync (158.1 kHz e)
[   257.587] (II) RADEON(0): Modeline "1920x1080"x120.0  285.50  1920 1968 2000 2080  1080 1083 1088 1144 +hsync -vsync (137.3 kHz e)
[   257.587] (II) RADEON(0): Modeline "1920x1080"x99.9  235.50  1920 1968 2000 2080  1080 1083 1088 1133 +hsync -vsync (113.2 kHz e)
[   257.587] (II) RADEON(0): Modeline "1920x1080"x59.9  148.35  1920 2008 2052 2200  1080 1084 1089 1125 +hsync +vsync (67.4 kHz e)
[   257.587] (II) RADEON(0): Modeline "1280x1024"x120.0  187.25  1280 1328 1360 1440  1024 1027 1034 1084 +hsync -vsync (130.0 kHz e)
[   257.587] (II) RADEON(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   257.587] (II) RADEON(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   257.587] (II) RADEON(0): Modeline "1440x900"x119.9  182.75  1440 1488 1520 1600  900 903 909 953 +hsync -vsync (114.2 kHz e)
[   257.587] (II) RADEON(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   257.587] (II) RADEON(0): Modeline "1024x768"x120.0  115.50  1024 1072 1104 1184  768 771 775 813 +hsync -vsync (97.6 kHz e)
[   257.587] (II) RADEON(0): Modeline "1024x768"x75.1   78.80  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.1 kHz e)
[   257.587] (II) RADEON(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   257.587] (II) RADEON(0): Modeline "832x624"x74.6   57.28  832 864 928 1152  624 625 628 667 -hsync -vsync (49.7 kHz e)
[   257.587] (II) RADEON(0): Modeline "800x600"x120.0   73.25  800 848 880 960  600 603 607 636 +hsync -vsync (76.3 kHz e)
[   257.587] (II) RADEON(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   257.587] (II) RADEON(0): Modeline "800x600"x60.3   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   257.587] (II) RADEON(0): Modeline "640x480"x120.0   52.40  640 680 744 848  480 481 484 515 -hsync +vsync (61.8 kHz)
[   257.587] (II) RADEON(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   257.587] (II) RADEON(0): Modeline "640x480"x60.0   25.20  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   257.587] (II) RADEON(0): Modeline "640x480"x59.9   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   257.587] (II) RADEON(0): Modeline "720x400"x70.1   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   257.587] (II) RADEON(0): Output DisplayPort-0 disconnected
[   257.587] (II) RADEON(0): Output DisplayPort-1 disconnected
[   257.587] (II) RADEON(0): Output HDMI-0 disconnected
[   257.587] (II) RADEON(0): Output DVI-0 connected
[   257.587] (II) RADEON(0): Using exact sizes for initial modes
[   257.587] (II) RADEON(0): Output DVI-0 using initial mode 1920x1080 +0+0
[   257.587] (II) RADEON(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   257.587] (II) RADEON(0): mem size init: gart size :7fbcc000 vram size: s:c0000000 visible:bf12d000
[   257.587] (==) RADEON(0): DPI set to (96, 96)
[   257.587] (II) Loading sub module "ramdac"
[   257.587] (II) LoadModule: "ramdac"
[   257.587] (II) Module "ramdac" already built-in
[   257.587] (II) UnloadModule: "modesetting"
[   257.587] (II) Unloading modesetting
[   257.587] (II) UnloadModule: "fbdev"
[   257.587] (II) Unloading fbdev
[   257.587] (II) UnloadSubModule: "fbdevhw"
[   257.587] (II) Unloading fbdevhw
[   257.587] (II) UnloadModule: "vesa"
[   257.587] (II) Unloading vesa
[   257.587] (--) Depth 24 pixmap format is 32 bpp
[   257.587] (II) RADEON(0): [DRI2] Setup complete
[   257.587] (II) RADEON(0): [DRI2]   DRI driver: radeonsi
[   257.587] (II) RADEON(0): [DRI2]   VDPAU driver: radeonsi
[   257.587] (II) RADEON(0): Front buffer size: 8640K
[   257.587] (II) RADEON(0): VRAM usage limit set to 2809630K
[   257.587] (II) RADEON(0): SYNC extension fences enabled
[   257.587] (II) RADEON(0): Present extension enabled
[   257.587] (==) RADEON(0): DRI3 enabled
[   257.587] (==) RADEON(0): Backing store enabled
[   257.587] (II) RADEON(0): Direct rendering enabled
[   257.589] (II) RADEON(0): Use GLAMOR acceleration.
[   257.589] (II) RADEON(0): Acceleration enabled
[   257.589] (==) RADEON(0): DPMS enabled
[   257.589] (==) RADEON(0): Silken mouse enabled
[   257.589] (II) RADEON(0): Set up textured video (glamor)
[   257.589] (II) RADEON(0): [XvMC] Associated with GLAMOR Textured Video.
[   257.589] (II) RADEON(0): [XvMC] Extension initialized.
[   257.589] (II) RADEON(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   257.589] (--) RandR disabled
[   257.591] (II) SELinux: Disabled on system
[   257.592] (II) AIGLX: enabled GLX_MESA_copy_sub_buffer
[   257.592] (II) AIGLX: enabled GLX_ARB_create_context
[   257.592] (II) AIGLX: enabled GLX_ARB_create_context_profile
[   257.592] (II) AIGLX: enabled GLX_EXT_create_context_es{,2}_profile
[   257.592] (II) AIGLX: enabled GLX_INTEL_swap_event
[   257.592] (II) AIGLX: enabled GLX_SGI_swap_control and GLX_MESA_swap_control
[   257.593] (II) AIGLX: enabled GLX_EXT_framebuffer_sRGB
[   257.593] (II) AIGLX: enabled GLX_ARB_fbconfig_float
[   257.593] (II) AIGLX: enabled GLX_EXT_fbconfig_packed_float
[   257.593] (II) AIGLX: GLX_EXT_texture_from_pixmap backed by buffer objects
[   257.593] (II) AIGLX: enabled GLX_ARB_create_context_robustness
[   257.593] (II) AIGLX: Loaded and initialized radeonsi
[   257.593] (II) GLX: Initialized DRI2 GL provider for screen 0
[   257.597] (II) RADEON(0): Setting screen physical size to 508 x 285
[   257.618] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   257.618] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   257.618] (II) LoadModule: "evdev"
[   257.618] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   257.618] (II) Module evdev: vendor="X.Org Foundation"
[   257.618]     compiled for 1.18.1, module version = 2.10.1
[   257.618]     Module class: X.Org XInput Driver
[   257.618]     ABI class: X.Org XInput driver, version 22.1
[   257.619] (II) systemd-logind: got fd for /dev/input/event1 13:65 fd 15 paused 0
[   257.619] (II) Using input driver 'evdev' for 'Power Button'
[   257.619] (**) Power Button: always reports core events
[   257.619] (**) evdev: Power Button: Device: "/dev/input/event1"
[   257.619] (--) evdev: Power Button: Vendor 0 Product 0x1
[   257.619] (--) evdev: Power Button: Found keys
[   257.619] (II) evdev: Power Button: Configuring as keyboard
[   257.619] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   257.619] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   257.619] (**) Option "xkb_rules" "evdev"
[   257.619] (**) Option "xkb_model" "pc105"
[   257.619] (**) Option "xkb_layout" "pl"
[   257.627] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   257.627] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   257.627] (II) systemd-logind: got fd for /dev/input/event0 13:64 fd 16 paused 0
[   257.627] (II) Using input driver 'evdev' for 'Power Button'
[   257.627] (**) Power Button: always reports core events
[   257.627] (**) evdev: Power Button: Device: "/dev/input/event0"
[   257.627] (--) evdev: Power Button: Vendor 0 Product 0x1
[   257.627] (--) evdev: Power Button: Found keys
[   257.627] (II) evdev: Power Button: Configuring as keyboard
[   257.627] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   257.627] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   257.627] (**) Option "xkb_rules" "evdev"
[   257.627] (**) Option "xkb_model" "pc105"
[   257.627] (**) Option "xkb_layout" "pl"
[   257.628] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=10 (/dev/input/event10)
[   257.628] (II) No input driver specified, ignoring this device.
[   257.628] (II) This device may have been added with another device file.
[   257.628] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=11 (/dev/input/event11)
[   257.628] (II) No input driver specified, ignoring this device.
[   257.628] (II) This device may have been added with another device file.
[   257.628] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=3 (/dev/input/event6)
[   257.628] (II) No input driver specified, ignoring this device.
[   257.628] (II) This device may have been added with another device file.
[   257.628] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=7 (/dev/input/event7)
[   257.628] (II) No input driver specified, ignoring this device.
[   257.628] (II) This device may have been added with another device file.
[   257.628] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=8 (/dev/input/event8)
[   257.628] (II) No input driver specified, ignoring this device.
[   257.628] (II) This device may have been added with another device file.
[   257.629] (II) config/udev: Adding input device HDA ATI HDMI HDMI/DP,pcm=9 (/dev/input/event9)
[   257.629] (II) No input driver specified, ignoring this device.
[   257.629] (II) This device may have been added with another device file.
[   257.629] (II) config/udev: Adding input device Razer Razer DeathAdder Chroma (/dev/input/event3)
[   257.629] (**) Razer Razer DeathAdder Chroma: Applying InputClass "evdev pointer catchall"
[   257.684] (II) systemd-logind: got fd for /dev/input/event3 13:67 fd 17 paused 0
[   257.684] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder Chroma'
[   257.684] (**) Razer Razer DeathAdder Chroma: always reports core events
[   257.684] (**) evdev: Razer Razer DeathAdder Chroma: Device: "/dev/input/event3"
[   257.684] (--) evdev: Razer Razer DeathAdder Chroma: Vendor 0x1532 Product 0x43
[   257.684] (--) evdev: Razer Razer DeathAdder Chroma: Found 9 mouse buttons
[   257.684] (--) evdev: Razer Razer DeathAdder Chroma: Found scroll wheel(s)
[   257.684] (--) evdev: Razer Razer DeathAdder Chroma: Found relative axes
[   257.684] (--) evdev: Razer Razer DeathAdder Chroma: Found x and y relative axes
[   257.684] (II) evdev: Razer Razer DeathAdder Chroma: Configuring as mouse
[   257.684] (II) evdev: Razer Razer DeathAdder Chroma: Adding scrollwheel support
[   257.684] (**) evdev: Razer Razer DeathAdder Chroma: YAxisMapping: buttons 4 and 5
[   257.684] (**) evdev: Razer Razer DeathAdder Chroma: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   257.684] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.0/0003:1532:0043.0001/input/input3/event3"
[   257.684] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder Chroma" (type: MOUSE, id 8)
[   257.684] (II) evdev: Razer Razer DeathAdder Chroma: initialized for relative axes.
[   257.684] (**) Razer Razer DeathAdder Chroma: (accel) keeping acceleration scheme 1
[   257.684] (**) Razer Razer DeathAdder Chroma: (accel) acceleration profile 0
[   257.684] (**) Razer Razer DeathAdder Chroma: (accel) acceleration factor: 2.000
[   257.684] (**) Razer Razer DeathAdder Chroma: (accel) acceleration threshold: 4
[   257.684] (II) config/udev: Adding input device Razer Razer DeathAdder Chroma (/dev/input/mouse0)
[   257.684] (II) No input driver specified, ignoring this device.
[   257.684] (II) This device may have been added with another device file.
[   257.684] (II) config/udev: Adding input device Razer Razer DeathAdder Chroma (/dev/input/event4)
[   257.684] (**) Razer Razer DeathAdder Chroma: Applying InputClass "evdev keyboard catchall"
[   257.685] (II) systemd-logind: got fd for /dev/input/event4 13:68 fd 18 paused 0
[   257.685] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder Chroma'
[   257.685] (**) Razer Razer DeathAdder Chroma: always reports core events
[   257.685] (**) evdev: Razer Razer DeathAdder Chroma: Device: "/dev/input/event4"
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Vendor 0x1532 Product 0x43
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Found 1 mouse buttons
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Found scroll wheel(s)
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Found relative axes
[   257.685] (II) evdev: Razer Razer DeathAdder Chroma: Forcing relative x/y axes to exist.
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Found absolute axes
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Found absolute multitouch axes
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Fake MT device detected
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Found keys
[   257.685] (II) evdev: Razer Razer DeathAdder Chroma: Configuring as mouse
[   257.685] (II) evdev: Razer Razer DeathAdder Chroma: Configuring as keyboard
[   257.685] (II) evdev: Razer Razer DeathAdder Chroma: Adding scrollwheel support
[   257.685] (**) evdev: Razer Razer DeathAdder Chroma: YAxisMapping: buttons 4 and 5
[   257.685] (**) evdev: Razer Razer DeathAdder Chroma: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   257.685] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.1/0003:1532:0043.0002/input/input4/event4"
[   257.685] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder Chroma" (type: KEYBOARD, id 9)
[   257.685] (**) Option "xkb_rules" "evdev"
[   257.685] (**) Option "xkb_model" "pc105"
[   257.685] (**) Option "xkb_layout" "pl"
[   257.685] (II) evdev: Razer Razer DeathAdder Chroma: initialized for relative axes.
[   257.685] (WW) evdev: Razer Razer DeathAdder Chroma: ignoring absolute axes.
[   257.685] (**) Razer Razer DeathAdder Chroma: (accel) keeping acceleration scheme 1
[   257.685] (**) Razer Razer DeathAdder Chroma: (accel) acceleration profile 0
[   257.685] (**) Razer Razer DeathAdder Chroma: (accel) acceleration factor: 2.000
[   257.685] (**) Razer Razer DeathAdder Chroma: (accel) acceleration threshold: 4
[   257.685] (II) config/udev: Adding input device Razer Razer DeathAdder Chroma (/dev/input/event5)
[   257.685] (**) Razer Razer DeathAdder Chroma: Applying InputClass "evdev keyboard catchall"
[   257.685] (II) systemd-logind: got fd for /dev/input/event5 13:69 fd 19 paused 0
[   257.685] (II) Using input driver 'evdev' for 'Razer Razer DeathAdder Chroma'
[   257.685] (**) Razer Razer DeathAdder Chroma: always reports core events
[   257.685] (**) evdev: Razer Razer DeathAdder Chroma: Device: "/dev/input/event5"
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Vendor 0x1532 Product 0x43
[   257.685] (--) evdev: Razer Razer DeathAdder Chroma: Found keys
[   257.685] (II) evdev: Razer Razer DeathAdder Chroma: Configuring as keyboard
[   257.685] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:14.0/usb3/3-14/3-14:1.2/0003:1532:0043.0003/input/input5/event5"
[   257.685] (II) XINPUT: Adding extended input device "Razer Razer DeathAdder Chroma" (type: KEYBOARD, id 10)
[   257.685] (**) Option "xkb_rules" "evdev"
[   257.685] (**) Option "xkb_model" "pc105"
[   257.685] (**) Option "xkb_layout" "pl"
[   257.686] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event12)
[   257.686] (II) No input driver specified, ignoring this device.
[   257.686] (II) This device may have been added with another device file.
[   257.686] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event13)
[   257.686] (II) No input driver specified, ignoring this device.
[   257.686] (II) This device may have been added with another device file.
[   257.686] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event14)
[   257.686] (II) No input driver specified, ignoring this device.
[   257.686] (II) This device may have been added with another device file.
[   257.686] (II) config/udev: Adding input device HDA Intel PCH Line Out Front (/dev/input/event15)
[   257.686] (II) No input driver specified, ignoring this device.
[   257.686] (II) This device may have been added with another device file.
[   257.686] (II) config/udev: Adding input device HDA Intel PCH Line Out Surround (/dev/input/event16)
[   257.686] (II) No input driver specified, ignoring this device.
[   257.686] (II) This device may have been added with another device file.
[   257.686] (II) config/udev: Adding input device HDA Intel PCH Line Out CLFE (/dev/input/event17)
[   257.686] (II) No input driver specified, ignoring this device.
[   257.687] (II) This device may have been added with another device file.
[   257.687] (II) config/udev: Adding input device HDA Intel PCH Line Out Side (/dev/input/event18)
[   257.687] (II) No input driver specified, ignoring this device.
[   257.687] (II) This device may have been added with another device file.
[   257.687] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event19)
[   257.687] (II) No input driver specified, ignoring this device.
[   257.687] (II) This device may have been added with another device file.
[   257.687] (II) config/udev: Adding input device Eee PC WMI hotkeys (/dev/input/event20)
[   257.687] (**) Eee PC WMI hotkeys: Applying InputClass "evdev keyboard catchall"
[   257.687] (II) systemd-logind: got fd for /dev/input/event20 13:84 fd 20 paused 0
[   257.687] (II) Using input driver 'evdev' for 'Eee PC WMI hotkeys'
[   257.687] (**) Eee PC WMI hotkeys: always reports core events
[   257.687] (**) evdev: Eee PC WMI hotkeys: Device: "/dev/input/event20"
[   257.687] (--) evdev: Eee PC WMI hotkeys: Vendor 0 Product 0
[   257.687] (--) evdev: Eee PC WMI hotkeys: Found keys
[   257.687] (II) evdev: Eee PC WMI hotkeys: Configuring as keyboard
[   257.687] (**) Option "config_info" "udev:/sys/devices/platform/eeepc-wmi/input/input20/event20"
[   257.687] (II) XINPUT: Adding extended input device "Eee PC WMI hotkeys" (type: KEYBOARD, id 11)
[   257.687] (**) Option "xkb_rules" "evdev"
[   257.687] (**) Option "xkb_model" "pc105"
[   257.687] (**) Option "xkb_layout" "pl"
[   257.688] (II) config/udev: Adding input device AT Translated Set 2 keyboard (/dev/input/event2)
[   257.688] (**) AT Translated Set 2 keyboard: Applying InputClass "evdev keyboard catchall"
[   257.688] (II) systemd-logind: got fd for /dev/input/event2 13:66 fd 21 paused 0
[   257.688] (II) Using input driver 'evdev' for 'AT Translated Set 2 keyboard'
[   257.688] (**) AT Translated Set 2 keyboard: always reports core events
[   257.688] (**) evdev: AT Translated Set 2 keyboard: Device: "/dev/input/event2"
[   257.688] (--) evdev: AT Translated Set 2 keyboard: Vendor 0x1 Product 0x1
[   257.688] (--) evdev: AT Translated Set 2 keyboard: Found keys
[   257.688] (II) evdev: AT Translated Set 2 keyboard: Configuring as keyboard
[   257.688] (**) Option "config_info" "udev:/sys/devices/platform/i8042/serio0/input/input2/event2"
[   257.688] (II) XINPUT: Adding extended input device "AT Translated Set 2 keyboard" (type: KEYBOARD, id 12)
[   257.688] (**) Option "xkb_rules" "evdev"
[   257.688] (**) Option "xkb_model" "pc105"
[   257.688] (**) Option "xkb_layout" "pl"
[   257.879] (II) evdev: AT Translated Set 2 keyboard: Close
[   257.879] (II) UnloadModule: "evdev"
[   257.879] (II) systemd-logind: releasing fd for 13:66
[   257.928] (II) evdev: Eee PC WMI hotkeys: Close
[   257.928] (II) UnloadModule: "evdev"
[   257.928] (II) systemd-logind: releasing fd for 13:84
[   257.944] (II) evdev: Razer Razer DeathAdder Chroma: Close
[   257.944] (II) UnloadModule: "evdev"
[   257.944] (II) systemd-logind: releasing fd for 13:69
[   257.972] (II) evdev: Razer Razer DeathAdder Chroma: Close
[   257.972] (II) UnloadModule: "evdev"
[   257.972] (II) systemd-logind: releasing fd for 13:68
[   257.996] (II) evdev: Razer Razer DeathAdder Chroma: Close
[   257.996] (II) UnloadModule: "evdev"
[   257.996] (II) systemd-logind: releasing fd for 13:67
[   258.020] (II) evdev: Power Button: Close
[   258.020] (II) UnloadModule: "evdev"
[   258.020] (II) systemd-logind: releasing fd for 13:64
[   258.032] (II) evdev: Power Button: Close
[   258.032] (II) UnloadModule: "evdev"
[   258.032] (II) systemd-logind: releasing fd for 13:65
[   258.047] (II) Server terminated successfully (0). Closing log file.

```

---

### Post by rtimai on 2018-06-14
@archi2:  Absolutely do not feel stupid! You're doing very well for someone who claims to be uncomfortable at the console, and you succeeded in attempting to boot previous kernels as Impavidus suggested. 

Q1: How are you communicating now? 

Q2: The fsck (file system check) message on startup that you mentioned shows you're booting /dev/sdc1 (on single boot systems it's usually partition sda1)-- do you have multi-boot with an alternate operating system?

 sudo fdisk --list /dev/sd* ## List ATA disks - USE EXTREME CAUTION W/ OTHER OPTIONS

Q3:  If you can boot the current kernel in Recovery Mode, in the Software & Updates application, "Additional Drivers" page, are you using any proprietary drivers? I saw a thread on the AskUbuntu forum where a misguided user suggested installing an nVidia proprietary driver in response to the "dev/sda1: clean" message (which is NOT an error msg.) The reason I ask is my wife's HP is also an AMD64/ATI system, and I've found the opensource driver more reliable than the proprietary one -- and I'm wondering if disabling an nVidia proprietary driver might fix the graphics issue. (This might not even be a graphics issue, but a stall caused by another component failing to respond during the startup sequence. See below.)

The reason I forced a shutdown and restarted as many as 6 times is that I noticed small differences in behavior each time, and it seemed as if the boot procedure was *adjusting* itself on each reboot. My wife's HP dv6 has several keys w LED lights, and they lit up in a different order and blinking patterns on each reboot. I know it sounds crazy, but her computer recovered. And would you know it, the bootup stall happened yet AGAIN today, and again recovered. And yes, there were still more kernel updates waiting to be installed. I wonder if the stall is just updates being downloaded in the background. Upon login Software Updater indicated that the updates were already downloaded, waiting to be installed.

Q4: If you can't boot Recovery Mode, and have your Ubuntu Live CD/USB drive, you can boot from that. If you're still running 16.04, is there any reason you can't install 18.04 LTS? -- it's a long-term-support release. Booting from the external media, you should be able to copy crucial data to a backup.

TIP1: in the console enter the line below for session information (yes, case-sensitive):
  lsb_release -d ; uname -r ; gnome-shell --version ; echo $DESKTOP_SESSION

TIP2: In console, Shift-Ctrl-C to Copy, Shift-Ctrl-V to Paste. Everywhere else, it's just Ctrl-C or -V.

BTW, pardon my general suggestions. I very recently migrated from Debian to Ubuntu, so I'm not certain about procedural differences. Beyond the above, there's not much more I would venture to suggest. Good luck.

---

### Post by archi2 on 2018-06-15
> [COLOR=#000000]Q1: How are you communicating now? [/COLOR]
I am using different computer. I learned how to copy files from console to network drive so I can access it from this machine.

> [COLOR=#000000]Q2: The fsck (file system check) message on startup that you mentioned shows you're booting /dev/sdc1 (on single boot systems it's usually partition sda1)-- do you have multi-boot with an alternate operating system?[/COLOR]

[COLOR=#000000]sudo fdisk --list /dev/sd* ## List ATA disks - USE EXTREME CAUTION W/ OTHER OPTIONS[/COLOR]
Yes it is multiboot. I did not install or configure it. Here is fdisk:
```
Failed to read extended partition table (offset=30818306): Invalid argument
Disk /dev/sda: 1.8 TiB, 2000398934016 bytes, 3907029168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: 5AF9BD5D-78EF-4005-8257-FB9D2EE3C5F5


Device      Start        End    Sectors  Size Type
/dev/sda2  409640 3906766983 3906357344  1.8T Apple HFS/HFS+
Disk /dev/sda2: 1.8 TiB, 2000054960128 bytes, 3906357344 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sdb: 232.9 GiB, 250059350016 bytes, 488397168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: C3A9DEF7-CF3C-44FF-9ED0-9F1D7DF91B8C


Device         Start       End   Sectors   Size Type
/dev/sdb1         40    409639    409600   200M EFI System
/dev/sdb2     409640 487127591 486717952 232.1G Apple HFS/HFS+
/dev/sdb3  487127592 488397127   1269536 619.9M Apple boot
Disk /dev/sdb1: 200 MiB, 209715200 bytes, 409600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: dos
Disk identifier: 0x00000000
Disk /dev/sdb2: 232.1 GiB, 249199591424 bytes, 486717952 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sdb3: 619.9 MiB, 650002432 bytes, 1269536 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk /dev/sdc: 931.5 GiB, 1000204886016 bytes, 1953525168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x0008d4cf


Device     Boot     Start        End    Sectors   Size Id Type
/dev/sdc1            2048  359475199  359473152 171.4G 83 Linux
/dev/sdc2       360001534 1953523711 1593522178 759.9G  5 Extended
/dev/sdc3  *    359475200  359999487     524288   256M  b W95 FAT32
/dev/sdc5       360001536  390819839   30818304  14.7G 82 Linux swap / Solaris
/dev/sdc6       390821888 1953523711 1562701824 745.2G 83 Linux


Partition table entries are not in disk order.
Disk /dev/sdc1: 171.4 GiB, 184050253824 bytes, 359473152 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdc2: 1 KiB, 1024 bytes, 2 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000


Device      Boot    Start        End    Sectors   Size Id Type
/dev/sdc2p1             2   30818305   30818304  14.7G 82 Linux swap / Solaris
/dev/sdc2p2      30818306 1593522177 1562703872 745.2G  5 Extended
Disk /dev/sdc3: 256 MiB, 268435456 bytes, 524288 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000
Disk /dev/sdc5: 14.7 GiB, 15778971648 bytes, 30818304 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdc6: 745.2 GiB, 800103333888 bytes, 1562701824 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdd: 465.8 GiB, 500106780160 bytes, 976771055 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 264CD83D-776E-4300-B05A-9A8DC5EB666B


Device       Start       End   Sectors   Size Type
/dev/sdd1     2048    923647    921600   450M Windows recovery environment
/dev/sdd2   923648   1128447    204800   100M EFI System
/dev/sdd3  1128448   1161215     32768    16M Microsoft reserved
/dev/sdd4  1161216 976769023 975607808 465.2G Microsoft basic data
Disk /dev/sdd1: 450 MiB, 471859200 bytes, 921600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x73736572


Device      Boot      Start        End    Sectors   Size Id Type
/dev/sdd1p1      1920221984 3736432267 1816210284   866G 72 unknown
/dev/sdd1p2      1936028192 3889681299 1953653108 931.6G 6c unknown
/dev/sdd1p3               0          0          0     0B  0 Empty
/dev/sdd1p4        27722122   27722568        447 223.5K  0 Empty


Partition table entries are not in disk order.
Disk /dev/sdd2: 100 MiB, 104857600 bytes, 204800 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x500a0dff


Device      Boot      Start        End    Sectors   Size Id Type
/dev/sdd2p1      1948285285 3650263507 1701978223 811.6G 6e unknown
/dev/sdd2p2               0          0          0     0B 74 unknown
/dev/sdd2p4        28049408   28049848        441 220.5K  0 Empty


Partition table entries are not in disk order.
Disk /dev/sdd3: 16 MiB, 16777216 bytes, 32768 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk /dev/sdd4: 465.2 GiB, 499511197696 bytes, 975607808 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x73736572


Device      Boot      Start        End    Sectors   Size Id Type
/dev/sdd4p1      1920221984 3736432267 1816210284   866G 72 unknown
/dev/sdd4p2      1936028192 3889681299 1953653108 931.6G 6c unknown
/dev/sdd4p3               0          0          0     0B  0 Empty
/dev/sdd4p4        27722122   27722568        447 223.5K  0 Empty


Partition table entries are not in disk order.
Disk /dev/sde: 7.5 GiB, 8004304896 bytes, 15633408 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0xa049978a


Device     Boot   Start      End  Sectors   Size Id Type
/dev/sde1             2  1953129  1953128 953.7M  b W95 FAT32
/dev/sde2       1953131 15633407 13680277   6.5G af HFS / HFS+
Disk /dev/sde1: 953.7 MiB, 1000001536 bytes, 1953128 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x00000000
Disk /dev/sde2: 6.5 GiB, 7004301824 bytes, 13680277 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes

```> [COLOR=#000000]Q3: If you can boot the current kernel in Recovery Mode, in the Software & Updates application, "Additional Drivers" page, are you using any proprietary drivers? [/COLOR]

I did recovery mode and started fsck hence "clean" output, I think, not sure.
I am not able to run failsafeX it does not work. No idea how to check additional drivers. I don't think I have nvidia drivers.
> [COLOR=#000000]Q4: If you can't boot Recovery Mode, and have your Ubuntu Live CD/USB drive, you can boot from that. If you're still running 16.04, is there any reason you can't install 18.04 LTS? -- it's a long-term-support release. Booting from the external media, you should be able to copy crucial data to a backup.[/COLOR]
Upgrade from 16.04 to next LTS will be possible after 18.04.1 release as I remember from earlier LTS upgrades. Complete reinstall is the last option. It is a multiboot. I have no idea how to do it and if sth goes wrong how to fix it.
> [COLOR=#000000]lsb_release -d ; uname -r ; gnome-shell --version ; echo $DESKTOP_SESSION[/COLOR]
```
Description:    Ubuntu 16.04.4 LTS


4.4.0-128-generic


WARNING:root:could not open file '/etc/apt/sources.list'


The program 'gnome-shell' is currently not installed. You can install it by typing:
sudo apt install gnome-shell
You will have to enable the component called 'universe'

```
There was no output from echo.


```
xf86EnableIOPorts: failed to set IOPL for I/O (Operation not permitted)
```
I have been trying to find solution for this error but nothing helped.

---

### Post by rtimai on 2018-06-15
@archi2:  I never saw such convoluted disk partitioning before. Looks like there are unused disk space, remnants of previous OS installations, with multiple filesystem formats. And there seems critical data and Linux system components are missing. I may be wrong -- if I wrongly presumed that you were running Gnome 3 desktop. Still, my opinion is that the damage is complicated, and beyond fixing by remote advice. Sorry.

---

### Post by archi2 on 2018-06-21
I tried everything I have found online but no joy. I finally reinstalled system. Thanx for your help

---

