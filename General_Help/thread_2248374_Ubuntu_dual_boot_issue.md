---
title: "Ubuntu dual boot issue"
date: 2014-10-14
forum: General Help
---

### Post by eipapp on 2014-10-14
I have my machine set up to dual boot Ubuntu  14.04 along with Mint 17 KDE. My issue is that when I select Mint at the option menu I'm never sure whether it will boot up or not. When it doesn't, I get a blank screen and then have to re-boot my computer. This never seems to happen with Ubuntu only with KDE. Does anyone have an idea as to why the KDE is so unstable and how to fix it?
I've included a boot repair URL if it will help to analyze the problem.

Thanks in advance for any help,
Bruce

[HTML]http://paste2.org/9pECxKa8[/HTML]

---

### Post by oldfred on 2014-10-14
I do not see any boot issue.

It does look like Boot-Repair installed Mint's grub to MBR. So it now is first in boot menu.
You want whichever system you use the most to be in MBR and default boot.

Perhaps video driver issue? Are both using same AMD driver?
You can try removing quiet spash in grub with each boot and see if you get errors. Or look in log files to see if error has been saved.

System log or log file viewer and look at dmseg. With 14.04 the tiny icon in upper right let me open a new file to use dmseg. Or just open /var/log/dmesg.

---

### Post by eipapp on 2014-10-14
Ran dmesg and this is what it returned. Means nothing to me but maybe will answer some of your questions OldFred:



```
 1.265740] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.265744] usb usb2: Product: EHCI Host Controller
[    1.265748] usb usb2: Manufacturer: Linux 3.13.0-37-generic ehci_hcd
[    1.265752] usb usb2: SerialNumber: 0000:00:13.2
[    1.266282] hub 2-0:1.0: USB hub found
[    1.266304] hub 2-0:1.0: 5 ports detected
[    1.266986] ehci-platform: EHCI generic platform driver
[    1.267009] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.267012] ohci-pci: OHCI PCI platform driver
[    1.267247] ohci-pci 0000:00:12.0: OHCI PCI host controller
[    1.267262] ohci-pci 0000:00:12.0: new USB bus registered, assigned bus number 3
[    1.267311] ohci-pci 0000:00:12.0: irq 18, io mem 0xfeb4a000
[    1.325603] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.325613] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.325617] usb usb3: Product: OHCI PCI host controller
[    1.325621] usb usb3: Manufacturer: Linux 3.13.0-37-generic ohci_hcd
[    1.325624] usb usb3: SerialNumber: 0000:00:12.0
[    1.326180] hub 3-0:1.0: USB hub found
[    1.326270] hub 3-0:1.0: 5 ports detected
[    1.326942] ohci-pci 0000:00:13.0: OHCI PCI host controller
[    1.326954] ohci-pci 0000:00:13.0: new USB bus registered, assigned bus number 4
[    1.326983] ohci-pci 0000:00:13.0: irq 18, io mem 0xfeb48000
[    1.385561] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.385571] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.385575] usb usb4: Product: OHCI PCI host controller
[    1.385579] usb usb4: Manufacturer: Linux 3.13.0-37-generic ohci_hcd
[    1.385583] usb usb4: SerialNumber: 0000:00:13.0
[    1.386119] hub 4-0:1.0: USB hub found
[    1.386210] hub 4-0:1.0: 5 ports detected
[    1.386930] ohci-pci 0000:00:14.5: OHCI PCI host controller
[    1.386941] ohci-pci 0000:00:14.5: new USB bus registered, assigned bus number 5
[    1.386972] ohci-pci 0000:00:14.5: irq 18, io mem 0xfeb46000
[    1.445539] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.445548] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.445552] usb usb5: Product: OHCI PCI host controller
[    1.445556] usb usb5: Manufacturer: Linux 3.13.0-37-generic ohci_hcd
[    1.445560] usb usb5: SerialNumber: 0000:00:14.5
[    1.446070] hub 5-0:1.0: USB hub found
[    1.446160] hub 5-0:1.0: 2 ports detected
[    1.446332] ohci-platform: OHCI generic platform driver
[    1.446354] uhci_hcd: USB Universal Host Controller Interface driver
[    1.446631] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.446642] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 6
[    1.446904] xhci_hcd 0000:00:10.0: irq 44 for MSI/MSI-X
[    1.446918] xhci_hcd 0000:00:10.0: irq 45 for MSI/MSI-X
[    1.446930] xhci_hcd 0000:00:10.0: irq 46 for MSI/MSI-X
[    1.447085] usb usb6: New USB device found, idVendor=1d6b, idProduct=0002
[    1.447089] usb usb6: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.447093] usb usb6: Product: xHCI Host Controller
[    1.447097] usb usb6: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.447100] usb usb6: SerialNumber: 0000:00:10.0
[    1.447582] hub 6-0:1.0: USB hub found
[    1.447673] hub 6-0:1.0: 2 ports detected
[    1.447900] xhci_hcd 0000:00:10.0: xHCI Host Controller
[    1.447909] xhci_hcd 0000:00:10.0: new USB bus registered, assigned bus number 7
[    1.450330] usb usb7: New USB device found, idVendor=1d6b, idProduct=0003
[    1.450335] usb usb7: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.450338] usb usb7: Product: xHCI Host Controller
[    1.450343] usb usb7: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.450346] usb usb7: SerialNumber: 0000:00:10.0
[    1.450730] hub 7-0:1.0: USB hub found
[    1.450820] hub 7-0:1.0: 2 ports detected
[    1.457769] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.458414] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.458433] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.459042] mousedev: PS/2 mouse device common for all mice
[    1.459725] rtc_cmos 00:04: RTC can wake from S4
[    1.459887] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.459926] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.460070] device-mapper: uevent: version 1.0.3
[    1.460206] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    1.460219] ledtrig-cpu: registered to indicate activity on CPUs
[    1.460408] TCP: cubic registered
[    1.460588] NET: Registered protocol family 10
[    1.460944] NET: Registered protocol family 17
[    1.460973] Key type dns_resolver registered
[    1.461531] Loading compiled-in X.509 certificates
[    1.463758] Loaded X.509 cert 'Magrathea: Glacier signing key: 2cb1133b35f95a9e24deabeeb12ba449bcbabbc9'
[    1.463784] registered taskstats version 1
[    1.469459] Key type trusted registered
[    1.474275] Key type encrypted registered
[    1.479001] AppArmor: AppArmor sha1 policy hashing enabled
[    1.479013] IMA: No TPM chip found, activating TPM-bypass!
[    1.479601] regulator-dummy: disabling
[    1.479743]   Magic number: 2:390:186
[    1.479943] rtc_cmos 00:04: setting system clock to 2014-10-14 16:11:57 UTC (1413303117)
[    1.480142] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.480347] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.480350] EDD information not available.
[    1.480437] PM: Hibernation image not present or could not be loaded.
[    1.483361] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.483372] Write protecting the kernel read-only data: 12288k
[    1.488564] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    1.492811] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.529434] systemd-udevd[99]: starting version 204
[    1.586194] ahci 0000:00:11.0: version 3.0
[    1.587375] ahci 0000:00:11.0: irq 47 for MSI/MSI-X
[    1.587530] ahci 0000:00:11.0: AHCI 0001.0300 32 slots 3 ports 6 Gbps 0xd impl SATA mode
[    1.587537] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pio slum part sxs 
[    1.589167] scsi0 : ahci
[    1.589340] scsi1 : ahci
[    1.589463] scsi2 : ahci
[    1.589581] scsi3 : ahci
[    1.589699] ata1: SATA max UDMA/133 abar m2048@0xfeb4b000 port 0xfeb4b100 irq 47
[    1.589703] ata2: DUMMY
[    1.589707] ata3: SATA max UDMA/133 abar m2048@0xfeb4b000 port 0xfeb4b200 irq 47
[    1.589711] ata4: SATA max UDMA/133 abar m2048@0xfeb4b000 port 0xfeb4b280 irq 47
[    1.614770] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.615258] r8169 0000:03:00.0: irq 48 for MSI/MSI-X
[    1.615632] r8169 0000:03:00.0 eth0: RTL8105e at 0xffffc90000c7a000, 4c:72:b9:9d:ff:82, XID 00a00000 IRQ 48
[    1.616810] rtsx_pci 0000:05:00.0: irq 49 for MSI/MSI-X
[    1.616837] rtsx_pci 0000:05:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 49
[    1.825256] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    1.909155] ata4: SATA link down (SStatus 0 SControl 300)
[    1.909212] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    1.909254] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    1.910508] ata1.00: ATA-8: ST500DM002-1BD142, HP73, max UDMA/100
[    1.910520] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    1.912345] ata1.00: configured for UDMA/100
[    1.912577] ata3.00: ATAPI: hp       DVDRAM GT50N, R703, max UDMA/100
[    1.912910] scsi 0:0:0:0: Direct-Access     ATA      ST500DM002-1BD14 HP73 PQ: 0 ANSI: 5
[    1.913301] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.913324] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    1.913329] sd 0:0:0:0: [sda] 4096-byte physical blocks
[    1.913458] sd 0:0:0:0: [sda] Write Protect is off
[    1.913464] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.913688] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.915678] ata3.00: configured for UDMA/100
[    1.919915] scsi 2:0:0:0: CD-ROM            hp       DVDRAM GT50N     R703 PQ: 0 ANSI: 5
[    1.926873] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    1.926885] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.927164] sr 2:0:0:0: Attached scsi CD-ROM sr0
[    1.927418] sr 2:0:0:0: Attached scsi generic sg1 type 5
[    1.958424]  sda: sda1 sda2 < sda5 sda6 >
[    1.960041] sd 0:0:0:0: [sda] Attached SCSI disk
[    2.075264] usb 2-1: New USB device found, idVendor=04f2, idProduct=b34a
[    2.075275] usb 2-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.075280] usb 2-1: Product: HP High Definition 1MP Webcam
[    2.075284] usb 2-1: Manufacturer: Sunplus IT Co 
[    2.164674] tsc: Refined TSC clocksource calibration: 1696.913 MHz
[    2.386065] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    2.488806] usb 6-1: new full-speed USB device number 2 using xhci_hcd
[    2.533594] usb 6-1: New USB device found, idVendor=046d, idProduct=c52b
[    2.533610] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.533619] usb 6-1: Product: USB Receiver
[    2.533626] usb 6-1: Manufacturer: Logitech
[    2.672568] usb 3-1: new full-speed USB device number 2 using ohci-pci
[    2.847441] usb 3-1: New USB device found, idVendor=045e, idProduct=0745
[    2.847458] usb 3-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.847466] usb 3-1: Product: Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v7.0
[    2.847473] usb 3-1: Manufacturer: Microsoft
[    3.164480] Switched to clocksource tsc
[    3.176334] random: init urandom read with 103 bits of entropy available
[    3.644438] random: nonblocking pool is initialized
[    9.619811] Adding 5849084k swap on /dev/sda5.  Priority:-1 extents:1 across:5849084k FS
[    9.676542] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    9.844634] systemd-udevd[272]: starting version 204
[    9.989111] lp: driver loaded but no devices found
[   10.006618] ppdev: user-space parallel port driver
[   10.064434] [drm] Initialized drm 1.1.0 20060810
[   10.086203] ACPI: Video Device [VGA] (multi-head: yes  rom: no  post: no)
[   10.086261] [Firmware Bug]: ACPI: No _BQC method, cannot determine initial brightness
[   10.147831] [drm] radeon kernel modesetting enabled.
[   10.150649] [drm] initializing kernel modesetting (PALM 0x1002:0x9808 0x103C:0x2AF0).
[   10.150748] [drm] register mmio base: 0xFEB00000
[   10.150751] [drm] register mmio size: 262144
[   10.150859] ATOM BIOS: AMD
[   10.151459] radeon 0000:00:01.0: VRAM: 384M 0x0000000000000000 - 0x0000000017FFFFFF (384M used)
[   10.151468] radeon 0000:00:01.0: GTT: 1024M 0x0000000018000000 - 0x0000000057FFFFFF
[   10.151473] [drm] Detected VRAM RAM=384M, BAR=256M
[   10.151475] [drm] RAM width 32bits DDR
[   10.151928] acpi device:19: registered as cooling_device2
[   10.152082] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input5
[   10.152984] [TTM] Zone  kernel: Available graphics memory: 2839370 kiB
[   10.152992] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   10.152994] [TTM] Initializing pool allocator
[   10.153003] [TTM] Initializing DMA pool allocator
[   10.153062] [drm] radeon: 384M of VRAM memory ready
[   10.153066] [drm] radeon: 1024M of GTT memory ready.
[   10.153096] [drm] Loading PALM Microcode
[   10.368221] cfg80211: Calling CRDA to update world regulatory domain
[   10.420975] type=1400 audit(1413303126.441:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=346 comm="apparmor_parser"
[   10.420992] type=1400 audit(1413303126.441:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=346 comm="apparmor_parser"
[   10.421002] type=1400 audit(1413303126.441:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=346 comm="apparmor_parser"
[   10.421804] type=1400 audit(1413303126.441:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=346 comm="apparmor_parser"
[   10.421817] type=1400 audit(1413303126.441:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=346 comm="apparmor_parser"
[   10.422235] type=1400 audit(1413303126.441:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=346 comm="apparmor_parser"
[   10.450383] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   10.467758] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   10.524321] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   10.565745] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   10.585242] kvm: disabled by bios
[   10.597755] [drm] PCIE GART of 1024M enabled (table at 0x0000000000273000).
[   10.625918] radeon 0000:00:01.0: WB enabled
[   10.625932] radeon 0000:00:01.0: fence driver on ring 0 use gpu addr 0x0000000018000c00 and cpu addr 0xffff8800a1bc1c00
[   10.625938] radeon 0000:00:01.0: fence driver on ring 3 use gpu addr 0x0000000018000c0c and cpu addr 0xffff8800a1bc1c0c
[   10.626857] radeon 0000:00:01.0: fence driver on ring 5 use gpu addr 0x0000000000072118 and cpu addr 0xffffc900113b2118
[   10.626863] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   10.626866] [drm] Driver supports precise vblank timestamp query.
[   10.626916] radeon 0000:00:01.0: irq 50 for MSI/MSI-X
[   10.626952] radeon 0000:00:01.0: radeon: using MSI.
[   10.627001] [drm] radeon: irq initialized.
[   10.649171] Linux video capture interface: v2.00
[   10.649412] hidraw: raw HID events driver (C) Jiri Kosina
[   10.666920] [drm] ring test on 0 succeeded in 1 usecs
[   10.666988] [drm] ring test on 3 succeeded in 1 usecs
[   10.680460] uvcvideo: Found UVC 1.00 device HP High Definition 1MP Webcam (04f2:b34a)
[   10.697982] input: HP High Definition 1MP Webcam as /devices/pci0000:00/0000:00:13.2/usb2/2-1/2-1:1.0/input/input6
[   10.698118] usbcore: registered new interface driver uvcvideo
[   10.698122] USB Video Class driver (1.1.1)
[   10.719098] usbcore: registered new interface driver usbhid
[   10.719106] usbhid: USB HID core driver
[   10.738157] ip_tables: (C) 2000-2006 Netfilter Core Team
[   10.755122] [drm] ring test on 5 succeeded in 1 usecs
[   10.764903] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   10.796518] [drm] UVD initialized successfully.
[   10.810603] [drm] Enabling audio 0 support
[   10.810673] [drm] ib test on ring 0 succeeded in 0 usecs
[   10.810714] [drm] ib test on ring 3 succeeded in 0 usecs
[   10.827902] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   10.844508] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   10.844699] [drm] ib test on ring 5 succeeded
[   10.878491] [drm] radeon atom DIG backlight initialized
[   10.878505] [drm] Radeon Display Connectors
[   10.878508] [drm] Connector 0:
[   10.878512] [drm]   DP-1
[   10.878514] [drm]   HPD1
[   10.878519] [drm]   DDC: 0x6430 0x6430 0x6434 0x6434 0x6438 0x6438 0x643c 0x643c
[   10.878522] [drm]   Encoders:
[   10.878524] [drm]     DFP1: INTERNAL_UNIPHY
[   10.878527] [drm] Connector 1:
[   10.878530] [drm]   LVDS-1
[   10.878531] [drm]   HPD2
[   10.878535] [drm]   DDC: 0x6440 0x6440 0x6444 0x6444 0x6448 0x6448 0x644c 0x644c
[   10.878537] [drm]   Encoders:
[   10.878539] [drm]     LCD1: INTERNAL_UNIPHY
[   10.878541] [drm]     LCD1: TRAVIS
[   10.878543] [drm] Connector 2:
[   10.878546] [drm]   VGA-1
[   10.878549] [drm]   DDC: 0x64d8 0x64d8 0x64dc 0x64dc 0x64e0 0x64e0 0x64e4 0x64e4
[   10.878551] [drm]   Encoders:
[   10.878556] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   10.893351] [drm] Internal thermal controller without fan control
[   10.893460] [drm] Found smc ucode version: 0x00010601
[   10.897395] [drm] radeon: dpm initialized
[   11.192738] [drm] fb mappable at 0xC0477000
[   11.192749] [drm] vram apper at 0xC0000000
[   11.192752] [drm] size 8294400
[   11.192755] [drm] fb depth is 24
[   11.192757] [drm]    pitch is 7680
[   11.193073] fbcon: radeondrmfb (fb0) is primary device
[   11.401534] Console: switching to colour frame buffer device 240x67
[   11.413621] radeon 0000:00:01.0: fb0: radeondrmfb frame buffer device
[   11.413623] radeon 0000:00:01.0: registered panic notifier
[   11.423313] [drm] Initialized radeon 2.36.0 20080528 for 0000:00:01.0 on minor 0
[   11.423569] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[   11.427628] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
[   11.432993] hda-intel 0000:00:14.2: Using LPIB position fix
[   11.462027] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[   11.499136] hda_codec: ALC269VC: SKU not ready 0x411111f0
[   11.499713] autoconfig: line_outs=1 (0x1b/0x0/0x0/0x0/0x0) type:line
[   11.499715]    speaker_outs=1 (0x14/0x0/0x0/0x0/0x0)
[   11.499717]    hp_outs=1 (0x15/0x0/0x0/0x0/0x0)
[   11.499718]    mono: mono_out=0x0
[   11.499719]    inputs:
[   11.499722]      Mic=0x18
[   11.499723]      Internal Mic=0x12
[   11.499726] realtek: No valid SSID, checking pincfg 0x411111f0 for NID 0x1d
[   11.499727] realtek: Enable default setup for auto mode as fallback
[   11.633121] input: HD-Audio Generic Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[   11.635046] input: HD-Audio Generic Line Out as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[   11.635186] input: HD-Audio Generic Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[   11.903784] cfg80211: World regulatory domain updated:
[   11.903796] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   11.903800] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.903804] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.903808] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   11.903811] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   11.903814] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   12.036941] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v7.0 as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.0/input/input10
[   12.041568] hid-generic 0003:045E:0745.0004: input,hidraw0: USB HID v1.11 Keyboard [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v7.0] on usb-0000:00:12.0-1/input0
[   12.048321] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v7.0 as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.1/input/input11
[   12.049820] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:10.0-1/input2
[   12.054634] hid-generic 0003:045E:0745.0005: input,hidraw2: USB HID v1.11 Mouse [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v7.0] on usb-0000:00:12.0-1/input1
[   12.056981] input: Logitech Unifying Device. Wireless PID:4013 as /devices/pci0000:00/0000:00:10.0/usb6/6-1/6-1:1.2/0003:046D:C52B.0003/input/input12
[   12.059350] logitech-djdevice 0003:046D:C52B.0007: input,hidraw3: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:4013] on usb-0000:00:10.0-1:1
[   12.075676] input: Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v7.0 as /devices/pci0000:00/0000:00:12.0/usb3/3-1/3-1:1.2/input/input13
[   12.083062] hid-generic 0003:045E:0745.0006: input,hiddev0,hidraw4: USB HID v1.11 Device [Microsoft Microsoft\xffffffc2\xffffffae\xffffffae 2.4GHz Transceiver v7.0] on usb-0000:00:12.0-1/input2
[   12.429425] init: failsafe main process (605) killed by TERM signal
[   12.958613] Bluetooth: Core ver 2.17
[   12.958711] NET: Registered protocol family 31
[   12.958715] Bluetooth: HCI device and connection manager initialized
[   12.958734] Bluetooth: HCI socket layer initialized
[   12.958739] Bluetooth: L2CAP socket layer initialized
[   12.958749] Bluetooth: SCO socket layer initialized
[   12.977430] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   12.977439] Bluetooth: BNEP filters: protocol multicast
[   12.977461] Bluetooth: BNEP socket layer initialized
[   13.260482] Bluetooth: RFCOMM TTY layer initialized
[   13.260511] Bluetooth: RFCOMM socket layer initialized
[   13.260532] Bluetooth: RFCOMM ver 1.11
[   13.353578] init: samba-ad-dc main process (695) terminated with status 1
[   14.072704] r8169 0000:03:00.0 eth0: link down
[   14.072769] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.078110] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   14.099893] type=1400 audit(1413303130.125:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=766 comm="apparmor_parser"
[   14.099914] type=1400 audit(1413303130.125:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=766 comm="apparmor_parser"
[   14.100721] type=1400 audit(1413303130.125:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=766 comm="apparmor_parser"
[   14.117407] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   14.147810] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   14.328279] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.328905] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   14.647991] init: cups main process (774) killed by HUP signal
[   14.648024] init: cups main process ended, respawning
[   15.127234] type=1400 audit(1413303131.153:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=882 comm="apparmor_parser"
[   16.431955] audit_printk_skb: 156 callbacks suppressed
[   16.431966] type=1400 audit(1413303132.457:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=1085 comm="apparmor_parser"
[   16.632982] init: gdm main process (1014) killed by TERM signal
[   16.654816] wlan0: authenticate with 58:6d:8f:5a:43:8f
[   16.670287] wlan0: send auth to 58:6d:8f:5a:43:8f (try 1/3)
[   16.672372] wlan0: authenticated
[   16.674133] wlan0: associate with 58:6d:8f:5a:43:8f (try 1/3)
[   16.677531] wlan0: RX AssocResp from 58:6d:8f:5a:43:8f (capab=0x411 status=0 aid=2)
[   16.677747] wlan0: associated
[   16.677801] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   16.795971] wlan0: deauthenticating from 58:6d:8f:5a:43:8f by local choice (reason=2)
[   16.822692] cfg80211: Calling CRDA to update world regulatory domain
[   16.822900] wlan0: authenticate with 58:6d:8f:5a:43:8f
[   16.830289] wlan0: send auth to 58:6d:8f:5a:43:8f (try 1/3)
[   16.830658] cfg80211: World regulatory domain updated:
[   16.830663] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   16.830667] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.830671] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.830674] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   16.830677] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.830680] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   16.831985] wlan0: authenticated
[   16.834106] wlan0: associate with 58:6d:8f:5a:43:8f (try 1/3)
[   16.837463] wlan0: RX AssocResp from 58:6d:8f:5a:43:8f (capab=0x411 status=0 aid=2)
[   16.837598] wlan0: associated
[   18.150843] init: plymouth-upstart-bridge main process ended, respawning
[   18.173217] init: plymouth-upstart-bridge main process (1178) terminated with status 1
[   18.173256] init: plymouth-upstart-bridge main process ended, respawning
[   19.287302] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   20.555357] [UFW BLOCK] IN=wlan0 OUT= MAC=68:94:23:41:a2:4a:58:6d:8f:5a:43:8d:08:00 SRC=128.121.22.133 DST=192.168.1.120 LEN=83 TOS=0x00 PREC=0x00 TTL=56 ID=28306 DF PROTO=TCP SPT=443 DPT=44657 WINDOW=143 RES=0x00 ACK PSH URGP=0 
[   44.556921] type=1400 audit(1413303160.601:65): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1754 comm="apparmor_parser"
[   44.556945] type=1400 audit(1413303160.601:66): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1754 comm="apparmor_parser"
[   44.557862] type=1400 audit(1413303160.605:67): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1754 comm="apparmor_parser"
[   49.813314] [UFW BLOCK] IN=wlan0 OUT= MAC=68:94:23:41:a2:4a:58:6d:8f:5a:43:8d:08:00 SRC=128.121.22.133 DST=192.168.1.120 LEN=83 TOS=0x00 PREC=0x00 TTL=56 ID=28307 DF PROTO=TCP SPT=443 DPT=44657 WINDOW=143 RES=0x00 ACK PSH URGP=0 
[   98.830114] systemd-hostnamed[2461]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  110.076856] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  111.771596] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:b0:65:bd:e3:40:1d:08:00 SRC=192.168.1.146 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=47342 PROTO=2 
[  236.086849] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  239.796748] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:b0:65:bd:e3:40:1d:08:00 SRC=192.168.1.146 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=54638 PROTO=2 
[  361.945235] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  363.684717] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  487.803852] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  490.876538] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:b0:65:bd:e3:40:1d:08:00 SRC=192.168.1.146 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=4489 PROTO=2 
[  519.195405] systemd-hostnamed[2987]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  613.765807] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  619.700567] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  739.625149] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 
[  744.950564] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:fb:b0:65:bd:e3:40:1d:08:00 SRC=192.168.1.146 DST=224.0.0.251 LEN=32 TOS=0x00 PREC=0x00 TTL=1 ID=55188 PROTO=2 

```

---

### Post by oldfred on 2014-10-14
The entries with larger time gaps are usually an issue.
Seems to go along ok till here:
> 
[   49.813314] [UFW BLOCK] IN=wlan0 OUT= MAC=68:94:23:41:a2:4a:58:6d:8f:5a:43:8d:08:00 SRC=128.121.22.133 DST=192.168.1.120 LEN=83 TOS=0x00 PREC=0x00 TTL=56 ID=28307 DF PROTO=TCP SPT=443 DPT=44657 WINDOW=143 RES=0x00 ACK PSH URGP=0 
[   98.830114] systemd-hostnamed[2461]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  110.076856] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:58:6d:8f:5a:43:8d:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=28 TOS=0x00 PREC=0x00 TTL=1 ID=0 DF PROTO=2 


Are you using systemd?  Not familar with that, it still seems to be testing. 
Some have said it works well, others seem to have issues.

And it says something about nss-myhostname should be installed.

Is this your Ubuntu or your Mint?

Do not post full dmesg from your other install, but post any with long time gaps like above if also issues.

---

### Post by eipapp on 2014-10-14
OK, installed nss-myhosttname

Will let you know if that made any difference.

Thanks,
Bruce

---

### Post by eipapp on 2014-10-14
Unfortunately, installing nss-myhostname had no affect. The problem persists.

---

### Post by oldfred on 2014-10-14
Have not tried systemd yet, so do not know about those issues.

Some other threads on systemd

google search  site:ubuntuforums.org systemd

[https://www.google.com/search?hl=en&source=hp&q=site%3Aubuntuforums.org+systemd&btnG=Google+Search&gbv=2&gws_rd=ssl](https://www.google.com/search?hl=en&source=hp&q=site%3Aubuntuforums.org+systemd&btnG=Google+Search&gbv=2&gws_rd=ssl)

---

### Post by Dennis N on 2014-10-15
Hello eipapp,

What make of graphics system does this computer have - Intel, Nvidia, or AMD? I don't see it mentioned anywhere. Also, how old is the computer?

---

### Post by eipapp on 2014-10-15
Bought the machine 8 months ago.
AMD E2-1800 API w/Radeon HD Graphics x2

---

### Post by Dennis N on 2014-10-15
Maybe you already tried it, but have you tried switching the graphics driver? Open Source to Proprietary or Proprietary to Open Source?

Well, not quite a comparable situation, but some time ago I had an older AMD powered machine with NVidia Graphics that occasionally never would get to the desktop when using the open source (nouveau) driver (requiring a reset), but worked always with proprietary NVidia driver after changing.

That is the only thing I have thought of as a possible cause.

---

### Post by Dennis N on 2014-10-15
I see the APU is Ubuntu Certified.

[http://www.ubuntu.com/certification/catalog/component/dmi/4458/dmi%3AAMDE2-1800APUwithRadeon%28tm%29HDGraphics/](http://www.ubuntu.com/certification/catalog/component/dmi/4458/dmi%3AAMDE2-1800APUwithRadeon%28tm%29HDGraphics/)

---

### Post by Dennis N on 2014-10-16
Did the change of video driver make any difference? Since your system is Ubuntu Certified, you might have success with Kubuntu if you want a KDE system. At least in your case, you can ditch Mint KDE if nothing further develops since your Ubuntu is working.

Good Luck

---

### Post by eipapp on 2014-10-16
Hi Dennis,

I've been trying to figure out how to change my video driver as you suggested but have to say I'm stumped as to how to do that.
Funny you should mention Kubuntu as I was thinking along the same line. 
How difficut would it be to replace Mint KDE with Kubuntu KDE on my dual boot system ???
This is new territory for me.

Thanks,
Bruce

---

### Post by oldfred on 2014-10-16
It looks like you have some room. 
Using 18GB of 500. :)

 /dev/sda6 ext4 220G 8.0G 201G 4% /
/dev/sda1 ext4 234G 10G 212G 5% /mnt/boot-sav/sda1

I have many installs but allocated about 20 or 25GB to each / (root) and include /home inside root. But then create a large /mnt/data partition and link Documents, Music, etc into each /home so every install has same data. I do not attempt to share a /home as I may want different settings and want same user/password in every install.

So you can use gparted, shrink one of your installs and create a new 25GB / partition and install. If it works great, if not it was a good test.

Different flavors will look different, but process is the same.

 Lots of detail, screenshots and essential info.14.04  Something Else example
[http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html](http://www.dedoimedo.com/computers/ubuntu-14-04-install-guide.html)
[http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation](http://askubuntu.com/questions/343268/how-to-use-manual-partitioning-during-installation)
[http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using](http://askubuntu.com/questions/163962/install-alongside-option-missing-how-do-i-install-ubuntu-beside-windows-using)

I am not suggesting 14.10 yet unless you want to really test new version, but these screens will be similar.

 Kubuntu install screens
[http://www.ubuntugeek.com/kubuntu-14-10-beta-2-screenshots-tour.html](http://www.ubuntugeek.com/kubuntu-14-10-beta-2-screenshots-tour.html)

---

### Post by Dennis N on 2014-10-16
I am not a KDE user, but somewhere in your Settings dialog should be a section for "Additional Drivers" or something like that. It should offer the proprietary driver (sometimes more than one version) if you are using the open-source driver.

To try Kubuntu instead:

Install Kubuntu in the same partition as Mint KDE uses now.  After starting the Kubuntu installer, at the "Installation Type" screen choose the "Something Else" option, then on the next screen, select the Mint KDE partition, press the "change" button below. A dialog will pop up, and you select use as "journalling ext4 filesystem", mount as / and check the format box. At the bottom, choose Install Grub to sda.  Then click "Install Now" button.

That's about it. Good luck.

---

