---
title: "How to Speed Up 135 Second Boot Time Ubuntu 14.04 dmesg"
date: 2015-03-10
forum: General Help
---

### Post by darrenllr on 2015-03-10
Hi All,

I have a slow startup on my Lenovo Thinkpad R61i.

I've tinkered a bit with it since installing 14.04, installed stuff, uninstalled stuff, and I'm running TLP for battery control / charging limits.

I have foraged around on the forum here / google in general, and have so far followed some instructions for removing 'orphaned' packages / dependencies / generally cleaning up.

It still hasn't improved boot time by much (think it was 170-ish seconds before).

I have found on other threads something about the output of dmesg in Terminal - so that's below - 

I'm just not sure what it all means, or how I can speed things up a little.

Any ideas would be great thanks - 

Darren
```

[    0.696403] rtc_cmos 00:02: RTC can wake from S4
[    0.696608] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.696645] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.696751] device-mapper: uevent: version 1.0.3
[    0.696873] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.696893] ledtrig-cpu: registered to indicate activity on CPUs
[    0.697026] TCP: cubic registered
[    0.697210] NET: Registered protocol family 10
[    0.697498] NET: Registered protocol family 17
[    0.697523] Key type dns_resolver registered
[    0.697941] Loading compiled-in X.509 certificates
[    0.699297] Loaded X.509 cert 'Magrathea: Glacier signing key: 7be2a7200f17f00ca011f70e5a874c37e3e0f6be'
[    0.699321] registered taskstats version 1
[    0.701405] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.702216] Key type trusted registered
[    0.704618] Key type encrypted registered
[    0.707392] AppArmor: AppArmor sha1 policy hashing enabled
[    0.707397] ima: No TPM chip found, activating TPM-bypass!
[    0.707428] evm: HMAC attrs: 0x1
[    0.708103]   Magic number: 7:257:923
[    0.708275] rtc_cmos 00:02: setting system clock to 2015-03-10 06:54:19 UTC (1425970459)
[    0.710359] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.710361] EDD information not available.
[    0.710470] PM: Hibernation image not present or could not be loaded.
[    0.809932] Freeing unused kernel memory: 1356K (ffffffff81d1c000 - ffffffff81e6f000)
[    0.809936] Write protecting the kernel read-only data: 12288k
[    0.812116] Freeing unused kernel memory: 564K (ffff880001773000 - ffff880001800000)
[    0.814027] Freeing unused kernel memory: 500K (ffff880001b83000 - ffff880001c00000)
[    0.829225] systemd-udevd[106]: starting version 204
[    0.860452] pps_core: LinuxPPS API ver. 1 registered
[    0.860455] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.862301] PTP clock support registered
[    0.867893] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.867897] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    0.868150] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.868181] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    0.887081] sdhci: Secure Digital Host Controller Interface driver
[    0.887085] sdhci: Copyright(c) Pierre Ossman
[    0.889225] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[    0.889245] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.890348] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[    0.890359] mmc0: no vqmmc regulator found
[    0.890361] mmc0: no vmmc regulator found
[    0.891361] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[    0.892744] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[    0.960093] firewire_ohci 0000:15:00.1: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.000091] usb 2-5: new high-speed USB device number 2 using ehci-pci
[    1.143474] usb 2-5: New USB device found, idVendor=17ef, idProduct=1004
[    1.143478] usb 2-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.143481] usb 2-5: Product: Integrated Camera
[    1.143483] usb 2-5: Manufacturer: Chicony Electronics Co., Ltd.
[    1.143486] usb 2-5: SerialNumber: SN0001
[    1.196363] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:15:58:84:5a:d6
[    1.196368] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.196398] e1000e 0000:00:19.0 eth0: MAC: 6, PHY: 6, PBA No: 1008FF-0FF
[    1.196586] ahci 0000:00:1f.2: version 3.0
[    1.196756] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    1.196819] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATA mode
[    1.196823] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.198076] scsi2 : ahci
[    1.198852] scsi3 : ahci
[    1.199035] scsi4 : ahci
[    1.199120] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 47
[    1.199123] ata4: DUMMY
[    1.199126] ata5: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 47
[    1.460461] firewire_core 0000:15:00.1: created device fw0: GUID 00016c2000bee5ff, S400
[    1.516074] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.516630] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.516634] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.516638] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.520066] ata5: SATA link down (SStatus 0 SControl 300)
[    1.562815] ata3.00: ATA-7: WDC WD1600BEVS-08RST2, 08.01G08, max UDMA/133
[    1.562818] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.563705] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.563709] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.563712] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.564551] ata3.00: configured for UDMA/133
[    1.564715] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 1G08 PQ: 0 ANSI: 5
[    1.565057] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.565124] sd 2:0:0:0: [sda] Write Protect is off
[    1.565127] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.565152] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.565157] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.596425]  sda: sda1 sda2 < sda5 >
[    1.596995] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.624856] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04791/0x300000/0x0, board id: 71, fw id: 496542
[    1.624864] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    1.666659] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.931349] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.892096] floppy0: no floppy controllers found
[    4.796696] random: nonblocking pool is initialized
[    4.967237] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    6.430687] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    6.664763] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input6
[   14.376363] Adding 4125692k swap on /dev/sda5.  Priority:-1 extents:1 across:4125692k FS
[   14.764858] systemd-udevd[280]: starting version 204
[   14.913826] lp: driver loaded but no devices found
[   14.919825] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   14.949695] wmi: Mapper loaded
[   14.950048] ppdev: user-space parallel port driver
[   14.979911] [drm] Initialized drm 1.1.0 20060810
[   15.022697] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   15.027674] acpi device:06: registered as cooling_device2
[   15.031930] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   15.054414] Non-volatile memory driver v1.3
[   15.058755] cfg80211: Calling CRDA to update world regulatory domain
[   15.067585] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   15.067589] thinkpad_acpi: http://ibm-acpi.sf.net/
[   15.067591] thinkpad_acpi: ThinkPad BIOS 7LETD0WW (2.30 ), EC 7KHT24WW-1.08
[   15.067593] thinkpad_acpi: Lenovo ThinkPad T61, model 7742B6V
[   15.068994] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   15.069701] thinkpad_acpi: ACPI backlight control delay disabled
[   15.069843] thinkpad_acpi: radio switch found; radios are enabled
[   15.069866] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   15.069868] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   15.072444] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x0000000000001000-0x000000000000107f (\_SB_.PCI0.LPC_.PMIO) (20140424/utaddress-258)
[   15.072452] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.072457] ACPI Warning: 
[   15.072460] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is blocked
[   15.072463] SystemIO range 0x00000000000011b0-0x00000000000011bf conflicts with OpRegion 0x0000000000001180-0x00000000000011bf (\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   15.072466] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.072468] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011af conflicts with OpRegion 0x0000000000001180-0x00000000000011bf (\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   15.072474] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.072476] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.077239] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   15.077436] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   15.078628] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input8
[   15.098072] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   15.133484] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   15.133489] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   15.133558] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   15.191122] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.191127] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   15.191203] iwl3945 0000:03:00.0: irq 48 for MSI/MSI-X
[   15.198108] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.225125] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   15.225132] yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   15.225140] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [io  0x8000-0xbfff]
[   15.225144] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xf8100000-0xfbffffff]
[   15.225147] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf8100000-0xfbffffff:
[   15.225153]  excluding 0xf8100000-0xf84effff
[   15.225163] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xf4000000-0xf7ffffff 64bit pref]
[   15.225166] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf4000000-0xf7ffffff:
[   15.225171]  excluding 0xf4000000-0xf7ffffff
[   15.239161] r592: driver successfully loaded
[   15.239669] r852: driver loaded successfully
[   15.340135] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.347424] snd_hda_intel 0000:00:1b.0: probe_mask set to 0x1 for device 17aa:20ac
[   15.347492] snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   15.360619] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.380896] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   15.494235] audit: type=1400 audit(1425970474.280:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=370 comm="apparmor_parser"
[   15.494243] audit: type=1400 audit(1425970474.280:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=370 comm="apparmor_parser"
[   15.494248] audit: type=1400 audit(1425970474.280:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   15.494801] audit: type=1400 audit(1425970474.280:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=370 comm="apparmor_parser"
[   15.494807] audit: type=1400 audit(1425970474.280:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   15.494835] audit: type=1400 audit(1425970474.280:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=398 comm="apparmor_parser"
[   15.494842] audit: type=1400 audit(1425970474.280:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=398 comm="apparmor_parser"
[   15.494847] audit: type=1400 audit(1425970474.280:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=398 comm="apparmor_parser"
[   15.495093] audit: type=1400 audit(1425970474.280:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=370 comm="apparmor_parser"
[   15.495394] audit: type=1400 audit(1425970474.280:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=398 comm="apparmor_parser"
[   15.723690] sound hdaudioC0D0: autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0) type:speaker
[   15.723696] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.723699] sound hdaudioC0D0:    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   15.723701] sound hdaudioC0D0:    mono: mono_out=0x0
[   15.723704] sound hdaudioC0D0:    dig-out=0x1b/0x0
[   15.723706] sound hdaudioC0D0:    inputs:
[   15.723709] sound hdaudioC0D0:      Internal Mic=0x15
[   15.723712] sound hdaudioC0D0:      Dock Mic=0x1c
[   15.723715] sound hdaudioC0D0:      Mic=0x14
[   15.730220] input: HDA Intel Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   15.730369] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.730513] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.738140] cfg80211: World regulatory domain updated:
[   15.738144] cfg80211:  DFS Master region: unset
[   15.738146] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   15.738150] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.738153] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.738156] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.738158] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.738161] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   15.826883] media: Linux media interface: v0.10
[   15.833146] Linux video capture interface: v2.00
[   15.872477] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:1004)
[   15.877623] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input12
[   15.878302] usbcore: registered new interface driver uvcvideo
[   15.878306] USB Video Class driver (1.1.1)
[   16.052068] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[   16.080346] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   16.080356]  excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   16.080381] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   16.080391]  excluding 0xa0000000-0xa0ffffff
[   16.080408] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   16.080417]  excluding 0x60000000-0x60ffffff
[   16.223105] usb 3-1: New USB device found, idVendor=0a5c, idProduct=2110
[   16.223110] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[   16.223113] usb 3-1: Product: BCM2045B
[   16.223116] usb 3-1: Manufacturer: Broadcom Corp
[   16.254546] Bluetooth: Core ver 2.19
[   16.254574] NET: Registered protocol family 31
[   16.254576] Bluetooth: HCI device and connection manager initialized
[   16.254588] Bluetooth: HCI socket layer initialized
[   16.254592] Bluetooth: L2CAP socket layer initialized
[   16.254611] Bluetooth: SCO socket layer initialized
[   16.263471] usbcore: registered new interface driver btusb
[   16.568574] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   16.757442] nvidia: module license 'NVIDIA' taints kernel.
[   16.757448] Disabling lock debugging due to kernel taint
[   16.772739] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   16.781386] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   16.782100] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   16.782118] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.113  Mon Dec  1 21:08:13 PST 2014
[   17.684313] init: failsafe main process (718) killed by TERM signal
[   18.084074] floppy0: no floppy controllers found
[   18.084090] work still pending
[   18.731377] Bluetooth: RFCOMM TTY layer initialized
[   18.731393] Bluetooth: RFCOMM socket layer initialized
[   18.731403] Bluetooth: RFCOMM ver 1.11
[   19.018855] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.018862] Bluetooth: BNEP filters: protocol multicast
[   19.018875] Bluetooth: BNEP socket layer initialized
[   19.224534] init: cups main process (824) killed by HUP signal
[   19.224550] init: cups main process ended, respawning
[   20.748365] init: samba-ad-dc main process (985) terminated with status 1
[   21.539047] audit_printk_skb: 120 callbacks suppressed
[   21.539052] audit: type=1400 audit(1425970480.324:52): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1147 comm="apparmor_parser"
[   21.644346] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   21.748109] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   21.748244] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.069767] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   22.142449] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.443125] thinkpad_ec: thinkpad_ec 0.41 loaded.
[   22.443457] tp_smapi 0.41 loading...
[   22.443654] tp_smapi successfully loaded (smapi_port=0xb2).
[   22.735153] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.735219] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.735268] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.735318] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.735368] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.735415] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.867840] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.867906] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.867954] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.868067] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.868122] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.868169] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.100175] nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
[   26.504689] wlan0: authenticate with 68:b6:fc:2d:f5:88
[   26.509553] wlan0: send auth to 68:b6:fc:2d:f5:88 (try 1/3)
[   26.512468] wlan0: authenticated
[   26.516056] wlan0: associate with 68:b6:fc:2d:f5:88 (try 1/3)
[   26.525488] wlan0: RX AssocResp from 68:b6:fc:2d:f5:88 (capab=0x411 status=0 aid=2)
[   26.526656] wlan0: associated
[   26.526701] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.526767] cfg80211: Calling CRDA for country: US
[   26.533330] cfg80211: Regulatory domain changed to country: US
[   26.533335] cfg80211:  DFS Master region: unset
[   26.533337] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   26.533341] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
[   26.533344] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (N/A)
[   26.533347] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   26.533349] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   26.533352] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   26.533355] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
[   26.533357] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   28.378013] wlan0: deauthenticating from 68:b6:fc:2d:f5:88 by local choice (Reason: 2=PREV_AUTH_NOT_VALID)
[   28.401376] wlan0: authenticate with 68:b6:fc:2d:f5:88
[   28.401458] wlan0: send auth to 68:b6:fc:2d:f5:88 (try 1/3)
[   28.402738] cfg80211: Calling CRDA to update world regulatory domain
[   28.406067] cfg80211: World regulatory domain updated:
[   28.406072] cfg80211:  DFS Master region: unset
[   28.406074] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   28.406078] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.406081] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.406084] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.406086] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.406089] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   28.406396] wlan0: authenticated
[   28.408077] wlan0: associate with 68:b6:fc:2d:f5:88 (try 1/3)
[   28.420362] wlan0: RX AssocResp from 68:b6:fc:2d:f5:88 (capab=0x411 status=0 aid=2)
[   28.421598] wlan0: associated
[   28.421924] cfg80211: Calling CRDA for country: US
[   28.428878] cfg80211: Regulatory domain changed to country: US
[   28.428883] cfg80211:  DFS Master region: unset
[   28.428885] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   28.428889] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm), (N/A)
[   28.428892] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm), (N/A)
[   28.428895] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   28.428898] cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   28.428900] cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (0 s)
[   28.428903] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm), (N/A)
[   28.428906] cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000 mBm), (N/A)
[   28.558308] init: plymouth-upstart-bridge main process ended, respawning
[   28.882553] audit: type=1400 audit(1425970487.668:53): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1415 comm="nm-dhcp-client." lport=52172 family="inet" sock_type="dgram" protocol=17
[   28.882570] audit: type=1400 audit(1425970487.668:54): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1415 comm="nm-dhcp-client." lport=51274 family="inet6" sock_type="dgram" protocol=17
[   28.930281] audit: type=1400 audit(1425970487.720:55): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1420 comm="nm-dhcp-client." lport=52172 family="inet" sock_type="dgram" protocol=17
[   28.930296] audit: type=1400 audit(1425970487.720:56): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1420 comm="nm-dhcp-client." lport=51274 family="inet6" sock_type="dgram" protocol=17
[   32.701033] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   32.737015] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:6c:62:6d:57:82:17:08:00 SRC=192.168.0.13 DST=192.168.0.16 LEN=48 TOS=0x00 PREC=0x00 TTL=128 ID=24772 DF PROTO=TCP SPT=54551 DPT=4242 WINDOW=65535 RES=0x00 SYN URGP=0 
[   48.934966] audit: type=1400 audit(1425970507.720:57): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1900 comm="apparmor_parser"
[   48.934979] audit: type=1400 audit(1425970507.720:58): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1900 comm="apparmor_parser"
[   48.935536] audit: type=1400 audit(1425970507.720:59): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1900 comm="apparmor_parser"
[   66.673152] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=192.168.0.1 DST=192.168.0.16 LEN=438 TOS=0x00 PREC=0x00 TTL=64 ID=0 DF PROTO=UDP SPT=1900 DPT=1901 LEN=418 
[   71.932235] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=216.17.8.55 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=40824 DF PROTO=TCP SPT=42912 DPT=4242 WINDOW=29200 RES=0x00 SYN URGP=0 
[   72.931070] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=216.17.8.55 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=40825 DF PROTO=TCP SPT=42912 DPT=4242 WINDOW=29200 RES=0x00 SYN URGP=0 
[   74.945124] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=216.17.8.55 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=40826 DF PROTO=TCP SPT=42912 DPT=4242 WINDOW=29200 RES=0x00 SYN URGP=0 
[   78.936183] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=216.17.8.55 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=40827 DF PROTO=TCP SPT=42912 DPT=4242 WINDOW=29200 RES=0x00 SYN URGP=0 
[   86.947998] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=216.17.8.55 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=40828 DF PROTO=TCP SPT=42912 DPT=4242 WINDOW=29200 RES=0x00 SYN URGP=0 
[  102.971044] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=216.17.8.55 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=40829 DF PROTO=TCP SPT=42912 DPT=4242 WINDOW=29200 RES=0x00 SYN URGP=0 
[  123.438861] wlan0: deauthenticating from 68:b6:fc:2d:f5:88 by local choice (Reason: 3=DEAUTH_LEAVING)
[  123.462605] cfg80211: Calling CRDA to update world regulatory domain
[  123.470353] cfg80211: World regulatory domain updated:
[  123.470368] cfg80211:  DFS Master region: unset
[  123.470373] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[  123.470380] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  123.470387] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  123.470392] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[  123.470398] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  123.470404] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[  125.565080] wlan0: authenticate with 00:26:18:c5:ad:9c
[  125.568927] wlan0: send auth to 00:26:18:c5:ad:9c (try 1/3)
[  125.572129] wlan0: authenticated
[  125.576095] wlan0: associate with 00:26:18:c5:ad:9c (try 1/3)
[  125.580634] wlan0: RX AssocResp from 00:26:18:c5:ad:9c (capab=0x411 status=0 aid=5)
[  125.583032] wlan0: associated
[  125.642715] audit: type=1400 audit(1425970584.430:60): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1957 comm="nm-dhcp-client." lport=33906 family="inet" sock_type="dgram" protocol=17
[  125.642732] audit: type=1400 audit(1425970584.430:61): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1957 comm="nm-dhcp-client." lport=35858 family="inet6" sock_type="dgram" protocol=17
[  128.555684] audit: type=1400 audit(1425970587.341:62): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1976 comm="nm-dhcp-client." lport=33906 family="inet" sock_type="dgram" protocol=17
[  128.555698] audit: type=1400 audit(1425970587.341:63): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1976 comm="nm-dhcp-client." lport=35858 family="inet6" sock_type="dgram" protocol=17
[  135.018819] [UFW BLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00 SRC=216.17.8.55 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=47 ID=40830 DF PROTO=TCP SPT=42912 DPT=4242 WINDOW=29200 RES=0x00 SYN URGP=0 
darren@darren-ThinkPad-R61i:~$ 



```

---

### Post by tripp98 on 2015-03-10
How much ram does it have?  Have you done any customization on the swap partition?

---

### Post by oldfred on 2015-03-10
You want to review the entries with large time stamp differences. 
one is floppy drive? Do you even have one, sometimes it is turned on in UEFI/BIOS so system has to search for it, and then timeout when not found.
The other is all sorts of inet6 or IPv6 related stuff. I do not know about it but it looks like you are trying to enable IPv6 and do not have it so it also has to timeout. 
Does your router now use IPv6 as an alternative?

---

### Post by darrenllr on 2015-03-11
Hi Trip - thanks for the reply,

4Gb RAM I think, 4Gb Swap.

here is the output from free -m :

```

darren@darren-ThinkPad-R61i:~$ free -m
             total       used       free     shared    buffers     cached
Mem:          3887       2594       1293         20        155        782
-/+ buffers/cache:       1656       2231
Swap:         4028          0       402

```

I *might* have set the SWAP to be equal or greater to the amount of RAM available - I do recall reading somewhere that it *should* be set that way to avoid issues / maybe with Hibernate.  I can't remember if I set it myself, or if it was already set to 4Gb when I checked. 

Hope that helps ;-)

Darren.

Thanks OldFred - 

I'm just checking my Network Connections now.

On the IPv6 Settings tab (on 1 - will check rest shortly) - I see 

Method: Automatic

selected on the dropdown.

I'll set them all to "Ignore".

Will check BIOS for floppy / restart - will probably be when I get back home to check dmesg again & repost.

Many Thanks ;-)
Darren.

Just had 10 minutes to investigate again.

I couldn't see a floppy drive enabled in BIOS - I did see that there were various USB / network entries in Boot / Startup, so disabled everything that didn't say "HDD".

I checked TLP to make sure that wasn't trying to 'turn on' or 'turn off' anything with regards to power management.

Around 5 or 6 seconds, just after the 'floppy0' line, I see it's got something about the IBM trackpad.  I'll Google that, seems to take 9 or 10 seconds.

There seem to be 11 acpi_call entries around 23 seconds - no idea what that is, but I'm not sure if there should be 11 of them in a row.  Will try to research that also.

Then from 30 seconds-ish, up to around 169 seconds, seems to be doing all sorts of network stuff, I see MAC addresses in there.  Maybe this is a red herring for me though - could that be after I logged in & connected to wifi maybe?

Here is the updated output from dmesg anyhow - 

Thanks for any advice again - 

Darren

```
[    1.192437] usbusb6: Manufacturer: Linux 3.16.0-30-generic uhci_hcd[    1.192442] usbusb6: SerialNumber: 0000:00:1d.1
[    1.192739] hub6-0:1.0: USB hub found
[    1.192770] hub6-0:1.0: 2 ports detected
[    1.193166]uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.193180]uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.193192]uhci_hcd 0000:00:1d.2: detected 2 ports
[    1.193238]uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    1.193338] usbusb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.193344] usbusb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.193350] usbusb7: Product: UHCI Host Controller
[    1.193355] usbusb7: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    1.193360] usbusb7: SerialNumber: 0000:00:1d.2
[    1.193653] hub7-0:1.0: USB hub found
[    1.193670] hub7-0:1.0: 2 ports detected
[    1.194084]i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64irq 1,12
[    1.201978]serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.201989]serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.202365]mousedev: PS/2 mouse device common for all mice
[    1.202869]rtc_cmos 00:02: RTC can wake from S4
[    1.203142]rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.203188]rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpetirqs
[    1.203399]device-mapper: uevent: version 1.0.3
[    1.203605]device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised:dm-devel@redhat.com
[    1.203658]ledtrig-cpu: registered to indicate activity on CPUs
[    1.203902] TCP:cubic registered
[    1.204289] NET:Registered protocol family 10
[    1.204768] NET:Registered protocol family 17
[    1.204804] Keytype dns_resolver registered
[    1.205524]Loading compiled-in X.509 certificates
[    1.207680]input: AT Translated Set 2 keyboard as/devices/platform/i8042/serio0/input/input3
[    1.208249]Loaded X.509 cert 'Magrathea: Glacier signing key:7be2a7200f17f00ca011f70e5a874c37e3e0f6be'
[    1.208296]registered taskstats version 1
[    1.213764] Keytype trusted registered
[    1.218203] Keytype encrypted registered
[    1.222693]AppArmor: AppArmor sha1 policy hashing enabled
[    1.222703] ima:No TPM chip found, activating TPM-bypass!
[    1.222751] evm:HMAC attrs: 0x1
[    1.223634]  Magic number: 7:923:320
[    1.223711] miscmicrocode: hash matches
[    1.223717]platform microcode: hash matches
[    1.223727] ttytty45: hash matches
[    1.223864]rtc_cmos 00:02: setting system clock to 2015-03-11 08:20:52 UTC(1426062052)
[    1.225577] BIOSEDD facility v0.16 2004-Jun-25, 0 devices found
[    1.225581] EDDinformation not available.
[    1.225777] PM:Hibernation image not present or could not be loaded.
[    1.313973]Freeing unused kernel memory: 1356K (ffffffff81d1c000 -ffffffff81e6f000)
[    1.313977] Writeprotecting the kernel read-only data: 12288k
[    1.316163]Freeing unused kernel memory: 564K (ffff880001773000 -ffff880001800000)
[    1.318078]Freeing unused kernel memory: 500K (ffff880001b83000 -ffff880001c00000)
[    1.333228]systemd-udevd[106]: starting version 204
[    1.377989]pps_core: LinuxPPS API ver. 1 registered
[    1.377992]pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti<giometti@linux.it>
[    1.381554]sdhci: Secure Digital Host Controller Interface driver
[    1.381557]sdhci: Copyright(c) Pierre Ossman
[    1.383446]sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[    1.383465] pci0000:00:1e.0: enabling device (0005 -> 0007)
[    1.384567]sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn'tfully claim to support it.
[    1.384590] mmc0:no vqmmc regulator found
[    1.384592] mmc0:no vmmc regulator found
[    1.384955] PTPclock support registered
[    1.385592]sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn'tfully claim to support it.
[    1.390731]e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    1.390735]e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    1.390939]e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set todynamic conservative mode
[    1.390968]e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    1.391435] mmc0:SDHCI controller on PCI [0000:15:00.2] using DMA
[    1.460170]firewire_ohci 0000:15:00.1: added OHCI v1.10 device as card 0, 4 IR +4 IT contexts, quirks 0x11
[    1.716486]e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1)00:15:58:84:5a:d6
[    1.716491]e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.716522]e1000e 0000:00:19.0 eth0: MAC: 6, PHY: 6, PBA No: 1008FF-0FF
[    1.716570] ahci0000:00:1f.2: version 3.0
[    1.716760] ahci0000:00:1f.2: irq 47 for MSI/MSI-X
[    1.716822] ahci0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATAmode
[    1.716826] ahci0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.717469] scsi2: ahci
[    1.717626] scsi3: ahci
[    1.718188] scsi4: ahci
[    1.718281] ata3:SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 47
[    1.718284] ata4:DUMMY
[    1.718288] ata5:SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 47
[    1.744124] usb2-5: new high-speed USB device number 2 using ehci-pci
[    1.887508] usb2-5: New USB device found, idVendor=17ef, idProduct=1004
[    1.887516] usb2-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.887522] usb2-5: Product: Integrated Camera
[    1.887527] usb2-5: Manufacturer: Chicony Electronics Co., Ltd.
[    1.887532] usb2-5: SerialNumber: SN0001
[    1.960275]firewire_core 0000:15:00.1: created device fw0: GUID00016c2000bee5ff, S400
[    2.036083] ata3:SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.036120] ata5:SATA link down (SStatus 0 SControl 300)
[    2.036794]ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.036797]ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK)filtered out
[    2.036800]ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.080871]ata3.00: ATA-7: WDC WD1600BEVS-08RST2, 08.01G08, max UDMA/133
[    2.080877]ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.082015]ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    2.082023]ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK)filtered out
[    2.082030]ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    2.082928]ata3.00: configured for UDMA/133
[    2.083088] scsi2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 1G08 PQ: 0 ANSI:5
[    2.083414] sd2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    2.083452] sd2:0:0:0: Attached scsi generic sg0 type 0
[    2.083597] sd2:0:0:0: [sda] Write Protect is off
[    2.083601] sd2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.083631] sd2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn'tsupport DPO or FUA
[    2.095866]psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x81a0b1,caps: 0xa04791/0x300000/0x0, board id: 71, fw id: 496542
[    2.095876]psmouse serio1: synaptics: serio: Synaptics pass-through port atisa0060/serio1/input0
[    2.125585]  sda:sda1 sda2 < sda5 >
[    2.126199] sd2:0:0:0: [sda] Attached SCSI disk
[    2.128046] usb3-1: new full-speed USB device number 2 using uhci_hcd
[    2.134629]input: SynPS/2 Synaptics TouchPad as/devices/platform/i8042/serio1/input/input5
[    2.298107] usb3-1: New USB device found, idVendor=0a5c, idProduct=2110
[    2.298116] usb3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.298122] usb3-1: Product: BCM2045B
[    2.298127] usb3-1: Manufacturer: Broadcom Corp
[    2.482922]EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts:(null)
[    4.396142]floppy0: no floppy controllers found
[    5.173436]psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 0064
[    5.208257]random: nonblocking pool is initialized
[    6.554819]psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons:3/3
[    6.767177]input: TPPS/2 IBM TrackPoint as/devices/platform/i8042/serio1/serio2/input/input6
[   15.161075]Adding 4125692k swap on /dev/sda5.  Priority:-1 extents:1across:4125692k FS
[   15.549615]systemd-udevd[280]: starting version 204
[   15.711942] lp:driver loaded but no devices found
[   15.713155] wmi:Mapper loaded
[   15.713421]shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.730083] ACPI:Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   15.735531]ppdev: user-space parallel port driver
[   15.784835] acpidevice:06: registered as cooling_device2
[   15.785852]input: Video Bus as/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   15.789692] [drm]Initialized drm 1.1.0 20060810
[   15.901067] ACPIWarning: SystemIO range 0x0000000000001028-0x000000000000102fconflicts with OpRegion 0x0000000000001000-0x000000000000107f(\_SB_.PCI0.LPC_.PMIO) (20140424/utaddress-258)
[   15.901076] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   15.901081] ACPIWarning: SystemIO range 0x00000000000011b0-0x00000000000011bfconflicts with OpRegion 0x0000000000001180-0x00000000000011bf(\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   15.901085] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   15.901087] ACPIWarning: SystemIO range 0x0000000000001180-0x00000000000011afconflicts with OpRegion 0x0000000000001180-0x00000000000011bf(\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   15.901092] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   15.901094]lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.908239] r592:driver successfully loaded
[   15.909680]cfg80211: Calling CRDA to update world regulatory domain
[   15.920239]yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   15.948492]iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driverfor Linux, in-tree:s
[   15.948497]iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   15.948568]iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPMcontrol
[   15.970645]Bluetooth: Core ver 2.19
[   15.970671] NET:Registered protocol family 31
[   15.970673]Bluetooth: HCI device and connection manager initialized
[   15.970683]Bluetooth: HCI socket layer initialized
[   15.970686]Bluetooth: L2CAP socket layer initialized
[   15.970698]Bluetooth: SCO socket layer initialized
[   15.990657]ip_tables: (C) 2000-2006 Netfilter Core Team
[   16.004442]iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11achannels
[   16.004448]iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   16.004526]iwl3945 0000:03:00.0: irq 48 for MSI/MSI-X
[   16.014120]nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   16.014390]Non-volatile memory driver v1.3
[   16.018721]thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   16.018725]thinkpad_acpi: http://ibm-acpi.sf.net/
[   16.018727]thinkpad_acpi: ThinkPad BIOS 7LETD0WW (2.30 ), EC 7KHT24WW-1.08
[   16.018729]thinkpad_acpi: Lenovo ThinkPad T61, model 7742B6V
[   16.030319]thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   16.034991]ip6_tables: (C) 2000-2006 Netfilter Core Team
[   16.035722]thinkpad_acpi: ACPI backlight control delay disabled
[   16.035881]thinkpad_acpi: radio switch found; radios are enabled
[   16.035904]thinkpad_acpi: This ThinkPad has standard ACPI backlight brightnesscontrol, supported by the ACPI video driver
[   16.035906]thinkpad_acpi: Disabling thinkpad-acpi brightness events bydefault...
[   16.037463]usbcore: registered new interface driver btusb
[   16.046821]thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   16.052504]yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   16.052510]yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   16.056369]ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   16.057032]thinkpad_acpi: Standard ACPI backlight interface available, notloading native one
[   16.057353]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [io 0x8000-0xbfff]
[   16.057359]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem0xf8100000-0xfbffffff]
[   16.057363]pcmcia_socket pcmcia_socket0: cs: memory probe0xf8100000-0xfbffffff:
[   16.057368] excluding 0xf8100000-0xf84effff
[   16.057379]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem0xf4000000-0xf7ffffff 64bit pref]
[   16.057382]pcmcia_socket pcmcia_socket0: cs: memory probe0xf4000000-0xf7ffffff:
[   16.057387] excluding 0xf4000000-0xf7ffffff
[   16.058996]thinkpad_acpi: Console audio control enabled, mode: monitor (readonly)
[   16.060337]input: ThinkPad Extra Buttons as/devices/platform/thinkpad_acpi/input/input8
[   16.080910] r852:driver loaded successfully
[   16.113082]snd_hda_intel 0000:00:1b.0: probe_mask set to 0x1 for device17aa:20ac
[   16.113136]snd_hda_intel 0000:00:1b.0: irq 49 for MSI/MSI-X
[   16.125899]media: Linux media interface: v0.10
[   16.131686] Linuxvideo capture interface: v2.00
[   16.150260]uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:1004)
[   16.167374]input: Integrated Camera as/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   16.167549]usbcore: registered new interface driver uvcvideo
[   16.167552] USBVideo Class driver (1.1.1)
[   16.336822]audit: type=1400 audit(1426062067.610:2): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/sbin/dhclient" pid=349 comm="apparmor_parser"
[   16.336831]audit: type=1400 audit(1426062067.610:3): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=349 comm="apparmor_parser"
[   16.336837]audit: type=1400 audit(1426062067.610:4): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=349comm="apparmor_parser"
[   16.337404]audit: type=1400 audit(1426062067.610:5): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=349 comm="apparmor_parser"
[   16.337414]audit: type=1400 audit(1426062067.610:6): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=349comm="apparmor_parser"
[   16.337702]audit: type=1400 audit(1426062067.610:7): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=349comm="apparmor_parser"
[   16.340535]audit: type=1400 audit(1426062067.614:8): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/sbin/dhclient" pid=504 comm="apparmor_parser"
[   16.340545]audit: type=1400 audit(1426062067.614:9): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=504 comm="apparmor_parser"
[   16.340552]audit: type=1400 audit(1426062067.614:10): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=504comm="apparmor_parser"
[   16.341156]audit: type=1400 audit(1426062067.614:11): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=504 comm="apparmor_parser"
[   16.517478] soundhdaudioC0D0: autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0)type:speaker
[   16.517484] soundhdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.517487] soundhdaudioC0D0:    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   16.517489] soundhdaudioC0D0:    mono: mono_out=0x0
[   16.517492] soundhdaudioC0D0:    dig-out=0x1b/0x0
[   16.517494] soundhdaudioC0D0:    inputs:
[   16.517497] soundhdaudioC0D0:      Internal Mic=0x15
[   16.517500] soundhdaudioC0D0:      Dock Mic=0x1c
[   16.517503] soundhdaudioC0D0:      Mic=0x14
[   16.529113]input: HDA Intel Dock Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   16.529265]input: HDA Intel Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   16.529435]input: HDA Intel Front Headphone as/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   16.622785]cfg80211: World regulatory domain updated:
[   16.622791]cfg80211:  DFS Master region: unset
[   16.622793]cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain,max_eirp), (dfs_cac_time)
[   16.622796]cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   16.622799]cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   16.622802]cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000mBm), (N/A)
[   16.622805]cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   16.622808]cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   16.787268]pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   16.787279] excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   16.787305]pcmcia_socket pcmcia_socket0: cs: memory probe0xa0000000-0xa0ffffff:
[   16.787314] excluding 0xa0000000-0xa0ffffff
[   16.787332]pcmcia_socket pcmcia_socket0: cs: memory probe0x60000000-0x60ffffff:
[   16.787341] excluding 0x60000000-0x60ffffff
[   17.219947]nvidia: module license 'NVIDIA' taints kernel.
[   17.219955]Disabling lock debugging due to kernel taint
[   17.235231]nvidia: module verification failed: signature and/or  required keymissing - tainting kernel
[   17.243663]vgaarb: device changed decodes:PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   17.244108] [drm]Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   17.244122] NVRM:loading NVIDIA UNIX x86_64 Kernel Module  331.113  Mon Dec  121:08:13 PST 2014
[   17.775192]EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   18.362113] init:failsafe main process (729) killed by TERM signal
[   18.812115]floppy0: no floppy controllers found
[   19.792560]Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.792565]Bluetooth: BNEP filters: protocol multicast
[   19.792579]Bluetooth: BNEP socket layer initialized
[   19.805520]Bluetooth: RFCOMM TTY layer initialized
[   19.805539]Bluetooth: RFCOMM socket layer initialized
[   19.805547]Bluetooth: RFCOMM ver 1.11
[   20.362839] init:cups main process (936) killed by HUP signal
[   20.362856] init:cups main process ended, respawning
[   21.873357] init:samba-ad-dc main process (991) terminated with status 1
[   22.004802]audit_printk_skb: 120 callbacks suppressed
[   22.004807]audit: type=1400 audit(1426062073.278:52): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cups-browsed" pid=1134comm="apparmor_parser"
[   22.008359]e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   22.112137]e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   22.112306] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready
[   22.276760]iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   22.350528] IPv6:ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   22.670279]thinkpad_ec: thinkpad_ec 0.41 loaded.
[   22.670900]tp_smapi 0.41 loading...
[   22.671107]tp_smapi successfully loaded (smapi_port=0xb2).
[   23.030966]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.031042]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.031093]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.031140]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.031186]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.031231]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.167116]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.167181]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.167230]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.167281]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.167328]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   23.167372]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.762349]nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
[   26.860637]wlan0: authenticate with 68:b6:fc:2d:f5:88
[   26.863739]wlan0: send auth to 68:b6:fc:2d:f5:88 (try 1/3)
[   26.866255]wlan0: authenticated
[   26.868050]wlan0: associate with 68:b6:fc:2d:f5:88 (try 1/3)
[   26.877476]wlan0: RX AssocResp from 68:b6:fc:2d:f5:88 (capab=0x411 status=0aid=3)
[   26.878652]wlan0: associated
[   26.878698] IPv6:ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   26.878765]cfg80211: Calling CRDA for country: US
[   26.882708]cfg80211: Regulatory domain changed to country: US
[   26.882713]cfg80211:  DFS Master region: unset
[   26.882715]cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain,max_eirp), (dfs_cac_time)
[   26.882719]cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700mBm), (N/A)
[   26.882722]cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700mBm), (N/A)
[   26.882725]cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (0 s)
[   26.882727]cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (0 s)
[   26.882730]cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (0 s)
[   26.882733]cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000mBm), (N/A)
[   26.882735]cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000mBm), (N/A)
[   28.155492]wlan0: deauthenticating from 68:b6:fc:2d:f5:88 by local choice(Reason: 2=PREV_AUTH_NOT_VALID)
[   28.688024]iwl3945 0000:03:00.0: Error sending C_RXON: time out after 500ms.
[   28.688029]iwl3945 0000:03:00.0: Error setting new configuration (-110).
[   28.969663]iwl3945 0000:03:00.0: Microcode SW error detected. Restarting0x82000008.
[   28.969668]iwl3945 0000:03:00.0: Loaded firmware version: 15.32.2.9
[   28.969701]iwl3945 0000:03:00.0: Start IWL Error Log Dump:
[   28.969704]iwl3945 0000:03:00.0: Status: 0x000202E4, count: 1
[   28.969706]iwl3945 0000:03:00.0: Desc       Time       asrtPC  blink2 ilink1 nmiPC   Line
[   28.969930]iwl3945 0000:03:00.0: SYSASSERT     (0x5) 0000496508 0x008B6 0x088CA0x00320 0x00000 58
[   28.969930] 
[   28.969995]iwl3945 0000:03:00.0: Error Reply type 0x0000003A cmd C_RXON_ASSOC(0x11) seq 0x0430 ser 0x00000000
[   28.970183]iwl3945 0000:03:00.0: Error: Response NULL in 'C_RXON_ASSOC'
[   29.257166] init:plymouth-upstart-bridge main process ended, respawning
[   29.468145]iwl3945 0000:03:00.0: Error sending C_RXON_ASSOC: time out after500ms.
[   29.468281]wlan0: authenticate with 68:b6:fc:2d:f5:88
[   29.469917]iwl3945 0000:03:00.0: Can't stop Rx DMA.
[   29.470171]ieee80211 phy0: Hardware restart was requested
[   29.470239]wlan0: send auth to 68:b6:fc:2d:f5:88 (try 1/3)
[   29.539896]cfg80211: Calling CRDA to update world regulatory domain
[   29.540840]wlan0: authenticated
[   29.543270]cfg80211: World regulatory domain updated:
[   29.543276]cfg80211:  DFS Master region: unset
[   29.543279]cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain,max_eirp), (dfs_cac_time)
[   29.543283]cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   29.543286]cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   29.543289]cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000mBm), (N/A)
[   29.543291]cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   29.543294]cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   29.544119]wlan0: associate with 68:b6:fc:2d:f5:88 (try 1/3)
[   29.553565]wlan0: RX AssocResp from 68:b6:fc:2d:f5:88 (capab=0x411 status=0aid=3)
[   29.554701]wlan0: associated
[   29.554796]cfg80211: Calling CRDA for country: US
[   29.558125]cfg80211: Regulatory domain changed to country: US
[   29.558132]cfg80211:  DFS Master region: unset
[   29.558135]cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain,max_eirp), (dfs_cac_time)
[   29.558139]cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700mBm), (N/A)
[   29.558142]cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700mBm), (N/A)
[   29.558145]cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (0 s)
[   29.558147]cfg80211:   (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (0 s)
[   29.558150]cfg80211:   (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (0 s)
[   29.558153]cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000mBm), (N/A)
[   29.558155]cfg80211:   (57240000 KHz - 63720000 KHz @ 2160000 KHz), (N/A, 4000mBm), (N/A)
[   30.233761]audit: type=1400 audit(1426062081.506:53): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=1444 comm="nm-dhcp-client." lport=11647 family="inet"sock_type="dgram" protocol=17
[   30.233780]audit: type=1400 audit(1426062081.506:54): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=1444 comm="nm-dhcp-client." lport=15728 family="inet6"sock_type="dgram" protocol=17
[   30.276516]audit: type=1400 audit(1426062081.550:55): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=1446 comm="nm-dhcp-client." lport=11647 family="inet"sock_type="dgram" protocol=17
[   30.276532]audit: type=1400 audit(1426062081.550:56): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=1446 comm="nm-dhcp-client." lport=15728 family="inet6"sock_type="dgram" protocol=17
[   34.497267]nf_conntrack: automatic helper assignment is deprecated and it willbe removed soon. Use the iptables CT target to attach helpersinstead.
[   37.516258] init:anacron main process (1123) killed by TERM signal
[   50.965228]audit: type=1400 audit(1426062102.237:57): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=2120comm="apparmor_parser"
[   50.965242]audit: type=1400 audit(1426062102.237:58): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2120 comm="apparmor_parser"
[   50.965819]audit: type=1400 audit(1426062102.237:59): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2120 comm="apparmor_parser"
[  100.810107] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=192.168.0.1 DST=192.168.0.16 LEN=438 TOS=0x00 PREC=0x00 TTL=64ID=0 DF PROTO=UDP SPT=1900 DPT=1901 LEN=418 
[  106.132298] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=216.17.8.4 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=44ID=4591 DF PROTO=TCP SPT=40174 DPT=4242 WINDOW=29200 RES=0x00 SYNURGP=0 
[  107.155635] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=216.17.8.4 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=44ID=4592 DF PROTO=TCP SPT=40174 DPT=4242 WINDOW=29200 RES=0x00 SYNURGP=0 
[  109.100114] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=216.17.8.4 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=44ID=4593 DF PROTO=TCP SPT=40174 DPT=4242 WINDOW=29200 RES=0x00 SYNURGP=0 
[  113.091708] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=216.17.8.4 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=44ID=4594 DF PROTO=TCP SPT=40174 DPT=4242 WINDOW=29200 RES=0x00 SYNURGP=0 
[  121.279424] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=216.17.8.4 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=44ID=4595 DF PROTO=TCP SPT=40174 DPT=4242 WINDOW=29200 RES=0x00 SYNURGP=0 
[  137.143631] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=216.17.8.4 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=44ID=4596 DF PROTO=TCP SPT=40174 DPT=4242 WINDOW=29200 RES=0x00 SYNURGP=0 
[  169.178525] [UFWBLOCK] IN=wlan0 OUT= MAC=00:1f:3c:20:cd:12:68:b6:fc:2d:f5:82:08:00SRC=216.17.8.4 DST=192.168.0.16 LEN=52 TOS=0x00 PREC=0x00 TTL=44ID=4597 DF PROTO=TCP SPT=40174 DPT=4242 WINDOW=29200 RES=0x00 SYNURGP=0 
darren@darren-ThinkPad-R61i:~$  
```

---

### Post by oldfred on 2015-03-11
I think these again are important. 
Does printer work ok? That cups takes that long seems a bit much, but perhaps not a standard printer?

Then wlan or your wireless is repeatedly trying to connect and after a bunch of times, not sure if it worked or gave up. Does it work, is port ok or DHCP and available, or are you not near router and it just has trouble connecting?

---

### Post by darrenllr on 2015-03-11
Thanks OldFred,

Just opened Dash & looked for Printers, clicked that, and there are no printers installed (and I don't use one on this laptop, so that makes sense)

I have noticed that Serial & Parallel are enabled in BIOS - not sure if they're required?  Perhaps that's causing ubuntu to look for whatever cups does.  I won't disable them yet in case I turn off  something important.

Did a quick google search for usr/libs/cups ubuntu, found a thread that gave the terminal command to reinstall cups.  So did that.  Will reboot & check again.

Wifi - I've come across a similar thread that is similar to what happens to my wifi - my laptop always tries to connect to the one in the front room, even if I'm at the back of the building (there's a router in between also).

I'm thinking to just delete all Wifi connections actually.  See if that has any effect.  IPv6 is still disabled as I did that earlier for all connections.

Will reboot first & come back!
Thanks,
Darren.

---

### Post by darrenllr on 2015-03-11
* ( going on the latest output from dmesg sorry - forgot to say) I see a 21 second gap after

init: plymouth......

found this post - [http://ubuntuforums.org/showthread.php?t=2218100](http://ubuntuforums.org/showthread.php?t=2218100)

which describes disabling plymouth I guess.

so am also changing the grub as per the post 

```
[COLOR=#000000]GRUB_CMDLINE_LINUX_DEFAULT="noplymouth"
```

now I'm rebooting.  Honest!!!
Darren.[/COLOR]

---

### Post by darrenllr on 2015-03-11
When looking at Wifi connections - I noticed that all of them were set to 'connect automatically' - so un-checked that box for all of them.

this is the dmesg output now -

```
[    0.674294] ACPI: Power Button [PWRF][    0.676033] Monitor-Mwait will be used to enter C-1 state
[    0.676052] Monitor-Mwait will be used to enter C-2 state
[    0.676068] Monitor-Mwait will be used to enter C-3 state
[    0.676089] ACPI: acpi_idle registered with cpuidle
[    0.678649] thermal LNXTHERM:00: registered as thermal_zone0
[    0.678722] ACPI: Thermal Zone [THM0] (49 C)
[    0.680164] thermal LNXTHERM:01: registered as thermal_zone1
[    0.680228] ACPI: Thermal Zone [THM1] (53 C)
[    0.680334] GHES: HEST is not enabled!
[    0.680588] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    0.684379] Linux agpgart interface v0.103
[    0.687560] brd: module loaded
[    0.689032] loop: module loaded
[    0.689385] ata_piix 0000:00:1f.1: version 2.13
[    0.690530] scsi0 : ata_piix
[    0.690956] scsi1 : ata_piix
[    0.691117] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1830 irq 14
[    0.691218] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1838 irq 15
[    0.691520] libphy: Fixed MDIO Bus: probed
[    0.691605] tun: Universal TUN/TAP device driver, 1.6
[    0.691705] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    0.691898] PPP generic driver version 2.4.2
[    0.691909] ata2: port disabled--ignoring
[    0.692146] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    0.692269] ehci-pci: EHCI PCI platform driver
[    0.692522] ehci-pci 0000:00:1a.7: EHCI Host Controller
[    0.692626] ehci-pci 0000:00:1a.7: new USB bus registered, assigned bus number 1
[    0.695430] ACPI: Battery Slot [BAT0] (battery present)
[    0.696685] ehci-pci 0000:00:1a.7: cache line size of 64 is not supported
[    0.696704] ehci-pci 0000:00:1a.7: irq 22, io mem 0xfe226c00
[    0.712053] ehci-pci 0000:00:1a.7: USB 2.0 started, EHCI 1.00
[    0.712270] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    0.712387] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.712493] usb usb1: Product: EHCI Host Controller
[    0.712591] usb usb1: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    0.712681] usb usb1: SerialNumber: 0000:00:1a.7
[    0.712947] ACPI: Battery Slot [BAT1] (battery present)
[    0.713092] hub 1-0:1.0: USB hub found
[    0.713162] hub 1-0:1.0: 4 ports detected
[    0.713519] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    0.713587] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 2
[    0.713676] ehci-pci 0000:00:1d.7: debug port 1
[    0.717648] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    0.717668] ehci-pci 0000:00:1d.7: irq 19, io mem 0xfe227000
[    0.728044] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    0.728206] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    0.728282] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.728357] usb usb2: Product: EHCI Host Controller
[    0.728420] usb usb2: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    0.728484] usb usb2: SerialNumber: 0000:00:1d.7
[    0.728720] hub 2-0:1.0: USB hub found
[    0.728788] hub 2-0:1.0: 6 ports detected
[    0.729086] ehci-platform: EHCI generic platform driver
[    0.729168] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    0.729236] ohci-pci: OHCI PCI platform driver
[    0.729319] ohci-platform: OHCI generic platform driver
[    0.729394] uhci_hcd: USB Universal Host Controller Interface driver
[    0.729553] uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    0.729621] uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    0.729702] uhci_hcd 0000:00:1a.0: detected 2 ports
[    0.729798] uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    0.730853] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    0.730918] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.730993] usb usb3: Product: UHCI Host Controller
[    0.731056] usb usb3: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    0.731120] usb usb3: SerialNumber: 0000:00:1a.0
[    0.731350] hub 3-0:1.0: USB hub found
[    0.731418] hub 3-0:1.0: 2 ports detected
[    0.731680] uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    0.731748] uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    0.731829] uhci_hcd 0000:00:1a.1: detected 2 ports
[    0.731923] uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    0.732063] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    0.732129] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.732204] usb usb4: Product: UHCI Host Controller
[    0.732267] usb usb4: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    0.732331] usb usb4: SerialNumber: 0000:00:1a.1
[    0.732564] hub 4-0:1.0: USB hub found
[    0.732632] hub 4-0:1.0: 2 ports detected
[    0.732909] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    0.732980] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    0.733061] uhci_hcd 0000:00:1d.0: detected 2 ports
[    0.733154] uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    0.733274] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    0.733340] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.733415] usb usb5: Product: UHCI Host Controller
[    0.733477] usb usb5: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    0.733541] usb usb5: SerialNumber: 0000:00:1d.0
[    0.733764] hub 5-0:1.0: USB hub found
[    0.733834] hub 5-0:1.0: 2 ports detected
[    0.734098] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.734166] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    0.734248] uhci_hcd 0000:00:1d.1: detected 2 ports
[    0.734341] uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    0.734461] usb usb6: New USB device found, idVendor=1d6b, idProduct=0001
[    0.734526] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.734601] usb usb6: Product: UHCI Host Controller
[    0.734664] usb usb6: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    0.734728] usb usb6: SerialNumber: 0000:00:1d.1
[    0.734954] hub 6-0:1.0: USB hub found
[    0.735022] hub 6-0:1.0: 2 ports detected
[    0.735295] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.735363] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    0.735444] uhci_hcd 0000:00:1d.2: detected 2 ports
[    0.735536] uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    0.735656] usb usb7: New USB device found, idVendor=1d6b, idProduct=0001
[    0.735722] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.735797] usb usb7: Product: UHCI Host Controller
[    0.735859] usb usb7: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    0.735923] usb usb7: SerialNumber: 0000:00:1d.2
[    0.736151] hub 7-0:1.0: USB hub found
[    0.736219] hub 7-0:1.0: 2 ports detected
[    0.736500] i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64 irq 1,12
[    0.744534] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.744601] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.744885] mousedev: PS/2 mouse device common for all mice
[    0.745257] rtc_cmos 00:02: RTC can wake from S4
[    0.745518] rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    0.745619] rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.745807] device-mapper: uevent: version 1.0.3
[    0.745986] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    0.746080] ledtrig-cpu: registered to indicate activity on CPUs
[    0.746272] TCP: cubic registered
[    0.746517] NET: Registered protocol family 10
[    0.746881] NET: Registered protocol family 17
[    0.746958] Key type dns_resolver registered
[    0.747440] Loading compiled-in X.509 certificates
[    0.748882] Loaded X.509 cert 'Magrathea: Glacier signing key: 7be2a7200f17f00ca011f70e5a874c37e3e0f6be'
[    0.748981] registered taskstats version 1
[    0.750435] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.752140] Key type trusted registered
[    0.754601] Key type encrypted registered
[    0.757588] AppArmor: AppArmor sha1 policy hashing enabled
[    0.757656] ima: No TPM chip found, activating TPM-bypass!
[    0.757741] evm: HMAC attrs: 0x1
[    0.758411]   Magic number: 7:909:82
[    0.758550] pci 0000:15:00.2: hash matches
[    0.758706] rtc_cmos 00:02: setting system clock to 2015-03-11 15:03:18 UTC (1426086198)
[    0.760925] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.760997] EDD information not available.
[    0.761181] PM: Hibernation image not present or could not be loaded.
[    0.845984] Freeing unused kernel memory: 1356K (ffffffff81d1c000 - ffffffff81e6f000)
[    0.846063] Write protecting the kernel read-only data: 12288k
[    0.848305] Freeing unused kernel memory: 564K (ffff880001773000 - ffff880001800000)
[    0.850292] Freeing unused kernel memory: 500K (ffff880001b83000 - ffff880001c00000)
[    0.865642] systemd-udevd[106]: starting version 204
[    0.883403] pps_core: LinuxPPS API ver. 1 registered
[    0.883473] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    0.888504] PTP clock support registered
[    0.894339] e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    0.894407] e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    0.894727] e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set to dynamic conservative mode
[    0.894841] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[    0.929126] sdhci: Secure Digital Host Controller Interface driver
[    0.929194] sdhci: Copyright(c) Pierre Ossman
[    0.931239] sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[    0.931335] pci 0000:00:1e.0: enabling device (0005 -> 0007)
[    0.932520] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[    0.936556] mmc0: no vqmmc regulator found
[    0.936627] mmc0: no vmmc regulator found
[    0.937690] sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn't fully claim to support it.
[    0.937920] mmc0: SDHCI controller on PCI [0000:15:00.2] using DMA
[    1.000085] firewire_ohci 0000:15:00.1: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.224416] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 00:15:58:84:5a:d6
[    1.224495] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    1.224588] e1000e 0000:00:19.0 eth0: MAC: 6, PHY: 6, PBA No: 1008FF-0FF
[    1.224737] ahci 0000:00:1f.2: version 3.0
[    1.224916] ahci 0000:00:1f.2: irq 47 for MSI/MSI-X
[    1.224980] ahci 0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATA mode
[    1.225058] ahci 0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    1.225848] scsi2 : ahci
[    1.226056] scsi3 : ahci
[    1.226340] scsi4 : ahci
[    1.226488] ata3: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 47
[    1.226566] ata4: DUMMY
[    1.226630] ata5: SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 47
[    1.284092] usb 2-5: new high-speed USB device number 2 using ehci-pci
[    1.427542] usb 2-5: New USB device found, idVendor=17ef, idProduct=1004
[    1.427608] usb 2-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    1.427673] usb 2-5: Product: Integrated Camera
[    1.427735] usb 2-5: Manufacturer: Chicony Electronics Co., Ltd.
[    1.427799] usb 2-5: SerialNumber: SN0001
[    1.500181] firewire_core 0000:15:00.1: created device fw0: GUID 00016c2000bee5ff, S400
[    1.544071] ata5: SATA link down (SStatus 0 SControl 300)
[    1.548070] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.548719] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.548723] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.548799] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.597215] ata3.00: ATA-7: WDC WD1600BEVS-08RST2, 08.01G08, max UDMA/133
[    1.597280] ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.598258] ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    1.598262] ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.598339] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.599311] ata3.00: configured for UDMA/133
[    1.599538] scsi 2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 1G08 PQ: 0 ANSI: 5
[    1.599909] sd 2:0:0:0: Attached scsi generic sg0 type 0
[    1.599912] sd 2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    1.599981] sd 2:0:0:0: [sda] Write Protect is off
[    1.599983] sd 2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.600017] sd 2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.641741]  sda: sda1 sda2 < sda5 >
[    1.642328] sd 2:0:0:0: [sda] Attached SCSI disk
[    1.668089] usb 3-1: new full-speed USB device number 2 using uhci_hcd
[    1.679236] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x81a0b1, caps: 0xa04791/0x300000/0x0, board id: 71, fw id: 496542
[    1.679322] psmouse serio1: synaptics: serio: Synaptics pass-through port at isa0060/serio1/input0
[    1.724913] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input5
[    1.835862] usb 3-1: New USB device found, idVendor=0a5c, idProduct=2110
[    1.835932] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.836012] usb 3-1: Product: BCM2045B
[    1.836078] usb 3-1: Manufacturer: Broadcom Corp
[    1.976810] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.932096] floppy0: no floppy controllers found
[    4.746640] random: nonblocking pool is initialized
[    5.015993] psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 00 64
[    6.497140] psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons: 3/3
[    6.728848] input: TPPS/2 IBM TrackPoint as /devices/platform/i8042/serio1/serio2/input/input6
[   14.421601] Adding 4125692k swap on /dev/sda5.  Priority:-1 extents:1 across:4125692k FS
[   14.799451] systemd-udevd[286]: starting version 204
[   14.975389] lp: driver loaded but no devices found
[   14.988447] ppdev: user-space parallel port driver
[   15.033911] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   15.039620] acpi device:06: registered as cooling_device2
[   15.039789] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   15.103975] Non-volatile memory driver v1.3
[   15.105925] wmi: Mapper loaded
[   15.108537] thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   15.108541] thinkpad_acpi: http://ibm-acpi.sf.net/
[   15.108543] thinkpad_acpi: ThinkPad BIOS 7LETD0WW (2.30 ), EC 7KHT24WW-1.08
[   15.108545] thinkpad_acpi: Lenovo ThinkPad T61, model 7742B6V
[   15.110378] thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   15.126475] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   15.131556] thinkpad_acpi: ACPI backlight control delay disabled
[   15.133459] thinkpad_acpi: radio switch found; radios are enabled
[   15.133487] thinkpad_acpi: This ThinkPad has standard ACPI backlight brightness control, supported by the ACPI video driver
[   15.133489] thinkpad_acpi: Disabling thinkpad-acpi brightness events by default...
[   15.137958] thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   15.143139] thinkpad_acpi: Standard ACPI backlight interface available, not loading native one
[   15.143384] thinkpad_acpi: Console audio control enabled, mode: monitor (read only)
[   15.147286] input: ThinkPad Extra Buttons as /devices/platform/thinkpad_acpi/input/input8
[   15.155910] [drm] Initialized drm 1.1.0 20060810
[   15.156309] cfg80211: Calling CRDA to update world regulatory domain
[   15.186393] yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   15.216184] ACPI Warning: SystemIO range 0x0000000000001028-0x000000000000102f conflicts with OpRegion 0x0000000000001000-0x000000000000107f (\_SB_.PCI0.LPC_.PMIO) (20140424/utaddress-258)
[   15.216194] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.216198] ACPI Warning: SystemIO range 0x00000000000011b0-0x00000000000011bf conflicts with OpRegion 0x0000000000001180-0x00000000000011bf (\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   15.216203] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.216205] ACPI Warning: SystemIO range 0x0000000000001180-0x00000000000011af conflicts with OpRegion 0x0000000000001180-0x00000000000011bf (\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   15.216210] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   15.216211] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   15.249064] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   15.249070] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   15.249191] iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPM control
[   15.253632] snd_hda_intel 0000:00:1b.0: probe_mask set to 0x1 for device 17aa:20ac
[   15.253680] snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   15.256821] Bluetooth: Core ver 2.19
[   15.256865] NET: Registered protocol family 31
[   15.256867] Bluetooth: HCI device and connection manager initialized
[   15.256878] Bluetooth: HCI socket layer initialized
[   15.256881] Bluetooth: L2CAP socket layer initialized
[   15.256894] Bluetooth: SCO socket layer initialized
[   15.265987] ip_tables: (C) 2000-2006 Netfilter Core Team
[   15.287914] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   15.304768] iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   15.304774] iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   15.304848] iwl3945 0000:03:00.0: irq 49 for MSI/MSI-X
[   15.310824] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   15.316666] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   15.324731] yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   15.324738] yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   15.324747] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [io  0x8000-0xbfff]
[   15.324750] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xf8100000-0xfbffffff]
[   15.324753] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf8100000-0xfbffffff:
[   15.324759]  excluding 0xf8100000-0xf84effff
[   15.324770] yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem 0xf4000000-0xf7ffffff 64bit pref]
[   15.324773] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf4000000-0xf7ffffff:
[   15.324777]  excluding 0xf4000000-0xf7ffffff
[   15.334409] r592: driver successfully loaded
[   15.335167] r852: driver loaded successfully
[   15.340626] usbcore: registered new interface driver btusb
[   15.412381] media: Linux media interface: v0.10
[   15.423608] Linux video capture interface: v2.00
[   15.444186] uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:1004)
[   15.452805] input: Integrated Camera as /devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   15.453709] usbcore: registered new interface driver uvcvideo
[   15.453714] USB Video Class driver (1.1.1)
[   15.678060] sound hdaudioC0D0: autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0) type:speaker
[   15.678065] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   15.678068] sound hdaudioC0D0:    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   15.678071] sound hdaudioC0D0:    mono: mono_out=0x0
[   15.678073] sound hdaudioC0D0:    dig-out=0x1b/0x0
[   15.678076] sound hdaudioC0D0:    inputs:
[   15.678079] sound hdaudioC0D0:      Internal Mic=0x15
[   15.678082] sound hdaudioC0D0:      Dock Mic=0x1c
[   15.678085] sound hdaudioC0D0:      Mic=0x14
[   15.692608] input: HDA Intel Dock Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   15.693371] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   15.693513] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   15.720067] audit: type=1400 audit(1426086213.458:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=447 comm="apparmor_parser"
[   15.720077] audit: type=1400 audit(1426086213.458:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=447 comm="apparmor_parser"
[   15.720083] audit: type=1400 audit(1426086213.458:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=447 comm="apparmor_parser"
[   15.720103] audit: type=1400 audit(1426086213.458:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=357 comm="apparmor_parser"
[   15.720112] audit: type=1400 audit(1426086213.458:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=357 comm="apparmor_parser"
[   15.720118] audit: type=1400 audit(1426086213.458:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=357 comm="apparmor_parser"
[   15.720642] audit: type=1400 audit(1426086213.458:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=447 comm="apparmor_parser"
[   15.720649] audit: type=1400 audit(1426086213.458:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=447 comm="apparmor_parser"
[   15.720674] audit: type=1400 audit(1426086213.458:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=357 comm="apparmor_parser"
[   15.720681] audit: type=1400 audit(1426086213.458:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=357 comm="apparmor_parser"
[   16.077869] cfg80211: World regulatory domain updated:
[   16.077873] cfg80211:  DFS Master region: unset
[   16.077876] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   16.077879] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   16.077882] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   16.077885] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   16.077887] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   16.077890] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   16.169566] nvidia: module license 'NVIDIA' taints kernel.
[   16.169571] Disabling lock debugging due to kernel taint
[   16.184984] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[   16.193350] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[   16.193897] [drm] Initialized nvidia-drm 0.0.0 20130102 for 0000:01:00.0 on minor 0
[   16.193911] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  331.113  Mon Dec  1 21:08:13 PST 2014
[   16.225618] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   16.225627]  excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   16.225653] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   16.225663]  excluding 0xa0000000-0xa0ffffff
[   16.225680] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   16.225689]  excluding 0x60000000-0x60ffffff
[   16.858364] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.604332] init: failsafe main process (658) killed by TERM signal
[   18.068084] floppy0: no floppy controllers found
[   19.075376] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.075382] Bluetooth: BNEP filters: protocol multicast
[   19.075395] Bluetooth: BNEP socket layer initialized
[   19.081369] Bluetooth: RFCOMM TTY layer initialized
[   19.081385] Bluetooth: RFCOMM socket layer initialized
[   19.081393] Bluetooth: RFCOMM ver 1.11
[   19.818634] init: cups main process (720) killed by HUP signal
[   19.818651] init: cups main process ended, respawning
[   21.036295] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   21.068193] audit_printk_skb: 120 callbacks suppressed
[   21.068198] audit: type=1400 audit(1426086218.806:52): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1060 comm="apparmor_parser"
[   21.140124] e1000e 0000:00:19.0: irq 46 for MSI/MSI-X
[   21.140278] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   21.304206] iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   21.374978] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   21.619541] thinkpad_ec: thinkpad_ec 0.41 loaded.
[   21.619906] tp_smapi 0.41 loading...
[   21.620294] tp_smapi successfully loaded (smapi_port=0xb2).
[   21.932359] init: samba-ad-dc main process (982) terminated with status 1
[   22.369280] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.369408] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.369518] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.369629] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.369741] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.369847] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.504771] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.504902] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.505013] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.505121] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.505229] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   22.505337] acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.000839] nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
[   28.471214] init: plymouth-upstart-bridge main process ended, respawning
[   48.578432] audit: type=1400 audit(1426086246.315:53): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1835 comm="apparmor_parser"
[   48.578446] audit: type=1400 audit(1426086246.315:54): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1835 comm="apparmor_parser"
[   48.579008] audit: type=1400 audit(1426086246.315:55): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1835 comm="apparmor_parser"
[   79.785585] wlan0: authenticate with 00:26:18:c5:ad:9c
[   79.787132] wlan0: send auth to 00:26:18:c5:ad:9c (try 1/3)
[   79.788936] wlan0: authenticated
[   79.792479] wlan0: associate with 00:26:18:c5:ad:9c (try 1/3)
[   79.795290] wlan0: RX AssocResp from 00:26:18:c5:ad:9c (capab=0x411 status=0 aid=2)
[   79.797007] wlan0: associated
[   79.797048] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.482883] audit: type=1400 audit(1426086278.219:56): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2224 comm="nm-dhcp-client." lport=1374 family="inet" sock_type="dgram" protocol=17
[   80.482898] audit: type=1400 audit(1426086278.219:57): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2224 comm="nm-dhcp-client." lport=41994 family="inet6" sock_type="dgram" protocol=17
[   80.507203] audit: type=1400 audit(1426086278.243:58): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2225 comm="nm-dhcp-client." lport=1374 family="inet" sock_type="dgram" protocol=17
[   80.507217] audit: type=1400 audit(1426086278.243:59): apparmor="DENIED" operation="file_inherit" profile="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=2225 comm="nm-dhcp-client." lport=41994 family="inet6" sock_type="dgram" protocol=17
darren@darren-ThinkPad-R61i:~$ 

```

So far, a bit of an improvement over 135 up to 180 seconds.

Down to 80.

Still something going on around 28 seconds that takes a while:

```
[   28.471214] init:plymouth-upstart-bridge main process ended, respawning
[   48.578432]audit: type=1400 audit(1426086246.315:53): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=1835comm="apparmor_parser" 
```

and then at 48 seconds

```
[   48.579008]audit: type=1400 audit(1426086246.315:55): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=1835 comm="apparmor_parser" 
```

nothing then till 79 seconds.

and about 10 acpi_calls still - I'll try to get a photo of something I've seen in BIOS - - a bunch of bios entries that are similar to each other, but ending with a, b, c and so on.  Might tally up with the number of acpi_call: entries in dmesg.

I'll report back anything else I find tomorrow, 

Thanks again
Darren.

---

### Post by oldfred on 2015-03-11
Have not used a parallel port for ages. I might at least experiment with turning that off.
You may need serial as that can go thru USB, not sure if separate now or not?

---

### Post by darrenllr on 2015-03-12
Okay, so - 

I disabled Parallel in BIOS.  Nothing has blown up yet as far as I can tell.

Tried reinstalling cups - nothing seems to have changed there.

Tried reinstalling nvidia drivers - I get warnings about 'held packages' - still under investigation ;-)

The 3 main things that I see now are:

12 acpi_calls not found
Gap from 28 seconds to 53 seconds - maybe plymouth issue
Gap from 53 seconds to 82 seconds - 

I'll try and figure it out.....any tips would be great ;-)

```
[   25.191692]acpi_call: Cannot get handle: Error: AE_NOT_FOUND 
```
 
```
[   28.539356] init:plymouth-upstart-bridge main process ended, respawning
[   53.074906]audit: type=1400 audit(1426134898.945:47): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=2038comm="apparmor_parser" 
```
   
```
[   53.074920]audit: type=1400 audit(1426134898.945:48): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2038 comm="apparmor_parser"[   53.075479]audit: type=1400 audit(1426134898.945:49): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2038 comm="apparmor_parser"
[   82.552951]wlan0: authenticate with 36:8f:c6:b0:10:f8 
```

and the full output from dmesg - 

```
[    1.354642] usbusb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1[    1.378583] usbusb2: Product: EHCI Host Controller
[    1.402142] usbusb2: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    1.425734] usbusb2: SerialNumber: 0000:00:1d.7
[    1.449217] hub2-0:1.0: USB hub found
[    1.472456] hub2-0:1.0: 6 ports detected
[    1.495410]ehci-platform: EHCI generic platform driver
[    1.517930]ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.540263]ohci-pci: OHCI PCI platform driver
[    1.562149]ohci-platform: OHCI generic platform driver
[    1.583823]uhci_hcd: USB Universal Host Controller Interface driver
[    1.605568]uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.627098]uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.648786]uhci_hcd 0000:00:1a.0: detected 2 ports
[    1.670176]uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    1.691490] usbusb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.713178] usbusb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.734844] usbusb3: Product: UHCI Host Controller
[    1.756258] usbusb3: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    1.777976] usbusb3: SerialNumber: 0000:00:1a.0
[    1.799866] hub3-0:1.0: USB hub found
[    1.821669] hub3-0:1.0: 2 ports detected
[    1.843842]uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.865830]uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.888365]uhci_hcd 0000:00:1a.1: detected 2 ports
[    1.910504]uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    1.932666] usbusb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.955003] usbusb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.977289] usbusb4: Product: UHCI Host Controller
[    1.988043] usb2-5: new high-speed USB device number 2 using ehci-pci
[    2.021838] usbusb4: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    2.044371] usbusb4: SerialNumber: 0000:00:1a.1
[    2.066726] hub4-0:1.0: USB hub found
[    2.088796] hub4-0:1.0: 2 ports detected
[    2.110770]uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    2.132861]uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    2.155053]uhci_hcd 0000:00:1d.0: detected 2 ports
[    2.176980]uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    2.198789] usbusb5: New USB device found, idVendor=1d6b, idProduct=0001
[    2.220881] usbusb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.243020] usbusb5: Product: UHCI Host Controller
[    2.265039] usbusb5: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    2.266210] usb2-5: New USB device found, idVendor=17ef, idProduct=1004
[    2.266212] usb2-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.266213] usb2-5: Product: Integrated Camera
[    2.266215] usb2-5: Manufacturer: Chicony Electronics Co., Ltd.
[    2.266216] usb2-5: SerialNumber: SN0001
[    2.400058] usbusb5: SerialNumber: 0000:00:1d.0
[    2.422589] hub5-0:1.0: USB hub found
[    2.444585] hub5-0:1.0: 2 ports detected
[    2.466552]uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    2.488263]uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    2.510145]uhci_hcd 0000:00:1d.1: detected 2 ports
[    2.531722]uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    2.553343] usbusb6: New USB device found, idVendor=1d6b, idProduct=0001
[    2.575434] usbusb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.575462] usb3-1: new full-speed USB device number 2 using uhci_hcd
[    2.619746] usbusb6: Product: UHCI Host Controller
[    2.641843] usbusb6: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    2.664130] usbusb6: SerialNumber: 0000:00:1d.1
[    2.686287] hub6-0:1.0: USB hub found
[    2.708075] hub6-0:1.0: 2 ports detected
[    2.729908]uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    2.751670]uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    2.773798]uhci_hcd 0000:00:1d.2: detected 2 ports
[    2.795503]uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    2.817173] usbusb7: New USB device found, idVendor=1d6b, idProduct=0001
[    2.838934] usbusb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    2.860709] usbusb7: Product: UHCI Host Controller
[    2.882419] usbusb7: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    2.882487] usb3-1: New USB device found, idVendor=0a5c, idProduct=2110
[    2.882489] usb3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.882491] usb3-1: Product: BCM2045B
[    2.882492] usb3-1: Manufacturer: Broadcom Corp
[    2.992986] usbusb7: SerialNumber: 0000:00:1d.2
[    3.015190] hub7-0:1.0: USB hub found
[    3.036910] hub7-0:1.0: 2 ports detected
[    3.058623]i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64irq 1,12
[    3.093771]serio: i8042 KBD port at 0x60,0x64 irq 1
[    3.115662]serio: i8042 AUX port at 0x60,0x64 irq 12
[    3.137307]mousedev: PS/2 mouse device common for all mice
[    3.159178]rtc_cmos 00:02: RTC can wake from S4
[    3.180938]rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    3.202849]rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpetirqs
[    3.225086]device-mapper: uevent: version 1.0.3
[    3.247244]device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised:dm-devel@redhat.com
[    3.269932]ledtrig-cpu: registered to indicate activity on CPUs
[    3.292834]input: AT Translated Set 2 keyboard as/devices/platform/i8042/serio0/input/input3
[    3.316250] TCP:cubic registered
[    3.339498] NET:Registered protocol family 10
[    3.362755] NET:Registered protocol family 17
[    3.385353] Keytype dns_resolver registered
[    3.408040]Loading compiled-in X.509 certificates
[    3.431807]Loaded X.509 cert 'Magrathea: Glacier signing key:7be2a7200f17f00ca011f70e5a874c37e3e0f6be'
[    3.455079]registered taskstats version 1
[    3.481023] Keytype trusted registered
[    3.506437] Keytype encrypted registered
[    3.531749]AppArmor: AppArmor sha1 policy hashing enabled
[    3.555004] ima:No TPM chip found, activating TPM-bypass!
[    3.578547] evm:HMAC attrs: 0x1
[    3.602460]  Magic number: 7:333:565
[    3.625865]rtc_cmos 00:02: setting system clock to 2015-03-12 04:34:09 UTC(1426134849)
[    3.651876] BIOSEDD facility v0.16 2004-Jun-25, 0 devices found
[    3.676069] EDDinformation not available.
[    3.699979] PM:Hibernation image not present or could not be loaded.
[    3.701795]Freeing unused kernel memory: 1356K (ffffffff81d1c000 -ffffffff81e6f000)
[    3.726264] Writeprotecting the kernel read-only data: 12288k
[    3.752781]Freeing unused kernel memory: 564K (ffff880001773000 -ffff880001800000)
[    3.779395]Freeing unused kernel memory: 500K (ffff880001b83000 -ffff880001c00000)
[    3.843256]systemd-udevd[107]: starting version 204
[    3.899283]pps_core: LinuxPPS API ver. 1 registered
[    3.899284]pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti<giometti@linux.it>
[    3.901155] PTPclock support registered
[    3.991510]sdhci: Secure Digital Host Controller Interface driver
[    4.017389]sdhci: Copyright(c) Pierre Ossman
[    4.045543] ahci0000:00:1f.2: version 3.0
[    4.045722] ahci0000:00:1f.2: irq 46 for MSI/MSI-X
[    4.045794] ahci0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATAmode
[    4.045797] ahci0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    4.058829] scsi2: ahci
[    4.058991] pci0000:00:1e.0: enabling device (0005 -> 0007)
[    4.060798]e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    4.060799]e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    4.072036] scsi3: ahci
[    4.123616]firewire_ohci 0000:15:00.1: added OHCI v1.10 device as card 0, 4 IR +4 IT contexts, quirks 0x11
[    4.202059]sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[    4.203173]sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn'tfully claim to support it.
[    4.203184] mmc0:no vqmmc regulator found
[    4.203185] mmc0:no vmmc regulator found
[    4.204185]sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn'tfully claim to support it.
[    4.204439] mmc0:SDHCI controller on PCI [0000:15:00.2] using DMA
[    4.232084] scsi4: ahci
[    4.232181] ata3:SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 46
[    4.232182] ata4:DUMMY
[    4.232185] ata5:SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 46
[    4.232396]e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set todynamic conservative mode
[    4.232425]e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[    4.588614] ata3:SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.589192] ata5:SATA link down (SStatus 0 SControl 300)
[    4.617132]ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    4.617135]ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK)filtered out
[    4.617137]ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.715792]ata3.00: ATA-7: WDC WD1600BEVS-08RST2, 08.01G08, max UDMA/133
[    4.715794]ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.716655]ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    4.716657]ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK)filtered out
[    4.716659]ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.717490]ata3.00: configured for UDMA/133
[    4.717635] scsi2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 1G08 PQ: 0 ANSI:5
[    4.717948] sd2:0:0:0: Attached scsi generic sg0 type 0
[    4.717975] sd2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    4.718072] sd2:0:0:0: [sda] Write Protect is off
[    4.718075] sd2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.718108] sd2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn'tsupport DPO or FUA
[    4.802940]  sda:sda1 sda2 < sda5 >
[    4.803315] sd2:0:0:0: [sda] Attached SCSI disk
[    4.894651]e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1)00:15:58:84:5a:d6
[    4.894653]e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    4.894680]e1000e 0000:00:19.0 eth0: MAC: 6, PHY: 6, PBA No: 1008FF-0FF
[    5.096952]firewire_core 0000:15:00.1: created device fw0: GUID00016c2000bee5ff, S400
[    5.493928]psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x81a0b1,caps: 0xa04791/0x300000/0x0, board id: 71, fw id: 496542
[    5.499356]EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts:(null)
[    5.555912]psmouse serio1: synaptics: serio: Synaptics pass-through port atisa0060/serio1/input0
[    5.633046]input: SynPS/2 Synaptics TouchPad as/devices/platform/i8042/serio1/input/input5
[    6.908106]floppy0: no floppy controllers found
[    7.588027]random: nonblocking pool is initialized
[    9.035245]psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 0064
[   10.550373]psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons:3/3
[   10.814802]input: TPPS/2 IBM TrackPoint as/devices/platform/i8042/serio1/serio2/input/input6
[   17.211147]Adding 4125692k swap on /dev/sda5.  Priority:-1 extents:1across:4125692k FS
[   17.566606]systemd-udevd[279]: starting version 204
[   17.729367] lp:driver loaded but no devices found
[   17.740782]ppdev: user-space parallel port driver
[   17.760614]shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.816179] ACPI:Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.819318] acpidevice:06: registered as cooling_device2
[   17.819429]input: Video Bus as/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   17.855029]Non-volatile memory driver v1.3
[   17.859315]thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   17.859318]thinkpad_acpi: http://ibm-acpi.sf.net/
[   17.859320]thinkpad_acpi: ThinkPad BIOS 7LETD0WW (2.30 ), EC 7KHT24WW-1.08
[   17.859322]thinkpad_acpi: Lenovo ThinkPad T61, model 7742B6V
[   17.863098]thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   17.864430]thinkpad_acpi: ACPI backlight control delay disabled
[   17.866358]thinkpad_acpi: radio switch found; radios are enabled
[   17.866387]thinkpad_acpi: This ThinkPad has standard ACPI backlight brightnesscontrol, supported by the ACPI video driver
[   17.866388]thinkpad_acpi: Disabling thinkpad-acpi brightness events bydefault...
[   17.882972] wmi:Mapper loaded
[   17.906822]thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   17.915306]ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.916853]snd_hda_intel 0000:00:1b.0: probe_mask set to 0x1 for device17aa:20ac
[   17.916916]snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   17.920127]cfg80211: Calling CRDA to update world regulatory domain
[   17.933050]nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   17.946637]thinkpad_acpi: Standard ACPI backlight interface available, notloading native one
[   17.946866]thinkpad_acpi: Console audio control enabled, mode: monitor (readonly)
[   17.948076]input: ThinkPad Extra Buttons as/devices/platform/thinkpad_acpi/input/input8
[   17.952381] [drm]Initialized drm 1.1.0 20060810
[   17.963964]iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driverfor Linux, in-tree:s
[   17.963969]iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   17.964111]iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPMcontrol
[   17.985281]Bluetooth: Core ver 2.19
[   17.985302] NET:Registered protocol family 31
[   17.985304]Bluetooth: HCI device and connection manager initialized
[   17.985315]Bluetooth: HCI socket layer initialized
[   17.985318]Bluetooth: L2CAP socket layer initialized
[   17.985331]Bluetooth: SCO socket layer initialized
[   18.012984] ACPIWarning: SystemIO range 0x0000000000001028-0x000000000000102fconflicts with OpRegion 0x0000000000001000-0x000000000000107f(\_SB_.PCI0.LPC_.PMIO) (20140424/utaddress-258)
[   18.012993] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   18.012997] ACPIWarning: SystemIO range 0x00000000000011b0-0x00000000000011bfconflicts with OpRegion 0x0000000000001180-0x00000000000011bf(\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   18.013002] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   18.013004] ACPIWarning: SystemIO range 0x0000000000001180-0x00000000000011afconflicts with OpRegion 0x0000000000001180-0x00000000000011bf(\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   18.013009] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   18.013011]lpc_ich: Resource conflict(s) found affecting gpio_ich
[   18.029515]ip6_tables: (C) 2000-2006 Netfilter Core Team
[   18.029758]audit: type=1400 audit(1426134863.901:2): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/sbin/dhclient" pid=338 comm="apparmor_parser"
[   18.029766]audit: type=1400 audit(1426134863.901:3): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=338 comm="apparmor_parser"
[   18.029773]audit: type=1400 audit(1426134863.901:4): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=338comm="apparmor_parser"
[   18.030329]audit: type=1400 audit(1426134863.901:5): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=338 comm="apparmor_parser"
[   18.030337]audit: type=1400 audit(1426134863.901:6): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=338comm="apparmor_parser"
[   18.030622]audit: type=1400 audit(1426134863.901:7): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=338comm="apparmor_parser"
[   18.037300]iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11achannels
[   18.037305]iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   18.037379]iwl3945 0000:03:00.0: irq 49 for MSI/MSI-X
[   18.056288] r592:driver successfully loaded
[   18.057797]yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   18.061405]ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   18.079047]usbcore: registered new interface driver btusb
[   18.190656]yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   18.190663]yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   18.190720]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [io 0x8000-0xbfff]
[   18.190724]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem0xf8100000-0xfbffffff]
[   18.190727]pcmcia_socket pcmcia_socket0: cs: memory probe0xf8100000-0xfbffffff:
[   18.190733] excluding 0xf8100000-0xf84effff
[   18.190743]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem0xf4000000-0xf7ffffff 64bit pref]
[   18.190746]pcmcia_socket pcmcia_socket0: cs: memory probe0xf4000000-0xf7ffffff:
[   18.190751] excluding 0xf4000000-0xf7ffffff
[   18.207561] r852:driver loaded successfully
[   18.315495] soundhdaudioC0D0: autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0)type:speaker
[   18.315498] soundhdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.315500] soundhdaudioC0D0:    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   18.315501] soundhdaudioC0D0:    mono: mono_out=0x0
[   18.315503] soundhdaudioC0D0:    dig-out=0x1b/0x0
[   18.315504] soundhdaudioC0D0:    inputs:
[   18.315506] soundhdaudioC0D0:      Internal Mic=0x15
[   18.315508] soundhdaudioC0D0:      Dock Mic=0x1c
[   18.315510] soundhdaudioC0D0:      Mic=0x14
[   18.322218]input: HDA Intel Dock Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   18.322322]input: HDA Intel Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.322419]input: HDA Intel Front Headphone as/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.415720]checking generic (d5000000 3f0000) vs hw (e0000000 10000000)
[   18.415725]checking generic (d5000000 3f0000) vs hw (d4000000 2000000)
[   18.415727] fb:switching to nouveaufb from VESA VGA
[   18.415791]Console: switching to colour dummy device 80x25
[   18.436153]nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x086900a2
[   18.436158]nouveau  [  DEVICE][0000:01:00.0] Chipset: G86 (NV86)
[   18.436161]nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[   18.436207]nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   18.500188]nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   18.500193]nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[   18.500325]nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   18.500330]nouveau  [   VBIOS][0000:01:00.0] version 60.86.3e.00.00
[   18.521728]nouveau 0000:01:00.0: irq 50 for MSI/MSI-X
[   18.521750]nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[   18.521794]nouveau  [     PFB][0000:01:00.0] RAM type: GDDR3
[   18.521797]nouveau  [     PFB][0000:01:00.0] RAM size: 128 MiB
[   18.521799]nouveau  [     PFB][0000:01:00.0]    ZCOMP: 646 tags
[   18.524142]nouveau  [    VOLT][0000:01:00.0] GPU voltage: 1150000uv
[   18.559775]media: Linux media interface: v0.10
[   18.580534] Linuxvideo capture interface: v2.00
[   18.704174]uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:1004)
[   18.712959]input: Integrated Camera as/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input12
[   18.713083]usbcore: registered new interface driver uvcvideo
[   18.713085] USBVideo Class driver (1.1.1)
[   18.759770]pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   18.759781] excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   18.759808]pcmcia_socket pcmcia_socket0: cs: memory probe0xa0000000-0xa0ffffff:
[   18.759817] excluding 0xa0000000-0xa0ffffff
[   18.759835]pcmcia_socket pcmcia_socket0: cs: memory probe0x60000000-0x60ffffff:
[   18.759845] excluding 0x60000000-0x60ffffff
[   18.761601]nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[   18.761617]nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
[   18.761620]nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[   18.761660]nouveau  [     CLK][0000:01:00.0] 20: core 169 MHz shader 338 MHzmemory 100 MHz
[   18.761665]nouveau  [     CLK][0000:01:00.0] 21: core 275 MHz shader 550 MHzmemory 301 MHz
[   18.761669]nouveau  [     CLK][0000:01:00.0] 22: core 400 MHz shader 800 MHzmemory 600 MHz
[   18.761704]nouveau  [     CLK][0000:01:00.0] --: core 275 MHz shader 550 MHzmemory 302 MHz
[   18.762025] [TTM]Zone  kernel: Available graphics memory: 1990576 kiB
[   18.762028] [TTM]Initializing pool allocator
[   18.762036] [TTM]Initializing DMA pool allocator
[   18.762053]nouveau  [     DRM] VRAM: 128 MiB
[   18.762055]nouveau  [     DRM] GART: 1048576 MiB
[   18.762060]nouveau  [     DRM] TMDS table version 2.0
[   18.762063]nouveau  [     DRM] DCB version 4.0
[   18.762066]nouveau  [     DRM] DCB outp 00: 01000323 00010034
[   18.762069]nouveau  [     DRM] DCB outp 01: 02811300 00000028
[   18.762072]nouveau  [     DRM] DCB outp 02: 02822312 00010030
[   18.762074]nouveau  [     DRM] DCB outp 03: 014333f1 0080c080
[   18.762076]nouveau  [     DRM] DCB conn 00: 0040
[   18.762079]nouveau  [     DRM] DCB conn 01: 0100
[   18.762082]nouveau  [     DRM] DCB conn 02: 1231
[   18.762084]nouveau  [     DRM] DCB conn 03: 0311
[   18.783978]nouveau W[     DRM] failed to create encoder 0/1/0: -19
[   18.783982]nouveau W[     DRM] TV-1 has no encoders, removing
[   18.784327] [drm]Supports vblank timestamp caching Rev 2 (21.10.2013).
[   18.784329] [drm]Driver supports precise vblank timestamp query.
[   18.808823]nouveau  [     DRM] MM: using CRYPT for buffer copies
[   18.883995]cfg80211: World regulatory domain updated:
[   18.884018]cfg80211:  DFS Master region: unset
[   18.884020]cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain,max_eirp), (dfs_cac_time)
[   18.884024]cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.884027]cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.884029]cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.884032]cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.884035]cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   19.614351]EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   20.152587]nouveau  [     DRM] allocated 1440x900 fb: 0x60000, boffff8800b8cd7800
[   20.153307]fbcon: nouveaufb (fb0) is primary device
[   20.236230]Console: switching to colour frame buffer device 180x56
[   20.237953]nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[   20.237955]nouveau 0000:01:00.0: registered panic notifier
[   20.256046] [drm]Initialized nouveau 1.1.2 20120801 for 0000:01:00.0 on minor 0
[   20.386611] init:failsafe main process (653) killed by TERM signal
[   20.860174]floppy0: no floppy controllers found
[   20.860191] workstill pending
[   21.766101]Bluetooth: RFCOMM TTY layer initialized
[   21.766118]Bluetooth: RFCOMM socket layer initialized
[   21.766127]Bluetooth: RFCOMM ver 1.11
[   21.820498]Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   21.820502]Bluetooth: BNEP filters: protocol multicast
[   21.820516]Bluetooth: BNEP socket layer initialized
[   22.000283]audit: type=1400 audit(1426134867.873:8): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=852comm="apparmor_parser"
[   22.000295]audit: type=1400 audit(1426134867.873:9): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/sbin/cupsd" pid=852 comm="apparmor_parser"
[   22.000855]audit: type=1400 audit(1426134867.873:10): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=852 comm="apparmor_parser"
[   22.291991]audit: type=1400 audit(1426134868.161:11): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/sbin/dhclient" pid=859 comm="apparmor_parser"
[   22.948274] init:cups main process (856) killed by HUP signal
[   22.948290] init:cups main process ended, respawning
[   23.227807] init:samba-ad-dc main process (880) terminated with status 1
[   23.966108]audit_printk_skb: 102 callbacks suppressed
[   23.966113]audit: type=1400 audit(1426134869.837:46): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cups-browsed" pid=1050comm="apparmor_parser"
[   24.259813]e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   24.360157]e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   24.360337] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.393631]iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   24.461935] IPv6:ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   24.470256]acpi_call: module verification failed: signature and/or  required keymissing - tainting kernel
[   24.482286]thinkpad_ec: thinkpad_ec 0.41 loaded.
[   24.482793]tp_smapi 0.41 loading...
[   24.483039]tp_smapi successfully loaded (smapi_port=0xb2).
[   25.191692]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.192243]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.192575]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.192921]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.193600]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.194272]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.325825]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.326208]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.326537]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.326950]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.327573]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.328235]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   28.539356] init:plymouth-upstart-bridge main process ended, respawning
[   53.074906]audit: type=1400 audit(1426134898.945:47): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=2038comm="apparmor_parser"
[   53.074920]audit: type=1400 audit(1426134898.945:48): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2038 comm="apparmor_parser"
[   53.075479]audit: type=1400 audit(1426134898.945:49): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2038 comm="apparmor_parser"
[   82.552951]wlan0: authenticate with 36:8f:c6:b0:10:f8
[   82.557987]wlan0: send auth to 36:8f:c6:b0:10:f8 (try 1/3)
[   82.559061]wlan0: authenticated
[   82.560875]wlan0: associate with 36:8f:c6:b0:10:f8 (try 1/3)
[   82.562826]wlan0: RX AssocResp from 36:8f:c6:b0:10:f8 (capab=0x431 status=0aid=1)
[   82.564098]wlan0: associated
[   82.564134] IPv6:ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   83.305740]audit: type=1400 audit(1426134929.177:50): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2225 comm="nm-dhcp-client." lport=45847 family="inet"sock_type="dgram" protocol=17
[   83.305756]audit: type=1400 audit(1426134929.177:51): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2225 comm="nm-dhcp-client." lport=56941 family="inet6"sock_type="dgram" protocol=17
[   83.343605]audit: type=1400 audit(1426134929.213:52): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2226 comm="nm-dhcp-client." lport=45847 family="inet"sock_type="dgram" protocol=17
[   83.343620]audit: type=1400 audit(1426134929.213:53): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2226 comm="nm-dhcp-client." lport=56941 family="inet6"sock_type="dgram" protocol=17
[   86.518248]nf_conntrack: automatic helper assignment is deprecated and it willbe removed soon. Use the iptables CT target to attach helpersinstead.
darren@darren-ThinkPad-R61i:~$  
```

---

### Post by darrenllr on 2015-03-12
Okay, 

I've plateaud ;-)

Added a 'sleep 2' line to [COLOR=#333333][FONT=Noto Serif]/etc/init/plymouth-upstart-bridge.conf, [/FONT][/COLOR]as per this thread [http://www.unrelatedshit.com/2014/07/30/kvm-too-fast-for-plymouth-upstart-bridge/](http://www.unrelatedshit.com/2014/07/30/kvm-too-fast-for-plymouth-upstart-bridge/)

Stumped with the last 2 big gaps between

25 seconds to 53 seconds

53 seconds to 80 seconds.

Thanks OldFred & Tripp98 for the pointers.  Here's the latest dmesg output if anything strikes you?:

```
[    1.302232]ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00[    1.326001] usbusb2: New USB device found, idVendor=1d6b, idProduct=0002
[    1.350055] usbusb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.374031] usbusb2: Product: EHCI Host Controller
[    1.397610] usbusb2: Manufacturer: Linux 3.16.0-30-generic ehci_hcd
[    1.421212] usbusb2: SerialNumber: 0000:00:1d.7
[    1.444697] hub2-0:1.0: USB hub found
[    1.467957] hub2-0:1.0: 6 ports detected
[    1.490883]ehci-platform: EHCI generic platform driver
[    1.513395]ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.513401]ohci-pci: OHCI PCI platform driver
[    1.513423]ohci-platform: OHCI generic platform driver
[    1.513436]uhci_hcd: USB Universal Host Controller Interface driver
[    1.513542]uhci_hcd 0000:00:1a.0: UHCI Host Controller
[    1.513549]uhci_hcd 0000:00:1a.0: new USB bus registered, assigned bus number 3
[    1.513557]uhci_hcd 0000:00:1a.0: detected 2 ports
[    1.513592]uhci_hcd 0000:00:1a.0: irq 20, io base 0x00001860
[    1.513655] usbusb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.513657] usbusb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.513658] usbusb3: Product: UHCI Host Controller
[    1.513660] usbusb3: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    1.513662] usbusb3: SerialNumber: 0000:00:1a.0
[    1.513805] hub3-0:1.0: USB hub found
[    1.513818] hub3-0:1.0: 2 ports detected
[    1.514027]uhci_hcd 0000:00:1a.1: UHCI Host Controller
[    1.514033]uhci_hcd 0000:00:1a.1: new USB bus registered, assigned bus number 4
[    1.514041]uhci_hcd 0000:00:1a.1: detected 2 ports
[    1.514075]uhci_hcd 0000:00:1a.1: irq 21, io base 0x00001880
[    1.514135] usbusb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.514137] usbusb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.514139] usbusb4: Product: UHCI Host Controller
[    1.514140] usbusb4: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    1.514142] usbusb4: SerialNumber: 0000:00:1a.1
[    1.514286] hub4-0:1.0: USB hub found
[    1.514293] hub4-0:1.0: 2 ports detected
[    1.514511]uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.514517]uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 5
[    1.514525]uhci_hcd 0000:00:1d.0: detected 2 ports
[    1.514561]uhci_hcd 0000:00:1d.0: irq 16, io base 0x000018a0
[    1.514622] usbusb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.514624] usbusb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.514626] usbusb5: Product: UHCI Host Controller
[    1.514627] usbusb5: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    1.514629] usbusb5: SerialNumber: 0000:00:1d.0
[    1.514760] hub5-0:1.0: USB hub found
[    1.514768] hub5-0:1.0: 2 ports detected
[    1.514971]uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.514978]uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 6
[    1.514986]uhci_hcd 0000:00:1d.1: detected 2 ports
[    1.515019]uhci_hcd 0000:00:1d.1: irq 17, io base 0x000018c0
[    1.515077] usbusb6: New USB device found, idVendor=1d6b, idProduct=0001
[    1.515079] usbusb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.515081] usbusb6: Product: UHCI Host Controller
[    1.515083] usbusb6: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    1.515084] usbusb6: SerialNumber: 0000:00:1d.1
[    1.515224] hub6-0:1.0: USB hub found
[    1.515232] hub6-0:1.0: 2 ports detected
[    1.515451]uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.515457]uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 7
[    1.515468]uhci_hcd 0000:00:1d.2: detected 2 ports
[    1.515503]uhci_hcd 0000:00:1d.2: irq 18, io base 0x000018e0
[    1.515566] usbusb7: New USB device found, idVendor=1d6b, idProduct=0001
[    1.515567] usbusb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.515569] usbusb7: Product: UHCI Host Controller
[    1.515571] usbusb7: Manufacturer: Linux 3.16.0-30-generic uhci_hcd
[    1.515573] usbusb7: SerialNumber: 0000:00:1d.2
[    1.515703] hub7-0:1.0: USB hub found
[    1.515711] hub7-0:1.0: 2 ports detected
[    1.515934]i8042: PNP: PS/2 Controller [PNP0303:KBD,PNP0f13:MOU] at 0x60,0x64irq 1,12
[    1.524635]serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.524640]serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.524811]mousedev: PS/2 mouse device common for all mice
[    1.525028]rtc_cmos 00:02: RTC can wake from S4
[    1.525207]rtc_cmos 00:02: rtc core: registered rtc_cmos as rtc0
[    1.525243]rtc_cmos 00:02: alarms up to one month, y3k, 114 bytes nvram, hpetirqs
[    1.525359]device-mapper: uevent: version 1.0.3
[    1.525455]device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised:dm-devel@redhat.com
[    1.525476]ledtrig-cpu: registered to indicate activity on CPUs
[    1.525609] TCP:cubic registered
[    1.525794] NET:Registered protocol family 10
[    1.526080] NET:Registered protocol family 17
[    1.526095] Keytype dns_resolver registered
[    1.526432]Loading compiled-in X.509 certificates
[    1.527786]Loaded X.509 cert 'Magrathea: Glacier signing key:7be2a7200f17f00ca011f70e5a874c37e3e0f6be'
[    1.527809]registered taskstats version 1
[    1.538555] Keytype trusted registered
[    1.540638] Keytype encrypted registered
[    1.542746]AppArmor: AppArmor sha1 policy hashing enabled
[    1.542751] ima:No TPM chip found, activating TPM-bypass!
[    1.542780] evm:HMAC attrs: 0x1
[    1.543403]  Magic number: 7:921:61
[    1.558194]rtc_cmos 00:02: setting system clock to 2015-03-12 05:03:34 UTC(1426136614)
[    1.602265]input: AT Translated Set 2 keyboard as/devices/platform/i8042/serio0/input/input3
[    1.772784] BIOSEDD facility v0.16 2004-Jun-25, 0 devices found
[    1.772784] EDDinformation not available.
[    1.772893] PM:Hibernation image not present or could not be loaded.
[    1.968166] usb2-5: new high-speed USB device number 2 using ehci-pci
[    2.471876] usb2-5: New USB device found, idVendor=17ef, idProduct=1004
[    2.471878] usb2-5: New USB device strings: Mfr=2, Product=1, SerialNumber=3
[    2.471880] usb2-5: Product: Integrated Camera
[    2.471881] usb2-5: Manufacturer: Chicony Electronics Co., Ltd.
[    2.471883] usb2-5: SerialNumber: SN0001
[    2.688043] usb3-1: new full-speed USB device number 2 using uhci_hcd
[    3.002655] usb3-1: New USB device found, idVendor=0a5c, idProduct=2110
[    3.002657] usb3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.002659] usb3-1: Product: BCM2045B
[    3.002661] usb3-1: Manufacturer: Broadcom Corp
[    3.578367]Freeing unused kernel memory: 1356K (ffffffff81d1c000 -ffffffff81e6f000)
[    3.602118] Writeprotecting the kernel read-only data: 12288k
[    3.628473]Freeing unused kernel memory: 564K (ffff880001773000 -ffff880001800000)
[    3.654724]Freeing unused kernel memory: 500K (ffff880001b83000 -ffff880001c00000)
[    3.717808]systemd-udevd[108]: starting version 204
[    3.778575]pps_core: LinuxPPS API ver. 1 registered
[    3.778576]pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti<giometti@linux.it>
[    3.781798] PTPclock support registered
[    3.874634] ahci0000:00:1f.2: version 3.0
[    3.874808] ahci0000:00:1f.2: irq 46 for MSI/MSI-X
[    3.874876] ahci0000:00:1f.2: AHCI 0001.0100 32 slots 3 ports 1.5 Gbps 0x5 impl SATAmode
[    3.874879] ahci0000:00:1f.2: flags: 64bit ncq sntf pm led clo pio slum part ccc 
[    3.875781]sdhci: Secure Digital Host Controller Interface driver
[    3.875781]sdhci: Copyright(c) Pierre Ossman
[    3.877871]sdhci-pci 0000:15:00.2: SDHCI controller found [1180:0822] (rev 21)
[    3.877888] pci0000:00:1e.0: enabling device (0005 -> 0007)
[    3.878979]sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn'tfully claim to support it.
[    3.878989] mmc0:no vqmmc regulator found
[    3.878990] mmc0:no vmmc regulator found
[    3.879988]sdhci-pci 0000:15:00.2: Will use DMA mode even though HW doesn'tfully claim to support it.
[    3.889407] scsi2: ahci
[    3.892342] mmc0:SDHCI controller on PCI [0000:15:00.2] using DMA
[    3.897342] scsi3: ahci
[    3.907433] scsi4: ahci
[    3.907541] ata3:SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226100 irq 46
[    3.907542] ata4:DUMMY
[    3.907545] ata5:SATA max UDMA/133 abar m2048@0xfe226000 port 0xfe226200 irq 46
[    3.941753]e1000e: Intel(R) PRO/1000 Network Driver - 2.3.2-k
[    3.941754]e1000e: Copyright(c) 1999 - 2014 Intel Corporation.
[    3.941999]e1000e 0000:00:19.0: Interrupt Throttling Rate (ints/sec) set todynamic conservative mode
[    3.942029]e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[    3.975838]firewire_ohci 0000:15:00.1: added OHCI v1.10 device as card 0, 4 IR +4 IT contexts, quirks 0x11
[    4.265680] ata3:SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    4.265706] ata5:SATA link down (SStatus 0 SControl 300)
[    4.292940]ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    4.292942]ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK)filtered out
[    4.292957]ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.372926]ata3.00: ATA-7: WDC WD1600BEVS-08RST2, 08.01G08, max UDMA/133
[    4.372939]ata3.00: 312581808 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    4.427675]ata3.00: ACPI cmd ef/02:00:00:00:00:a0 (SET FEATURES) succeeded
[    4.427677]ata3.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK)filtered out
[    4.427679]ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    4.489315]ata3.00: configured for UDMA/133
[    4.489430] scsi2:0:0:0: Direct-Access     ATA      WDC WD1600BEVS-0 1G08 PQ: 0 ANSI:5
[    4.489714] sd2:0:0:0: [sda] 312581808 512-byte logical blocks: (160 GB/149 GiB)
[    4.489778] sd2:0:0:0: [sda] Write Protect is off
[    4.489781] sd2:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    4.489808] sd2:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn'tsupport DPO or FUA
[    4.500216] sd2:0:0:0: Attached scsi generic sg0 type 0
[    4.541256]  sda:sda1 sda2 < sda5 >
[    4.541610] sd2:0:0:0: [sda] Attached SCSI disk
[    4.709246]e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1)00:15:58:84:5a:d6
[    4.709248]e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    4.709281]e1000e 0000:00:19.0 eth0: MAC: 6, PHY: 6, PBA No: 1008FF-0FF
[    5.216258]psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x81a0b1,caps: 0xa04791/0x300000/0x0, board id: 71, fw id: 496542
[    5.216264]psmouse serio1: synaptics: serio: Synaptics pass-through port atisa0060/serio1/input0
[    5.303001]input: SynPS/2 Synaptics TouchPad as/devices/platform/i8042/serio1/input/input5
[    5.354101]EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts:(null)
[    5.492222]firewire_core 0000:15:00.1: created device fw0: GUID00016c2000bee5ff, S400
[    6.788053]floppy0: no floppy controllers found
[    7.409391]random: nonblocking pool is initialized
[    8.450374]psmouse serio2: alps: Unknown ALPS touchpad: E7=10 00 64, EC=10 0064
[    9.870017]psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons:3/3
[   10.114301]input: TPPS/2 IBM TrackPoint as/devices/platform/i8042/serio1/serio2/input/input6
[   17.232294]Adding 4125692k swap on /dev/sda5.  Priority:-1 extents:1across:4125692k FS
[   17.565350]systemd-udevd[279]: starting version 204
[   17.628090] lp:driver loaded but no devices found
[   17.639199]ppdev: user-space parallel port driver
[   17.675917] ACPI:Video Device [VID1] (multi-head: yes  rom: no  post: no)
[   17.680660] acpidevice:06: registered as cooling_device2
[   17.690478]input: Video Bus as/devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/LNXVIDEO:01/input/input7
[   17.767410]shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   17.771312] wmi:Mapper loaded
[   17.791973]cfg80211: Calling CRDA to update world regulatory domain
[   17.861971]Bluetooth: Core ver 2.19
[   17.861996] NET:Registered protocol family 31
[   17.861998]Bluetooth: HCI device and connection manager initialized
[   17.862009]Bluetooth: HCI socket layer initialized
[   17.862013]Bluetooth: L2CAP socket layer initialized
[   17.862029]Bluetooth: SCO socket layer initialized
[   17.872231]iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driverfor Linux, in-tree:s
[   17.872235]iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   17.872311]iwl3945 0000:03:00.0: can't disable ASPM; OS doesn't have ASPMcontrol
[   17.879155]snd_hda_intel 0000:00:1b.0: probe_mask set to 0x1 for device17aa:20ac
[   17.879208]snd_hda_intel 0000:00:1b.0: irq 48 for MSI/MSI-X
[   17.885277]Non-volatile memory driver v1.3
[   17.889302]thinkpad_acpi: ThinkPad ACPI Extras v0.25
[   17.889305]thinkpad_acpi: http://ibm-acpi.sf.net/
[   17.889308]thinkpad_acpi: ThinkPad BIOS 7LETD0WW (2.30 ), EC 7KHT24WW-1.08
[   17.889309]thinkpad_acpi: Lenovo ThinkPad T61, model 7742B6V
[   17.899586] ACPIWarning: SystemIO range 0x0000000000001028-0x000000000000102fconflicts with OpRegion 0x0000000000001000-0x000000000000107f(\_SB_.PCI0.LPC_.PMIO) (20140424/utaddress-258)
[   17.899595] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   17.899599] ACPIWarning: SystemIO range 0x00000000000011b0-0x00000000000011bfconflicts with OpRegion 0x0000000000001180-0x00000000000011bf(\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   17.899604] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   17.899606] ACPIWarning: SystemIO range 0x0000000000001180-0x00000000000011afconflicts with OpRegion 0x0000000000001180-0x00000000000011bf(\_SB_.PCI0.LPC_.LPIO) (20140424/utaddress-258)
[   17.899611] ACPI:If an ACPI driver is available for this device, you should use itinstead of the native driver
[   17.899613]lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.927725]yenta_cardbus 0000:15:00.0: CardBus bridge found [17aa:20c6]
[   17.928178]iwl3945 0000:03:00.0: Tunable channels: 11 802.11bg, 13 802.11achannels
[   17.928182]iwl3945 0000:03:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   17.928250]iwl3945 0000:03:00.0: irq 49 for MSI/MSI-X
[   17.935921]usbcore: registered new interface driver btusb
[   17.936707]thinkpad_acpi: detected a 16-level brightness capable ThinkPad
[   17.937348]thinkpad_acpi: ACPI backlight control delay disabled
[   17.937512]thinkpad_acpi: radio switch found; radios are enabled
[   17.937541]thinkpad_acpi: This ThinkPad has standard ACPI backlight brightnesscontrol, supported by the ACPI video driver
[   17.937542]thinkpad_acpi: Disabling thinkpad-acpi brightness events bydefault...
[   17.942946]thinkpad_acpi: rfkill switch tpacpi_bluetooth_sw: radio is unblocked
[   17.953641]thinkpad_acpi: Standard ACPI backlight interface available, notloading native one
[   17.953808]thinkpad_acpi: Console audio control enabled, mode: monitor (readonly)
[   17.955992]input: ThinkPad Extra Buttons as/devices/platform/thinkpad_acpi/input/input8
[   17.960221]ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   17.973019]ip_tables: (C) 2000-2006 Netfilter Core Team
[   17.983082]nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   18.001415] [drm]Initialized drm 1.1.0 20060810
[   18.001624]ip6_tables: (C) 2000-2006 Netfilter Core Team
[   18.053162]yenta_cardbus 0000:15:00.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   18.053169]yenta_cardbus 0000:15:00.0: Socket status: 30000006
[   18.053587]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [io 0x8000-0xbfff]
[   18.053591]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem0xf8100000-0xfbffffff]
[   18.053595]pcmcia_socket pcmcia_socket0: cs: memory probe0xf8100000-0xfbffffff:
[   18.053601] excluding 0xf8100000-0xf84effff
[   18.053611]yenta_cardbus 0000:15:00.0: pcmcia: parent PCI bridge window: [mem0xf4000000-0xf7ffffff 64bit pref]
[   18.053614]pcmcia_socket pcmcia_socket0: cs: memory probe0xf4000000-0xf7ffffff:
[   18.053619] excluding 0xf4000000-0xf7ffffff
[   18.068134] r592:driver successfully loaded
[   18.071557] r852:driver loaded successfully
[   18.279200]audit: type=1400 audit(1426136631.230:2): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/sbin/dhclient" pid=345 comm="apparmor_parser"
[   18.279207]audit: type=1400 audit(1426136631.230:3): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=345 comm="apparmor_parser"
[   18.279212]audit: type=1400 audit(1426136631.230:4): apparmor="STATUS"operation="profile_load" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=345comm="apparmor_parser"
[   18.279764]audit: type=1400 audit(1426136631.230:5): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=345 comm="apparmor_parser"
[   18.279770]audit: type=1400 audit(1426136631.230:6): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=345comm="apparmor_parser"
[   18.281834]audit: type=1400 audit(1426136631.234:7): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/sbin/dhclient" pid=464 comm="apparmor_parser"
[   18.281840]audit: type=1400 audit(1426136631.234:8): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=464 comm="apparmor_parser"
[   18.281844]audit: type=1400 audit(1426136631.234:9): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=464comm="apparmor_parser"
[   18.282397]audit: type=1400 audit(1426136631.234:10): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=464 comm="apparmor_parser"
[   18.282402]audit: type=1400 audit(1426136631.234:11): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/connman/scripts/dhclient-script" pid=464comm="apparmor_parser"
[   18.300683] soundhdaudioC0D0: autoconfig: line_outs=1 (0x12/0x0/0x0/0x0/0x0)type:speaker
[   18.300685] soundhdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   18.300687] soundhdaudioC0D0:    hp_outs=1 (0x11/0x0/0x0/0x0/0x0)
[   18.300688] soundhdaudioC0D0:    mono: mono_out=0x0
[   18.300690] soundhdaudioC0D0:    dig-out=0x1b/0x0
[   18.300691] soundhdaudioC0D0:    inputs:
[   18.300694] soundhdaudioC0D0:      Internal Mic=0x15
[   18.300696] soundhdaudioC0D0:      Dock Mic=0x1c
[   18.300698] soundhdaudioC0D0:      Mic=0x14
[   18.322723]media: Linux media interface: v0.10
[   18.329197] Linuxvideo capture interface: v2.00
[   18.342137]uvcvideo: Found UVC 1.00 device Integrated Camera (17ef:1004)
[   18.348973]input: Integrated Camera as/devices/pci0000:00/0000:00:1d.7/usb2/2-5/2-5:1.0/input/input9
[   18.349742]usbcore: registered new interface driver uvcvideo
[   18.349742] USBVideo Class driver (1.1.1)
[   18.386736]input: HDA Intel Dock Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   18.386878]input: HDA Intel Mic as/devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   18.387010]input: HDA Intel Front Headphone as/devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[   18.405782]checking generic (d5000000 3f0000) vs hw (e0000000 10000000)
[   18.405786]checking generic (d5000000 3f0000) vs hw (d4000000 2000000)
[   18.405788] fb:switching to nouveaufb from VESA VGA
[   18.405849]Console: switching to colour dummy device 80x25
[   18.408342]nouveau  [  DEVICE][0000:01:00.0] BOOT0  : 0x086900a2
[   18.408346]nouveau  [  DEVICE][0000:01:00.0] Chipset: G86 (NV86)
[   18.408349]nouveau  [  DEVICE][0000:01:00.0] Family : NV50
[   18.408396]nouveau  [   VBIOS][0000:01:00.0] checking PRAMIN for image...
[   18.477708]nouveau  [   VBIOS][0000:01:00.0] ... appears to be valid
[   18.477714]nouveau  [   VBIOS][0000:01:00.0] using image from PRAMIN
[   18.477847]nouveau  [   VBIOS][0000:01:00.0] BIT signature found
[   18.477851]nouveau  [   VBIOS][0000:01:00.0] version 60.86.3e.00.00
[   18.509685]nouveau 0000:01:00.0: irq 50 for MSI/MSI-X
[   18.509706]nouveau  [     PMC][0000:01:00.0] MSI interrupts enabled
[   18.509751]nouveau  [     PFB][0000:01:00.0] RAM type: GDDR3
[   18.509753]nouveau  [     PFB][0000:01:00.0] RAM size: 128 MiB
[   18.509756]nouveau  [     PFB][0000:01:00.0]    ZCOMP: 646 tags
[   18.512415]nouveau  [    VOLT][0000:01:00.0] GPU voltage: 1150000uv
[   18.548676]nouveau  [  PTHERM][0000:01:00.0] FAN control: none / external
[   18.548691]nouveau  [  PTHERM][0000:01:00.0] fan management: automatic
[   18.548694]nouveau  [  PTHERM][0000:01:00.0] internal sensor: yes
[   18.548705]nouveau  [     CLK][0000:01:00.0] 20: core 169 MHz shader 338 MHzmemory 100 MHz
[   18.548709]nouveau  [     CLK][0000:01:00.0] 21: core 275 MHz shader 550 MHzmemory 301 MHz
[   18.548713]nouveau  [     CLK][0000:01:00.0] 22: core 400 MHz shader 800 MHzmemory 600 MHz
[   18.548756]nouveau  [     CLK][0000:01:00.0] --: core 275 MHz shader 550 MHzmemory 302 MHz
[   18.548999] [TTM]Zone  kernel: Available graphics memory: 1990576 kiB
[   18.549001] [TTM]Initializing pool allocator
[   18.549010] [TTM]Initializing DMA pool allocator
[   18.549026]nouveau  [     DRM] VRAM: 128 MiB
[   18.549028]nouveau  [     DRM] GART: 1048576 MiB
[   18.549034]nouveau  [     DRM] TMDS table version 2.0
[   18.549037]nouveau  [     DRM] DCB version 4.0
[   18.549040]nouveau  [     DRM] DCB outp 00: 01000323 00010034
[   18.549043]nouveau  [     DRM] DCB outp 01: 02811300 00000028
[   18.549045]nouveau  [     DRM] DCB outp 02: 02822312 00010030
[   18.549048]nouveau  [     DRM] DCB outp 03: 014333f1 0080c080
[   18.549050]nouveau  [     DRM] DCB conn 00: 0040
[   18.549053]nouveau  [     DRM] DCB conn 01: 0100
[   18.549055]nouveau  [     DRM] DCB conn 02: 1231
[   18.549058]nouveau  [     DRM] DCB conn 03: 0311
[   18.549687]cfg80211: World regulatory domain updated:
[   18.549690]cfg80211:  DFS Master region: unset
[   18.549692]cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain,max_eirp), (dfs_cac_time)
[   18.549696]cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.549699]cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.549701]cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.549704]cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.549707]cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000mBm), (N/A)
[   18.569738]nouveau W[     DRM] failed to create encoder 0/1/0: -19
[   18.569742]nouveau W[     DRM] TV-1 has no encoders, removing
[   18.569779] [drm]Supports vblank timestamp caching Rev 2 (21.10.2013).
[   18.569781] [drm]Driver supports precise vblank timestamp query.
[   18.590688]nouveau  [     DRM] MM: using CRYPT for buffer copies
[   18.647406]pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   18.647416] excluding 0xc0000-0xd3fff 0xe0000-0xfffff
[   18.647442]pcmcia_socket pcmcia_socket0: cs: memory probe0xa0000000-0xa0ffffff:
[   18.647452] excluding 0xa0000000-0xa0ffffff
[   18.647469]pcmcia_socket pcmcia_socket0: cs: memory probe0x60000000-0x60ffffff:
[   18.647478] excluding 0x60000000-0x60ffffff
[   19.736043]EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.915711]nouveau  [     DRM] allocated 1440x900 fb: 0x60000, boffff8801352e0000
[   19.915856]fbcon: nouveaufb (fb0) is primary device
[   19.998730]Console: switching to colour frame buffer device 180x56
[   20.000475]nouveau 0000:01:00.0: fb0: nouveaufb frame buffer device
[   20.000477]nouveau 0000:01:00.0: registered panic notifier
[   20.012119] [drm]Initialized nouveau 1.1.2 20120801 for 0000:01:00.0 on minor 0
[   20.344749] init:failsafe main process (655) killed by TERM signal
[   20.724098]floppy0: no floppy controllers found
[   22.619178]Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   22.619184]Bluetooth: BNEP filters: protocol multicast
[   22.619197]Bluetooth: BNEP socket layer initialized
[   22.624755]Bluetooth: RFCOMM TTY layer initialized
[   22.624771]Bluetooth: RFCOMM socket layer initialized
[   22.624779]Bluetooth: RFCOMM ver 1.11
[   23.023499] init:cups main process (878) killed by HUP signal
[   23.023516] init:cups main process ended, respawning
[   23.625834] init:samba-ad-dc main process (932) terminated with status 1
[   24.139511]audit_printk_skb: 120 callbacks suppressed
[   24.139516]audit: type=1400 audit(1426136637.090:52): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cups-browsed" pid=1067comm="apparmor_parser"
[   24.452501]acpi_call: module verification failed: signature and/or  required keymissing - tainting kernel
[   24.463815]thinkpad_ec: thinkpad_ec 0.41 loaded.
[   24.464350]tp_smapi 0.41 loading...
[   24.464561]tp_smapi successfully loaded (smapi_port=0xb2).
[   24.704352]e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   24.808152]e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[   24.808319] IPv6:ADDRCONF(NETDEV_UP): eth0: link is not ready
[   24.925698]iwl3945 0000:03:00.0: loaded firmware version 15.32.2.9
[   24.998677] IPv6:ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   25.213348]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.213431]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.213485]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.213538]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.213594]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.213645]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.341989]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.342080]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.342140]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.342197]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.342254]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   25.342312]acpi_call: Cannot get handle: Error: AE_NOT_FOUND
[   53.240458]audit: type=1400 audit(1426136666.194:53): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=2016comm="apparmor_parser"
[   53.240471]audit: type=1400 audit(1426136666.194:54): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2016 comm="apparmor_parser"
[   53.241032]audit: type=1400 audit(1426136666.194:55): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2016 comm="apparmor_parser"
[   80.145118]wlan0: authenticate with 36:8f:c6:b0:10:f8
[   80.150440]wlan0: send auth to 36:8f:c6:b0:10:f8 (try 1/3)
[   80.153872]wlan0: authenticated
[   80.156103]wlan0: associate with 36:8f:c6:b0:10:f8 (try 1/3)
[   80.158940]wlan0: RX AssocResp from 36:8f:c6:b0:10:f8 (capab=0x431 status=0aid=2)
[   80.160405]wlan0: associated
[   80.160474] IPv6:ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   80.571839]audit: type=1400 audit(1426136693.523:56): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2221 comm="nm-dhcp-client." lport=13249 family="inet"sock_type="dgram" protocol=17
[   80.571855]audit: type=1400 audit(1426136693.523:57): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2221 comm="nm-dhcp-client." lport=41397 family="inet6"sock_type="dgram" protocol=17
[   80.613930]audit: type=1400 audit(1426136693.567:58): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2222 comm="nm-dhcp-client." lport=13249 family="inet"sock_type="dgram" protocol=17
[   80.613944]audit: type=1400 audit(1426136693.567:59): apparmor="DENIED"operation="file_inherit"profile="/usr/lib/NetworkManager/nm-dhcp-client.action"pid=2222 comm="nm-dhcp-client." lport=41397 family="inet6"sock_type="dgram" protocol=17
[   83.187901]nf_conntrack: automatic helper assignment is deprecated and it willbe removed soon. Use the iptables CT target to attach helpersinstead.
darren@darren-ThinkPad-R61i:~$  
```

---

### Post by oldfred on 2015-03-12
When I look up specs for that computer, I do not see nVidia? So why nVidia drivers, that would just create conflicts.

---

### Post by darrenllr on 2015-03-18
> **oldfred said:**
> When I look up specs for that computer, I do not see nVidia? So why nVidia drivers, that would just create conflicts.

Hi OldFred - 

I've done a sudo lshw and it shows Nvidia in there - here is the output for 'display' (full output below).

It shows nVidia in there.  I've since reinstalled 14.04 clean / wiped the disk during installation.  I'll post the latest dmesg in the next thread, thanks.

*Having checked Additional Drivers, the nVidia driver 331.113 is currently being used.  I'll try using the Nouveau / other nVidia drivers & report back ;-)

**I'm not sure if it's relevant, but for some reason my command prompt in Terminal says ....'T61' - and my Lenovo is actually an R60i.

```
           *-display                description: VGA compatible controller
                product: G86M [Quadro NVS 140M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:50 memory:d6000000-d6ffffff memory:e0000000-efffffff memory:d4000000-d5ffffff ioport:2000(size=128)
```

```
darren@darren-ThinkPad-T61:~$ ^Cdarren@darren-ThinkPad-T61:~$ ^C
darren@darren-ThinkPad-T61:~$ sudo lshw
darren-thinkpad-t61       
    description: Notebook
    product: 7742B6V ()
    vendor: LENOVO
    version: ThinkPad T61
    serial: L3D6773
    width: 64 bits
    capabilities: smbios-2.4 dmi-2.4 vsyscall32
    configuration: administrator_password=disabled boot=normal chassis=notebook family=ThinkPad T61 frontpanel_password=unknown keyboard_password=disabled power-on_password=disabled uuid=20695F81-5119-11CB-BFA4-ECE34BDBB8B0
  *-core
       description: Motherboard
       product: 7742B6V
       vendor: LENOVO
       physical id: 0
       version: Not Available
       serial: VF1NX0BXF03
     *-firmware
          description: BIOS
          vendor: LENOVO
          physical id: 0
          version: 7LETD0WW (2.30 )
          date: 02/27/2012
          size: 128KiB
          capacity: 4032KiB
          capabilities: pci pcmcia pnp upgrade shadowing escd cdboot bootselect socketedrom edd acpi usb biosbootspecification
     *-cpu
          description: CPU
          product: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
          vendor: Intel Corp.
          physical id: 6
          bus info: cpu@0
          version: Intel(R) Core(TM)2 Duo CPU     T5750  @ 2.00GHz
          slot: None
          size: 2GHz
          capacity: 2GHz
          width: 64 bits
          clock: 167MHz
          capabilities: fpu fpu_exception wp vme de pse tsc msr pae mce cx8 apic sep mtrr pge mca cmov pat pse36 clflush dts acpi mmx fxsr sse sse2 ss ht tm pbe syscall nx x86-64 constant_tsc arch_perfmon pebs bts rep_good nopl aperfmperf pni dtes64 monitor ds_cpl est tm2 ssse3 cx16 xtpr pdcm lahf_lm dtherm cpufreq
        *-cache:0
             description: L1 cache
             physical id: a
             slot: Internal L1 Cache
             size: 64KiB
             capacity: 64KiB
             capabilities: synchronous internal write-back instruction
        *-cache:1
             description: L2 cache
             physical id: c
             slot: Internal L2 Cache
             size: 2MiB
             capacity: 2MiB
             capabilities: burst internal write-back unified
     *-cache
          description: L1 cache
          physical id: b
          slot: Internal L1 Cache
          size: 64KiB
          capacity: 64KiB
          capabilities: synchronous internal write-back data
     *-memory
          description: System Memory
          physical id: 2b
          slot: System board or motherboard
          size: 4GiB
        *-bank:0
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 0
             slot: DIMM 1
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
        *-bank:1
             description: SODIMM DDR2 Synchronous 667 MHz (1.5 ns)
             physical id: 1
             slot: DIMM 2
             size: 2GiB
             width: 64 bits
             clock: 667MHz (1.5ns)
     *-pci
          description: Host bridge
          product: Mobile PM965/GM965/GL960 Memory Controller Hub
          vendor: Intel Corporation
          physical id: 100
          bus info: pci@0000:00:00.0
          version: 0c
          width: 32 bits
          clock: 33MHz
        *-pci:0
             description: PCI bridge
             product: Mobile PM965/GM965/GL960 PCI Express Root Port
             vendor: Intel Corporation
             physical id: 1
             bus info: pci@0000:00:01.0
             version: 0c
             width: 32 bits
             clock: 33MHz
             capabilities: pci pm msi pciexpress normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:40 ioport:2000(size=4096) memory:d4000000-d6ffffff ioport:e0000000(size=268435456)
           *-display
                description: VGA compatible controller
                product: G86M [Quadro NVS 140M]
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:50 memory:d6000000-d6ffffff memory:e0000000-efffffff memory:d4000000-d5ffffff ioport:2000(size=128)
        *-network
             description: Ethernet interface
             product: 82566MM Gigabit Network Connection
             vendor: Intel Corporation
             physical id: 19
             bus info: pci@0000:00:19.0
             logical name: eth0
             version: 03
             serial: 00:15:58:84:5a:d6
             capacity: 1Gbit/s
             width: 32 bits
             clock: 33MHz
             capabilities: pm msi cap_list ethernet physical tp 10bt 10bt-fd 100bt 100bt-fd 1000bt-fd autonegotiation
             configuration: autonegotiation=on broadcast=yes driver=e1000e driverversion=2.3.2-k firmware=0.3-0 latency=0 link=no multicast=yes port=twisted pair
             resources: irq:49 memory:fe200000-fe21ffff memory:fe225000-fe225fff ioport:1840(size=32)
        *-usb:0
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #4
             vendor: Intel Corporation
             physical id: 1a
             bus info: pci@0000:00:1a.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:20 ioport:1860(size=32)
        *-usb:1
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #5
             vendor: Intel Corporation
             physical id: 1a.1
             bus info: pci@0000:00:1a.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:21 ioport:1880(size=32)
        *-usb:2
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #2
             vendor: Intel Corporation
             physical id: 1a.7
             bus info: pci@0000:00:1a.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:22 memory:fe226c00-fe226fff
        *-multimedia
             description: Audio device
             product: 82801H (ICH8 Family) HD Audio Controller
             vendor: Intel Corporation
             physical id: 1b
             bus info: pci@0000:00:1b.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pm msi pciexpress bus_master cap_list
             configuration: driver=snd_hda_intel latency=0
             resources: irq:46 memory:fe220000-fe223fff
        *-pci:1
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 1
             vendor: Intel Corporation
             physical id: 1c
             bus info: pci@0000:00:1c.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:41 ioport:3000(size=4096) memory:fc000000-fdffffff ioport:f8000000(size=1048576)
        *-pci:2
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 2
             vendor: Intel Corporation
             physical id: 1c.1
             bus info: pci@0000:00:1c.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:42 ioport:4000(size=4096) memory:dc100000-df2fffff ioport:dfd00000(size=1048576)
           *-network
                description: Wireless interface
                product: PRO/Wireless 3945ABG [Golan] Network Connection
                vendor: Intel Corporation
                physical id: 0
                bus info: pci@0000:03:00.0
                logical name: wlan0
                version: 02
                serial: 00:1f:3c:20:cd:12
                width: 32 bits
                clock: 33MHz
                capabilities: pm msi pciexpress bus_master cap_list ethernet physical wireless
                configuration: broadcast=yes driver=iwl3945 driverversion=3.16.0-31-generic firmware=15.32.2.9 latency=0 link=no multicast=yes wireless=IEEE 802.11abg
                resources: irq:48 memory:df2ff000-df2fffff
        *-pci:3
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 3
             vendor: Intel Corporation
             physical id: 1c.2
             bus info: pci@0000:00:1c.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:43 ioport:5000(size=4096) memory:d8000000-d9ffffff ioport:dfa00000(size=1048576)
        *-pci:4
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 4
             vendor: Intel Corporation
             physical id: 1c.3
             bus info: pci@0000:00:1c.3
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:44 ioport:6000(size=4096) memory:d0000000-d1ffffff ioport:df700000(size=1048576)
        *-pci:5
             description: PCI bridge
             product: 82801H (ICH8 Family) PCI Express Port 5
             vendor: Intel Corporation
             physical id: 1c.4
             bus info: pci@0000:00:1c.4
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pci pciexpress msi pm normal_decode bus_master cap_list
             configuration: driver=pcieport
             resources: irq:45 ioport:7000(size=4096) memory:cc000000-cdffffff ioport:df400000(size=1048576)
        *-usb:3
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d
             bus info: pci@0000:00:1d.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:16 ioport:18a0(size=32)
        *-usb:4
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #2
             vendor: Intel Corporation
             physical id: 1d.1
             bus info: pci@0000:00:1d.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:17 ioport:18c0(size=32)
        *-usb:5
             description: USB controller
             product: 82801H (ICH8 Family) USB UHCI Controller #3
             vendor: Intel Corporation
             physical id: 1d.2
             bus info: pci@0000:00:1d.2
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: uhci bus_master
             configuration: driver=uhci_hcd latency=0
             resources: irq:18 ioport:18e0(size=32)
        *-usb:6
             description: USB controller
             product: 82801H (ICH8 Family) USB2 EHCI Controller #1
             vendor: Intel Corporation
             physical id: 1d.7
             bus info: pci@0000:00:1d.7
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: pm debug ehci bus_master cap_list
             configuration: driver=ehci-pci latency=0
             resources: irq:19 memory:fe227000-fe2273ff
        *-pci:6
             description: PCI bridge
             product: 82801 Mobile PCI Bridge
             vendor: Intel Corporation
             physical id: 1e
             bus info: pci@0000:00:1e.0
             version: f3
             width: 32 bits
             clock: 33MHz
             capabilities: pci subtractive_decode bus_master cap_list
             resources: ioport:8000(size=16384) memory:f8100000-fbffffff ioport:f4000000(size=67108864)
           *-pcmcia
                description: CardBus bridge
                product: RL5c476 II
                vendor: Ricoh Co Ltd
                physical id: 0
                bus info: pci@0000:15:00.0
                version: ba
                width: 64 bits
                clock: 33MHz
                capabilities: pcmcia bus_master cap_list
                configuration: driver=yenta_cardbus latency=176 maxlatency=5 mingnt=128
                resources: iomemory:b01716150-b0171614f irq:16 memory:f8100000-f8100fff ioport:8000(size=256) ioport:8400(size=256) memory:f4000000-f7ffffff memory:c0000000-c3ffffff
           *-firewire
                description: FireWire (IEEE 1394)
                product: R5C832 IEEE 1394 Controller
                vendor: Ricoh Co Ltd
                physical id: 0.1
                bus info: pci@0000:15:00.1
                version: 04
                width: 32 bits
                clock: 33MHz
                capabilities: pm ohci bus_master cap_list
                configuration: driver=firewire_ohci latency=32 maxlatency=4 mingnt=2
                resources: irq:17 memory:f8101000-f81017ff
           *-generic:0
                description: SD Host controller
                product: R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.2
                bus info: pci@0000:15:00.2
                version: 21
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=sdhci-pci latency=64
                resources: irq:18 memory:f8101800-f81018ff
           *-generic:1
                description: System peripheral
                product: R5C592 Memory Stick Bus Host Adapter
                vendor: Ricoh Co Ltd
                physical id: 0.4
                bus info: pci@0000:15:00.4
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r592 latency=64
                resources: irq:18 memory:f8102000-f81020ff
           *-generic:2
                description: System peripheral
                product: xD-Picture Card Controller
                vendor: Ricoh Co Ltd
                physical id: 0.5
                bus info: pci@0000:15:00.5
                version: 11
                width: 32 bits
                clock: 33MHz
                capabilities: pm bus_master cap_list
                configuration: driver=r852 latency=64
                resources: irq:18 memory:f8102400-f81024ff
        *-isa
             description: ISA bridge
             product: 82801HEM (ICH8M-E) LPC Interface Controller
             vendor: Intel Corporation
             physical id: 1f
             bus info: pci@0000:00:1f.0
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: isa bus_master cap_list
             configuration: driver=lpc_ich latency=0
             resources: irq:0
        *-ide
             description: IDE interface
             product: 82801HM/HEM (ICH8M/ICH8M-E) IDE Controller
             vendor: Intel Corporation
             physical id: 1f.1
             bus info: pci@0000:00:1f.1
             version: 03
             width: 32 bits
             clock: 33MHz
             capabilities: ide bus_master
             configuration: driver=ata_piix latency=0
             resources: irq:16 ioport:1f0(size=8) ioport:3f6 ioport:170(size=8) ioport:376 ioport:1830(size=16)
        *-storage
             description: SATA controller
             product: 82801HM/HEM (ICH8M/ICH8M-E) SATA Controller [AHCI mode]
             vendor: Intel Corporation
             physical id: 1f.2
             bus info: pci@0000:00:1f.2
             version: 03
             width: 32 bits
             clock: 66MHz
             capabilities: storage msi pm ahci_1.0 bus_master cap_list
             configuration: driver=ahci latency=0
             resources: irq:47 ioport:1c48(size=8) ioport:1c1c(size=4) ioport:1c40(size=8) ioport:1c18(size=4) ioport:1c20(size=32) memory:fe226000-fe2267ff
        *-serial UNCLAIMED
             description: SMBus
             product: 82801H (ICH8 Family) SMBus Controller
             vendor: Intel Corporation
             physical id: 1f.3
             bus info: pci@0000:00:1f.3
             version: 03
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:fe227400-fe2274ff ioport:1c60(size=32)
     *-scsi
          physical id: 1
          logical name: scsi2
          capabilities: emulated
        *-disk
             description: ATA Disk
             product: WDC WD1600BEVS-0
             vendor: Western Digital
             physical id: 0.0.0
             bus info: scsi@2:0.0.0
             logical name: /dev/sda
             version: 1G08
             serial: WD-WXE308EN1747
             size: 149GiB (160GB)
             capabilities: partitioned partitioned:dos
             configuration: ansiversion=5 sectorsize=512 signature=000db0de
           *-volume:0
                description: EXT4 volume
                vendor: Linux
                physical id: 1
                bus info: scsi@2:0.0.0,1
                logical name: /dev/sda1
                logical name: /
                version: 1.0
                serial: 416af6a9-258a-41fc-93a0-91be9e679150
                size: 145GiB
                capacity: 145GiB
                capabilities: primary bootable journaled extended_attributes large_files huge_files dir_nlink recover extents ext4 ext2 initialized
                configuration: created=2015-03-12 21:37:05 filesystem=ext4 lastmountpoint=/ modified=2015-03-18 11:35:41 mount.fstype=ext4 mount.options=rw,relatime,errors=remount-ro,data=ordered mounted=2015-03-18 11:35:42 state=mounted
           *-volume:1
                description: Extended partition
                physical id: 2
                bus info: scsi@2:0.0.0,2
                logical name: /dev/sda2
                size: 4029MiB
                capacity: 4029MiB
                capabilities: primary extended partitioned partitioned:extended
              *-logicalvolume
                   description: Linux swap / Solaris partition
                   physical id: 5
                   logical name: /dev/sda5
                   capacity: 4029MiB
                   capabilities: nofs
  *-battery:0
       product: 42T4644
       vendor: SANYO
       physical id: 1
       slot: Rear
       capacity: 84240mWh
       configuration: voltage=10.8V
  *-battery:1
       product: 45N1041
       vendor: SONY
       physical id: 2
       slot: Bay
       capacity: 31320mWh
       configuration: voltage=10.8V
darren@darren-ThinkPad-T61:~$ 



```

---

### Post by darrenllr on 2015-03-18
Okay, back to the recommended nVidia driver now - version 331.113 (proprietary, tested)

Just under a minute to boot - with a couple of time gaps in dmesg output.

First gap around 6 seconds after a *LOT* of 'plymouth respawning' lines.

```
[    5.714407] init:plymouth-upstart-bridge main process ended, respawning[    5.716555] init:plymouth-upstart-bridge main process (193) terminated with status 1
[    5.716571] init:plymouth-upstart-bridge respawning too fast, stopped
[    6.464911]psmouse serio2: trackpoint: IBM TrackPoint firmware: 0x0e, buttons:3/3
[    6.702418]input: TPPS/2 IBM TrackPoint as/devices/platform/i8042/serio1/serio2/input/input6
[   16.691109]Adding 4125692k swap on /dev/sda5.  Priority:-1 extents:1across:4125692k FS
[   17.094895]systemd-udevd[298]: starting version 204
[   17.320478]EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   17.377567] lp:driver loaded but no devices found
[   17.385364]ppdev: user-space parallel port driver 
```

Second gap from 25 to 50 seconds just after an nvidia entry:

```
[   23.113942]audit_printk_skb: 147 callbacks suppressed[   23.113947]audit: type=1400 audit(1426663261.904:61): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cups-browsed" pid=1079comm="apparmor_parser"
[   23.839469]thinkpad_ec: thinkpad_ec 0.41 loaded.
[   23.839798]tp_smapi 0.41 loading...
[   23.840118]tp_smapi successfully loaded (smapi_port=0xb2).
[   25.911547]nvidia 0000:01:00.0: irq 50 for MSI/MSI-X
[   50.511205]audit: type=1400 audit(1426663289.300:62): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/lib/cups/backend/cups-pdf" pid=2138comm="apparmor_parser"
[   50.511220]audit: type=1400 audit(1426663289.300:63): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2138 comm="apparmor_parser"
[   50.511779]audit: type=1400 audit(1426663289.300:64): apparmor="STATUS"operation="profile_replace" profile="unconfined"name="/usr/sbin/cupsd" pid=2138 comm="apparmor_parser" 
```

That's me flummoxed.  

Any suggestions would be wonderful ;-)

Thanks,
Darren

---

### Post by oldfred on 2015-03-18
Perhaps there is something that is checking models and the extras they add are then wrong.

Have you updated to the most current version of BIOS. 
But then which model BIOS is really correct?

---

### Post by darrenllr on 2015-03-21
Hi OldFred - 

The guys at the Lenovo shop here updated BIOS for me - it's V 2.30.

I've filed a possible bug report over at the NVidia Linux forums - I'm not even sure if it's a bug but it looks like it hangs for 30 seconds, so.

I'll come back if/when I hear anything back on that forum, maybe someone knows something that's already existing over there.

Fingers crossed.

(Nvidia forum link is [https://devtalk.nvidia.com/default/topic/820301/linux/slow-boot-nvidia-30-second-hang-ubuntu-14-04-thinkpad-r61i-quadro-nvs-140m-pcie-sse2-log-file/](https://devtalk.nvidia.com/default/topic/820301/linux/slow-boot-nvidia-30-second-hang-ubuntu-14-04-thinkpad-r61i-quadro-nvs-140m-pcie-sse2-log-file/) )

Thanks,
Darren.

---

