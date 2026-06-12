---
title: "Hung Synaptic blocking the whole system"
date: 2007-04-23
forum: General Help
---

### Post by Thematrian on 2007-04-23
This weekend, I installed Edgy Eft and upgraded to whichever minor version is most recent (I can't check, for reasons I'll explain anon).  I installed a few basic necessities: Emacs, SBCL, XMMS, and the 'Highly Experimental' plugin for XMPlay (despite the name, all it does it let XMMS play .psf files).  XMMS wedged itself when run on a test .psf file: it will minimize and maximize fine, but it doesn't respond to 'Close'.  Well, fair enough, I tried playing a midi instead, but this opened Synaptic (to hunt for a midi player, I guess), and it hung too: it's been in the 'Loading System Tools' phase of 'Searching for Appropriate Applications' for the last 45 minutes, just sitting in the toolbar and flashing malevolently.

Normally I'd just shrug and reboot, but some aspect of this tangle is preventing me from running any programs through the top menu bar.  I can select (for example) Applications > Accessories > Terminal, and when I do "[Starting Terminal]" appears in my task bar, but...that's it.  A few seconds later, "[Starting Terminal]" goes away again, and I don't get my terminal window.  Applications, Places, System, none of them work, and neither does quit!  This means that if I want to reboot, I must do so the hard way, which I don't want to do because something is trying to talk to my detached USB hard drive.  I can feel the disk spinning, and I can't eject it from the desktop.  This isn't a disaster, as I can open the drive by double-clicking on it and move all the really important stuff onto my local disk, but I'd just as soon not trash it with a hard reboot if I can avoid it.  Emacs doesn't run either, even when I right-click on a desktop text document and tell it to open with Emacs.  ALT-F2 seems to work, bringing up the Run Application window, but nothing actually runs.

So, to summarize:
I can run Firefox, and Nautilus (the file browser), but no other applications that I've tried.  XMMS and Synaptic are both hanging, unresponsive to the close command and to pkill via ALT-F2.  The quit button does not work, but the window manager seems generally fine (except that the trash can won't open, for some reason).

Does anyone know how this might have happened, or how I might fix it?  If my current situation is unsalvageable, I'd settle for knowing how to kill Synaptic the *next* time it runs out of control.

---

### Post by amohanty on 2007-04-24
Can you post the output of 

dmesg | tail -n 100

AM

---

### Post by Thematrian on 2007-04-24
Thanks for the thought, but I don't think I can.  I can't get at the shell at all: no Terminal, no ALT-F2, no Emacs even.  Are there any avenues I've overlooked?

---

### Post by zvacet on 2007-04-24
**ctrl+alt+F1**

---

### Post by Thematrian on 2007-04-24
Googling on Ctrl-Alt-F1 suggests that it's supposed to bring up a shell of some kind, but it actually hosed the display completely, into some kind neo-Cubist mosaic thing.  Alt-F7 or possibly Alt-F8 brought my screen back (though the program runner was still fuxxored).  However, that same Google search informed me of Ctrl-Alt-Backspace, which restarts Gnome without bringing down the whole OS.  I backed up as much as I had space for and tried it.  Success!  I can run stuff now, and I got to keep all my data.  Thank you all.

dmesg output follows.  I went with the last 200 lines, since Ctrl-Alt-Backspace apparently disconnected and reconnected all my devices.

[17179586.332000] kjournald starting.  Commit interval 5 seconds
[17179586.332000] EXT3-fs: sda5: orphan cleanup on readonly fs
[17179586.332000] ext3_orphan_cleanup: deleting unreferenced inode 1723401
[17179586.348000] ext3_orphan_cleanup: deleting unreferenced inode 1720342
[17179586.368000] EXT3-fs: sda5: 2 orphan inodes deleted
[17179586.368000] EXT3-fs: recovery complete.
[17179586.420000] EXT3-fs: mounted filesystem with ordered data mode.
[17179591.220000] usb-storage: device scan complete
[17179591.220000]   Vendor: SAMSUNG   Model: HD501LJ           Rev: CR10
[17179591.220000]   Type:   Direct-Access                      ANSI SCSI revision: 04
[17179591.224000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[17179591.224000] sdb: Write Protect is off
[17179591.224000] sdb: Mode Sense: 11 00 00 00
[17179591.224000] sdb: assuming drive cache: write through
[17179591.228000] SCSI device sdb: 976773168 512-byte hdwr sectors (500108 MB)
[17179591.228000] sdb: Write Protect is off
[17179591.228000] sdb: Mode Sense: 11 00 00 00
[17179591.228000] sdb: assuming drive cache: write through
[17179591.228000]  sdb: sdb1
[17179591.248000] sd 4:0:0:0: Attached scsi disk sdb
[17179593.644000] input: PC Speaker as /class/input/input3
[17179593.704000] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[17179593.704000] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[17179593.944000] hw_random hardware driver 1.0.0 loaded
[17179594.052000] Linux agpgart interface v0.101 (c) Dave Jones
[17179594.376000] Intel(R) PRO/1000 Network Driver - version 7.1.9-k4
[17179594.376000] Copyright (c) 1999-2006 Intel Corporation.
[17179594.376000] ACPI: PCI Interrupt 0000:04:00.0[A] -> GSI 17 (level, low) -> IRQ 177
[17179594.376000] PCI: Setting latency timer of device 0000:04:00.0 to 64
[17179594.432000] e1000: 0000:04:00.0: e1000_probe: (PCI Express:2.5Gb/s:Width x1) 00:13:72:21:1a:66
[17179594.436000] agpgart: Detected an Intel 945G Chipset.
[17179594.452000] agpgart: AGP aperture is 256M @ 0x0
[17179594.496000] e1000: eth0: e1000_probe: Intel(R) PRO/1000 Network Connection
[17179594.584000] sd 0:0:0:0: Attached scsi generic sg0 type 0
[17179594.584000] sd 4:0:0:0: Attached scsi generic sg1 type 0
[17179594.820000] ts: Compaq touchscreen protocol output
[17179595.252000] ACPI: PCI Interrupt 0000:00:1b.0[A] -> GSI 16 (level, low) -> IRQ 169
[17179595.252000] PCI: Setting latency timer of device 0000:00:1b.0 to 64
[17179595.992000] lp: driver loaded but no devices found
[17179596.004000] NET: Registered protocol family 17
[17179596.020000] Adding 2048248k swap on /dev/disk/by-uuid/4d9489c9-edd3-4261-9457-7e20c7c3928a.  Priority:-1 extents:1 across:2048248k
[17179596.236000] e1000: eth0: e1000_watchdog: NIC Link is Up 100 Mbps Full Duplex
[17179596.236000] e1000: eth0: e1000_watchdog: 10/100 speed: disabling TSO
[17179596.240000] EXT3 FS on sda5, internal journal
[17179597.004000] NTFS driver 2.1.27 [Flags: R/O MODULE].
[17179597.068000] NTFS volume version 3.1.
[17179597.412000] NET: Registered protocol family 10
[17179597.412000] lo: Disabled Privacy Extensions
[17179597.416000] IPv6 over IPv4 tunneling driver
[17179602.456000] ACPI: Power Button (FF) [PWRF]
[17179602.456000] ACPI: Power Button (CM) [VBTN]
[17179602.572000] ibm_acpi: ec object not found
[17179602.616000] pcc_acpi: loading...
[17179604.560000] apm: BIOS version 1.2 Flags 0x03 (Driver version 1.16ac)
[17179604.560000] apm: disabled - APM is not SMP safe.
[17179607.568000] eth0: no IPv6 routers present
[17179607.920000] Bluetooth: Core ver 2.8
[17179607.920000] NET: Registered protocol family 31
[17179607.920000] Bluetooth: HCI device and connection manager initialized
[17179607.920000] Bluetooth: HCI socket layer initialized
[17179607.956000] Bluetooth: L2CAP ver 2.8
[17179607.956000] Bluetooth: L2CAP socket layer initialized
[17179607.956000] Bluetooth: RFCOMM socket layer initialized
[17179607.956000] Bluetooth: RFCOMM TTY layer initialized
[17179607.956000] Bluetooth: RFCOMM ver 1.7
[17179702.752000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17257405.784000] usb 4-1: USB disconnect, address 2
[17257414.464000] usb 5-7: new high speed USB device using ehci_hcd and address 6
[17257414.596000] usb 5-7: configuration #1 chosen from 1 choice
[17257414.596000] scsi5 : SCSI emulation for USB Mass Storage devices
[17257414.596000] usb-storage: device found at 6
[17257414.596000] usb-storage: waiting for device to settle before scanning
[17257419.596000] usb-storage: device scan complete
[17257419.600000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.15
[17257419.600000]   Type:   Direct-Access                      ANSI SCSI revision: 02
[17257419.600000]   Vendor: SanDisk   Model: U3 Cruzer Micro   Rev: 2.15
[17257419.600000]   Type:   CD-ROM                             ANSI SCSI revision: 02
[17257419.604000] SCSI device sdc: 1994385 512-byte hdwr sectors (1021 MB)
[17257419.608000] sdc: Write Protect is off
[17257419.608000] sdc: Mode Sense: 03 00 00 00
[17257419.608000] sdc: assuming drive cache: write through
[17257419.620000] SCSI device sdc: 1994385 512-byte hdwr sectors (1021 MB)
[17257419.624000] sdc: Write Protect is off
[17257419.624000] sdc: Mode Sense: 03 00 00 00
[17257419.624000] sdc: assuming drive cache: write through
[17257419.624000]  sdc: sdc1
[17257419.628000] sd 5:0:0:0: Attached scsi removable disk sdc
[17257419.628000] sd 5:0:0:0: Attached scsi generic sg2 type 0
[17257419.628000]  5:0:0:1: Attached scsi generic sg3 type 5
[17257419.696000] sr0: scsi3-mmc drive: 8x/40x writer xa/form2 cdda tray
[17257419.696000] sr 5:0:0:1: Attached scsi CD-ROM sr0
[17257419.892000] cdrom: This disc doesn't have any tracks I recognize!
[17257419.896000] FAT: utf8 is not a recommended IO charset for FAT filesystems, filesystem will be case sensitive!
[17305269.624000] usb 2-2: reset low speed USB device using uhci_hcd and address 2
[17305350.288000] usb 5-7: USB disconnect, address 6
[17340237.384000] usb 2-2: USB disconnect, address 2
[17340573.224000] usb 2-2: new low speed USB device using uhci_hcd and address 3
[17340573.396000] usb 2-2: configuration #1 chosen from 1 choice
[17340573.416000] input: USB Optical Mouse as /class/input/input4
[17340573.416000] input: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.1-2

---

### Post by amohanty on 2007-04-25
That looks fine. What surprises me more is tha synaptic popped up when you tried to play a midi file. Oh well if it ever crops up again, dmesg and the contents of /var/log/Xorg.0.log are your best friends.

AM

---

