---
title: "Ubuntu 12.10 will not boot all the time"
date: 2013-04-20
forum: General Help
---

### Post by SUPERFITTER on 2013-04-20
I have a duel boot system, Windows 7 and Ubuntu 12.10.  Windows 7 I have no problem booting in Grub.  Ubuntu 12.10 will not boot all the time and I have to hit the reset button on my tower once or twice to get  Ubuntu 12.10 to boot. When it is booted I do not have any problem getting on the Internet or updates.    

 Ubuntu 12.10 is on a 500 Gb drive and Windows 7 is on another 500Gb drive.  Has anyone else had this problem?  If so how did you correct this problem?
 

 Thank You

---

### Post by oldfred on 2013-04-20
Is system shutting down normally? 

Have you looked in log files to see if anything is reported as not loading, trying repeatedly and then working (sometimes?) or just errors.
I use log file viewer and look at dmesg first, but there are many log files.

logs are in:
 /var/log

---

### Post by SUPERFITTER on 2013-04-21
My system shuts down normally.

These are the files that I found:

```
[    0.531809] hub 4-0:1.0: USB hub found
[    0.531814] hub 4-0:1.0: 4 ports detected
[    0.531877] usbcore: registered new interface driver libusual
[    0.531895] i8042: PNP: PS/2 Controller [PNP0303:PS2K] at 0x60,0x64 irq 1
[    0.531896] i8042: PNP: PS/2 appears to have AUX port disabled, if this is incorrect please boot with i8042.nopnp
[    0.532008] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.532049] mousedev: PS/2 mouse device common for all mice
[    0.532107] rtc_cmos 00:06: RTC can wake from S4
[    0.532202] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.532225] rtc0: alarms up to one month, y3k, 242 bytes nvram, hpet irqs
[    0.532258] device-mapper: uevent: version 1.0.3
[    0.532290] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[    0.532350] cpuidle: using governor ladder
[    0.532434] cpuidle: using governor menu
[    0.532435] EFI Variables Facility v0.08 2004-May-17
[    0.532557] ashmem: initialized
[    0.532616] TCP: cubic registered
[    0.532663] NET: Registered protocol family 10
[    0.532766] NET: Registered protocol family 17
[    0.532772] Key type dns_resolver registered
[    0.532890] PM: Hibernation image not present or could not be loaded.
[    0.532896] registered taskstats version 1
[    0.534540] Key type trusted registered
[    0.536067] Key type encrypted registered
[    0.537794]   Magic number: 9:5:962
[    0.537851] memory memory13: hash matches
[    0.537927] rtc_cmos 00:06: setting system clock to 2013-04-21 00:59:36 UTC (1366505976)
[    0.538841] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.538842] EDD information not available.
[    0.539804] Freeing unused kernel memory: 932k freed
[    0.539872] Write protecting the kernel read-only data: 12288k
[    0.542242] Freeing unused kernel memory: 1472k freed
[    0.544104] Freeing unused kernel memory: 1136k freed
[    0.552743] udevd[114]: starting version 175
[    0.556122] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input2
[    0.567652] ahci 0000:00:1f.2: version 3.0
[    0.567823] ahci 0000:00:1f.2: irq 42 for MSI/MSI-X
[    0.583349] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x13 impl SATA mode
[    0.583355] ahci 0000:00:1f.2: flags: 64bit ncq led clo pio slum part ems apst 
[    0.583361] ahci 0000:00:1f.2: setting latency timer to 64
[    0.599693] scsi0 : ahci
[    0.599824] scsi1 : ahci
[    0.599955] scsi2 : ahci
[    0.600042] scsi3 : ahci
[    0.600166] scsi4 : ahci
[    0.600289] scsi5 : ahci
[    0.600431] ata1: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16100 irq 42
[    0.600433] ata2: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16180 irq 42
[    0.600434] ata3: DUMMY
[    0.600434] ata4: DUMMY
[    0.600435] ata5: SATA max UDMA/133 abar m2048@0xf7f16000 port 0xf7f16300 irq 42
[    0.600436] ata6: DUMMY
[    0.827112] usb 1-1: new high-speed USB device number 2 using ehci_hcd
[    0.919034] ata1: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.919059] ata2: SATA link up 6.0 Gbps (SStatus 133 SControl 300)
[    0.919083] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    0.920456] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.920464] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff880408477d70), AE_NOT_FOUND (20120320/psparse-536)
[    0.920503] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.920507] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff880408477de8), AE_NOT_FOUND (20120320/psparse-536)
[    0.920890] ata1.00: ATA-8: WDC WD5000AAKX-00ERMA0, 15.01H15, max UDMA/133
[    0.920895] ata1.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.921326] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.921333] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880408477f50), AE_NOT_FOUND (20120320/psparse-536)
[    0.921352] ata5.00: ATAPI: TSSTcorp CDDVDW SH-224BB, SB00, max UDMA/100
[    0.921741] ata2.00: ATA-8: WDC WD5000AAKX-00ERMA0, 15.01H15, max UDMA/133
[    0.921745] ata2.00: 976773168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    0.922398] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.922406] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT0._GTF] (Node ffff880408477d70), AE_NOT_FOUND (20120320/psparse-536)
[    0.922676] ata1.00: configured for UDMA/133
[    0.922885] scsi 0:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-0 15.0 PQ: 0 ANSI: 5
[    0.922979] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    0.922995] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.923025] sd 0:0:0:0: [sda] Write Protect is off
[    0.923027] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    0.923037] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.923147] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.923151] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT1._GTF] (Node ffff880408477de8), AE_NOT_FOUND (20120320/psparse-536)
[    0.923339] ata2.00: configured for UDMA/133
[    0.925561] ACPI Error: [DSSP] Namespace lookup failure, AE_NOT_FOUND (20120320/psargs-359)
[    0.925568] ACPI Error: Method parse/execution failed [\_SB_.PCI0.SAT0.SPT4._GTF] (Node ffff880408477f50), AE_NOT_FOUND (20120320/psparse-536)
[    0.925580] ata5.00: configured for UDMA/100
[    0.946207]  sda: sda1 sda2 < sda5 >
[    0.946611] sd 0:0:0:0: [sda] Attached SCSI disk
[    0.946780] scsi 1:0:0:0: Direct-Access     ATA      WDC WD5000AAKX-0 15.0 PQ: 0 ANSI: 5
[    0.946833] sd 1:0:0:0: [sdb] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[    0.946850] sd 1:0:0:0: [sdb] Write Protect is off
[    0.946851] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    0.946855] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    0.946859] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    0.959353] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[    0.959358] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    0.959587] hub 1-1:1.0: USB hub found
[    0.959686] hub 1-1:1.0: 6 ports detected
[    0.993414]  sdb: sdb1 sdb2 < sdb5 sdb6 >
[    0.993902] sd 1:0:0:0: [sdb] Attached SCSI disk
[    0.996196] scsi 4:0:0:0: CD-ROM            TSSTcorp CDDVDW SH-224BB  SB00 PQ: 0 ANSI: 5
[    0.999358] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    0.999363] cdrom: Uniform CD-ROM driver Revision: 3.20
[    0.999517] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    0.999601] sr 4:0:0:0: Attached scsi generic sg2 type 5
[    1.070860] usb 2-1: new high-speed USB device number 2 using ehci_hcd
[    1.203077] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[    1.203081] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    1.203335] hub 2-1:1.0: USB hub found
[    1.203443] hub 2-1:1.0: 8 ports detected
[    1.357120] EXT4-fs (sdb1): INFO: recovery required on readonly filesystem
[    1.357121] EXT4-fs (sdb1): write access will be enabled during recovery
[    1.370559] usb 3-3: new high-speed USB device number 2 using xhci_hcd
[    1.387744] usb 3-3: New USB device found, idVendor=0b05, idProduct=17ab
[    1.387747] usb 3-3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    1.387750] usb 3-3: Product: 802.11n WLAN Adapter
[    1.387752] usb 3-3: Manufacturer: Realtek
[    1.387754] usb 3-3: SerialNumber: 00e04c000001
[    1.438489] Refined TSC clocksource calibration: 3503.445 MHz.
[    1.438495] Switching to clocksource tsc
[    1.458584] usb 1-1.4: new low-speed USB device number 3 using ehci_hcd
[    1.554607] usb 1-1.4: New USB device found, idVendor=046d, idProduct=c05a
[    1.554612] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.554615] usb 1-1.4: Product: USB Optical Mouse
[    1.554617] usb 1-1.4: Manufacturer: Logitech
[    1.558400] usbcore: registered new interface driver usbhid
[    1.558402] usbhid: USB HID core driver
[    1.559507] input: Logitech USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input3
[    1.559639] hid-generic 0003:046D:C05A.0001: input,hidraw0: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:00:1a.0-1.4/input0
[    2.841769] EXT4-fs (sdb1): recovery complete
[    2.855954] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   10.272063] Adding 16736252k swap on /dev/sdb6.  Priority:-1 extents:1 across:16736252k 
[   10.389854] udevd[481]: starting version 175
[   10.513042] microcode: CPU0 sig=0x306a9, pf=0x2, revision=0x15
[   10.546219] microcode: CPU1 sig=0x306a9, pf=0x2, revision=0x15
[   10.546907] microcode: CPU2 sig=0x306a9, pf=0x2, revision=0x15
[   10.547508] microcode: CPU3 sig=0x306a9, pf=0x2, revision=0x15
[   10.548048] microcode: CPU4 sig=0x306a9, pf=0x2, revision=0x15
[   10.548574] microcode: CPU5 sig=0x306a9, pf=0x2, revision=0x15
[   10.549153] microcode: CPU6 sig=0x306a9, pf=0x2, revision=0x15
[   10.549748] microcode: CPU7 sig=0x306a9, pf=0x2, revision=0x15
[   10.550315] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[   10.629447] type=1400 audit(1366520386.595:2): apparmor="STATUS" operation="profile_load" name="/sbin/dhclient" pid=639 comm="apparmor_parser"
[   10.629648] type=1400 audit(1366520386.599:3): apparmor="STATUS" operation="profile_load" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=639 comm="apparmor_parser"
[   10.629760] type=1400 audit(1366520386.599:4): apparmor="STATUS" operation="profile_load" name="/usr/lib/connman/scripts/dhclient-script" pid=639 comm="apparmor_parser"
[   10.652593] ACPI Warning: 0x0000000000000460-0x000000000000047f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   10.652598] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.652599] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[   10.652601] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20120320/utaddress-251)
[   10.652603] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.652605] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \LED_ 1 (20120320/utaddress-251)
[   10.652606] ACPI Warning: 0x0000000000000500-0x000000000000053f SystemIO conflicts with Region \GPIO 2 (20120320/utaddress-251)
[   10.652608] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   10.652608] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   10.694274] 
[   10.694274] rtw driver version=v3.3.2_3192.20120103
[   10.694292] register rtw_netdev_ops to netdev_ops
[   10.694293] CHIP TYPE: RTL8188C_8192C
[   10.694294] 
[   10.694294] usb_endpoint_descriptor(0):
[   10.694295] bLength=7
[   10.694296] bDescriptorType=5
[   10.694296] bEndpointAddress=81
[   10.694297] wMaxPacketSize=200
[   10.694297] bInterval=0
[   10.694298] RT_usb_endpoint_is_bulk_in = 1
[   10.694298] 
[   10.694298] usb_endpoint_descriptor(1):
[   10.694299] bLength=7
[   10.694300] bDescriptorType=5
[   10.694300] bEndpointAddress=2
[   10.694301] wMaxPacketSize=200
[   10.694301] bInterval=0
[   10.694302] RT_usb_endpoint_is_bulk_out = 2
[   10.694302] 
[   10.694302] usb_endpoint_descriptor(2):
[   10.694303] bLength=7
[   10.694304] bDescriptorType=5
[   10.694304] bEndpointAddress=3
[   10.694305] wMaxPacketSize=200
[   10.694305] bInterval=0
[   10.694306] RT_usb_endpoint_is_bulk_out = 3
[   10.694306] 
[   10.694306] usb_endpoint_descriptor(3):
[   10.694307] bLength=7
[   10.694308] bDescriptorType=5
[   10.694308] bEndpointAddress=84
[   10.694309] wMaxPacketSize=40
[   10.694309] bInterval=1
[   10.694310] RT_usb_endpoint_is_int_in = 4, Interval = 1
[   10.694310] nr_endpoint=4, in_num=2, out_num=2
[   10.694310] 
[   10.694311] USB_SPEED_HIGH
[   10.694379] Chip Version ID: VERSION_NORMAL_TSMC_CHIP_92C.
[   10.694381] RF_Type is 2!!
[   10.694493] EEPROM type is E-FUSE
[   10.694495] ====> ReadAdapterInfo8192C
[   10.694535] Boot from EFUSE, Autoload OK !
[   10.718236] mei 0000:00:16.0: setting latency timer to 64
[   10.718280] mei 0000:00:16.0: irq 43 for MSI/MSI-X
[   10.723991] mei 0000:00:16.0: wd: failed to find the client
[   10.740039] Qualcomm Atheros(R) AR816x/AR817x PCI-E Ethernet Network Driver
[   10.749928] alx 0000:03:00.0: alx(90:2b:34:5a:b3:03): Qualcomm Atheros Ethernet Network Connection
[   10.750559] EEPROMVID = 0x0b05
[   10.750560] EEPROMPID = 0x17ab
[   10.750561] EEPROMCustomerID : 0x00
[   10.750562] EEPROMSubCustomerID: 0x00
[   10.750562] RT_CustomerID: 0x00
[   10.750563] _ReadMACAddress MAC Address from EFUSE = 08:60:6e:cd:f6:1a
[   10.750564] EEPROMRegulatory = 0x0
[   10.750565] _ReadBoardType(0)
[   10.750565] BT Coexistance = disable
[   10.750566] RT_ChannelPlan: 0x00
[   10.750567] _ReadPSSetting...bHWPwrPindetect(0)-bHWPowerdown(0) ,bSupportRemoteWakeup(0)
[   10.750567] ### PS params=>  power_mgnt(0),usbss_enable(0) ###
[   10.750568] ### AntDivCfg(0)
[   10.750568] readAdapterInfo_8192CU(): REPLACEMENT = 1
[   10.750569] <==== ReadAdapterInfo8192C in 56 ms
[   10.750636] rtw_macaddr_cfg MAC Address  = 08:60:6e:cd:f6:1a
[   10.750637] MAC Address from pnetdev->dev_addr= 08:60:6e:cd:f6:1a
[   10.750705] bDriverStopped:1, bSurpriseRemoved:0, bup:0, hw_init_completed:0
[   10.750717] usbcore: registered new interface driver rtl8192cu
[   10.758683] lp: driver loaded but no devices found
[   10.884407] kvm: disabled by bios
[   10.885720] kvm: disabled by bios
[   10.889737] kvm: disabled by bios
[   10.913770] kvm: disabled by bios
[   10.917820] kvm: disabled by bios
[   10.921721] kvm: disabled by bios
[   10.925653] kvm: disabled by bios
[   10.929613] kvm: disabled by bios
[   10.963279] [drm] Initialized drm 1.1.0 20060810
[   10.990195] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[   11.088327] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[   11.088446] input: HDA Intel PCH Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[   11.088502] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[   11.088555] input: HDA Intel PCH Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[   11.088607] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   11.088926] hda-intel: 0000:01:00.1: Handle VGA-switcheroo audio client
[   11.088927] hda-intel: Force to non-snoop mode
[   11.088968] snd_hda_intel 0000:01:00.1: irq 45 for MSI/MSI-X
[   11.391399] [drm] radeon defaulting to kernel modesetting.
[   11.391401] [drm] radeon kernel modesetting enabled.
[   11.667510] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   11.667552] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   11.667603] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   11.667649] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   11.667693] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input13
[   11.667717] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input14
[   11.667956] [drm] initializing kernel modesetting (VERDE 0x1002:0x683D 0x1458:0x2556).
[   11.667994] [drm] register mmio base: 0xF7E00000
[   11.667995] [drm] register mmio size: 262144
[   11.668056] ATOM BIOS: GV
[   11.668075] radeon 0000:01:00.0: VRAM: 1024M 0x0000000000000000 - 0x000000003FFFFFFF (1024M used)
[   11.668077] radeon 0000:01:00.0: GTT: 512M 0x0000000040000000 - 0x000000005FFFFFFF
[   11.672301] [drm] Detected VRAM RAM=1024M, BAR=256M
[   11.672303] [drm] RAM width 128bits DDR
[   11.672345] [TTM] Zone  kernel: Available graphics memory: 8196832 kiB
[   11.672346] [TTM] Zone   dma32: Available graphics memory: 2097152 kiB
[   11.672347] [TTM] Initializing pool allocator
[   11.672351] [TTM] Initializing DMA pool allocator
[   11.672368] [drm] radeon: 1024M of VRAM memory ready
[   11.672369] [drm] radeon: 512M of GTT memory ready.
[   11.672384] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   11.672385] [drm] Driver supports precise vblank timestamp query.
[   11.672425] radeon 0000:01:00.0: irq 46 for MSI/MSI-X
[   11.672433] radeon 0000:01:00.0: radeon: using MSI.
[   11.672466] [drm] radeon: irq initialized.
[   11.672470] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   11.672756] [drm] Loading VERDE Microcode
[   12.057642] [drm] PCIE GART of 512M enabled (table at 0x0000000000040000).
[   12.057727] radeon 0000:01:00.0: WB enabled
[   12.057729] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000040000c00 and cpu addr 0xffff8803f4a34c00
[   12.057730] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000040000c04 and cpu addr 0xffff8803f4a34c04
[   12.057731] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000040000c08 and cpu addr 0xffff8803f4a34c08
[   12.076408] [drm] ring test on 0 succeeded in 1 usecs
[   12.076413] [drm] ring test on 1 succeeded in 1 usecs
[   12.076416] [drm] ring test on 2 succeeded in 1 usecs
[   12.076551] [drm] ib test on ring 0 succeeded in 0 usecs
[   12.076586] [drm] ib test on ring 1 succeeded in 0 usecs
[   12.076623] [drm] ib test on ring 2 succeeded in 0 usecs
[   12.087181] [drm] Radeon Display Connectors
[   12.087183] [drm] Connector 0:
[   12.087184] [drm]   DP-1
[   12.087184] [drm]   HPD2
[   12.087185] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[   12.087186] [drm]   Encoders:
[   12.087186] [drm]     DFP1: INTERNAL_UNIPHY2
[   12.087187] [drm] Connector 1:
[   12.087188] [drm]   DP-2
[   12.087188] [drm]   HPD3
[   12.087189] [drm]   DDC: 0x6570 0x6570 0x6574 0x6574 0x6578 0x6578 0x657c 0x657c
[   12.087189] [drm]   Encoders:
[   12.087190] [drm]     DFP2: INTERNAL_UNIPHY2
[   12.087191] [drm] Connector 2:
[   12.087191] [drm]   HDMI-A-1
[   12.087192] [drm]   HPD1
[   12.087193] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[   12.087193] [drm]   Encoders:
[   12.087194] [drm]     DFP3: INTERNAL_UNIPHY1
[   12.087194] [drm] Connector 3:
[   12.087195] [drm]   DVI-I-1
[   12.087195] [drm]   HPD4
[   12.087196] [drm]   DDC: 0x6560 0x6560 0x6564 0x6564 0x6568 0x6568 0x656c 0x656c
[   12.087197] [drm]   Encoders:
[   12.087197] [drm]     DFP4: INTERNAL_UNIPHY
[   12.087198] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[   12.087410] [drm] Internal thermal controller with fan control
[   12.087438] [drm] radeon: power management initialized
[   12.140768] [drm] fb mappable at 0xE1143000
[   12.140769] [drm] vram apper at 0xE0000000
[   12.140770] [drm] size 7299072
[   12.140770] [drm] fb depth is 24
[   12.140771] [drm]    pitch is 6912
[   12.140855] fbcon: radeondrmfb (fb0) is primary device
[   12.140911] Console: switching to colour frame buffer device 210x65
[   12.140927] fb0: radeondrmfb frame buffer device
[   12.140928] drm: registered panic notifier
[   12.140931] [drm] Initialized radeon 2.18.0 20080528 for 0000:01:00.0 on minor 0
[   12.718138] EXT4-fs (sdb1): re-mounted. Opts: errors=remount-ro
[   12.759255] init: failsafe main process (929) killed by TERM signal
[   12.850986] type=1400 audit(1366520388.819:5): apparmor="STATUS" operation="profile_replace" name="/sbin/dhclient" pid=1014 comm="apparmor_parser"
[   12.851190] type=1400 audit(1366520388.819:6): apparmor="STATUS" operation="profile_replace" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=1014 comm="apparmor_parser"
[   12.851303] type=1400 audit(1366520388.819:7): apparmor="STATUS" operation="profile_replace" name="/usr/lib/connman/scripts/dhclient-script" pid=1014 comm="apparmor_parser"
[   12.851352] type=1400 audit(1366520388.819:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper" pid=1011 comm="apparmor_parser"
[   12.851364] type=1400 audit(1366520388.819:9): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper" pid=1012 comm="apparmor_parser"
[   12.851567] type=1400 audit(1366520388.823:10): apparmor="STATUS" operation="profile_load" name="/usr/lib/lightdm/lightdm/lightdm-guest-session-wrapper//chromium_browser" pid=1011 comm="apparmor_parser"
[   12.851591] type=1400 audit(1366520388.823:11): apparmor="STATUS" operation="profile_load" name="/usr/lib/x86_64-linux-gnu/lightdm-remote-session-freerdp/freerdp-session-wrapper//chromium_browser" pid=1012 comm="apparmor_parser"
[   13.105432] bDriverStopped=1
[   13.105651] +871x_drv - drv_open, bup=0
[   13.107881]  ===> FirmwareDownload91C() fw:Rtl819XFwImageArray_TSMC
[   13.107885] FirmwareDownload92C accquire FW from embedded image
[   13.107888] fw_ver=v79, fw_subver=0, sig=0x88c0
[   13.123006] ppdev: user-space parallel port driver
[   13.123214] fw download ok!
[   13.123215] Set RF Chip ID to RF_6052 and RF type to 2.
[   13.174180] Bluetooth: Core ver 2.16
[   13.174191] NET: Registered protocol family 31
[   13.174192] Bluetooth: HCI device and connection manager initialized
[   13.174193] Bluetooth: HCI socket layer initialized
[   13.174194] Bluetooth: L2CAP socket layer initialized
[   13.174196] Bluetooth: SCO socket layer initialized
[   13.190570] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   13.190572] Bluetooth: BNEP filters: protocol multicast
[   13.446415] Bluetooth: RFCOMM TTY layer initialized
[   13.446417] Bluetooth: RFCOMM socket layer initialized
[   13.446418] Bluetooth: RFCOMM ver 1.11
[   13.508960] IQK:Start!!!
[   13.514937] Path A IQK failed!!
[   13.516945] Path B IQK Success!!
[   13.521884] Path A IQK failed!!
[   13.523956] Path B IQK Success!!
[   13.525540] IQK: final_candidate is 0
[   13.525544] IQK: RegE94=0 RegE9C=0 RegEA4=0 RegEAC=0 RegEB4=102 RegEBC=b RegEC4=f7 RegECC=7
[   13.525544]  Path B IQ Calibration Success !
[   13.631815] pdmpriv->TxPowerTrackControl = 1
[   13.633375] MAC Address from REG_MACID = 08:60:6e:cd:f6:1a
[   13.633376] rtl8192cu_hal_init in 528ms
[   13.633378] MAC Address = 08:60:6e:cd:f6:1a
[   13.634925] -871x_drv - drv_open, bup=1
[   13.635575] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.635715] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   13.635727] set_mode = IW_MODE_INFRA
[   13.637016] alx 0000:03:00.0: irq 47 for MSI/MSI-X
[   13.637022] alx 0000:03:00.0: irq 48 for MSI/MSI-X
[   13.637027] alx 0000:03:00.0: irq 49 for MSI/MSI-X
[   13.637032] alx 0000:03:00.0: irq 50 for MSI/MSI-X
[   13.637037] alx 0000:03:00.0: irq 51 for MSI/MSI-X
[   13.637041] alx 0000:03:00.0: irq 52 for MSI/MSI-X
[   13.637046] alx 0000:03:00.0: irq 53 for MSI/MSI-X
[   13.637050] alx 0000:03:00.0: irq 54 for MSI/MSI-X
[   13.637055] alx 0000:03:00.0: irq 55 for MSI/MSI-X
[   13.638590] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.639137] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   13.722654] [rtw_wx_set_pmkid] IW_PMKSA_FLUSH!
[   13.722658] set_mode = IW_MODE_INFRA
[   13.722690] =>rtw_wx_set_essid
[   13.722691] ssid=g\xffffffc6isQ\xffffffffJ\xffffffec)\xffffffcd\xffffffba\xffffffba\xffffffab\xfffffff2\xfffffffb\xffffffe3F|\xffffffc2T\xfffffff8\x1b\xffffffe8\xffffffe7\xffffff8dvZ.c3\xffffff9f\xffffffc9\xffffff9a\xffffff9a\xffffffc0\xffffffdf\x1d\x02\x04\xffffff88\xffffffff\xffffffff, len=32
[   13.722693] Set SSID under fw_state=0x00000008
[   13.722694] <=rtw_wx_set_essid, ret -1
[   13.726663] [rtw_wx_set_pmkid] IW_PMKSA_FLUSH!
[   14.831254] survey done event(14)
[   14.833098] IW_SCAN_THIS_ESSID, ssid=SUPERFITTER1, len=12
[   15.934136] survey done event(e)
[   15.934330] wpa_set_encryption, crypt.alg = WEP
[   15.934331] (1)wep_key_idx=0
[   15.934332] wep, set_tx=1
[   15.934333] ==> rtw_set_key algorithm(1),keyid(0),key_mask(1)
[   15.934359] wpa_set_auth_algs, AUTH_ALG_OPEN_SYSTEM
[   15.934360] set_mode = IW_MODE_INFRA
[   15.934369] =>rtw_wx_set_essid
[   15.934370] ssid=SUPERFITTER1, len=12
[   15.934371] Set SSID under fw_state=0x00000008
[   15.934373] [by_bssid:0][assoc_ssid:SUPERFITTER1][to_roaming:0] new candidate: SUPERFITTER1(00:16:b6:b6:53:35) rssi:-46
[   15.934375] rtw_select_and_join_from_scanned_queue: candidate: SUPERFITTER1(00:16:b6:b6:53:35)
[   15.934377] link to Broadcom AP
[   15.934378] <=rtw_wx_set_essid, ret 0
[   15.934381] Set BSSID under fw_state=0x00000088
[   15.939033] link to Broadcom AP
[   15.941300] OnAuthClient
[   15.941305] network.SupportedRates[0]=82
[   15.941306] network.SupportedRates[1]=84
[   15.941307] network.SupportedRates[2]=8B
[   15.941308] network.SupportedRates[3]=96
[   15.941309] network.SupportedRates[4]=24
[   15.941310] network.SupportedRates[5]=30
[   15.941311] network.SupportedRates[6]=48
[   15.941312] network.SupportedRates[7]=6C
[   15.941313] network.SupportedRates[8]=0C
[   15.941314] network.SupportedRates[9]=12
[   15.941315] network.SupportedRates[10]=18
[   15.941316] network.SupportedRates[11]=60
[   15.941317] bssrate_len = 12
[   15.943488] OnAssocRsp
[   15.943493] report_join_res(1)
[   15.943496] rtw_joinbss_update_network
[   15.943502] rtw_joinbss_update_stainfo
[   15.943599] HW_VAR_BASIC_RATE: BrateCfg(0x15d)
[   15.943939] HTOnAssocRsp
[   15.944252] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   15.945482] update raid entry, mask=0x40000fff, arg=0x80
[   15.945958] rtl8192c_set_FwJoinBssReport_cmd mstatus(1)
[   15.946236] SetFwRsvdPagePkt
[   15.946244] Set RSVD page location to Fw.
[   15.946633] =>mlmeext_joinbss_event_callback
dennis@dennis:~$ 
```


What do I do next?

---

### Post by oldfred on 2013-04-21
Your 15sec boot looks pretty good. My hard drives are 30 to 40 sec and my inexensive SSD is 10 sec.

The only thing a little slow is this. And I am not sure if first or second entry (entry is start or finish as posted), but I think it is your swap taking 8 sec to mount? Perhaps because it is large? Or is it taking 8 sec to mount your / before the swap entry?

>  [    2.855954] EXT4-fs (sdb1): mounted filesystem with ordered data mode. Opts: (null)
[   10.272063] Adding 16736252k swap on /dev/sdb6.  Priority:-1 extents:1 across:16736252k 



This is my entry. I have / on sdd3 which is the SSD, and swap on hard drive.

>  [    5.599921] EXT4-fs (sdd3): mounted filesystem with ordered data mode. Opts: (null)
[    7.561106] Adding 3076412k swap on /dev/sdc11.  Priority:-1 extents:1 across:3076412k 



---

### Post by SUPERFITTER on 2013-04-21
Is there anyway to speed up this slow entry?  Are there other options?  I'm using a i7 processor and 16 Gbs of DDR3 memory.

---

### Post by oldfred on 2013-04-21
I noticed that it had to run file recovery. Is it having some sort of issue that need fsck on every other reboot?

Perhaps run the full fsck from a live installer DVD or Flash drive? Reboot fsck is just a quick check.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

---

### Post by SUPERFITTER on 2013-04-21
> **oldfred said:**
> I noticed that it had to run file recovery. Is it having some sort of issue that need fsck on every other reboot?

Perhaps run the full fsck from a live installer DVD or Flash drive? Reboot fsck is just a quick check.

       #From liveCD so everything is unmounted,swap off if necessary, change example shown with partition sdb1 to your partition(s)
#e2fsck is used to check the ext2/ext3/ext4 family of file systems. -p trys fixes where response not required
sudo e2fsck -C0 -p -f -v /dev/sdb1
#if errors: -y auto answers yes for fixes needing response see man e2fsck
sudo e2fsck -f -y -v /dev/sdb1

I understand running fsck in terminal with the live DVD after that I am confused.

---

### Post by oldfred on 2013-04-21
It is just to see it that clears up the message of it running recovery on boot.

---

### Post by SUPERFITTER on 2013-04-21
I ran fsck from the DVD and nothing changed. Is there anything that I can copy from the disk to fix problem?

---

### Post by oldfred on 2013-04-21
So is it still running recovery on every reboot?

Did e2fsck report any errors?

---

### Post by SUPERFITTER on 2013-04-22
ubuntu@ubuntu:~$ fsck
fsck from util-linux 2.20.1
ubuntu@ubuntu:~$ sudo e2fsck -C0 -p -f -v /dev/sdb1
/dev/sdb1: Superblock last mount time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set)  **FIXED**.
/dev/sdb1: Superblock last write time is in the future.
    (by less than a day, probably due to the hardware clock being incorrectly set).**  FIXED**.
                                                                               
      242338 inodes used (3.78%, out of 6406144)
         461 non-contiguous files (0.2%)
         299 non-contiguous directories (0.1%)
             # of inodes with ind/dind/tind blocks: 0/0/0
             Extent depth histogram: 192675/163/1
     2284008 blocks used (8.92%, out of 25599999)
           0 bad blocks
           1 large file

      153307 regular files
       24309 directories
          57 character device files
          25 block device files
           0 fifos
          18 links
       64631 symbolic links (49409 fast symbolic links)
           0 sockets
------------
      242347 files
ubuntu@ubuntu:~$


Had to reboot once, like before.  It says **FIXED**?

---

### Post by oldfred on 2013-04-22
Are you having time issues? Maybe that is why it wants to run fsck every time?
 [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

---

### Post by r.stiltskin on 2013-04-22
Two things you can investigate:
1. Do you have Windows and Linux using different time zones?  Probably not, but maybe one is using local time and the other using GMT, and then the hardware clock is being reset each time you boot Windows.

2. How old is your motherboard battery?  If it's old and weak (or dead) your hardware clock will be reset back to "the year one" (e.g. 1/1/1980) each time you turn the computer off.

---

### Post by SUPERFITTER on 2013-04-22
> **oldfred said:**
> Are you having time issues? Maybe that is why it wants to run fsck every time?
 [https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts](https://help.ubuntu.com/community/UbuntuTime#Multiple_Boot_Systems_Time_Conflicts)

Hi oldfred
I tried this: 
[B][SIZE=2]Make Linux use 'Local' time
[/SIZE][/B]

[SIZE=2]To tell your Ubuntu system that the hardware clock is set to 'local' time: [/SIZE]

[LIST=1]
[*][SIZE=2]edit /etc/default/rcS [/SIZE] 
[*][SIZE=2]add or change the following section [/SIZE]
# Set UTC=yes if your hardware clock is set to UTC (GMT) UTC=no

[FONT=arial]It's working now, I will try it for a few days and check to see if it keeps working.

Thank You very much!
[/FONT] 
[/LIST]

---

### Post by SUPERFITTER on 2013-04-22
_[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=195636")_ Hi r.stiltskin

I'm on the same time zone and the computer is just built.

Thank You

---

### Post by SUPERFITTER on 2013-04-24
Hi oldfred
The time is perfect on every boot.  Thank You again for your time.  

How do I mark this thread solved?

---

### Post by BlinkinCat on 2013-04-25
Hi,

Here is how to mark your thread as solved -

[https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads](https://wiki.ubuntu.com/UnansweredPostsTeam/SolvedThreads)

Cheers - :)

---

### Post by SUPERFITTER on 2013-04-26
Solved!

---

