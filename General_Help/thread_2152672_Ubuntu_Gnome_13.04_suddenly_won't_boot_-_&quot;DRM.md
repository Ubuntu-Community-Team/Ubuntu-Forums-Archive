---
title: "Ubuntu Gnome 13.04 suddenly won't boot - &quot;DRM: Fill_in_dev failed.&quot;"
date: 2013-06-08
forum: General Help
---

### Post by vaguely_clear on 2013-06-08
So I have a fresh install of Ubuntu Gnome 13.04 that worked well for a day or two, long enough to get needed software installed and use it for a bit. Now, suddenly, when I try to boot, I receive the following messages (they flash on the screen for a few brief moments):

```

[     2.639957] [drm:drm_pci_agp_init] *ERROR* Cannot initialize the agpgart module.
[     2.639961] DRM: Fill_in_dev failed.

```

and then the machine locks up at a blank black screen.

Here are some things that might be relevant, though I'm just totally guessing, as I have no idea what this error message means:
[LIST=1]
[*]I have a Radeon 6850 and am using the proprietary fglrx-updates package. This card/driver has given me fits before, but my Windows install seems to be working just fine still, so I don't suspect a hardware issue.
[*]I have to use "quiet splash nomodeset" to get Ubuntu to boot with this card on 12.10 or 13.04.
[*]I can't think of any substantial change that was made before the boot failure, but I did use some PPAs for what I think are trivial things. If someone could let me know a way to check all the PPAs in use on the system from a root prompt, I could provide that.
[/LIST]

Here are some things that I have tried so far:
[LIST=1]
[*]I ran filesystem check, check for broken packages, and autoremove from the recovery menu. No dice.
[*]I tried booting in low graphics mode, but I get the same errors flashing on the screen before a lock up.
[*]From the root prompt, I issues the command ```
startx
``` and I was presented with a working gui, but logged in as root obviously. I didn't do anything as root, just logged back out, but gnome seemed to be working fine.
[/LIST]

Here is what I am planning to do next: remove the 6850 and try running the machine on the built in Intel HD 4000, and, if necessary, purge fglrx.

I'd love it if someone could convince me to try something else first, though. I've struggled with fglrx in the past, and I was quite happy that it worked well without fiddling in 13.04.

I found some threads around the net with these errors, but most were quite old, from 2009 or 2010.

Anybody have thoughts?

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]vaguely_clear; Hey ...
You seem to know your way around... What I would do if I were presented with this situation.
Boot to the grub menu and in the boot parameters line, I would remove "quiet and splash" and use the term "text" in place; Booting to the text log in....play about with some cli commands to verify the system's integrity...in particular I want to know what graphics driver is loaded:
[/COLOR]```
sudo lshw -C display
``` make note of the driver(if any) that is presently in use.

OK, poking to see what happens:
```
sudo service lightdm start
```Observations (??):

Reboot -> boot parameters -> "text nomodeset" ->text login:
```
sudo lshw -C display
``` What driver (if any, none I expect) is present ?
```
sudo service lightdm start
``` check again for driver loaded.

Deductions: If the system (less GUI applications) is functional in these respects and "breaks" loading a graphics driver....
looking at a incompatible driver ? OR and it happens ... the card has failed ?
well ; go through the hassle to remove purge the ATI graphics drivers , revert back to the open source driver, see what haps then.
Go to the ATI web site and see what driver they recommend for your card/linux. [INDENT=2]
a fresh perspective, better outlook [/INDENT]

---

### Post by vaguely_clear on 2013-06-08
Hi, thanks for the reply! It's helped me progress a bit. Here's what happened.

In GRUB, I changed the boot parameters from ```
quiet splash nomodeset
``` to ```
text nomodeset
``` and then logged in as my regular user.

> **Bashing-om said:**
> 
```
sudo lshw -C display
``` make note of the driver(if any) that is presently in use.


The output of that command was:
```
  *-display       description: VGA compatible controller
       product: Barts PRO [Radeon HD 6850]
       vendor: Advanced Micro Devices [AMD] nee ATI
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 00
       width: 64 bits
       clock: 33MHz
       capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=fglrx_pci latency=0
       resources: irq:16 memory:e0000000-efffffff memory:fbcc0000-fbcdffff ioport:de00(size=256) memory:fbc00000-fbc1ffff
  *-display UNCLAIMED
       description: Display controller
       product: Xeon E3-1200 v2/3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm cap_list
       configuration: latency=0
       resources: memory:fb400000-fb7fffff memory:d0000000-dfffffff ioport:ff00(size=64)

```

Everything looks in order here to me, but maybe not?

> **Bashing-om said:**
> OK, poking to see what happens:
```
sudo service lightdm start
```Observations (??):

This command returned
```
lightdm: unrecognized service
```
which is about what I expected, as Ubuntu Gnome uses GDM instead of LightDM (I think).

So, at this point, I decided to deviate from your suggestions and try something else. I issued the command ```
sudo gdm
``` and GDM started right up. I logged in from GDM, but then the gui was unresponsive, though the cursor moved around just fine.

I then Ctrl + Alt + F2'd into a text login, logged in as my normal user, and issued the command ```
startx
``` which brought me to a usable gui. In fact, I'm typing this response from this point. So, I don't think it's FGLRX, actually. It must be something else?

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]vaguely_clear;

Regret I did not recall the DE you are using vice lightdm... no real biggy in this case//

And yeah, pretty well says the driver and card are not the issue, the operating system is good to go ///bout all that is left is the desk top and gdm.
How bout this:
[/COLOR]```
sudo dpkg-reconfigure gdm
```

And by the way, I would have expected "X" to complain in starting the desk top with the term "startx" now-a-days;
```
sudo service gdm start
``` is the more appropriate now. Kinda makes me wonder what is going on that X did not complain...X must have gotten started somewhere, and may be the cause of the problem ...we got a conflict here (???) Xorg service is started but the desk top is not loading for some reason.... huummm...what does the log file /var/log/Xorg.0.log have to say about all this ?[INDENT=2]
shed'n light on a subject

[/INDENT]

---

### Post by vaguely_clear on 2013-06-08
> **Bashing-om said:**
> [COLOR=#000000]vaguely_clear;
[/COLOR]Kinda makes me wonder what is going on that X did not complain...


Well, actually, I stepped away from the computer for a bit, and when I returned, waking the display did not go so well. The gui was garbled, and when I Ctrl + Alt + F2'd, I found some errors (see attached image - sorry, don't feel like typing that out). Perhaps this is a result of my outdated command.

I'll try your suggestions in a bit and respond again. Thanks for all your help!

---

### Post by vaguely_clear on 2013-06-08
> **Bashing-om said:**
> 
```
sudo dpkg-reconfigure gdm
```


This command completed without any apparent fuss. However,

> **Bashing-om said:**
> [COLOR=#000000]
[/COLOR]```
sudo service gdm start
```


This command failed I guess, as GDM did not start up.

> **Bashing-om said:**
> [COLOR=#000000]
[/COLOR]huummm...what does the log file /var/log/Xorg.0.log have to say about all this ?


Here are the contents of /var/log/Xorg.0.log - looks like there's a seg fault at the end:
```
[   426.953] X.Org X Server 1.13.3
Release Date: 2013-03-07
[   426.953] X Protocol Version 11, Revision 0
[   426.953] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[   426.953] Current Operating System: Linux ian-RaringDesktop 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64
[   426.953] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-23-generic root=UUID=1e12a58a-4edc-4ce9-a8d8-b216bf4bd911 ro nomodeset text nomodeset
[   426.953] Build Date: 17 April 2013  10:43:13PM
[   426.953] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[   426.953] Current version of pixman: 0.28.2
[   426.953]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   426.953] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   426.954] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun  8 16:21:18 2013
[   426.954] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   426.954] (==) No Layout section.  Using the first Screen section.
[   426.954] (==) No screen section available. Using defaults.
[   426.954] (**) |-->Screen "Default Screen Section" (0)
[   426.954] (**) |   |-->Monitor "<default monitor>"
[   426.954] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   426.954] (==) Automatically adding devices
[   426.954] (==) Automatically enabling devices
[   426.954] (==) Automatically adding GPU devices
[   426.954] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   426.954]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   426.955] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   426.955] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   426.955] (II) Loader magic: 0x7f133c109d20
[   426.955] (II) Module ABI versions:
[   426.955]     X.Org ANSI C Emulation: 0.4
[   426.955]     X.Org Video Driver: 13.1
[   426.955]     X.Org XInput driver : 18.0
[   426.955]     X.Org Server Extension : 7.0
[   426.956] (--) PCI: (0:0:2:0) 8086:0162:1458:d000 rev 9, Mem @ 0xfb400000/4194304, 0xd0000000/268435456, I/O @ 0x0000ff00/64
[   426.957] (--) PCI:*(0:1:0:0) 1002:6739:174b:174b rev 0, Mem @ 0xe0000000/268435456, 0xfbcc0000/131072, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[   426.957] (II) Open ACPI successful (/var/run/acpid.socket)
[   426.957] Initializing built-in extension Generic Event Extension
[   426.957] Initializing built-in extension SHAPE
[   426.957] Initializing built-in extension MIT-SHM
[   426.957] Initializing built-in extension XInputExtension
[   426.957] Initializing built-in extension XTEST
[   426.957] Initializing built-in extension BIG-REQUESTS
[   426.957] Initializing built-in extension SYNC
[   426.957] Initializing built-in extension XKEYBOARD
[   426.957] Initializing built-in extension XC-MISC
[   426.957] Initializing built-in extension SECURITY
[   426.957] Initializing built-in extension XINERAMA
[   426.957] Initializing built-in extension XFIXES
[   426.957] Initializing built-in extension RENDER
[   426.957] Initializing built-in extension RANDR
[   426.957] Initializing built-in extension COMPOSITE
[   426.957] Initializing built-in extension DAMAGE
[   426.957] Initializing built-in extension MIT-SCREEN-SAVER
[   426.957] Initializing built-in extension DOUBLE-BUFFER
[   426.957] Initializing built-in extension RECORD
[   426.957] Initializing built-in extension DPMS
[   426.957] Initializing built-in extension X-Resource
[   426.957] Initializing built-in extension XVideo
[   426.957] Initializing built-in extension XVideo-MotionCompensation
[   426.957] Initializing built-in extension SELinux
[   426.957] Initializing built-in extension XFree86-VidModeExtension
[   426.957] Initializing built-in extension XFree86-DGA
[   426.957] Initializing built-in extension XFree86-DRI
[   426.957] Initializing built-in extension DRI2
[   426.957] (II) LoadModule: "glx"
[   426.957] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[   426.958] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[   426.958]     compiled for 6.9.0, module version = 1.0.0
[   426.958] Loading extension GLX
[   426.958] (==) Matched fglrx as autoconfigured driver 0
[   426.958] (==) Matched ati as autoconfigured driver 1
[   426.958] (==) Matched vesa as autoconfigured driver 2
[   426.958] (==) Matched modesetting as autoconfigured driver 3
[   426.958] (==) Matched fbdev as autoconfigured driver 4
[   426.958] (==) Assigned the driver to the xf86ConfigLayout
[   426.958] (II) LoadModule: "fglrx"
[   426.958] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   426.970] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[   426.970]     compiled for 1.4.99.906, module version = 9.1.11
[   426.970]     Module class: X.Org Video Driver
[   426.970] (II) Loading sub module "fglrxdrm"
[   426.970] (II) LoadModule: "fglrxdrm"
[   426.970] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   426.971] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[   426.971]     compiled for 1.4.99.906, module version = 9.1.11
[   426.971] (II) LoadModule: "ati"
[   426.972] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   426.972] (II) Module ati: vendor="X.Org Foundation"
[   426.972]     compiled for 1.13.3, module version = 7.1.0
[   426.972]     Module class: X.Org Video Driver
[   426.972]     ABI class: X.Org Video Driver, version 13.1
[   426.972] (II) LoadModule: "radeon"
[   426.972] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   426.972] (II) Module radeon: vendor="X.Org Foundation"
[   426.972]     compiled for 1.13.3, module version = 7.1.0
[   426.972]     Module class: X.Org Video Driver
[   426.972]     ABI class: X.Org Video Driver, version 13.1
[   426.972] (II) LoadModule: "vesa"
[   426.973] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   426.973] (II) Module vesa: vendor="X.Org Foundation"
[   426.973]     compiled for 1.12.99.902, module version = 2.3.2
[   426.973]     Module class: X.Org Video Driver
[   426.973]     ABI class: X.Org Video Driver, version 13.0
[   426.973] (II) LoadModule: "modesetting"
[   426.973] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   426.973] (II) Module modesetting: vendor="X.Org Foundation"
[   426.973]     compiled for 1.13.3, module version = 0.7.0
[   426.973]     Module class: X.Org Video Driver
[   426.973]     ABI class: X.Org Video Driver, version 13.1
[   426.973] (II) LoadModule: "fbdev"
[   426.973] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   426.973] (II) Module fbdev: vendor="X.Org Foundation"
[   426.973]     compiled for 1.12.99.902, module version = 0.4.3
[   426.973]     Module class: X.Org Video Driver
[   426.973]     ABI class: X.Org Video Driver, version 13.0
[   426.973] (II) AMD Proprietary Linux Driver Version Identifier:9.01.11
[   426.973] (II) AMD Proprietary Linux Driver Release Identifier: 9.012                                
[   426.973] (II) AMD Proprietary Linux Driver Build Date: Dec 19 2012 14:41:10
[   426.973] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[   426.976] (II) VESA: driver for VESA chipsets: vesa
[   426.976] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   426.976] (II) FBDEV: driver for framebuffer: fbdev
[   426.976] (++) using VT number 7


[   426.980] (WW) Falling back to old probe method for fglrx
[   426.983] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[   426.992] ukiDynamicMajor: found major device number 249
[   426.992] (--) Assigning device section with no busID to primary device
[   426.992] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[   426.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[   426.993] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[   426.993] (II) AMD Video driver is signed
[   426.993] (II) fglrx(0): pEnt->device->identifier=0x7f133beb16a7
[   426.993] (WW) Falling back to old probe method for vesa
[   426.993] (WW) Falling back to old probe method for modesetting
[   426.993] (EE) open /dev/dri/card0: No such file or directory
[   426.993] (WW) Falling back to old probe method for fbdev
[   426.993] (II) Loading sub module "fbdevhw"
[   426.993] (II) LoadModule: "fbdevhw"
[   426.993] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   426.993] (II) Module fbdevhw: vendor="X.Org Foundation"
[   426.993]     compiled for 1.13.3, module version = 0.0.2
[   426.993]     ABI class: X.Org Video Driver, version 13.1
[   426.993] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[   426.993] (II) Loading sub module "vgahw"
[   426.993] (II) LoadModule: "vgahw"
[   426.994] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   426.994] (II) Module vgahw: vendor="X.Org Foundation"
[   426.994]     compiled for 1.13.3, module version = 0.1.0
[   426.994]     ABI class: X.Org Video Driver, version 13.1
[   426.994] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   426.994] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[   426.994] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   426.994] (==) fglrx(0): Default visual is TrueColor
[   426.994] (==) fglrx(0): RGB weight 888
[   426.994] (II) fglrx(0): Using 8 bits per RGB 
[   426.994] (==) fglrx(0): Buffer Tiling is ON
[   426.994] (II) Loading sub module "fglrxdrm"
[   426.994] (II) LoadModule: "fglrxdrm"
[   426.994] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   426.994] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[   426.994]     compiled for 1.4.99.906, module version = 9.1.11
[   427.001] ukiDynamicMajor: found major device number 249
[   427.001] ukiDynamicMajor: found major device number 249
[   427.001] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   427.001] ukiOpenDevice: node name is /dev/ati/card0
[   427.001] ukiOpenDevice: open result is 13, (OK)
[   427.292] ukiOpenByBusid: ukiOpenMinor returns 13
[   427.292] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   427.293] (**) fglrx(0): NoAccel = NO
[   427.293] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[   427.293] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series  " (Chipset = 0x6739)
[   427.293] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x174b)
[   427.293] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[   427.293] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[   427.293] (--) fglrx(0): MMIO registers at 0xfbcc0000
[   427.293] (--) fglrx(0): I/O port at 0x0000de00
[   427.293] (==) fglrx(0): ROM-BIOS at 0x000c0000
[   427.293] (II) fglrx(0): AC Adapter is used
[   427.293] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[   427.293] (II) Loading sub module "vbe"
[   427.293] (II) LoadModule: "vbe"
[   427.293] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   427.294] (II) Module vbe: vendor="X.Org Foundation"
[   427.294]     compiled for 1.13.3, module version = 1.1.0
[   427.294]     ABI class: X.Org Video Driver, version 13.1
[   427.294] (II) fglrx(0): VESA BIOS detected
[   427.294] (II) fglrx(0): VESA VBE Version 3.0
[   427.294] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[   427.294] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[   427.294] (II) fglrx(0): VESA VBE OEM Software Rev: 13.12
[   427.294] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[   427.294] (II) fglrx(0): VESA VBE OEM Product: BARTS
[   427.294] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[   427.294] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[   427.294] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[   427.294] (II) fglrx(0): PCIE card detected
[   427.294] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[   427.294] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   427.294] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[   427.294] (II) fglrx(0): RandR 1.2 support is enabled!
[   427.294] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[   427.294] (==) fglrx(0): Center Mode is disabled 
[   427.294] (II) Loading sub module "fb"
[   427.294] (II) LoadModule: "fb"
[   427.294] (II) Loading /usr/lib/xorg/modules/libfb.so
[   427.294] (II) Module fb: vendor="X.Org Foundation"
[   427.294]     compiled for 1.13.3, module version = 1.0.0
[   427.294]     ABI class: X.Org ANSI C Emulation, version 0.4
[   427.294] (II) Loading sub module "ddc"
[   427.294] (II) LoadModule: "ddc"
[   427.294] (II) Module "ddc" already built-in
[   427.367] (II) fglrx(0): Output DFP1 has no monitor section
[   427.367] (II) fglrx(0): Output DFP2 has no monitor section
[   427.367] (II) fglrx(0): Output DFP3 has no monitor section
[   427.367] (II) fglrx(0): Output DFP4 has no monitor section
[   427.367] (II) fglrx(0): Output DFP5 has no monitor section
[   427.367] (II) fglrx(0): Output DFP6 has no monitor section
[   427.367] (II) fglrx(0): Output DFP7 has no monitor section
[   427.367] (II) fglrx(0): Output CRT1 has no monitor section
[   427.367] (II) Loading sub module "ddc"
[   427.367] (II) LoadModule: "ddc"
[   427.367] (II) Module "ddc" already built-in
[   427.367] (II) fglrx(0): Connected Display0: DFP6
[   427.367] (II) fglrx(0):  Display0: Failed to get EDID information. 
[   427.368] (II) fglrx(0): EDID for output DFP1
[   427.368] (II) fglrx(0): EDID for output DFP2
[   427.368] (II) fglrx(0): EDID for output DFP3
[   427.368] (II) fglrx(0): EDID for output DFP4
[   427.368] (II) fglrx(0): EDID for output DFP5
[   427.368] (II) fglrx(0): EDID for output DFP6
[   427.368] (II) fglrx(0): Manufacturer: DEL  Model: f011  Serial#: 826552652
[   427.368] (II) fglrx(0): Year: 2009  Week: 39
[   427.368] (II) fglrx(0): EDID Version: 1.3
[   427.368] (II) fglrx(0): Digital Display Input
[   427.368] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[   427.368] (II) fglrx(0): Gamma: 2.20
[   427.368] (II) fglrx(0): DPMS capabilities: Off
[   427.368] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   427.368] (II) fglrx(0): Default color space is primary color space
[   427.368] (II) fglrx(0): First detailed timing is preferred mode
[   427.368] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[   427.368] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[   427.368] (II) fglrx(0): Supported established timings:
[   427.368] (II) fglrx(0): 720x400@70Hz
[   427.368] (II) fglrx(0): 640x480@60Hz
[   427.368] (II) fglrx(0): 640x480@75Hz
[   427.368] (II) fglrx(0): 800x600@60Hz
[   427.368] (II) fglrx(0): 800x600@75Hz
[   427.368] (II) fglrx(0): 1024x768@60Hz
[   427.368] (II) fglrx(0): 1024x768@75Hz
[   427.368] (II) fglrx(0): 1280x1024@75Hz
[   427.368] (II) fglrx(0): Manufacturer's mask: 0
[   427.368] (II) fglrx(0): Supported standard timings:
[   427.368] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   427.368] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   427.368] (II) fglrx(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   427.368] (II) fglrx(0): Supported detailed timing:
[   427.368] (II) fglrx(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[   427.368] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[   427.368] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[   427.368] (II) fglrx(0): Serial No: H736H99L1D1L
[   427.368] (II) fglrx(0): Monitor name: DELL 2209WA
[   427.368] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 165 MHz
[   427.368] (II) fglrx(0): EDID (in hex):
[   427.368] (II) fglrx(0):     00ffffffffffff0010ac11f04c314431
[   427.368] (II) fglrx(0):     27130103802f1e782eee95a3544c9926
[   427.368] (II) fglrx(0):     0f5054a54b00714f8180b30001010101
[   427.368] (II) fglrx(0):     01010101010121399030621a274068b0
[   427.368] (II) fglrx(0):     3600da281100001c000000ff00483733
[   427.368] (II) fglrx(0):     364839394c3144314c0a000000fc0044
[   427.368] (II) fglrx(0):     454c4c203232303957410a20000000fd
[   427.368] (II) fglrx(0):     00384b1e5310000a2020202020200006
[   427.368] (II) fglrx(0): Printing probed modes for output DFP6
[   427.368] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   427.368] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1440x900"x60.0  146.25  1440 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x800"x75.0  135.00  1280 1296 1440 1688  800 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x800"x60.0  108.00  1280 1328 1440 1688  800 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1152x864"x60.0  146.25  1152 1784 1960 2240  864 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x720"x75.0  135.00  1280 1296 1440 1688  720 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1328 1440 1688  720 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   427.368] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   427.368] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   427.368] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   427.368] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   427.368] (II) fglrx(0): EDID for output DFP7
[   427.368] (II) fglrx(0): EDID for output CRT1
[   427.368] (II) fglrx(0): Output DFP1 disconnected
[   427.368] (II) fglrx(0): Output DFP2 disconnected
[   427.368] (II) fglrx(0): Output DFP3 disconnected
[   427.368] (II) fglrx(0): Output DFP4 disconnected
[   427.368] (II) fglrx(0): Output DFP5 disconnected
[   427.368] (II) fglrx(0): Output DFP6 connected
[   427.368] (II) fglrx(0): Output DFP7 disconnected
[   427.368] (II) fglrx(0): Output CRT1 disconnected
[   427.368] (II) fglrx(0): Using exact sizes for initial modes
[   427.368] (II) fglrx(0): Output DFP6 using initial mode 1680x1050
[   427.368] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   427.368] (II) fglrx(0): DPI set to (96, 96)
[   427.368] (II) fglrx(0): Eyefinity capable adapter detected.
[   427.368] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series   has 6 configurable heads and 1 displays connected.
[   427.368] (==) fglrx(0):  PseudoColor visuals disabled
[   427.368] (II) Loading sub module "ramdac"
[   427.368] (II) LoadModule: "ramdac"
[   427.368] (II) Module "ramdac" already built-in
[   427.368] (==) fglrx(0): NoDRI = NO
[   427.368] (==) fglrx(0): Capabilities: 0x00000000
[   427.368] (==) fglrx(0): CapabilitiesEx: 0x00000000
[   427.368] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[   427.368] (==) fglrx(0): UseFastTLS=0
[   427.368] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[   427.368] (II) UnloadModule: "radeon"
[   427.368] (II) Unloading radeon
[   427.368] (II) UnloadModule: "vesa"
[   427.368] (II) Unloading vesa
[   427.368] (II) UnloadModule: "modesetting"
[   427.368] (II) Unloading modesetting
[   427.368] (II) UnloadModule: "fbdev"
[   427.368] (II) Unloading fbdev
[   427.368] (II) UnloadSubModule: "fbdevhw"
[   427.368] (II) Unloading fbdevhw
[   427.369] (--) Depth 24 pixmap format is 32 bpp
[   427.370] Loading extension ATIFGLRXDRI
[   427.370] (II) fglrx(0): doing swlDriScreenInit
[   427.370] (II) fglrx(0): swlDriScreenInit for fglrx driver
[   427.370] ukiDynamicMajor: found major device number 249
[   427.370] ukiDynamicMajor: found major device number 249
[   427.370] ukiDynamicMajor: found major device number 249
[   427.370] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   427.370] ukiOpenDevice: node name is /dev/ati/card0
[   427.370] ukiOpenDevice: open result is 14, (OK)
[   427.370] ukiOpenByBusid: ukiOpenMinor returns 14
[   427.370] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   427.370] (II) fglrx(0): [uki] DRM interface version 1.0
[   427.370] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[   427.370] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[   427.370] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f133bcc9000
[   427.370] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[   427.370] (II) fglrx(0): [uki] added 1 reserved context for kernel
[   427.370] (II) fglrx(0): swlDriScreenInit done
[   427.370] (II) fglrx(0): Kernel Module Version Information:
[   427.370] (II) fglrx(0):     Name: fglrx
[   427.370] (II) fglrx(0):     Version: 9.1.11
[   427.370] (II) fglrx(0):     Date: Dec 19 2012
[   427.370] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[   427.371] (II) fglrx(0): Kernel Module version matches driver.
[   427.371] (II) fglrx(0): Kernel Module Build Time Information:
[   427.371] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.8.0-23-generic
[   427.371] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[   427.371] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[   427.371] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[   427.371] (II) fglrx(0): [uki] register handle = 0x00004000
[   427.371] (II) fglrx(0): DRI initialization successfull
[   427.371] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01008000
[   427.371] (==) fglrx(0): Backing store disabled
[   427.371] Loading extension FGLRXEXTENSION
[   427.371] (==) fglrx(0): DPMS enabled
[   427.371] (II) fglrx(0): Initialized in-driver Xinerama extension
[   427.371] (**) fglrx(0): Textured Video is enabled.
[   427.371] (II) LoadModule: "glesx"
[   427.372] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[   427.372] (II) Module glesx: vendor="X.Org Foundation"
[   427.372]     compiled for 1.4.99.906, module version = 1.0.0
[   427.372] Loading extension GLESX
[   427.372] (II) fglrx(0): GLESX enableFlags = 592
[   427.372] (II) fglrx(0): GLESX is enabled
[   427.372] (II) LoadModule: "amdxmm"
[   427.372] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[   427.372] (II) Module amdxmm: vendor="X.Org Foundation"
[   427.372]     compiled for 1.4.99.906, module version = 2.0.0
[   427.387] Loading extension AMDXVOPL
[   427.387] Loading extension AMDXVBA
[   427.387] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[   427.388] (II) fglrx(0): Enable composite support successfully
[   427.388] (II) fglrx(0): X context handle = 0x1
[   427.388] (II) fglrx(0): [DRI] installation complete
[   427.388] (==) fglrx(0): Silken mouse enabled
[   427.388] (==) fglrx(0): Using HW cursor of display infrastructure!
[   427.388] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   427.433] (--) RandR disabled
[   427.436] (II) SELinux: Disabled on system
[   427.436] ukiDynamicMajor: found major device number 249
[   427.436] ukiDynamicMajor: found major device number 249
[   427.436] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   427.436] ukiOpenDevice: node name is /dev/ati/card0
[   427.436] ukiOpenDevice: open result is 15, (OK)
[   427.436] ukiOpenByBusid: ukiOpenMinor returns 15
[   427.436] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   427.477] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[   427.485] (II) fglrx(0): Setting screen physical size to 444 x 277
[   427.489] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   427.490] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   427.490] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   427.490] (II) LoadModule: "evdev"
[   427.490] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   427.491] (II) Module evdev: vendor="X.Org Foundation"
[   427.491]     compiled for 1.13.3, module version = 2.7.3
[   427.491]     Module class: X.Org XInput Driver
[   427.491]     ABI class: X.Org XInput driver, version 18.0
[   427.491] (II) Using input driver 'evdev' for 'Power Button'
[   427.491] (**) Power Button: always reports core events
[   427.491] (**) evdev: Power Button: Device: "/dev/input/event1"
[   427.491] (--) evdev: Power Button: Vendor 0 Product 0x1
[   427.491] (--) evdev: Power Button: Found keys
[   427.491] (II) evdev: Power Button: Configuring as keyboard
[   427.491] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   427.491] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   427.491] (**) Option "xkb_rules" "evdev"
[   427.491] (**) Option "xkb_model" "pc105"
[   427.491] (**) Option "xkb_layout" "us"
[   427.491] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   427.491] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   427.491] (II) Using input driver 'evdev' for 'Power Button'
[   427.491] (**) Power Button: always reports core events
[   427.491] (**) evdev: Power Button: Device: "/dev/input/event0"
[   427.491] (--) evdev: Power Button: Vendor 0 Product 0x1
[   427.491] (--) evdev: Power Button: Found keys
[   427.491] (II) evdev: Power Button: Configuring as keyboard
[   427.491] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   427.491] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   427.491] (**) Option "xkb_rules" "evdev"
[   427.491] (**) Option "xkb_model" "pc105"
[   427.491] (**) Option "xkb_layout" "us"
[   427.492] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event14)
[   427.492] (II) No input driver specified, ignoring this device.
[   427.492] (II) This device may have been added with another device file.
[   427.492] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event5)
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   427.492] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event5"
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[   427.492] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input5/event5"
[   427.492] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 8)
[   427.492] (**) Option "xkb_rules" "evdev"
[   427.492] (**) Option "xkb_model" "pc105"
[   427.492] (**) Option "xkb_layout" "us"
[   427.492] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event6)
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   427.492] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event6"
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[   427.492] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1/input/input6/event6"
[   427.492] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 9)
[   427.492] (**) Option "xkb_rules" "evdev"
[   427.492] (**) Option "xkb_model" "pc105"
[   427.492] (**) Option "xkb_layout" "us"
[   427.492] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event7)
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev pointer catchall"
[   427.492] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event7"
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found 9 mouse buttons
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found scroll wheel(s)
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found relative axes
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found x and y relative axes
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as mouse
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Adding scrollwheel support
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: YAxisMapping: buttons 4 and 5
[   427.493] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   427.493] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.2/input/input7/event7"
[   427.493] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: MOUSE, id 10)
[   427.493] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: initialized for relative axes.
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) keeping acceleration scheme 1
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) acceleration profile 0
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) acceleration factor: 2.000
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) acceleration threshold: 4
[   427.493] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/mouse1)
[   427.493] (II) No input driver specified, ignoring this device.
[   427.493] (II) This device may have been added with another device file.
[   427.493] (II) config/udev: Adding input device Logitech Logitech USB Headset (/dev/input/event2)
[   427.493] (**) Logitech Logitech USB Headset: Applying InputClass "evdev keyboard catchall"
[   427.493] (II) Using input driver 'evdev' for 'Logitech Logitech USB Headset'
[   427.493] (**) Logitech Logitech USB Headset: always reports core events
[   427.493] (**) evdev: Logitech Logitech USB Headset: Device: "/dev/input/event2"
[   427.493] (--) evdev: Logitech Logitech USB Headset: Vendor 0x46d Product 0xa0c
[   427.493] (--) evdev: Logitech Logitech USB Headset: Found keys
[   427.493] (II) evdev: Logitech Logitech USB Headset: Configuring as keyboard
[   427.493] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.3/input/input2/event2"
[   427.493] (II) XINPUT: Adding extended input device "Logitech Logitech USB Headset" (type: KEYBOARD, id 11)
[   427.493] (**) Option "xkb_rules" "evdev"
[   427.493] (**) Option "xkb_model" "pc105"
[   427.493] (**) Option "xkb_layout" "us"
[   427.493] (II) config/udev: Adding input device Logitech G500 (/dev/input/event3)
[   427.493] (**) Logitech G500: Applying InputClass "evdev pointer catchall"
[   427.493] (II) Using input driver 'evdev' for 'Logitech G500'
[   427.493] (**) Logitech G500: always reports core events
[   427.493] (**) evdev: Logitech G500: Device: "/dev/input/event3"
[   427.493] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[   427.493] (--) evdev: Logitech G500: Found 20 mouse buttons
[   427.493] (--) evdev: Logitech G500: Found scroll wheel(s)
[   427.493] (--) evdev: Logitech G500: Found relative axes
[   427.493] (--) evdev: Logitech G500: Found x and y relative axes
[   427.493] (II) evdev: Logitech G500: Configuring as mouse
[   427.493] (II) evdev: Logitech G500: Adding scrollwheel support
[   427.493] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[   427.493] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   427.493] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/event3"
[   427.493] (II) XINPUT: Adding extended input device "Logitech G500" (type: MOUSE, id 12)
[   427.493] (II) evdev: Logitech G500: initialized for relative axes.
[   427.493] (**) Logitech G500: (accel) keeping acceleration scheme 1
[   427.493] (**) Logitech G500: (accel) acceleration profile 0
[   427.493] (**) Logitech G500: (accel) acceleration factor: 2.000
[   427.493] (**) Logitech G500: (accel) acceleration threshold: 4
[   427.494] (II) config/udev: Adding input device Logitech G500 (/dev/input/mouse0)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device Logitech G500 (/dev/input/event4)
[   427.494] (**) Logitech G500: Applying InputClass "evdev keyboard catchall"
[   427.494] (II) Using input driver 'evdev' for 'Logitech G500'
[   427.494] (**) Logitech G500: always reports core events
[   427.494] (**) evdev: Logitech G500: Device: "/dev/input/event4"
[   427.494] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[   427.494] (--) evdev: Logitech G500: Found 1 mouse buttons
[   427.494] (--) evdev: Logitech G500: Found scroll wheel(s)
[   427.494] (--) evdev: Logitech G500: Found relative axes
[   427.494] (II) evdev: Logitech G500: Forcing relative x/y axes to exist.
[   427.494] (--) evdev: Logitech G500: Found absolute axes
[   427.494] (II) evdev: Logitech G500: Forcing absolute x/y axes to exist.
[   427.494] (--) evdev: Logitech G500: Found keys
[   427.494] (II) evdev: Logitech G500: Configuring as mouse
[   427.494] (II) evdev: Logitech G500: Configuring as keyboard
[   427.494] (II) evdev: Logitech G500: Adding scrollwheel support
[   427.494] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[   427.494] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   427.494] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input4/event4"
[   427.494] (II) XINPUT: Adding extended input device "Logitech G500" (type: KEYBOARD, id 13)
[   427.494] (**) Option "xkb_rules" "evdev"
[   427.494] (**) Option "xkb_model" "pc105"
[   427.494] (**) Option "xkb_layout" "us"
[   427.494] (II) evdev: Logitech G500: initialized for relative axes.
[   427.494] (WW) evdev: Logitech G500: ignoring absolute axes.
[   427.494] (**) Logitech G500: (accel) keeping acceleration scheme 1
[   427.494] (**) Logitech G500: (accel) acceleration profile 0
[   427.494] (**) Logitech G500: (accel) acceleration factor: 2.000
[   427.494] (**) Logitech G500: (accel) acceleration threshold: 4
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event11)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event13)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.495] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[   427.495] (II) No input driver specified, ignoring this device.
[   427.495] (II) This device may have been added with another device file.
[   427.495] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event9)
[   427.495] (II) No input driver specified, ignoring this device.
[   427.495] (II) This device may have been added with another device file.
[   427.497] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[   427.499] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   427.499] (II) fglrx(0): Using EDID range info for horizontal sync
[   427.499] (II) fglrx(0): Using EDID range info for vertical refresh
[   427.499] (II) fglrx(0): Printing DDC gathered Modelines:
[   427.499] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   427.499] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   427.499] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.499] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   427.499] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   427.499] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   427.499] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.499] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   427.841] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   427.841] (II) fglrx(0): Using hsync ranges from config file
[   427.841] (II) fglrx(0): Using vrefresh ranges from config file
[   427.841] (II) fglrx(0): Printing DDC gathered Modelines:
[   427.841] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   427.841] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   427.841] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.841] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   427.841] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   427.841] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   427.841] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.841] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   428.055] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   428.055] (II) fglrx(0): Using hsync ranges from config file
[   428.055] (II) fglrx(0): Using vrefresh ranges from config file
[   428.055] (II) fglrx(0): Printing DDC gathered Modelines:
[   428.055] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   428.055] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   428.055] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   428.055] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   428.055] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   428.055] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   428.055] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   428.055] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   428.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   430.993] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   434.630] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   434.630] (II) fglrx(0): Using hsync ranges from config file
[   434.630] (II) fglrx(0): Using vrefresh ranges from config file
[   434.630] (II) fglrx(0): Printing DDC gathered Modelines:
[   434.630] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   434.630] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   434.630] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   434.630] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   434.630] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   434.630] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   434.630] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   434.630] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   434.798] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   434.798] (II) fglrx(0): Using hsync ranges from config file
[   434.798] (II) fglrx(0): Using vrefresh ranges from config file
[   434.798] (II) fglrx(0): Printing DDC gathered Modelines:
[   434.798] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   434.798] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   434.798] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   434.798] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   434.798] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   434.798] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   434.798] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   434.798] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   434.820] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   434.820] (II) fglrx(0): Using hsync ranges from config file
[   434.820] (II) fglrx(0): Using vrefresh ranges from config file
[   434.820] (II) fglrx(0): Printing DDC gathered Modelines:
[   434.820] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   434.820] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   434.820] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   434.820] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   434.820] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   434.820] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   434.820] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   434.820] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   435.005] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   489.364] (II) AIGLX: Suspending AIGLX clients for VT switch
[   489.364] (II) fglrx(0): Backup framebuffer data.
[   489.389] (II) fglrx(0): Backup complete.
[  3453.568] (II) AIGLX: Resuming AIGLX clients after VT switch
[  3453.697] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[  3453.697] (II) fglrx(0): Using hsync ranges from config file
[  3453.697] (II) fglrx(0): Using vrefresh ranges from config file
[  3453.697] (II) fglrx(0): Printing DDC gathered Modelines:
[  3453.697] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  3453.697] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3453.697] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3453.697] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  3453.718] (II) fglrx(0): Hot-plug event occurs on device: 1:0:0 
[  3453.730] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[  3453.730] (II) fglrx(0): Using hsync ranges from config file
[  3453.730] (II) fglrx(0): Using vrefresh ranges from config file
[  3453.730] (II) fglrx(0): Printing DDC gathered Modelines:
[  3453.730] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  3453.730] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3453.730] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3453.730] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3453.730] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3453.730] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3453.731] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3453.731] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  3453.739] (II) fglrx(0): xdl_xs113_atiddxDisplayScreenEnableDisplays
[  3491.300] (II) AIGLX: Suspending AIGLX clients for VT switch
[  3491.300] (II) fglrx(0): Backup framebuffer data.
[  3491.376] (II) fglrx(0): Backup complete.
[  3556.482] (II) evdev: Logitech G500: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Logitech G500: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Logitech Logitech USB Headset: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Power Button: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Power Button: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.483] (II) fglrx(0): Shutdown CMMQS
[  3556.499] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[  3556.499] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0x7f133bcc9000
[  3556.504] (EE) 
[  3556.504] (EE) Backtrace:
[  3556.504] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f133be93476]
[  3556.504] (EE) 1: /usr/bin/X (0x7f133bce3000+0x1b42b9) [0x7f133be972b9]
[  3556.504] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f133ade6000+0xfbd0) [0x7f133adf5bd0]
[  3556.504] (EE) 3: /usr/lib/x86_64-linux-gnu/libpciaccess.so.0 (0x7f133b003000+0x4c3e) [0x7f133b007c3e]
[  3556.504] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (amd_xs113_int10_x_inb+0x46) [0x7f13382c3e66]
[  3556.504] (EE) 5: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7f1337ae3000+0x7d70c5) [0x7f13382ba0c5]
[  3556.505] (EE) 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (X86EMU_exec+0xa5) [0x7f13382ad815]
[  3556.505] (EE) 7: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (amd_xs113_int10_xf86ExecX86int10+0x46) [0x7f13382c4fc6]
[  3556.505] (EE) 8: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xf86ExecX86int10+0xd) [0x7f1337e1a49d]
[  3556.505] (EE) 9: /usr/lib/xorg/modules/libvbe.so (VBESetVBEMode+0x9d) [0x7f133663f4ed]
[  3556.505] (EE) 10: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7f1337ae3000+0x3691b3) [0x7f1337e4c1b3]
[  3556.505] (EE) 11: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (atiddxVBESetConsoleMode+0x42) [0x7f1337e4bff2]
[  3556.505] (EE) 12: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxFreeScreen+0x46a) [0x7f1337f9c4aa]
[  3556.505] (EE) 13: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxCloseScreen+0x260) [0x7f1337f9bd80]
[  3556.505] (EE) 14: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7f1337ae3000+0x84c9c6) [0x7f133832f9c6]
[  3556.505] (EE) 15: /usr/bin/X (0x7f133bce3000+0xea338) [0x7f133bdcd338]
[  3556.505] (EE) 16: /usr/bin/X (0x7f133bce3000+0x135fb4) [0x7f133be18fb4]
[  3556.505] (EE) 17: /usr/bin/X (0x7f133bce3000+0x47687) [0x7f133bd2a687]
[  3556.505] (EE) 18: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f1339a33ea5]
[  3556.505] (EE) 19: /usr/bin/X (0x7f133bce3000+0x478c1) [0x7f133bd2a8c1]
[  3556.505] (EE) 
[  3556.505] (EE) Segmentation fault at address 0x0
[  3556.505] 
Fatal server error:
[  3556.505] Caught signal 11 (Segmentation fault). Server aborting
[  3556.505] 
[  3556.505] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  3556.505] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3556.505] (EE) 
[  3556.508] Server terminated with error (1). Closing log file.

```

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]vaguely_clear; ..

Looks like xorg is not to happy with fglrx.....
try this:
[/COLOR]```
sudo apt-get install linux-headers-generic fglrx-updates
```
reboot for effect;
and run terminal command:
```
sudo aticonfig --initial
```

and advise on status - difference in the Xorg.0.log file.[INDENT=2]
regards

[/INDENT]
[INDENT=2]

[/INDENT]

---

### Post by vaguely_clear on 2013-06-09
> **Bashing-om said:**
> [COLOR=#000000]vaguely_clear; ..
Looks like xorg is not to happy with fglrx.....
try this:
[/COLOR]```
sudo apt-get install linux-headers-generic fglrx-updates
```
reboot for effect;
and run terminal command:
```
sudo aticonfig --initial
```


Aha, linux-headers-generic has come up recently. For whatever reason, I kept getting a message on my apt commands that it was no longer needed and that I should run sudo apt-get autoremove to remove it. Finally, I reluctantly ran autoremove, though linux-headers-generic sounds, you know, kind of important.

I'm doing something on this machine on another installation right now, but I'll try this as soon as possible.

---

### Post by vaguely_clear on 2013-06-09
> **Bashing-om said:**
> 
[COLOR=#000000]try this:
[/COLOR]```
sudo apt-get install linux-headers-generic fglrx-updates
```


Nothing happened - it said the two were already the latest versions. Perhaps I was mistaken about the autoremove thing...

> **Bashing-om said:**
> 
and run terminal command:
```
sudo aticonfig --initial
```


This command returned:
```

Uninitialised file found, configuring.
Using /etc/X11/xorg.conf
Saving back-up to /etc/X11/xorg.conf.original-0

```

> **Bashing-om said:**
> 
and advise on status - difference in the Xorg.0.log file.


Here it is (doesn't look like anything has changed?):
```

[   426.953] 
X.Org X Server 1.13.3
Release Date: 2013-03-07
[   426.953] X Protocol Version 11, Revision 0
[   426.953] Build Operating System: Linux 3.2.0-37-generic x86_64 Ubuntu
[   426.953] Current Operating System: Linux ian-RaringDesktop 3.8.0-23-generic #34-Ubuntu SMP Wed May 29 20:22:58 UTC 2013 x86_64
[   426.953] Kernel command line: BOOT_IMAGE=/boot/vmlinuz-3.8.0-23-generic root=UUID=1e12a58a-4edc-4ce9-a8d8-b216bf4bd911 ro nomodeset text nomodeset
[   426.953] Build Date: 17 April 2013  10:43:13PM
[   426.953] xorg-server 2:1.13.3-0ubuntu6 (For technical support please see http://www.ubuntu.com/support) 
[   426.953] Current version of pixman: 0.28.2
[   426.953]     Before reporting problems, check http://wiki.x.org
    to make sure that you have the latest version.
[   426.953] Markers: (--) probed, (**) from config file, (==) default setting,
    (++) from command line, (!!) notice, (II) informational,
    (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
[   426.954] (==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun  8 16:21:18 2013
[   426.954] (==) Using system config directory "/usr/share/X11/xorg.conf.d"
[   426.954] (==) No Layout section.  Using the first Screen section.
[   426.954] (==) No screen section available. Using defaults.
[   426.954] (**) |-->Screen "Default Screen Section" (0)
[   426.954] (**) |   |-->Monitor "<default monitor>"
[   426.954] (==) No monitor specified for screen "Default Screen Section".
    Using a default monitor configuration.
[   426.954] (==) Automatically adding devices
[   426.954] (==) Automatically enabling devices
[   426.954] (==) Automatically adding GPU devices
[   426.954] (WW) The directory "/usr/share/fonts/X11/cyrillic" does not exist.
[   426.954]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/100dpi/" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/75dpi/" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/100dpi" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/usr/share/fonts/X11/75dpi" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (WW) The directory "/var/lib/defoma/x-ttcidfont-conf.d/dirs/TrueType" does not exist.
[   426.955]     Entry deleted from font path.
[   426.955] (==) FontPath set to:
    /usr/share/fonts/X11/misc,
    /usr/share/fonts/X11/Type1,
    built-ins
[   426.955] (==) ModulePath set to "/usr/lib/x86_64-linux-gnu/xorg/extra-modules,/usr/lib/xorg/extra-modules,/usr/lib/xorg/modules"
[   426.955] (II) The server relies on udev to provide the list of input devices.
    If no devices become available, reconfigure udev or disable AutoAddDevices.
[   426.955] (II) Loader magic: 0x7f133c109d20
[   426.955] (II) Module ABI versions:
[   426.955]     X.Org ANSI C Emulation: 0.4
[   426.955]     X.Org Video Driver: 13.1
[   426.955]     X.Org XInput driver : 18.0
[   426.955]     X.Org Server Extension : 7.0
[   426.956] (--) PCI: (0:0:2:0) 8086:0162:1458:d000 rev 9, Mem @ 0xfb400000/4194304, 0xd0000000/268435456, I/O @ 0x0000ff00/64
[   426.957] (--) PCI:*(0:1:0:0) 1002:6739:174b:174b rev 0, Mem @ 0xe0000000/268435456, 0xfbcc0000/131072, I/O @ 0x0000de00/256, BIOS @ 0x????????/131072
[   426.957] (II) Open ACPI successful (/var/run/acpid.socket)
[   426.957] Initializing built-in extension Generic Event Extension
[   426.957] Initializing built-in extension SHAPE
[   426.957] Initializing built-in extension MIT-SHM
[   426.957] Initializing built-in extension XInputExtension
[   426.957] Initializing built-in extension XTEST
[   426.957] Initializing built-in extension BIG-REQUESTS
[   426.957] Initializing built-in extension SYNC
[   426.957] Initializing built-in extension XKEYBOARD
[   426.957] Initializing built-in extension XC-MISC
[   426.957] Initializing built-in extension SECURITY
[   426.957] Initializing built-in extension XINERAMA
[   426.957] Initializing built-in extension XFIXES
[   426.957] Initializing built-in extension RENDER
[   426.957] Initializing built-in extension RANDR
[   426.957] Initializing built-in extension COMPOSITE
[   426.957] Initializing built-in extension DAMAGE
[   426.957] Initializing built-in extension MIT-SCREEN-SAVER
[   426.957] Initializing built-in extension DOUBLE-BUFFER
[   426.957] Initializing built-in extension RECORD
[   426.957] Initializing built-in extension DPMS
[   426.957] Initializing built-in extension X-Resource
[   426.957] Initializing built-in extension XVideo
[   426.957] Initializing built-in extension XVideo-MotionCompensation
[   426.957] Initializing built-in extension SELinux
[   426.957] Initializing built-in extension XFree86-VidModeExtension
[   426.957] Initializing built-in extension XFree86-DGA
[   426.957] Initializing built-in extension XFree86-DRI
[   426.957] Initializing built-in extension DRI2
[   426.957] (II) LoadModule: "glx"
[   426.957] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/extensions/libglx.so
[   426.958] (II) Module glx: vendor="Advanced Micro Devices, Inc."
[   426.958]     compiled for 6.9.0, module version = 1.0.0
[   426.958] Loading extension GLX
[   426.958] (==) Matched fglrx as autoconfigured driver 0
[   426.958] (==) Matched ati as autoconfigured driver 1
[   426.958] (==) Matched vesa as autoconfigured driver 2
[   426.958] (==) Matched modesetting as autoconfigured driver 3
[   426.958] (==) Matched fbdev as autoconfigured driver 4
[   426.958] (==) Assigned the driver to the xf86ConfigLayout
[   426.958] (II) LoadModule: "fglrx"
[   426.958] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so
[   426.970] (II) Module fglrx: vendor="FireGL - AMD Technologies Inc."
[   426.970]     compiled for 1.4.99.906, module version = 9.1.11
[   426.970]     Module class: X.Org Video Driver
[   426.970] (II) Loading sub module "fglrxdrm"
[   426.970] (II) LoadModule: "fglrxdrm"
[   426.970] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   426.971] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[   426.971]     compiled for 1.4.99.906, module version = 9.1.11
[   426.971] (II) LoadModule: "ati"
[   426.972] (II) Loading /usr/lib/xorg/modules/drivers/ati_drv.so
[   426.972] (II) Module ati: vendor="X.Org Foundation"
[   426.972]     compiled for 1.13.3, module version = 7.1.0
[   426.972]     Module class: X.Org Video Driver
[   426.972]     ABI class: X.Org Video Driver, version 13.1
[   426.972] (II) LoadModule: "radeon"
[   426.972] (II) Loading /usr/lib/xorg/modules/drivers/radeon_drv.so
[   426.972] (II) Module radeon: vendor="X.Org Foundation"
[   426.972]     compiled for 1.13.3, module version = 7.1.0
[   426.972]     Module class: X.Org Video Driver
[   426.972]     ABI class: X.Org Video Driver, version 13.1
[   426.972] (II) LoadModule: "vesa"
[   426.973] (II) Loading /usr/lib/xorg/modules/drivers/vesa_drv.so
[   426.973] (II) Module vesa: vendor="X.Org Foundation"
[   426.973]     compiled for 1.12.99.902, module version = 2.3.2
[   426.973]     Module class: X.Org Video Driver
[   426.973]     ABI class: X.Org Video Driver, version 13.0
[   426.973] (II) LoadModule: "modesetting"
[   426.973] (II) Loading /usr/lib/xorg/modules/drivers/modesetting_drv.so
[   426.973] (II) Module modesetting: vendor="X.Org Foundation"
[   426.973]     compiled for 1.13.3, module version = 0.7.0
[   426.973]     Module class: X.Org Video Driver
[   426.973]     ABI class: X.Org Video Driver, version 13.1
[   426.973] (II) LoadModule: "fbdev"
[   426.973] (II) Loading /usr/lib/xorg/modules/drivers/fbdev_drv.so
[   426.973] (II) Module fbdev: vendor="X.Org Foundation"
[   426.973]     compiled for 1.12.99.902, module version = 0.4.3
[   426.973]     Module class: X.Org Video Driver
[   426.973]     ABI class: X.Org Video Driver, version 13.0
[   426.973] (II) AMD Proprietary Linux Driver Version Identifier:9.01.11
[   426.973] (II) AMD Proprietary Linux Driver Release Identifier: 9.012                                
[   426.973] (II) AMD Proprietary Linux Driver Build Date: Dec 19 2012 14:41:10
[   426.973] (II) RADEON: Driver for ATI Radeon chipsets:
    ATI Radeon Mobility X600 (M24) 3150 (PCIE), ATI FireMV 2400 (PCI),
    ATI Radeon Mobility X300 (M24) 3152 (PCIE),
    ATI FireGL M24 GL 3154 (PCIE), ATI FireMV 2400 3155 (PCI),
    ATI Radeon X600 (RV380) 3E50 (PCIE),
    ATI FireGL V3200 (RV380) 3E54 (PCIE), ATI Radeon IGP320 (A3) 4136,
    ATI Radeon IGP330/340/350 (A4) 4137, ATI Radeon 9500 AD (AGP),
    ATI Radeon 9500 AE (AGP), ATI Radeon 9600TX AF (AGP),
    ATI FireGL Z1 AG (AGP), ATI Radeon 9800SE AH (AGP),
    ATI Radeon 9800 AI (AGP), ATI Radeon 9800 AJ (AGP),
    ATI FireGL X2 AK (AGP), ATI Radeon 9600 AP (AGP),
    ATI Radeon 9600SE AQ (AGP), ATI Radeon 9600XT AR (AGP),
    ATI Radeon 9600 AS (AGP), ATI FireGL T2 AT (AGP), ATI Radeon 9650,
    ATI FireGL RV360 AV (AGP), ATI Radeon 7000 IGP (A4+) 4237,
    ATI Radeon 8500 AIW BB (AGP), ATI Radeon IGP320M (U1) 4336,
    ATI Radeon IGP330M/340M/350M (U2) 4337,
    ATI Radeon Mobility 7000 IGP 4437, ATI Radeon 9000/PRO If (AGP/PCI),
    ATI Radeon 9000 Ig (AGP/PCI), ATI Radeon X800 (R420) JH (AGP),
    ATI Radeon X800PRO (R420) JI (AGP),
    ATI Radeon X800SE (R420) JJ (AGP), ATI Radeon X800 (R420) JK (AGP),
    ATI Radeon X800 (R420) JL (AGP), ATI FireGL X3 (R420) JM (AGP),
    ATI Radeon Mobility 9800 (M18) JN (AGP),
    ATI Radeon X800 SE (R420) (AGP), ATI Radeon X800XT (R420) JP (AGP),
    ATI Radeon X800 VE (R420) JT (AGP), ATI Radeon X850 (R480) (AGP),
    ATI Radeon X850 XT (R480) (AGP), ATI Radeon X850 SE (R480) (AGP),
    ATI Radeon X850 PRO (R480) (AGP), ATI Radeon X850 XT PE (R480) (AGP),
    ATI Radeon Mobility M7 LW (AGP),
    ATI Mobility FireGL 7800 M7 LX (AGP),
    ATI Radeon Mobility M6 LY (AGP), ATI Radeon Mobility M6 LZ (AGP),
    ATI FireGL Mobility 9000 (M9) Ld (AGP),
    ATI Radeon Mobility 9000 (M9) Lf (AGP),
    ATI Radeon Mobility 9000 (M9) Lg (AGP), ATI FireMV 2400 PCI,
    ATI Radeon 9700 Pro ND (AGP), ATI Radeon 9700/9500Pro NE (AGP),
    ATI Radeon 9600TX NF (AGP), ATI FireGL X1 NG (AGP),
    ATI Radeon 9800PRO NH (AGP), ATI Radeon 9800 NI (AGP),
    ATI FireGL X2 NK (AGP), ATI Radeon 9800XT NJ (AGP),
    ATI Radeon Mobility 9600/9700 (M10/M11) NP (AGP),
    ATI Radeon Mobility 9600 (M10) NQ (AGP),
    ATI Radeon Mobility 9600 (M11) NR (AGP),
    ATI Radeon Mobility 9600 (M10) NS (AGP),
    ATI FireGL Mobility T2 (M10) NT (AGP),
    ATI FireGL Mobility T2e (M11) NV (AGP), ATI Radeon QD (AGP),
    ATI Radeon QE (AGP), ATI Radeon QF (AGP), ATI Radeon QG (AGP),
    ATI FireGL 8700/8800 QH (AGP), ATI Radeon 8500 QL (AGP),
    ATI Radeon 9100 QM (AGP), ATI Radeon 7500 QW (AGP/PCI),
    ATI Radeon 7500 QX (AGP/PCI), ATI Radeon VE/7000 QY (AGP/PCI),
    ATI Radeon VE/7000 QZ (AGP/PCI), ATI ES1000 515E (PCI),
    ATI Radeon Mobility X300 (M22) 5460 (PCIE),
    ATI Radeon Mobility X600 SE (M24C) 5462 (PCIE),
    ATI FireGL M22 GL 5464 (PCIE), ATI Radeon X800 (R423) UH (PCIE),
    ATI Radeon X800PRO (R423) UI (PCIE),
    ATI Radeon X800LE (R423) UJ (PCIE),
    ATI Radeon X800SE (R423) UK (PCIE),
    ATI Radeon X800 XTP (R430) (PCIE), ATI Radeon X800 XL (R430) (PCIE),
    ATI Radeon X800 SE (R430) (PCIE), ATI Radeon X800 (R430) (PCIE),
    ATI FireGL V7100 (R423) (PCIE), ATI FireGL V5100 (R423) UQ (PCIE),
    ATI FireGL unknown (R423) UR (PCIE),
    ATI FireGL unknown (R423) UT (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility FireGL V5000 (M26) (PCIE),
    ATI Mobility Radeon X700 XL (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Mobility Radeon X700 (M26) (PCIE),
    ATI Radeon X550XTX 5657 (PCIE), ATI Radeon 9100 IGP (A5) 5834,
    ATI Radeon Mobility 9100 IGP (U3) 5835,
    ATI Radeon XPRESS 200 5954 (PCIE),
    ATI Radeon XPRESS 200M 5955 (PCIE), ATI Radeon 9250 5960 (AGP),
    ATI Radeon 9200 5961 (AGP), ATI Radeon 9200 5962 (AGP),
    ATI Radeon 9200SE 5964 (AGP), ATI FireMV 2200 (PCI),
    ATI ES1000 5969 (PCI), ATI Radeon XPRESS 200 5974 (PCIE),
    ATI Radeon XPRESS 200M 5975 (PCIE),
    ATI Radeon XPRESS 200 5A41 (PCIE),
    ATI Radeon XPRESS 200M 5A42 (PCIE),
    ATI Radeon XPRESS 200 5A61 (PCIE),
    ATI Radeon XPRESS 200M 5A62 (PCIE),
    ATI Radeon X300 (RV370) 5B60 (PCIE),
    ATI Radeon X600 (RV370) 5B62 (PCIE),
    ATI Radeon X550 (RV370) 5B63 (PCIE),
    ATI FireGL V3100 (RV370) 5B64 (PCIE),
    ATI FireMV 2200 PCIE (RV370) 5B65 (PCIE),
    ATI Radeon Mobility 9200 (M9+) 5C61 (AGP),
    ATI Radeon Mobility 9200 (M9+) 5C63 (AGP),
    ATI Mobility Radeon X800 XT (M28) (PCIE),
    ATI Mobility FireGL V5100 (M28) (PCIE),
    ATI Mobility Radeon X800 (M28) (PCIE), ATI Radeon X850 5D4C (PCIE),
    ATI Radeon X850 XT PE (R480) (PCIE),
    ATI Radeon X850 SE (R480) (PCIE), ATI Radeon X850 PRO (R480) (PCIE),
    ATI unknown Radeon / FireGL (R480) 5D50 (PCIE),
    ATI Radeon X850 XT (R480) (PCIE),
    ATI Radeon X800XT (R423) 5D57 (PCIE),
    ATI FireGL V5000 (RV410) (PCIE), ATI Radeon X700 XT (RV410) (PCIE),
    ATI Radeon X700 PRO (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X700 (RV410) (PCIE),
    ATI Radeon X700 SE (RV410) (PCIE), ATI Radeon X1800,
    ATI Mobility Radeon X1800 XT, ATI Mobility Radeon X1800,
    ATI Mobility FireGL V7200, ATI FireGL V7200, ATI FireGL V5300,
    ATI Mobility FireGL V7100, ATI Radeon X1800, ATI Radeon X1800,
    ATI Radeon X1800, ATI Radeon X1800, ATI Radeon X1800,
    ATI FireGL V7300, ATI FireGL V7350, ATI Radeon X1600, ATI RV505,
    ATI Radeon X1300/X1550, ATI Radeon X1550, ATI M54-GL,
    ATI Mobility Radeon X1400, ATI Radeon X1300/X1550,
    ATI Radeon X1550 64-bit, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Mobility Radeon X1300,
    ATI Mobility Radeon X1300, ATI Radeon X1300, ATI Radeon X1300,
    ATI RV505, ATI RV505, ATI FireGL V3300, ATI FireGL V3350,
    ATI Radeon X1300, ATI Radeon X1550 64-bit, ATI Radeon X1300/X1550,
    ATI Radeon X1600, ATI Radeon X1300/X1550, ATI Mobility Radeon X1450,
    ATI Radeon X1300/X1550, ATI Mobility Radeon X2300,
    ATI Mobility Radeon X2300, ATI Mobility Radeon X1350,
    ATI Mobility Radeon X1350, ATI Mobility Radeon X1450,
    ATI Radeon X1300, ATI Radeon X1550, ATI Mobility Radeon X1350,
    ATI FireMV 2250, ATI Radeon X1550 64-bit, ATI Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1600, ATI Radeon X1600,
    ATI Mobility FireGL V5200, ATI Mobility Radeon X1600,
    ATI Radeon X1650, ATI Radeon X1650, ATI Radeon X1600,
    ATI Radeon X1300 XT/X1600 Pro, ATI FireGL V3400,
    ATI Mobility FireGL V5250, ATI Mobility Radeon X1700,
    ATI Mobility Radeon X1700 XT, ATI FireGL V5200,
    ATI Mobility Radeon X1700, ATI Radeon X2300HD,
    ATI Mobility Radeon HD 2300, ATI Mobility Radeon HD 2300,
    ATI Radeon X1950, ATI Radeon X1900, ATI Radeon X1950,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI Radeon X1900, ATI Radeon X1900, ATI Radeon X1900,
    ATI AMD Stream Processor, ATI Radeon X1900, ATI Radeon X1950,
    ATI RV560, ATI RV560, ATI Mobility Radeon X1900, ATI RV560,
    ATI Radeon X1950 GT, ATI RV570, ATI RV570, ATI FireGL V7400,
    ATI RV560, ATI Radeon X1650, ATI Radeon X1650, ATI RV560,
    ATI Radeon 9100 PRO IGP 7834, ATI Radeon Mobility 9200 IGP 7835,
    ATI Radeon X1200, ATI Radeon X1200, ATI Radeon X1200,
    ATI Radeon X1200, ATI Radeon X1200, ATI RS740, ATI RS740M, ATI RS740,
    ATI RS740M, ATI Radeon HD 2900 XT, ATI Radeon HD 2900 XT,
    ATI Radeon HD 2900 XT, ATI Radeon HD 2900 Pro, ATI Radeon HD 2900 GT,
    ATI FireGL V8650, ATI FireGL V8600, ATI FireGL V7600,
    ATI Radeon 4800 Series, ATI Radeon HD 4870 x2,
    ATI Radeon 4800 Series, ATI Radeon HD 4850 x2,
    ATI FirePro V8750 (FireGL), ATI FirePro V7760 (FireGL),
    ATI Mobility RADEON HD 4850, ATI Mobility RADEON HD 4850 X2,
    ATI Radeon 4800 Series, ATI FirePro RV770, AMD FireStream 9270,
    AMD FireStream 9250, ATI FirePro V8700 (FireGL),
    ATI Mobility RADEON HD 4870, ATI Mobility RADEON M98,
    ATI Mobility RADEON HD 4870, ATI Radeon 4800 Series,
    ATI Radeon 4800 Series, ATI FirePro M7750, ATI M98, ATI M98, ATI M98,
    ATI Mobility Radeon HD 4650, ATI Radeon RV730 (AGP),
    ATI Mobility Radeon HD 4670, ATI FirePro M5750,
    ATI Mobility Radeon HD 4670, ATI Radeon RV730 (AGP),
    ATI RV730XT [Radeon HD 4670], ATI RADEON E4600,
    ATI Radeon HD 4600 Series, ATI RV730 PRO [Radeon HD 4650],
    ATI FirePro V7750 (FireGL), ATI FirePro V5700 (FireGL),
    ATI FirePro V3750 (FireGL), ATI Mobility Radeon HD 4830,
    ATI Mobility Radeon HD 4850, ATI FirePro M7740, ATI RV740,
    ATI Radeon HD 4770, ATI Radeon HD 4700 Series, ATI Radeon HD 4770,
    ATI FirePro M5750, ATI RV610, ATI Radeon HD 2400 XT,
    ATI Radeon HD 2400 Pro, ATI Radeon HD 2400 PRO AGP, ATI FireGL V4000,
    ATI RV610, ATI Radeon HD 2350, ATI Mobility Radeon HD 2400 XT,
    ATI Mobility Radeon HD 2400, ATI RADEON E2400, ATI RV610,
    ATI FireMV 2260, ATI RV670, ATI Radeon HD3870,
    ATI Mobility Radeon HD 3850, ATI Radeon HD3850,
    ATI Mobility Radeon HD 3850 X2, ATI RV670,
    ATI Mobility Radeon HD 3870, ATI Mobility Radeon HD 3870 X2,
    ATI Radeon HD3870 X2, ATI FireGL V7700, ATI Radeon HD3850,
    ATI Radeon HD3690, AMD Firestream 9170, ATI Radeon HD 4550,
    ATI Radeon RV710, ATI Radeon RV710, ATI Radeon RV710,
    ATI Radeon HD 4350, ATI Mobility Radeon 4300 Series,
    ATI Mobility Radeon 4500 Series, ATI Mobility Radeon 4500 Series,
    ATI FirePro RG220, ATI Mobility Radeon 4330, ATI RV630,
    ATI Mobility Radeon HD 2600, ATI Mobility Radeon HD 2600 XT,
    ATI Radeon HD 2600 XT AGP, ATI Radeon HD 2600 Pro AGP,
    ATI Radeon HD 2600 XT, ATI Radeon HD 2600 Pro, ATI Gemini RV630,
    ATI Gemini Mobility Radeon HD 2600 XT, ATI FireGL V5600,
    ATI FireGL V3600, ATI Radeon HD 2600 LE,
    ATI Mobility FireGL Graphics Processor, ATI Radeon HD 3470,
    ATI Mobility Radeon HD 3430, ATI Mobility Radeon HD 3400 Series,
    ATI Radeon HD 3450, ATI Radeon HD 3450, ATI Radeon HD 3430,
    ATI Radeon HD 3450, ATI FirePro V3700, ATI FireMV 2450,
    ATI FireMV 2260, ATI FireMV 2260, ATI Radeon HD 3600 Series,
    ATI Radeon HD 3650 AGP, ATI Radeon HD 3600 PRO,
    ATI Radeon HD 3600 XT, ATI Radeon HD 3600 PRO,
    ATI Mobility Radeon HD 3650, ATI Mobility Radeon HD 3670,
    ATI Mobility FireGL V5700, ATI Mobility FireGL V5725,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3200 Graphics, ATI Radeon 3100 Graphics,
    ATI Radeon HD 3300 Graphics, ATI Radeon HD 3200 Graphics,
    ATI Radeon 3000 Graphics, SUMO, SUMO, SUMO2, SUMO2, SUMO2, SUMO2,
    SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, SUMO, ATI Radeon HD 4200,
    ATI Radeon 4100, ATI Mobility Radeon HD 4200,
    ATI Mobility Radeon 4100, ATI Radeon HD 4290, ATI Radeon HD 4250,
    AMD Radeon HD 6310 Graphics, AMD Radeon HD 6310 Graphics,
    AMD Radeon HD 6250 Graphics, AMD Radeon HD 6250 Graphics,
    AMD Radeon HD 6300 Series Graphics,
    AMD Radeon HD 6200 Series Graphics, PALM, PALM, PALM, CYPRESS,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, AMD Firestream 9370,
    AMD Firestream 9350, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5800 Series,
    ATI Radeon HD 5800 Series, ATI Radeon HD 5900 Series,
    ATI Radeon HD 5900 Series, ATI Mobility Radeon HD 5800 Series,
    ATI Mobility Radeon HD 5800 Series,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI Mobility Radeon HD 5800 Series, ATI Radeon HD 5700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Radeon HD 5700 Series, ATI Radeon HD 6700 Series,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon HD 5570,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI Radeon HD 5670,
    ATI Radeon HD 5570, ATI Radeon HD 5500 Series, REDWOOD,
    ATI Mobility Radeon HD 5000 Series,
    ATI Mobility Radeon HD 5000 Series, ATI Mobility Radeon Graphics,
    ATI Mobility Radeon Graphics, CEDAR,
    ATI FirePro (FireGL) Graphics Adapter,
    ATI FirePro (FireGL) Graphics Adapter, ATI FirePro 2270, CEDAR,
    ATI Radeon HD 5450, CEDAR, CEDAR, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN, CAYMAN,
    AMD Radeon HD 6900 Series, AMD Radeon HD 6900 Series, CAYMAN, CAYMAN,
    CAYMAN, AMD Radeon HD 6900M Series, Mobility Radeon HD 6000 Series,
    BARTS, BARTS, Mobility Radeon HD 6000 Series,
    Mobility Radeon HD 6000 Series, BARTS, BARTS, BARTS, BARTS,
    AMD Radeon HD 6800 Series, AMD Radeon HD 6800 Series,
    AMD Radeon HD 6700 Series, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS, TURKS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS,
    CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, CAICOS, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA, ARUBA,
    ARUBA, ARUBA, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI,
    TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, TAHITI, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN,
    PITCAIRN, PITCAIRN, PITCAIRN, PITCAIRN, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE, VERDE,
    VERDE, VERDE, VERDE, VERDE, VERDE, VERDE
[   426.976] (II) VESA: driver for VESA chipsets: vesa
[   426.976] (II) modesetting: Driver for Modesetting Kernel Drivers: kms
[   426.976] (II) FBDEV: driver for framebuffer: fbdev
[   426.976] (++) using VT number 7


[   426.980] (WW) Falling back to old probe method for fglrx
[   426.983] (II) Loading PCS database from /etc/ati/amdpcsdb /etc/ati/amdpcsdb.default
[   426.992] ukiDynamicMajor: found major device number 249
[   426.992] (--) Assigning device section with no busID to primary device
[   426.992] (--) Chipset Supported AMD Graphics Processor (0x6739) found
[   426.993] (WW) fglrx: No matching Device section for instance (BusID PCI:0@1:0:1) found
[   426.993] (II) AMD Video driver is running on a device belonging to a group targeted for this release
[   426.993] (II) AMD Video driver is signed
[   426.993] (II) fglrx(0): pEnt->device->identifier=0x7f133beb16a7
[   426.993] (WW) Falling back to old probe method for vesa
[   426.993] (WW) Falling back to old probe method for modesetting
[   426.993] (EE) open /dev/dri/card0: No such file or directory
[   426.993] (WW) Falling back to old probe method for fbdev
[   426.993] (II) Loading sub module "fbdevhw"
[   426.993] (II) LoadModule: "fbdevhw"
[   426.993] (II) Loading /usr/lib/xorg/modules/libfbdevhw.so
[   426.993] (II) Module fbdevhw: vendor="X.Org Foundation"
[   426.993]     compiled for 1.13.3, module version = 0.0.2
[   426.993]     ABI class: X.Org Video Driver, version 13.1
[   426.993] (II) fglrx(0): === [xdl_xs113_atiddxPreInit] === begin
[   426.993] (II) Loading sub module "vgahw"
[   426.993] (II) LoadModule: "vgahw"
[   426.994] (II) Loading /usr/lib/xorg/modules/libvgahw.so
[   426.994] (II) Module vgahw: vendor="X.Org Foundation"
[   426.994]     compiled for 1.13.3, module version = 0.1.0
[   426.994]     ABI class: X.Org Video Driver, version 13.1
[   426.994] (II) fglrx(0): Creating default Display subsection in Screen section
    "Default Screen Section" for depth/fbbpp 24/32
[   426.994] (==) fglrx(0): Depth 24, (==) framebuffer bpp 32
[   426.994] (II) fglrx(0): Pixel depth = 24 bits stored in 4 bytes (32 bpp pixmaps)
[   426.994] (==) fglrx(0): Default visual is TrueColor
[   426.994] (==) fglrx(0): RGB weight 888
[   426.994] (II) fglrx(0): Using 8 bits per RGB 
[   426.994] (==) fglrx(0): Buffer Tiling is ON
[   426.994] (II) Loading sub module "fglrxdrm"
[   426.994] (II) LoadModule: "fglrxdrm"
[   426.994] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/linux/libfglrxdrm.so
[   426.994] (II) Module fglrxdrm: vendor="FireGL - AMD Technologies Inc."
[   426.994]     compiled for 1.4.99.906, module version = 9.1.11
[   427.001] ukiDynamicMajor: found major device number 249
[   427.001] ukiDynamicMajor: found major device number 249
[   427.001] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   427.001] ukiOpenDevice: node name is /dev/ati/card0
[   427.001] ukiOpenDevice: open result is 13, (OK)
[   427.292] ukiOpenByBusid: ukiOpenMinor returns 13
[   427.292] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   427.293] (**) fglrx(0): NoAccel = NO
[   427.293] (**) fglrx(0): AMD 2D Acceleration Architecture enabled
[   427.293] (--) fglrx(0): Chipset: "AMD Radeon HD 6800 Series  " (Chipset = 0x6739)
[   427.293] (--) fglrx(0): (PciSubVendor = 0x174b, PciSubDevice = 0x174b)
[   427.293] (==) fglrx(0): board vendor info: third party graphics adapter - NOT original AMD
[   427.293] (--) fglrx(0): Linear framebuffer (phys) at 0xe0000000
[   427.293] (--) fglrx(0): MMIO registers at 0xfbcc0000
[   427.293] (--) fglrx(0): I/O port at 0x0000de00
[   427.293] (==) fglrx(0): ROM-BIOS at 0x000c0000
[   427.293] (II) fglrx(0): AC Adapter is used
[   427.293] (II) fglrx(0): Primary V_BIOS segment is: 0xc000
[   427.293] (II) Loading sub module "vbe"
[   427.293] (II) LoadModule: "vbe"
[   427.293] (II) Loading /usr/lib/xorg/modules/libvbe.so
[   427.294] (II) Module vbe: vendor="X.Org Foundation"
[   427.294]     compiled for 1.13.3, module version = 1.1.0
[   427.294]     ABI class: X.Org Video Driver, version 13.1
[   427.294] (II) fglrx(0): VESA BIOS detected
[   427.294] (II) fglrx(0): VESA VBE Version 3.0
[   427.294] (II) fglrx(0): VESA VBE Total Mem: 16384 kB
[   427.294] (II) fglrx(0): VESA VBE OEM: AMD ATOMBIOS
[   427.294] (II) fglrx(0): VESA VBE OEM Software Rev: 13.12
[   427.294] (II) fglrx(0): VESA VBE OEM Vendor: (C) 1988-2010, AMD Technologies Inc. 
[   427.294] (II) fglrx(0): VESA VBE OEM Product: BARTS
[   427.294] (II) fglrx(0): VESA VBE OEM Product Rev: 01.00
[   427.294] (II) fglrx(0): AMD Video BIOS revision 9 or later detected
[   427.294] (--) fglrx(0): Video RAM: 1048576 kByte, Type: GDDR5
[   427.294] (II) fglrx(0): PCIE card detected
[   427.294] (--) fglrx(0): Using per-process page tables (PPPT) as GART.
[   427.294] (WW) fglrx(0): board is an unknown third party board, chipset is supported
[   427.294] (II) fglrx(0): [FB] MC range(MCFBBase = 0xf00000000, MCFBSize = 0x40000000)
[   427.294] (II) fglrx(0): RandR 1.2 support is enabled!
[   427.294] (II) fglrx(0): RandR 1.2 rotation support is enabled!
[   427.294] (==) fglrx(0): Center Mode is disabled 
[   427.294] (II) Loading sub module "fb"
[   427.294] (II) LoadModule: "fb"
[   427.294] (II) Loading /usr/lib/xorg/modules/libfb.so
[   427.294] (II) Module fb: vendor="X.Org Foundation"
[   427.294]     compiled for 1.13.3, module version = 1.0.0
[   427.294]     ABI class: X.Org ANSI C Emulation, version 0.4
[   427.294] (II) Loading sub module "ddc"
[   427.294] (II) LoadModule: "ddc"
[   427.294] (II) Module "ddc" already built-in
[   427.367] (II) fglrx(0): Output DFP1 has no monitor section
[   427.367] (II) fglrx(0): Output DFP2 has no monitor section
[   427.367] (II) fglrx(0): Output DFP3 has no monitor section
[   427.367] (II) fglrx(0): Output DFP4 has no monitor section
[   427.367] (II) fglrx(0): Output DFP5 has no monitor section
[   427.367] (II) fglrx(0): Output DFP6 has no monitor section
[   427.367] (II) fglrx(0): Output DFP7 has no monitor section
[   427.367] (II) fglrx(0): Output CRT1 has no monitor section
[   427.367] (II) Loading sub module "ddc"
[   427.367] (II) LoadModule: "ddc"
[   427.367] (II) Module "ddc" already built-in
[   427.367] (II) fglrx(0): Connected Display0: DFP6
[   427.367] (II) fglrx(0):  Display0: Failed to get EDID information. 
[   427.368] (II) fglrx(0): EDID for output DFP1
[   427.368] (II) fglrx(0): EDID for output DFP2
[   427.368] (II) fglrx(0): EDID for output DFP3
[   427.368] (II) fglrx(0): EDID for output DFP4
[   427.368] (II) fglrx(0): EDID for output DFP5
[   427.368] (II) fglrx(0): EDID for output DFP6
[   427.368] (II) fglrx(0): Manufacturer: DEL  Model: f011  Serial#: 826552652
[   427.368] (II) fglrx(0): Year: 2009  Week: 39
[   427.368] (II) fglrx(0): EDID Version: 1.3
[   427.368] (II) fglrx(0): Digital Display Input
[   427.368] (II) fglrx(0): Max Image Size [cm]: horiz.: 47  vert.: 30
[   427.368] (II) fglrx(0): Gamma: 2.20
[   427.368] (II) fglrx(0): DPMS capabilities: Off
[   427.368] (II) fglrx(0): Supported color encodings: RGB 4:4:4 YCrCb 4:4:4 
[   427.368] (II) fglrx(0): Default color space is primary color space
[   427.368] (II) fglrx(0): First detailed timing is preferred mode
[   427.368] (II) fglrx(0): redX: 0.640 redY: 0.330   greenX: 0.300 greenY: 0.600
[   427.368] (II) fglrx(0): blueX: 0.150 blueY: 0.060   whiteX: 0.313 whiteY: 0.329
[   427.368] (II) fglrx(0): Supported established timings:
[   427.368] (II) fglrx(0): 720x400@70Hz
[   427.368] (II) fglrx(0): 640x480@60Hz
[   427.368] (II) fglrx(0): 640x480@75Hz
[   427.368] (II) fglrx(0): 800x600@60Hz
[   427.368] (II) fglrx(0): 800x600@75Hz
[   427.368] (II) fglrx(0): 1024x768@60Hz
[   427.368] (II) fglrx(0): 1024x768@75Hz
[   427.368] (II) fglrx(0): 1280x1024@75Hz
[   427.368] (II) fglrx(0): Manufacturer's mask: 0
[   427.368] (II) fglrx(0): Supported standard timings:
[   427.368] (II) fglrx(0): #0: hsize: 1152  vsize 864  refresh: 75  vid: 20337
[   427.368] (II) fglrx(0): #1: hsize: 1280  vsize 1024  refresh: 60  vid: 32897
[   427.368] (II) fglrx(0): #2: hsize: 1680  vsize 1050  refresh: 60  vid: 179
[   427.368] (II) fglrx(0): Supported detailed timing:
[   427.368] (II) fglrx(0): clock: 146.2 MHz   Image Size:  474 x 296 mm
[   427.368] (II) fglrx(0): h_active: 1680  h_sync: 1784  h_sync_end 1960 h_blank_end 2240 h_border: 0
[   427.368] (II) fglrx(0): v_active: 1050  v_sync: 1053  v_sync_end 1059 v_blanking: 1089 v_border: 0
[   427.368] (II) fglrx(0): Serial No: H736H99L1D1L
[   427.368] (II) fglrx(0): Monitor name: DELL 2209WA
[   427.368] (II) fglrx(0): Ranges: V min: 56 V max: 75 Hz, H min: 30 H max: 83 kHz, PixClock max 165 MHz
[   427.368] (II) fglrx(0): EDID (in hex):
[   427.368] (II) fglrx(0):     00ffffffffffff0010ac11f04c314431
[   427.368] (II) fglrx(0):     27130103802f1e782eee95a3544c9926
[   427.368] (II) fglrx(0):     0f5054a54b00714f8180b30001010101
[   427.368] (II) fglrx(0):     01010101010121399030621a274068b0
[   427.368] (II) fglrx(0):     3600da281100001c000000ff00483733
[   427.368] (II) fglrx(0):     364839394c3144314c0a000000fc0044
[   427.368] (II) fglrx(0):     454c4c203232303957410a20000000fd
[   427.368] (II) fglrx(0):     00384b1e5310000a2020202020200006
[   427.368] (II) fglrx(0): Printing probed modes for output DFP6
[   427.368] (II) fglrx(0): Modeline "1680x1050"x60.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   427.368] (II) fglrx(0): Modeline "1400x1050"x60.0  146.25  1400 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1600x900"x60.0  146.25  1600 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1360x1024"x60.0  146.25  1360 1784 1960 2240  1024 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x1024"x75.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x1024"x60.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1440x900"x60.0  146.25  1440 1784 1960 2240  900 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x960"x75.0  135.00  1280 1296 1440 1688  960 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x960"x60.0  108.00  1280 1328 1440 1688  960 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x800"x75.0  135.00  1280 1296 1440 1688  800 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x800"x60.0  108.00  1280 1328 1440 1688  800 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1152x864"x60.0  146.25  1152 1784 1960 2240  864 1053 1059 1089 -hsync +vsync (65.3 kHz e)
[   427.368] (II) fglrx(0): Modeline "1152x864"x75.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x768"x75.0  135.00  1280 1296 1440 1688  768 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x768"x60.0  108.00  1280 1328 1440 1688  768 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x720"x75.0  135.00  1280 1296 1440 1688  720 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1280x720"x60.0  108.00  1280 1328 1440 1688  720 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1024x768"x75.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   427.368] (II) fglrx(0): Modeline "1024x768"x60.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   427.368] (II) fglrx(0): Modeline "800x600"x75.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   427.368] (II) fglrx(0): Modeline "800x600"x60.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   427.368] (II) fglrx(0): Modeline "640x480"x75.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   427.368] (II) fglrx(0): Modeline "640x480"x60.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   427.368] (II) fglrx(0): EDID for output DFP7
[   427.368] (II) fglrx(0): EDID for output CRT1
[   427.368] (II) fglrx(0): Output DFP1 disconnected
[   427.368] (II) fglrx(0): Output DFP2 disconnected
[   427.368] (II) fglrx(0): Output DFP3 disconnected
[   427.368] (II) fglrx(0): Output DFP4 disconnected
[   427.368] (II) fglrx(0): Output DFP5 disconnected
[   427.368] (II) fglrx(0): Output DFP6 connected
[   427.368] (II) fglrx(0): Output DFP7 disconnected
[   427.368] (II) fglrx(0): Output CRT1 disconnected
[   427.368] (II) fglrx(0): Using exact sizes for initial modes
[   427.368] (II) fglrx(0): Output DFP6 using initial mode 1680x1050
[   427.368] (II) fglrx(0): Using default gamma of (1.0, 1.0, 1.0) unless otherwise stated.
[   427.368] (II) fglrx(0): DPI set to (96, 96)
[   427.368] (II) fglrx(0): Eyefinity capable adapter detected.
[   427.368] (II) fglrx(0): Adapter AMD Radeon HD 6800 Series   has 6 configurable heads and 1 displays connected.
[   427.368] (==) fglrx(0):  PseudoColor visuals disabled
[   427.368] (II) Loading sub module "ramdac"
[   427.368] (II) LoadModule: "ramdac"
[   427.368] (II) Module "ramdac" already built-in
[   427.368] (==) fglrx(0): NoDRI = NO
[   427.368] (==) fglrx(0): Capabilities: 0x00000000
[   427.368] (==) fglrx(0): CapabilitiesEx: 0x00000000
[   427.368] (==) fglrx(0): OpenGL ClientDriverName: "fglrx_dri.so"
[   427.368] (==) fglrx(0): UseFastTLS=0
[   427.368] (II) fglrx(0): Shadow Primary option: ShadowPrimary is enabled
[   427.368] (II) UnloadModule: "radeon"
[   427.368] (II) Unloading radeon
[   427.368] (II) UnloadModule: "vesa"
[   427.368] (II) Unloading vesa
[   427.368] (II) UnloadModule: "modesetting"
[   427.368] (II) Unloading modesetting
[   427.368] (II) UnloadModule: "fbdev"
[   427.368] (II) Unloading fbdev
[   427.368] (II) UnloadSubModule: "fbdevhw"
[   427.368] (II) Unloading fbdevhw
[   427.369] (--) Depth 24 pixmap format is 32 bpp
[   427.370] Loading extension ATIFGLRXDRI
[   427.370] (II) fglrx(0): doing swlDriScreenInit
[   427.370] (II) fglrx(0): swlDriScreenInit for fglrx driver
[   427.370] ukiDynamicMajor: found major device number 249
[   427.370] ukiDynamicMajor: found major device number 249
[   427.370] ukiDynamicMajor: found major device number 249
[   427.370] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   427.370] ukiOpenDevice: node name is /dev/ati/card0
[   427.370] ukiOpenDevice: open result is 14, (OK)
[   427.370] ukiOpenByBusid: ukiOpenMinor returns 14
[   427.370] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   427.370] (II) fglrx(0): [uki] DRM interface version 1.0
[   427.370] (II) fglrx(0): [uki] created "fglrx" driver at busid "PCI:1:0:0"
[   427.370] (II) fglrx(0): [uki] added 8192 byte SAREA at 0x2000
[   427.370] (II) fglrx(0): [uki] mapped SAREA 0x2000 to 0x7f133bcc9000
[   427.370] (II) fglrx(0): [uki] framebuffer handle = 0x3000
[   427.370] (II) fglrx(0): [uki] added 1 reserved context for kernel
[   427.370] (II) fglrx(0): swlDriScreenInit done
[   427.370] (II) fglrx(0): Kernel Module Version Information:
[   427.370] (II) fglrx(0):     Name: fglrx
[   427.370] (II) fglrx(0):     Version: 9.1.11
[   427.370] (II) fglrx(0):     Date: Dec 19 2012
[   427.370] (II) fglrx(0):     Desc: AMD FireGL DRM kernel module
[   427.371] (II) fglrx(0): Kernel Module version matches driver.
[   427.371] (II) fglrx(0): Kernel Module Build Time Information:
[   427.371] (II) fglrx(0):     Build-Kernel UTS_RELEASE:        3.8.0-23-generic
[   427.371] (II) fglrx(0):     Build-Kernel MODVERSIONS:        yes
[   427.371] (II) fglrx(0):     Build-Kernel __SMP__:            yes
[   427.371] (II) fglrx(0):     Build-Kernel PAGE_SIZE:          0x1000
[   427.371] (II) fglrx(0): [uki] register handle = 0x00004000
[   427.371] (II) fglrx(0): DRI initialization successfull
[   427.371] (II) fglrx(0): FBADPhys: 0xf00000000 FBMappedSize: 0x01008000
[   427.371] (==) fglrx(0): Backing store disabled
[   427.371] Loading extension FGLRXEXTENSION
[   427.371] (==) fglrx(0): DPMS enabled
[   427.371] (II) fglrx(0): Initialized in-driver Xinerama extension
[   427.371] (**) fglrx(0): Textured Video is enabled.
[   427.371] (II) LoadModule: "glesx"
[   427.372] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/glesx.so
[   427.372] (II) Module glesx: vendor="X.Org Foundation"
[   427.372]     compiled for 1.4.99.906, module version = 1.0.0
[   427.372] Loading extension GLESX
[   427.372] (II) fglrx(0): GLESX enableFlags = 592
[   427.372] (II) fglrx(0): GLESX is enabled
[   427.372] (II) LoadModule: "amdxmm"
[   427.372] (II) Loading /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/amdxmm.so
[   427.372] (II) Module amdxmm: vendor="X.Org Foundation"
[   427.372]     compiled for 1.4.99.906, module version = 2.0.0
[   427.387] Loading extension AMDXVOPL
[   427.387] Loading extension AMDXVBA
[   427.387] (II) fglrx(0): UVD feature is enabled(II) fglrx(0): 
[   427.388] (II) fglrx(0): Enable composite support successfully
[   427.388] (II) fglrx(0): X context handle = 0x1
[   427.388] (II) fglrx(0): [DRI] installation complete
[   427.388] (==) fglrx(0): Silken mouse enabled
[   427.388] (==) fglrx(0): Using HW cursor of display infrastructure!
[   427.388] (II) fglrx(0): RandR 1.2 enabled, ignore the following RandR disabled message.
[   427.433] (--) RandR disabled
[   427.436] (II) SELinux: Disabled on system
[   427.436] ukiDynamicMajor: found major device number 249
[   427.436] ukiDynamicMajor: found major device number 249
[   427.436] ukiOpenByBusid: Searching for BusID PCI:1:0:0
[   427.436] ukiOpenDevice: node name is /dev/ati/card0
[   427.436] ukiOpenDevice: open result is 15, (OK)
[   427.436] ukiOpenByBusid: ukiOpenMinor returns 15
[   427.436] ukiOpenByBusid: ukiGetBusid reports PCI:1:0:0
[   427.477] (II) AIGLX: Loaded and initialized OpenGL driver(II) GLX: Initialized DRI GL provider for screen 0
[   427.485] (II) fglrx(0): Setting screen physical size to 444 x 277
[   427.489] (II) XKB: reuse xkmfile /var/lib/xkb/server-B20D7FC79C7F597315E3E501AEF10E0D866E8E92.xkm
[   427.490] (II) config/udev: Adding input device Power Button (/dev/input/event1)
[   427.490] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   427.490] (II) LoadModule: "evdev"
[   427.490] (II) Loading /usr/lib/xorg/modules/input/evdev_drv.so
[   427.491] (II) Module evdev: vendor="X.Org Foundation"
[   427.491]     compiled for 1.13.3, module version = 2.7.3
[   427.491]     Module class: X.Org XInput Driver
[   427.491]     ABI class: X.Org XInput driver, version 18.0
[   427.491] (II) Using input driver 'evdev' for 'Power Button'
[   427.491] (**) Power Button: always reports core events
[   427.491] (**) evdev: Power Button: Device: "/dev/input/event1"
[   427.491] (--) evdev: Power Button: Vendor 0 Product 0x1
[   427.491] (--) evdev: Power Button: Found keys
[   427.491] (II) evdev: Power Button: Configuring as keyboard
[   427.491] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXPWRBN:00/input/input1/event1"
[   427.491] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 6)
[   427.491] (**) Option "xkb_rules" "evdev"
[   427.491] (**) Option "xkb_model" "pc105"
[   427.491] (**) Option "xkb_layout" "us"
[   427.491] (II) config/udev: Adding input device Power Button (/dev/input/event0)
[   427.491] (**) Power Button: Applying InputClass "evdev keyboard catchall"
[   427.491] (II) Using input driver 'evdev' for 'Power Button'
[   427.491] (**) Power Button: always reports core events
[   427.491] (**) evdev: Power Button: Device: "/dev/input/event0"
[   427.491] (--) evdev: Power Button: Vendor 0 Product 0x1
[   427.491] (--) evdev: Power Button: Found keys
[   427.491] (II) evdev: Power Button: Configuring as keyboard
[   427.491] (**) Option "config_info" "udev:/sys/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input0/event0"
[   427.491] (II) XINPUT: Adding extended input device "Power Button" (type: KEYBOARD, id 7)
[   427.491] (**) Option "xkb_rules" "evdev"
[   427.491] (**) Option "xkb_model" "pc105"
[   427.491] (**) Option "xkb_layout" "us"
[   427.492] (II) config/udev: Adding input device HD-Audio Generic HDMI/DP,pcm=3 (/dev/input/event14)
[   427.492] (II) No input driver specified, ignoring this device.
[   427.492] (II) This device may have been added with another device file.
[   427.492] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event5)
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   427.492] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event5"
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[   427.492] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.0/input/input5/event5"
[   427.492] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 8)
[   427.492] (**) Option "xkb_rules" "evdev"
[   427.492] (**) Option "xkb_model" "pc105"
[   427.492] (**) Option "xkb_layout" "us"
[   427.492] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event6)
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev keyboard catchall"
[   427.492] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event6"
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found keys
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as keyboard
[   427.492] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.1/input/input6/event6"
[   427.492] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: KEYBOARD, id 9)
[   427.492] (**) Option "xkb_rules" "evdev"
[   427.492] (**) Option "xkb_model" "pc105"
[   427.492] (**) Option "xkb_layout" "us"
[   427.492] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/event7)
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: Applying InputClass "evdev pointer catchall"
[   427.492] (II) Using input driver 'evdev' for 'Mitsumi Electric Apple Extended USB Keyboard'
[   427.492] (**) Mitsumi Electric Apple Extended USB Keyboard: always reports core events
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: Device: "/dev/input/event7"
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Vendor 0x5ac Product 0x204
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found 9 mouse buttons
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found scroll wheel(s)
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found relative axes
[   427.492] (--) evdev: Mitsumi Electric Apple Extended USB Keyboard: Found x and y relative axes
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Configuring as mouse
[   427.492] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Adding scrollwheel support
[   427.492] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: YAxisMapping: buttons 4 and 5
[   427.493] (**) evdev: Mitsumi Electric Apple Extended USB Keyboard: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   427.493] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.3/1-1.3.1/1-1.3.1:1.2/input/input7/event7"
[   427.493] (II) XINPUT: Adding extended input device "Mitsumi Electric Apple Extended USB Keyboard" (type: MOUSE, id 10)
[   427.493] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: initialized for relative axes.
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) keeping acceleration scheme 1
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) acceleration profile 0
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) acceleration factor: 2.000
[   427.493] (**) Mitsumi Electric Apple Extended USB Keyboard: (accel) acceleration threshold: 4
[   427.493] (II) config/udev: Adding input device Mitsumi Electric Apple Extended USB Keyboard (/dev/input/mouse1)
[   427.493] (II) No input driver specified, ignoring this device.
[   427.493] (II) This device may have been added with another device file.
[   427.493] (II) config/udev: Adding input device Logitech Logitech USB Headset (/dev/input/event2)
[   427.493] (**) Logitech Logitech USB Headset: Applying InputClass "evdev keyboard catchall"
[   427.493] (II) Using input driver 'evdev' for 'Logitech Logitech USB Headset'
[   427.493] (**) Logitech Logitech USB Headset: always reports core events
[   427.493] (**) evdev: Logitech Logitech USB Headset: Device: "/dev/input/event2"
[   427.493] (--) evdev: Logitech Logitech USB Headset: Vendor 0x46d Product 0xa0c
[   427.493] (--) evdev: Logitech Logitech USB Headset: Found keys
[   427.493] (II) evdev: Logitech Logitech USB Headset: Configuring as keyboard
[   427.493] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.5/1-1.5:1.3/input/input2/event2"
[   427.493] (II) XINPUT: Adding extended input device "Logitech Logitech USB Headset" (type: KEYBOARD, id 11)
[   427.493] (**) Option "xkb_rules" "evdev"
[   427.493] (**) Option "xkb_model" "pc105"
[   427.493] (**) Option "xkb_layout" "us"
[   427.493] (II) config/udev: Adding input device Logitech G500 (/dev/input/event3)
[   427.493] (**) Logitech G500: Applying InputClass "evdev pointer catchall"
[   427.493] (II) Using input driver 'evdev' for 'Logitech G500'
[   427.493] (**) Logitech G500: always reports core events
[   427.493] (**) evdev: Logitech G500: Device: "/dev/input/event3"
[   427.493] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[   427.493] (--) evdev: Logitech G500: Found 20 mouse buttons
[   427.493] (--) evdev: Logitech G500: Found scroll wheel(s)
[   427.493] (--) evdev: Logitech G500: Found relative axes
[   427.493] (--) evdev: Logitech G500: Found x and y relative axes
[   427.493] (II) evdev: Logitech G500: Configuring as mouse
[   427.493] (II) evdev: Logitech G500: Adding scrollwheel support
[   427.493] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[   427.493] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   427.493] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input3/event3"
[   427.493] (II) XINPUT: Adding extended input device "Logitech G500" (type: MOUSE, id 12)
[   427.493] (II) evdev: Logitech G500: initialized for relative axes.
[   427.493] (**) Logitech G500: (accel) keeping acceleration scheme 1
[   427.493] (**) Logitech G500: (accel) acceleration profile 0
[   427.493] (**) Logitech G500: (accel) acceleration factor: 2.000
[   427.493] (**) Logitech G500: (accel) acceleration threshold: 4
[   427.494] (II) config/udev: Adding input device Logitech G500 (/dev/input/mouse0)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device Logitech G500 (/dev/input/event4)
[   427.494] (**) Logitech G500: Applying InputClass "evdev keyboard catchall"
[   427.494] (II) Using input driver 'evdev' for 'Logitech G500'
[   427.494] (**) Logitech G500: always reports core events
[   427.494] (**) evdev: Logitech G500: Device: "/dev/input/event4"
[   427.494] (--) evdev: Logitech G500: Vendor 0x46d Product 0xc068
[   427.494] (--) evdev: Logitech G500: Found 1 mouse buttons
[   427.494] (--) evdev: Logitech G500: Found scroll wheel(s)
[   427.494] (--) evdev: Logitech G500: Found relative axes
[   427.494] (II) evdev: Logitech G500: Forcing relative x/y axes to exist.
[   427.494] (--) evdev: Logitech G500: Found absolute axes
[   427.494] (II) evdev: Logitech G500: Forcing absolute x/y axes to exist.
[   427.494] (--) evdev: Logitech G500: Found keys
[   427.494] (II) evdev: Logitech G500: Configuring as mouse
[   427.494] (II) evdev: Logitech G500: Configuring as keyboard
[   427.494] (II) evdev: Logitech G500: Adding scrollwheel support
[   427.494] (**) evdev: Logitech G500: YAxisMapping: buttons 4 and 5
[   427.494] (**) evdev: Logitech G500: EmulateWheelButton: 4, EmulateWheelInertia: 10, EmulateWheelTimeout: 200
[   427.494] (**) Option "config_info" "udev:/sys/devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.1/input/input4/event4"
[   427.494] (II) XINPUT: Adding extended input device "Logitech G500" (type: KEYBOARD, id 13)
[   427.494] (**) Option "xkb_rules" "evdev"
[   427.494] (**) Option "xkb_model" "pc105"
[   427.494] (**) Option "xkb_layout" "us"
[   427.494] (II) evdev: Logitech G500: initialized for relative axes.
[   427.494] (WW) evdev: Logitech G500: ignoring absolute axes.
[   427.494] (**) Logitech G500: (accel) keeping acceleration scheme 1
[   427.494] (**) Logitech G500: (accel) acceleration profile 0
[   427.494] (**) Logitech G500: (accel) acceleration factor: 2.000
[   427.494] (**) Logitech G500: (accel) acceleration threshold: 4
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Front Mic (/dev/input/event10)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Rear Mic (/dev/input/event11)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Front Headphone (/dev/input/event12)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.494] (II) config/udev: Adding input device HDA Intel PCH Line Out (/dev/input/event13)
[   427.494] (II) No input driver specified, ignoring this device.
[   427.494] (II) This device may have been added with another device file.
[   427.495] (II) config/udev: Adding input device HDA Intel PCH HDMI/DP,pcm=3 (/dev/input/event8)
[   427.495] (II) No input driver specified, ignoring this device.
[   427.495] (II) This device may have been added with another device file.
[   427.495] (II) config/udev: Adding input device HDA Intel PCH Line (/dev/input/event9)
[   427.495] (II) No input driver specified, ignoring this device.
[   427.495] (II) This device may have been added with another device file.
[   427.497] (II) fglrx(0): Restoring Recent Mode via PCS is not supported in RANDR 1.2 capable environments
[   427.499] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   427.499] (II) fglrx(0): Using EDID range info for horizontal sync
[   427.499] (II) fglrx(0): Using EDID range info for vertical refresh
[   427.499] (II) fglrx(0): Printing DDC gathered Modelines:
[   427.499] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   427.499] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   427.499] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.499] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   427.499] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   427.499] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   427.499] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   427.499] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.499] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   427.841] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   427.841] (II) fglrx(0): Using hsync ranges from config file
[   427.841] (II) fglrx(0): Using vrefresh ranges from config file
[   427.841] (II) fglrx(0): Printing DDC gathered Modelines:
[   427.841] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   427.841] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   427.841] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   427.841] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   427.841] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   427.841] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   427.841] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   427.841] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   427.841] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   428.055] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   428.055] (II) fglrx(0): Using hsync ranges from config file
[   428.055] (II) fglrx(0): Using vrefresh ranges from config file
[   428.055] (II) fglrx(0): Printing DDC gathered Modelines:
[   428.055] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   428.055] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   428.055] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   428.055] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   428.055] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   428.055] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   428.055] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   428.055] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   428.055] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   428.273] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   430.993] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   434.630] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   434.630] (II) fglrx(0): Using hsync ranges from config file
[   434.630] (II) fglrx(0): Using vrefresh ranges from config file
[   434.630] (II) fglrx(0): Printing DDC gathered Modelines:
[   434.630] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   434.630] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   434.630] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   434.630] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   434.630] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   434.630] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   434.630] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   434.630] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   434.630] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   434.798] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   434.798] (II) fglrx(0): Using hsync ranges from config file
[   434.798] (II) fglrx(0): Using vrefresh ranges from config file
[   434.798] (II) fglrx(0): Printing DDC gathered Modelines:
[   434.798] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   434.798] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   434.798] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   434.798] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   434.798] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   434.798] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   434.798] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   434.798] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   434.798] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   434.820] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[   434.820] (II) fglrx(0): Using hsync ranges from config file
[   434.820] (II) fglrx(0): Using vrefresh ranges from config file
[   434.820] (II) fglrx(0): Printing DDC gathered Modelines:
[   434.820] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[   434.820] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[   434.820] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[   434.820] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[   434.820] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[   434.820] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[   434.820] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[   434.820] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[   434.820] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[   435.005] (II) XKB: reuse xkmfile /var/lib/xkb/server-8C3648A5FD728529D869F46730BE1BC287DB231C.xkm
[   489.364] (II) AIGLX: Suspending AIGLX clients for VT switch
[   489.364] (II) fglrx(0): Backup framebuffer data.
[   489.389] (II) fglrx(0): Backup complete.
[  3453.568] (II) AIGLX: Resuming AIGLX clients after VT switch
[  3453.697] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[  3453.697] (II) fglrx(0): Using hsync ranges from config file
[  3453.697] (II) fglrx(0): Using vrefresh ranges from config file
[  3453.697] (II) fglrx(0): Printing DDC gathered Modelines:
[  3453.697] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  3453.697] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3453.697] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3453.697] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3453.697] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  3453.718] (II) fglrx(0): Hot-plug event occurs on device: 1:0:0 
[  3453.730] (II) fglrx(0): EDID vendor "DEL", prod id 61457
[  3453.730] (II) fglrx(0): Using hsync ranges from config file
[  3453.730] (II) fglrx(0): Using vrefresh ranges from config file
[  3453.730] (II) fglrx(0): Printing DDC gathered Modelines:
[  3453.730] (II) fglrx(0): Modeline "1680x1050"x0.0  146.25  1680 1784 1960 2240  1050 1053 1059 1089 -hsync +vsync (65.3 kHz eP)
[  3453.730] (II) fglrx(0): Modeline "800x600"x0.0   40.00  800 840 968 1056  600 601 605 628 +hsync +vsync (37.9 kHz e)
[  3453.730] (II) fglrx(0): Modeline "640x480"x0.0   31.50  640 656 720 840  480 481 484 500 -hsync -vsync (37.5 kHz e)
[  3453.730] (II) fglrx(0): Modeline "640x480"x0.0   25.18  640 656 752 800  480 490 492 525 -hsync -vsync (31.5 kHz e)
[  3453.730] (II) fglrx(0): Modeline "720x400"x0.0   28.32  720 738 846 900  400 412 414 449 -hsync +vsync (31.5 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1280x1024"x0.0  135.00  1280 1296 1440 1688  1024 1025 1028 1066 +hsync +vsync (80.0 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1024x768"x0.0   78.75  1024 1040 1136 1312  768 769 772 800 +hsync +vsync (60.0 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1024x768"x0.0   65.00  1024 1048 1184 1344  768 771 777 806 -hsync -vsync (48.4 kHz e)
[  3453.730] (II) fglrx(0): Modeline "800x600"x0.0   49.50  800 816 896 1056  600 601 604 625 +hsync +vsync (46.9 kHz e)
[  3453.730] (II) fglrx(0): Modeline "1152x864"x0.0  108.00  1152 1216 1344 1600  864 865 868 900 +hsync +vsync (67.5 kHz e)
[  3453.731] (II) fglrx(0): Modeline "1280x1024"x0.0  108.00  1280 1328 1440 1688  1024 1025 1028 1066 +hsync +vsync (64.0 kHz e)
[  3453.731] (II) fglrx(0): Modeline "1680x1050"x0.0  119.00  1680 1728 1760 1840  1050 1053 1059 1080 +hsync -vsync (64.7 kHz e)
[  3453.739] (II) fglrx(0): xdl_xs113_atiddxDisplayScreenEnableDisplays
[  3491.300] (II) AIGLX: Suspending AIGLX clients for VT switch
[  3491.300] (II) fglrx(0): Backup framebuffer data.
[  3491.376] (II) fglrx(0): Backup complete.
[  3556.482] (II) evdev: Logitech G500: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Logitech G500: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Logitech Logitech USB Headset: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Mitsumi Electric Apple Extended USB Keyboard: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Power Button: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.482] (II) evdev: Power Button: Close
[  3556.482] (II) UnloadModule: "evdev"
[  3556.483] (II) fglrx(0): Shutdown CMMQS
[  3556.499] (II) fglrx(0): [uki] removed 1 reserved context for kernel
[  3556.499] (II) fglrx(0): [uki] unmapping 8192 bytes of SAREA 0x2000 at 0x7f133bcc9000
[  3556.504] (EE) 
[  3556.504] (EE) Backtrace:
[  3556.504] (EE) 0: /usr/bin/X (xorg_backtrace+0x36) [0x7f133be93476]
[  3556.504] (EE) 1: /usr/bin/X (0x7f133bce3000+0x1b42b9) [0x7f133be972b9]
[  3556.504] (EE) 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f133ade6000+0xfbd0) [0x7f133adf5bd0]
[  3556.504] (EE) 3: /usr/lib/x86_64-linux-gnu/libpciaccess.so.0 (0x7f133b003000+0x4c3e) [0x7f133b007c3e]
[  3556.504] (EE) 4: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (amd_xs113_int10_x_inb+0x46) [0x7f13382c3e66]
[  3556.504] (EE) 5: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7f1337ae3000+0x7d70c5) [0x7f13382ba0c5]
[  3556.505] (EE) 6: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (X86EMU_exec+0xa5) [0x7f13382ad815]
[  3556.505] (EE) 7: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (amd_xs113_int10_xf86ExecX86int10+0x46) [0x7f13382c4fc6]
[  3556.505] (EE) 8: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xf86ExecX86int10+0xd) [0x7f1337e1a49d]
[  3556.505] (EE) 9: /usr/lib/xorg/modules/libvbe.so (VBESetVBEMode+0x9d) [0x7f133663f4ed]
[  3556.505] (EE) 10: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7f1337ae3000+0x3691b3) [0x7f1337e4c1b3]
[  3556.505] (EE) 11: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (atiddxVBESetConsoleMode+0x42) [0x7f1337e4bff2]
[  3556.505] (EE) 12: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxFreeScreen+0x46a) [0x7f1337f9c4aa]
[  3556.505] (EE) 13: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (xdl_xs113_atiddxCloseScreen+0x260) [0x7f1337f9bd80]
[  3556.505] (EE) 14: /usr/lib/x86_64-linux-gnu/xorg/extra-modules/modules/drivers/fglrx_drv.so (0x7f1337ae3000+0x84c9c6) [0x7f133832f9c6]
[  3556.505] (EE) 15: /usr/bin/X (0x7f133bce3000+0xea338) [0x7f133bdcd338]
[  3556.505] (EE) 16: /usr/bin/X (0x7f133bce3000+0x135fb4) [0x7f133be18fb4]
[  3556.505] (EE) 17: /usr/bin/X (0x7f133bce3000+0x47687) [0x7f133bd2a687]
[  3556.505] (EE) 18: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xf5) [0x7f1339a33ea5]
[  3556.505] (EE) 19: /usr/bin/X (0x7f133bce3000+0x478c1) [0x7f133bd2a8c1]
[  3556.505] (EE) 
[  3556.505] (EE) Segmentation fault at address 0x0
[  3556.505] 
Fatal server error:
[  3556.505] Caught signal 11 (Segmentation fault). Server aborting
[  3556.505] 
[  3556.505] (EE) 
Please consult the The X.Org Foundation support 
     at http://wiki.x.org
 for help. 
[  3556.505] (EE) Please also check the log file at "/var/log/Xorg.0.log" for additional information.
[  3556.505] (EE) 
[  3556.508] Server terminated with error (1). Closing log file.

```

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]vaguely_clear;

Well, looking more and more like hardware failure... a couple other instances in the log file where errors were detected...but, let's try a different driver ...what does Additional Drivers have to offer ?
And while thinking along these lines.... is the on-board graphics disabled in bios ?
Also what does the system say about the hardware -> terminal code:
[/COLOR]```
lspci -nnk | grep -iA3 vga 
```
Then again, what do you think about switching graphics in software -> switcheroo
--if hardware failure, may present more problems than cures --
[https://help.ubuntu.com/community/HybridGraphics](https://help.ubuntu.com/community/HybridGraphics)[INDENT=2]
stretch'n, sometimes worth the effort [/INDENT]

---

### Post by vaguely_clear on 2013-06-09
> **Bashing-om said:**
> 
[COLOR=#000000]Well, looking more and more like hardware failure... a couple other instances in the log file where errors were detected...but, let's try a different driver ...what does Additional Drivers have to offer ?
[/COLOR]

Additional Drivers offers the regular fglrx package, fglrx-updates (installed), and the open-source driver (see attachment).

> **Bashing-om said:**
> [COLOR=#000000]
And while thinking along these lines.... is the on-board graphics disabled in bios ?
[/COLOR]

The option "Onboard VGA" in BIOS offers the following:
[LIST=1]
[*]Enable If No Ext PEG
[*]Always Enable
[*]Auto
[/LIST]
"Auto" was selected, and I left it that way.

> **Bashing-om said:**
> [COLOR=#000000]
Also what does the system say about the hardware -> terminal code:
[/COLOR]```
lspci -nnk | grep -iA3 vga 
```


That command returns the following:

```

01:00.0 VGA compatible controller [0300]: Advanced Micro Devices [AMD] nee ATI Barts PRO [Radeon HD 6850] [1002:6739]
    Subsystem: PC Partner Limited Device [174b:174b]
    Kernel driver in use: fglrx_pci
01:00.1 Audio device [0403]: Advanced Micro Devices [AMD] nee ATI Barts HDMI Audio [Radeon HD 6800 Series] [1002:aa88]

```

> **Bashing-om said:**
> 
Then again, what do you think about switching graphics in software -> switcheroo
--if hardware failure, may present more problems than cures --
[URL="https://help.ubuntu.com/community/HybridGraphics"]https://help.ubuntu.com/community/HybridGraphics
[/URL]

I don't believe my hardware (Intel i5 tower with Radeon 6850 card installed) can utilize switcheroo.

Finally, while in BIOS, I did notice another issue. Under one of the menus, I was presented with a big red box that said:

```

The system has experienced boot failures because of overclocking or changes of voltages.

Last settings in this page may not coincide with current H/W states.

```

I have no idea what that's about! I haven't touched overclocking. I did do a memtest a few days ago, which passed.

Hmmm.

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]vaguely_clear;

I am done for the eve...will check your status my next[/COLOR][INDENT][COLOR=#000000]
regards

[/COLOR][/INDENT]

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]vaguely_clear;
lemme offer this before I go --getting cloudy in my think'n ...gonna desist .. but
the bios warning .... have you done any changes to your bios ? What I have in mind is to reset the bios to default. I hope there exist an option in the menus to permit this.
Do that and see if the error in bios goes away and also the errors in the log file.
We can think about changing the graphics driver to open source... I have worked a few threads in which the open source driver performed better on their hardware than the proprietary drivers ....open source will certainly integrate into the operating system closer. 
[/COLOR][INDENT=3][COLOR=#000000]
something to think about

[/COLOR][/INDENT]

---

### Post by Bashing-om on 2013-06-11
vaguely_clear;

Just a request for updated status... I will be away from the keyboard for several hours today//I will check back in when I return.
[INDENT=2]
regards

[/INDENT]

---

### Post by vaguely_clear on 2013-06-17
> **Bashing-om said:**
> vaguely_clear;

Just a request for updated status... I will be away from the keyboard for several hours today//I will check back in when I return.[INDENT=2]
regards

[/INDENT]


Hi! I'm really sorry about the late reply.

I tried removing my graphics card and using the Intel HD 4000 built onto my processor, but to no avail. I tried a few other things that I can't exactly recall, but the system ultimately became a pretty tragic mess! I was using a Gnome Shell theme that I've heard can introduce some bugs, and I became suspicious that it may have been the culprit, but I've just gotten a bit worn out from the trouble.

I have backed up my personal data on that installation, and I'm planning to reinstall. So, the tl;dr version is: I didn't find a solution.

However, your help was extremely valuable, and I learned a lot. So thank you for all your time!

---

