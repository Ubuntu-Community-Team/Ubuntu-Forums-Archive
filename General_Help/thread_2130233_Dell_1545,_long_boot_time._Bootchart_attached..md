---
title: "Dell 1545, long boot time. Bootchart attached."
date: 2013-03-28
forum: General Help
---

### Post by JohnBUK on 2013-03-28
I have a four year old Dell 1545 laptop running Ubuntu 12:10 Unity. It is a Pentium Dual Core T4200 2GHz with 3Gb RAM.

In the last few months the boot up time has been getting worse and worse and the last boot time was 3m 39secs! It takes 1m 49s to P/W request and then the remainder to being available for input.

If someone wouldn't mind viewing the Bootchart and providing some advice on how to reduce this somewhat I would be very grateful. Thank you

---

### Post by hectorgrebbell on 2013-03-28
That image appears to be illegibly small. If your using a separate home partition i'd suggest a fresh install (Not a great solution I realise).

My knowledge of the boot system isn't great but if you can get a legible copy of that up I can take a look.
picturepush.com/upa lets you up an image without login if this is reducing the size.

---

### Post by oldfred on 2013-03-28
I have never understood boot chart, but suggest looking at log files to see if you can find the error.

I use Log File Viewer (not sure if default on not) and first look at dmesg for anything with outright errors, long times between tasks or repeated tries and either failure or it works but took too long.

       [https://help.ubuntu.com/community/LinuxLogFiles](https://help.ubuntu.com/community/LinuxLogFiles)

---

### Post by tgalati4 on 2013-03-28
What is the SMART status of the drive?  If it is failing, then it may take a long time to boot.

```
smartctl -a /dev/sda
```

I can't read the chart, but it looks like your boot is IO bound during the entire boot time.  How full is the disk?

---

### Post by JohnBUK on 2013-03-29
Apologies for delay in coming back and many thanks to those who have replied.

I have uploaded the Bootchart file to my Public Dropbox - [http://dl.dropbox.com/u/141284/john-Inspiron-1545-quantal-20130328-1.png](http://dl.dropbox.com/u/141284/john-Inspiron-1545-quantal-20130328-1.png)

My HDD shows some 82Gb unused (I'm not a big user of music or videos)

I've installed the SMART software and run it - sorry, this may sound pathetic but how do I copy the readout showing in my Terminal?

I will have a look at LogFile Viewer and get back with data shortly.

Once again many thanks for helping.

---

### Post by JohnBUK on 2013-03-29
OK, ran "dmesg" and this is what transpired. I've read through it and there are failures but I've no idea what they are.

```
[    0.592366] tun: Universal TUN/TAP device driver, 1.6
[    0.592368] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.592411] PPP generic driver version 2.4.2
[    0.592457] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.592504] ehci_hcd 0000:00:1a.7: setting latency timer to 64
[    0.592509] ehci_hcd 0000:00:1a.7: EHCI Host Controller
[    0.592515] ehci_hcd 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.592549] ehci_hcd 0000:00:1a.7: debug port 1
[    0.596449] ehci_hcd 0000:00:1a.7: cache line size of 64 is not supported
[    0.596470] ehci_hcd 0000:00:1a.7: irq 22, io mem 0xfed1c400
[    0.608020] ehci_hcd 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.608062] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.608065] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.608068] usb usb1: Product: EHCI Host Controller
[    0.608071] usb usb1: Manufacturer: Linux 3.5.0-26-generic ehci_hcd
[    0.608074] usb usb1: SerialNumber: 0000:00:1a.7
[    0.608205] hub 1-0:1.0: USB hub found
[    0.608210] hub 1-0:1.0: 6 ports detected
[    0.608310] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[    0.608314] ehci_hcd 0000:00:1d.7: EHCI Host Controller
[    0.608320] ehci_hcd 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.608346] ehci_hcd 0000:00:1d.7: debug port 1
[    0.612227] ehci_hcd 0000:00:1d.7: cache line size of 64 is not supported
[    0.612244] ehci_hcd 0000:00:1d.7: irq 20, io mem 0xfed1c000
[    0.624020] ehci_hcd 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.624036] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.624039] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.624042] usb usb2: Product: EHCI Host Controller
[    0.624045] usb usb2: Manufacturer: Linux 3.5.0-26-generic ehci_hcd
[    0.624047] usb usb2: SerialNumber: 0000:00:1d.7
[    0.624165] hub 2-0:1.0: USB hub found
[    0.624169] hub 2-0:1.0: 6 ports detected
[    0.624254] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.624277] uhci_hcd: USB Universal Host Controller Interface driver
[    0.624305] uhci_hcd 0000:00:1a.0: setting latency timer to 64
[    0.624309] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.624315] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.624345] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00006f60
[    0.624380] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.624383] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.624386] usb usb3: Product: UHCI Host Controller
[    0.624388] usb usb3: Manufacturer: Linux 3.5.0-26-generic uhci_hcd
[    0.624391] usb usb3: SerialNumber: 0000:00:1a.0
[    0.624506] hub 3-0:1.0: USB hub found
[    0.624511] hub 3-0:1.0: 2 ports detected
[    0.624596] uhci_hcd 0000:00:1a.1: setting latency timer to 64
[    0.624600] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.624605] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.624646] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00006f80
[    0.624679] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.624682] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.624685] usb usb4: Product: UHCI Host Controller
[    0.624687] usb usb4: Manufacturer: Linux 3.5.0-26-generic uhci_hcd
[    0.624690] usb usb4: SerialNumber: 0000:00:1a.1
[    0.624807] hub 4-0:1.0: USB hub found
[    0.624811] hub 4-0:1.0: 2 ports detected
[    0.624891] uhci_hcd 0000:00:1a.2: setting latency timer to 64
[    0.624895] uhci_hcd 0000:00:1a.2: UHCI Host Controller
[    0.624900] uhci_hcd 0000:00:1a.2: new USB bus registered, assigned bus number 5
[    0.624928] uhci_hcd 0000:00:1a.2: irq 22, io base 0x00006fa0
[    0.624962] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.624965] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.624968] usb usb5: Product: UHCI Host Controller
[    0.624970] usb usb5: Manufacturer: Linux 3.5.0-26-generic uhci_hcd
[    0.624973] usb usb5: SerialNumber: 0000:00:1a.2
[    0.625084] hub 5-0:1.0: USB hub found
[    0.625088] hub 5-0:1.0: 2 ports detected
[    0.625167] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[    0.625171] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.625177] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 6
[    0.625207] uhci_hcd 0000:00:1d.0: irq 20, io base 0x00006f00
[    0.625241] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.625244] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.625247] usb usb6: Product: UHCI Host Controller
[    0.625249] usb usb6: Manufacturer: Linux 3.5.0-26-generic uhci_hcd
[    0.625252] usb usb6: SerialNumber: 0000:00:1d.0
[    0.625362] hub 6-0:1.0: USB hub found
[    0.625366] hub 6-0:1.0: 2 ports detected
[    0.625449] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.625453] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.625459] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 7
[    0.625488] uhci_hcd 0000:00:1d.1: irq 21, io base 0x00006f20
[    0.625523] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.625526] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.625529] usb usb7: Product: UHCI Host Controller
[    0.625532] usb usb7: Manufacturer: Linux 3.5.0-26-generic uhci_hcd
[    0.625534] usb usb7: SerialNumber: 0000:00:1d.1
[    0.625650] hub 7-0:1.0: USB hub found
[    0.625654] hub 7-0:1.0: 2 ports detected
[    0.625735] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.625739] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.625745] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 8
[    0.625774] uhci_hcd 0000:00:1d.2: irq 22, io base 0x00006f40
[    0.625809] usb usb8: New USB device found, idVendor=1d6b, idProduct=0001
[    0.625812] usb usb8: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.625815] usb usb8: Product: UHCI Host Controller
[    0.625818] usb usb8: Manufacturer: Linux 3.5.0-26-generic uhci_hcd
[    0.625820] usb usb8: SerialNumber: 0000:00:1d.2
[    0.625931] hub 8-0:1.0: USB hub found
[    0.625935] hub 8-0:1.0: 2 ports detected
[    0.626074] usbcore: registered new interface driver libusual
[    0.626131] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.645547] i8042: Detected active multiplexing controller, rev 1.1
[    0.659003] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.659011] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[    0.659040] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[    0.659065] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[    0.659092] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[    0.659205] mousedev: PS/2 mouse device common for all mice
[    0.659824] rtc_cmos 00:04: RTC can wake from S4
[    0.659976] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    0.660022] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.660084] device-mapper: uevent: version 1.0.3
[    0.660156] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.660191] EISA: Probing bus 0 at eisa.0
[    0.660193] EISA: Cannot allocate resource for mainboard
[    0.660195] Cannot allocate resource for EISA slot 1
[    0.660197] Cannot allocate resource for EISA slot 2
[    0.660199] Cannot allocate resource for EISA slot 3
[    0.660201] Cannot allocate resource for EISA slot 4
[    0.660203] Cannot allocate resource for EISA slot 5
[    0.660204] Cannot allocate resource for EISA slot 6
[    0.660206] Cannot allocate resource for EISA slot 7
[    0.660208] Cannot allocate resource for EISA slot 8
[    0.660210] EISA: Detected 0 cards.
[    0.660252] cpuidle: using governor ladder
[    0.660298] cpuidle: using governor menu
[    0.660300] EFI Variables Facility v0.08 2004-May-17
[    0.660489] ashmem: initialized
[    0.660635] TCP: cubic registered
[    0.660751] NET: Registered protocol family 10
[    0.660963] NET: Registered protocol family 17
[    0.660976] Key type dns_resolver registered
[    0.661058] Using IPI No-Shortcut mode
[    0.661151] PM: Hibernation image not present or could not be loaded.
[    0.661166] registered taskstats version 1
[    0.663811] Key type trusted registered
[    0.666137] Key type encrypted registered
[    0.669159]   Magic number: 5:854:947
[    0.669166] misc binder: hash matches
[    0.669198] tty tty4: hash matches
[    0.669270] rtc_cmos 00:04: setting system clock to 2013-03-29 17:54:01 UTC (1364579641)
[    0.670794] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.670796] EDD information not available.
[    0.686613] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.925156] isapnp: No Plug & Play device found
[    0.947368] Freeing unused kernel memory: 756k freed
[    0.947411] usb 1-5: new high-speed USB device number 2 using ehci_hcd
[    0.947705] Write protecting the kernel text: 5956k
[    0.947734] Write protecting the kernel read-only data: 2412k
[    0.947736] NX-protecting the kernel data: 4284k
[    0.983436] udevd[105]: starting version 175
[    1.071565] sky2: driver version 1.30
[    1.071649] sky2 0000:09:00.0: Yukon-2 FE+ chip revision 0
[    1.071767] sky2 0000:09:00.0: irq 44 for MSI/MSI-X
[    1.080551] sky2 0000:09:00.0: eth0: addr 00:23:ae:1b:73:15
[    1.091028] usb 1-5: New USB device found, idVendor=0bda, idProduct=0158
[    1.091033] usb 1-5: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.091037] usb 1-5: Product: USB2.0-CRW
[    1.091040] usb 1-5: Manufacturer: Generic
[    1.091042] usb 1-5: SerialNumber: 20071114173400000
[    1.103430] Initializing USB Mass Storage driver...
[    1.103501] usbcore: registered new interface driver usb-storage
[    1.103503] USB Mass Storage support registered.
[    1.115092] ahci 0000:00:1f.2: version 3.0
[    1.115170] ahci 0000:00:1f.2: irq 45 for MSI/MSI-X
[    1.115228] ahci: SSS flag set, parallel bus scan disabled
[    1.115269] ahci 0000:00:1f.2: AHCI 0001.0200 32 slots 4 ports 3 Gbps 0x33 impl SATA mode
[    1.115273] ahci 0000:00:1f.2: flags: 64bit ncq sntf stag pm led clo pio slum part ccc ems 
[    1.115279] ahci 0000:00:1f.2: setting latency timer to 64
[    1.139377] scsi0 : ahci
[    1.139548] scsi1 : ahci
[    1.139684] scsi2 : ahci
[    1.139808] scsi3 : ahci
[    1.139927] scsi4 : ahci
[    1.140080] scsi5 : ahci
[    1.140353] ata1: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c900 irq 45
[    1.140357] ata2: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1c980 irq 45
[    1.140359] ata3: DUMMY
[    1.140361] ata4: DUMMY
[    1.140365] ata5: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb00 irq 45
[    1.140368] ata6: SATA max UDMA/133 abar m2048@0xfed1c800 port 0xfed1cb80 irq 45
[    1.143584] scsi6 : usb-storage 1-5:1.0
[    1.143681] usbcore: registered new interface driver ums-realtek
[    1.460082] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.461636] ata1.00: ATA-8: ST9160310AS, DE05, max UDMA/133
[    1.461639] ata1.00: 312581808 sectors, multi 8: LBA48 NCQ (depth 31/32), AA
[    1.463309] ata1.00: configured for UDMA/133
[    1.463483] scsi 0:0:0:0: Direct-Access     ATA      ST9160310AS      DE05 PQ: 0 ANSI: 5
[    1.463682] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.463731] sd 0:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.463783] sd 0:0:0:0: [sda] Write Protect is off
[    1.463786] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.463838] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.780066] ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.780105]  sda: sda1 sda2 < sda5 >
[    1.780574] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.781257] ata2.00: ATAPI: HL-DT-ST DVD+/-RW GT10N, A103, max UDMA/100
[    1.784489] ata2.00: configured for UDMA/100
[    1.789883] scsi 1:0:0:0: CD-ROM            HL-DT-ST DVD+-RW GT10N    A103 PQ: 0 ANSI: 5
[    1.793568] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.793571] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.793699] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.793790] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    2.112077] ata5: SATA link down (SStatus 0 SControl 300)
[    2.142436] scsi 6:0:0:0: Direct-Access     Generic- Multi-Card       1.00 PQ: 0 ANSI: 0 CCS
[    2.143303] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.147048] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[    2.432054] ata6: SATA link down (SStatus 0 SControl 300)
[    4.166892] EXT4-fs (sda1): INFO: recovery required on readonly filesystem
[    4.166897] EXT4-fs (sda1): write access will be enabled during recovery
[   10.790894] EXT4-fs (sda1): recovery complete
[   10.806827] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   35.554616] Adding 3103740k swap on /dev/sda5.  Priority:-1 extents:1 across:3103740k 
[   35.891874] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.006450] udevd[368]: starting version 175
[   38.011740] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   40.424932] type=1400 audit(1364579681.254:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=731 comm="apparmor_parser"
[   40.424945] type=1400 audit(1364579681.254:3): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=732 comm="apparmor_parser"
[   40.425421] type=1400 audit(1364579681.254:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=731 comm="apparmor_parser"
[   40.425434] type=1400 audit(1364579681.254:5): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=732 comm="apparmor_parser"
[   40.425690] type=1400 audit(1364579681.254:6): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=731 comm="apparmor_parser"
[   40.425707] type=1400 audit(1364579681.254:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=732 comm="apparmor_parser"
[   40.874452] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   40.934739] wmi: Mapper loaded
[   40.936998] lib80211: common routines for IEEE802.11 drivers
[   40.937003] lib80211_crypt: registered algorithm 'NULL'
[   41.060880] ACPI Warning: 0x00001060-0x0000107f SystemIO conflicts with Region \_SB_.PCI0.VID_.TCOI 1 (20120320/utaddress-251)
[   41.060889] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   41.060891] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   41.137134] input: Dell WMI hotkeys as /devices/virtual/input/input4
[   41.165601] [drm] Initialized drm 1.1.0 20060810
[   41.172194] gpio_ich: GPIO from 195 to 255 on gpio_ich
[   41.300749] wl: module license 'MIXED/Proprietary' taints kernel.
[   41.300753] Disabling lock debugging due to kernel taint
[   41.508552] microcode: CPU0 sig=0x1067a, pf=0x80, revision=0xa07
[   41.581403] lib80211_crypt: registered algorithm 'TKIP'
[   41.891348] eth1: Broadcom BCM4315 802.11 Hybrid Wireless Controller 5.100.82.112
[   41.986254] input: PS/2 Mouse as /devices/platform/i8042/serio2/input/input5
[   42.015383] input: AlpsPS/2 ALPS GlidePoint as /devices/platform/i8042/serio2/input/input6
[   42.179192] i915 0000:00:02.0: setting latency timer to 64
[   42.179864] i915 0000:00:02.0: irq 46 for MSI/MSI-X
[   42.179876] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   42.179878] [drm] Driver supports precise vblank timestamp query.
[   42.179922] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   42.218836] microcode: CPU1 sig=0x1067a, pf=0x80, revision=0xa07
[   42.221363] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   42.332209] i915: fixme: max PWM is zero
[   42.777727] fbcon: inteldrmfb (fb0) is primary device
[   42.777867] Console: switching to colour frame buffer device 170x48
[   42.777905] fb0: inteldrmfb frame buffer device
[   42.777907] drm: registered panic notifier
[   42.791921] acpi device:3b: registered as cooling_device2
[   42.792420] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   42.793573] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input7
[   42.793766] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[   42.793869] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   42.794049] snd_hda_intel 0000:00:1b.0: irq 47 for MSI/MSI-X
[   42.823268] init: failsafe main process (767) killed by TERM signal
[   42.977477] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   42.977650] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   44.824803] lp: driver loaded but no devices found
[   44.850292] ppdev: user-space parallel port driver
[   45.312683] Bluetooth: Core ver 2.16
[   45.312711] NET: Registered protocol family 31
[   45.312713] Bluetooth: HCI device and connection manager initialized
[   45.312715] Bluetooth: HCI socket layer initialized
[   45.312717] Bluetooth: L2CAP socket layer initialized
[   45.312722] Bluetooth: SCO socket layer initialized
[   45.681207] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   45.681212] Bluetooth: BNEP filters: protocol multicast
[   45.682321] Bluetooth: RFCOMM TTY layer initialized
[   45.682327] Bluetooth: RFCOMM socket layer initialized
[   45.682329] Bluetooth: RFCOMM ver 1.11
[   45.790641] type=1400 audit(1364579686.618:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=1009 comm="apparmor_parser"
[   45.791220] type=1400 audit(1364579686.618:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=1009 comm="apparmor_parser"
[   46.309103] type=1400 audit(1364579687.138:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1052 comm="apparmor_parser"
[   46.309537] type=1400 audit(1364579687.138:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1052 comm="apparmor_parser"
[   46.405385] type=1400 audit(1364579687.234:12): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=1056 comm="apparmor_parser"
[   46.405793] type=1400 audit(1364579687.234:13): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper//chromium_browser" pid=1056 comm="apparmor_parser"
[   46.406736] type=1400 audit(1364579687.234:14): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1053 comm="apparmor_parser"
[   46.407147] type=1400 audit(1364579687.234:15): apparmor="STATUS" operation="profile_load" name="/usr/lib/i386-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1053 comm="apparmor_parser"
[   46.409547] type=1400 audit(1364579687.238:16): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1058 comm="apparmor_parser"
[   46.410040] type=1400 audit(1364579687.238:17): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1058 comm="apparmor_parser"
[   49.259508] sky2 0000:09:00.0: eth0: enabling interface
[   49.259771] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   49.260479] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   52.260813] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[   52.262924] sd 6:0:0:0: [sdb] Asking for cache data failed
[   52.262929] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[   57.102757] vboxdrv: Found 2 processor cores.
[   57.102890] vboxdrv: fAsync=0 offMin=0x1d6 offMax=0x730
[   57.102964] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   57.102966] vboxdrv: Successfully loaded version 4.1.18_Ubuntu (interface 0x00190000).
[   57.401912] vboxpci: IOMMU not found (not registered)
[   61.505724] init: anacron main process (1218) killed by TERM signal
[   63.274763] init: plymouth-stop pre-start process (2079) terminated with status 1
[  103.956556] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  103.958815] sd 6:0:0:0: [sdb] Asking for cache data failed
[  103.958820] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  155.672585] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  155.674703] sd 6:0:0:0: [sdb] Asking for cache data failed
[  155.674708] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  207.384738] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  207.386854] sd 6:0:0:0: [sdb] Asking for cache data failed
[  207.386862] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  259.097103] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  259.099240] sd 6:0:0:0: [sdb] Asking for cache data failed
[  259.099246] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  310.808881] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  310.810996] sd 6:0:0:0: [sdb] Asking for cache data failed
[  310.811003] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  362.520771] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  362.522886] sd 6:0:0:0: [sdb] Asking for cache data failed
[  362.522893] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  414.228759] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  414.230871] sd 6:0:0:0: [sdb] Asking for cache data failed
[  414.230875] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  464.920761] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  464.922876] sd 6:0:0:0: [sdb] Asking for cache data failed
[  464.922880] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  516.628787] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  516.630892] sd 6:0:0:0: [sdb] Asking for cache data failed
[  516.630897] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  568.344681] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  568.346801] sd 6:0:0:0: [sdb] Asking for cache data failed
[  568.346808] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  620.056694] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  620.058948] sd 6:0:0:0: [sdb] Asking for cache data failed
[  620.058954] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  671.768950] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  671.771067] sd 6:0:0:0: [sdb] Asking for cache data failed
[  671.771074] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  723.480837] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  723.482957] sd 6:0:0:0: [sdb] Asking for cache data failed
[  723.482965] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  775.188850] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  775.190966] sd 6:0:0:0: [sdb] Asking for cache data failed
[  775.190973] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  826.904595] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  826.906833] sd 6:0:0:0: [sdb] Asking for cache data failed
[  826.906838] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  878.616996] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  878.619109] sd 6:0:0:0: [sdb] Asking for cache data failed
[  878.619117] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  930.324755] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  930.326870] sd 6:0:0:0: [sdb] Asking for cache data failed
[  930.326877] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[  982.040645] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[  982.042881] sd 6:0:0:0: [sdb] Asking for cache data failed
[  982.042888] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1033.752895] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1033.755023] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1033.755030] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1085.464791] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1085.466904] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1085.466911] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1137.177862] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1137.180087] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1137.180099] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1188.888808] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1188.890920] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1188.890928] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1240.596675] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1240.598791] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1240.598795] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1292.308794] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1292.310918] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1292.310924] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1344.024837] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1344.026957] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1344.026964] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1395.736845] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1395.738967] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1395.738974] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1447.449486] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1447.451607] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1447.451615] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1499.160747] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1499.162855] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1499.162862] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1550.872762] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1550.875004] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1550.875012] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1602.584769] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1602.586877] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1602.586886] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1654.296777] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1654.298889] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1654.298896] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1706.008655] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1706.010773] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1706.010779] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1757.720671] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1757.722908] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1757.722914] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1809.432937] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1809.435049] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1809.435056] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1861.144811] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1861.146931] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1861.146939] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1912.856821] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1912.858941] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1912.858948] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 1964.568689] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 1964.570801] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 1964.570807] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2016.280715] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2016.282961] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2016.282968] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2067.992856] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2067.994969] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2067.994976] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2119.704862] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2119.706981] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2119.706989] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2171.416879] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2171.418990] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2171.418997] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2223.128633] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2223.130879] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2223.130886] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2274.840892] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2274.843009] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2274.843016] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2326.552654] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2326.554772] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2326.554779] sd 6:0:0:0: [sdb] Assuming drive cache: write through
[ 2378.264675] sd 6:0:0:0: [sdb] Test WP failed, assume Write Enabled
[ 2378.266780] sd 6:0:0:0: [sdb] Asking for cache data failed
[ 2378.266787] sd 6:0:0:0: [sdb] Assuming drive cache: write through
```

SMARTDRIVE
Output:
```

smartctl 5.43 2012-06-30 r3573 [i686-linux-3.5.0-26-generic] (local build)
Copyright (C) 2002-12 by Bruce Allen, [http://smartmontools.sourceforge.net](http://smartmontools.sourceforge.net)

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Momentus 5400.5
Device Model:     ST9160310AS
Serial Number:    5SV3V27N
LU WWN Device Id: 5 000c50 013ae4b08
Firmware Version: DE05
User Capacity:    160,041,885,696 bytes [160 GB]
Sector Size:      512 bytes logical/physical
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   8
ATA Standard is:  ATA-8-ACS revision 4
Local Time is:    Fri Mar 29 18:43:29 2013 GMT
SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: PASSED

General SMART Values:
Offline data collection status:  (0x00)    Offline data collection activity
                    was never started.
                    Auto Offline Data Collection: Disabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (    0) seconds.
Offline data collection
capabilities:              (0x73) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    No Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  59) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   117   099   006    Pre-fail  Always       -       157379492
  3 Spin_Up_Time            0x0003   099   099   085    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   096   096   020    Old_age   Always       -       4172
  5 Reallocated_Sector_Ct   0x0033   100   100   036    Pre-fail  Always       -       0
  7 Seek_Error_Rate         0x000f   081   060   030    Pre-fail  Always       -       157576683
  9 Power_On_Hours          0x0032   091   091   000    Old_age   Always       -       8187
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   097   097   020    Old_age   Always       -       3806
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   099   099   000    Old_age   Always       -       1
188 Command_Timeout         0x0032   100   099   000    Old_age   Always       -       18
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   067   053   045    Old_age   Always       -       33 (Min/Max 18/33)
191 G-Sense_Error_Rate      0x0032   100   100   000    Old_age   Always       -       129
192 Power-Off_Retract_Count 0x0032   099   099   000    Old_age   Always       -       3773
193 Load_Cycle_Count        0x0032   061   061   000    Old_age   Always       -       78370
194 Temperature_Celsius     0x0022   033   047   000    Old_age   Always       -       33 (0 11 0 0 0)
195 Hardware_ECC_Recovered  0x001a   057   040   000    Old_age   Always       -       157379492
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       78885664333570
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3275950430
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       2384249604

SMART Error Log Version: 1
ATA Error Count: 23 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 23 occurred at disk power-on lifetime: 773 hours (32 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b6 4f 8e 0a  Error: UNC at LBA = 0x0a8e4fb6 = 177098678

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 50 08 6c 8e 4a 00      03:04:37.299  READ FPDMA QUEUED
  60 00 00 08 6b 8e 4a 00      03:04:37.299  READ FPDMA QUEUED
  60 00 00 08 6a 8e 4a 00      03:04:37.299  READ FPDMA QUEUED
  60 00 00 08 69 8e 4a 00      03:04:37.298  READ FPDMA QUEUED
  60 00 00 08 68 8e 4a 00      03:04:37.298  READ FPDMA QUEUED

Error 22 occurred at disk power-on lifetime: 770 hours (32 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b6 4f 8e 0a  Error: UNC at LBA = 0x0a8e4fb6 = 177098678

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 50 08 6c 8e 4a 00      00:20:05.827  READ FPDMA QUEUED
  60 00 00 08 6b 8e 4a 00      00:20:05.826  READ FPDMA QUEUED
  60 00 00 08 6a 8e 4a 00      00:20:05.826  READ FPDMA QUEUED
  60 00 00 08 69 8e 4a 00      00:20:05.825  READ FPDMA QUEUED
  60 00 00 08 68 8e 4a 00      00:20:05.825  READ FPDMA QUEUED

Error 21 occurred at disk power-on lifetime: 770 hours (32 days + 2 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b6 4f 8e 0a  Error: UNC at LBA = 0x0a8e4fb6 = 177098678

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 40 00 68 81 41 00      00:02:11.327  READ FPDMA QUEUED
  60 00 40 c0 67 81 41 00      00:02:11.317  READ FPDMA QUEUED
  60 00 50 08 6c 8e 4a 00      00:02:11.294  READ FPDMA QUEUED
  60 00 00 08 6b 8e 4a 00      00:02:11.293  READ FPDMA QUEUED
  60 00 00 08 6a 8e 4a 00      00:02:11.293  READ FPDMA QUEUED

Error 20 occurred at disk power-on lifetime: 768 hours (32 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b6 4f 8e 0a  Error: UNC at LBA = 0x0a8e4fb6 = 177098678

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 08 b8 a8 5c 41 00      00:02:43.595  READ FPDMA QUEUED
  60 00 20 20 bd 86 41 00      00:02:43.591  READ FPDMA QUEUED
  60 00 50 08 6c 8e 4a 00      00:02:43.590  READ FPDMA QUEUED
  60 00 00 08 6b 8e 4a 00      00:02:43.589  READ FPDMA QUEUED
  60 00 00 08 6a 8e 4a 00      00:02:43.589  READ FPDMA QUEUED

Error 19 occurred at disk power-on lifetime: 768 hours (32 days + 0 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  40 51 00 b6 4f 8e 0a  Error: UNC at LBA = 0x0a8e4fb6 = 177098678

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  60 00 00 02 0f a9 41 00      01:34:09.850  READ FPDMA QUEUED
  60 00 00 02 0e a9 41 00      01:34:09.849  READ FPDMA QUEUED
  60 00 00 02 0d a9 41 00      01:34:09.846  READ FPDMA QUEUED
  60 00 00 02 0c a9 41 00      01:34:09.843  READ FPDMA QUEUED
  60 00 00 02 0b a9 41 00      01:34:09.831  READ FPDMA QUEUED

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Short offline       Completed without error       00%      5353         -
# 2  Short offline       Completed without error       00%      4769         -
# 3  Short offline       Completed without error       00%      4265         -
# 4  Short offline       Completed without error       00%      3619         -
# 5  Short offline       Completed without error       00%       766         -
# 6  Short offline       Completed without error       00%       766         -
# 7  Short offline       Completed without error       00%         8         -
# 8  Short offline       Completed without error       00%         5         -
# 9  Short offline       Interrupted (host reset)      70%         5         -
#10  Short offline       Completed without error       00%         1         -
#11  Short offline       Completed without error       00%         1         -
#12  Short offline       Completed without error       00%         1         -
#13  Short offline       Completed without error       00%         1         -
#14  Short offline       Completed without error       00%         1         -

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.

```

Is it possible to make anything out of this?

Thank you.
John B

---

### Post by oldfred on 2013-03-29
Please use code tags. Using advanced edit menu you can easily add them with the # in edit panel.

All I know with Smart Status is green in Disk Utility is good. 
In your test file it shows passed, so that should be ok.

But it seems to be having issues mounting drives (partitions?).
What is sdb?

I might run fsck if ext formatted on all ext partitions.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by JohnBUK on 2013-03-29
I run a website using NetObjectsFusion running on Windows via Virtualbox (20Gb) (I'm soon to divest myself of this) .

Could this be what you mention?

John

---

### Post by oldfred on 2013-03-29
I so not know anything about vitualbox.

But is you are mounting partitions from the network that can slow things down a lot, especially if you have network issues.

---

### Post by tgalati4 on 2013-03-30
It's possible your 20GB virtual machine--I assume it is a single 20GB file is taking a long time to check to make sure it is intact.  Normally when you run virtual machines, they are on a server that you run 24/7 so you don't boot very often.  Who cares if it takes a server 1 minute to boot or 3 mintutes to boot if you only take it down twice a year.

It looks like Unity-greeter takes a long time to load, but I don't run Unity so I can't comment if that is normal or not.

---

