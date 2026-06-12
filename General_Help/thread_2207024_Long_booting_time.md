---
title: "Long booting time"
date: 2014-02-21
forum: General Help
---

### Post by giannhs905 on 2014-02-21
Can anyone help me fix the booting time of my machine.?it is almost 25 seconds. My dmesg is the following :

[PHP]> `[    4.610922] intel_idle: lapic_timer_reliable_states 0xffffffff
[    4.611001] ipmi message handler version 39.2
[    4.611007] IPMI System Interface driver.
[    4.611023] ipmi_si: Adding default-specified kcs state machine
[    4.611025] ipmi_si: Trying default-specified kcs state machine at i/o address 0xca2, slave address 0x0, irq 0
[    4.611029] ipmi_si: Interface detection failed
[    4.618702] ipmi_si: Adding default-specified smic state machine
[    4.618705] ipmi_si: Trying default-specified smic state machine at i/o address 0xca9, slave address 0x0, irq 0
[    4.618707] ipmi_si: Interface detection failed
[    4.626712] ipmi_si: Adding default-specified bt state machine
[    4.626714] ipmi_si: Trying default-specified bt state machine at i/o address 0xe4, slave address 0x0, irq 0
[    4.626717] ipmi_si: Interface detection failed
[    4.630746] ipmi_si: Unable to find any System Interface(s)
[    4.631872] ACPI: AC Adapter [ACAD] (on-line)
[    4.631945] input: Power Button as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:02/PNP0C0C:00/input/input0
[    4.631949] ACPI: Power Button [PWRB]
[    4.631985] input: Lid Switch as /devices/LNXSYSTM:00/device:00/PNP0C0D:00/input/input1
[    4.632001] ACPI: Lid Switch [LID0]
[    4.632022] input: Power Button as /devices/LNXSYSTM:00/LNXPWRBN:00/input/input2
[    4.632024] ACPI: Power Button [PWRF]
[    4.632391] thermal LNXTHERM:00: registered as thermal_zone0
[    4.632394] ACPI: Thermal Zone [TZ00] (48 C)
[    4.632415] GHES: HEST is not enabled!
[    4.632495] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    4.714884] ACPI: Battery Slot [BAT1] (battery present)
[    4.714978] Linux agpgart interface v0.103
[    4.715883] brd: module loaded
[    4.716301] loop: module loaded
[    4.716544] libphy: Fixed MDIO Bus: probed
[    4.716600] tun: Universal TUN/TAP device driver, 1.6
[    4.716601] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    4.716639] PPP generic driver version 2.4.2
[    4.716671] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    4.716674] ehci-pci: EHCI PCI platform driver
[    4.716779] ehci-pci 0000:00:1a.0: EHCI Host Controller
[    4.716784] ehci-pci 0000:00:1a.0: new USB bus registered, assigned bus number 1
[    4.716795] ehci-pci 0000:00:1a.0: debug port 2
[    4.720689] ehci-pci 0000:00:1a.0: cache line size of 64 is not supported
[    4.720711] ehci-pci 0000:00:1a.0: irq 16, io mem 0xb961d000
[    4.730820] ehci-pci 0000:00:1a.0: USB 2.0 started, EHCI 1.00
[    4.730855] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    4.730857] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.730858] usb usb1: Product: EHCI Host Controller
[    4.730860] usb usb1: Manufacturer: Linux 3.13.0-11-generic ehci_hcd
[    4.730861] usb usb1: SerialNumber: 0000:00:1a.0
[    4.730941] hub 1-0:1.0: USB hub found
[    4.730945] hub 1-0:1.0: 2 ports detected
[    4.731108] ehci-pci 0000:00:1d.0: EHCI Host Controller
[    4.731111] ehci-pci 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    4.731121] ehci-pci 0000:00:1d.0: debug port 2
[    4.735017] ehci-pci 0000:00:1d.0: cache line size of 64 is not supported
[    4.735037] ehci-pci 0000:00:1d.0: irq 23, io mem 0xb961c000
[    4.746877] ehci-pci 0000:00:1d.0: USB 2.0 started, EHCI 1.00
[    4.746908] usb usb2: New USB device found, idVendor=1d6b, idProduct=0002
[    4.746909] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.746911] usb usb2: Product: EHCI Host Controller
[    4.746912] usb usb2: Manufacturer: Linux 3.13.0-11-generic ehci_hcd
[    4.746913] usb usb2: SerialNumber: 0000:00:1d.0
[    4.747029] hub 2-0:1.0: USB hub found
[    4.747035] hub 2-0:1.0: 2 ports detected
[    4.747122] ehci-platform: EHCI generic platform driver
[    4.747129] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.747130] ohci-pci: OHCI PCI platform driver
[    4.747136] ohci-platform: OHCI generic platform driver
[    4.747140] uhci_hcd: USB Universal Host Controller Interface driver
[    4.747238] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    4.747241] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    4.747324] xhci_hcd 0000:00:14.0: cache line size of 64 is not supported
[    4.747341] xhci_hcd 0000:00:14.0: irq 41 for MSI/MSI-X
[    4.747391] usb usb3: New USB device found, idVendor=1d6b, idProduct=0002
[    4.747393] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.747394] usb usb3: Product: xHCI Host Controller
[    4.747395] usb usb3: Manufacturer: Linux 3.13.0-11-generic xhci_hcd
[    4.747397] usb usb3: SerialNumber: 0000:00:14.0
[    4.747549] hub 3-0:1.0: USB hub found
[    4.747566] hub 3-0:1.0: 14 ports detected
[    4.750444] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    4.750447] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 4
[    4.750485] usb usb4: New USB device found, idVendor=1d6b, idProduct=0003
[    4.750487] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    4.750488] usb usb4: Product: xHCI Host Controller
[    4.750489] usb usb4: Manufacturer: Linux 3.13.0-11-generic xhci_hcd
[    4.750490] usb usb4: SerialNumber: 0000:00:14.0
[    4.750614] hub 4-0:1.0: USB hub found
[    4.750624] hub 4-0:1.0: 4 ports detected
[    4.759027] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:MSS4] at 0x60,0x64 irq 1,12
[    4.798258] serio: i8042 KBD port at 0x60,0x64 irq 1
[    4.798263] serio: i8042 AUX port at 0x60,0x64 irq 12
[    4.798443] mousedev: PS/2 mouse device common for all mice
[    4.801229] rtc_cmos 00:06: RTC can wake from S4
[    4.801354] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    4.801381] rtc_cmos 00:06: alarms up to one month, 242 bytes nvram, hpet irqs
[    4.801426] device-mapper: uevent: version 1.0.3
[    4.801490] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: dm-devel@redhat.com
[    4.801496] ledtrig-cpu: registered to indicate activity on CPUs
[    4.801569] TCP: cubic registered
[    4.801634] NET: Registered protocol family 10
[    4.801763] NET: Registered protocol family 17
[    4.801774] Key type dns_resolver registered
[    4.801991] Loading compiled-in X.509 certificates
[    4.802706] Loaded X.509 cert 'Magrathea: Glacier signing key: 0eaba770ef754c46e356b032e5065130fe98f60e'
[    4.802714] registered taskstats version 1
[    4.804601] Key type trusted registered
[    4.806224] Key type encrypted registered
[    4.807811] AppArmor: AppArmor sha1 policy hashing enabled
[    4.807814] IMA: No TPM chip found, activating TPM-bypass!
[    4.808238]   Magic number: 2:25:606
[    4.808329] rtc_cmos 00:06: setting system clock to 2014-02-21 23:33:16 UTC (1393025596)
[    4.809010] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    4.809011] EDD information not available.
[    4.809036] PM: Hibernation image not present or could not be loaded.
[    4.809640] Freeing unused kernel memory: 1332K (ffffffff81d1e000 - ffffffff81e6b000)
[    4.809641] Write protecting the kernel read-only data: 12288k
[    4.811184] Freeing unused kernel memory: 840K (ffff88000172e000 - ffff880001800000)
[    4.812295] Freeing unused kernel memory: 708K (ffff880001b4f000 - ffff880001c00000)
[    4.828969] systemd-udevd[140]: starting version 204
[    4.850343] ahci 0000:00:1f.2: version 3.0
[    4.850452] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    4.850472] ahci 0000:00:1f.2: SSS flag set, parallel bus scan disabled
[    4.850490] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 4 ports 6 Gbps 0x30 impl SATA mode
[    4.850492] ahci 0000:00:1f.2: flags: 64bit ncq stag led clo pio slum part ems apst 
[    4.851626] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    4.854639] alx 0000:09:00.0 eth0: Qualcomm Atheros AR816x/AR817x Ethernet [20:1a:06:34:39:41]
[    4.859459] scsi0 : ahci
[    4.859551] scsi1 : ahci
[    4.859676] scsi2 : ahci
[    4.859784] scsi3 : ahci
[    4.859902] scsi4 : ahci
[    4.860079] scsi5 : ahci
[    4.860118] ata1: DUMMY
[    4.860120] ata2: DUMMY
[    4.860121] ata3: DUMMY
[    4.860122] ata4: DUMMY
[    4.860130] ata5: SATA max UDMA/133 abar m2048@0xb961b000 port 0xb961b300 irq 42
[    4.860133] ata6: SATA max UDMA/133 abar m2048@0xb961b000 port 0xb961b380 irq 42
[    5.043257] usb 1-1: new high-speed USB device number 2 using ehci-pci
[    5.175794] usb 1-1: New USB device found, idVendor=8087, idProduct=8008
[    5.175798] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.176054] hub 1-1:1.0: USB hub found
[    5.176132] hub 1-1:1.0: 6 ports detected
[    5.179364] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    5.185660] ata5.00: failed to enable AA (error_mask=0x1)
[    5.185664] ata5.00: ATA-8: ST1000LM024 HN-M101MBB, 2BA30001, max UDMA/133
[    5.185666] ata5.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32)
[    5.192010] ata5.00: failed to enable AA (error_mask=0x1)
[    5.192018] ata5.00: configured for UDMA/133
[    5.192182] scsi 4:0:0:0: Direct-Access     ATA      ST1000LM024 HN-M 2BA3 PQ: 0 ANSI: 5
[    5.192305] sd 4:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    5.192308] sd 4:0:0:0: [sda] 4096-byte physical blocks
[    5.192317] sd 4:0:0:0: Attached scsi generic sg0 type 0
[    5.192366] sd 4:0:0:0: [sda] Write Protect is off
[    5.192369] sd 4:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    5.192398] sd 4:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    5.259211]  sda: sda1 sda2 sda3 sda4 < sda5 sda6 >
[    5.259762] sd 4:0:0:0: [sda] Attached SCSI disk
[    5.287513] usb 2-1: new high-speed USB device number 2 using ehci-pci
[    5.420073] usb 2-1: New USB device found, idVendor=8087, idProduct=8000
[    5.420077] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    5.420302] hub 2-1:1.0: USB hub found
[    5.420400] hub 2-1:1.0: 8 ports detected
[    5.423623] tsc: Refined TSC clocksource calibration: 2494.226 MHz
[    5.511755] ata6: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    5.515693] ata6.00: ATAPI: PLDS DVD-RW DS8A9SH, EL3A, max UDMA/100
[    5.516564] ata6.00: configured for UDMA/100
[    5.523470] scsi 5:0:0:0: CD-ROM            PLDS     DVD-RW DS8A9SH   EL3A PQ: 0 ANSI: 5
[    5.526562] sr0: scsi3-mmc drive: 24x/24x writer dvd-ram cd/rw xa/form2 cdda tray
[    5.526565] cdrom: Uniform CD-ROM driver Revision: 3.20
[    5.526706] sr 5:0:0:0: Attached scsi CD-ROM sr0
[    5.526775] sr 5:0:0:0: Attached scsi generic sg1 type 5
[    5.587858] usb 3-4: new high-speed USB device number 2 using xhci_hcd
[    5.641643] usb 3-4: New USB device found, idVendor=0bda, idProduct=5728
[    5.641646] usb 3-4: New USB device strings: Mfr=3, Product=1, SerialNumber=2
[    5.641648] usb 3-4: Product: Lenovo EasyCamera
[    5.641649] usb 3-4: Manufacturer: CF0D9RNVF
[    5.641651] usb 3-4: SerialNumber: 200901010001
[    5.756046] usb 3-7: new full-speed USB device number 3 using xhci_hcd
[    5.773963] usb 3-7: New USB device found, idVendor=105b, idProduct=e065
[    5.773966] usb 3-7: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.773968] usb 3-7: Product: BCM43142A0
[    5.773969] usb 3-7: Manufacturer: Broadcom Corp
[    5.773971] usb 3-7: SerialNumber: F82FA8FECF18
[    5.940232] usb 3-8: new high-speed USB device number 4 using xhci_hcd
[    5.956631] usb 3-8: New USB device found, idVendor=0bda, idProduct=0129
[    5.956634] usb 3-8: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    5.956636] usb 3-8: Product: USB2.0-CRW
[    5.956637] usb 3-8: Manufacturer: Generic
[    5.956638] usb 3-8: SerialNumber: 20100201396000000
[    6.134208] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[    6.424888] Switched to clocksource tsc
[    6.668772] random: nonblocking pool is initialized
[   15.710668] Adding 9763836k swap on /dev/sda6.  Priority:-1 extents:1 across:9763836k FS
[   15.988494] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   16.028205] systemd-udevd[313]: starting version 204
[   16.264722] lp: driver loaded but no devices found
[   17.258487] ACPI Warning: 0x0000000000001828-0x000000000000182f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   17.258494] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.258582] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \GPR_ 1 (20131115/utaddress-251)
[   17.258585] ACPI Warning: 0x0000000000000830-0x000000000000083f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 2 (20131115/utaddress-251)
[   17.258587] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.258588] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \GPR_ 1 (20131115/utaddress-251)
[   17.258590] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \IO_D 2 (20131115/utaddress-251)
[   17.258591] ACPI Warning: 0x0000000000000800-0x000000000000082f SystemIO conflicts with Region \_SB_.PCI0.PEG0.PEGP.GPIO 3 (20131115/utaddress-251)
[   17.258593] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   17.258594] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   17.265842] cfg80211: Calling CRDA to update world regulatory domain
[   17.269549] lib80211: common routines for IEEE802.11 drivers
[   17.269552] lib80211_crypt: registered algorithm 'NULL'
[   17.271121] wl: module license 'MIXED/Proprietary' taints kernel.
[   17.271126] Disabling lock debugging due to kernel taint
[   17.273229] wl: module verification failed: signature and/or  required key missing - tainting kernel
[   17.295740] microcode: CPU0 sig=0x306c3, pf=0x10, revision=0x12
[   17.307068] INFO @wl_cfg80211_attach : Registered CFG80211 phy
[   17.309876] lib80211_crypt: registered algorithm 'TKIP'
[   17.359369] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   17.387634] hda_codec: CX20757: BIOS auto-probing.
[   17.387864] autoconfig: line_outs=1 (0x17/0x0/0x0/0x0/0x0) type:speaker
[   17.387865]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   17.387866]    hp_outs=1 (0x16/0x0/0x0/0x0/0x0)
[   17.387867]    mono: mono_out=0x0
[   17.387868]    inputs:
[   17.387869]      Internal Mic=0x1a
[   17.387870]      Mic=0x19
[   17.388585] hda_codec: Enable sync_write for stable communication
[   17.391209] type=1400 audit(1393018409.065:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=405 comm="apparmor_parser"
[   17.391215] type=1400 audit(1393018409.065:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=405 comm="apparmor_parser"
[   17.391220] type=1400 audit(1393018409.065:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=405 comm="apparmor_parser"
[   17.391612] type=1400 audit(1393018409.065:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=405 comm="apparmor_parser"
[   17.391618] type=1400 audit(1393018409.065:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=405 comm="apparmor_parser"
[   17.391819] type=1400 audit(1393018409.065:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=405 comm="apparmor_parser"
[   17.392390] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card1/input7
[   17.392442] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card1/input6
[   17.396369] [drm] Initialized drm 1.1.0 20060810
[   17.402670] wlan0: Broadcom BCM4365 802.11 Hybrid Wireless Controller 6.30.223.141 (r415941)
[   17.468988] [drm] radeon kernel modesetting enabled.
[   17.469022] checking generic (a0000000 410000) vs hw (b0000000 8000000)
[   17.469034] radeon 0000:01:00.0: enabling device (0006 -> 0007)
[   17.469064] ACPI Error: [AR02] Namespace lookup failure, AE_NOT_FOUND (20131115/psargs-359)
[   17.469067] ACPI Error: Method parse/execution failed [\_SB_.PCI0.PEG0._PRT] (Node ffff8801592b48e8), AE_NOT_FOUND (20131115/psparse-536)
[   17.469242] [drm] initializing kernel modesetting (HAINAN 0x1002:0x6663 0x17AA:0x3801).
[   17.469270] [drm] register mmio base: 0xB8000000
[   17.469271] [drm] register mmio size: 262144
[   17.629774] Linux video capture interface: v2.00
[   17.633957] Bluetooth: Core ver 2.17
[   17.633968] NET: Registered protocol family 31
[   17.633969] Bluetooth: HCI device and connection manager initialized
[   17.633975] Bluetooth: HCI socket layer initialized
[   17.633976] Bluetooth: L2CAP socket layer initialized
[   17.633979] Bluetooth: SCO socket layer initialized
[   17.635196] usbcore: registered new interface driver btusb
[   17.641293] rts5139: module is from the staging directory, the quality is unknown, you have been warned.
[   17.642735] scsi6 : SCSI emulation for RTS5139 USB card reader
[   17.642800] usbcore: registered new interface driver rts5139
[   17.642829] scsi 6:0:0:0: Direct-Access     Generic- xD/SD/M.S.       1.00 PQ: 0 ANSI: 0 CCS
[   17.643078] sd 6:0:0:0: Attached scsi generic sg2 type 0
[   17.697864] platform microcode: Direct firmware load failed with error -2
[   17.697867] platform microcode: Falling back to user helper
[   17.697869] usb 3-7: Direct firmware load failed with error -2
[   17.697872] usb 3-7: Falling back to user helper
[   17.723457] sd 6:0:0:0: [sdb] Attached SCSI removable disk
[   17.793498] uvcvideo: Found UVC 1.00 device Lenovo EasyCamera (0bda:5728)
[   17.796106] input: Lenovo EasyCamera as /devices/pci0000:00/0000:00:14.0/usb3/3-4/3-4:1.0/input/input9
[   17.796160] usbcore: registered new interface driver uvcvideo
[   17.796161] USB Video Class driver (1.1.1)
[   18.150027] input: Ideapad extra buttons as /devices/platform/VPC2004:00/input/input10
[   18.153842] ATOM BIOS: Lenovo/Compal
[   18.153891] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[   18.153893] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[   18.153895] [drm] Detected VRAM RAM=2048M, BAR=128M
[   18.153896] [drm] RAM width 64bits DDR
[   18.153943] [TTM] Zone  kernel: Available graphics memory: 1981208 kiB
[   18.153944] [TTM] Initializing pool allocator
[   18.153947] [TTM] Initializing DMA pool allocator
[   18.153959] [drm] radeon: 2048M of VRAM memory ready
[   18.153960] [drm] radeon: 1024M of GTT memory ready.
[   18.153971] [drm] GART: num cpu pages 262144, num gpu pages 262144
[   18.154735] [drm] probing gen 2 caps for device 8086:c01 = 261ad03/e
[   18.154740] [drm] PCIE gen 3 link speeds already enabled
[   18.154900] [drm] Loading HAINAN Microcode
[   18.445102] microcode: CPU1 sig=0x306c3, pf=0x10, revision=0x12
[   18.445115] platform microcode: Direct firmware load failed with error -2
[   18.445117] platform microcode: Falling back to user helper
[   18.445240] Bluetooth: can't load firmware, may not work correctly
[   18.455264] microcode: CPU2 sig=0x306c3, pf=0x10, revision=0x12
[   18.455276] platform microcode: Direct firmware load failed with error -2
[   18.455279] platform microcode: Falling back to user helper
[   18.455900] microcode: CPU3 sig=0x306c3, pf=0x10, revision=0x12
[   18.455910] platform microcode: Direct firmware load failed with error -2
[   18.455913] platform microcode: Falling back to user helper
[   18.456376] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   18.550749] [drm] PCIE GART of 1024M enabled (table at 0x0000000000040000).
[   18.550860] radeon 0000:01:00.0: WB enabled
[   18.550863] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880156affc00
[   18.550865] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff880156affc04
[   18.550867] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff880156affc08
[   18.550869] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880156affc0c
[   18.550870] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff880156affc10
[   18.550872] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   18.550873] [drm] Driver supports precise vblank timestamp query.
[   18.550892] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[   18.550905] radeon 0000:01:00.0: radeon: using MSI.
[   18.550934] [drm] radeon: irq initialized.
[   18.731836] [drm] ring test on 0 succeeded in 1 usecs
[   18.731842] [drm] ring test on 1 succeeded in 1 usecs
[   18.731846] [drm] ring test on 2 succeeded in 1 usecs
[   18.731906] [drm] ring test on 3 succeeded in 2 usecs
[   18.731914] [drm] ring test on 4 succeeded in 1 usecs
[   18.733141] [drm] ib test on ring 0 succeeded in 0 usecs
[   18.733193] [drm] ib test on ring 1 succeeded in 0 usecs
[   18.733241] [drm] ib test on ring 2 succeeded in 0 usecs
[   18.733261] [drm] ib test on ring 3 succeeded in 0 usecs
[   18.733284] [drm] ib test on ring 4 succeeded in 1 usecs
[   18.733494] [drm] Radeon Display Connectors
[   18.733542] [drm] Internal thermal controller without fan control
[   18.733587] [drm] probing gen 2 caps for device 8086:c01 = 261ad03/e
[   18.738608] cfg80211: World regulatory domain updated:
[   18.738610] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   18.738612] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.738613] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.738614] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   18.738616] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   18.738617] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   19.223202] psmouse serio1: elantech: assuming hardware version 3 (with firmware version 0x450f03)
[   19.269836] psmouse serio1: elantech: Synaptics capabilities query result 0x78, 0x17, 0x0b.
[   19.496373] input: ETPS/2 Elantech Touchpad as /devices/platform/i8042/serio1/input/input8
[   19.947990] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   20.128985] [drm] radeon: dpm initialized
[   20.128991] radeon 0000:01:00.0: No connectors reported connected with modes
[   20.128993] [drm] Cannot find any crtc or sizes - going 1024x768
[   20.130381] [drm] fb mappable at 0xB1250000
[   20.130382] [drm] vram apper at 0xB0000000
[   20.130383] [drm] size 3145728
[   20.130384] [drm] fb depth is 24
[   20.130385] [drm]    pitch is 4096
[   20.130387] checking generic (a0000000 410000) vs hw (b0000000 8000000)
[   20.130448] radeon 0000:01:00.0: fb1: radeondrmfb frame buffer device
[   20.130450] radeon 0000:01:00.0: registered panic notifier
[   20.130467] [drm] Initialized radeon 2.36.0 20080528 for 0000:01:00.0 on minor 0
[   20.131135] [drm] Memory usable by graphics device = 2048M
[   20.131139] checking generic (a0000000 410000) vs hw (a0000000 10000000)
[   20.131141] fb: conflicting fb hw usage inteldrmfb vs VESA VGA - removing generic driver
[   20.131187] Console: switching to colour dummy device 80x25
[   20.171953] i915 0000:00:02.0: irq 45 for MSI/MSI-X
[   20.171967] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   20.171968] [drm] Driver supports precise vblank timestamp query.
[   20.172053] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   20.452091] Bluetooth: hci0 command 0x1003 tx timeout
[   20.469803] fbcon: inteldrmfb (fb0) is primary device
[   21.809656] Console: switching to colour frame buffer device 170x48
[   21.811629] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   21.811924] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[   21.817700] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[   21.826836] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[   21.830221] init: failsafe main process (668) killed by TERM signal
[   21.835706] acpi device:3b: registered as cooling_device5
[   21.835753] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/device:39/LNXVIDEO:00/input/input11
[   21.837001] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   21.842231] acpi device:55: registered as cooling_device6
[   21.842295] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:01/input/input12
[   21.842372] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[   21.842544] mei_me 0000:00:16.0: irq 46 for MSI/MSI-X
[   21.842924] HDA driver get symbol successfully from i915 module
[   21.849683] snd_hda_intel 0000:00:03.0: irq 47 for MSI/MSI-X
[   21.865151] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[   21.865220] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[   21.865281] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input13
[   23.615159] Bluetooth: RFCOMM TTY layer initialized
[   23.615168] Bluetooth: RFCOMM socket layer initialized
[   23.615172] Bluetooth: RFCOMM ver 1.11
[   23.679240] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   23.679243] Bluetooth: BNEP filters: protocol multicast
[   23.679251] Bluetooth: BNEP socket layer initialized
[   23.888488] init: avahi-cups-reload main process (823) terminated with status 1
[   24.072397] ppdev: user-space parallel port driver
[   24.217083] type=1400 audit(1393018415.885:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=839 comm="apparmor_parser"
[   24.217089] type=1400 audit(1393018415.885:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=839 comm="apparmor_parser"
[   24.217390] type=1400 audit(1393018415.885:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=839 comm="apparmor_parser"
[   25.105375] alx 0000:09:00.0: irq 48 for MSI/MSI-X
[   25.105827] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.107086] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   25.755804] type=1400 audit(1393018417.421:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-uccsconfigure/uccsconfigure-session-wrapper" pid=903 comm="apparmor_parser"
[   25.755809] type=1400 audit(1393018417.421:12): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium_browser" pid=903 comm="apparmor_parser"
[   25.755938] type=1400 audit(1393018417.421:13): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="chromium_browser" pid=903 comm="apparmor_parser"
[   25.757801] type=1400 audit(1393018417.421:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=904 comm="apparmor_parser"
[   25.757808] type=1400 audit(1393018417.421:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=904 comm="apparmor_parser"
[   25.757812] type=1400 audit(1393018417.421:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=904 comm="apparmor_parser"
[   25.758214] type=1400 audit(1393018417.425:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=904 comm="apparmor_parser"
[   32.857792] pci_pm_runtime_suspend(): radeon_pmops_runtime_suspend+0x0/0xa0 [radeon] returns -22
[  192.261531] psmouse serio1: Touchpad at isa0060/serio1/input0 lost sync at byte 6
[  192.277235] psmouse serio1: Touchpad at isa0060/serio1/input0 - driver resynced.[/PHP]
`  
I also attach my bootchart png file. My model is Lenovo g-pad 510 with an amd card(8000 series), a 2,6 processor and 4GB ram. I just can t read the png file and understand what is the problem..

---

### Post by mörgæs on 2014-02-21
The bootchart is hard to read. Please post the file in Pastebin or a similar place.

---

### Post by giannhs905 on 2014-02-21
can you please help me a little bit cause I am a newbie..?Where is that pastebin..?

---

### Post by giannhs905 on 2014-02-21
> **mörgæs said:**
> The bootchart is hard to read. Please post the file in Pastebin or a similar place.
can you please help me a little bit cause I am a newbie..?Where is that pastebin..?

---

### Post by giannhs905 on 2014-02-21
> **mörgæs said:**
> The bootchart is hard to read. Please post the file in Pastebin or a similar place.

Ok...the url is the following: [http://imagebin.org/294914](http://imagebin.org/294914)

---

