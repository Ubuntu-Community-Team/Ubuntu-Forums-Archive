---
title: "Remount once &quot;Safely Removed&quot;?"
date: 2014-01-16
forum: General Help
---

### Post by PDA1 on 2014-01-16
I have an external USB flash drive (one of those small plug in things). After I get done using it, in Computer, I right click and select "Safely Remove". My assumption is the flash drive is unmounted and the power it removed from it.

How can that same usb flash drive be re-mounted so that it's usable without unplugging it and then plugging it back in?

Thanks for the help.

---

### Post by silvervulpus on 2014-01-16
every time you "eject or safely remove drive" you unmount it. every time it get plugged in... it should auto mount. does it show up in your folder browser when you plug it in? there are commands for remounting it via terminal, however if you want to leave it plugged in constantly then there is no need to unmount it at all, you only need to unmount it if you plan on removing it from the USB port, otherwise, there is no sense in unmounting it just to leave it plugged in and then remount it later.... if your trying to hide information a pretty simple way to do that to the unexperienced is to put a period at the beginning of your directory name such as ( /.HIDDENFILENAME   ) as opposed to (  /notsohiddenfilename  ) then use Control+H to view or unview hidden files.... you might also consider the storage device manager available through the ubuntu software centre or through synaptic package manager. you can use the storage device manager to mount and unmount whatever drive you want to when you want to without using the terminal command lines.

---

### Post by silvervulpus on 2014-01-16
ok so i went back and read the reviews on the device storage manager, apparently it is total crap, dont take that advice, and dont install it... us the command in the terminal 
sudo fdisk -l 

after you get the output it should 'see' you usb drive on the list
if you dont have a mount point already set you need to set one with 

sudo  mkdir /media/usb

 then use the command

sudo mount /dev/sdb1 /media/usb
the /dev/sdb1 will be changed to match whatever your drive at home is,  do not copy paste this line unless you flash drive is sdb1

also if you dont want to right click safely remove.... the CLI way to unmount is 

sudo umount /media/usb


all of this info and more is available at [http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal](http://askubuntu.com/questions/37767/how-to-access-a-usb-flash-drive-from-the-terminal)

---

### Post by llamabr on 2014-01-16
You can also see where the kernel is putting the device after you plug it in, by running dmesg.  Here you'll also be able to see any problems, before you try to mount.

---

### Post by PDA1 on 2014-01-16
Later I'll try your ideas. 

My primary concern is limiting "wear and tear" on the flash drive and the usb port it's plugged into. 

Also, energy consumption is a huge concern in what I'm doing- I've to limit power consumption as I'm running on batteries.

Like I said, all I want to do is- remove power from the usb flash drive so it's essential disconnected....but still plugged in. Then I want to re-connect (re-mount or whatever it's called) the flash drive and use it as before.

All of the flash drives or usb devices I have always auto-mount once they're plugged in my machine.

---

### Post by llamabr on 2014-01-16
This is a separate question, and there are people who can speak much more specifically about such things, but a device such as a usb thumb drive draws very little power when plugged in.  Larger usb disks will draw more, perhaps.  But I'd guess that the energy expended to find the device, and then unmount it, would equal the energy consumed by letting it sit.

In any case, if it automounts, you can find it with this command:

df

and then unmount it with this command:

sudo umount /the/path/to/the/device

---

### Post by silvervulpus on 2014-01-16
> **llamabr said:**
> This is a separate question, and there are people who can speak much more specifically about such things, but a device such as a usb thumb drive draws very little power when plugged in.  Larger usb disks will draw more, perhaps.  But I'd guess that the energy expended to find the device, and then unmount it, would equal the energy consumed by letting it sit.

In any case, if it automounts, you can find it with this command:

df

and then unmount it with this command:

sudo unmount /the/path/to/the/device


you can sufficiently remount it with almost the same command

sudo mount /the/path/to/the/device

---

### Post by PDA1 on 2014-01-16
Doesn't work.

Here's what I did-

~$ df
Filesystem          1K-blocks     Used Available Use% Mounted on
/dev/sda1            75900000 47661748  24382688  67% /

/dev/sdb1            3125864  9007824  22240640  29% /media/2881-787C

To unmount-

~$ sudo unmount /dev/sdb1
sudo: unmount: command not found

I assume you meant [I]**umount**

so....

[/I]~$ sudo umount /dev/sdb1

The drive is unmounted now but can still be seen as one of the devices using the COMPUTER window.  I want the power removed from that flash drive and be able to remount it.

That being said. Trying to remount the flash drive doesn't work.

See-

~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

Don't know what to do.

---

### Post by Dave_L on 2014-01-16
> **PDA1 said:**
> 
~$ sudo mount /dev/sdb1
mount: can't find /dev/sdb1 in /etc/fstab or /etc/mtab

Try:

```
sudo mount /dev/sdb1 /media/usb
```

---

### Post by PDA1 on 2014-01-16
Here's the result of *dmesg* while the flash drive (Sandisk Cruzer) is mounted.

```
   [    0.956393] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver 
 [    0.956417] uhci_hcd: USB Universal Host Controller Interface driver 
 [    0.956443] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [    0.956454] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
 [    0.956459] uhci_hcd 0000:00:1d.0: UHCI Host Controller 
 [    0.956538] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2 
 [    0.956572] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80 
 [    0.956791] hub 2-0:1.0: USB hub found 
 [    0.956797] hub 2-0:1.0: 2 ports detected 
 [    0.956911] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21 
 [    0.956922] uhci_hcd 0000:00:1d.1: setting latency timer to 64 
 [    0.956927] uhci_hcd 0000:00:1d.1: UHCI Host Controller 
 [    0.957012] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3 
 [    0.957059] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60 
 [    0.957278] hub 3-0:1.0: USB hub found 
 [    0.957284] hub 3-0:1.0: 2 ports detected 
 [    0.957396] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22 
 [    0.957407] uhci_hcd 0000:00:1d.2: setting latency timer to 64 
 [    0.957412] uhci_hcd 0000:00:1d.2: UHCI Host Controller 
 [    0.957487] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4 
 [    0.957534] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40 
 [    0.957752] hub 4-0:1.0: USB hub found 
 [    0.957759] hub 4-0:1.0: 2 ports detected 
 [    0.957878] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23 
 [    0.957889] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
 [    0.957894] uhci_hcd 0000:00:1d.3: UHCI Host Controller 
 [    0.957972] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5 
 [    0.958022] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20 
 [    0.958248] hub 5-0:1.0: USB hub found 
 [    0.958254] hub 5-0:1.0: 2 ports detected 
 [    0.958450] usbcore: registered new interface driver libusual 
 [    0.958532] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12 
 [    0.961207] serio: i8042 KBD port at 0x60,0x64 irq 1 
 [    0.961218] serio: i8042 AUX port at 0x60,0x64 irq 12 
 [    0.961455] mousedev: PS/2 mouse device common for all mice 
 [    0.961772] rtc_cmos 00:06: RTC can wake from S4 
 [    0.961957] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0 
 [    0.961995] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs 
 [    0.962085] device-mapper: uevent: version 1.0.3 
 [    0.962212] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com 
 [    0.962246] EISA: Probing bus 0 at eisa.0 
 [    0.962256] Cannot allocate resource for EISA slot 1 
 [    0.962259] Cannot allocate resource for EISA slot 2 
 [    0.962292] EISA: Detected 0 cards. 
 [    0.962307] cpufreq-nforce2: No nForce2 chipset. 
 [    0.962414] cpuidle: using governor ladder 
 [    0.962592] cpuidle: using governor menu 
 [    0.962595] EFI Variables Facility v0.08 2004-May-17 
 [    0.963056] TCP cubic registered 
 [    0.963258] NET: Registered protocol family 10 
 [    0.964313] NET: Registered protocol family 17 
 [    0.964323] Registering the dns_resolver key type 
 [    0.964350] Using IPI No-Shortcut mode 
 [    0.964721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3 
 [    0.964749] PM: Hibernation image not present or could not be loaded. 
 [    0.964923] registered taskstats version 1 
 [    0.975198]   Magic number: 14:377:559 
 [    0.975228] tty ttyS31: hash matches 
 [    0.975349] rtc_cmos 00:06: setting system clock to 2014-01-17 01:35:33 UTC (1389922533) 
 [    0.976352] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found 
 [    0.976355] EDD information not available. 
 [    1.100634] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX835E, KDKE, max UDMA/33 
 [    1.100779] ata1.00: ATA-7: ST980210AS, 3.CXA, max UDMA/133 
 [    1.100785] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32) 
 [    1.116513] ata2.00: configured for UDMA/33 
 [    1.116621] ata1.00: configured for UDMA/133 
 [    1.116869] scsi 0:0:0:0: Direct-Access     ATA      ST980210AS       3.CX PQ: 0 ANSI: 5 
 [    1.117093] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB) 
 [    1.117136] sd 0:0:0:0: Attached scsi generic sg0 type 0 
 [    1.117203] sd 0:0:0:0: [sda] Write Protect is off 
 [    1.117208] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00 
 [    1.117251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA 
 [    1.118580] scsi 1:0:0:0: CD-ROM            SONY     CDRW/DVD CRX835E KDKE PQ: 0 ANSI: 5 
 [    1.120343] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray 
 [    1.120348] cdrom: Uniform CD-ROM driver Revision: 3.20 
 [    1.120565] sr 1:0:0:0: Attached scsi CD-ROM sr0 
 [    1.120746] sr 1:0:0:0: Attached scsi generic sg1 type 5 
 [    1.181077]  sda: sda1 sda2 < sda5 > 
 [    1.181891] sd 0:0:0:0: [sda] Attached SCSI disk 
 [    1.182045] Freeing unused kernel memory: 744k freed 
 [    1.182528] Write protecting the kernel text: 5844k 
 [    1.182569] Write protecting the kernel read-only data: 2388k 
 [    1.182572] NX-protecting the kernel data: 4396k 
 [    1.264932] udevd[164]: starting version 175 
 [    1.334411] wmi: Mapper loaded 
 [    1.380555] acpi device:27: registered as cooling_device2 
 [    1.380894] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input4 
 [    1.380983] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no) 
 [    1.381021] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work. 
 [    1.391143] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17 
 [    1.394491] sdhci: Secure Digital Host Controller Interface driver 
 [    1.394496] sdhci: Copyright(c) Pierre Ossman 
 [    1.408155] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243) 
 [    1.408166] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243) 
 [    1.408175] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243) 
 [    1.448235] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0 
 [    1.448272] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0 
 [    1.448294] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19) 
 [    1.448330] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
 [    1.449388] mmc0: no vmmc regulator found 
 [    1.449432] Registered led device: mmc0:: 
 [    1.451471] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA 
 [    1.451530] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19 
 [    1.469102] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:19:b9:73:66:38 
 [    1.471687] [drm] Initialized drm 1.1.0 20060810 
 [    1.488458] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [    1.488467] i915 0000:00:02.0: setting latency timer to 64 
 [    1.491528] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010). 
 [    1.491533] [drm] Driver supports precise vblank timestamp query. 
 [    1.512583] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11 
 [    1.519915] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem 
 [    1.640167] usb 4-1: new full-speed USB device number 2 using uhci_hcd 
 [    1.803460] [drm] initialized overlay support 
 [    1.807660] hub 4-1:1.0: USB hub found 
 [    1.809619] hub 4-1:1.0: 4 ports detected 
 [    2.016260] firewire_core: created device fw0: GUID 5b4fc0003fffffff, S400 
 [    2.053363] fbcon: inteldrmfb (fb0) is primary device 
 [    2.053454] Console: switching to colour frame buffer device 160x64 
 [    2.053515] fb0: inteldrmfb frame buffer device 
 [    2.053518] drm: registered panic notifier 
 [    2.053549] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0 
 [    2.093615] usb 4-1.1: new low-speed USB device number 3 using uhci_hcd 
 [    2.295681] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input5 
 [    2.295906] generic-usb 0003:049F:000E.0001: input,hidraw0: USB HID v1.00 Keyboard [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.2-1.1/input0 
 [    2.353616] usb 4-1.2: new full-speed USB device number 4 using uhci_hcd 
 [    2.410866] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.1/input/input6 
 [    2.411444] generic-usb 0003:049F:000E.0002: input,hiddev0,hidraw1: USB HID v1.00 Device [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.2-1.1/input1 
 [    2.411673] usbcore: registered new interface driver usbhid 
 [    2.411677] usbhid: USB HID core driver 
 [    2.501829] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.2/4-1.2:1.0/input/input7 
 [    2.502034] generic-usb 0003:046D:C52F.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1.2/input0 
 [    2.507783] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.2/4-1.2:1.1/input/input8 
 [    2.507987] generic-usb 0003:046D:C52F.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-1.2/input1 
 [    7.593534] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null) 
 [   42.321311] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   42.354921] udevd[489]: starting version 175 
 [   42.428142] lp: driver loaded but no devices found 
 [   42.469885] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro 
 [   42.656599] cfg80211: Calling CRDA to update world regulatory domain 
 [   42.840500] Bluetooth: Core ver 2.16 
 [   42.840535] NET: Registered protocol family 31 
 [   42.840538] Bluetooth: HCI device and connection manager initialized 
 [   42.840543] Bluetooth: HCI socket layer initialized 
 [   42.840547] Bluetooth: L2CAP socket layer initialized 
 [   42.840555] Bluetooth: SCO socket layer initialized 
 [   42.918017] Bluetooth: BNEP (Ethernet Emulation) ver 1.3 
 [   42.918023] Bluetooth: BNEP filters: protocol multicast 
 [   42.931555] ppdev: user-space parallel port driver 
 [   42.958483] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s 
 [   42.958489] iwl3945: Copyright(c) 2003-2011 Intel Corporation 
 [   42.958577] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16 
 [   42.958595] iwl3945 0000:0b:00.0: setting latency timer to 64 
 [   43.023013] intel_rng: FWH not detected 
 [   43.023556] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels 
 [   43.023562] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG 
 [   43.023726] iwl3945 0000:0b:00.0: irq 42 for MSI/MSI-X 
 [   43.029668] Bluetooth: RFCOMM TTY layer initialized 
 [   43.029677] Bluetooth: RFCOMM socket layer initialized 
 [   43.029680] Bluetooth: RFCOMM ver 1.11 
 [   43.040031] Registered led device: phy0-led 
 [   43.040079] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
 [   43.041284] leds_ss4200: no LED devices found 
 [   43.079684] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
 [   43.079698] r592 0000:03:01.2: setting latency timer to 64 
 [   43.084211] r592: driver successfully loaded 
 [   43.091573] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs' 
 [   43.094939] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18 
 [   43.094952] r852 0000:03:01.3: setting latency timer to 64 
 [   43.098262] r852: Non dma capable device detected, dma disabled 
 [   43.098286] r852: driver loaded successfully 
 [   43.121485] ip_tables: (C) 2000-2006 Netfilter Core Team 
 [   43.137395] nf_conntrack version 0.5.0 (16384 buckets, 65536 max) 
 [   43.174091] ip6_tables: (C) 2000-2006 Netfilter Core Team 
 [   43.694874] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21 
 [   43.694962] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X 
 [   43.695004] snd_hda_intel 0000:00:1b.0: setting latency timer to 64 
 [   43.695354] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2) 
 [   43.746706] init: Failed to spawn smbd main process: unable to execute: No such file or directory 
 [   43.827959] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0 
 [   43.866818] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9 
 [   43.889108] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10 
 [   43.889379] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11 
 [   43.934564] init: failsafe main process (1232) killed by TERM signal 
 [   44.035803] input: Dell WMI hotkeys as /devices/virtual/input/input12 
 [   44.064115] init: macchanger pre-start process (1314) terminated with status 1 
 [   44.239874] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain 
 [   44.239881] cfg80211: World regulatory domain updated: 
 [   44.239884] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
 [   44.239889] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   44.239893] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
 [   44.239898] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm) 
 [   44.239902] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   44.239906] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   44.350999] init: kdm main process (1461) killed by TERM signal 
 [   44.585722] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9 
 [   44.640034] vboxdrv: Found 2 processor cores. 
 [   44.643472] vboxdrv: fAsync=1 offMin=0xc50d8e2c offMax=0xc50d8e2c 
 [   44.643585] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'. 
 [   44.643588] vboxdrv: Successfully loaded version 4.1.30 (interface 0x00190000). 
 [   44.656313] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   44.656703] ADDRCONF(NETDEV_UP): wlan0: link is not ready 
 [   44.666586] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   44.668295] ADDRCONF(NETDEV_UP): eth0: link is not ready 
 [   44.864589] vboxpci: IOMMU not found (not registered) 
 [   45.520298] [drm] Changing LVDS panel from (-hsync, -vsync) to (+hsync, +vsync) 
 [   46.834865] uhci_hcd 0000:00:1d.0: PCI INT A disabled 
 [   46.841795] uhci_hcd 0000:00:1d.3: PCI INT D disabled 
 [   46.856448] ehci_hcd 0000:00:1d.7: PCI INT A disabled 
 [   46.856499] ehci_hcd 0000:00:1d.7: PME# enabled 
 [   47.124063] ehci_hcd 0000:00:1d.7: BAR 0: set to [mem 0xffa80000-0xffa803ff] (PCI address [0xffa80000-0xffa803ff]) 
 [   47.124088] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x109) 
 [   47.124118] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102) 
 [   47.126396] ehci_hcd 0000:00:1d.7: PME# disabled 
 [   47.126412] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [   47.126421] ehci_hcd 0000:00:1d.7: setting latency timer to 64 
 [   47.179929] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20 
 [   47.179942] uhci_hcd 0000:00:1d.0: setting latency timer to 64 
 [   47.231618] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23 
 [   47.231631] uhci_hcd 0000:00:1d.3: setting latency timer to 64 
 [   47.470855] init: plymouth-stop pre-start process (2434) terminated with status 1 
 [   50.210466] wlan0: authenticate with 00:1f:90:ba:c3:9c (try 1) 
 [   50.212200] wlan0: authenticated 
 [   50.212656] wlan0: associate with 00:1f:90:ba:c3:9c (try 1) 
 [   50.215021] wlan0: RX AssocResp from 00:1f:90:ba:c3:9c (capab=0x431 status=0 aid=3) 
 [   50.215028] wlan0: associated 
 [   50.216640] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready 
 [   50.216729] cfg80211: Calling CRDA for country: US 
 [   50.233314] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233321] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233325] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233330] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233334] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233338] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233342] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233347] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233351] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233355] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233359] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233364] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233368] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233372] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233376] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233384] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233389] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233393] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233397] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233401] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233406] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233410] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233414] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm) 
 [   50.233418] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233423] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm) 
 [   50.233427] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233431] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm) 
 [   50.233435] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233439] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm) 
 [   50.233443] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233448] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   50.233452] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233456] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   50.233460] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233465] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   50.233469] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233473] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   50.233477] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233481] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
 [   50.233485] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233490] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
 [   50.233494] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233498] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
 [   50.233502] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233507] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
 [   50.233511] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule: 
 [   50.233515] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
 [   50.233519] cfg80211: Regulatory domain changed to country: US 
 [   50.233522] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp) 
 [   50.233527] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm) 
 [   50.233532] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm) 
 [   50.233536] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   50.233540] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   50.233544] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm) 
 [   50.233548] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm) 
 [   53.057510] init: Failed to spawn nmbd main process: unable to execute: No such file or directory 
 [   61.184057] wlan0: no IPv6 routers present 
 [   94.920136] usb 1-1: new high-speed USB device number 3 using ehci_hcd 
 [   95.102140] Initializing USB Mass Storage driver... 
 [   95.108062] scsi2 : usb-storage 1-1:1.0 
 [   95.108213] usbcore: registered new interface driver usb-storage 
 [   95.108217] USB Mass Storage support registered. 
 [   96.109448] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           1.19 PQ: 0 ANSI: 5 
 [   96.111690] sd 2:0:0:0: Attached scsi generic sg2 type 0 
 [   96.115631] sd 2:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB) 
 [   96.116864] sd 2:0:0:0: [sdb] Write Protect is off 
 [   96.116875] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00 
 [   96.118121] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA 
 [   96.127910]  sdb: sdb1 sdb2 
 [   96.130871] sd 2:0:0:0: [sdb] Attached SCSI removable disk 
 [  128.134686] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended 
 [  128.136332] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null) 
 [  128.252862] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [  253.277572] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [  278.653602] WARNING! power/level is deprecated; use power/control instead 
 [  278.736057] usb 1-1: USB disconnect, device number 3 
 [  344.764082] usb 1-3: new high-speed USB device number 4 using ehci_hcd 
 [  344.901122] scsi3 : usb-storage 1-3:1.0 
 [  345.901221] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           1.01 PQ: 0 ANSI: 2 
 [  345.903538] sd 3:0:0:0: Attached scsi generic sg2 type 0 
 [  345.906264] sd 3:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB) 
 [  345.907889] sd 3:0:0:0: [sdb] Write Protect is off 
 [  345.907900] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00 
 [  345.908750] sd 3:0:0:0: [sdb] No Caching mode page found 
 [  345.908759] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
 [  345.912379] sd 3:0:0:0: [sdb] No Caching mode page found 
 [  345.912390] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
 [  345.916295]  sdb: sdb1 
 [  345.919503] sd 3:0:0:0: [sdb] No Caching mode page found 
 [  345.919514] sd 3:0:0:0: [sdb] Assuming drive cache: write through 
 [  345.919522] sd 3:0:0:0: [sdb] Attached SCSI removable disk 
 [  378.281668] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [  492.000206] CE: hpet increased min_delta_ns to 20113 nsec 
 [  503.285942] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [  628.289976] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [  753.293872] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [  878.297960] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1003.301837] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1128.305865] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1253.309861] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1378.313782] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1503.317776] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1628.321696] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1753.325689] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 1878.329613] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 2003.333564] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 2128.337503] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 [ 2135.889963] sdb: detected capacity change from 32015679488 to 0 
 [ 2227.068145] usb 1-3: USB disconnect, device number 4 
 [ 2231.956107] usb 1-1: new high-speed USB device number 5 using ehci_hcd 
 [ 2232.093211] scsi4 : usb-storage 1-1:1.0 
 [ 2233.093097] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer           1.01 PQ: 0 ANSI: 2 
 [ 2233.095392] sd 4:0:0:0: Attached scsi generic sg2 type 0 
 [ 2233.098009] sd 4:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB) 
 [ 2233.099637] sd 4:0:0:0: [sdb] Write Protect is off 
 [ 2233.099648] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00 
 [ 2233.100497] sd 4:0:0:0: [sdb] No Caching mode page found 
 [ 2233.100506] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
 [ 2233.104758] sd 4:0:0:0: [sdb] No Caching mode page found 
 [ 2233.104769] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
 [ 2233.108191]  sdb: sdb1 
 [ 2233.111126] sd 4:0:0:0: [sdb] No Caching mode page found 
 [ 2233.111137] sd 4:0:0:0: [sdb] Assuming drive cache: write through 
 [ 2233.111146] sd 4:0:0:0: [sdb] Attached SCSI removable disk 
 [ 2253.341438] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2  
 MM061:~$  


```

Here's the result of *dmesg* while the flash drive (Sandisk Cruzer) is UNmounted.

```
r 2
[    0.956572] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.956791] hub 2-0:1.0: USB hub found
[    0.956797] hub 2-0:1.0: 2 ports detected
[    0.956911] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.956922] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.956927] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.957012] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.957059] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.957278] hub 3-0:1.0: USB hub found
[    0.957284] hub 3-0:1.0: 2 ports detected
[    0.957396] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.957407] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.957412] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.957487] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.957534] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.957752] hub 4-0:1.0: USB hub found
[    0.957759] hub 4-0:1.0: 2 ports detected
[    0.957878] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.957889] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.957894] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.957972] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.958022] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.958248] hub 5-0:1.0: USB hub found
[    0.958254] hub 5-0:1.0: 2 ports detected
[    0.958450] usbcore: registered new interface driver libusual
[    0.958532] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.961207] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.961218] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.961455] mousedev: PS/2 mouse device common for all mice
[    0.961772] rtc_cmos 00:06: RTC can wake from S4
[    0.961957] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.961995] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.962085] device-mapper: uevent: version 1.0.3
[    0.962212] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.962246] EISA: Probing bus 0 at eisa.0
[    0.962256] Cannot allocate resource for EISA slot 1
[    0.962259] Cannot allocate resource for EISA slot 2
[    0.962292] EISA: Detected 0 cards.
[    0.962307] cpufreq-nforce2: No nForce2 chipset.
[    0.962414] cpuidle: using governor ladder
[    0.962592] cpuidle: using governor menu
[    0.962595] EFI Variables Facility v0.08 2004-May-17
[    0.963056] TCP cubic registered
[    0.963258] NET: Registered protocol family 10
[    0.964313] NET: Registered protocol family 17
[    0.964323] Registering the dns_resolver key type
[    0.964350] Using IPI No-Shortcut mode
[    0.964721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.964749] PM: Hibernation image not present or could not be loaded.
[    0.964923] registered taskstats version 1
[    0.975198]   Magic number: 14:377:559
[    0.975228] tty ttyS31: hash matches
[    0.975349] rtc_cmos 00:06: setting system clock to 2014-01-17 01:35:33 UTC (1389922533)
[    0.976352] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.976355] EDD information not available.
[    1.100634] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX835E, KDKE, max UDMA/33
[    1.100779] ata1.00: ATA-7: ST980210AS, 3.CXA, max UDMA/133
[    1.100785] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.116513] ata2.00: configured for UDMA/33
[    1.116621] ata1.00: configured for UDMA/133
[    1.116869] scsi 0:0:0:0: Direct-Access     ATA      ST980210AS       3.CX PQ: 0 ANSI: 5
[    1.117093] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.117136] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.117203] sd 0:0:0:0: [sda] Write Protect is off
[    1.117208] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.117251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.118580] scsi 1:0:0:0: CD-ROM            SONY     CDRW/DVD CRX835E KDKE PQ: 0 ANSI: 5
[    1.120343] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    1.120348] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.120565] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.120746] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.181077]  sda: sda1 sda2 < sda5 >
[    1.181891] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.182045] Freeing unused kernel memory: 744k freed
[    1.182528] Write protecting the kernel text: 5844k
[    1.182569] Write protecting the kernel read-only data: 2388k
[    1.182572] NX-protecting the kernel data: 4396k
[    1.264932] udevd[164]: starting version 175
[    1.334411] wmi: Mapper loaded
[    1.380555] acpi device:27: registered as cooling_device2
[    1.380894] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input4
[    1.380983] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.381021] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    1.391143] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.394491] sdhci: Secure Digital Host Controller Interface driver
[    1.394496] sdhci: Copyright(c) Pierre Ossman
[    1.408155] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.408166] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.408175] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.448235] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.448272] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.448294] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.448330] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.449388] mmc0: no vmmc regulator found
[    1.449432] Registered led device: mmc0::
[    1.451471] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.451530] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.469102] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:19:b9:73:66:38
[    1.471687] [drm] Initialized drm 1.1.0 20060810
[    1.488458] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.488467] i915 0000:00:02.0: setting latency timer to 64
[    1.491528] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.491533] [drm] Driver supports precise vblank timestamp query.
[    1.512583] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.519915] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.640167] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.803460] [drm] initialized overlay support
[    1.807660] hub 4-1:1.0: USB hub found
[    1.809619] hub 4-1:1.0: 4 ports detected
[    2.016260] firewire_core: created device fw0: GUID 5b4fc0003fffffff, S400
[    2.053363] fbcon: inteldrmfb (fb0) is primary device
[    2.053454] Console: switching to colour frame buffer device 160x64
[    2.053515] fb0: inteldrmfb frame buffer device
[    2.053518] drm: registered panic notifier
[    2.053549] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.093615] usb 4-1.1: new low-speed USB device number 3 using uhci_hcd
[    2.295681] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input5
[    2.295906] generic-usb 0003:049F:000E.0001: input,hidraw0: USB HID v1.00 Keyboard [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.2-1.1/input0
[    2.353616] usb 4-1.2: new full-speed USB device number 4 using uhci_hcd
[    2.410866] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.1/input/input6
[    2.411444] generic-usb 0003:049F:000E.0002: input,hiddev0,hidraw1: USB HID v1.00 Device [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.2-1.1/input1
[    2.411673] usbcore: registered new interface driver usbhid
[    2.411677] usbhid: USB HID core driver
[    2.501829] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.2/4-1.2:1.0/input/input7
[    2.502034] generic-usb 0003:046D:C52F.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1.2/input0
[    2.507783] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.2/4-1.2:1.1/input/input8
[    2.507987] generic-usb 0003:046D:C52F.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-1.2/input1
[    7.593534] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   42.321311] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.354921] udevd[489]: starting version 175
[   42.428142] lp: driver loaded but no devices found
[   42.469885] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   42.656599] cfg80211: Calling CRDA to update world regulatory domain
[   42.840500] Bluetooth: Core ver 2.16
[   42.840535] NET: Registered protocol family 31
[   42.840538] Bluetooth: HCI device and connection manager initialized
[   42.840543] Bluetooth: HCI socket layer initialized
[   42.840547] Bluetooth: L2CAP socket layer initialized
[   42.840555] Bluetooth: SCO socket layer initialized
[   42.918017] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.918023] Bluetooth: BNEP filters: protocol multicast
[   42.931555] ppdev: user-space parallel port driver
[   42.958483] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   42.958489] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   42.958577] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   42.958595] iwl3945 0000:0b:00.0: setting latency timer to 64
[   43.023013] intel_rng: FWH not detected
[   43.023556] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   43.023562] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   43.023726] iwl3945 0000:0b:00.0: irq 42 for MSI/MSI-X
[   43.029668] Bluetooth: RFCOMM TTY layer initialized
[   43.029677] Bluetooth: RFCOMM socket layer initialized
[   43.029680] Bluetooth: RFCOMM ver 1.11
[   43.040031] Registered led device: phy0-led
[   43.040079] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   43.041284] leds_ss4200: no LED devices found
[   43.079684] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   43.079698] r592 0000:03:01.2: setting latency timer to 64
[   43.084211] r592: driver successfully loaded
[   43.091573] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   43.094939] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   43.094952] r852 0000:03:01.3: setting latency timer to 64
[   43.098262] r852: Non dma capable device detected, dma disabled
[   43.098286] r852: driver loaded successfully
[   43.121485] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.137395] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   43.174091] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   43.694874] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   43.694962] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   43.695004] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   43.695354] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   43.746706] init: Failed to spawn smbd main process: unable to execute: No such file or directory
[   43.827959] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   43.866818] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   43.889108] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   43.889379] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   43.934564] init: failsafe main process (1232) killed by TERM signal
[   44.035803] input: Dell WMI hotkeys as /devices/virtual/input/input12
[   44.064115] init: macchanger pre-start process (1314) terminated with status 1
[   44.239874] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   44.239881] cfg80211: World regulatory domain updated:
[   44.239884] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   44.239889] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.239893] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   44.239898] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   44.239902] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.239906] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.350999] init: kdm main process (1461) killed by TERM signal
[   44.585722] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   44.640034] vboxdrv: Found 2 processor cores.
[   44.643472] vboxdrv: fAsync=1 offMin=0xc50d8e2c offMax=0xc50d8e2c
[   44.643585] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   44.643588] vboxdrv: Successfully loaded version 4.1.30 (interface 0x00190000).
[   44.656313] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.656703] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.666586] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.668295] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.864589] vboxpci: IOMMU not found (not registered)
[   45.520298] [drm] Changing LVDS panel from (-hsync, -vsync) to (+hsync, +vsync)
[   46.834865] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[   46.841795] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[   46.856448] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[   46.856499] ehci_hcd 0000:00:1d.7: PME# enabled
[   47.124063] ehci_hcd 0000:00:1d.7: BAR 0: set to [mem 0xffa80000-0xffa803ff] (PCI address [0xffa80000-0xffa803ff])
[   47.124088] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x109)
[   47.124118] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[   47.126396] ehci_hcd 0000:00:1d.7: PME# disabled
[   47.126412] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   47.126421] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   47.179929] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   47.179942] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   47.231618] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   47.231631] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   47.470855] init: plymouth-stop pre-start process (2434) terminated with status 1
[   50.210466] wlan0: authenticate with 00:1f:90:ba:c3:9c (try 1)
[   50.212200] wlan0: authenticated
[   50.212656] wlan0: associate with 00:1f:90:ba:c3:9c (try 1)
[   50.215021] wlan0: RX AssocResp from 00:1f:90:ba:c3:9c (capab=0x431 status=0 aid=3)
[   50.215028] wlan0: associated
[   50.216640] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.216729] cfg80211: Calling CRDA for country: US
[   50.233314] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   50.233321] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233325] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   50.233330] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233334] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   50.233338] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233342] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   50.233347] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233351] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   50.233355] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233359] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   50.233364] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233368] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   50.233372] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233376] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   50.233381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233384] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   50.233389] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233393] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   50.233397] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233401] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   50.233406] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233410] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   50.233414] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233418] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   50.233423] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233427] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   50.233431] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233435] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   50.233439] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233443] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   50.233448] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233452] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   50.233456] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233460] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   50.233465] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233469] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   50.233473] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233477] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   50.233481] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233485] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   50.233490] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233494] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   50.233498] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233502] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   50.233507] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233511] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   50.233515] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233519] cfg80211: Regulatory domain changed to country: US
[   50.233522] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.233527] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233532] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233536] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233540] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233544] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233548] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   53.057510] init: Failed to spawn nmbd main process: unable to execute: No such file or directory
[   61.184057] wlan0: no IPv6 routers present
[   94.920136] usb 1-1: new high-speed USB device number 3 using ehci_hcd
[   95.102140] Initializing USB Mass Storage driver...
[   95.108062] scsi2 : usb-storage 1-1:1.0
[   95.108213] usbcore: registered new interface driver usb-storage
[   95.108217] USB Mass Storage support registered.
[   96.109448] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           1.19 PQ: 0 ANSI: 5
[   96.111690] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   96.115631] sd 2:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[   96.116864] sd 2:0:0:0: [sdb] Write Protect is off
[   96.116875] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   96.118121] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   96.127910]  sdb: sdb1 sdb2
[   96.130871] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  128.134686] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[  128.136332] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[  128.252862] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  253.277572] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  278.653602] WARNING! power/level is deprecated; use power/control instead
[  278.736057] usb 1-1: USB disconnect, device number 3
[  344.764082] usb 1-3: new high-speed USB device number 4 using ehci_hcd
[  344.901122] scsi3 : usb-storage 1-3:1.0
[  345.901221] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           1.01 PQ: 0 ANSI: 2
[  345.903538] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  345.906264] sd 3:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB)
[  345.907889] sd 3:0:0:0: [sdb] Write Protect is off
[  345.907900] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  345.908750] sd 3:0:0:0: [sdb] No Caching mode page found
[  345.908759] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  345.912379] sd 3:0:0:0: [sdb] No Caching mode page found
[  345.912390] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  345.916295]  sdb: sdb1
[  345.919503] sd 3:0:0:0: [sdb] No Caching mode page found
[  345.919514] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  345.919522] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  378.281668] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  492.000206] CE: hpet increased min_delta_ns to 20113 nsec
[  503.285942] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  628.289976] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  753.293872] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  878.297960] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1003.301837] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1128.305865] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1253.309861] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1378.313782] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1503.317776] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1628.321696] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1753.325689] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1878.329613] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2003.333564] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2128.337503] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2135.889963] sdb: detected capacity change from 32015679488 to 0
[ 2227.068145] usb 1-3: USB disconnect, device number 4
[ 2231.956107] usb 1-1: new high-speed USB device number 5 using ehci_hcd
[ 2232.093211] scsi4 : usb-storage 1-1:1.0
[ 2233.093097] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer           1.01 PQ: 0 ANSI: 2
[ 2233.095392] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2233.098009] sd 4:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB)
[ 2233.099637] sd 4:0:0:0: [sdb] Write Protect is off
[ 2233.099648] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2233.100497] sd 4:0:0:0: [sdb] No Caching mode page found
[ 2233.100506] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.104758] sd 4:0:0:0: [sdb] No Caching mode page found
[ 2233.104769] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.108191]  sdb: sdb1
[ 2233.111126] sd 4:0:0:0: [sdb] No Caching mode page found
[ 2233.111137] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.111146] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 2253.341438] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2378.345412] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2503.349289] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
MM061:~$ 


```

Here's *dmesg* with the flash drive "Safely removed"

```
[    0.956572] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    0.956791] hub 2-0:1.0: USB hub found
[    0.956797] hub 2-0:1.0: 2 ports detected
[    0.956911] uhci_hcd 0000:00:1d.1: PCI INT B -> GSI 21 (level, low) -> IRQ 21
[    0.956922] uhci_hcd 0000:00:1d.1: setting latency timer to 64
[    0.956927] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    0.957012] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    0.957059] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    0.957278] hub 3-0:1.0: USB hub found
[    0.957284] hub 3-0:1.0: 2 ports detected
[    0.957396] uhci_hcd 0000:00:1d.2: PCI INT C -> GSI 22 (level, low) -> IRQ 22
[    0.957407] uhci_hcd 0000:00:1d.2: setting latency timer to 64
[    0.957412] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    0.957487] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    0.957534] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    0.957752] hub 4-0:1.0: USB hub found
[    0.957759] hub 4-0:1.0: 2 ports detected
[    0.957878] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[    0.957889] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[    0.957894] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    0.957972] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    0.958022] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    0.958248] hub 5-0:1.0: USB hub found
[    0.958254] hub 5-0:1.0: 2 ports detected
[    0.958450] usbcore: registered new interface driver libusual
[    0.958532] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    0.961207] serio: i8042 KBD port at 0x60,0x64 irq 1
[    0.961218] serio: i8042 AUX port at 0x60,0x64 irq 12
[    0.961455] mousedev: PS/2 mouse device common for all mice
[    0.961772] rtc_cmos 00:06: RTC can wake from S4
[    0.961957] rtc_cmos 00:06: rtc core: registered rtc_cmos as rtc0
[    0.961995] rtc0: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    0.962085] device-mapper: uevent: version 1.0.3
[    0.962212] device-mapper: ioctl: 4.22.0-ioctl (2011-10-19) initialised: dm-devel@redhat.com
[    0.962246] EISA: Probing bus 0 at eisa.0
[    0.962256] Cannot allocate resource for EISA slot 1
[    0.962259] Cannot allocate resource for EISA slot 2
[    0.962292] EISA: Detected 0 cards.
[    0.962307] cpufreq-nforce2: No nForce2 chipset.
[    0.962414] cpuidle: using governor ladder
[    0.962592] cpuidle: using governor menu
[    0.962595] EFI Variables Facility v0.08 2004-May-17
[    0.963056] TCP cubic registered
[    0.963258] NET: Registered protocol family 10
[    0.964313] NET: Registered protocol family 17
[    0.964323] Registering the dns_resolver key type
[    0.964350] Using IPI No-Shortcut mode
[    0.964721] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    0.964749] PM: Hibernation image not present or could not be loaded.
[    0.964923] registered taskstats version 1
[    0.975198]   Magic number: 14:377:559
[    0.975228] tty ttyS31: hash matches
[    0.975349] rtc_cmos 00:06: setting system clock to 2014-01-17 01:35:33 UTC (1389922533)
[    0.976352] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    0.976355] EDD information not available.
[    1.100634] ata2.00: ATAPI: SONY CD-RW/DVD-ROM CRX835E, KDKE, max UDMA/33
[    1.100779] ata1.00: ATA-7: ST980210AS, 3.CXA, max UDMA/133
[    1.100785] ata1.00: 156301488 sectors, multi 8: LBA48 NCQ (depth 0/32)
[    1.116513] ata2.00: configured for UDMA/33
[    1.116621] ata1.00: configured for UDMA/133
[    1.116869] scsi 0:0:0:0: Direct-Access     ATA      ST980210AS       3.CX PQ: 0 ANSI: 5
[    1.117093] sd 0:0:0:0: [sda] 156301488 512-byte logical blocks: (80.0 GB/74.5 GiB)
[    1.117136] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.117203] sd 0:0:0:0: [sda] Write Protect is off
[    1.117208] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.117251] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.118580] scsi 1:0:0:0: CD-ROM            SONY     CDRW/DVD CRX835E KDKE PQ: 0 ANSI: 5
[    1.120343] sr0: scsi3-mmc drive: 0x/24x writer cd/rw xa/form2 cdda tray
[    1.120348] cdrom: Uniform CD-ROM driver Revision: 3.20
[    1.120565] sr 1:0:0:0: Attached scsi CD-ROM sr0
[    1.120746] sr 1:0:0:0: Attached scsi generic sg1 type 5
[    1.181077]  sda: sda1 sda2 < sda5 >
[    1.181891] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.182045] Freeing unused kernel memory: 744k freed
[    1.182528] Write protecting the kernel text: 5844k
[    1.182569] Write protecting the kernel read-only data: 2388k
[    1.182572] NX-protecting the kernel data: 4396k
[    1.264932] udevd[164]: starting version 175
[    1.334411] wmi: Mapper loaded
[    1.380555] acpi device:27: registered as cooling_device2
[    1.380894] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:01/input/input4
[    1.380983] ACPI: Video Device [VID1] (multi-head: yes  rom: no  post: no)
[    1.381021] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    1.391143] b44 0000:03:00.0: PCI INT A -> GSI 17 (level, low) -> IRQ 17
[    1.394491] sdhci: Secure Digital Host Controller Interface driver
[    1.394496] sdhci: Copyright(c) Pierre Ossman
[    1.408155] ssb: Core 0 found: Fast Ethernet (cc 0x806, rev 0x07, vendor 0x4243)
[    1.408166] ssb: Core 1 found: V90 (cc 0x807, rev 0x03, vendor 0x4243)
[    1.408175] ssb: Core 2 found: PCI (cc 0x804, rev 0x0A, vendor 0x4243)
[    1.448235] ssb: Sonics Silicon Backplane found on PCI device 0000:03:00.0
[    1.448272] b44: Broadcom 44xx/47xx 10/100 PCI ethernet driver version 2.0
[    1.448294] sdhci-pci 0000:03:01.1: SDHCI controller found [1180:0822] (rev 19)
[    1.448330] sdhci-pci 0000:03:01.1: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[    1.449388] mmc0: no vmmc regulator found
[    1.449432] Registered led device: mmc0::
[    1.451471] mmc0: SDHCI controller on PCI [0000:03:01.1] using DMA
[    1.451530] firewire_ohci 0000:03:01.0: PCI INT A -> GSI 19 (level, low) -> IRQ 19
[    1.469102] b44 ssb0:0: eth0: Broadcom 44xx/47xx 10/100 PCI ethernet driver 00:19:b9:73:66:38
[    1.471687] [drm] Initialized drm 1.1.0 20060810
[    1.488458] i915 0000:00:02.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[    1.488467] i915 0000:00:02.0: setting latency timer to 64
[    1.491528] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[    1.491533] [drm] Driver supports precise vblank timestamp query.
[    1.512583] firewire_ohci: Added fw-ohci device 0000:03:01.0, OHCI v1.10, 4 IR + 4 IT contexts, quirks 0x11
[    1.519915] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.640167] usb 4-1: new full-speed USB device number 2 using uhci_hcd
[    1.803460] [drm] initialized overlay support
[    1.807660] hub 4-1:1.0: USB hub found
[    1.809619] hub 4-1:1.0: 4 ports detected
[    2.016260] firewire_core: created device fw0: GUID 5b4fc0003fffffff, S400
[    2.053363] fbcon: inteldrmfb (fb0) is primary device
[    2.053454] Console: switching to colour frame buffer device 160x64
[    2.053515] fb0: inteldrmfb frame buffer device
[    2.053518] drm: registered panic notifier
[    2.053549] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[    2.093615] usb 4-1.1: new low-speed USB device number 3 using uhci_hcd
[    2.295681] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.0/input/input5
[    2.295906] generic-usb 0003:049F:000E.0001: input,hidraw0: USB HID v1.00 Keyboard [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.2-1.1/input0
[    2.353616] usb 4-1.2: new full-speed USB device number 4 using uhci_hcd
[    2.410866] input: Compaq Compaq Internet Keyboard as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.1/4-1.1:1.1/input/input6
[    2.411444] generic-usb 0003:049F:000E.0002: input,hiddev0,hidraw1: USB HID v1.00 Device [Compaq Compaq Internet Keyboard] on usb-0000:00:1d.2-1.1/input1
[    2.411673] usbcore: registered new interface driver usbhid
[    2.411677] usbhid: USB HID core driver
[    2.501829] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.2/4-1.2:1.0/input/input7
[    2.502034] generic-usb 0003:046D:C52F.0003: input,hidraw2: USB HID v1.11 Mouse [Logitech USB Receiver] on usb-0000:00:1d.2-1.2/input0
[    2.507783] input: Logitech USB Receiver as /devices/pci0000:00/0000:00:1d.2/usb4/4-1/4-1.2/4-1.2:1.1/input/input8
[    2.507987] generic-usb 0003:046D:C52F.0004: input,hiddev0,hidraw3: USB HID v1.11 Device [Logitech USB Receiver] on usb-0000:00:1d.2-1.2/input1
[    7.593534] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[   42.321311] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   42.354921] udevd[489]: starting version 175
[   42.428142] lp: driver loaded but no devices found
[   42.469885] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   42.656599] cfg80211: Calling CRDA to update world regulatory domain
[   42.840500] Bluetooth: Core ver 2.16
[   42.840535] NET: Registered protocol family 31
[   42.840538] Bluetooth: HCI device and connection manager initialized
[   42.840543] Bluetooth: HCI socket layer initialized
[   42.840547] Bluetooth: L2CAP socket layer initialized
[   42.840555] Bluetooth: SCO socket layer initialized
[   42.918017] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   42.918023] Bluetooth: BNEP filters: protocol multicast
[   42.931555] ppdev: user-space parallel port driver
[   42.958483] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   42.958489] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   42.958577] iwl3945 0000:0b:00.0: PCI INT A -> GSI 16 (level, low) -> IRQ 16
[   42.958595] iwl3945 0000:0b:00.0: setting latency timer to 64
[   43.023013] intel_rng: FWH not detected
[   43.023556] iwl3945 0000:0b:00.0: Tunable channels: 11 802.11bg, 13 802.11a channels
[   43.023562] iwl3945 0000:0b:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   43.023726] iwl3945 0000:0b:00.0: irq 42 for MSI/MSI-X
[   43.029668] Bluetooth: RFCOMM TTY layer initialized
[   43.029677] Bluetooth: RFCOMM socket layer initialized
[   43.029680] Bluetooth: RFCOMM ver 1.11
[   43.040031] Registered led device: phy0-led
[   43.040079] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   43.041284] leds_ss4200: no LED devices found
[   43.079684] r592 0000:03:01.2: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   43.079698] r592 0000:03:01.2: setting latency timer to 64
[   43.084211] r592: driver successfully loaded
[   43.091573] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   43.094939] r852 0000:03:01.3: PCI INT B -> GSI 18 (level, low) -> IRQ 18
[   43.094952] r852 0000:03:01.3: setting latency timer to 64
[   43.098262] r852: Non dma capable device detected, dma disabled
[   43.098286] r852: driver loaded successfully
[   43.121485] ip_tables: (C) 2000-2006 Netfilter Core Team
[   43.137395] nf_conntrack version 0.5.0 (16384 buckets, 65536 max)
[   43.174091] ip6_tables: (C) 2000-2006 Netfilter Core Team
[   43.694874] snd_hda_intel 0000:00:1b.0: PCI INT A -> GSI 21 (level, low) -> IRQ 21
[   43.694962] snd_hda_intel 0000:00:1b.0: irq 43 for MSI/MSI-X
[   43.695004] snd_hda_intel 0000:00:1b.0: setting latency timer to 64
[   43.695354] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   43.746706] init: Failed to spawn smbd main process: unable to execute: No such file or directory
[   43.827959] psmouse serio1: synaptics: Touchpad model: 1, fw: 6.2, id: 0x180b1, caps: 0xa04713/0x200000/0x0
[   43.866818] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input9
[   43.889108] input: HDA Intel Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   43.889379] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input11
[   43.934564] init: failsafe main process (1232) killed by TERM signal
[   44.035803] input: Dell WMI hotkeys as /devices/virtual/input/input12
[   44.064115] init: macchanger pre-start process (1314) terminated with status 1
[   44.239874] cfg80211: Ignoring regulatory request Set by core since the driver uses its own custom regulatory domain
[   44.239881] cfg80211: World regulatory domain updated:
[   44.239884] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   44.239889] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.239893] cfg80211:     (2457000 KHz - 2482000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   44.239898] cfg80211:     (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[   44.239902] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.239906] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   44.350999] init: kdm main process (1461) killed by TERM signal
[   44.585722] iwl3945 0000:0b:00.0: loaded firmware version 15.32.2.9
[   44.640034] vboxdrv: Found 2 processor cores.
[   44.643472] vboxdrv: fAsync=1 offMin=0xc50d8e2c offMax=0xc50d8e2c
[   44.643585] vboxdrv: TSC mode is 'asynchronous', kernel timer mode is 'normal'.
[   44.643588] vboxdrv: Successfully loaded version 4.1.30 (interface 0x00190000).
[   44.656313] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.656703] ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   44.666586] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.668295] ADDRCONF(NETDEV_UP): eth0: link is not ready
[   44.864589] vboxpci: IOMMU not found (not registered)
[   45.520298] [drm] Changing LVDS panel from (-hsync, -vsync) to (+hsync, +vsync)
[   46.834865] uhci_hcd 0000:00:1d.0: PCI INT A disabled
[   46.841795] uhci_hcd 0000:00:1d.3: PCI INT D disabled
[   46.856448] ehci_hcd 0000:00:1d.7: PCI INT A disabled
[   46.856499] ehci_hcd 0000:00:1d.7: PME# enabled
[   47.124063] ehci_hcd 0000:00:1d.7: BAR 0: set to [mem 0xffa80000-0xffa803ff] (PCI address [0xffa80000-0xffa803ff])
[   47.124088] ehci_hcd 0000:00:1d.7: restoring config space at offset 0xf (was 0x100, writing 0x109)
[   47.124118] ehci_hcd 0000:00:1d.7: restoring config space at offset 0x1 (was 0x2900000, writing 0x2900102)
[   47.126396] ehci_hcd 0000:00:1d.7: PME# disabled
[   47.126412] ehci_hcd 0000:00:1d.7: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   47.126421] ehci_hcd 0000:00:1d.7: setting latency timer to 64
[   47.179929] uhci_hcd 0000:00:1d.0: PCI INT A -> GSI 20 (level, low) -> IRQ 20
[   47.179942] uhci_hcd 0000:00:1d.0: setting latency timer to 64
[   47.231618] uhci_hcd 0000:00:1d.3: PCI INT D -> GSI 23 (level, low) -> IRQ 23
[   47.231631] uhci_hcd 0000:00:1d.3: setting latency timer to 64
[   47.470855] init: plymouth-stop pre-start process (2434) terminated with status 1
[   50.210466] wlan0: authenticate with 00:1f:90:ba:c3:9c (try 1)
[   50.212200] wlan0: authenticated
[   50.212656] wlan0: associate with 00:1f:90:ba:c3:9c (try 1)
[   50.215021] wlan0: RX AssocResp from 00:1f:90:ba:c3:9c (capab=0x431 status=0 aid=3)
[   50.215028] wlan0: associated
[   50.216640] ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[   50.216729] cfg80211: Calling CRDA for country: US
[   50.233314] cfg80211: Updating information on frequency 2412 MHz for a 20 MHz width channel with regulatory rule:
[   50.233321] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233325] cfg80211: Updating information on frequency 2417 MHz for a 20 MHz width channel with regulatory rule:
[   50.233330] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233334] cfg80211: Updating information on frequency 2422 MHz for a 20 MHz width channel with regulatory rule:
[   50.233338] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233342] cfg80211: Updating information on frequency 2427 MHz for a 20 MHz width channel with regulatory rule:
[   50.233347] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233351] cfg80211: Updating information on frequency 2432 MHz for a 20 MHz width channel with regulatory rule:
[   50.233355] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233359] cfg80211: Updating information on frequency 2437 MHz for a 20 MHz width channel with regulatory rule:
[   50.233364] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233368] cfg80211: Updating information on frequency 2442 MHz for a 20 MHz width channel with regulatory rule:
[   50.233372] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233376] cfg80211: Updating information on frequency 2447 MHz for a 20 MHz width channel with regulatory rule:
[   50.233381] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233384] cfg80211: Updating information on frequency 2452 MHz for a 20 MHz width channel with regulatory rule:
[   50.233389] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233393] cfg80211: Updating information on frequency 2457 MHz for a 20 MHz width channel with regulatory rule:
[   50.233397] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233401] cfg80211: Updating information on frequency 2462 MHz for a 20 MHz width channel with regulatory rule:
[   50.233406] cfg80211: 2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233410] cfg80211: Updating information on frequency 5180 MHz for a 20 MHz width channel with regulatory rule:
[   50.233414] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233418] cfg80211: Updating information on frequency 5200 MHz for a 20 MHz width channel with regulatory rule:
[   50.233423] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233427] cfg80211: Updating information on frequency 5220 MHz for a 20 MHz width channel with regulatory rule:
[   50.233431] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233435] cfg80211: Updating information on frequency 5240 MHz for a 20 MHz width channel with regulatory rule:
[   50.233439] cfg80211: 5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233443] cfg80211: Updating information on frequency 5260 MHz for a 20 MHz width channel with regulatory rule:
[   50.233448] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233452] cfg80211: Updating information on frequency 5280 MHz for a 20 MHz width channel with regulatory rule:
[   50.233456] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233460] cfg80211: Updating information on frequency 5300 MHz for a 20 MHz width channel with regulatory rule:
[   50.233465] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233469] cfg80211: Updating information on frequency 5320 MHz for a 20 MHz width channel with regulatory rule:
[   50.233473] cfg80211: 5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233477] cfg80211: Updating information on frequency 5745 MHz for a 20 MHz width channel with regulatory rule:
[   50.233481] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233485] cfg80211: Updating information on frequency 5765 MHz for a 20 MHz width channel with regulatory rule:
[   50.233490] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233494] cfg80211: Updating information on frequency 5785 MHz for a 20 MHz width channel with regulatory rule:
[   50.233498] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233502] cfg80211: Updating information on frequency 5805 MHz for a 20 MHz width channel with regulatory rule:
[   50.233507] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233511] cfg80211: Updating information on frequency 5825 MHz for a 20 MHz width channel with regulatory rule:
[   50.233515] cfg80211: 5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   50.233519] cfg80211: Regulatory domain changed to country: US
[   50.233522] cfg80211:     (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[   50.233527] cfg80211:     (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2700 mBm)
[   50.233532] cfg80211:     (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 1700 mBm)
[   50.233536] cfg80211:     (5250000 KHz - 5330000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233540] cfg80211:     (5490000 KHz - 5600000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233544] cfg80211:     (5650000 KHz - 5710000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[   50.233548] cfg80211:     (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 3000 mBm)
[   53.057510] init: Failed to spawn nmbd main process: unable to execute: No such file or directory
[   61.184057] wlan0: no IPv6 routers present
[   94.920136] usb 1-1: new high-speed USB device number 3 using ehci_hcd
[   95.102140] Initializing USB Mass Storage driver...
[   95.108062] scsi2 : usb-storage 1-1:1.0
[   95.108213] usbcore: registered new interface driver usb-storage
[   95.108217] USB Mass Storage support registered.
[   96.109448] scsi 2:0:0:0: Direct-Access     SanDisk  Cruzer           1.19 PQ: 0 ANSI: 5
[   96.111690] sd 2:0:0:0: Attached scsi generic sg2 type 0
[   96.115631] sd 2:0:0:0: [sdb] 15633408 512-byte logical blocks: (8.00 GB/7.45 GiB)
[   96.116864] sd 2:0:0:0: [sdb] Write Protect is off
[   96.116875] sd 2:0:0:0: [sdb] Mode Sense: 43 00 00 00
[   96.118121] sd 2:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[   96.127910]  sdb: sdb1 sdb2
[   96.130871] sd 2:0:0:0: [sdb] Attached SCSI removable disk
[  128.134686] EXT4-fs (sdb2): warning: maximal mount count reached, running e2fsck is recommended
[  128.136332] EXT4-fs (sdb2): mounted filesystem with ordered data mode. Opts: (null)
[  128.252862] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  253.277572] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  278.653602] WARNING! power/level is deprecated; use power/control instead
[  278.736057] usb 1-1: USB disconnect, device number 3
[  344.764082] usb 1-3: new high-speed USB device number 4 using ehci_hcd
[  344.901122] scsi3 : usb-storage 1-3:1.0
[  345.901221] scsi 3:0:0:0: Direct-Access     SanDisk  Cruzer           1.01 PQ: 0 ANSI: 2
[  345.903538] sd 3:0:0:0: Attached scsi generic sg2 type 0
[  345.906264] sd 3:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB)
[  345.907889] sd 3:0:0:0: [sdb] Write Protect is off
[  345.907900] sd 3:0:0:0: [sdb] Mode Sense: 03 00 00 00
[  345.908750] sd 3:0:0:0: [sdb] No Caching mode page found
[  345.908759] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  345.912379] sd 3:0:0:0: [sdb] No Caching mode page found
[  345.912390] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  345.916295]  sdb: sdb1
[  345.919503] sd 3:0:0:0: [sdb] No Caching mode page found
[  345.919514] sd 3:0:0:0: [sdb] Assuming drive cache: write through
[  345.919522] sd 3:0:0:0: [sdb] Attached SCSI removable disk
[  378.281668] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  492.000206] CE: hpet increased min_delta_ns to 20113 nsec
[  503.285942] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  628.289976] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  753.293872] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[  878.297960] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1003.301837] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1128.305865] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1253.309861] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1378.313782] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1503.317776] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1628.321696] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1753.325689] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 1878.329613] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2003.333564] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2128.337503] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2135.889963] sdb: detected capacity change from 32015679488 to 0
[ 2227.068145] usb 1-3: USB disconnect, device number 4
[ 2231.956107] usb 1-1: new high-speed USB device number 5 using ehci_hcd
[ 2232.093211] scsi4 : usb-storage 1-1:1.0
[ 2233.093097] scsi 4:0:0:0: Direct-Access     SanDisk  Cruzer           1.01 PQ: 0 ANSI: 2
[ 2233.095392] sd 4:0:0:0: Attached scsi generic sg2 type 0
[ 2233.098009] sd 4:0:0:0: [sdb] 62530624 512-byte logical blocks: (32.0 GB/29.8 GiB)
[ 2233.099637] sd 4:0:0:0: [sdb] Write Protect is off
[ 2233.099648] sd 4:0:0:0: [sdb] Mode Sense: 03 00 00 00
[ 2233.100497] sd 4:0:0:0: [sdb] No Caching mode page found
[ 2233.100506] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.104758] sd 4:0:0:0: [sdb] No Caching mode page found
[ 2233.104769] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.108191]  sdb: sdb1
[ 2233.111126] sd 4:0:0:0: [sdb] No Caching mode page found
[ 2233.111137] sd 4:0:0:0: [sdb] Assuming drive cache: write through
[ 2233.111146] sd 4:0:0:0: [sdb] Attached SCSI removable disk
[ 2253.341438] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2378.345412] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2503.349289] [UFW BLOCK] IN=wlan0 OUT= MAC=01:00:5e:00:00:01:00:1f:90:96:5b:b1:08:00 SRC=192.168.1.1 DST=224.0.0.1 LEN=36 TOS=0x00 PREC=0xC0 TTL=1 ID=0 DF PROTO=2 
[ 2684.712101] usb 1-1: USB disconnect, device number 5
MM061:~$ 


```


Well, what do you think?

---

### Post by PDA1 on 2014-01-16
> **Dave_L said:**
> Try:

```
sudo mount /dev/sdb1 /media/usb
```


Ok, that works to remount the drive. But, the problem remains if it's "safely removed".

Thanks for the help.

---

### Post by steeldriver on 2014-01-16
Remember that plugable device handling is done via udev / udisks, not traditional mounts. The trouble is that once you do a 'safely remove', the device block file is gone from the system - and neither restarting the udev daemon nor reloading rules via udevadm seems to rediscover it. There are some references on the web to simulating unplug/replug by changing the USB bus power level, however newer kernels appear to have removed this option (the supported power levels are now only 'on' or 'auto' - no 'suspend').

---

