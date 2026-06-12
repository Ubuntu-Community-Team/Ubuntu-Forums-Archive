---
title: "aplications go black, then notebook dies!!!"
date: 2007-06-09
forum: General Help
---

### Post by pontifex3 on 2007-06-09
Hi, i have a HP dv2000 notebook with an NVIDIA GeForce Go 6150 card, i installed feisty along with beryl yesterday and everything seemed fine but today when i try to open programs (it has happened with kile, firefox and aterm so far), the border appears with a black filling, i have to close and reopen about 3 or 4 the aplication to get rid of the plain black window, after a few minutes of this, the computer suddenly freezes, nothing works except the mouse, it wont do anything with ctrl alt F1, but the power off buton still works, any help appreciated!
btw: when i restart gdm (ctrl alt backspace) everything loads fine except the mouse disappears, i know its there because when it passes over the buttons i can click them. thanks in advance!!

---

### Post by pestilence on 2007-06-09
If you load an Xsession without beryl does it work normally?
If yes try adding some debug info from:
**/var/log/Xorg.0.log**
and maybe from **dmesg** output.

---

### Post by pontifex3 on 2007-06-09
im not sure because i cant really control when it happens but it seems to be ok without beryl
here is /var/log/Xorg.0.log

```

X Window System Version 7.2.0
Release Date: 22 January 2007
X Protocol Version 11, Revision 0, Release 7.2
Build Operating System: Linux Ubuntu
Current Operating System: Linux Keroberos 2.6.20-15-generic #2 SMP Sun Apr 15 07
:36:31 UTC 2007 i686
Build Date: 04 April 2007
        Before reporting problems, check http://wiki.x.org
        to make sure that you have the latest version.
Module Loader present
Markers: (--) probed, (**) from config file, (==) default setting,
        (++) from command line, (!!) notice, (II) informational,
        (WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(==) Log file: "/var/log/Xorg.0.log", Time: Sat Jun  9 15:02:24 2007
(==) Using config file: "/etc/X11/xorg.conf"
(==) ServerLayout "Default Layout"
(**) |-->Screen "Default Screen" (0)
(**) |   |-->Monitor "Generic Monitor"
(**) |   |-->Device "Generic Video Card"
(**) |-->Input Device "Generic Keyboard"
(**) |-->Input Device "Configured Mouse"
(**) |-->Input Device "stylus"
(**) |-->Input Device "cursor"
(**) |-->Input Device "eraser"
(**) |-->Input Device "Synaptics Touchpad"
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
(II) PCI: 00:00:0: chip 10de,02f0 card 103c,30b5 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:1: chip 10de,02fa card 103c,30b5 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:2: chip 10de,02fe card 103c,30b5 rev a2 class 05,00,00 hdr 80
(II) PCI: 00:00:3: chip 10de,02f8 card 103c,30b5 rev a2 class 05,00,00 hdr 80


BLA BLA BLA.... AND THEEN!


(II) XINPUT: Adding extended input device "NVIDIA Event Handler" (type: Other)
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
Synaptics DeviceInit called
SynapticsCtrl called.
(II) Configured Mouse: ps2EnableDataReporting: succeeded
Synaptics DeviceOn called
(--) Synaptics Touchpad auto-dev sets device to /dev/input/event3
(**) Option "Device" "/dev/input/event3"
(--) Synaptics Touchpad touchpad found
Could not init font path element /usr/X11R6/lib/X11/fonts/misc, removing from li
st!
Could not init font path element /usr/share/fonts/X11/cyrillic, removing from li
st!
Could not init font path element /usr/X11R6/lib/X11/fonts/Type1, removing from l
ist!
(WW) NVIDIA(0): WAIT (2, 7, 0x8000, 0x00008bec, 0x00008c10)
(WW) NVIDIA(0): WAIT (0, 7, 0x8000, 0x00008c10, 0x00008c10)

```


and  dmesg!
BLA BLA BLA..
```
 14.872000] sdhci: SDHCI controller found at 0000:03:09.1 [1180:0822] (rev 19)
[   14.872000] ACPI: PCI Interrupt Link [LNK2] enabled at IRQ 23
[   14.872000] ACPI: PCI Interrupt 0000:03:09.1[B] -> Link [LNK2] -> GSI 23 (level, high) -> IRQ 16
[   14.872000] mmc0: SDHCI at 0xc3100800 irq 16 DMA
[   14.892000] ACPI: PCI Interrupt Link [LK3E] enabled at IRQ 21
[   14.892000] ACPI: PCI Interrupt 0000:00:05.0[A] -> Link [LK3E] -> GSI 21 (level, high) -> IRQ 21
[   14.892000] PCI: Setting latency timer of device 0000:00:05.0 to 64
[   14.892000] NVRM: loading NVIDIA Linux x86 Kernel Module  1.0-9631  Thu Nov  9 17:38:10 PST 2006
[   14.940000] hdc: ATAPI 63X DVD-ROM DVD-R-RAM CD-R/RW drive, 2048kB Cache, (U)DMA
[   14.940000] Uniform CD-ROM driver Revision: 3.20
[   14.968000] ieee80211_crypt: registered algorithm 'NULL'
[   14.968000] ieee80211: 802.11 data/management/control stack, git-1.1.13
[   14.968000] ieee80211: Copyright (C) 2004-2005 Intel Corporation <jketreno@linux.intel.com>
[   15.032000] input: PC Speaker as /class/input/input2
[   15.148000] bcm43xx driver
[   15.148000] ACPI: PCI Interrupt Link [LK2E] enabled at IRQ 19
[   15.148000] ACPI: PCI Interrupt 0000:01:00.0[A] -> Link [LK2E] -> GSI 19 (level, high) -> IRQ 22
[   15.148000] PCI: Setting latency timer of device 0000:01:00.0 to 64
[   15.200000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   15.224000] Linux video capture interface: v2.00
[   15.252000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   15.260000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   15.344000] uvcvideo: Found UVC 1.00 device USB 2.0 Camera (0c45:62c0)
[   15.348000] usbcore: registered new interface driver uvcvideo
[   15.348000] USB Video Class driver (v0.1.0)
[   15.432000] ACPI: PCI Interrupt Link [LAZA] enabled at IRQ 22
[   15.432000] ACPI: PCI Interrupt 0000:00:10.1[B] -> Link [LAZA] -> GSI 22 (level, high) -> IRQ 17
[   15.432000] PCI: Setting latency timer of device 0000:00:10.1 to 64
[   15.480000] Synaptics Touchpad, model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x200000
[   15.512000] input: SynPS/2 Synaptics TouchPad as /class/input/input3
[   15.792000] fuse init (API version 7.8)
[   15.892000] lp: driver loaded but no devices found
[   15.960000] Adding 3903784k swap on /dev/disk/by-uuid/561156ec-69f8-46f9-9710-ecefcf9a09fa.  Priority:-1 extents:1 across:3903784k
[   16.072000] EXT3 FS on sda1, internal journal
[   16.188000] NET: Registered protocol family 10
[   16.188000] lo: Disabled Privacy Extensions
[   16.348000] kjournald starting.  Commit interval 5 seconds
[   16.348000] EXT3 FS on sda3, internal journal
[   16.348000] EXT3-fs: mounted filesystem with ordered data mode.
[   20.648000] input: Power Button (FF) as /class/input/input4
[   20.648000] ACPI: Power Button (FF) [PWRF]
[   20.652000] input: Lid Switch as /class/input/input5
[   20.652000] ACPI: Lid Switch [LID0]
[   20.680000] input: Sleep Button (CM) as /class/input/input6
[   20.680000] ACPI: Sleep Button (CM) [SLPB]
[   20.696000] input: Power Button (CM) as /class/input/input7
[   20.696000] ACPI: Power Button (CM) [PWRB]
[   20.756000] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   20.776000] No dock devices found.
[   20.952000] ACPI: Battery Slot [BAT0] (battery present)
[   20.968000] ACPI: AC Adapter [ADP1] (off-line)
[   20.988000] Using specific hotkey driver
[   21.076000] ibm_acpi: ec object not found
[   21.116000] pcc_acpi: loading...
[   21.136000] wmi_add device=df884800
[   21.136000] calling WQBA
[   21.404000] powernow-k8: Found 2 AMD Turion(tm) 64 X2  processors (version 2.00.00)
[   21.404000] powernow-k8:    0 : fid 0x8 (1600 MHz), vid 0x13
[   21.404000] powernow-k8:    1 : fid 0x0 (800 MHz), vid 0x1e
[   26.460000] eth0: no IPv6 routers present
[   30.696000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 0 at 0:05.0] forgot to specify physical device; fix it!
[   30.696000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 1 at 0:05.0] forgot to specify physical device; fix it!
[   30.696000] **WARNING** I2C adapter driver [NVIDIA i2c adapter 2 at 0:05.0] forgot to specify physical device; fix it!
[   30.768000] ppdev: user-space parallel port driver
[   32.760000] apm: BIOS not found.
[   48.260000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[   95.788000] NVRM: Xid (0000:05): 6, PE0002 0184 beef0201 00000054 0a426b20 05000320
[   95.788000] NVRM: Xid (0000:05): 29,  L1 -> L0
[  492.276000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[  970.272000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1411.288000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 1867.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2225.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2578.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 2777.276000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3053.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3434.280000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.
[ 3718.296000] bcm43xx: Error: Microcode "bcm43xx_microcode5.fw" not available or load failed.

```

---

### Post by ChrisNiemy on 2007-09-07
Mhm, that looks very similiar to what I experiences from time to time. If found this specific thread by searching Google for the error message "calling WQBA".

Please also check this thread. I think there's a connection:
[PCI BIOS BUG # 81](http://ubuntuforums.org/showthread.php?t=332829)

I also get these errors, see especially page 2 in the linked thread. No solution so far. A workaround is definetly to disable ACPI. kernel boot options (for GRUB) ```
noapic nolapic
``` For a desktop or a laptop at home this is ok, though cpu scaling is also a nice thing at home. However with this options, powermanagement etc won't work.

Therefore you can try:
```
pnpbios=off irqpoll mem=nopentium pci=biosirq
```
Then ACPI still works, but input devices seem to be a bit buggy. However, hope you can find some help in the linked thread.

PS: My system goes unstable espescially when my broadcom wireless card IS working.

---

### Post by ChrisNiemy on 2007-09-12
in the thread linked in my previous post, we have found some more boot options, like **noirqdebug**, Seems to be a quite satisfying workaround so far. However problems remains from time to time.

---

### Post by ChrisNiemy on 2007-12-22
I had to change my notebook because of a graphic card failure.

Now (the same model) it does not completely go black but sometimes showing a weird snow in the framebuffer when switching to VTs and back to desktop. Looks very strange. Though I'm lucky that happens not that often.

PS: Perhaps try pci=nommconf at boot options

---

