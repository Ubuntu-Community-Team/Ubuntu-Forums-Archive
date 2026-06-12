---
title: "Very Slow boot up 14.04"
date: 2016-07-21
forum: General Help
---

### Post by aviator1 on 2016-07-21
Had a normal shut down last night. When I went to start up again, nothing would happen. Black screen.

Tried a different monitor and eventually got a "grub rescue" message, but could do nothing with it.

Finally, unplugged power and tried another normal boot up on original monitor. After 15-20 minutes, it booted up.

Did a normal shut down, which took about 5 minutes.

It took 5 minutes to boot up or shut down this morning.

Just took 5 minutes to boot up this afternoon.

All operations seem normal except for boot up and shut down times. I have not installed anything new, or updates lately.

Anyone have anything similar or suggestions as to how to fix this?

My normal boot up-shut down is about 15 seconds.

Thanks for any help.

---

### Post by aviator1 on 2016-07-21
Here is what dmesg looks like I have no idea what to look for.

```
[    1.645328] xhci_hcd 0000:04:00.0: xHCI Host Controller
[    1.645331] xhci_hcd 0000:04:00.0: new USB bus registered, assigned bus number 11
[    1.645367] usb usb11: New USB device found, idVendor=1d6b, idProduct=0003
[    1.645369] usb usb11: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.645370] usb usb11: Product: xHCI Host Controller
[    1.645371] usb usb11: Manufacturer: Linux 3.13.0-37-generic xhci_hcd
[    1.645372] usb usb11: SerialNumber: 0000:04:00.0
[    1.645438] hub 11-0:1.0: USB hub found
[    1.645444] hub 11-0:1.0: 2 ports detected
[    1.653138] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    1.653522] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.653527] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.653606] mousedev: PS/2 mouse device common for all mice
[    1.653756] rtc_cmos 00:04: RTC can wake from S4
[    1.653849] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.653869] rtc_cmos 00:04: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.653925] device-mapper: uevent: version 1.0.3
[    1.653986] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    1.653991] ledtrig-cpu: registered to indicate activity on CPUs
[    1.654075] TCP: cubic registered
[    1.654148] NET: Registered protocol family 10
[    1.654274] NET: Registered protocol family 17
[    1.654281] Key type dns_resolver registered
[    1.654857] Loading compiled-in X.509 certificates
[    1.655573] Loaded X.509 cert 'Magrathea: Glacier signing key: 2cb1133b35f95a9e24deabeeb12ba449bcbabbc9'
[    1.655580] registered taskstats version 1
[    1.657860] Key type trusted registered
[    1.659467] Key type encrypted registered
[    1.661109] AppArmor: AppArmor sha1 policy hashing enabled
[    1.661112] IMA: No TPM chip found, activating TPM-bypass!
[    1.661347] regulator-dummy: disabling
[    1.661431]   Magic number: 8:494:852
[    1.661506] rtc_cmos 00:04: setting system clock to 2016-07-21 20:50:04 UTC (1469134204)
[    1.661621] acpi-cpufreq: overriding BIOS provided _PSD data
[    1.661940] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.661941] EDD information not available.
[    1.661977] PM: Hibernation image not present or could not be loaded.
[    1.663069] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[    1.663070] Write protecting the kernel read-only data: 12288k
[    1.665677] Freeing unused kernel memory: 804K (ffff880001737000 - ffff880001800000)
[    1.667788] Freeing unused kernel memory: 692K (ffff880001b53000 - ffff880001c00000)
[    1.678440] systemd-udevd[146]: starting version 204
[    1.695556] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    1.695565] r8169 0000:02:00.0: can't disable ASPM; OS doesn't have ASPM control
[    1.695770] r8169 0000:02:00.0: irq 88 for MSI/MSI-X
[    1.695898] r8169 0000:02:00.0 eth0: RTL8168f/8111f at 0xffffc9000189a000, 60:a4:4c:59:69:96, XID 08000800 IRQ 88
[    1.695900] r8169 0000:02:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    1.696767] ahci 0000:00:11.0: version 3.0
[    1.696905] ahci 0000:00:11.0: AHCI 0001.0200 32 slots 3 ports 6 Gbps 0x13 impl SATA mode
[    1.696907] ahci 0000:00:11.0: flags: 64bit ncq sntf ilck pm led clo pmp pio slum part 
[    1.697854] scsi0 : ahci
[    1.698081] scsi1 : ahci
[    1.698153] scsi2 : ahci
[    1.698277] scsi3 : ahci
[    1.698385] scsi4 : ahci
[    1.698524] ata1: SATA max UDMA/133 abar m1024@0xfe30b000 port 0xfe30b100 irq 19
[    1.698526] ata2: SATA max UDMA/133 abar m1024@0xfe30b000 port 0xfe30b180 irq 19
[    1.698527] ata3: DUMMY
[    1.698528] ata4: DUMMY
[    1.698530] ata5: SATA max UDMA/133 abar m1024@0xfe30b000 port 0xfe30b300 irq 19
[    2.028894] usb 1-4: new high-speed USB device number 4 using ehci-pci
[    2.136784] tsc: Refined TSC clocksource calibration: 4013.493 MHz
[    2.161616] usb 1-4: New USB device found, idVendor=03f0, idProduct=af11
[    2.161619] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.161620] usb 1-4: Product: Photosmart 6520 series
[    2.161622] usb 1-4: Manufacturer: HP
[    2.161623] usb 1-4: SerialNumber: CN2811614V05TZ
[    2.164532] usb-storage 1-4:1.2: USB Mass Storage device detected
[    2.164607] scsi5 : usb-storage 1-4:1.2
[    2.164666] usbcore: registered new interface driver usb-storage
[    2.188768] ata5: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.188796] ata1: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.188815] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    2.189172] ata2.00: ATA-9: M4-CT256M4SSD2, 040H, max UDMA/100
[    2.189173] ata2.00: 500118192 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.189543] ata5.00: ATA-8: ST2000DL003-9VT166, CC32, max UDMA/133
[    2.189545] ata5.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 31/32)
[    2.189577] ata2.00: configured for UDMA/100
[    2.190436] ata5.00: configured for UDMA/133
[    2.191677] ata1.00: ATAPI: HL-DT-ST BD-RE  WH14NS40, 1.00, max UDMA/100
[    2.192627] ata1.00: configured for UDMA/100
[    2.197220] scsi 0:0:0:0: CD-ROM            HL-DT-ST BD-RE  WH14NS40  1.00 PQ: 0 ANSI: 5
[    2.202088] sr0: scsi3-mmc drive: 1x/1x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.202091] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.202210] sr 0:0:0:0: Attached scsi CD-ROM sr0
[    2.202308] sr 0:0:0:0: Attached scsi generic sg0 type 5
[    2.202447] scsi 1:0:0:0: Direct-Access     ATA      M4-CT256M4SSD2   040H PQ: 0 ANSI: 5
[    2.202566] sd 1:0:0:0: [sda] 500118192 512-byte logical blocks: (256 GB/238 GiB)
[    2.202571] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    2.202723] scsi 4:0:0:0: Direct-Access     ATA      ST2000DL003-9VT1 CC32 PQ: 0 ANSI: 5
[    2.202763] sd 1:0:0:0: [sda] Write Protect is off
[    2.202765] sd 1:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.202803] sd 1:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.202842] sd 4:0:0:0: [sdb] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.202876] sd 4:0:0:0: Attached scsi generic sg2 type 0
[    2.202933] sd 4:0:0:0: [sdb] Write Protect is off
[    2.202935] sd 4:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    2.202974] sd 4:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.203465]  sda: sda1 sda2 sda3 < sda5 sda6 >
[    2.203947] sd 1:0:0:0: [sda] Attached SCSI disk
[    2.260134]  sdb: sdb1 sdb2 sdb3 sdb4 sdb5 sdb6
[    2.260608] sd 4:0:0:0: [sdb] Attached SCSI disk
[    2.300582] EXT4-fs (sda6): mounted filesystem with ordered data mode. Opts: (null)
[    2.438338] random: init urandom read with 72 bits of entropy available
[    2.463945] init: plymouth-upstart-bridge main process (226) terminated with status 1
[    2.463953] init: plymouth-upstart-bridge main process ended, respawning
[    2.468852] init: plymouth-upstart-bridge main process (235) terminated with status 1
[    2.468861] init: plymouth-upstart-bridge main process ended, respawning
[    2.471352] init: plymouth-upstart-bridge main process (239) terminated with status 1
[    2.471359] init: plymouth-upstart-bridge main process ended, respawning
[    2.473449] init: plymouth-upstart-bridge main process (241) terminated with status 1
[    2.473457] init: plymouth-upstart-bridge main process ended, respawning
[    2.573663] Adding 16674812k swap on /dev/sda5.  Priority:-1 extents:1 across:16674812k SSFS
[    2.584535] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    2.655579] systemd-udevd[328]: starting version 204
[    2.678296] lp: driver loaded but no devices found
[    2.687245] wmi: Mapper loaded
[    2.695575] ppdev: user-space parallel port driver
[    2.702440] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[    2.708604] [drm] Initialized drm 1.1.0 20060810
[    2.714832] nvidia: module license 'NVIDIA' taints kernel.
[    2.714836] Disabling lock debugging due to kernel taint
[    2.719009] piix4_smbus 0000:00:14.0: SMBus Host Controller at 0xb00, revision 0
[    2.719066] piix4_smbus 0000:00:14.0: Auxiliary SMBus Host Controller at 0xb20
[    2.723942] nvidia: module verification failed: signature and/or  required key missing - tainting kernel
[    2.725043] MCE: In-kernel MCE decoding enabled.
[    2.726812] EDAC MC: Ver: 3.0.0
[    2.727277] random: nonblocking pool is initialized
[    2.728766] AMD64 EDAC driver v3.4.0
[    2.728788] EDAC amd64: DRAM ECC disabled.
[    2.728798] EDAC amd64: ECC disabled in the BIOS or no ECC capability, module will not load.
[    2.728798]  Either enable ECC checking or force module loading by setting 'ecc_enable_override'.
[    2.728798]  (Note that use of the override may cause unknown side effects.)
[    2.729436] WARNING! power/level is deprecated; use power/control instead
[    2.729554] EXT4-fs (sda6): re-mounted. Opts: errors=remount-ro
[    2.732477] vgaarb: device changed decodes: PCI:0000:01:00.0,olddecodes=io+mem,decodes=none:owns=none
[    2.736451] [drm] Initialized nvidia-drm 0.0.0 20150116 for 0000:01:00.0 on minor 0
[    2.736460] NVRM: loading NVIDIA UNIX x86_64 Kernel Module  340.96  Sun Nov  8 22:33:28 PST 2015
[    2.743269] type=1400 audit(1469134205.576:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=427 comm="apparmor_parser"
[    2.743275] type=1400 audit(1469134205.576:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=427 comm="apparmor_parser"
[    2.743279] type=1400 audit(1469134205.576:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=427 comm="apparmor_parser"
[    2.743639] type=1400 audit(1469134205.576:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=427 comm="apparmor_parser"
[    2.743645] type=1400 audit(1469134205.576:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=427 comm="apparmor_parser"
[    2.743839] type=1400 audit(1469134205.576:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=427 comm="apparmor_parser"
[    2.745849] hda-intel 0000:00:14.2: Using LPIB position fix
[    2.752508] hda-intel 0000:00:14.2: Enable sync_write for stable communication
[    2.764633] SKU: Nid=0x1d sku_cfg=0x4005e601
[    2.764636] SKU: port_connectivity=0x1
[    2.764637] SKU: enable_pcbeep=0x0
[    2.764639] SKU: check_sum=0x00000005
[    2.764640] SKU: customization=0x000000e6
[    2.764641] SKU: external_amp=0x0
[    2.764642] SKU: platform_type=0x0
[    2.764643] SKU: swap=0x0
[    2.764644] SKU: override=0x1
[    2.765083] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line
[    2.765084]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[    2.765085]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[    2.765086]    mono: mono_out=0x0
[    2.765087]    dig-out=0x11/0x1e
[    2.765088]    inputs:
[    2.765089]      Front Mic=0x19
[    2.765090]      Rear Mic=0x18
[    2.765091]      Line=0x1a
[    2.765092] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d
[    2.765093] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0887
[    2.772173] kvm: Nested Virtualization enabled
[    2.772181] kvm: Nested Paging enabled
[    2.783686] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input12
[    2.783907] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input11
[    2.785331] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10
[    2.785576] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input9
[    2.786347] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input8
[    2.786431] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input7
[    2.786524] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6
[    2.786597] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5
[    2.789568] hda_intel: Disabling MSI
[    2.789577] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client
[    2.789613] hda-intel 0000:01:00.1: Disabling 64bit DMA
[    2.793473] hda-intel 0000:01:00.1: Enable delay in RIRB handling
[    2.837743] asus_wmi: ASUS WMI generic driver loaded
[    2.839491] asus_wmi: Initialization: 0x0
[    2.839519] asus_wmi: BIOS WMI version: 0.9
[    2.839579] asus_wmi: SFUN value: 0x0
[    2.840131] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input13
[    2.841612] asus_wmi: Disabling ACPI video driver
[    2.944387] usb 5-4: new full-speed USB device number 2 using ohci-pci
[    2.999916] init: failsafe main process (606) killed by TERM signal
[    3.038401] Bluetooth: Core ver 2.17
[    3.038417] NET: Registered protocol family 31
[    3.038419] Bluetooth: HCI device and connection manager initialized
[    3.038426] Bluetooth: HCI socket layer initialized
[    3.038428] Bluetooth: L2CAP socket layer initialized
[    3.038433] Bluetooth: SCO socket layer initialized
[    3.041359] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[    3.041361] Bluetooth: BNEP filters: protocol multicast
[    3.041365] Bluetooth: BNEP socket layer initialized
[    3.042181] Bluetooth: RFCOMM TTY layer initialized
[    3.042190] Bluetooth: RFCOMM socket layer initialized
[    3.042195] Bluetooth: RFCOMM ver 1.11
[    3.045750] type=1400 audit(1469134205.880:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=752 comm="apparmor_parser"
[    3.045757] type=1400 audit(1469134205.880:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=752 comm="apparmor_parser"
[    3.046101] type=1400 audit(1469134205.880:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=752 comm="apparmor_parser"
[    3.094312] init: cups main process (761) killed by HUP signal
[    3.094323] init: cups main process ended, respawning
[    3.117287] usb 5-4: New USB device found, idVendor=046d, idProduct=c52b
[    3.117291] usb 5-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.117293] usb 5-4: Product: USB Receiver
[    3.117295] usb 5-4: Manufacturer: Logitech
[    3.136594] Switched to clocksource tsc
[    3.160784] scsi 5:0:0:0: Direct-Access     HP       Photosmart 6520  1.00 PQ: 0 ANSI: 5
[    3.160983] sd 5:0:0:0: Attached scsi generic sg3 type 0
[    3.162275] sd 5:0:0:0: [sdc] Attached SCSI removable disk
[    3.220659] init: samba-ad-dc main process (847) terminated with status 1
[    3.236298] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16
[    3.236372] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15
[    3.236432] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14
[    3.278886] r8169 0000:02:00.0 eth0: link down
[    3.278907] r8169 0000:02:00.0 eth0: link down
[    3.278928] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.279154] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    3.384090] usb 5-5: new full-speed USB device number 3 using ohci-pci
[    3.515076] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory
[    3.557038] usb 5-5: New USB device found, idVendor=046d, idProduct=c52b
[    3.557042] usb 5-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    3.557044] usb 5-5: Product: USB Receiver
[    3.557046] usb 5-5: Manufacturer: Logitech
[    3.573810] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[    3.573839] usbcore: registered new interface driver usblp
[    3.581606] hidraw: raw HID events driver (C) Jiri Kosina
[    3.608051] usbcore: registered new interface driver usbhid
[    3.608054] usbhid: USB HID core driver
[    3.615422] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-4/input2
[    3.620147] logitech-djreceiver 0003:046D:C52B.0006: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-5/input2
[    3.620376] input: Logitech Unifying Device. Wireless PID:1028 as /devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/input/input17
[    3.620616] logitech-djdevice 0003:046D:C52B.0007: input,hidraw2: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1028] on usb-0000:00:13.0-4:1
[    3.627326] input: Logitech Unifying Device. Wireless PID:4004 as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0006/input/input18
[    3.627497] logitech-djdevice 0003:046D:C52B.0008: input,hidraw3: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:4004] on usb-0000:00:13.0-5:1
[    3.951808] usb 4-1: new full-speed USB device number 2 using ohci-pci
[    4.124769] usb 4-1: New USB device found, idVendor=046d, idProduct=c52b
[    4.124772] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.124774] usb 4-1: Product: USB Receiver
[    4.124775] usb 4-1: Manufacturer: Logitech
[    4.146825] logitech-djreceiver 0003:046D:C52B.000B: hiddev0,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-1/input2
[    4.150958] input: Logitech Unifying Device. Wireless PID:1028 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.2/0003:046D:C52B.000B/input/input19
[    4.151083] logitech-djdevice 0003:046D:C52B.000C: input,hidraw5: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1028] on usb-0000:00:12.0-1:1
[    4.195015] init: plymouth-upstart-bridge main process ended, respawning
[    4.224142] nvidia 0000:01:00.0: irq 89 for MSI/MSI-X
[    4.411540] usb 4-3: new full-speed USB device number 3 using ohci-pci
[    4.600501] usb 4-3: New USB device found, idVendor=0a48, idProduct=5007
[    4.600503] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    4.600504] usb 4-3: Product: Secure Digital Keychain
[    4.600504] usb 4-3: Manufacturer: mediaGear
[    4.602588] usb-storage 4-3:1.0: USB Mass Storage device detected
[    4.602663] scsi6 : usb-storage 4-3:1.0
[    4.781321] init: plymouth-splash main process (1245) terminated with status 1
[    4.803055] usb 11-2: new SuperSpeed USB device number 2 using xhci_hcd
[    4.815577] usb 11-2: Parent hub missing LPM exit latency info.  Power management will be impacted.
[    4.816099] usb 11-2: New USB device found, idVendor=0480, idProduct=0100
[    4.816102] usb 11-2: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    4.816104] usb 11-2: Product: External USB 3.0
[    4.816106] usb 11-2: Manufacturer: TOSHIBA
[    4.816107] usb 11-2: SerialNumber: 20130411006794F
[    4.816952] usb-storage 11-2:1.0: USB Mass Storage device detected
[    4.817023] scsi7 : usb-storage 11-2:1.0
[    5.537278] r8169 0000:02:00.0 eth0: link up
[    5.537287] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    5.610940] scsi 6:0:0:0: Direct-Access     MG       SD-Key           1.00 PQ: 0 ANSI: 0
[    5.611208] sd 6:0:0:0: Attached scsi generic sg4 type 0
[    5.696883] sd 6:0:0:0: [sdd] Spinning up disk...
[    5.815043] scsi 7:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0    PQ: 0 ANSI: 6
[    5.815228] sd 7:0:0:0: Attached scsi generic sg5 type 0
[    5.818114] sd 7:0:0:0: [sde] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    5.820698] sd 7:0:0:0: [sde] Write Protect is off
[    5.820702] sd 7:0:0:0: [sde] Mode Sense: 43 00 00 00
[    5.823300] sd 7:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    6.191468]  sde: sde1
[    6.207890] sd 7:0:0:0: [sde] Attached SCSI disk
[   33.090599] audit_printk_skb: 153 callbacks suppressed
[   33.090601] type=1400 audit(1469152236.644:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2373 comm="apparmor_parser"
[   33.090606] type=1400 audit(1469152236.644:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2373 comm="apparmor_parser"
[   33.090902] type=1400 audit(1469152236.644:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2373 comm="apparmor_parser"
[    6.702239] .............................................................................................not responding...
[  106.701787] sd 6:0:0:0: [sdd] READ CAPACITY failed
[  106.701796] sd 6:0:0:0: [sdd]  
[  106.701800] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  106.701804] sd 6:0:0:0: [sdd]  
[  106.701807] Sense Key : Not Ready [current] 
[  106.701812] sd 6:0:0:0: [sdd]  
[  106.701818] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  106.734768] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[  106.767656] sd 6:0:0:0: [sdd] Asking for cache data failed
[  106.767665] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  106.912671] sd 6:0:0:0: [sdd] Spinning up disk...
[  107.032603] sd 6:0:0:0: [sdd] Spinning up disk...
[  107.947051] .
[  108.038980] ..
[  109.126406] ..
[  110.213817] ..
[  111.301119] ..
[  112.384537] ..
[  113.468001] ..
[  114.555412] ..
[  115.638850] ..
[  116.722215] ..
[  117.805646] ..
[  118.889018] ..
[  119.972421] ..
[  121.055877] ..
[  122.139297] ..
[  123.222691] ..
[  124.310062] ..
[  125.397432] ..
[  126.484922] ..
[  127.572329] ..
[  128.659692] ..
[  129.747020] ..
[  130.834502] ..
[  131.921898] ..
[  133.009356] ..
[  134.096672] ..
[  135.184147] ..
[  136.271573] ..
[  137.358921] ..
[  138.446385] ..
[  139.533798] ..
[  140.621126] ..
[  141.708510] ..
[  142.791947] ..
[  143.875398] ..
[  144.958796] ..
[  146.042143] ..
[  147.125608] ..
[  148.209040] ..
[  149.292455] ..
[  150.379807] ..
[  151.463216] ..
[  152.550671] ..
[  153.638020] ..
[  154.725449] ..
[  155.812845] ..
[  156.900218] ..
[  157.987695] ..
[  159.075073] ..
[  160.162456] ..
[  161.249818] ..
[  162.337317] ..
[  163.424697] ..
[  164.512128] ..
[  165.599492] ..
[  166.686896] ..
[  167.774297] ..
[  168.861735] ..
[  169.949157] ..
[  171.036531] ..
[  172.119930] ..
[  173.203359] ..
[  174.286787] ..
[  175.370149] ..
[  176.453607] ..
[  177.537002] ..
[  178.620419] ..
[  179.707825] ..
[  180.795231] ..
[  181.882641] ..
[  182.969994] ..
[  184.057449] ..
[  185.144854] ..
[  186.232260] ..
[  187.319666] ..
[  188.407073] ..
[  189.494492] ..
[  190.581883] ..
[  191.669266] ..
[  192.756697] ..
[  193.844100] ..
[  194.931510] ..
[  196.022855] ..
[  197.110315] ..
[  198.197720] ..
[  199.285111] ..
[  200.372507] ..
[  201.455827] ..
[  202.539304] ..
[  203.622783] ..
[  204.706228] ..
[  205.789524] ..
[  206.872926] ..not responding...
[  207.943381] sd 6:0:0:0: [sdd] READ CAPACITY failed
[  207.943390] sd 6:0:0:0: [sdd]  
[  207.943394] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  207.943398] sd 6:0:0:0: [sdd]  
[  207.943401] Sense Key : Not Ready [current] 
[  207.943406] sd 6:0:0:0: [sdd]  
[  207.943412] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  207.960385] .not responding...
[  207.976379] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[  208.038340] sd 6:0:0:0: [sdd] Asking for cache data failed
[  208.038352] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  208.038359] sd 6:0:0:0: [sdd] Attached SCSI removable disk
[  208.125212] sd 6:0:0:0: [sdd] Spinning up disk...
[  209.131759] .............................................................................................not responding...
[  309.220949] sd 6:0:0:0: [sdd] READ CAPACITY failed
[  309.220958] sd 6:0:0:0: [sdd]  
[  309.220962] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  309.220965] sd 6:0:0:0: [sdd]  
[  309.220968] Sense Key : Not Ready [current] 
[  309.220974] sd 6:0:0:0: [sdd]  
[  309.220980] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  309.253931] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[  309.286913] sd 6:0:0:0: [sdd] Asking for cache data failed
[  309.286922] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[  309.398847] sd 6:0:0:0: [sdd] Spinning up disk...
dave@dave-desktop:~$
```

---

### Post by papibe on 2016-07-21
Hi aviator1.

It looks like disk /dev/sdd is having serious problems. Either it has connectivity issues, or it is plain failing.

I would backup the date on it, ASAP. 

Let us know if you need suggestions on how to do that.

Regards.

---

### Post by aviator1 on 2016-07-22
Can you tell me which disk is affected. I have a Solid State and a older standard type.

Thanks. I have backed up both drives.

---

### Post by oldfred on 2016-07-22
It is saying sdd. That would be a fourth drive, or a flash drive remounted so no actual third drive?

Post this:
sudo parted -l

       sudo lshw -C Disk -short

---

### Post by aviator1 on 2016-07-22
When I enter    **sudo parted -l** I get a request for my password. After entering my password, all I get is a flashing block, which eventually turns solid.

When I enter
**sudo lshw -C Disk -short** I get a request for my password. After entering my password, I get PCI (SYSFS), which disappears and then I get SCSI on the screen.


Thanks for any help.

---

### Post by oldfred on 2016-07-22
Does UEFI/BIOS show drives correctly?

From Disks, the icon in upper right corner has Smart Data. Does that show drives? 
And what is status if shown.

---

### Post by aviator1 on 2016-07-22
Sorry, I don't know where to look.

---

### Post by papibe on 2016-07-22
Try these commands:
```
mount -l | grep sdd

df -h

lsblk
```

---

### Post by aviator1 on 2016-07-22
The Toshiba is an external back up HD

   ```
dave@dave-desktop:~$ mount -l | grep sdd 
 /dev/sdd1 on /media/dave/TOSHIBA EXT type fuseblk (rw,nosuid,nodev,allow_other,default_permissions,blksize=4096) [TOSHIBA EXT] 
 

```
 ```
dave@dave-desktop:~$ df -h 
 Filesystem      Size  Used Avail Use% Mounted on 
 udev            7.8G  4.0K  7.8G   1% /dev 
 tmpfs           1.6G  1.7M  1.6G   1% /run 
 /dev/sda6       102G   46G   51G  48% / 
 none            4.0K     0  4.0K   0% /sys/fs/cgroup 
 none            5.0M     0  5.0M   0% /run/lock 
 none            7.8G  140K  7.8G   1% /run/shm 
 none            100M   52K  100M   1% /run/user 
 /dev/sdd1       466G  446G   21G  96% /media/dave/TOSHIBA EXT 
 /dev/sdb2       936G  121G  768G  14% /media/dave/01a0c8e9-208b-446f-8194-25189c603de1 
 
```
 ```
dave@dave-desktop:~$ lsblk 
 NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT 
 sda      8:0    0 238.5G  0 disk  
 &#9500;&#9472;sda1   8:1    0   499M  0 part  
 &#9500;&#9472;sda2   8:2    0   119G  0 part  
 &#9500;&#9472;sda3   8:3    0     1K  0 part  
 &#9500;&#9472;sda5   8:5    0  15.9G  0 part [SWAP] 
 &#9492;&#9472;sda6   8:6    0 103.1G  0 part / 
 sdb      8:16   0   1.8T  0 disk  
 &#9500;&#9472;sdb1   8:17   0     1M  0 part  
 &#9500;&#9472;sdb2   8:18   0 950.9G  0 part /media/dave/01a0c8e9-208b-446f-8194-25189c603de 
 &#9500;&#9472;sdb3   8:19   0   8.7G  0 part  
 &#9500;&#9472;sdb4   8:20   0     1M  0 part  
 &#9500;&#9472;sdb5   8:21   0 894.9G  0 part  
 &#9492;&#9472;sdb6   8:22   0   8.7G  0 part  
 sdd      8:48   0 465.8G  0 disk  
 &#9492;&#9472;sdd1   8:49   0 465.7G  0 part /media/dave/TOSHIBA EXT 
 sr0     11:0    1  1024M  0 rom
```

---

### Post by papibe on 2016-07-22
Is it a external USB disk?

If so, it will always slow down both boot and shutdown. This is regardless if the disk is OK or failing.

Boot with out it to confirm that's the problem. If you created an entry in fstab, comment it out before booting.

Let us know how that goes.
Regards.

---

### Post by aviator1 on 2016-07-22
It is a USB drive.

However, it has been plugged in for many months, as I have auto backups go to it.

I'll disconnect it and see what happens and report back.

Thanks for your help.

---

### Post by oldfred on 2016-07-22
In addition to papibe's suggestions, is external NTFS formatted and used with Windows 8 or 10. 
Then it will be hibernated as Windows fast start up is always on hibernation and it leaves all NTFS partitions mounted.
Not really good for external drives as then you cannot easily access except by rebooting in system originally used.

---

### Post by aviator1 on 2016-07-22
I did the reboot without the External drive and there was no difference.

However, on the boot prior to this, times got worse.

I would get the screen identifying the computer and components, which would very quickly switch to a screen which would allow me to select the older drive with 12.04, or the SSD with Windows 7 or 14.04.

It now takes about 5 minutes between just those 2 screens.

I have not selected Windows on any of the boots.

---

### Post by papibe on 2016-07-22
Could you post the output of dmesg after the new slow boot?

---

### Post by aviator1 on 2016-07-22
Here it is.Thanks for your help.
```

[ 1523.696258] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 1523.696262] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 1523.808223] sd 6:0:0:0: [sdd] Spinning up disk...
[ 1524.812097] .............................................................................................not responding...
[ 1624.814807] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 1624.814816] sd 6:0:0:0: [sdd]  
[ 1624.814820] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1624.814823] sd 6:0:0:0: [sdd]  
[ 1624.814826] Sense Key : Not Ready [current] 
[ 1624.814832] sd 6:0:0:0: [sdd]  
[ 1624.814851] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1624.847774] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 1624.880690] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 1624.880699] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 1624.996641] sd 6:0:0:0: [sdd] Spinning up disk...
[ 1626.004266] .............................................................................................not responding...
[ 1725.999351] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 1725.999361] sd 6:0:0:0: [sdd]  
[ 1725.999365] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1725.999369] sd 6:0:0:0: [sdd]  
[ 1725.999371] Sense Key : Not Ready [current] 
[ 1725.999377] sd 6:0:0:0: [sdd]  
[ 1725.999383] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1726.032252] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 1726.065382] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 1726.065390] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 1726.181239] sd 6:0:0:0: [sdd] Spinning up disk...
[ 1727.188382] .............................................................................................not responding...
[ 1827.196906] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 1827.196916] sd 6:0:0:0: [sdd]  
[ 1827.196920] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1827.196924] sd 6:0:0:0: [sdd]  
[ 1827.196926] Sense Key : Not Ready [current] 
[ 1827.196932] sd 6:0:0:0: [sdd]  
[ 1827.196938] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1827.228890] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 1827.260814] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 1827.260824] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 1827.372797] sd 6:0:0:0: [sdd] Spinning up disk...
[ 1828.376399] .............................................................................................not responding...
[ 1928.379474] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 1928.379484] sd 6:0:0:0: [sdd]  
[ 1928.379488] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1928.379491] sd 6:0:0:0: [sdd]  
[ 1928.379494] Sense Key : Not Ready [current] 
[ 1928.379500] sd 6:0:0:0: [sdd]  
[ 1928.379506] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1928.412456] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 1928.445433] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 1928.445442] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 1928.561318] sd 6:0:0:0: [sdd] Spinning up disk...
[ 1929.568629] .............................................................................................not responding...
[ 2029.528035] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2029.528044] sd 6:0:0:0: [sdd]  
[ 2029.528048] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2029.528052] sd 6:0:0:0: [sdd]  
[ 2029.528055] Sense Key : Not Ready [current] 
[ 2029.528061] sd 6:0:0:0: [sdd]  
[ 2029.528067] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2029.561004] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2029.594005] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2029.594015] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2029.709904] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2030.716752] .............................................................................................not responding...
[ 2130.732571] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2130.732581] sd 6:0:0:0: [sdd]  
[ 2130.732585] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2130.732588] sd 6:0:0:0: [sdd]  
[ 2130.732591] Sense Key : Not Ready [current] 
[ 2130.732597] sd 6:0:0:0: [sdd]  
[ 2130.732603] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2130.764553] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2130.796467] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2130.796476] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2130.908496] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2131.912912] .............................................................................................not responding...
[ 2231.899074] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2231.899079] sd 6:0:0:0: [sdd]  
[ 2231.899081] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2231.899082] sd 6:0:0:0: [sdd]  
[ 2231.899083] Sense Key : Not Ready [current] 
[ 2231.899085] sd 6:0:0:0: [sdd]  
[ 2231.899088] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2231.932082] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2231.965061] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2231.965066] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2232.080940] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2275.639142] usb 1-4: USB disconnect, device number 4
[ 2275.639515] usblp0: removed
[ 2275.909438] usb 1-4: new high-speed USB device number 5 using ehci-pci
[ 2276.042114] usb 1-4: New USB device found, idVendor=03f0, idProduct=af11
[ 2276.042120] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2276.042123] usb 1-4: Product: Photosmart 6520 series
[ 2276.042126] usb 1-4: Manufacturer: HP
[ 2276.042128] usb 1-4: SerialNumber: CN2811614V05TZ
[ 2276.042805] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 5 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2276.042871] usb-storage 1-4:1.2: USB Mass Storage device detected
[ 2276.042999] scsi7 : usb-storage 1-4:1.2
[ 2276.253548] usb 1-4: USB disconnect, device number 5
[ 2276.253891] usblp0: removed
[ 2276.525076] usb 1-4: new high-speed USB device number 6 using ehci-pci
[ 2276.657803] usb 1-4: New USB device found, idVendor=03f0, idProduct=af11
[ 2276.657808] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2276.657812] usb 1-4: Product: Photosmart 6520 series
[ 2276.657814] usb 1-4: Manufacturer: HP
[ 2276.657817] usb 1-4: SerialNumber: CN2811614V05TZ
[ 2276.658621] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2276.658683] usb-storage 1-4:1.2: USB Mass Storage device detected
[ 2276.658819] scsi8 : usb-storage 1-4:1.2
[ 2277.657022] scsi 8:0:0:0: Direct-Access     HP       Photosmart 6520  1.00 PQ: 0 ANSI: 5
[ 2277.657288] sd 8:0:0:0: Attached scsi generic sg3 type 0
[ 2277.658835] sd 8:0:0:0: [sdc] Attached SCSI removable disk
[ 2278.755591] usb 1-4: USB disconnect, device number 6
[ 2278.755873] usblp0: removed
[ 2279.027798] usb 1-4: new high-speed USB device number 7 using ehci-pci
[ 2279.523436] usb 4-4: new full-speed USB device number 4 using ohci-pci
[ 2279.681851] usb 4-4: not running at top speed; connect to a high speed hub
[ 2279.693847] usb 4-4: New USB device found, idVendor=03f0, idProduct=af11
[ 2279.693856] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2279.693862] usb 4-4: Product: Photosmart 6520 series
[ 2279.693867] usb 4-4: Manufacturer: HP
[ 2279.693872] usb 4-4: SerialNumber: CN2811614V05TZ
[ 2279.701010] usblp 4-4:1.1: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2279.701113] usb-storage 4-4:1.2: USB Mass Storage device detected
[ 2279.701226] scsi9 : usb-storage 4-4:1.2
[ 2280.705390] scsi 9:0:0:0: Direct-Access     HP       Photosmart 6520  1.00 PQ: 0 ANSI: 5
[ 2280.705808] sd 9:0:0:0: Attached scsi generic sg3 type 0
[ 2280.725258] sd 9:0:0:0: [sdc] Attached SCSI removable disk
[ 2281.024337] usb 4-4: USB disconnect, device number 4
[ 2281.024705] usblp0: removed
[ 2281.358439] usb 1-4: new high-speed USB device number 8 using ehci-pci
[ 2282.181952] usb 4-4: new full-speed USB device number 6 using ohci-pci
[ 2282.340324] usb 4-4: not running at top speed; connect to a high speed hub
[ 2282.352391] usb 4-4: New USB device found, idVendor=03f0, idProduct=af11
[ 2282.352399] usb 4-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2282.352404] usb 4-4: Product: Photosmart 6520 series
[ 2282.352408] usb 4-4: Manufacturer: HP
[ 2282.352412] usb 4-4: SerialNumber: CN2811614V05TZ
[ 2282.359501] usblp 4-4:1.1: usblp0: USB Bidirectional printer dev 6 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2282.359610] usb-storage 4-4:1.2: USB Mass Storage device detected
[ 2282.359726] scsi10 : usb-storage 4-4:1.2
[ 2282.608513] usb 4-4: USB disconnect, device number 6
[ 2282.608799] usblp0: removed
[ 2283.137497] usb 1-4: new high-speed USB device number 9 using ehci-pci
[ 2283.270135] usb 1-4: New USB device found, idVendor=03f0, idProduct=af11
[ 2283.270143] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2283.270149] usb 1-4: Product: Photosmart 6520 series
[ 2283.270152] usb 1-4: Manufacturer: HP
[ 2283.270156] usb 1-4: SerialNumber: CN2811614V05TZ
[ 2283.270970] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 9 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2283.271055] usb-storage 1-4:1.2: USB Mass Storage device detected
[ 2283.271189] scsi11 : usb-storage 1-4:1.2
[ 2283.286316] usb 1-4: USB disconnect, device number 9
[ 2283.286689] usblp0: removed
[ 2283.557167] usb 1-4: new high-speed USB device number 10 using ehci-pci
[ 2283.689969] usb 1-4: New USB device found, idVendor=03f0, idProduct=af11
[ 2283.689976] usb 1-4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[ 2283.689980] usb 1-4: Product: Photosmart 6520 series
[ 2283.689983] usb 1-4: Manufacturer: HP
[ 2283.689986] usb 1-4: SerialNumber: CN2811614V05TZ
[ 2283.690779] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 10 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2283.690854] usb-storage 1-4:1.2: USB Mass Storage device detected
[ 2283.690978] scsi12 : usb-storage 1-4:1.2
[ 2283.801015] usb 2-1: new high-speed USB device number 4 using ehci-pci
[ 2283.934745] usb 2-1: New USB device found, idVendor=0480, idProduct=0100
[ 2283.934754] usb 2-1: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[ 2283.934759] usb 2-1: Product: External USB 3.0
[ 2283.934763] usb 2-1: Manufacturer: TOSHIBA
[ 2283.934766] usb 2-1: SerialNumber: 20130411006794F
[ 2283.935195] usb-storage 2-1:1.0: USB Mass Storage device detected
[ 2283.935318] scsi13 : usb-storage 2-1:1.0
[ 2284.689071] scsi 12:0:0:0: Direct-Access     HP       Photosmart 6520  1.00 PQ: 0 ANSI: 5
[ 2284.689382] sd 12:0:0:0: Attached scsi generic sg3 type 0
[ 2284.690858] sd 12:0:0:0: [sdc] Attached SCSI removable disk
[ 2284.933230] scsi 13:0:0:0: Direct-Access     TOSHIBA  External USB 3.0 0    PQ: 0 ANSI: 6
[ 2284.933596] sd 13:0:0:0: Attached scsi generic sg5 type 0
[ 2285.475467] sd 13:0:0:0: [sde] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[ 2285.476595] sd 13:0:0:0: [sde] Write Protect is off
[ 2285.476605] sd 13:0:0:0: [sde] Mode Sense: 43 00 00 00
[ 2285.477802] sd 13:0:0:0: [sde] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[ 2285.493283]  sde: sde1
[ 2285.497340] sd 13:0:0:0: [sde] Attached SCSI disk
[ 2233.085041] .............................................................................................not responding...
[ 2333.059612] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2333.059630] sd 6:0:0:0: [sdd]  
[ 2333.059634] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2333.059638] sd 6:0:0:0: [sdd]  
[ 2333.059640] Sense Key : Not Ready [current] 
[ 2333.059646] sd 6:0:0:0: [sdd]  
[ 2333.059652] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2333.092555] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2333.125514] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2333.125520] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2333.241451] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2334.245073] .............................................................................................not responding...
[ 2434.265066] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2434.265074] sd 6:0:0:0: [sdd]  
[ 2434.265078] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2434.265082] sd 6:0:0:0: [sdd]  
[ 2434.265084] Sense Key : Not Ready [current] 
[ 2434.265090] sd 6:0:0:0: [sdd]  
[ 2434.265096] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2434.297041] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2434.329019] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2434.329027] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2434.440938] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2435.405452] usblp0: removed
[ 2435.406245] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 10 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2435.470588] systemd-udevd[13540]: Failed to apply ACL on /dev/bus/usb/001/005: No such file or directory
[ 2435.470596] systemd-udevd[13540]: Failed to apply ACL on /dev/bus/usb/001/005: No such file or directory
[ 2436.525990] usblp0: removed
[ 2436.526730] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 10 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2436.579016] systemd-udevd[13540]: Failed to apply ACL on /dev/bus/usb/001/006: No such file or directory
[ 2436.579025] systemd-udevd[13540]: Failed to apply ACL on /dev/bus/usb/001/006: No such file or directory
[ 2437.740157] usblp0: removed
[ 2437.740884] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 10 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2437.788985] systemd-udevd[13540]: Failed to apply ACL on /dev/bus/usb/001/009: No such file or directory
[ 2437.788998] systemd-udevd[13540]: Failed to apply ACL on /dev/bus/usb/001/009: No such file or directory
[ 2438.841799] usblp0: removed
[ 2438.842770] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 10 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11
[ 2485.628690] systemd-hostnamed[14011]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2435.445283] .............................................................................................not responding...
[ 2535.461488] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2535.461496] sd 6:0:0:0: [sdd]  
[ 2535.461500] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2535.461504] sd 6:0:0:0: [sdd]  
[ 2535.461507] Sense Key : Not Ready [current] 
[ 2535.461513] sd 6:0:0:0: [sdd]  
[ 2535.461519] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2535.494465] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2535.526507] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2535.526517] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2535.638445] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2592.975661] EXT4-fs (sdb5): warning: maximal mount count reached, running e2fsck is recommended
[ 2593.009163] EXT4-fs (sdb5): mounted filesystem with ordered data mode. Opts: (null)
[ 2536.645437] .............................................................................................not responding...
[ 2636.640106] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2636.640111] sd 6:0:0:0: [sdd]  
[ 2636.640114] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2636.640116] sd 6:0:0:0: [sdd]  
[ 2636.640118] Sense Key : Not Ready [current] 
[ 2636.640122] sd 6:0:0:0: [sdd]  
[ 2636.640126] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2636.673046] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2636.706060] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2636.706065] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2636.822036] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2637.829461] .............................................................................................not responding...
[ 2737.841702] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2737.841705] sd 6:0:0:0: [sdd]  
[ 2737.841707] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2737.841708] sd 6:0:0:0: [sdd]  
[ 2737.841709] Sense Key : Not Ready [current] 
[ 2737.841711] sd 6:0:0:0: [sdd]  
[ 2737.841714] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2737.873683] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2737.905662] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2737.905665] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2738.017635] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2739.021688] .............................................................................................not responding...
[ 2839.028303] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2839.028311] sd 6:0:0:0: [sdd]  
[ 2839.028315] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2839.028319] sd 6:0:0:0: [sdd]  
[ 2839.028321] Sense Key : Not Ready [current] 
[ 2839.028327] sd 6:0:0:0: [sdd]  
[ 2839.028333] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2839.061287] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2839.094241] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2839.094249] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2839.206095] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2882.573395] systemd-hostnamed[16206]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2840.209811] .............................................................................................not responding...
[ 2940.212874] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 2940.212882] sd 6:0:0:0: [sdd]  
[ 2940.212886] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2940.212890] sd 6:0:0:0: [sdd]  
[ 2940.212892] Sense Key : Not Ready [current] 
[ 2940.212898] sd 6:0:0:0: [sdd]  
[ 2940.212904] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2940.245854] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 2940.278699] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 2940.278708] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 2940.394713] sd 6:0:0:0: [sdd] Spinning up disk...
[ 2941.401883] .............................................................................................not responding...
[ 3041.378404] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3041.378414] sd 6:0:0:0: [sdd]  
[ 3041.378418] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3041.378422] sd 6:0:0:0: [sdd]  
[ 3041.378424] Sense Key : Not Ready [current] 
[ 3041.378430] sd 6:0:0:0: [sdd]  
[ 3041.378436] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3041.410390] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3041.442298] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3041.442306] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3041.554224] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3042.557973] .............................................................................................not responding...
[ 3142.592008] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3142.592017] sd 6:0:0:0: [sdd]  
[ 3142.592021] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3142.592025] sd 6:0:0:0: [sdd]  
[ 3142.592027] Sense Key : Not Ready [current] 
[ 3142.592033] sd 6:0:0:0: [sdd]  
[ 3142.592039] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3142.624981] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3142.657967] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3142.657976] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3142.772868] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3143.778149] .............................................................................................not responding...
[ 3243.744522] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3243.744526] sd 6:0:0:0: [sdd]  
[ 3243.744527] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3243.744529] sd 6:0:0:0: [sdd]  
[ 3243.744530] Sense Key : Not Ready [current] 
[ 3243.744532] sd 6:0:0:0: [sdd]  
[ 3243.744534] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3243.777462] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3243.810428] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3243.810439] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3243.926453] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3244.930282] .............................................................................................not responding...
[ 3344.942164] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3344.942173] sd 6:0:0:0: [sdd]  
[ 3344.942177] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3344.942180] sd 6:0:0:0: [sdd]  
[ 3344.942183] Sense Key : Not Ready [current] 
[ 3344.942189] sd 6:0:0:0: [sdd]  
[ 3344.942194] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3344.974144] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3345.006127] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3345.006135] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3345.118013] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3346.122418] .............................................................................................not responding...
[ 3446.128695] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3446.128703] sd 6:0:0:0: [sdd]  
[ 3446.128707] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3446.128711] sd 6:0:0:0: [sdd]  
[ 3446.128713] Sense Key : Not Ready [current] 
[ 3446.128719] sd 6:0:0:0: [sdd]  
[ 3446.128725] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3446.161676] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3446.194623] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3446.194632] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3446.310637] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3528.935095] systemd-hostnamed[19581]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 3447.314574] .............................................................................................not responding...
[ 3547.297343] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3547.297352] sd 6:0:0:0: [sdd]  
[ 3547.297356] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3547.297360] sd 6:0:0:0: [sdd]  
[ 3547.297362] Sense Key : Not Ready [current] 
[ 3547.297368] sd 6:0:0:0: [sdd]  
[ 3547.297374] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3547.330314] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3547.363311] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3547.363320] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3547.479190] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3548.486682] .............................................................................................not responding...
[ 3648.478911] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3648.478920] sd 6:0:0:0: [sdd]  
[ 3648.478924] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3648.478928] sd 6:0:0:0: [sdd]  
[ 3648.478931] Sense Key : Not Ready [current] 
[ 3648.478936] sd 6:0:0:0: [sdd]  
[ 3648.478942] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3648.510888] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3648.542772] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3648.542777] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3648.654677] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3649.658829] .............................................................................................not responding...
[ 3749.657490] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3749.657498] sd 6:0:0:0: [sdd]  
[ 3749.657502] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3749.657506] sd 6:0:0:0: [sdd]  
[ 3749.657509] Sense Key : Not Ready [current] 
[ 3749.657514] sd 6:0:0:0: [sdd]  
[ 3749.657520] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3749.690473] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3749.723471] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3749.723480] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3749.839403] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3750.846906] .............................................................................................not responding...
[ 3850.842023] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3850.842034] sd 6:0:0:0: [sdd]  
[ 3850.842036] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3850.842037] sd 6:0:0:0: [sdd]  
[ 3850.842038] Sense Key : Not Ready [current] 
[ 3850.842041] sd 6:0:0:0: [sdd]  
[ 3850.842044] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3850.875025] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3850.907977] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3850.907987] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3851.023848] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3852.030962] .............................................................................................not responding...
[ 3952.047534] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 3952.047543] sd 6:0:0:0: [sdd]  
[ 3952.047547] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3952.047550] sd 6:0:0:0: [sdd]  
[ 3952.047553] Sense Key : Not Ready [current] 
[ 3952.047559] sd 6:0:0:0: [sdd]  
[ 3952.047565] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3952.079632] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 3952.111611] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 3952.111620] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 3952.223484] sd 6:0:0:0: [sdd] Spinning up disk...
[ 3953.227129] .............................................................................................not responding...
[ 4053.262105] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 4053.262110] sd 6:0:0:0: [sdd]  
[ 4053.262111] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4053.262118] sd 6:0:0:0: [sdd]  
[ 4053.262119] Sense Key : Not Ready [current] 
[ 4053.262122] sd 6:0:0:0: [sdd]  
[ 4053.262125] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 4053.295066] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 4053.328078] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 4053.328089] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 4053.443984] sd 6:0:0:0: [sdd] Spinning up disk...
[ 4054.451254] .............................................................................................not responding...
[ 4154.425702] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 4154.425707] sd 6:0:0:0: [sdd]  
[ 4154.425709] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4154.425710] sd 6:0:0:0: [sdd]  
[ 4154.425711] Sense Key : Not Ready [current] 
[ 4154.425713] sd 6:0:0:0: [sdd]  
[ 4154.425716] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 4154.458672] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 4154.491702] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 4154.491707] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 4154.607537] sd 6:0:0:0: [sdd] Spinning up disk...
[ 4155.611411] .............................................................................................not responding...
[ 4255.603213] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 4255.603217] sd 6:0:0:0: [sdd]  
[ 4255.603219] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4255.603220] sd 6:0:0:0: [sdd]  
[ 4255.603221] Sense Key : Not Ready [current] 
[ 4255.603229] sd 6:0:0:0: [sdd]  
[ 4255.603232] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 4255.635165] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 4255.667112] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 4255.667123] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 4255.779108] sd 6:0:0:0: [sdd] Spinning up disk...
[ 4256.783538] .............................................................................................not responding...
[ 4356.779740] sd 6:0:0:0: [sdd] READ CAPACITY failed
[ 4356.779749] sd 6:0:0:0: [sdd]  
[ 4356.779753] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 4356.779757] sd 6:0:0:0: [sdd]  
[ 4356.779759] Sense Key : Not Ready [current] 
[ 4356.779765] sd 6:0:0:0: [sdd]  
[ 4356.779771] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 4356.811730] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled
[ 4356.843709] sd 6:0:0:0: [sdd] Asking for cache data failed
[ 4356.843717] sd 6:0:0:0: [sdd] Assuming drive cache: write through
[ 4356.955600] sd 6:0:0:0: [sdd] Spinning up disk...

```
dave@dave-desktop:~$

---

### Post by papibe on 2016-07-22
It looks, from just reading the log, that you haven't disconnected the drive.

Could you make sure the drive is removed, then boot again, and post the log? (please use code tags)

If you actually disconnected the drive, there is something odd. If so, could you run these again?
```
mount -l | grep sdd

df -h

lsblk
```
Regards.

---

### Post by aviator1 on 2016-07-22
I forgot on the last reboot that I had reconnected.
Sorry. Will go for it again and report.

Thanks.

---

### Post by aviator1 on 2016-07-22
I booted without the external HD.

   mount -l | grep sdd did nothing. I tried it twice. Sorry, I do not know how to use code tags.

   
```
dave@dave-desktop:~$ mount -l | grep sdd 
```
 ```
dave@dave-desktop:~$ df -h 
 Filesystem      Size  Used Avail Use% Mounted on 
 udev            7.8G  4.0K  7.8G   1% /dev 
 tmpfs           1.6G  1.7M  1.6G   1% /run 
 /dev/sda6       102G   46G   51G  48% / 
 none            4.0K     0  4.0K   0% /sys/fs/cgroup 
 none            5.0M     0  5.0M   0% /run/lock 
 none            7.8G   76K  7.8G   1% /run/shm 
 none            100M   48K  100M   1% /run/user 
 dave@dave-desktop:~$  
```
 

 ```
dave@dave-desktop:~$ lsblk 
 NAME   MAJ:MIN RM   SIZE RO TYPE MOUNTPOINT 
 sda      8:0    0 238.5G  0 disk  
 &#9500;&#9472;sda1   8:1    0   499M  0 part  
 &#9500;&#9472;sda2   8:2    0   119G  0 part  
 &#9500;&#9472;sda3   8:3    0     1K  0 part  
 &#9500;&#9472;sda5   8:5    0  15.9G  0 part [SWAP] 
 &#9492;&#9472;sda6   8:6    0 103.1G  0 part / 
 sdb      8:16   0   1.8T  0 disk  
 &#9500;&#9472;sdb1   8:17   0     1M  0 part  
 &#9500;&#9472;sdb2   8:18   0 950.9G  0 part  
 &#9500;&#9472;sdb3   8:19   0   8.7G  0 part  
 &#9500;&#9472;sdb4   8:20   0     1M  0 part  
 &#9500;&#9472;sdb5   8:21   0 894.9G  0 part  
 &#9492;&#9472;sdb6   8:22   0   8.7G  0 part  
 sr0     11:0    1  1024M  0 rom   
 dave@dave-desktop:~$
```

---

### Post by aviator1 on 2016-07-22
I ran the dmesg again and it looks very different. Would post, but do not know how to use code tags.

---

### Post by papibe on 2016-07-22
How to use code tags: [https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168](https://ubuntuforums.org/showthread.php?t=2171721&p=12776168#post12776168)

---

### Post by aviator1 on 2016-07-22
Here is the dmesg

```
   [    2.622013] type=1400 audit(1469234099.564:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=427 comm="apparmor_parser" 
 [    2.622188] type=1400 audit(1469234099.564:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=427 comm="apparmor_parser" 
 [    2.639177] SKU: Nid=0x1d sku_cfg=0x4005e601 
 [    2.639180] SKU: port_connectivity=0x1 
 [    2.639181] SKU: enable_pcbeep=0x0 
 [    2.639182] SKU: check_sum=0x00000005 
 [    2.639182] SKU: customization=0x000000e6 
 [    2.639183] SKU: external_amp=0x0 
 [    2.639184] SKU: platform_type=0x0 
 [    2.639185] SKU: swap=0x0 
 [    2.639186] SKU: override=0x1 
 [    2.639639] autoconfig: line_outs=4 (0x14/0x15/0x16/0x17/0x0) type:line 
 [    2.639640]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0) 
 [    2.639642]    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0) 
 [    2.639642]    mono: mono_out=0x0 
 [    2.639643]    dig-out=0x11/0x1e 
 [    2.639644]    inputs: 
 [    2.639645]      Front Mic=0x19 
 [    2.639646]      Rear Mic=0x18 
 [    2.639647]      Line=0x1a 
 [    2.639648] realtek: No valid SSID, checking pincfg 0x4005e601 for NID 0x1d 
 [    2.639649] realtek: Enabling init ASM_ID=0xe601 CODEC_ID=10ec0887 
 [    2.652034] kvm: Nested Virtualization enabled 
 [    2.652038] kvm: Nested Paging enabled 
 [    2.667115] input: HDA ATI SB Front Headphone as /devices/pci0000:00/0000:00:14.2/sound/card0/input12 
 [    2.667239] input: HDA ATI SB Line Out Side as /devices/pci0000:00/0000:00:14.2/sound/card0/input11 
 [    2.667430] input: HDA ATI SB Line Out CLFE as /devices/pci0000:00/0000:00:14.2/sound/card0/input10 
 [    2.667520] input: HDA ATI SB Line Out Surround as /devices/pci0000:00/0000:00:14.2/sound/card0/input9 
 [    2.667606] input: HDA ATI SB Line Out Front as /devices/pci0000:00/0000:00:14.2/sound/card0/input8 
 [    2.667691] input: HDA ATI SB Line as /devices/pci0000:00/0000:00:14.2/sound/card0/input7 
 [    2.667774] input: HDA ATI SB Rear Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input6 
 [    2.667865] input: HDA ATI SB Front Mic as /devices/pci0000:00/0000:00:14.2/sound/card0/input5 
 [    2.668557] hda_intel: Disabling MSI 
 [    2.668563] hda-intel 0000:01:00.1: Handle VGA-switcheroo audio client 
 [    2.668674] hda-intel 0000:01:00.1: Disabling 64bit DMA 
 [    2.672341] hda-intel 0000:01:00.1: Enable delay in RIRB handling 
 [    2.689736] asus_wmi: ASUS WMI generic driver loaded 
 [    2.691515] asus_wmi: Initialization: 0x0 
 [    2.691547] asus_wmi: BIOS WMI version: 0.9 
 [    2.691609] asus_wmi: SFUN value: 0x0 
 [    2.692085] input: Eee PC WMI hotkeys as /devices/platform/eeepc-wmi/input/input13 
 [    2.693376] asus_wmi: Disabling ACPI video driver 
 [    2.792268] init: failsafe main process (644) killed by TERM signal 
 [    2.889347] usb 5-4: new full-speed USB device number 2 using ohci-pci 
 [    2.936053] Bluetooth: Core ver 2.17 
 [    2.936069] NET: Registered protocol family 31 
 [    2.936071] Bluetooth: HCI device and connection manager initialized 
 [    2.936078] Bluetooth: HCI socket layer initialized 
 [    2.936080] Bluetooth: L2CAP socket layer initialized 
 [    2.936084] Bluetooth: SCO socket layer initialized 
 [    2.941863] type=1400 audit(1469234099.884:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=742 comm="apparmor_parser" 
 [    2.941871] type=1400 audit(1469234099.884:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=742 comm="apparmor_parser" 
 [    2.942200] type=1400 audit(1469234099.884:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=742 comm="apparmor_parser" 
 [    2.942394] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
 [    2.942397] Bluetooth: BNEP filters: protocol multicast 
 [    2.942405] Bluetooth: BNEP socket layer initialized 
 [    2.943015] Bluetooth: RFCOMM TTY layer initialized 
 [    2.943023] Bluetooth: RFCOMM socket layer initialized 
 [    2.943029] Bluetooth: RFCOMM ver 1.11 
 [    2.973867] init: cups main process (759) killed by HUP signal 
 [    2.973878] init: cups main process ended, respawning 
 [    3.066335] usb 5-4: New USB device found, idVendor=046d, idProduct=c52b 
 [    3.066339] usb 5-4: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
 [    3.066340] usb 5-4: Product: USB Receiver 
 [    3.066342] usb 5-4: Manufacturer: Logitech 
 [    3.109687] scsi 5:0:0:0: Direct-Access     HP       Photosmart 6520  1.00 PQ: 0 ANSI: 5 
 [    3.109880] sd 5:0:0:0: Attached scsi generic sg3 type 0 
 [    3.111184] sd 5:0:0:0: [sdc] Attached SCSI removable disk 
 [    3.113297] input: HDA NVidia HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input16 
 [    3.113425] input: HDA NVidia HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input15 
 [    3.113504] input: HDA NVidia HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:02.0/0000:01:00.1/sound/card1/input14 
 [    3.119795] init: samba-ad-dc main process (849) terminated with status 1 
 [    3.175672] Switched to clocksource tsc 
 [    3.183964] r8169 0000:02:00.0 eth0: link down 
 [    3.183990] r8169 0000:02:00.0 eth0: link down 
 [    3.184013] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [    3.184249] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [    3.333125] usb 5-5: new full-speed USB device number 3 using ohci-pci 
 [    3.398882] init: Failed to spawn hybrid-gfx main process: unable to execute: No such file or directory 
 [    3.506108] usb 5-5: New USB device found, idVendor=046d, idProduct=c52b 
 [    3.506111] usb 5-5: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
 [    3.506113] usb 5-5: Product: USB Receiver 
 [    3.506115] usb 5-5: Manufacturer: Logitech 
 [    3.518831] usblp 1-4:1.1: usblp0: USB Bidirectional printer dev 4 if 1 alt 0 proto 2 vid 0x03F0 pid 0xAF11 
 [    3.518864] usbcore: registered new interface driver usblp 
 [    3.549606] hidraw: raw HID events driver (C) Jiri Kosina 
 [    3.576153] usbcore: registered new interface driver usbhid 
 [    3.576155] usbhid: USB HID core driver 
 [    3.583179] logitech-djreceiver 0003:046D:C52B.0003: hiddev0,hidraw0: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-4/input2 
 [    3.588203] logitech-djreceiver 0003:046D:C52B.0006: hiddev0,hidraw1: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:13.0-5/input2 
 [    3.588454] input: Logitech Unifying Device. Wireless PID:1028 as /devices/pci0000:00/0000:00:13.0/usb5/5-4/5-4:1.2/0003:046D:C52B.0003/input/input17 
 [    3.588648] logitech-djdevice 0003:046D:C52B.0007: input,hidraw2: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1028] on usb-0000:00:13.0-4:1 
 [    3.592357] input: Logitech Unifying Device. Wireless PID:4004 as /devices/pci0000:00/0000:00:13.0/usb5/5-5/5-5:1.2/0003:046D:C52B.0006/input/input18 
 [    3.592537] logitech-djdevice 0003:046D:C52B.0008: input,hidraw3: USB HID v1.11 Keyboard [Logitech Unifying Device. Wireless PID:4004] on usb-0000:00:13.0-5:1 
 [    3.900818] usb 4-1: new full-speed USB device number 2 using ohci-pci 
 [    4.073782] usb 4-1: New USB device found, idVendor=046d, idProduct=c52b 
 [    4.073786] usb 4-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
 [    4.073788] usb 4-1: Product: USB Receiver 
 [    4.073789] usb 4-1: Manufacturer: Logitech 
 [    4.081349] init: plymouth-upstart-bridge main process ended, respawning 
 [    4.095909] logitech-djreceiver 0003:046D:C52B.000B: hiddev0,hidraw4: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:12.0-1/input2 
 [    4.099997] input: Logitech Unifying Device. Wireless PID:1028 as /devices/pci0000:00/0000:00:12.0/usb4/4-1/4-1:1.2/0003:046D:C52B.000B/input/input19 
 [    4.100149] logitech-djdevice 0003:046D:C52B.000C: input,hidraw5: USB HID v1.11 Mouse [Logitech Unifying Device. Wireless PID:1028] on usb-0000:00:12.0-1:1 
 [    4.111305] nvidia 0000:01:00.0: irq 89 for MSI/MSI-X 
 [    4.356558] usb 4-3: new full-speed USB device number 3 using ohci-pci 
 [    4.545518] usb 4-3: New USB device found, idVendor=0a48, idProduct=5007 
 [    4.545519] usb 4-3: New USB device strings: Mfr=1, Product=2, SerialNumber=0 
 [    4.545520] usb 4-3: Product: Secure Digital Keychain 
 [    4.545521] usb 4-3: Manufacturer: mediaGear 
 [    4.547578] usb-storage 4-3:1.0: USB Mass Storage device detected 
 [    4.547676] scsi6 : usb-storage 4-3:1.0 
 [    4.680554] init: plymouth-splash main process (1253) terminated with status 1 
 [    5.553936] scsi 6:0:0:0: Direct-Access     MG       SD-Key           1.00 PQ: 0 ANSI: 0 
 [    5.554131] sd 6:0:0:0: Attached scsi generic sg4 type 0 
 [    5.637890] sd 6:0:0:0: [sdd] Spinning up disk... 
 [    6.865558] r8169 0000:02:00.0 eth0: link up 
 [    6.865566] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready 
 [   32.980633] audit_printk_skb: 153 callbacks suppressed 
 [   32.980636] type=1400 audit(1469234129.950:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2357 comm="apparmor_parser" 
 [   32.980642] type=1400 audit(1469234129.950:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2357 comm="apparmor_parser" 
 [   32.980943] type=1400 audit(1469234129.950:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2357 comm="apparmor_parser" 
 [    6.643254] .............................................................................................not responding... 
 [  106.589273] sd 6:0:0:0: [sdd] READ CAPACITY failed 
 [  106.589283] sd 6:0:0:0: [sdd]   
 [  106.589287] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [  106.589290] sd 6:0:0:0: [sdd]   
 [  106.589293] Sense Key : Not Ready [current]  
 [  106.589299] sd 6:0:0:0: [sdd]   
 [  106.589305] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff 
 [  106.621218] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled 
 [  106.653202] sd 6:0:0:0: [sdd] Asking for cache data failed 
 [  106.653207] sd 6:0:0:0: [sdd] Assuming drive cache: write through 
 [  106.793085] sd 6:0:0:0: [sdd] Spinning up disk... 
 [  106.909099] sd 6:0:0:0: [sdd] Spinning up disk... 
 [  107.824938] . 
 [  107.912852] .. 
 [  108.995759] .. 
 [  110.078852] .. 
 [  111.161495] .. 
 [  112.248376] .. 
 [  113.335169] .. 
 [  114.422151] .. 
 [  115.508874] .. 
 [  116.595807] .. 
 [  117.682539] .. 
 [  118.769542] .. 
 [  119.860394] .. 
 [  120.947215] .. 
 [  122.034004] .. 
 [  123.120889] .. 
 [  124.207748] .. 
 [  125.294608] .. 
 [  126.377510] .. 
 [  127.464384] .. 
 [  128.547550] .. 
 [  129.630951] .. 
 [  130.714329] .. 
 [  131.797742] .. 
 [  132.881057] .. 
 [  133.964582] .. 
 [  135.047908] .. 
 [  136.135332] .. 
 [  137.222699] .. 
 [  138.310160] .. 
 [  139.397556] .. 
 [  140.484953] .. 
 [  141.572352] .. 
 [  142.659738] .. 
 [  143.747118] .. 
 [  144.834552] .. 
 [  145.921924] .. 
 [  147.009348] .. 
 [  148.096751] .. 
 [  149.184030] .. 
 [  150.271460] .. 
 [  151.354945] .. 
 [  152.438317] .. 
 [  153.521694] .. 
 [  154.605149] .. 
 [  155.688504] .. 
 [  156.771952] .. 
 [  157.855291] .. 
 [  158.938725] .. 
 [  160.022087] .. 
 [  161.109554] .. 
 [  162.196940] .. 
 [  163.284277] .. 
 [  164.371699] .. 
 [  165.459124] .. 
 [  166.546493] .. 
 [  167.633931] .. 
 [  168.721340] .. 
 [  169.808746] .. 
 [  170.896145] .. 
 [  171.983516] .. 
 [  173.070942] .. 
 [  174.158343] .. 
 [  175.241668] .. 
 [  176.325145] .. 
 [  177.408550] .. 
 [  178.491950] .. 
 [  179.575352] .. 
 [  180.658750] .. 
 [  181.742055] .. 
 [  182.825508] .. 
 [  183.908954] .. 
 [  184.996355] .. 
 [  186.083683] .. 
 [  187.171119] .. 
 [  188.262490] .. 
 [  189.349883] .. 
 [  190.437235] .. 
 [  191.524732] .. 
 [  192.612144] .. 
 [  193.699543] .. 
 [  194.786884] .. 
 [  195.874341] .. 
 [  196.961718] .. 
 [  198.049139] .. 
 [  199.132486] .. 
 [  200.215925] .. 
 [  201.299277] .. 
 [  202.382744] .. 
 [  203.466145] .. 
 [  204.549550] .. 
 [  205.632977] .. 
 [  206.716352] ..not responding... 
 [  207.799473] sd 6:0:0:0: [sdd] READ CAPACITY failed 
 [  207.799481] sd 6:0:0:0: [sdd]   
 [  207.799485] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [  207.799489] sd 6:0:0:0: [sdd]   
 [  207.799492] Sense Key : Not Ready [current]  
 [  207.799498] sd 6:0:0:0: [sdd]   
 [  207.799504] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff 
 [  207.799682] .not responding... 
 [  207.831461] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled 
 [  207.891429] sd 6:0:0:0: [sdd] Asking for cache data failed 
 [  207.891437] sd 6:0:0:0: [sdd] Assuming drive cache: write through 
 [  207.891444] sd 6:0:0:0: [sdd] Attached SCSI removable disk 
 [  207.977296] sd 6:0:0:0: [sdd] Spinning up disk... 
 [  208.983098] .............................................................................................not responding... 
 [  308.973626] sd 6:0:0:0: [sdd] READ CAPACITY failed 
 [  308.973635] sd 6:0:0:0: [sdd]   
 [  308.973639] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [  308.973642] sd 6:0:0:0: [sdd]   
 [  308.973645] Sense Key : Not Ready [current]  
 [  308.973651] sd 6:0:0:0: [sdd]   
 [  308.973657] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff 
 [  309.006609] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled 
 [  309.039591] sd 6:0:0:0: [sdd] Asking for cache data failed 
 [  309.039600] sd 6:0:0:0: [sdd] Assuming drive cache: write through 
 [  309.155465] sd 6:0:0:0: [sdd] Spinning up disk... 
 [  360.847241] INFO: task systemd-udevd:2597 blocked for more than 120 seconds. 
 [  360.847250]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu 
 [  360.847253] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message. 
 [  310.159179] ............................................... 
 [  360.847257] systemd-udevd   D ffff88043ed54480     0  2597    328 0x00000004 
 [  360.847266]  ffff8803f3bd3b30 0000000000000082 ffff8803f3834800 ffff8803f3bd3fd8 
 [  360.847274]  0000000000014480 0000000000014480 ffff8803f3834800 ffff880427fe0358 
 [  360.847281]  ffff880427fe035c ffff8803f3834800 00000000ffffffff ffff880427fe0360 
 [  360.847288] Call Trace: 
 [  360.847303]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70 
 [  360.847312]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0 
 [  360.847319]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f 
 [  360.847326]  [<ffffffff811f7413>] __blkdev_get+0x63/0x4c0 
 [  360.847332]  [<ffffffff811f7a35>] blkdev_get+0x1c5/0x340 
 [  360.847339]  [<ffffffff811f7c5b>] blkdev_open+0x5b/0x80 
 [  360.847345]  [<ffffffff811ba6c3>] do_dentry_open+0x233/0x2e0 
 [  360.847351]  [<ffffffff811f7c00>] ? blkdev_get_by_dev+0x50/0x50 
 [  360.847356]  [<ffffffff811ba9f9>] vfs_open+0x49/0x50 
 [  360.847363]  [<ffffffff811c9594>] do_last+0x554/0x1200 
 [  360.847371]  [<ffffffff81312d5b>] ? apparmor_file_alloc_security+0x5b/0x180 
 [  360.847378]  [<ffffffff811cca1b>] path_openat+0xbb/0x640 
 [  360.847386]  [<ffffffff811cddfa>] do_filp_open+0x3a/0x90 
 [  360.847394]  [<ffffffff811dac87>] ? __alloc_fd+0xa7/0x130 
 [  360.847401]  [<ffffffff811bc519>] do_sys_open+0x129/0x280 
 [  360.847407]  [<ffffffff811bc68e>] SyS_open+0x1e/0x20 
 [  360.847412]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f 
 [  361.194972] ..............................................not responding... 
 [  410.153691] sd 6:0:0:0: [sdd] READ CAPACITY failed 
 [  410.153700] sd 6:0:0:0: [sdd]   
 [  410.153704] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [  410.153708] sd 6:0:0:0: [sdd]   
 [  410.153711] Sense Key : Not Ready [current]  
 [  410.153717] sd 6:0:0:0: [sdd]   
 [  410.153723] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff 
 [  410.186785] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled 
 [  410.219697] sd 6:0:0:0: [sdd] Asking for cache data failed 
 [  410.219707] sd 6:0:0:0: [sdd] Assuming drive cache: write through 
 [  410.335641] sd 6:0:0:0: [sdd] Spinning up disk... 
 [  480.780905] INFO: task systemd-udevd:2600 blocked for more than 120 seconds. 
 [  480.780914]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu 
 [  480.780918] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message. 
 [  411.339215] ................................................................ 
 [  480.780922] systemd-udevd   D ffff88043ecd4480     0  2600    328 0x00000004 
 [  480.780930]  ffff880423fdfb30 0000000000000086 ffff880427bf3000 ffff880423fdffd8 
 [  480.780939]  0000000000014480 0000000000014480 ffff880427bf3000 ffff880427fe0358 
 [  480.780945]  ffff880427fe035c ffff880427bf3000 00000000ffffffff ffff880427fe0360 
 [  480.780952] Call Trace: 
 [  480.780968]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70 
 [  480.780976]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0 
 [  480.780983]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f 
 [  480.780991]  [<ffffffff811f7413>] __blkdev_get+0x63/0x4c0 
 [  480.780997]  [<ffffffff811f7a35>] blkdev_get+0x1c5/0x340 
 [  480.781003]  [<ffffffff811f7c5b>] blkdev_open+0x5b/0x80 
 [  480.781010]  [<ffffffff811ba6c3>] do_dentry_open+0x233/0x2e0 
 [  480.781016]  [<ffffffff811f7c00>] ? blkdev_get_by_dev+0x50/0x50 
 [  480.781022]  [<ffffffff811ba9f9>] vfs_open+0x49/0x50 
 [  480.781028]  [<ffffffff811c9594>] do_last+0x554/0x1200 
 [  480.781036]  [<ffffffff81312d5b>] ? apparmor_file_alloc_security+0x5b/0x180 
 [  480.781043]  [<ffffffff811cca1b>] path_openat+0xbb/0x640 
 [  480.781051]  [<ffffffff811cddfa>] do_filp_open+0x3a/0x90 
 [  480.781059]  [<ffffffff811dac87>] ? __alloc_fd+0xa7/0x130 
 [  480.781065]  [<ffffffff811bc519>] do_sys_open+0x129/0x280 
 [  480.781072]  [<ffffffff811bc68e>] SyS_open+0x1e/0x20 
 [  480.781078]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f 
 [  480.781083] INFO: task systemd-udevd:2601 blocked for more than 120 seconds. 
 [  480.781086]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu 
 [  480.781089] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message. 
 [  480.781091] systemd-udevd   D ffff88043ecd4480     0  2601    328 0x00000004 
 [  480.781097]  ffff8804285d3b30 0000000000000086 ffff8804018b9800 ffff8804285d3fd8 
 [  480.781104]  0000000000014480 0000000000014480 ffff8804018b9800 ffff880427fe0358 
 [  480.781110]  ffff880427fe035c ffff8804018b9800 00000000ffffffff ffff880427fe0360 
 [  480.781117] Call Trace: 
 [  480.781125]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70 
 [  480.781132]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0 
 [  480.781139]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f 
 [  480.781144]  [<ffffffff811f7413>] __blkdev_get+0x63/0x4c0 
 [  480.781150]  [<ffffffff811f7a35>] blkdev_get+0x1c5/0x340 
 [  480.781157]  [<ffffffff811f7c5b>] blkdev_open+0x5b/0x80 
 [  480.781162]  [<ffffffff811ba6c3>] do_dentry_open+0x233/0x2e0 
 [  480.781168]  [<ffffffff811f7c00>] ? blkdev_get_by_dev+0x50/0x50 
 [  480.781173]  [<ffffffff811ba9f9>] vfs_open+0x49/0x50 
 [  480.781179]  [<ffffffff811c9594>] do_last+0x554/0x1200 
 [  480.781185]  [<ffffffff81312d5b>] ? apparmor_file_alloc_security+0x5b/0x180 
 [  480.781193]  [<ffffffff811cca1b>] path_openat+0xbb/0x640 
 [  480.781200]  [<ffffffff811cddfa>] do_filp_open+0x3a/0x90 
 [  480.781207]  [<ffffffff811dac87>] ? __alloc_fd+0xa7/0x130 
 [  480.781213]  [<ffffffff811bc519>] do_sys_open+0x129/0x280 
 [  480.781219]  [<ffffffff811bc68e>] SyS_open+0x1e/0x20 
 [  480.781224]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f 
 [  480.864789] .............................not responding... 
 [  511.374036] sd 6:0:0:0: [sdd] READ CAPACITY failed 
 [  511.374044] sd 6:0:0:0: [sdd]   
 [  511.374048] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [  511.374052] sd 6:0:0:0: [sdd]   
 [  511.374054] Sense Key : Not Ready [current]  
 [  511.374060] sd 6:0:0:0: [sdd]   
 [  511.374066] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff 
 [  511.407016] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled 
 [  511.440031] sd 6:0:0:0: [sdd] Asking for cache data failed 
 [  511.440040] sd 6:0:0:0: [sdd] Assuming drive cache: write through 
 [  511.555932] sd 6:0:0:0: [sdd] Spinning up disk... 
 [  600.714572] INFO: task systemd-udevd:2601 blocked for more than 120 seconds. 
 [  600.714580]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu 
 [  600.714584] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message. 
 [  512.563272] .................................................................................. 
 [  600.714589] systemd-udevd   D ffff88043ecd4480     0  2601    328 0x00000004 
 [  600.714597]  ffff8804285d3b30 0000000000000086 ffff8804018b9800 ffff8804285d3fd8 
 [  600.714605]  0000000000014480 0000000000014480 ffff8804018b9800 ffff880427fe0358 
 [  600.714612]  ffff880427fe035c ffff8804018b9800 00000000ffffffff ffff880427fe0360 
 [  600.714620] Call Trace: 
 [  600.714636]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70 
 [  600.714644]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0 
 [  600.714652]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f 
 [  600.714659]  [<ffffffff811f7413>] __blkdev_get+0x63/0x4c0 
 [  600.714665]  [<ffffffff811f7a35>] blkdev_get+0x1c5/0x340 
 [  600.714672]  [<ffffffff811f7c5b>] blkdev_open+0x5b/0x80 
 [  600.714679]  [<ffffffff811ba6c3>] do_dentry_open+0x233/0x2e0 
 [  600.714685]  [<ffffffff811f7c00>] ? blkdev_get_by_dev+0x50/0x50 
 [  600.714690]  [<ffffffff811ba9f9>] vfs_open+0x49/0x50 
 [  600.714697]  [<ffffffff811c9594>] do_last+0x554/0x1200 
 [  600.714705]  [<ffffffff81312d5b>] ? apparmor_file_alloc_security+0x5b/0x180 
 [  600.714713]  [<ffffffff811cca1b>] path_openat+0xbb/0x640 
 [  600.714720]  [<ffffffff811cddfa>] do_filp_open+0x3a/0x90 
 [  600.714728]  [<ffffffff811dac87>] ? __alloc_fd+0xa7/0x130 
 [  600.714735]  [<ffffffff811bc519>] do_sys_open+0x129/0x280 
 [  600.714741]  [<ffffffff811bc68e>] SyS_open+0x1e/0x20 
 [  600.714747]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f 
 [  600.714752] INFO: task systemd-udevd:2602 blocked for more than 120 seconds. 
 [  600.714756]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu 
 [  600.714758] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message. 
 [  600.714761] systemd-udevd   D ffff88043ec54480     0  2602    328 0x00000004 
 [  600.714766]  ffff8800af747b30 0000000000000086 ffff8804285d8000 ffff8800af747fd8 
 [  600.714773]  0000000000014480 0000000000014480 ffff8804285d8000 ffff880427fe0358 
 [  600.714780]  ffff880427fe035c ffff8804285d8000 00000000ffffffff ffff880427fe0360 
 [  600.714786] Call Trace: 
 [  600.714794]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70 
 [  600.714801]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0 
 [  600.714808]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f 
 [  600.714814]  [<ffffffff811f7413>] __blkdev_get+0x63/0x4c0 
 [  600.714820]  [<ffffffff811f7a35>] blkdev_get+0x1c5/0x340 
 [  600.714826]  [<ffffffff811f7c5b>] blkdev_open+0x5b/0x80 
 [  600.714832]  [<ffffffff811ba6c3>] do_dentry_open+0x233/0x2e0 
 [  600.714837]  [<ffffffff811f7c00>] ? blkdev_get_by_dev+0x50/0x50 
 [  600.714843]  [<ffffffff811ba9f9>] vfs_open+0x49/0x50 
 [  600.714848]  [<ffffffff811c9594>] do_last+0x554/0x1200 
 [  600.714855]  [<ffffffff81312d5b>] ? apparmor_file_alloc_security+0x5b/0x180 
 [  600.714862]  [<ffffffff811cca1b>] path_openat+0xbb/0x640 
 [  600.714869]  [<ffffffff811cddfa>] do_filp_open+0x3a/0x90 
 [  600.714876]  [<ffffffff811dac87>] ? __alloc_fd+0xa7/0x130 
 [  600.714883]  [<ffffffff811bc519>] do_sys_open+0x129/0x280 
 [  600.714889]  [<ffffffff811bc68e>] SyS_open+0x1e/0x20 
 [  600.714894]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f 
 [  600.714899] INFO: task systemd-udevd:2607 blocked for more than 120 seconds. 
 [  600.714902]       Tainted: P           OX 3.13.0-37-generic #64-Ubuntu 
 [  600.714905] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message. 
 [  600.714907] systemd-udevd   D ffff88043ec54480     0  2607    328 0x00000004 
 [  600.714913]  ffff8803d895db30 0000000000000082 ffff8803d89b8000 ffff8803d895dfd8 
 [  600.714919]  0000000000014480 0000000000014480 ffff8803d89b8000 ffff880427fe0358 
 [  600.714925]  ffff880427fe035c ffff8803d89b8000 00000000ffffffff ffff880427fe0360 
 [  600.714932] Call Trace: 
 [  600.714939]  [<ffffffff81723649>] schedule_preempt_disabled+0x29/0x70 
 [  600.714946]  [<ffffffff817254b5>] __mutex_lock_slowpath+0x135/0x1b0 
 [  600.714953]  [<ffffffff8172554f>] mutex_lock+0x1f/0x2f 
 [  600.714959]  [<ffffffff811f7413>] __blkdev_get+0x63/0x4c0 
 [  600.714965]  [<ffffffff811f7a35>] blkdev_get+0x1c5/0x340 
 [  600.714971]  [<ffffffff811f7c5b>] blkdev_open+0x5b/0x80 
 [  600.714977]  [<ffffffff811ba6c3>] do_dentry_open+0x233/0x2e0 
 [  600.714982]  [<ffffffff811f7c00>] ? blkdev_get_by_dev+0x50/0x50 
 [  600.714987]  [<ffffffff811ba9f9>] vfs_open+0x49/0x50 
 [  600.714993]  [<ffffffff811c9594>] do_last+0x554/0x1200 
 [  600.715000]  [<ffffffff81312d5b>] ? apparmor_file_alloc_security+0x5b/0x180 
 [  600.715007]  [<ffffffff811cca1b>] path_openat+0xbb/0x640 
 [  600.715014]  [<ffffffff811cddfa>] do_filp_open+0x3a/0x90 
 [  600.715021]  [<ffffffff811dac87>] ? __alloc_fd+0xa7/0x130 
 [  600.715027]  [<ffffffff811bc519>] do_sys_open+0x129/0x280 
 [  600.715034]  [<ffffffff811bc68e>] SyS_open+0x1e/0x20 
 [  600.715039]  [<ffffffff8172f82d>] system_call_fastpath+0x1a/0x1f 
 [  601.610065] ...........not responding... 
 [  612.550374] sd 6:0:0:0: [sdd] READ CAPACITY failed 
 [  612.550381] sd 6:0:0:0: [sdd]   
 [  612.550383] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE 
 [  612.550386] sd 6:0:0:0: [sdd]   
 [  612.550388] Sense Key : Not Ready [current]  
 [  612.550392] sd 6:0:0:0: [sdd]   
 [  612.550396] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff 
 [  612.583392] sd 6:0:0:0: [sdd] Test WP failed, assume Write Enabled 
 [  612.616335] sd 6:0:0:0: [sdd] Asking for cache data failed 
 [  612.616342] sd 6:0:0:0: [sdd] Assuming drive cache: write through 
 [  612.732220] sd 6:0:0:0: [sdd] Spinning up disk... 
 dave@dave-desktop:~$ 
```

---

### Post by papibe on 2016-07-22
There's the disk again. It looks connected, and slowing down the boot process.

Do you have a mount point for it? Could you post the content of your /etc/fstab?

Regards.

P.S.: Thanks for the code tags! :D

---

### Post by aviator1 on 2016-07-22
> **papibe said:**
> There's the disk again. It looks connected, and slowing down the boot process.

Do you have a mount point for it? Could you post the content of your /etc/fstab?

Regards.

P.S.: Thanks for the code tags! :D

The external disk was and is definitely disconnected.

Do not know what a mount point is, or how to determine where it is. Sorry.

Also, typed /etc/fstab and got a permission denied message.

Thanks for your help.

---

### Post by QDR06VV9 on 2016-07-22
> **aviator1 said:**
> The external disk was and is definitely disconnected.

Do not know what a mount point is, or how to determine where it is. Sorry.

Also, typed /etc/fstab and got a permission denied message.

Thanks for your help.
Sorry for jumping in here use a text editor in front of /etc/fstab
Like this
```
gedit /etc/fstab
```
If you do not have gedit replace with installed editor IE pluma, kate mousepad, etc etc

---

### Post by oldfred on 2016-07-22
And you need sudo or gksudo to edit fstab.

If you want to see what fstab is:

cat /etc/fstab

---

### Post by papibe on 2016-07-22
Now that you booted without the external drive, what is the result of these (I added an fstab command):
```
mount -l | grep sdd

df -h

lsblk

cat /etc/fstab
```
Regards.

---

### Post by aviator1 on 2016-07-22
> **runrickus said:**
> Sorry for jumping in here use a text editor in front of /etc/fstab
Like this
```
gedit /etc/fstab
```
If you do not have gedit replace with installed editor IE pluma, kate mousepad, etc etc

Thanks very much. Learning all the time. :-)

```

# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
# / was on /dev/sda6 during installation
UUID=75e89545-dc5c-4553-907d-23269bb7b2a9 /               ext4    errors=remount-ro 0       1
# swap was on /dev/sda5 during installation
UUID=80d61814-fc43-4c38-b772-d32945f6b4a1 none            swap    sw              0       0 
```

---

### Post by aviator1 on 2016-07-22
Thank you oldfred.

---

### Post by aviator1 on 2016-07-22
I have to go offline for the night. 5 AM was early today.

I really appreciate all the help.

Please post any requirements, and I will get to them first thing in the morning.

Regards.

---

### Post by aviator1 on 2016-07-23
Here is something interesting.

I had an extra internal HD from another compter that has 12.04 on it. I disconnected both my SSD and current internal HD, and connected the "new" HD.

I still have the external HD disconnected.

I have the same problems with the boot up time with the "new" HD connected. About 5 minutes to the ID screen, and about 8 minutes to get to the desktop. This HD only has 12.04 on it.

Any ideas or suggestions?

Thanks everyone.

---

### Post by oldfred on 2016-07-23
Now another drive can be totally separate unrelated issues.

But if you run dmesg, do you get the same jumps in timestamps as you showed in Post #2? 6 sec, to 33 sec to 106 sec? And is it the same issues?
Just post any parts with large jumps, no need to post entire dmesg.

---

### Post by aviator1 on 2016-07-23
Not sure what you meant about post just parts

```

[  600.431893]  [<ffffffff811f0f07>] ? __alloc_fd+0xa7/0x130
[  600.431895]  [<ffffffff811d2ce9>] do_sys_open+0x129/0x280
[  600.431897]  [<ffffffff8105b2b1>] ? do_page_fault+0x31/0x70
[  600.431899]  [<ffffffff811d2e5e>] SyS_open+0x1e/0x20
[  600.431901]  [<ffffffff8176aced>] system_call_fastpath+0x1a/0x1f
[  600.431903] INFO: task systemd-udevd:2467 blocked for more than 120 seconds.
[  600.431904]       Not tainted 3.16.0-30-generic #40~14.04.1-Ubuntu
[  600.431905] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  600.431906] systemd-udevd   D ffff88043ec53440     0  2467    341 0x00000004
[  600.431907]  ffff880425207b10 0000000000000086 ffff880417390000 ffff880425207fd8
[  600.431909]  0000000000013440 0000000000013440 ffff880428659460 ffff880424068d18
[  600.431911]  ffff880424068d1c ffff880417390000 00000000ffffffff ffff880424068d20
[  600.431913] Call Trace:
[  600.431915]  [<ffffffff81767159>] schedule_preempt_disabled+0x29/0x70
[  600.431917]  [<ffffffff81768fa5>] __mutex_lock_slowpath+0xd5/0x1d0
[  600.431919]  [<ffffffff817690bf>] mutex_lock+0x1f/0x2f
[  600.431921]  [<ffffffff8120a823>] __blkdev_get+0x63/0x4c0
[  600.431923]  [<ffffffff8120ae45>] blkdev_get+0x1c5/0x340
[  600.431925]  [<ffffffff8120b06b>] blkdev_open+0x5b/0x80
[  600.431927]  [<ffffffff811d117f>] do_dentry_open+0x1ff/0x350
[  600.431929]  [<ffffffff8120b010>] ? blkdev_get_by_dev+0x50/0x50
[  600.431931]  [<ffffffff811d1419>] vfs_open+0x49/0x50
[  600.431933]  [<ffffffff811dfb44>] do_last+0x564/0x1240
[  600.431935]  [<ffffffff811e0dd1>] ? link_path_walk+0x71/0x8a0
[  600.431937]  [<ffffffff8132af4b>] ? apparmor_file_alloc_security+0x5b/0x180
[  600.431939]  [<ffffffff811e266b>] path_openat+0xbb/0x670
[  600.431941]  [<ffffffff8118e71b>] ? handle_mm_fault+0x7db/0x10b0
[  600.431943]  [<ffffffff811e438a>] do_filp_open+0x3a/0x90
[  600.431945]  [<ffffffff811f0f07>] ? __alloc_fd+0xa7/0x130
[  600.431947]  [<ffffffff811d2ce9>] do_sys_open+0x129/0x280
[  600.431949]  [<ffffffff8105b2b1>] ? do_page_fault+0x31/0x70
[  600.431952]  [<ffffffff811d2e5e>] SyS_open+0x1e/0x20
[  600.431953]  [<ffffffff8176aced>] system_call_fastpath+0x1a/0x1f
[  601.003714] ............not responding...
[  613.067416] sd 4:0:0:0: [sdc] READ CAPACITY failed
[  613.067424] sd 4:0:0:0: [sdc]  
[  613.067428] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  613.067432] sd 4:0:0:0: [sdc]  
[  613.067435] Sense Key : Not Ready [current] 
[  613.067441] sd 4:0:0:0: [sdc]  
[  613.067447] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  613.245345] sd 4:0:0:0: [sdc] Spinning up disk...
[  614.251069] ......................................
[  655.127836] systemd-hostnamed[2486]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[  655.491719] .......................................................not responding...
[  714.221962] sd 4:0:0:0: [sdc] READ CAPACITY failed
[  714.221965] sd 4:0:0:0: [sdc]  
[  714.221967] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  714.221968] sd 4:0:0:0: [sdc]  
[  714.221969] Sense Key : Not Ready [current] 
[  714.221971] sd 4:0:0:0: [sdc]  
[  714.221974] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  714.403947] sd 4:0:0:0: [sdc] Spinning up disk...
[  715.410966] .....
[  720.376212] INFO: task systemd-udevd:2467 blocked for more than 120 seconds.
[  720.376220]       Not tainted 3.16.0-30-generic #40~14.04.1-Ubuntu
[  720.376224] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.376228] systemd-udevd   D ffff88043ec53440     0  2467    341 0x00000004
[  720.376236]  ffff880425207b10 0000000000000086 ffff880417390000 ffff880425207fd8
[  720.376242]  0000000000013440 0000000000013440 ffff880428659460 ffff880424068d18
[  720.376248]  ffff880424068d1c ffff880417390000 00000000ffffffff ffff880424068d20
[  720.376254] Call Trace:
[  720.376267]  [<ffffffff81767159>] schedule_preempt_disabled+0x29/0x70
[  720.376274]  [<ffffffff81768fa5>] __mutex_lock_slowpath+0xd5/0x1d0
[  720.376280]  [<ffffffff817690bf>] mutex_lock+0x1f/0x2f
[  720.376287]  [<ffffffff8120a823>] __blkdev_get+0x63/0x4c0
[  720.376293]  [<ffffffff8120ae45>] blkdev_get+0x1c5/0x340
[  720.376299]  [<ffffffff8120b06b>] blkdev_open+0x5b/0x80
[  720.376306]  [<ffffffff811d117f>] do_dentry_open+0x1ff/0x350
[  720.376311]  [<ffffffff8120b010>] ? blkdev_get_by_dev+0x50/0x50
[  720.376317]  [<ffffffff811d1419>] vfs_open+0x49/0x50
[  720.376324]  [<ffffffff811dfb44>] do_last+0x564/0x1240
[  720.376330]  [<ffffffff811e0dd1>] ? link_path_walk+0x71/0x8a0
[  720.376336]  [<ffffffff8132af4b>] ? apparmor_file_alloc_security+0x5b/0x180
[  720.376344]  [<ffffffff811e266b>] path_openat+0xbb/0x670
[  720.376350]  [<ffffffff8118e71b>] ? handle_mm_fault+0x7db/0x10b0
[  720.376356]  [<ffffffff811e438a>] do_filp_open+0x3a/0x90
[  720.376362]  [<ffffffff811f0f07>] ? __alloc_fd+0xa7/0x130
[  720.376369]  [<ffffffff811d2ce9>] do_sys_open+0x129/0x280
[  720.376376]  [<ffffffff8105b2b1>] ? do_page_fault+0x31/0x70
[  720.376382]  [<ffffffff811d2e5e>] SyS_open+0x1e/0x20
[  720.376388]  [<ffffffff8176aced>] system_call_fastpath+0x1a/0x1f
[  720.376393] INFO: task systemd-udevd:2468 blocked for more than 120 seconds.
[  720.376397]       Not tainted 3.16.0-30-generic #40~14.04.1-Ubuntu
[  720.376399] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.376402] systemd-udevd   D ffff88043ecd3440     0  2468    341 0x00000004
[  720.376408]  ffff880424897b10 0000000000000082 ffff880424fd4750 ffff880424897fd8
[  720.376414]  0000000000013440 0000000000013440 ffff8804248cf010 ffff880424068d18
[  720.376419]  ffff880424068d1c ffff880424fd4750 00000000ffffffff ffff880424068d20
[  720.376425] Call Trace:
[  720.376432]  [<ffffffff81767159>] schedule_preempt_disabled+0x29/0x70
[  720.376437]  [<ffffffff81768fa5>] __mutex_lock_slowpath+0xd5/0x1d0
[  720.376443]  [<ffffffff817690bf>] mutex_lock+0x1f/0x2f
[  720.376448]  [<ffffffff8120a823>] __blkdev_get+0x63/0x4c0
[  720.376454]  [<ffffffff8120ae45>] blkdev_get+0x1c5/0x340
[  720.376460]  [<ffffffff8120b06b>] blkdev_open+0x5b/0x80
[  720.376466]  [<ffffffff811d117f>] do_dentry_open+0x1ff/0x350
[  720.376472]  [<ffffffff8120b010>] ? blkdev_get_by_dev+0x50/0x50
[  720.376477]  [<ffffffff811d1419>] vfs_open+0x49/0x50
[  720.376483]  [<ffffffff811dfb44>] do_last+0x564/0x1240
[  720.376489]  [<ffffffff811e0dd1>] ? link_path_walk+0x71/0x8a0
[  720.376495]  [<ffffffff8132af4b>] ? apparmor_file_alloc_security+0x5b/0x180
[  720.376502]  [<ffffffff811e266b>] path_openat+0xbb/0x670
[  720.376508]  [<ffffffff8118e71b>] ? handle_mm_fault+0x7db/0x10b0
[  720.376514]  [<ffffffff811e438a>] do_filp_open+0x3a/0x90
[  720.376520]  [<ffffffff811f0f07>] ? __alloc_fd+0xa7/0x130
[  720.376526]  [<ffffffff811d2ce9>] do_sys_open+0x129/0x280
[  720.376532]  [<ffffffff8105b2b1>] ? do_page_fault+0x31/0x70
[  720.376538]  [<ffffffff811d2e5e>] SyS_open+0x1e/0x20
[  720.376544]  [<ffffffff8176aced>] system_call_fastpath+0x1a/0x1f
[  720.376549] INFO: task systemd-udevd:2469 blocked for more than 120 seconds.
[  720.376552]       Not tainted 3.16.0-30-generic #40~14.04.1-Ubuntu
[  720.376554] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  720.376557] systemd-udevd   D ffff88043ed53440     0  2469    341 0x00000004
[  720.376562]  ffff8800b67e3b10 0000000000000082 ffff880409cee5e0 ffff8800b67e3fd8
[  720.376568]  0000000000013440 0000000000013440 ffff88042802e5e0 ffff880424068d18
[  720.376573]  ffff880424068d1c ffff880409cee5e0 00000000ffffffff ffff880424068d20
[  720.376579] Call Trace:
[  720.376585]  [<ffffffff81767159>] schedule_preempt_disabled+0x29/0x70
[  720.376590]  [<ffffffff81768fa5>] __mutex_lock_slowpath+0xd5/0x1d0
[  720.376596]  [<ffffffff817690bf>] mutex_lock+0x1f/0x2f
[  720.376602]  [<ffffffff8120a823>] __blkdev_get+0x63/0x4c0
[  720.376607]  [<ffffffff8120ae45>] blkdev_get+0x1c5/0x340
[  720.376614]  [<ffffffff8120b06b>] blkdev_open+0x5b/0x80
[  720.376619]  [<ffffffff811d117f>] do_dentry_open+0x1ff/0x350
[  720.376625]  [<ffffffff8120b010>] ? blkdev_get_by_dev+0x50/0x50
[  720.376630]  [<ffffffff811d1419>] vfs_open+0x49/0x50
[  720.376636]  [<ffffffff811dfb44>] do_last+0x564/0x1240
[  720.376642]  [<ffffffff811e0dd1>] ? link_path_walk+0x71/0x8a0
[  720.376648]  [<ffffffff8132af4b>] ? apparmor_file_alloc_security+0x5b/0x180
[  720.376655]  [<ffffffff811e266b>] path_openat+0xbb/0x670
[  720.376661]  [<ffffffff8118e71b>] ? handle_mm_fault+0x7db/0x10b0
[  720.376667]  [<ffffffff811e438a>] do_filp_open+0x3a/0x90
[  720.376673]  [<ffffffff811f0f07>] ? __alloc_fd+0xa7/0x130
[  720.376679]  [<ffffffff811d2ce9>] do_sys_open+0x129/0x280
[  720.376685]  [<ffffffff8105b2b1>] ? do_page_fault+0x31/0x70
[  720.376692]  [<ffffffff811d2e5e>] SyS_open+0x1e/0x20
[  720.376697]  [<ffffffff8176aced>] system_call_fastpath+0x1a/0x1f
[  720.847997] ........................................................................................not responding...
[  815.387614] sd 4:0:0:0: [sdc] READ CAPACITY failed
[  815.387622] sd 4:0:0:0: [sdc]  
[  815.387626] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  815.387630] sd 4:0:0:0: [sdc]  
[  815.387633] Sense Key : Not Ready [current] 
[  815.387638] sd 4:0:0:0: [sdc]  
[  815.387644] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  815.563512] sd 4:0:0:0: [sdc] Spinning up disk...
[  816.567532] ......................
[  840.310655] INFO: task systemd-udevd:2468 blocked for more than 120 seconds.
[  840.310663]       Not tainted 3.16.0-30-generic #40~14.04.1-Ubuntu
[  840.310666] "echo 0 > /proc/sys/kernel/hung_task_timeout_secs" disables this message.
[  840.310670] systemd-udevd   D ffff88043ecd3440     0  2468    341 0x00000004
[  840.310678]  ffff880424897b10 0000000000000082 ffff880424fd4750 ffff880424897fd8
[  840.310684]  0000000000013440 0000000000013440 ffff8804248cf010 ffff880424068d18
[  840.310690]  ffff880424068d1c ffff880424fd4750 00000000ffffffff ffff880424068d20
[  840.310696] Call Trace:
[  840.310709]  [<ffffffff81767159>] schedule_preempt_disabled+0x29/0x70
[  840.310715]  [<ffffffff81768fa5>] __mutex_lock_slowpath+0xd5/0x1d0
[  840.310721]  [<ffffffff817690bf>] mutex_lock+0x1f/0x2f
[  840.310728]  [<ffffffff8120a823>] __blkdev_get+0x63/0x4c0
[  840.310734]  [<ffffffff8120ae45>] blkdev_get+0x1c5/0x340
[  840.310740]  [<ffffffff8120b06b>] blkdev_open+0x5b/0x80
[  840.310747]  [<ffffffff811d117f>] do_dentry_open+0x1ff/0x350
[  840.310753]  [<ffffffff8120b010>] ? blkdev_get_by_dev+0x50/0x50
[  840.310758]  [<ffffffff811d1419>] vfs_open+0x49/0x50
[  840.310765]  [<ffffffff811dfb44>] do_last+0x564/0x1240
[  840.310771]  [<ffffffff811e0dd1>] ? link_path_walk+0x71/0x8a0
[  840.310777]  [<ffffffff8132af4b>] ? apparmor_file_alloc_security+0x5b/0x180
[  840.310785]  [<ffffffff811e266b>] path_openat+0xbb/0x670
[  840.310791]  [<ffffffff8118e71b>] ? handle_mm_fault+0x7db/0x10b0
[  840.310797]  [<ffffffff811e438a>] do_filp_open+0x3a/0x90
[  840.310804]  [<ffffffff811f0f07>] ? __alloc_fd+0xa7/0x130
[  840.310810]  [<ffffffff811d2ce9>] do_sys_open+0x129/0x280
[  840.310817]  [<ffffffff8105b2b1>] ? do_page_fault+0x31/0x70
[  840.310823]  [<ffffffff811d2e5e>] SyS_open+0x1e/0x20
[  840.310829]  [<ffffffff8176aced>] system_call_fastpath+0x1a/0x1f
[  840.462514] .......................................................................not responding...
[  916.571192] sd 4:0:0:0: [sdc] READ CAPACITY failed
[  916.571199] sd 4:0:0:0: [sdc]  
[  916.571203] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[  916.571207] sd 4:0:0:0: [sdc]  
[  916.571210] Sense Key : Not Ready [current] 
[  916.571215] sd 4:0:0:0: [sdc]  
[  916.571222] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[  916.753078] sd 4:0:0:0: [sdc] Spinning up disk...
[  917.760218] .............................................................................................not responding...
[ 1017.735710] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1017.735717] sd 4:0:0:0: [sdc]  
[ 1017.735720] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1017.735724] sd 4:0:0:0: [sdc]  
[ 1017.735727] Sense Key : Not Ready [current] 
[ 1017.735733] sd 4:0:0:0: [sdc]  
[ 1017.735739] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1017.917548] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1018.924818] .............................................................................................not responding...
[ 1118.917267] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1118.917275] sd 4:0:0:0: [sdc]  
[ 1118.917279] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1118.917283] sd 4:0:0:0: [sdc]  
[ 1118.917285] Sense Key : Not Ready [current] 
[ 1118.917291] sd 4:0:0:0: [sdc]  
[ 1118.917297] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1119.093194] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1120.097470] .............................................................................................not responding...
[ 1220.092910] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1220.092918] sd 4:0:0:0: [sdc]  
[ 1220.092922] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1220.092926] sd 4:0:0:0: [sdc]  
[ 1220.092928] Sense Key : Not Ready [current] 
[ 1220.092934] sd 4:0:0:0: [sdc]  
[ 1220.092940] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1220.274799] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1221.282034] .............................................................................................not responding...
[ 1321.254502] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1321.254510] sd 4:0:0:0: [sdc]  
[ 1321.254514] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1321.254518] sd 4:0:0:0: [sdc]  
[ 1321.254521] Sense Key : Not Ready [current] 
[ 1321.254526] sd 4:0:0:0: [sdc]  
[ 1321.254532] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1321.436399] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1322.442620] .............................................................................................not responding...
[ 1422.456088] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1422.456096] sd 4:0:0:0: [sdc]  
[ 1422.456100] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1422.456103] sd 4:0:0:0: [sdc]  
[ 1422.456106] Sense Key : Not Ready [current] 
[ 1422.456112] sd 4:0:0:0: [sdc]  
[ 1422.456118] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1422.632975] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1423.639292] .............................................................................................not responding...
[ 1523.618660] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1523.618669] sd 4:0:0:0: [sdc]  
[ 1523.618674] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1523.618678] sd 4:0:0:0: [sdc]  
[ 1523.618681] Sense Key : Not Ready [current] 
[ 1523.618689] sd 4:0:0:0: [sdc]  
[ 1523.618696] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1523.800565] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1524.807833] ..........................................
[ 1569.618011] init: upstart-udev-bridge main process (334) terminated with status 1
[ 1569.618024] init: upstart-udev-bridge main process ended, respawning
[ 1569.618140] init: upstart-socket-bridge main process (591) terminated with status 1
[ 1569.618147] init: upstart-socket-bridge main process ended, respawning
[ 1569.618226] init: upstart-file-bridge main process (771) terminated with status 1
[ 1569.618232] init: upstart-file-bridge main process ended, respawning
[ 1570.414928] .........................................
[ 1614.067152] init: systemd-logind main process (892) killed by TERM signal
[ 1614.974508] ..........not responding...
[ 1624.828169] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1624.828177] sd 4:0:0:0: [sdc]  
[ 1624.828181] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1624.828185] sd 4:0:0:0: [sdc]  
[ 1624.828187] Sense Key : Not Ready [current] 
[ 1624.828193] sd 4:0:0:0: [sdc]  
[ 1624.828199] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1625.004138] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1626.008428] .............................................................................................not responding...
[ 1726.047750] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1726.047758] sd 4:0:0:0: [sdc]  
[ 1726.047762] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1726.047766] sd 4:0:0:0: [sdc]  
[ 1726.047769] Sense Key : Not Ready [current] 
[ 1726.047775] sd 4:0:0:0: [sdc]  
[ 1726.047781] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1726.226691] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1727.236967] .............................................................................................not responding...
[ 1827.264270] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1827.264275] sd 4:0:0:0: [sdc]  
[ 1827.264278] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1827.264281] sd 4:0:0:0: [sdc]  
[ 1827.264282] Sense Key : Not Ready [current] 
[ 1827.264286] sd 4:0:0:0: [sdc]  
[ 1827.264290] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1827.446157] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1828.453655] .............................................................................................not responding...
[ 1928.473901] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 1928.473908] sd 4:0:0:0: [sdc]  
[ 1928.473912] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 1928.473916] sd 4:0:0:0: [sdc]  
[ 1928.473919] Sense Key : Not Ready [current] 
[ 1928.473924] sd 4:0:0:0: [sdc]  
[ 1928.473930] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 1928.649846] sd 4:0:0:0: [sdc] Spinning up disk...
[ 1929.654275] ...........................................................................
[ 2010.428148] systemd-hostnamed[15591]: Warning: nss-myhostname is not installed. Changing the local hostname might make it unresolveable. Please install nss-myhostname!
[ 2011.113628] ..................not responding...
[ 2029.689439] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2029.689446] sd 4:0:0:0: [sdc]  
[ 2029.689448] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2029.689451] sd 4:0:0:0: [sdc]  
[ 2029.689453] Sense Key : Not Ready [current] 
[ 2029.689457] sd 4:0:0:0: [sdc]  
[ 2029.689461] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2029.871424] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2030.878870] .............................................................................................not responding...
[ 2130.898047] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2130.898055] sd 4:0:0:0: [sdc]  
[ 2130.898059] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2130.898063] sd 4:0:0:0: [sdc]  
[ 2130.898065] Sense Key : Not Ready [current] 
[ 2130.898071] sd 4:0:0:0: [sdc]  
[ 2130.898077] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2131.079956] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2132.087467] ..........................................................
[ 2194.824346] init: udev main process (341) killed by KILL signal
[ 2194.850830] systemd-udevd[18514]: starting version 204
[ 2195.104888] ....
[ 2199.371372] audit_printk_skb: 144 callbacks suppressed
[ 2199.371375] audit: type=1400 audit(1469284016.237:72): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=18714 comm="apparmor_parser"
[ 2199.454481] .
[ 2199.720351] audit: type=1400 audit(1469284016.585:73): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=18753 comm="apparmor_parser"
[ 2200.541975] .
[ 2200.566190] audit: type=1400 audit(1469284017.433:74): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=18777 comm="apparmor_parser"
[ 2200.566505] audit: type=1400 audit(1469284017.433:75): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=18777 comm="apparmor_parser"
[ 2200.631365] audit: type=1400 audit(1469284017.497:76): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=18814 comm="apparmor_parser"
[ 2200.631383] audit: type=1400 audit(1469284017.497:77): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=18814 comm="apparmor_parser"
[ 2200.632259] audit: type=1400 audit(1469284017.497:78): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=18814 comm="apparmor_parser"
[ 2201.625423] ...........................
[ 2230.633180] SGI XFS with ACLs, security attributes, realtime, large block/inode numbers, no debug enabled
[ 2230.706374] JFS: nTxBlock = 8192, nTxLock = 65536
[ 2230.797618] ntfs: driver 2.1.30 [Flags: R/O MODULE].
[ 2230.898249] QNX4 filesystem 0.2.3 registered.
[ 2230.973287] .
[ 2231.013192] raid6: sse2x1    2286 MB/s
[ 2231.081178] raid6: sse2x2    3633 MB/s
[ 2231.149120] raid6: sse2x4    4380 MB/s
[ 2231.149124] raid6: using algorithm sse2x4 (4380 MB/s)
[ 2231.149127] raid6: using ssse3x2 recovery algorithm
[ 2231.180038] xor: automatically using best checksumming function:
[ 2231.217078]    avx       :  1720.000 MB/sec
[ 2231.314460] Btrfs loaded
[ 2232.056699] .not responding...
[ 2232.151615] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2232.151620] sd 4:0:0:0: [sdc]  
[ 2232.151622] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2232.151623] sd 4:0:0:0: [sdc]  
[ 2232.151624] Sense Key : Not Ready [current] 
[ 2232.151626] sd 4:0:0:0: [sdc]  
[ 2232.151629] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2232.327497] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2233.331935] ...........
[ 2245.188071] audit: type=1400 audit(1469284062.077:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=415 comm="apparmor_parser"
[ 2245.188327] audit: type=1400 audit(1469284062.077:80): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=415 comm="apparmor_parser"
[ 2245.188545] audit: type=1400 audit(1469284062.077:81): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=415 comm="apparmor_parser"
[ 2245.277436] .......
[ 2252.804387] audit: type=1400 audit(1469284069.697:82): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/tcpdump" pid=4338 comm="apparmor_parser"
[ 2252.889286] ...........................................................................not responding...
[ 2333.375235] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2333.375243] sd 4:0:0:0: [sdc]  
[ 2333.375247] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2333.375251] sd 4:0:0:0: [sdc]  
[ 2333.375253] Sense Key : Not Ready [current] 
[ 2333.375259] sd 4:0:0:0: [sdc]  
[ 2333.375265] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2333.557155] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2334.564629] .............................................................................................not responding...
[ 2434.607746] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2434.607752] sd 4:0:0:0: [sdc]  
[ 2434.607755] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2434.607759] sd 4:0:0:0: [sdc]  
[ 2434.607762] Sense Key : Not Ready [current] 
[ 2434.607768] sd 4:0:0:0: [sdc]  
[ 2434.607774] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2434.789662] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2435.793167] .............................................................................................not responding...
[ 2535.846363] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2535.846371] sd 4:0:0:0: [sdc]  
[ 2535.846375] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2535.846378] sd 4:0:0:0: [sdc]  
[ 2535.846381] Sense Key : Not Ready [current] 
[ 2535.846387] sd 4:0:0:0: [sdc]  
[ 2535.846393] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2536.022262] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2537.029789] .............................................................................................not responding...
[ 2637.056879] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2637.056887] sd 4:0:0:0: [sdc]  
[ 2637.056891] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2637.056895] sd 4:0:0:0: [sdc]  
[ 2637.056897] Sense Key : Not Ready [current] 
[ 2637.056903] sd 4:0:0:0: [sdc]  
[ 2637.056909] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2637.238855] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2638.246354] .............................................................................................not responding...
[ 2738.261510] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2738.261524] sd 4:0:0:0: [sdc]  
[ 2738.261528] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2738.261532] sd 4:0:0:0: [sdc]  
[ 2738.261535] Sense Key : Not Ready [current] 
[ 2738.261540] sd 4:0:0:0: [sdc]  
[ 2738.261546] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2738.443406] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2739.446999] .............................................................................................not responding...
[ 2839.452094] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2839.452102] sd 4:0:0:0: [sdc]  
[ 2839.452105] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2839.452109] sd 4:0:0:0: [sdc]  
[ 2839.452112] Sense Key : Not Ready [current] 
[ 2839.452156] sd 4:0:0:0: [sdc]  
[ 2839.452163] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2839.628009] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2840.631641] .............................................................................................not responding...
[ 2940.614633] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 2940.614641] sd 4:0:0:0: [sdc]  
[ 2940.614644] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 2940.614648] sd 4:0:0:0: [sdc]  
[ 2940.614651] Sense Key : Not Ready [current] 
[ 2940.614657] sd 4:0:0:0: [sdc]  
[ 2940.614663] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 2940.796587] sd 4:0:0:0: [sdc] Spinning up disk...
[ 2941.800170] .............................................................................................not responding...
[ 3041.765245] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3041.765252] sd 4:0:0:0: [sdc]  
[ 3041.765256] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3041.765260] sd 4:0:0:0: [sdc]  
[ 3041.765262] Sense Key : Not Ready [current] 
[ 3041.765268] sd 4:0:0:0: [sdc]  
[ 3041.765274] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3041.947192] sd 4:0:0:0: [sdc] Spinning up disk...
[ 3042.952759] .............................................................................................not responding...
[ 3142.941834] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3142.941842] sd 4:0:0:0: [sdc]  
[ 3142.941846] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3142.941850] sd 4:0:0:0: [sdc]  
[ 3142.941852] Sense Key : Not Ready [current] 
[ 3142.941858] sd 4:0:0:0: [sdc]  
[ 3142.941864] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3143.117738] sd 4:0:0:0: [sdc] Spinning up disk...
[ 3144.121427] .............................................................................................not responding...
[ 3244.104441] sd 4:0:0:0: [sdc] READ CAPACITY failed
[ 3244.104450] sd 4:0:0:0: [sdc]  
[ 3244.104453] Result: hostbyte=DID_OK driverbyte=DRIVER_SENSE
[ 3244.104457] sd 4:0:0:0: [sdc]  
[ 3244.104460] Sense Key : Not Ready [current] 
[ 3244.104465] sd 4:0:0:0: [sdc]  
[ 3244.104471] <<vendor>> ASC=0xff ASCQ=0xffASC=0xff <<vendor>> ASCQ=0xff
[ 3244.286387] sd 4:0:0:0: [sdc] Spinning up disk...
dave@dave-AY748AA-ABA-p6320y:~$ 


```

---

### Post by oldfred on 2016-07-23
Bigger jumps like this:
```
[  916.753078] sd 4:0:0:0: [sdc] Spinning up disk...
[  917.760218] .............................................................................................not responding...
[ 1017.735710] sd 4:0:0:0: [sdc] READ CAPACITY failed
```

And that says major issues with sdc.
Again does BIOS show sdc, then does Disks & Smart Status show sdc as ok, then if ok, have you run fsck on sdc partition(s) or if NTFS, chkdsk?

---

### Post by aviator1 on 2016-07-23
> **oldfred said:**
> Bigger jumps like this:
```
[  916.753078] sd 4:0:0:0: [sdc] Spinning up disk...
[  917.760218] .............................................................................................not responding...
[ 1017.735710] sd 4:0:0:0: [sdc] READ CAPACITY failed
```

And that says major issues with sdc.
Again does BIOS show sdc, then does Disks & Smart Status show sdc as ok, then if ok, have you run fsck on sdc partition(s) or if NTFS, chkdsk?
.

I would not lose anything if I reformatted the old HD if that would help.

I'm a basic user, and do not understand the commands. The SMART disk shows the SSD as being OK. It shows the older HD as OK, but with 96 bad sectors.

Thanks for your help.

---

### Post by oldfred on 2016-07-23
96 bad sectors is not particularly good, but with drives it is increasing numbers of bad sectors in a short time that is the real issue.

Is sdc an internal drive, or do you have it in an USB caddy?
If external it may not be getting enough power. Is power thru USB port or from separate power brick?

---

### Post by aviator1 on 2016-07-23
> **oldfred said:**
> 96 bad sectors is not particularly good, but with drives it is increasing numbers of bad sectors in a short time that is the real issue.

Is sdc an internal drive, or do you have it in an USB caddy?
If external it may not be getting enough power. Is power thru USB port or from separate power brick?

I only have 2 drives at this time. Both are internal. One is the SSD and the other is a 2 TB HD

So far it appears the 2 TB drive is the issue?????

How can I determine which drive is which?

---

### Post by aviator1 on 2016-07-23
> **aviator1 said:**
> .

I would not lose anything if I reformatted the old HD if that would help.

I'm a basic user, and do not understand the commands. The SMART disk shows the SSD as being OK. It shows the older HD as OK, but with 96 bad sectors.

Thanks for your help.

I only have 2 drives at this time. Both are internal. One is the SSD and the other is a 2 TB HD

So far it appears the 2 TB drive is the issue?????

How can I determine which drive is which?

---

### Post by oldfred on 2016-07-23
As in Post #5

sudo lshw -C Disk -short

---

### Post by aviator1 on 2016-07-23
I get the same as from post #5

When I enter** sudo lshw -C Disk -short** I get a request for my password. After  entering my password, I get PCI (SYSFS), which disappears and then I get  SCSI on the screen.

---

### Post by oldfred on 2016-07-23
I get this. Never noticed the PCI(SYSFS), but in looking closely it does flash by.

```
fred@Z170N:~$ sudo lshw -C Disk -short 
H/W path           Device     Class          Description
========================================================
/0/1/0.0.0         /dev/sda   disk           250GB Samsung SSD 850
/0/2/0.0.0         /dev/sdb   disk           1TB HGST HTS721010A9

```

Are your drives connected with SCSI not SATA? I thought the system saw just about everything the same now.

---

### Post by smelheim85 on 2016-07-23
What is the /media/dave/TOSHIBA EXT device?  That looks like an external device like a flash drive or external hard drive.  I would start there because that device is almost full but shouldn't be the cause of slow boot up or shutdown depending on what the device is.

---

### Post by aviator1 on 2016-07-23
> **oldfred said:**
> I get this. Never noticed the PCI(SYSFS), but in looking closely it does flash by.

```
fred@Z170N:~$ sudo lshw -C Disk -short 
H/W path           Device     Class          Description
========================================================
/0/1/0.0.0         /dev/sda   disk           250GB Samsung SSD 850
/0/2/0.0.0         /dev/sdb   disk           1TB HGST HTS721010A9

```

Are your drives connected with SCSI not SATA? I thought the system saw just about everything the same now.

How do I tell if they are connected SCSI or SATA?

---

### Post by aviator1 on 2016-07-23
The SSD is connected with a black cable which appears to be SATA.

The older HD is connected with a red SATA cable.

Both are connected into SATA type female slots on the mpher board.

---

### Post by aviator1 on 2016-07-23
> **smelheim85 said:**
> What is the /media/dave/TOSHIBA EXT device?  That looks like an external device like a flash drive or external hard drive.  I would start there because that device is almost full but shouldn't be the cause of slow boot up or shutdown depending on what the device is.

The TOSHIBA was an external HD used as a back up. It has not been connected since yesterday.

---

### Post by oldfred on 2016-07-23
I do not understand why you are not correctly seeing the drives.
What setting in UEFI/BIOS are drives, should be AHCI, not RAID nor IDE nor anything else.

---

### Post by aviator1 on 2016-07-23
> **oldfred said:**
> I do not understand why you are not correctly seeing the drives.
What setting in UEFI/BIOS are drives, should be AHCI, not RAID nor IDE nor anything else.

Oldfred, I really appreciate the help you are giving me.

How do I find the UEFI/BIOS settings?

Thanks

---

### Post by aviator1 on 2016-07-23
Well......my problems have escalated..........

With the SSD and 2 TB HD will not boot at all.

I added the third HD I had as a backup and the computer will boot to it.

During the boot process, I get no choice as to which OS to select. It only boots to this third HD, which has 12.04 on it.

Also, during the boot up, the compter shuts down. It boots fine on the second start.

Boot up time to this new drive seems normal.

I can see and access the SSD and 2 TB HD once I get booted up on the third drive.

Oh well........

---

### Post by oldfred on 2016-07-23
You have to go into UEFI and find the tab for drive configurations, see attached for my Asus. I have normal boot for power on. And entry at top for fast boot I turned off during setup & configuration.

I think some boot parameter is missing.
But do not know your motherboard and what other boot parameter to add to grub.

---

### Post by aviator1 on 2016-07-24
I have an ASUS M5A97 mother board. Having major drive boot up issues. Have copied UEFI info.

Will publish tomorrow afternoon.

Thanks very much.

---

### Post by aviator1 on 2016-07-24
Had a few minutes this evening. Made some progress I looked at GRUB repair and used the following:

sudo **apt-add**-repository ppa:yannubuntu/boot-repair
sudo apt-get update
sudo apt-get install -y boot-repair
boot-repair

That got me back to a pretty normal boot situation. Boot up times seem pretty normal, and I get a selection of what drives to log on to during the sequence.

I now have 3 drives hooked up to the mother board. An SSD, a 2 TB HD, and a 500 GB HD.

If I disconnect the 500 GB HD, I get to a screen that shows GRUB- RESCUE, but goes no farther.

During the boot process, if I select the 500 GB HD, the sequence starts, but stalls. On the reboot, it goes through perfectly.

Also, when I boot to my SSD, I now see 2 250 GB drives on my icons. When I select disks, I see the SSD and the 500 GB HD, but do not see the 2 TB HD.

How do I upload/post my UEFI images?

Thanks for any help.

---

### Post by oldfred on 2016-07-24
My new UEFI systems allow me to take screen shots and save to a partition, but they only recognize FAT32. 
My old BIOS system I just used camera, shrank photos to much smaller size and uploaded.

Use Forum's advanced Editor and the paperclip icon.
       If you use the advanced editor, you can use the paperclip icon to attach screenshots. Post #4
[http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098](http://ubuntuforums.org/showthread.php?t=2054969&p=12229098#post12229098)

---

### Post by aviator1 on 2016-07-26
Will be back on in a few days. Have had some medical issues. I appreciate all the help.

---

