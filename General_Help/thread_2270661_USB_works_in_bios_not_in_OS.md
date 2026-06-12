---
title: "USB works in bios not in OS"
date: 2015-03-24
forum: General Help
---

### Post by grant9 on 2015-03-24
I went from windows 8 (due to to hard drive in water) to Ubuntu 14.04 and now my usb ports don't work unless I'm in bios.

```
[    4.569041] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1[    4.569043] usb usb2: Product: EHCI Host Controller
[    4.569044] usb usb2: Manufacturer: Linux 3.13.0-48-generic ehci_hcd
[    4.569045] usb usb2: SerialNumber: 0000:00:1d.0
[    4.569261] hub 2-0:1.0: USB hub found
[    4.569270] hub 2-0:1.0: 2 ports detected
[    4.569376] ehci-platform: EHCI generic platform driver
[    4.569386] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    4.569387] ohci-pci: OHCI PCI platform driver
[    4.569395] ohci-platform: OHCI generic platform driver
[    4.569399] uhci_hcd: USB Universal Host Controller Interface driver
[    4.569508] xhci_hcd 0000:00:14.0: xHCI Host Controller
[    4.569513] xhci_hcd 0000:00:14.0: new USB bus registered, assigned bus number 3
[    5.475925] tsc: Refined TSC clocksource calibration: 2195.012 MHz
[    7.387596] CPU5: Core temperature above threshold, cpu clock throttled (total events = 1)
[    7.387597] CPU4: Core temperature above threshold, cpu clock throttled (total events = 1)
[    7.387599] CPU2: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.387601] CPU7: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.387602] CPU3: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.387603] CPU6: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.387605] CPU0: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.387606] CPU1: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.387607] CPU4: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.387613] CPU5: Package temperature above threshold, cpu clock throttled (total events = 1)
[    7.388593] CPU5: Core temperature/speed normal
[    7.388593] CPU4: Core temperature/speed normal
[    7.388594] CPU3: Package temperature/speed normal
[    7.388595] CPU0: Package temperature/speed normal
[    7.388595] CPU7: Package temperature/speed normal
[    7.388596] CPU2: Package temperature/speed normal
[    7.388597] CPU1: Package temperature/speed normal
[    7.388597] CPU6: Package temperature/speed normal
[    7.388598] CPU4: Package temperature/speed normal
[    7.388603] CPU5: Package temperature/speed normal
[   29.662478] xhci_hcd 0000:00:14.0: can't setup: -110
[   29.662482] xhci_hcd 0000:00:14.0: USB bus 3 deregistered
[   29.662497] Switched to clocksource tsc
[   29.662586] xhci_hcd 0000:00:14.0: init 0000:00:14.0 fail, -110
[   29.662590] xhci_hcd: probe of 0000:00:14.0 failed with error -110
[   29.662631] i8042: PNP: PS/2 Controller [PNP0303:PS2K,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[   29.666254] i8042: Detected active multiplexing controller, rev 1.1
[   29.669058] serio: i8042 KBD port at 0x60,0x64 irq 1
[   29.669061] serio: i8042 AUX0 port at 0x60,0x64 irq 12
[   29.669079] serio: i8042 AUX1 port at 0x60,0x64 irq 12
[   29.669091] serio: i8042 AUX2 port at 0x60,0x64 irq 12
[   29.669102] serio: i8042 AUX3 port at 0x60,0x64 irq 12
[   29.669262] mousedev: PS/2 mouse device common for all mice
[   29.669543] rtc_cmos 00:05: RTC can wake from S4
[   29.669649] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[   29.669677] rtc_cmos 00:05: alarms up to one month, 242 bytes nvram, hpet irqs
[   29.669726] device-mapper: uevent: version 1.0.3
[   29.669768] device-mapper: ioctl: 4.27.0-ioctl (2013-10-30) initialised: [EMAIL="dm-devel@redhat.com"]dm-devel@redhat.com[/EMAIL]
[   29.669774] ledtrig-cpu: registered to indicate activity on CPUs
[   29.669776] EFI Variables Facility v0.08 2004-May-17
[   29.693429] TCP: cubic registered
[   29.693487] NET: Registered protocol family 10
[   29.693605] NET: Registered protocol family 17
[   29.693613] Key type dns_resolver registered
[   29.693869] Loading compiled-in X.509 certificates
[   29.694601] Loaded X.509 cert 'Magrathea: Glacier signing key: 4eb2de249917cbf39cb85692e54cebade594d680'
[   29.694610] registered taskstats version 1
[   29.696528] Key type trusted registered
[   29.700025] Key type encrypted registered
[   29.700028] AppArmor: AppArmor sha1 policy hashing enabled
[   29.700030] IMA: No TPM chip found, activating TPM-bypass!
[   29.700415] regulator-dummy: disabling
[   29.700499]   Magic number: 7:276:646
[   29.700596] rtc_cmos 00:05: setting system clock to 2015-03-24 18:36:55 UTC (1427222215)
[   29.701504] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[   29.701505] EDD information not available.
[   29.701533] PM: Hibernation image not present or could not be loaded.
[   29.702229] Freeing unused kernel memory: 1336K (ffffffff81d20000 - ffffffff81e6e000)
[   29.702230] Write protecting the kernel read-only data: 12288k
[   29.703853] Freeing unused kernel memory: 796K (ffff880002739000 - ffff880002800000)
[   29.705214] Freeing unused kernel memory: 688K (ffff880002b54000 - ffff880002c00000)
[   29.713727] systemd-udevd[148]: starting version 204
[   29.823112] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[   29.843798] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[   29.843801] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[   29.864916] rtsx_pci 0000:03:00.0: irq 40 for MSI/MSI-X
[   29.864954] rtsx_pci 0000:03:00.0: rtsx_pci_acquire_irq: pcr->msi_en = 1, pci->irq = 40
[   29.866632] ahci 0000:00:1f.2: version 3.0
[   29.866771] ahci 0000:00:1f.2: irq 41 for MSI/MSI-X
[   29.867013] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[   29.867023] r8169 0000:04:00.0: can't disable ASPM; OS doesn't have ASPM control
[   29.867252] r8169 0000:04:00.0: irq 42 for MSI/MSI-X
[   29.867441] r8169 0000:04:00.0 eth0: RTL8168evl/8111evl at 0xffffc90004e5a000, 6c:3b:e5:f1:b4:8e, XID 0c900800 IRQ 42
[   29.867443] r8169 0000:04:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[   29.873102] usb 1-1: new high-speed USB device number 2 using ehci-pci
[   29.881091] ahci 0000:00:1f.2: AHCI 0001.0300 32 slots 6 ports 6 Gbps 0x11 impl RAID mode
[   29.881095] ahci 0000:00:1f.2: flags: 64bit ncq pm led clo pio slum part ems apst 
[   29.889520] scsi0 : ahci
[   29.889583] scsi1 : ahci
[   29.889628] scsi2 : ahci
[   29.889669] scsi3 : ahci
[   29.889708] scsi4 : ahci
[   29.889752] scsi5 : ahci
[   29.889781] ata1: SATA max UDMA/133 abar m2048@0xc0717000 port 0xc0717100 irq 41
[   29.889783] ata2: DUMMY
[   29.889784] ata3: DUMMY
[   29.889784] ata4: DUMMY
[   29.889787] ata5: SATA max UDMA/133 abar m2048@0xc0717000 port 0xc0717300 irq 41
[   29.889787] ata6: DUMMY
[   30.005445] usb 1-1: New USB device found, idVendor=8087, idProduct=0024
[   30.005452] usb 1-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   30.005832] hub 1-1:1.0: USB hub found
[   30.005906] hub 1-1:1.0: 6 ports detected
[   30.042347] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[   30.042355] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[   30.116948] usb 2-1: new high-speed USB device number 2 using ehci-pci
[   30.208789] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[   30.211278] ata5.00: ATAPI: hp       CDDVDW SU-208BB, HH02, max UDMA/100
[   30.213953] ata5.00: configured for UDMA/100
[   30.216781] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[   30.217965] ata1.00: ATA-8: HITACHI HTS545050B9A300, PB4ZC6ZH, max UDMA/100
[   30.217972] ata1.00: 976773168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[   30.219369] ata1.00: configured for UDMA/100
[   30.219633] scsi 0:0:0:0: Direct-Access     ATA      HITACHI HTS54505 PB4Z PQ: 0 ANSI: 5
[   30.219792] sd 0:0:0:0: [sda] 976773168 512-byte logical blocks: (500 GB/465 GiB)
[   30.219837] sd 0:0:0:0: Attached scsi generic sg0 type 0
[   30.219838] sd 0:0:0:0: [sda] Write Protect is off
[   30.219841] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[   30.219860] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[   30.220857] scsi 4:0:0:0: CD-ROM            hp       CDDVDW SU-208BB  HH02 PQ: 0 ANSI: 5
[   30.225046] sr0: scsi3-mmc drive: 62x/62x writer dvd-ram cd/rw xa/form2 cdda tray
[   30.225053] cdrom: Uniform CD-ROM driver Revision: 3.20
[   30.225243] sr 4:0:0:0: Attached scsi CD-ROM sr0
[   30.225337] sr 4:0:0:0: Attached scsi generic sg1 type 5
[   30.244126] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[   30.244134] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[   30.249174] usb 2-1: New USB device found, idVendor=8087, idProduct=0024
[   30.249181] usb 2-1: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[   30.249564] hub 2-1:1.0: USB hub found
[   30.249643] hub 2-1:1.0: 8 ports detected
[   30.320846] usb 1-1.2: new full-speed USB device number 3 using ehci-pci
[   30.414752] usb 1-1.2: New USB device found, idVendor=08ff, idProduct=2665
[   30.414759] usb 1-1.2: New USB device strings: Mfr=0, Product=1, SerialNumber=0
[   30.414762] usb 1-1.2: Product: Fingerprint Sensor
[   30.442753] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[   30.442760] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[   30.484662] usb 1-1.6: new high-speed USB device number 4 using ehci-pci
[   30.581751]  sda: sda1 sda2 sda3
[   30.582298] sd 0:0:0:0: [sda] Attached SCSI disk
[   30.634428] usb 1-1.6: New USB device found, idVendor=064e, idProduct=c33c
[   30.634435] usb 1-1.6: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[   30.634438] usb 1-1.6: Product: HP Truevision HD
[   30.634442] usb 1-1.6: Manufacturer: SuYin
[   30.634444] usb 1-1.6: SerialNumber: HF1019-P62A-OV03-REV0201
[   30.653314] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[   30.653323] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[   30.849760] atkbd serio0: Unknown key released (translated set 2, code 0x7c on isa0060/serio0).
[   30.849768] atkbd serio0: Use 'setkeycodes 7c <keycode>' to make it known.
[   31.731493] psmouse serio4: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00223/0x840300/0x26c00, board id: 2058, fw id: 1199624
[   31.791420] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio4/input/input11
[   36.119196] EXT4-fs (sda2): INFO: recovery required on readonly filesystem
[   36.119198] EXT4-fs (sda2): write access will be enabled during recovery
[   36.147363] random: nonblocking pool is initialized
[   36.724113] EXT4-fs (sda2): orphan cleanup on readonly fs
[   36.844202] EXT4-fs (sda2): 26 orphan inodes deleted
[   36.844205] EXT4-fs (sda2): recovery complete
[   37.084453] EXT4-fs (sda2): mounted filesystem with ordered data mode. Opts: (null)
[   48.114677] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   48.212924] systemd-udevd[339]: starting version 204
[   48.346135] lp: driver loaded but no devices found
[   48.349887] ppdev: user-space parallel port driver
[   48.365519] Initializing HPQ6001 module
[   48.365585] input: HP Wireless hotkeys as /devices/virtual/input/input12
[   48.365844] video: module verification failed: signature and/or  required key missing - tainting kernel
[   48.390476] wmi: Mapper loaded
[   48.393980] [drm] Initialized drm 1.1.0 20060810
[   48.394675] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   48.396619] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[   48.406133] ACPI Warning: 0x0000000000000428-0x000000000000042f SystemIO conflicts with Region \PMIO 1 (20131115/utaddress-251)
[   48.406140] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   48.406144] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   48.406148] ACPI Warning: 0x0000000000000530-0x000000000000053f SystemIO conflicts with Region \_SB_.PCI0.LPCB.EC0_.IOS0 2 (20131115/utaddress-251)
[   48.406152] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   48.406153] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \GPIO 1 (20131115/utaddress-251)
[   48.406156] ACPI Warning: 0x0000000000000500-0x000000000000052f SystemIO conflicts with Region \_SB_.PCI0.LPCB.EC0_.IOS0 2 (20131115/utaddress-251)
[   48.406160] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   48.406161] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   48.407653] [drm] Memory usable by graphics device = 2048M
[   48.407657] checking generic (b0000000 410000) vs hw (b0000000 10000000)
[   48.407658] fb: conflicting fb hw usage inteldrmfb vs EFI VGA - removing generic driver
[   48.407676] Console: switching to colour dummy device 80x25
[   48.408536] cfg80211: Calling CRDA to update world regulatory domain
[   48.430658] ieee80211 phy0: rt2x00_set_rt: Info - RT chipset 5390, rev 1502 detected
[   48.434836] ieee80211 phy0: rt2x00_set_rf: Info - RF chipset 5390 detected
[   48.439057] ieee80211 phy0: Selected rate control algorithm 'minstrel_ht'
[   48.460684] i915 0000:00:02.0: irq 44 for MSI/MSI-X
[   48.460695] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   48.460697] [drm] Driver supports precise vblank timestamp query.
[   48.460801] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   48.502203] fbcon: inteldrmfb (fb0) is primary device
[   48.629044] intel_rapl: domain uncore energy ctr 15558:15558 not working, skip
[   48.724778] type=1400 audit(1427222234.541:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=478 comm="apparmor_parser"
[   48.724782] type=1400 audit(1427222234.541:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=478 comm="apparmor_parser"
[   48.724784] type=1400 audit(1427222234.541:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=478 comm="apparmor_parser"
[   48.724792] type=1400 audit(1427222234.541:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=469 comm="apparmor_parser"
[   48.724796] type=1400 audit(1427222234.541:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=469 comm="apparmor_parser"
[   48.724798] type=1400 audit(1427222234.541:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=469 comm="apparmor_parser"
[   48.725103] type=1400 audit(1427222234.541:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=478 comm="apparmor_parser"
[   48.725106] type=1400 audit(1427222234.541:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=478 comm="apparmor_parser"
[   48.725117] type=1400 audit(1427222234.541:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=469 comm="apparmor_parser"
[   48.725120] type=1400 audit(1427222234.541:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=469 comm="apparmor_parser"
[   48.823464] [drm:cpt_set_fifo_underrun_reporting] *ERROR* uncleared pch fifo underrun on pch transcoder A
[   48.823465] [drm:cpt_serr_int_handler] *ERROR* PCH transcoder A FIFO underrun
[   48.900369] input: HP WMI hotkeys as /devices/virtual/input/input13
[   49.153969] cfg80211: World regulatory domain updated:
[   49.153970] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   49.153971] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.153972] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.153973] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   49.153974] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.153975] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   49.260321] Console: switching to colour frame buffer device 170x48
[   49.262304] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   49.262305] i915 0000:00:02.0: registered panic notifier
[   49.268231] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   49.270300] acpi device:3f: registered as cooling_device9
[   49.270380] input: Video Bus as /devices/LNXSYSTM:00/device:00/PNP0A08:00/LNXVIDEO:00/input/input14
[   49.271873] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   49.272067] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[   49.282639] mute LED gpio 1 polarity 0
[   49.282824] autoconfig: line_outs=1 (0xd/0x0/0x0/0x0/0x0) type:speaker
[   49.282826]    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   49.282827]    hp_outs=1 (0xb/0x0/0x0/0x0/0x0)
[   49.282827]    mono: mono_out=0x0
[   49.282828]    inputs:
[   49.282829]      Internal Mic=0x11
[   49.282830]      Mic=0xa
[   49.304842] input: HDA Intel PCH HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input17
[   49.304917] input: HDA Intel PCH Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input16
[   49.304981] input: HDA Intel PCH Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   49.455501] Linux video capture interface: v2.00
[   49.460089] uvcvideo: Found UVC 1.00 device HP Truevision HD (064e:c33c)
[   49.468711] input: HP Truevision HD as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.6/1-1.6:1.0/input/input18
[   49.468771] usbcore: registered new interface driver uvcvideo
[   49.468773] USB Video Class driver (1.1.1)
[   49.783660] [drm] Enabling RC6 states: RC6 on, RC6p on, RC6pp off
[   53.426043] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   53.677894] init: failsafe main process (763) killed by TERM signal
[   54.059186] audit_printk_skb: 6 callbacks suppressed
[   54.059189] type=1400 audit(1427222239.881:14): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=886 comm="apparmor_parser"
[   54.059194] type=1400 audit(1427222239.881:15): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=886 comm="apparmor_parser"
[   54.059197] type=1400 audit(1427222239.881:16): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=886 comm="apparmor_parser"
[   54.059517] type=1400 audit(1427222239.881:17): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=886 comm="apparmor_parser"
[   54.059520] type=1400 audit(1427222239.881:18): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=886 comm="apparmor_parser"
[   54.059686] type=1400 audit(1427222239.881:19): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=886 comm="apparmor_parser"
[   54.060053] type=1400 audit(1427222239.881:20): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=891 comm="apparmor_parser"
[   54.060058] type=1400 audit(1427222239.881:21): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=891 comm="apparmor_parser"
[   54.060083] type=1400 audit(1427222239.881:22): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cups-browsed" pid=890 comm="apparmor_parser"
[   54.060390] type=1400 audit(1427222239.881:23): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=885 comm="apparmor_parser"
[   54.214131] Bluetooth: Core ver 2.17
[   54.214144] NET: Registered protocol family 31
[   54.214145] Bluetooth: HCI device and connection manager initialized
[   54.214152] Bluetooth: HCI socket layer initialized
[   54.214153] Bluetooth: L2CAP socket layer initialized
[   54.214156] Bluetooth: SCO socket layer initialized
[   54.216280] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   54.216282] Bluetooth: BNEP filters: protocol multicast
[   54.216288] Bluetooth: BNEP socket layer initialized
[   54.217531] Bluetooth: RFCOMM TTY layer initialized
[   54.217538] Bluetooth: RFCOMM socket layer initialized
[   54.217541] Bluetooth: RFCOMM ver 1.11
[   54.728171] init: cups main process (932) killed by HUP signal
[   54.728179] init: cups main process ended, respawning
[   56.864261] ieee80211 phy0: rt2x00lib_request_firmware: Info - Loading firmware file 'rt2860.bin'
[   57.046352] ieee80211 phy0: rt2x00lib_request_firmware: Info - Firmware detected - version: 0.34
[   57.171528] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.171776] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   57.464878] r8169 0000:04:00.0 eth0: link down
[   57.464922] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.465259] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   57.610098] vboxdrv: Found 8 processor cores.
[   57.610356] vboxdrv: fAsync=0 offMin=0x16c offMax=0x1089
[   57.610418] vboxdrv: TSC mode is 'synchronous', kernel timer mode is 'normal'.
[   57.610420] vboxdrv: Successfully loaded version 4.3.10_Ubuntu (interface 0x001a0007).
[   57.620426] vboxpci: IOMMU not found (not registered)
[   57.878696] init: samba-ad-dc main process (1160) terminated with status 1
[   58.638736] wlan0: authenticate with 20:3a:07:98:c5:c1
[   58.650093] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 1/3)
[   58.853269] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 2/3)
[   59.057032] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 3/3)
[   59.260818] wlan0: authentication with 20:3a:07:98:c5:c1 timed out
[   59.441377] wlan0: authenticate with f0:29:29:c2:9c:c1
[   59.456980] wlan0: direct probe to f0:29:29:c2:9c:c1 (try 1/3)
[   59.660425] wlan0: direct probe to f0:29:29:c2:9c:c1 (try 2/3)
[   59.864185] wlan0: direct probe to f0:29:29:c2:9c:c1 (try 3/3)
[   60.067912] wlan0: authentication with f0:29:29:c2:9c:c1 timed out
[   61.233162] init: plymouth-upstart-bridge main process ended, respawning
[   61.243033] wlan0: authenticate with 20:3a:07:98:c5:c1
[   61.243876] init: plymouth-upstart-bridge main process ended, respawning
[   61.259057] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 1/3)
[   61.462388] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 2/3)
[   61.666213] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 3/3)
[   61.869980] wlan0: authentication with 20:3a:07:98:c5:c1 timed out
[   62.949365] wlan0: authenticate with f0:29:29:c2:9c:c1
[   62.965126] wlan0: direct probe to f0:29:29:c2:9c:c1 (try 1/3)
[   63.168495] wlan0: direct probe to f0:29:29:c2:9c:c1 (try 2/3)
[   63.372297] wlan0: direct probe to f0:29:29:c2:9c:c1 (try 3/3)
[   63.576062] wlan0: authentication with f0:29:29:c2:9c:c1 timed out
[   65.646335] wlan0: authenticate with 20:3a:07:98:c5:c1
[   65.662102] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 1/3)
[   65.865647] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 2/3)
[   66.069317] wlan0: direct probe to 20:3a:07:98:c5:c1 (try 3/3)
[   66.273093] wlan0: authentication with 20:3a:07:98:c5:c1 timed out
[   84.267335] audit_printk_skb: 132 callbacks suppressed
[   84.267338] type=1400 audit(1427222270.121:68): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1709 comm="apparmor_parser"
[   84.267343] type=1400 audit(1427222270.121:69): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1709 comm="apparmor_parser"
[   84.267663] type=1400 audit(1427222270.121:70): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1709 comm="apparmor_parser"
[  115.954961] wlan0: authenticate with 04:da:d2:1f:29:21
[  115.970912] wlan0: direct probe to 04:da:d2:1f:29:21 (try 1/3)
[  116.174240] wlan0: direct probe to 04:da:d2:1f:29:21 (try 2/3)
[  116.377995] wlan0: direct probe to 04:da:d2:1f:29:21 (try 3/3)
[  116.581905] wlan0: authentication with 04:da:d2:1f:29:21 timed out
[  127.650528] wlan0: authenticate with 04:da:d2:1f:29:21
[  127.666129] wlan0: direct probe to 04:da:d2:1f:29:21 (try 1/3)
[  127.869409] wlan0: direct probe to 04:da:d2:1f:29:21 (try 2/3)
[  128.073184] wlan0: direct probe to 04:da:d2:1f:29:21 (try 3/3)
[  128.276981] wlan0: authentication with 04:da:d2:1f:29:21 timed out
[  170.844512] wlan0: authenticate with 20:3a:07:98:c5:c3
[  170.850402] wlan0: direct probe to 20:3a:07:98:c5:c3 (try 1/3)
[  171.053952] wlan0: direct probe to 20:3a:07:98:c5:c3 (try 2/3)
[  171.257715] wlan0: direct probe to 20:3a:07:98:c5:c3 (try 3/3)
[  171.461475] wlan0: authentication with 20:3a:07:98:c5:c3 timed out
[  181.602787] wlan0: authenticate with f0:29:29:c2:9c:c3
[  181.622637] wlan0: direct probe to f0:29:29:c2:9c:c3 (try 1/3)
[  181.826171] wlan0: direct probe to f0:29:29:c2:9c:c3 (try 2/3)
[  182.029826] wlan0: direct probe to f0:29:29:c2:9c:c3 (try 3/3)
[  182.233666] wlan0: authentication with f0:29:29:c2:9c:c3 timed out
[  218.014703] wlan0: authenticate with 04:da:d2:1f:29:23
[  218.030751] wlan0: direct probe to 04:da:d2:1f:29:23 (try 1/3)
[  218.234025] wlan0: direct probe to 04:da:d2:1f:29:23 (try 2/3)
[  218.437825] wlan0: direct probe to 04:da:d2:1f:29:23 (try 3/3)
[  218.641592] wlan0: authentication with 04:da:d2:1f:29:23 timed out
[  241.756714] wlan0: authenticate with 58:6d:8f:6d:b3:14
[  241.772404] wlan0: send auth to 58:6d:8f:6d:b3:14 (try 1/3)
[  241.774194] wlan0: authenticated
[  241.776160] wlan0: associate with 58:6d:8f:6d:b3:14 (try 1/3)
[  241.780528] wlan0: RX AssocResp from 58:6d:8f:6d:b3:14 (capab=0x401 status=0 aid=2)
[  241.780624] wlan0: associated
[  241.780633] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[  241.781190] wlan0: deauthenticating from 58:6d:8f:6d:b3:14 by local choice (reason=2)
[  241.804748] wlan0: authenticate with 58:6d:8f:6d:b3:14
[  241.812624] wlan0: send auth to 58:6d:8f:6d:b3:14 (try 1/3)
[  241.812694] cfg80211: Calling CRDA to update world regulatory domain
[  241.814962] wlan0: authenticated
[  241.816122] wlan0: associate with 58:6d:8f:6d:b3:14 (try 1/3)
[  241.816980] cfg80211: World regulatory domain updated:
[  241.816985] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  241.816989] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  241.816992] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  241.816995] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  241.816998] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  241.817001] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  241.819157] wlan0: RX AssocResp from 58:6d:8f:6d:b3:14 (capab=0x401 status=0 aid=2)
[  241.819265] wlan0: associated
[  251.813144] wlan0: deauthenticating from 58:6d:8f:6d:b3:14 by local choice (reason=3)
[  251.838261] cfg80211: Calling CRDA to update world regulatory domain
[  251.843396] cfg80211: World regulatory domain updated:
[  251.843402] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[  251.843405] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  251.843408] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  251.843410] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[  251.843413] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  251.843415] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[  252.988647] wlan0: authenticate with 58:6d:8f:6d:b3:14
[  253.004356] wlan0: send auth to 58:6d:8f:6d:b3:14 (try 1/3)
[  253.005956] wlan0: authenticated
[  253.007846] wlan0: associate with 58:6d:8f:6d:b3:14 (try 1/3)
[  253.010788] wlan0: RX AssocResp from 58:6d:8f:6d:b3:14 (capab=0x401 status=0 aid=2)
[  253.010895] wlan0: associated
[  299.523478] mce: [Hardware Error]: Machine check events logged
```

---

### Post by oldfred on 2015-03-24
Please use code tags or # in advanced editor not quotes for longer text or code.

You seem to have a very long boot with several large gaps, each large gap is an issue.

What brand, model system?
Are you booting in UEFI or BIOS boot mode?

Some systems require settings in UEFI to enable ports. Some also then require passwords to allow you to change settings (never lose that password if required). 
And some systems/motherboard have other seemingly unrelated settings that may be important.

---

### Post by grant9 on 2015-03-25
> **oldfred said:**
> Please use code tags or # in advanced editor not quotes for longer text or code.

You seem to have a very long boot with several large gaps, each large gap is an issue.

What brand, model system?
Are you booting in UEFI or BIOS boot mode?

Some systems require settings in UEFI to enable ports. Some also then require passwords to allow you to change settings (never lose that password if required). 
And some systems/motherboard have other seemingly unrelated settings that may be important.

Intel® Core™ i7-3632QM CPU @ 2.20GHz × 8 

64-bit

Hp envy m4

no UEFI mode

---

### Post by oldfred on 2015-03-25
Do not know that model, but all HP do not dual boot with UEFI without work arounds.
The i7 would be UEFI but have CSM mode, so your installs can be either. How you boot installer is how it installs.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

These may be similar?

 Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

---

### Post by grant9 on 2015-03-25
> **oldfred said:**
> Do not know that model, but all HP do not dual boot with UEFI without work arounds.
The i7 would be UEFI but have CSM mode, so your installs can be either. How you boot installer is how it installs.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

These may be similar?

 Envy M6 Change boot order sudo efibootmgr-o 2,1 post #23
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
HP Envy M6
[http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working](http://askubuntu.com/questions/346257/install-alongside-windows-8-is-not-working)
HP Envy - Legacy boot seems to mean either UEFI or Legacy depending on which is found to boot from
[http://ubuntuforums.org/showthread.php?t=2167063](http://ubuntuforums.org/showthread.php?t=2167063)
Installing Ubuntu on HP Envy-6  Details of what worked post #11
[http://ubuntuforums.org/showthread.php?t=2123975](http://ubuntuforums.org/showthread.php?t=2123975)

Sorry, I actually do have a UEFI mode, but I switched to both modes and nothing works. As soon as i leave bios setup and boot into Ubuntu, the lights on my USB devices go dead. I only have Ubuntu as my OS currently.

---

### Post by oldfred on 2015-03-25
Some systems require you to specifically enable USB ports. 
That must an UEFI secuity issue to protect system from using USB ports unless specifically allowed.

---

### Post by grant9 on 2015-03-25
> **oldfred said:**
> Some systems require you to specifically enable USB ports. 
That must an UEFI secuity issue to protect system from using USB ports unless specifically allowed.

I'm using legacy boot mode right now not UEFI, I see an option for enable usb 3.0, but it has no effect enabled or disabled.

I'm not trying to dual boot or boot Ubuntu from a usb.

---

