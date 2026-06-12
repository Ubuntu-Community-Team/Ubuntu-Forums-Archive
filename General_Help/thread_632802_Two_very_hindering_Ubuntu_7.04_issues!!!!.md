---
title: "Two very hindering Ubuntu 7.04 issues!!!!"
date: 2007-12-05
forum: General Help
---

### Post by Good Ol' Ramos on 2007-12-05
I'm having a problem with Rhythmbox, first of all. Every time I open it up, my entire music library slowly dissapears, and I have to re-add it manually. Then, it stays fine until the second issues arises. Ubuntu will just freeze out of nowhere. The Caps Lock and Scroll Lock lights start blinking, but that's it. Any ideas? Something that might help with the Rhythmbox issue is that my media is on hdb, and, of course, Rhythmbox, along with all of Linux, is on hda. 


AMD 64 3000+ Winchester
2GB WINTEC DDR
nVidia 7600GS 256MB

---

### Post by Good Ol' Ramos on 2007-12-05
*bump* Cuz ya never know...

---

### Post by Seti on 2007-12-05
Hardware issue???

---

### Post by Good Ol' Ramos on 2007-12-05
Lol, that's my fear, but if I could get some insite as to the specific possibilities, even just a few ideas, I could get the train rolling and possibly remedy this. I just don't know where to begin right now.

---

### Post by Good Ol' Ramos on 2007-12-05
Oh, and another I forgot about... Firefox will sporadically close out.

---

### Post by Good Ol' Ramos on 2007-12-05
*confuzzled bumpage*

---

### Post by Good Ol' Ramos on 2007-12-06
*bumpalicious*

---

### Post by Good Ol' Ramos on 2007-12-08
*bumpizzle*

---

### Post by tgalati4 on 2007-12-08
Time to open your machine.  Vacuum it out.  Reset the RAM and hard disk cables.  Check that the power connections to the drives are tight as well.  I had a server machine act strange because the hardisk power connector had wiggled loose after a year of continuous operation.

If the problem happens again, post the output of:

>dmesg | tail -50

---

### Post by vanadium on 2007-12-08
The "slowly dissappearing" library is certainly related to rhythmbox not having access to the library and automatically updating its datamase (means: removing songs). It is probably a hardware issue with your second drive, and I would indeed support tgalati4's suggestions first. It might also be a "dying" hard disk, in which case you will need to replace it.

---

### Post by Good Ol' Ramos on 2007-12-08
I actually cleaned it all out and rebuilt it a few weeks ago, so it's really spotless. I've had little issues here and there... I actually keep getting BSODs on my Vista partition, which leads me to believe that it's a hardware issue. Anywho, here's the output:

[B][   37.657399] kjournald starting.  Commit interval 5 seconds
[   37.657413] EXT3-fs: recovery complete.
[   37.699201] EXT3-fs: mounted filesystem with ordered data mode.
[   72.139599] i2c_adapter i2c-0: nForce2 SMBus adapter at 0x4c00
[   72.139636] i2c_adapter i2c-1: nForce2 SMBus adapter at 0x4c40
[   72.232636] NET: Registered protocol family 17
[   72.512274] gameport: EMU10K1 is pci0000:01:08.1/gameport0, io 0xa800, speed 1205kHz
[   72.707431] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[   72.730508] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   72.751031] input: PC Speaker as /class/input/input2
[   72.860222] parport: PnPBIOS parport detected.
[   72.860267] parport0: PC-style at 0x378, irq 7 [PCSPP,TRISTATE]
[   73.208488] nvidia: module license 'NVIDIA' taints kernel.
[   73.548277] ACPI: PCI Interrupt Link [APC3] enabled at IRQ 18
[   73.548287] ACPI: PCI Interrupt 0000:05:00.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   73.548296] PCI: Setting latency timer of device 0000:05:00.0 to 64
[   73.548455] NVRM: loading NVIDIA Linux x86_64 Kernel Module  1.0-9631  Thu Nov  9 17:35:27 PST 2006
[   73.551858] input: ImPS/2 Generic Wheel Mouse as /class/input/input3
[   74.170272] ACPI: PCI Interrupt 0000:01:08.0[A] -> Link [APC3] -> GSI 18 (level, low) -> IRQ 18
[   74.172632] Installing spdif_bug patch: Audigy 2 [SB0240]
[   74.542461] fuse init (API version 7.8)
[   74.626982] lp0: using parport0 (interrupt-driven).
[   74.723787] Adding 240932k swap on /dev/disk/by-uuid/bb4504ae-8774-4a4c-b45f-91e69021a129.  Priority:-1 extents:1 across:240932k
[   74.919724] EXT3 FS on hda1, internal journal
[   83.723270] ibm_acpi: ec object not found
[   83.816183] Using specific hotkey driver
[   83.909202] input: Power Button (FF) as /class/input/input4
[   83.913562] ACPI: Power Button (FF) [PWRF]
[   83.939189] input: Power Button (CM) as /class/input/input5
[   83.943521] ACPI: Power Button (CM) [PWRB]
[   83.970785] No dock devices found.
[   84.047633] pcc_acpi: loading...
[   84.366507] powernow-k8: Found 1 AMD Athlon(tm) 64 Processor 3000+ processors (version 2.00.00)
[   84.370743] powernow-k8: BIOS error - no PSB or ACPI _PSS objects
[   89.471952] ppdev: user-space parallel port driver
[   94.198558] NET: Registered protocol family 10
[   94.198649] lo: Disabled Privacy Extensions
[   95.634025] Installing knfsd (copyright (C) 1996 [email]okir@monad.swb.de[/email]).
[   95.824888] NFSD: Using /var/lib/nfs/v4recovery as the NFSv4 state recovery directory
[   95.842784] NFSD: starting 90-second grace period
[  100.799239] Bluetooth: Core ver 2.11
[  100.799290] NET: Registered protocol family 31
[  100.799293] Bluetooth: HCI device and connection manager initialized
[  100.799296] Bluetooth: HCI socket layer initialized
[  100.871851] Bluetooth: L2CAP ver 2.8
[  100.871855] Bluetooth: L2CAP socket layer initialized
[  100.944092] Bluetooth: RFCOMM socket layer initialized
[  100.944105] Bluetooth: RFCOMM TTY layer initialized
[  100.944107] Bluetooth: RFCOMM ver 1.8
[  104.979423] eth0: no IPv6 routers present
[/B]

Thanks for gettin' back to me, folks. =)

---

### Post by Good Ol' Ramos on 2007-12-08
*bumptastic*

---

### Post by fortytwo on 2007-12-17
I've got the exact same problem actually.  Could this be an nvidia drivers issue?

---

