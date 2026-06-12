---
title: "usb trouble"
date: 2013-06-08
forum: General Help
---

### Post by dog-soldier on 2013-06-08
most of the time that i use my card reader to get pics from my camera cards the usb works. but times like right now for some reason it wont see the card reader and i cant get pics from the card. it acts like the card reader isnt even connected. is there a fix or setting for this problem?

---

### Post by 3rdalbum on 2013-06-08
The output of 'dmesg' when the problem happens, would be very helpful.

If you "safely remove" a memory card instead of "eject"ing it, the memory card reader will be completely disassociated with the system and you will have to unplug the reader and plug it back in again.

If this is not what is happening, the dmesg output may help us figure out what is going wrong.

---

### Post by dog-soldier on 2013-06-08
> **3rdalbum said:**
> The output of 'dmesg' when the problem happens, would be very helpful.

If you "safely remove" a memory card instead of "eject"ing it, the memory card reader will be completely disassociated with the system and you will have to unplug the reader and plug it back in again.

If this is not what is happening, the dmesg output may help us figure out what is going wrong.

i have tried it both ways by safely removing and ejecting and the same thing happens. i have tried unpluging and also rebooting and still nothing.
here is the result of dmesg
```
[    0.783094] EDD information not available.
[    0.798727] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.908466] ata5.00: ATAPI: DW-224E-C, 4.AA, max UDMA/33
[    0.924340] ata5.00: configured for UDMA/33
[    1.064093] ata3: SATA link down (SStatus 0 SControl 300)
[    1.068090] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.068556] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.068562] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.070717] ata1.00: ATA-7: FUJITSU MHV2040BH, 00000028, max UDMA/100
[    1.070721] ata1.00: 78140160 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    1.073198] ata1.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[    1.073203] ata1.00: ACPI cmd f5/00:00:00:00:00:a0 (SECURITY FREEZE LOCK) filtered out
[    1.075402] ata1.00: configured for UDMA/100
[    1.075618] scsi 0:0:0:0: Direct-Access     ATA      FUJITSU MHV2040B 0000 PQ: 0 ANSI: 5
[    1.075810] sd 0:0:0:0: [sda] 78140160 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.075847] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.075892] sd 0:0:0:0: [sda] Write Protect is off
[    1.075897] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.075934] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.077913] scsi 4:0:0:0: CD-ROM            TEAC     DW-224E-C        4.AA PQ: 0 ANSI: 5
[    1.080592] sr0: scsi3-mmc drive: 24x/24x writer cd/rw xa/form2 cdda tray
[    1.080596] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.080792] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    1.080942] sr 4:0:0:0: Attached scsi generic sg1 type 5
[    1.143488]  sda: sda1 sda2 < sda5 >
[    1.144225] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.144364] Freeing unused kernel memory: 744k freed
[    1.144771] Write protecting the kernel text: 5836k
[    1.144807] Write protecting the kernel read-only data: 2384k
[    1.144810] NX-protecting the kernel data: 4404k
[    1.164562] udevd[97]: starting version 175
[    1.224698] sky2: driver version 1.30
[    1.224749] sky2 0000:02:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.224769] sky2 0000:02:00.0: setting latency timer to 64
[    1.224804] sky2 0000:02:00.0: Yukon-2 EC Ultra chip revision 2
[    1.224938] sky2 0000:02:00.0: irq 44 for MSI/MSI-X
[    1.228057] sky2 0000:02:00.0: eth0: addr 00:17:42:1b:0c:3a
[    1.269500] sdhci: Secure Digital Host Controller Interface driver
[    1.269504] sdhci: Copyright(c) Pierre Ossman
[    1.269906] sdhci-pci 0000:08:03.2: SDHCI controller found [1217:7120] (rev 0)
[    1.269926] sdhci-pci 0000:08:03.2: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.269957] mmc0: Unknown controller version (16). You may experience problems.
[    1.269974] mmc0: no vmmc regulator found
[    1.270019] Registered led device: mmc0::
[    1.272485] mmc0: SDHCI controller on PCI [0000:08:03.2] using PIO
[    1.372089] usb 2-1: new low-speed USB device number 2 using uhci_hcd
[    1.562630] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1:1.0/input/input4
[    1.562834] generic-usb 0003:0461:4D0F.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1d.0-1/input0
[    1.562854] usbcore: registered new interface driver usbhid
[    1.562857] usbhid: USB HID core driver
[    1.640805] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    1.780055] usb 4-2: new full-speed USB device number 2 using uhci_hcd
[   18.068614] Adding 2348028k swap on /dev/sda5.  Priority:-1 extents:1 across:2348028k 
[   18.075243] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   18.102439] udevd[340]: starting version 175
[   18.150927] lp: driver loaded but no devices found
[   18.164370] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   18.165061] acpi device:01: registered as cooling_device2
[   18.165227] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   18.178151] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   18.216938] intel_rng: FWH not detected
[   18.219286] [drm] Initialized drm 1.1.0 20060810
[   18.233390] cfg80211: Calling CRDA to update world regulatory domain
[   18.236889] leds_ss4200: no LED devices found
[   18.272153] ip_tables: (C) 2000-2006 Netfilter Core Team
[   18.272995] yenta_cardbus 0000:08:03.0: CardBus bridge found [10cf:131e]
[   18.273023] yenta_cardbus 0000:08:03.0: O2: enabling read prefetch/write burst. If you experience problems or performance issues, use the yenta_socket parameter 'o2_speedup=off'
[   18.285883] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   18.289772] type=1400 audit(1370709262.005:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=426 comm="apparmor_parser"
[   18.290359] type=1400 audit(1370709262.005:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=426 comm="apparmor_parser"
[   18.290702] type=1400 audit(1370709262.005:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=426 comm="apparmor_parser"
[   18.294726] input: Fujitsu FUJ02B1 as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:05/FUJ02B1:00/input/input6
[   18.294911] fujitsu_laptop: ACPI: Fujitsu FUJ02B1 [FJEX] (on)
[   18.295468] input: Fujitsu FUJ02E3 as /devices/LNXSYSTM:00/LNXSYBUS:00/FUJ02E3:00/input/input7
[   18.295710] fujitsu_laptop: ACPI: Fujitsu FUJ02E3 [FEXT] (on)
[   18.296415] fujitsu_laptop: BTNI: [0xf0001]
[   18.296582] fujitsu_laptop: driver 0.6.0 successfully loaded
[   18.302038] ath5k 0000:05:00.0: PCI INT A -> GSI 18 (level, low) -> IRQ 18
[   18.302054] ath5k 0000:05:00.0: setting latency timer to 64
[   18.302102] ath5k 0000:05:00.0: registered as 'phy0'
[   18.331097] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   18.432082] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   18.432089] i915 0000:00:02.0: setting latency timer to 64
[   18.782140] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   18.782144] [drm] Driver supports precise vblank timestamp query.
[   18.783099] yenta_cardbus 0000:08:03.0: ISA IRQ mask 0x0cb8, PCI irq 16
[   18.783104] yenta_cardbus 0000:08:03.0: Socket status: 30000006
[   18.783109] pci_bus 0000:08: Raising subordinate bus# of parent bus (#08) from #09 to #0c
[   18.783118] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   18.783123] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3000-0x3fff:
[   18.827503] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   18.829505]  excluding 0x3000-0x30ff 0x3400-0x34ff
[   18.832552] irda_init()
[   18.832565] NET: Registered protocol family 23
[   18.837004] found SMC SuperIO Chip (devid=0x7a rev=00 base=0x002e): LPC47N227
[   18.837030] smsc_superio_flat(): fir: 0x6e8, sir: 0x2e8, dma: 03, irq: 6, mode: 0x0e
[   18.837036] smsc_ircc_present: can't get sir_base of 0x2e8
[   18.880690] ath: EEPROM regdomain: 0x66
[   18.880693] ath: EEPROM indicates we should expect a direct regpair map
[   18.880698] ath: Country alpha2 being used: 00
[   18.880700] ath: Regpair used: 0x66
[   18.881908] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   18.881914] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881918] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   18.881922] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881925] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   18.881929] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881932] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   18.881936] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881939] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   18.881943] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881947] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   18.881951] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881954] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   18.881958] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881961] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   18.881965] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881968] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   18.881972] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881976] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   18.881980] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881983] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   18.881987] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (N/A mBi, 2000 mBm)
[   18.881990] cfg80211: Disabling freq 2467 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.881994] cfg80211: Disabling freq 2472 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.881997] cfg80211: Disabling freq 2484 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.882001] cfg80211: Disabling freq 5040 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.882004] cfg80211: Disabling freq 5060 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.882007] cfg80211: Disabling freq 5080 MHz as custom regd has no rule that fits a 20 MHz wide channel
[   18.882011] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   18.882015] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882018] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   18.882022] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882025] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   18.882029] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882033] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   18.882037] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882040] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   18.882044] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882047] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   18.882051] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882054] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   18.882058] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882062] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   18.882066] cfg80211: 5140000 KHz - 5360000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882069] cfg80211: Updating information on frequency 5500 MHz for a 20 MHz width channel with regulatory rule:
[   18.882073] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882076] cfg80211: Updating information on frequency 5520 MHz for a 20 MHz width channel with regulatory rule:
[   18.882080] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882083] cfg80211: Updating information on frequency 5540 MHz for a 20 MHz width channel with regulatory rule:
[   18.882087] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882091] cfg80211: Updating information on frequency 5560 MHz for a 20 MHz width channel with regulatory rule:
[   18.882095] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882098] cfg80211: Updating information on frequency 5580 MHz for a 20 MHz width channel with regulatory rule:
[   18.882102] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882105] cfg80211: Updating information on frequency 5600 MHz for a 20 MHz width channel with regulatory rule:
[   18.882109] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882112] cfg80211: Updating information on frequency 5620 MHz for a 20 MHz width channel with regulatory rule:
[   18.882116] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882120] cfg80211: Updating information on frequency 5640 MHz for a 20 MHz width channel with regulatory rule:
[   18.882124] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882127] cfg80211: Updating information on frequency 5660 MHz for a 20 MHz width channel with regulatory rule:
[   18.882131] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882134] cfg80211: Updating information on frequency 5680 MHz for a 20 MHz width channel with regulatory rule:
[   18.882138] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882142] cfg80211: Updating information on frequency 5700 MHz for a 20 MHz width channel with regulatory rule:
[   18.882146] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882149] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   18.882153] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882156] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   18.882160] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882163] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   18.882167] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882171] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   18.882175] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.882178] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   18.882182] cfg80211: 5460000 KHz - 5860000 KHz @ 40000 KHz), (N/A mBi, 3000 mBm)
[   18.885507] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   18.890318]  0x3800-0x38ff 0x3c00-0x3cff
[   18.893849] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge window: [mem 0xf0200000-0xf02fffff]
[   18.893856] pcmcia_socket pcmcia_socket0: cs: memory probe 0xf0200000-0xf02fffff: excluding 0xf0200000-0xf020ffff
[   18.893874] yenta_cardbus 0000:08:03.0: pcmcia: parent PCI bridge window: [mem 0x94000000-0x9bffffff pref]
[   18.893878] pcmcia_socket pcmcia_socket0: cs: memory probe 0x94000000-0x9bffffff: excluding 0x94000000-0x9bffffff
[   18.902960] yenta_cardbus 0000:08:03.1: CardBus bridge found [10cf:131e]
[   18.903216] serio: Serial port ttyS4
[   18.913584] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   18.915040] ath5k phy0: Atheros AR5414 chip found (MAC: 0xa3, PHY: 0x61)
[   19.004327] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   19.029275] yenta_cardbus 0000:08:03.1: ISA IRQ mask 0x0ca8, PCI irq 16
[   19.029282] yenta_cardbus 0000:08:03.1: Socket status: 30000410
[   19.029287] pci_bus 0000:08: Raising subordinate bus# of parent bus (#08) from #0c to #10
[   19.029329] yenta_cardbus 0000:08:03.1: pcmcia: parent PCI bridge window: [io  0x3000-0x3fff]
[   19.029333] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3000-0x3fff: excluding 0x3000-0x30ff 0x3400-0x34ff 0x3800-0x38ff 0x3c00-0x3cff
[   19.038469] yenta_cardbus 0000:08:03.1: pcmcia: parent PCI bridge window: [mem 0xf0200000-0xf02fffff]
[   19.038475] pcmcia_socket pcmcia_socket1: cs: memory probe 0xf0200000-0xf02fffff: excluding 0xf0200000-0xf020ffff
[   19.038493] yenta_cardbus 0000:08:03.1: pcmcia: parent PCI bridge window: [mem 0x94000000-0x9bffffff pref]
[   19.038497] pcmcia_socket pcmcia_socket1: cs: memory probe 0x94000000-0x9bffffff: excluding 0x94000000-0x9bffffff
[   19.320784] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   19.320790] cfg80211: World regulatory domain updated:
[   19.320793] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   19.320797] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.320801] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.320805] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   19.320808] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.320812] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.411823] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x220-0x227 0x2e8-0x2ef 0x370-0x377
[   19.413790] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   19.414638] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff: clean.
[   19.415316] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7: clean.
[   19.416100] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   19.416140] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   19.416177] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   19.416211] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff: clean.
[   19.585481] psmouse serio4: synaptics: Touchpad model: 1, fw: 6.2, id: 0x1a0b1, caps: 0xa04713/0x202000/0x0
[   19.618398] init: failsafe main process (880) killed by TERM signal
[   19.624772] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input8
[   19.754880] ppdev: user-space parallel port driver
[   19.775491] Bluetooth: Core ver 2.16
[   19.777666] NET: Registered protocol family 31
[   19.777671] Bluetooth: HCI device and connection manager initialized
[   19.777676] Bluetooth: HCI socket layer initialized
[   19.777679] Bluetooth: L2CAP socket layer initialized
[   19.777689] Bluetooth: SCO socket layer initialized
[   19.797241] type=1400 audit(1370709263.513:5): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=969 comm="apparmor_parser"
[   19.797973] type=1400 audit(1370709263.513:6): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=969 comm="apparmor_parser"
[   19.812087] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   19.812092] Bluetooth: BNEP filters: protocol multicast
[   19.831003] type=1400 audit(1370709263.545:7): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=986 comm="apparmor_parser"
[   19.833533] type=1400 audit(1370709263.549:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=985 comm="apparmor_parser"
[   19.834699] type=1400 audit(1370709263.549:9): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=986 comm="apparmor_parser"
[   19.835040] type=1400 audit(1370709263.549:10): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=986 comm="apparmor_parser"
[   19.855656] type=1400 audit(1370709263.569:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/telepathy/mission-control-5" pid=989 comm="apparmor_parser"
[   19.873061] Bluetooth: RFCOMM TTY layer initialized
[   19.873069] Bluetooth: RFCOMM socket layer initialized
[   19.873071] Bluetooth: RFCOMM ver 1.11
[   19.925923] [drm] initialized overlay support
[   19.980041] pcmcia_socket pcmcia_socket1: pccard: PCMCIA card inserted into slot 1
[   19.980052] pcmcia_socket pcmcia_socket1: cs: memory probe 0xf0210000-0xf02fffff:
[   20.008757] sky2 0000:02:00.0: eth0: enabling interface
[   20.020322] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.021084] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   20.049431] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x100-0x3af: excluding 0x170-0x177 0x1f0-0x1f7 0x220-0x227 0x2e8-0x2ef 0x370-0x377
[   20.051460] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x3e0-0x4ff: excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   20.052423] pcmcia_socket pcmcia_socket1: cs: IO port probe 0x820-0x8ff: clean.
[   20.053128] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xc00-0xcf7: clean.
[   20.053915] pcmcia_socket pcmcia_socket1: cs: memory probe 0x0c0000-0x0fffff: excluding 0xc0000-0xc7fff 0xcc000-0xcffff 0xdc000-0xfffff
[   20.053956] pcmcia_socket pcmcia_socket1: cs: memory probe 0xa0000000-0xa0ffffff: excluding 0xa0000000-0xa0ffffff
[   20.053994] pcmcia_socket pcmcia_socket1: cs: memory probe 0x60000000-0x60ffffff: excluding 0x60000000-0x60ffffff
[   20.054028] pcmcia_socket pcmcia_socket1: cs: IO port probe 0xa00-0xaff: clean.
[   20.059954]  excluding 0xf02fe000-0xf030bfff
[   20.064657] pcmcia 1.0: pcmcia: registering new device pcmcia1.0 (IRQ: 3)
[   20.078790] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.081729] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   20.187587] init: alsa-restore main process (1041) terminated with status 19
[   20.196255] fbcon: inteldrmfb (fb0) is primary device
[   20.196988] Console: switching to colour frame buffer device 128x48
[   20.197026] fb0: inteldrmfb frame buffer device
[   20.197029] drm: registered panic notifier
[   20.197101] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   20.197173] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[   20.197263] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   20.197300] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   20.308208] init: plymouth-splash main process (1132) terminated with status 2
[   20.604324] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   20.604533] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   20.604706] input: HDA Intel Dock Line-Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   20.909638] input: Wacom Serial Penabled Touchscreen as /devices/pnp0/00:04/tty/ttyS4/serio5/input/input12
[   20.925664] init: plymouth-stop pre-start process (1278) terminated with status 1
[   28.383469] wlan0: authenticate with 00:14:bf:27:c0:b7 (try 1)
[   28.384966] wlan0: authenticated
[   28.391566] wlan0: associate with 00:14:bf:27:c0:b7 (try 1)
[   28.393669] wlan0: RX AssocResp from 00:14:bf:27:c0:b7 (capab=0x411 status=0 aid=4)
[   28.393674] wlan0: associated
[   28.394388] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   38.752049] wlan0: no IPv6 routers present
[   66.580088] usb 5-2: new full-speed USB device number 2 using uhci_hcd
[   66.754628] hub 5-2:1.0: USB hub found
[   66.756329] hub 5-2:1.0: 4 ports detected
[   67.037489] usb 5-2.1: new full-speed USB device number 3 using uhci_hcd
[   67.138540] usb 5-2.1: not running at top speed; connect to a high speed hub
[   67.255834] keucr: module is from the staging directory, the quality is unknown, you have been warned.
[   67.256551] usb --- usb_stor_init start
[   67.256581] usb --- eucr_probe
[   67.256652] usb --- associate_dev
[   67.256663] usb --- get_device_info
[   67.256665] usb --- get_transport
[   67.256667] usb --- get_protocol
[   67.256669] us->pusb_dev->descriptor.idVendor = 58f
[   67.256671] us->pusb_dev->descriptor.idProduct = 6366
[   67.256674] usb --- get_pipes
[   67.256676] usb --- usb_stor_acquire_resources
[   67.256709] scsi6 : SCSI emulation for USB Mass Storage devices
[   67.256822] usb --- usb_stor_control_thread
[   67.256845] usb --- usb_stor_scan_thread
[   67.256847] EUCR : device found at 3
[   67.260600] data transfer fail ---
[   67.260605] usb --- quiesce_and_remove_host
[   67.260687] usb --- eucr_probe failed
[   67.260689] usb --- release_everything
[   67.260691] usb --- usb_stor_release_resources
[   67.260693] SM_FreeMem start
[   67.260720] usb --- dissociate_dev
[   67.260742] eucr: probe of 5-2.1:1.0 failed with error 3
[   67.260764] usbcore: registered new interface driver eucr
[   67.260767] ENE USB Mass Storage support registered.
[   67.273029] Initializing USB Mass Storage driver...
[   67.273200] scsi7 : usb-storage 5-2.1:1.0
[   67.273314] usbcore: registered new interface driver usb-storage
[   67.273316] USB Mass Storage support registered.
[   88.937453] usb 5-2.1: reset full-speed USB device number 3 using uhci_hcd
[   98.451280] scsi 7:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[   98.453298] sd 7:0:0:0: Attached scsi generic sg2 type 0
[   98.464240] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[  151.616793] usb 5-2.1: USB disconnect, device number 3
[  153.865918] usb 5-2.3: new full-speed USB device number 4 using uhci_hcd
[  153.966959] usb 5-2.3: not running at top speed; connect to a high speed hub
[  153.993086] usb --- eucr_probe
[  153.993238] usb --- associate_dev
[  153.993245] usb --- get_device_info
[  153.993248] usb --- get_transport
[  153.993252] usb --- get_protocol
[  153.993256] us->pusb_dev->descriptor.idVendor = 58f
[  153.993261] us->pusb_dev->descriptor.idProduct = 6366
[  153.993265] usb --- get_pipes
[  153.993269] usb --- usb_stor_acquire_resources
[  153.993307] scsi8 : SCSI emulation for USB Mass Storage devices
[  153.993567] usb --- usb_stor_control_thread
[  153.993590] usb --- usb_stor_scan_thread
[  153.993595] EUCR : device found at 4
[  153.996952] data transfer fail ---
[  153.996959] usb --- quiesce_and_remove_host
[  153.997109] usb --- eucr_probe failed
[  153.997113] usb --- release_everything
[  153.997117] usb --- usb_stor_release_resources
[  153.997121] SM_FreeMem start
[  153.997274] usb --- dissociate_dev
[  153.997316] eucr: probe of 5-2.3:1.0 failed with error 3
[  153.997487] scsi9 : usb-storage 5-2.3:1.0
[  175.913933] usb 5-2.3: reset full-speed USB device number 4 using uhci_hcd
[  185.426762] scsi 9:0:0:0: Direct-Access     Multi    Flash Reader     1.00 PQ: 0 ANSI: 0
[  185.429182] sd 9:0:0:0: Attached scsi generic sg2 type 0
[  185.438835] sd 9:0:0:0: [sdb] Attached SCSI removable disk
dogs@dogs-LifeBook-T4210:~$ 

```

---

