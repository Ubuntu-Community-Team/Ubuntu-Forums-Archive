---
title: "Help with Harddrive Mouting"
date: 2012-11-29
forum: General Help
---

### Post by haseotod1 on 2012-11-29
Hi Guys, 

please be nice im new to this website and ubuntu :P

I have been trying for days to work out how to static mount internal hard drives that have. Just for info purposes im running XBMC on a minimal install of ubuntu. 

I have reached as far as edited the fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=26181423-4202-4dd6-b784-60ac3e8b846e /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=92c769af-f500-474e-984b-898fd642e31d none            swap    sw           $
UUID=4AF454CFF454BF3F /media/Disk1 ntfs-3g  defaults,locale=en_US.UTF-8
UUID=6C642DE3642DB0AE /media/Disk2 ntfs-3g defaults,locale=en_US.UTF-8

```

When the pc boots and hits the XBMC splash screen i get an error that states there was an issue with mounting to /media/Disk1 

is there any obvious mistakes in what i have done?

Thanks for the help

---

### Post by for.i.am.root on 2012-11-29
Did you verify the UUID is correct? Please post the results of:
```

ls -l /dev/disk/by-uuid

```

---

### Post by Elfy on 2012-11-29
Did you make the folders for it to mount to?

Is that all the error states - > there was an issue?

---

### Post by haseotod1 on 2012-11-29
here are the results
```
total 0
lrwxrwxrwx 1 root root 10 Nov 29 18:33 26181423-4202-4dd6-b784-60ac3e8b846e -> ../../sda1
lrwxrwxrwx 1 root root 10 Nov 29 18:33 4AF454CFF454BF3F -> ../../sdb1
lrwxrwxrwx 1 root root 10 Nov 29 18:33 6C642DE3642DB0AE -> ../../sdd1
lrwxrwxrwx 1 root root 10 Nov 29 18:33 70A01293A0125FC0 -> ../../sdc1
lrwxrwxrwx 1 root root 10 Nov 29 18:33 92c769af-f500-474e-984b-898fd642e31d -> ../../sda5

```

and yes i have created the directories.

```
xbmc@HTPPC:~$ cd /media/
xbmc@HTPPC:/media$ dir
Disk1  Disk2  New_Volume  usbhd-sdb1  usbhd-sdc1  usbhd-sdd1

```

---

### Post by for.i.am.root on 2012-11-29
Try running dmesg and see if you can get us the error that you are getting:

```

dmesg

```

Try to post just the relevant section and/or use the CODE tags.

---

### Post by haseotod1 on 2012-11-29
Not sure what to look for :/

```
[    0.606551] usb usb8: SerialNumber: 0000:00:1d.2
[    0.606608] hub 8-0:1.0: USB hub found
[    0.606611] hub 8-0:1.0: 2 ports detected
[    0.606671] xhci_hcd 0000:01:00.0: xHCI Host Controller
[    0.606675] xhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 9
[    0.711167] xhci_hcd 0000:01:00.0: irq 16, io mem 0xfbdfe000
[    0.711201] xhci_hcd 0000:01:00.0: irq 42 for MSI/MSI-X
[    0.711206] xhci_hcd 0000:01:00.0: irq 43 for MSI/MSI-X
[    0.711210] xhci_hcd 0000:01:00.0: irq 44 for MSI/MSI-X
[    0.711215] xhci_hcd 0000:01:00.0: irq 45 for MSI/MSI-X
[    0.711220] xhci_hcd 0000:01:00.0: irq 46 for MSI/MSI-X
[    0.711281] usb usb9: New USB device found, idVendor=1d6b, idProduct=0002
[    0.711282] usb usb9: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.711284] usb usb9: Product: xHCI Host Controller
[    0.711285] usb usb9: Manufacturer: Linux 3.5.0-18-generic xhci_hcd
[    0.711286] usb usb9: SerialNumber: 0000:01:00.0
[    0.711331] xHCI xhci_add_endpoint called for root hub
[    0.711332] xHCI xhci_check_bandwidth called for root hub
[    0.711347] hub 9-0:1.0: USB hub found
[    0.711352] hub 9-0:1.0: 2 ports detected
[    0.711386] xhci_hcd 0000:01:00.0: xHCI Host Controller
[    0.711389] xhci_hcd 0000:01:00.0: new USB bus registered, assigned bus number 10
[    0.714474] usb usb10: New USB device found, idVendor=1d6b, idProduct=0003
[    0.714475] usb usb10: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    0.714477] usb usb10: Product: xHCI Host Controller
[    0.714478] usb usb10: Manufacturer: Linux 3.5.0-18-generic xhci_hcd
[    0.714479] usb usb10: SerialNumber: 0000:01:00.0
[    0.714525] xHCI xhci_add_endpoint called for root hub
[    0.714526] xHCI xhci_check_bandwidth called for root hub
[    0.714540] hub 10-0:1.0: USB hub found
[    0.714545] hub 10-0:1.0: 2 ports detected
[    0.876453] isapnp: No Plug & Play device found
[    0.876933] usbcore: registered new interface driver libusual
[    0.876962] i8042: PNP: No PS/2 controller found. Probing ports directly.
[    0.910048] i8042: Failed to disable AUX port, but continuing anyway... Is this a SiS?
[    0.910049] i8042: If AUX port is really absent please use the 'i8042.noaux' option
[    1.064307] ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.123691] ata1.00: ATA-8: FM-25S2S-40GBP2, 2.1, max UDMA/133
[    1.123696] ata1.00: 78161328 sectors, multi 1: LBA48 NCQ (depth 31/32), AA
[    1.160120] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.160155] usb 10-1: new SuperSpeed USB device number 2 using xhci_hcd
[    1.160207] mousedev: PS/2 mouse device common for all mice
[    1.160303] rtc_cmos 00:04: RTC can wake from S4
[    1.160404] rtc_cmos 00:04: rtc core: registered rtc_cmos as rtc0
[    1.160427] rtc0: alarms up to one month, 242 bytes nvram, hpet irqs
[    1.160464] device-mapper: uevent: version 1.0.3
[    1.160507] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    1.160526] EISA: Probing bus 0 at eisa.0
[    1.160528] EISA: Cannot allocate resource for mainboard
[    1.160529] Cannot allocate resource for EISA slot 1
[    1.160530] Cannot allocate resource for EISA slot 2
[    1.160531] Cannot allocate resource for EISA slot 3
[    1.160531] Cannot allocate resource for EISA slot 4
[    1.160532] Cannot allocate resource for EISA slot 5
[    1.160533] Cannot allocate resource for EISA slot 6
[    1.160534] Cannot allocate resource for EISA slot 7
[    1.160535] Cannot allocate resource for EISA slot 8
[    1.160536] EISA: Detected 0 cards.
[    1.160586] cpuidle: using governor ladder
[    1.160649] cpuidle: using governor menu
[    1.160651] EFI Variables Facility v0.08 2004-May-17
[    1.160784] ashmem: initialized
[    1.160873] TCP: cubic registered
[    1.160940] NET: Registered protocol family 10
[    1.161076] NET: Registered protocol family 17
[    1.161092] Key type dns_resolver registered
[    1.161155] Using IPI No-Shortcut mode
[    1.161225] PM: Hibernation image not present or could not be loaded.
[    1.161234] registered taskstats version 1
[    1.163329] Key type trusted registered
[    1.165287] Key type encrypted registered
[    1.167532]   Magic number: 4:598:545
[    1.167557] tty ttyS21: hash matches
[    1.167669] rtc_cmos 00:04: setting system clock to 2012-11-29 18:33:00 UTC (1354213980)
[    1.168448] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.168450] EDD information not available.
[    1.173621] ata1.00: configured for UDMA/133
[    1.173899] scsi 0:0:0:0: Direct-Access     ATA      FM-25S2S-40GBP2  2.1  PQ: 0 ANSI: 5
[    1.174068] sd 0:0:0:0: [sda] 78161328 512-byte logical blocks: (40.0 GB/37.2 GiB)
[    1.174102] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.174271] sd 0:0:0:0: [sda] Write Protect is off
[    1.174276] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.174352] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.175432]  sda: sda1 sda2 < sda5 >
[    1.176258] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.177500] usb 10-1: Parent hub missing LPM exit latency info.  Power management will be impacted.
[    1.179753] usb 10-1: New USB device found, idVendor=1058, idProduct=1140
[    1.179759] usb 10-1: New USB device strings: Mfr=1, Product=2, SerialNumber=5
[    1.179763] usb 10-1: Product: My Book 1140
[    1.179766] usb 10-1: Manufacturer: Western Digital
[    1.179770] usb 10-1: SerialNumber: 574D415A4137383231333532
[    1.182480] Initializing USB Mass Storage driver...
[    1.182662] scsi6 : usb-storage 10-1:1.0
[    1.182745] usbcore: registered new interface driver usb-storage
[    1.182747] USB Mass Storage support registered.
[    1.299696] Refined TSC clocksource calibration: 3066.629 MHz.
[    1.299702] Switching to clocksource tsc
[    1.419364] usb 6-1: new full-speed USB device number 2 using uhci_hcd
[    1.595580] usb 6-1: New USB device found, idVendor=046d, idProduct=0b06
[    1.595585] usb 6-1: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    1.595588] usb 6-1: Product: Logitech BT Mini-Receiver
[    1.595591] usb 6-1: Manufacturer: Logitech
[    1.597615] hub 6-1:1.0: USB hub found
[    1.599590] hub 6-1:1.0: 3 ports detected
[    1.662714] ata2: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    1.669299] ata2.00: ATA-7: SAMSUNG HD103UI, 1AA01113, max UDMA7
[    1.669304] ata2.00: 1953525168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    1.676004] ata2.00: configured for UDMA/133
[    1.676204] scsi 1:0:0:0: Direct-Access     ATA      SAMSUNG HD103UI  1AA0 PQ: 0 ANSI: 5
[    1.676375] sd 1:0:0:0: Attached scsi generic sg1 type 0
[    1.676397] sd 1:0:0:0: [sdb] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    1.676635] sd 1:0:0:0: [sdb] Write Protect is off
[    1.676641] sd 1:0:0:0: [sdb] Mode Sense: 00 3a 00 00
[    1.676791] sd 1:0:0:0: [sdb] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.681033]  sdb: sdb1
[    1.681598] sd 1:0:0:0: [sdb] Attached SCSI disk
[    1.879806] usb 6-1.2: new full-speed USB device number 3 using uhci_hcd
[    2.026393] usb 6-1.2: New USB device found, idVendor=046d, idProduct=c71b
[    2.026398] usb 6-1.2: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.026401] usb 6-1.2: Product: Logitech BT Mini-Receiver
[    2.026404] usb 6-1.2: Manufacturer: Logitech
[    2.026407] usb 6-1.2: SerialNumber: 001F2010277C
[    2.103204] usb 6-1.3: new full-speed USB device number 4 using uhci_hcd
[    2.165336] ata3: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.171614] ata3.00: ATA-8: SAMSUNG HD204UI, 1AQ10001, max UDMA/133
[    2.171619] ata3.00: 3907029168 sectors, multi 0: LBA48 NCQ (depth 31/32), AA
[    2.177915] ata3.00: configured for UDMA/133
[    2.177970] scsi: waiting for bus probes to complete ...
[    2.178195] scsi 6:0:0:0: Direct-Access     WD       My Book 1140     1019 PQ: 0 ANSI: 6
[    2.178584] scsi 6:0:0:1: Enclosure         WD       SES Device       1019 PQ: 0 ANSI: 6
[    2.180063] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    2.180251] sd 6:0:0:0: [sdc] 3906963456 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.180253] scsi 6:0:0:1: Attached scsi generic sg3 type 13
[    2.180881] sd 6:0:0:0: [sdc] Write Protect is off
[    2.180887] sd 6:0:0:0: [sdc] Mode Sense: 47 00 10 08
[    2.181674] sd 6:0:0:0: [sdc] No Caching mode page present
[    2.181679] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.183589] sd 6:0:0:0: [sdc] No Caching mode page present
[    2.183593] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.183907]  sdc: sdc1
[    2.185959] sd 6:0:0:0: [sdc] No Caching mode page present
[    2.185963] sd 6:0:0:0: [sdc] Assuming drive cache: write through
[    2.185967] sd 6:0:0:0: [sdc] Attached SCSI disk
[    2.186244] scsi 2:0:0:0: Direct-Access     ATA      SAMSUNG HD204UI  1AQ1 PQ: 0 ANSI: 5
[    2.186444] sd 2:0:0:0: [sdd] 3907029168 512-byte logical blocks: (2.00 TB/1.81 TiB)
[    2.186446] sd 2:0:0:0: Attached scsi generic sg4 type 0
[    2.186680] sd 2:0:0:0: [sdd] Write Protect is off
[    2.186686] sd 2:0:0:0: [sdd] Mode Sense: 00 3a 00 00
[    2.186787] sd 2:0:0:0: [sdd] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.199603]  sdd: sdd1
[    2.199784] sd 2:0:0:0: [sdd] Attached SCSI disk
[    2.250790] usb 6-1.3: New USB device found, idVendor=046d, idProduct=c71c
[    2.250796] usb 6-1.3: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.250801] usb 6-1.3: Product: Logitech BT Mini-Receiver
[    2.250804] usb 6-1.3: Manufacturer: Logitech
[    2.250808] usb 6-1.3: SerialNumber: 001F2010277C
[    2.675888] ata4: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.677529] ata4.00: ATAPI: Optiarc DVD RW AD-7240S, 1.03, max UDMA/100
[    2.679578] ata4.00: configured for UDMA/100
[    2.681561] scsi 3:0:0:0: CD-ROM            Optiarc  DVD RW AD-7240S  1.03 PQ: 0 ANSI: 5
[    2.683856] sr0: scsi3-mmc drive: 48x/48x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.683860] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.684089] sr 3:0:0:0: Attached scsi CD-ROM sr0
[    2.684202] sr 3:0:0:0: Attached scsi generic sg5 type 5
[    3.003026] ata5: SATA link down (SStatus 0 SControl 300)
[    3.322144] ata6: SATA link down (SStatus 0 SControl 300)
[    3.322346] Freeing unused kernel memory: 756k freed
[    3.322606] Write protecting the kernel text: 5964k
[    3.322655] Write protecting the kernel read-only data: 2424k
[    3.322656] NX-protecting the kernel data: 4276k
[    3.340824] udevd[121]: starting version 175
[    3.360811] [drm] Initialized drm 1.1.0 20060810
[    3.365562] i915 0000:00:02.0: setting latency timer to 64
[    3.366354] i915 0000:00:02.0: irq 47 for MSI/MSI-X
[    3.366364] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    3.366365] [drm] Driver supports precise vblank timestamp query.
[    3.366408] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    3.371068] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[    3.371164] r8169 0000:03:00.0: irq 48 for MSI/MSI-X
[    3.371335] r8169 0000:03:00.0: eth0: RTL8168e/8111e at 0xf8422000, 1c:6f:65:b6:cb:3b, XID 0c200000 IRQ 48
[    3.371338] r8169 0000:03:00.0: eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[    3.387693] usbcore: registered new interface driver usbhid
[    3.387697] usbhid: USB HID core driver
[    3.403141] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.2/6-1.2:1.0/input/input2
[    3.403214] hid-generic 0003:046D:C71B.0001: input,hidraw0: USB HID v1.11 Keyboard [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.2/input0
[    3.403461] input: Logitech Logitech BT Mini-Receiver as /devices/pci0000:00/0000:00:1d.0/usb6/6-1/6-1.3/6-1.3:1.0/input/input3
[    3.403573] hid-generic 0003:046D:C71C.0002: input,hiddev0,hidraw1: USB HID v1.11 Mouse [Logitech Logitech BT Mini-Receiver] on usb-0000:00:1d.0-1.3/input0
[    3.421001] ses 6:0:0:1: Attached Enclosure device
[    4.178354] fbcon: inteldrmfb (fb0) is primary device
[    4.178463] Console: switching to colour frame buffer device 240x67
[    4.178514] fb0: inteldrmfb frame buffer device
[    4.178515] drm: registered panic notifier
[    4.178556] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    4.184073] uvesafb: Intel Corporation, Intel(R)Ironlake Desktop Graphics Controller, Hardware Version 0.0, OEM: Intel(R)Ironlake Desktop Graphics Chipset Accelerated VGA BIOS, VBE v3.0
[    4.206407] uvesafb: NX protection is actively.We have better not to use the PMI.
[    4.363897] uvesafb: VBIOS/hardware supports DDC2 transfers
[    4.376531] uvesafb: monitor limits: vf = 61 Hz, hf = 68 kHz, clk = 150 MHz
[    4.376903] uvesafb: scrolling: redraw
[    4.376916] mtrr: type mismatch for e0000000,1000000 old: write-back new: write-combining
[    4.376921] mtrr: type mismatch for e0000000,800000 old: write-back new: write-combining
[    4.376925] mtrr: type mismatch for e0000000,400000 old: write-back new: write-combining
[    4.376928] mtrr: type mismatch for e0000000,200000 old: write-back new: write-combining
[    4.376932] mtrr: type mismatch for e0000000,100000 old: write-back new: write-combining
[    4.376935] mtrr: type mismatch for e0000000,80000 old: write-back new: write-combining
[    4.376939] mtrr: type mismatch for e0000000,40000 old: write-back new: write-combining
[    4.376943] mtrr: type mismatch for e0000000,20000 old: write-back new: write-combining
[    4.376946] mtrr: type mismatch for e0000000,10000 old: write-back new: write-combining
[    4.376950] mtrr: type mismatch for e0000000,8000 old: write-back new: write-combining
[    4.376953] mtrr: type mismatch for e0000000,4000 old: write-back new: write-combining
[    4.376957] mtrr: type mismatch for e0000000,2000 old: write-back new: write-combining
[    4.376960] mtrr: type mismatch for e0000000,1000 old: write-back new: write-combining
[    4.377567] uvesafb: framebuffer at 0xe0000000, mapped to 0xf9580000, using 10240k, total 65472k
[    4.377572] fb1: VESA VGA frame buffer device
[    5.544256] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    5.713638] Adding 3921916k swap on /dev/sda5.  Priority:-1 extents:1 across:3921916k SS
[    5.718745] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    5.726370] udevd[402]: starting version 175
[    5.736574] it87: Found IT8720F chip at 0x290, revision 8
[    5.736582] it87: VID is disabled (pins used for GPIO)
[    5.736591] it87: Routing internal VCCH to in7
[    5.736594] it87: Beeping is supported
[    5.756921] mei 0000:00:16.0: setting latency timer to 64
[    5.756987] mei 0000:00:16.0: irq 49 for MSI/MSI-X
[    5.794733] ACPI Warning: 0x00000460-0x0000047f SystemIO conflicts with Region \TCOI 1 (20120320/utaddress-251)
[    5.794740] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.794742] lpc_ich: Resource conflict(s) found affecting iTCO_wdt
[    5.794745] ACPI Warning: 0x00000428-0x0000042f SystemIO conflicts with Region \GP2C 1 (20120320/utaddress-251)
[    5.794748] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[    5.794816] lpc_ich: Resource conflict(s) found affecting gpio_ich
[    5.825038] snd_hda_intel 0000:00:1b.0: irq 50 for MSI/MSI-X
[    5.838791] microcode: CPU0 sig=0x20655, pf=0x2, revision=0x2
[    5.902461] gpio_ich: GPIO from 180 to 255 on gpio_ich
[    5.904253] input: HDA Intel HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:1b.0/sound/card0/input4
[    5.904566] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input5
[    5.904701] input: HDA Intel Front Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input6
[    5.904846] input: HDA Intel Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input7
[    5.904973] input: HDA Intel Front Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[    5.905157] input: HDA Intel Line Out Side as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[    5.905665] input: HDA Intel Line Out CLFE as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[    5.906289] input: HDA Intel Line Out Surround as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[    5.906415] input: HDA Intel Line Out Front as /devices/pci0000:00/0000:00:1b.0/sound/card0/input12
[    5.925953] microcode: CPU1 sig=0x20655, pf=0x2, revision=0x2
[    5.927869] microcode: CPU2 sig=0x20655, pf=0x2, revision=0x2
[    5.929331] microcode: CPU3 sig=0x20655, pf=0x2, revision=0x2
[    5.931014] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    5.941126] kvm: VM_EXIT_LOAD_IA32_PERF_GLOBAL_CTRL does not work properly. Using workaround
[    6.066088] r8169 0000:03:00.0: eth0: link down
[    6.066099] r8169 0000:03:00.0: eth0: link down
[    6.066262] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[    8.198319] r8169 0000:03:00.0: eth0: link up
[    8.198438] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[    8.754604] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[  860.579813] init: failsafe main process (879) killed by TERM signal
[  865.158841] Bluetooth: Core ver 2.16
[  865.158858] NET: Registered protocol family 31
[  865.158859] Bluetooth: HCI device and connection manager initialized
[  865.158860] Bluetooth: HCI socket layer initialized
[  865.158861] Bluetooth: L2CAP socket layer initialized
[  865.158863] Bluetooth: SCO socket layer initialized
[  865.160148] Bluetooth: RFCOMM TTY layer initialized
[  865.160151] Bluetooth: RFCOMM socket layer initialized
[  865.160153] Bluetooth: RFCOMM ver 1.11

```

---

### Post by sudodus on 2012-11-29
> **haseotod1 said:**
> Hi Guys, 

please be nice im new to this website and ubuntu :P

I have been trying for days to work out how to static mount internal hard drives that have. Just for info purposes im running XBMC on a minimal install of ubuntu. 

I have reached as far as edited the fstab:

```
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=26181423-4202-4dd6-b784-60ac3e8b846e /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=92c769af-f500-474e-984b-898fd642e31d none            swap    sw           $
UUID=4AF454CFF454BF3F /media/Disk1 ntfs-3g  defaults,locale=en_US.UTF-8
UUID=6C642DE3642DB0AE /media/Disk2 ntfs-3g defaults,locale=en_US.UTF-8

```

When the pc boots and hits the XBMC splash screen i get an error that states there was an issue with mounting to /media/Disk1 

is there any obvious mistakes in what i have done?

Thanks for the help
Try without specifying locale:

```
UUID=4AF454CFF454BF3F /media/Disk1 ntfs-3g defaults
UUID=6C642DE3642DB0AE /media/Disk2 ntfs-3g defaults
```

(I thought there was a space between 3 and g, but it was only due to poor rendering of the code box. The code behind was OK.)

---

### Post by haseotod1 on 2012-11-29
no still didn't work :/

---

### Post by sudodus on 2012-11-29
Can you mount the partitions manually with mount or via a file browser?

```
sudo mount -t auto -U 4AF454CFF454BF3F /media/Disk1
```

```
sudo mount -t auto -U 6C642DE3642DB0A /media/Disk2
```

What's the permissions of /media/Disk1 and /media/Disk2

```
ls -l /media/Disk*
```

---

### Post by haseotod1 on 2012-11-30
ok, so manually mounting works great.. but i have to unmount the drive first... so it seems as if it is already mounting at boot but the mount point keeps changing..
its changing between:
USBHD-SDB1
USBHD-SDC1
USBHD-SDD1

So it looks like the hard drives are being automounted at boot, but the UUID are not listed in FSTAB...

---

### Post by haseotod1 on 2012-11-30
```
ls -l /media/Disk*
```[/QUOTE]

```

drwxrwxrwx 1 root root 4096 Nov 24 13:44 Disk1
drwxrwxrwx 2 root root 4096 Nov 27 20:41 Disk2
drwxr-xr-x 2 root root 4096 Nov 24 16:31 New_Volume
drwxr-xr-x 2 root root 4096 Nov 24 16:31 usbhd-sdb1
drwxr-xr-x 2 root root 4096 Nov 24 16:50 usbhd-sdc1
drwxr-xr-x 2 root root 4096 Nov 24 16:31 usbhd-sdd1

```

---

### Post by sudodus on 2012-11-30
Let us be sure that the UUID specs in /etc/fstab are correct. Post the output of
```
sudo blkid
```

---

### Post by sudodus on 2012-11-30
Try (if the UUID and the file system specs are correct according to *blkid*)

```
UUID=4AF454CFF454BF3F  /media/Disk1  ntfs-3g  defaults  0  2
UUID=6C642DE3642DB0AE  /media/Disk2  ntfs-3g  defaults  0  2
```

---

### Post by oldfred on 2012-11-30
It looks like your original entries were missing two parameters at the end of the fstab entry. 

sudodus example has those required parameters and should work.

       Understanding fstab
[https://help.ubuntu.com/community/Fstab](https://help.ubuntu.com/community/Fstab)
[https://wiki.archlinux.org/index.php/Fstab](https://wiki.archlinux.org/index.php/Fstab)
[https://help.ubuntu.com/community/Mount/](https://help.ubuntu.com/community/Mount/)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://www.psychocats.net/ubuntu/mountlinux](http://www.psychocats.net/ubuntu/mountlinux)

---

### Post by haseotod1 on 2012-11-30
Still did not work,

Here are the results from BLKID

```

/dev/sda1: UUID="26181423-4202-4dd6-b784-60ac3e8b846e" TYPE="ext4"
/dev/sda5: UUID="92c769af-f500-474e-984b-898fd642e31d" TYPE="swap"
/dev/sdb1: UUID="4AF454CFF454BF3F" TYPE="ntfs"
/dev/sdc1: UUID="6C642DE3642DB0AE" TYPE="ntfs"
/dev/sdd1: LABEL="New Volume" UUID="70A01293A0125FC0" TYPE="ntfs"

```

and this is what is now in fstab

```
# /etc/fstab: static file system information.
#
# Use 'blkid' to print the universally unique identifier for a
# device; this may be used with UUID= as a more robust way to name devices
# that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
# / was on /dev/sda1 during installation
UUID=26181423-4202-4dd6-b784-60ac3e8b846e /               ext4    errors=remoun$
# swap was on /dev/sda5 during installation
UUID=92c769af-f500-474e-984b-898fd642e31d none            swap    sw           $
UUID=4AF454CFF454BF3F /media/Disk1 ntfs-3g  defaults 0 2
UUID=6C642DE3642DB0AE /media/Disk2 ntfs-3g  defaults 0 2

```

---

### Post by oldfred on 2012-12-01
IF you run this what error message does it give.

       sudo mount -a
    
That should just remount from fstab and if no errors it works, it an error then there is something to fix.

---

### Post by ohnonot on 2012-12-01
hey,

sudodus is definitely better at this, just 2 things from me to be added to the soup:

- they are usb hard drives? i think i remember some problem with usb hard drives in fstab and it actually worked better when i removed them from fstab because the file manager daemon is taking care of usb drives.

- is the drive actually ntfs? (sorry, i did not read 100 lines of code output)

---

### Post by haseotod1 on 2012-12-01
> **oldfred said:**
> IF you run this what error message does it give.

       sudo mount -a
    
That should just remount from fstab and if no errors it works, it an error then there is something to fix.

It errors saying that the drives are already mounted.. i unmounted the drives and ran 'sudo mount -a' and it WORKED! So this means there is nothing wrong with the actual FSTAB just how it runs at boot time..

---

### Post by haseotod1 on 2012-12-01
> **ohnonot said:**
> hey,

sudodus is definitely better at this, just 2 things from me to be added to the soup:

- they are usb hard drives? i think i remember some problem with usb hard drives in fstab and it actually worked better when i removed them from fstab because the file manager daemon is taking care of usb drives.

- is the drive actually ntfs? (sorry, i did not read 100 lines of code output)

They are internal hard drives and they are NTFS ^^

---

### Post by sudodus on 2012-12-01
> **haseotod1 said:**
> It errors saying that the drives are already mounted.. i unmounted the drives and ran 'sudo mount -a' and it WORKED! So this means there is nothing wrong with the actual FSTAB just how it runs at boot time..
Maybe the drives are slow starters, so that they are not ready to be mounted when the system wants to mount them. This may also be the reason why you, ohnonot, had problems with such drives.

Anyway, it is not necessary to mount them automatically at boot, use the noauto option
```
UUID=4AF454CFF454BF3F  /media/Disk1  ntfs-3g  defaults,noauto  0  2
```

---

### Post by haseotod1 on 2012-12-01
there is no longer the mounting error at startup but they are still being mounted on /media/usbhd-sdb1 or usbhd-sdc1 or usbhd-sdd1

---

### Post by haseotod1 on 2012-12-01
I FIXED IT !! 

I labeled each hard drive hd1 and 2 using ntfslabel and this corrected the issue. i removed the noauto option from fstab and they are now mounting correctly to disk1 and disk2.

So this is solved thanks for your help guys!

---

### Post by sudodus on 2012-12-02
> **haseotod1 said:**
> I FIXED IT !! 

I labeled each hard drive hd1 and 2 using ntfslabel and this corrected the issue. i removed the noauto option from fstab and they are now mounting correctly to disk1 and disk2.

So this is solved thanks for your help guys!

I'm glad you found this nice solution :-)

Please click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

