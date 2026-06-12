---
title: "Very high CPU usage during video playback"
date: 2015-05-15
forum: General Help
---

### Post by kumareshy on 2015-05-15
Hello everybody,
        I have this strange issue in ubuntu 14.04 and 14.10. I have very high CPU usage whenever I play online videos ( around 60-70% ) and even when I play offline videos ( 35-40 % ). My CPU load is hovering around 20% on idle as per system monitor. top shows that compiz uses around 14-20% on idle. The CPU usage spikes like crazy whenever I do anything, even opening a simple web browser. But the system is extremely fast and responsive with no hanging. I have sub pixel anti aliasing enabled, but even setting it to normal grayscale anti aliasing doesn't reduce the CPU usage much. I'm using the open source Xorg drivers provided by ubuntu. Anything that is graphically intensive ( lot of images ) spikes my CPU usage. Is this normal or is there something wrong ?

My specs
Intel core i7 3770 ( non k )
AMD Radeon HD 7850
4 GB ram

Edit: I have solved the issue and posted the solution on page 2. It will work for you if you have installed the default open source drivers for an amd card.

---

### Post by dino99 on 2015-05-15
With such hardware you should not get cpu spikes. So you might miss some video plugins to get a normal reading. It's time to check your logs to find some usefull warnings/errors (dmesg, xorg.0.log first)

---

### Post by SeijiSensei on 2015-05-15
Have you installed the [proprietary driver]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") for your AMD/ATI card?  That should make a big difference.

---

### Post by Vladlenin5000 on 2015-05-15
I would say it is normal for Radeon which isn't properly optimized for some newer chips.
An interesting project would be to compare the performance with proprietary AMD drivers but you may have a reason for staying with the open source driver. I would use AMD's for sure but I would also upgrade it to at least 8GB, install Steam and run a lot of modern and demanding games.

---

### Post by monkeybrain20122 on 2015-05-15
You need to enable vdpau to use hardware acceleration for video decoding in your video player. The video players that are vdpau capable are vlc,  smplayer with mplayer, mplayer 2 or mpv as backend, mpv, gnome-mplayer and other players that use mplayer/mplayer2 as backend. Totem and other gstreamer based video player wouldn't work. If you are using one of the vdpau capable video player, go to preferences and set hardware decoding to vdpau (it is not enabled by default)

 Make sure the package mesa-vdpau-drivers is installed. If you have up to date open driver (say in Ubuntu 15.04) you shouldn't need the proprietary driver for smooth video playback. 

Edited: the open source AMD drivers now use vdpau for hardware decoding, not sure about fglrx. Is there anyone other than intel still uses vaapi?

---

### Post by monkeybrain20122 on 2015-05-15
> **SeijiSensei said:**
> Have you installed the [proprietary driver]("https://help.ubuntu.com/community/BinaryDriverHowto/AMD") for your AMD/ATI card?  That should make a big difference.

The difference between the proprietary and open driver is not that much except may be for some very new cards and some special use cases. I find the open AMD driver a lot smoother and problem free. My experience with fglrx is not good It always has some odd artefacts, one thing or the other does not work and kernel updates frequently breaks it,-- Nvidia blob's survive updates with no issues. Gamers may need fglrx to squeeze a few more fps out of the hardware, but for other users it probably isn't worth the troubles. I am not saying this for ideological reasons, if OP has a Nvidia card I would recommend the proprietary driver.

---

### Post by kumareshy on 2015-05-16
Here's my dmesg output.
```
[    2.027430] [drm] radeon kernel modesetting enabled.
[    2.038499] checking generic (e0000000 300000) vs hw (e0000000 10000000)
[    2.038500] fb: switching to radeondrmfb from VESA VGA
[    2.049255] Console: switching to colour dummy device 80x25
[    2.049528] [drm] initializing kernel modesetting (PITCAIRN 0x1002:0x6819 0x1458:0x2553).
[    2.049544] [drm] register mmio base: 0xF7E00000
[    2.049545] [drm] register mmio size: 262144
[    2.049589] ATOM BIOS: GV
[    2.049635] radeon 0000:01:00.0: VRAM: 2048M 0x0000000000000000 - 0x000000007FFFFFFF (2048M used)
[    2.049637] radeon 0000:01:00.0: GTT: 1024M 0x0000000080000000 - 0x00000000BFFFFFFF
[    2.049638] [drm] Detected VRAM RAM=2048M, BAR=256M
[    2.049639] [drm] RAM width 256bits DDR
[    2.049725] [TTM] Zone  kernel: Available graphics memory: 2007038 kiB
[    2.049726] [TTM] Initializing pool allocator
[    2.049729] [TTM] Initializing DMA pool allocator
[    2.049739] [drm] radeon: 2048M of VRAM memory ready
[    2.049740] [drm] radeon: 1024M of GTT memory ready.
[    2.049746] [drm] Loading PITCAIRN Microcode
[    2.049791] [drm] radeon/PITCAIRN_mc2.bin: 31100 bytes
[    2.049808] [drm] Internal thermal controller with fan control
[    2.049837] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[    2.056821] [drm] radeon: dpm initialized
[    2.056877] [drm] GART: num cpu pages 262144, num gpu pages 262144
[    2.057271] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[    2.057275] [drm] PCIE gen 3 link speeds already enabled
[    2.066106] [drm] PCIE GART of 1024M enabled (table at 0x0000000000276000).
[    2.066205] radeon 0000:01:00.0: WB enabled
[    2.066207] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880034d6cc00
[    2.066209] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff880034d6cc04
[    2.066211] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff880034d6cc08
[    2.066213] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880034d6cc0c
[    2.066215] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff880034d6cc10
[    2.066473] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[    2.066505] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[    2.066854] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90004eb5a18
[    2.066857] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    2.066859] [drm] Driver supports precise vblank timestamp query.
[    2.066861] radeon 0000:01:00.0: radeon: MSI limited to 32-bit
[    2.066878] radeon 0000:01:00.0: irq 44 for MSI/MSI-X
[    2.066884] radeon 0000:01:00.0: radeon: using MSI.
[    2.066907] [drm] radeon: irq initialized.
[    2.067145] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.067147] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.067150] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.067635] ata6.00: ATA-8: ST1000DM003-1CH162, CC46, max UDMA/133
[    2.067638] ata6.00: 1953525168 sectors, multi 16: LBA48 NCQ (depth 31/32), AA
[    2.068198] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.068200] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.068203] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.068671] ata6.00: configured for UDMA/133
[    2.069897] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.069899] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.069901] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.071057] ata5.00: ATAPI: HL-DT-ST DVDRAM GH24NS95, RN01, max UDMA/133
[    2.072809] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[    2.072811] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[    2.072813] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[    2.073792] ata5.00: configured for UDMA/133
[    2.075955] scsi 4:0:0:0: CD-ROM            HL-DT-ST DVDRAM GH24NS95  RN01 PQ: 0 ANSI: 5
[    2.106587] sr0: scsi3-mmc drive: 48x/12x writer dvd-ram cd/rw xa/form2 cdda tray
[    2.106590] cdrom: Uniform CD-ROM driver Revision: 3.20
[    2.106729] sr 4:0:0:0: Attached scsi CD-ROM sr0
[    2.106803] sr 4:0:0:0: Attached scsi generic sg0 type 5
[    2.107001] scsi 5:0:0:0: Direct-Access     ATA      ST1000DM003-1CH1 CC46 PQ: 0 ANSI: 5
[    2.107304] sd 5:0:0:0: Attached scsi generic sg1 type 0
[    2.107315] sd 5:0:0:0: [sda] 1953525168 512-byte logical blocks: (1.00 TB/931 GiB)
[    2.107318] sd 5:0:0:0: [sda] 4096-byte physical blocks
[    2.107439] sd 5:0:0:0: [sda] Write Protect is off
[    2.107443] sd 5:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    2.107496] sd 5:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    2.142162]  sda: sda1 sda2 sda3 sda4 < sda5 >
[    2.142770] sd 5:0:0:0: [sda] Attached SCSI disk
[    2.144011] usb 1-1.3: New USB device found, idVendor=0bc2, idProduct=2320
[    2.144015] usb 1-1.3: New USB device strings: Mfr=2, Product=3, SerialNumber=1
[    2.144018] usb 1-1.3: Product: Expansion
[    2.144021] usb 1-1.3: Manufacturer: Seagate
[    2.144023] usb 1-1.3: SerialNumber: NA45QJJM
[    2.214662] usb 1-1.4: new full-speed USB device number 6 using ehci-pci
[    2.223570] [drm] ring test on 0 succeeded in 4 usecs
[    2.223574] [drm] ring test on 1 succeeded in 1 usecs
[    2.223578] [drm] ring test on 2 succeeded in 1 usecs
[    2.223588] [drm] ring test on 3 succeeded in 6 usecs
[    2.223596] [drm] ring test on 4 succeeded in 5 usecs
[    2.284427] e1000e 0000:00:19.0 eth0: registered PHC clock
[    2.284439] e1000e 0000:00:19.0 eth0: (PCI Express:2.5GT/s:Width x1) 70:54:d2:c4:5c:ab
[    2.284441] e1000e 0000:00:19.0 eth0: Intel(R) PRO/1000 Network Connection
[    2.284476] e1000e 0000:00:19.0 eth0: MAC: 10, PHY: 11, PBA No: FFFFFF-0FF
[    2.312602] usb 1-1.4: New USB device found, idVendor=045e, idProduct=028e
[    2.312605] usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[    2.312607] usb 1-1.4: Product: Controller
[    2.312608] usb 1-1.4: Manufacturer: ©Microsoft Corporation
[    2.312609] usb 1-1.4: SerialNumber: 0968AE6
[    2.317183] hidraw: raw HID events driver (C) Jiri Kosina
[    2.317977] usb-storage 1-1.3:1.0: USB Mass Storage device detected
[    2.318055] scsi6 : usb-storage 1-1.3:1.0
[    2.318129] usbcore: registered new interface driver usb-storage
[    2.319603] usbcore: registered new interface driver uas
[    2.323262] usbcore: registered new interface driver usbhid
[    2.323264] usbhid: USB HID core driver
[    2.324714] input: USB Optical Mouse as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.1/1-1.1:1.0/0003:0461:4D22.0001/input/input5
[    2.324802] hid-generic 0003:0461:4D22.0001: input,hidraw0: USB HID v1.11 Mouse [USB Optical Mouse] on usb-0000:00:1a.0-1.1/input0
[    2.324878] input: Dell Dell USB Entry Keyboard as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.2/1-1.2:1.0/0003:413C:2107.0002/input/input6
[    2.324937] hid-generic 0003:413C:2107.0002: input,hidraw1: USB HID v1.10 Keyboard [Dell Dell USB Entry Keyboard] on usb-0000:00:1a.0-1.2/input0
[    2.409270] [drm] ring test on 5 succeeded in 3 usecs
[    2.409276] [drm] UVD initialized successfully.
[    2.409438] [drm] ib test on ring 0 succeeded in 0 usecs
[    2.409489] [drm] ib test on ring 1 succeeded in 0 usecs
[    2.409539] [drm] ib test on ring 2 succeeded in 0 usecs
[    2.409585] [drm] ib test on ring 3 succeeded in 0 usecs
[    2.409630] [drm] ib test on ring 4 succeeded in 0 usecs
[    2.522823] usb 2-1-port1: over-current condition
[    2.560611] [drm] ib test on ring 5 succeeded
[    2.561147] [drm] Radeon Display Connectors
[    2.561149] [drm] Connector 0:
[    2.561150] [drm]   DP-1
[    2.561151] [drm]   HPD4
[    2.561152] [drm]   DDC: 0x6530 0x6530 0x6534 0x6534 0x6538 0x6538 0x653c 0x653c
[    2.561153] [drm]   Encoders:
[    2.561154] [drm]     DFP1: INTERNAL_UNIPHY2
[    2.561155] [drm] Connector 1:
[    2.561156] [drm]   DP-2
[    2.561157] [drm]   HPD5
[    2.561158] [drm]   DDC: 0x6540 0x6540 0x6544 0x6544 0x6548 0x6548 0x654c 0x654c
[    2.561159] [drm]   Encoders:
[    2.561160] [drm]     DFP2: INTERNAL_UNIPHY2
[    2.561161] [drm] Connector 2:
[    2.561162] [drm]   HDMI-A-1
[    2.561163] [drm]   HPD1
[    2.561164] [drm]   DDC: 0x6550 0x6550 0x6554 0x6554 0x6558 0x6558 0x655c 0x655c
[    2.561165] [drm]   Encoders:
[    2.561166] [drm]     DFP3: INTERNAL_UNIPHY1
[    2.561167] [drm] Connector 3:
[    2.561167] [drm]   DVI-I-1
[    2.561168] [drm]   HPD6
[    2.561169] [drm]   DDC: 0x6580 0x6580 0x6584 0x6584 0x6588 0x6588 0x658c 0x658c
[    2.561170] [drm]   Encoders:
[    2.561171] [drm]     DFP4: INTERNAL_UNIPHY
[    2.561172] [drm]     CRT1: INTERNAL_KLDSCP_DAC1
[    2.574789] Switched to clocksource tsc
[    2.610667] [drm] fb mappable at 0xE0478000
[    2.610668] [drm] vram apper at 0xE0000000
[    2.610669] [drm] size 4325376
[    2.610670] [drm] fb depth is 24
[    2.610671] [drm]    pitch is 5632
[    2.610766] fbcon: radeondrmfb (fb0) is primary device
[    2.619156] Console: switching to colour frame buffer device 170x48
[    2.620406] radeon 0000:01:00.0: fb0: radeondrmfb frame buffer device
[    2.620419] radeon 0000:01:00.0: registered panic notifier
[    2.630809] [drm] Initialized radeon 2.39.0 20080528 for 0000:01:00.0 on minor 0
[    2.730889] usb 2-1-port2: over-current condition
[    2.939031] usb 2-1-port3: over-current condition
[    3.147124] usb 2-1-port4: over-current condition
[    3.315886] scsi 6:0:0:0: Direct-Access     Seagate  Expansion        0608 PQ: 0 ANSI: 6
[    3.316157] sd 6:0:0:0: Attached scsi generic sg2 type 0
[    3.316682] sd 6:0:0:0: [sdb] 976773167 512-byte logical blocks: (500 GB/465 GiB)
[    3.317879] sd 6:0:0:0: [sdb] Write Protect is off
[    3.317892] sd 6:0:0:0: [sdb] Mode Sense: 4f 00 00 00
[    3.318978] sd 6:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[    4.524301]  sdb: sdb1
[    4.530060] sd 6:0:0:0: [sdb] Attached SCSI disk
[    4.703687] floppy0: no floppy controllers found
[    4.760199] random: nonblocking pool is initialized
[    4.859595] EXT4-fs (sda5): mounted filesystem with ordered data mode. Opts: (null)
[   16.069741] EXT4-fs (sda5): re-mounted. Opts: errors=remount-ro
[   16.502900] systemd-udevd[446]: starting version 208
[   16.565983] lp: driver loaded but no devices found
[   16.572061] ppdev: user-space parallel port driver
[   16.577245] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   16.581014] mei_me 0000:00:16.0: irq 45 for MSI/MSI-X
[   16.584101] ACPI Warning: SystemIO range 0x0000000000000428-0x000000000000042f conflicts with OpRegion 0x0000000000000400-0x000000000000047f (\PMIO) (20140424/utaddress-258)
[   16.584106] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.584109] ACPI Warning: SystemIO range 0x0000000000000540-0x000000000000054f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   16.584111] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.584111] ACPI Warning: SystemIO range 0x0000000000000530-0x000000000000053f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   16.584113] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.584113] ACPI Warning: SystemIO range 0x0000000000000500-0x000000000000052f conflicts with OpRegion 0x0000000000000500-0x0000000000000563 (\GPIO) (20140424/utaddress-258)
[   16.584115] ACPI: If an ACPI driver is available for this device, you should use it instead of the native driver
[   16.584116] lpc_ich: Resource conflict(s) found affecting gpio_ich
[   16.608709] AVX version of gcm_enc/dec engaged.
[   16.614295] snd_hda_intel 0000:00:1b.0: irq 46 for MSI/MSI-X
[   16.614365] snd_hda_intel 0000:01:00.1: Handle VGA-switcheroo audio client
[   16.614367] snd_hda_intel 0000:01:00.1: Force to non-snoop mode
[   16.614970] Adding 4194300k swap on /swapfile.  Priority:-1 extents:7 across:6553596k FS
[   16.617377] snd_hda_intel 0000:01:00.1: irq 47 for MSI/MSI-X
[   16.623338] intel_rapl: Found RAPL domain package
[   16.623340] intel_rapl: Found RAPL domain core
[   16.628193] input: HDA ATI HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input7
[   16.628292] input: HDA ATI HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input8
[   16.628377] input: HDA ATI HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input9
[   16.628438] input: HDA ATI HDMI HDMI/DP,pcm=9 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input10
[   16.628863] sound hdaudioC0D0: autoconfig: line_outs=1 (0x14/0x0/0x0/0x0/0x0) type:line
[   16.628865] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   16.628868] sound hdaudioC0D0:    hp_outs=1 (0x1b/0x0/0x0/0x0/0x0)
[   16.628869] sound hdaudioC0D0:    mono: mono_out=0x0
[   16.628870] sound hdaudioC0D0:    dig-out=0x11/0x0
[   16.628872] sound hdaudioC0D0:    inputs:
[   16.628874] sound hdaudioC0D0:      Front Mic=0x19
[   16.628876] sound hdaudioC0D0:      Rear Mic=0x18
[   16.628878] sound hdaudioC0D0:      Line=0x1a
[   16.638916] input: HDA ATI HDMI HDMI/DP,pcm=10 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input11
[   16.638994] input: HDA ATI HDMI HDMI/DP,pcm=11 as /devices/pci0000:00/0000:00:01.0/0000:01:00.1/sound/card1/input12
[   16.639340] input: HDA Intel PCH Rear Mic as /devices/pci0000:00/0000:00:1b.0/sound/card0/input13
[   16.639431] input: HDA Intel PCH Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input14
[   16.639495] input: HDA Intel PCH Line Out as /devices/pci0000:00/0000:00:1b.0/sound/card0/input15
[   16.641245] systemd-udevd[477]: renamed network interface eth0 to eth1
[   17.072617] audit: type=1400 audit(1431756225.073:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=589 comm="apparmor_parser"
[   17.072622] audit: type=1400 audit(1431756225.073:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=589 comm="apparmor_parser"
[   17.072624] audit: type=1400 audit(1431756225.073:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=589 comm="apparmor_parser"
[   17.072630] audit: type=1400 audit(1431756225.073:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=587 comm="apparmor_parser"
[   17.072635] audit: type=1400 audit(1431756225.073:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=587 comm="apparmor_parser"
[   17.072637] audit: type=1400 audit(1431756225.073:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=587 comm="apparmor_parser"
[   17.971691] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input16
[   17.971744] usbcore: registered new interface driver xpad
[   18.637041] init: Error while reading from descriptor: Broken pipe
[   18.637854] init: failsafe main process (791) killed by TERM signal
[   19.358922] audit: type=1400 audit(1431756227.361:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=870 comm="apparmor_parser"
[   19.358928] audit: type=1400 audit(1431756227.361:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="chromium" pid=870 comm="apparmor_parser"
[   19.359874] audit: type=1400 audit(1431756227.361:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=870 comm="apparmor_parser"
[   19.359878] audit: type=1400 audit(1431756227.361:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=870 comm="apparmor_parser"
[   19.590558] floppy0: no floppy controllers found
[   19.879127] init: cups main process (995) killed by HUP signal
[   19.879134] init: cups main process ended, respawning
[   19.993865] Bluetooth: Core ver 2.19
[   19.993874] NET: Registered protocol family 31
[   19.993875] Bluetooth: HCI device and connection manager initialized
[   19.993879] Bluetooth: HCI socket layer initialized
[   19.993880] Bluetooth: L2CAP socket layer initialized
[   19.993885] Bluetooth: SCO socket layer initialized
[   20.027876] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   20.027877] Bluetooth: BNEP filters: protocol multicast
[   20.027880] Bluetooth: BNEP socket layer initialized
[   20.030782] Bluetooth: RFCOMM TTY layer initialized
[   20.030786] Bluetooth: RFCOMM socket layer initialized
[   20.030790] Bluetooth: RFCOMM ver 1.11
[   21.328912] systemd-logind[1107]: New seat seat0.
[   21.338428] systemd-logind[1107]: Watching system buttons on /dev/input/event1 (Power Button)
[   21.338463] systemd-logind[1107]: Watching system buttons on /dev/input/event0 (Power Button)
[   21.543578] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   21.647540] e1000e 0000:00:19.0: irq 43 for MSI/MSI-X
[   21.725875] init: samba-ad-dc main process (1154) terminated with status 1
[   24.997042] init: gdm main process (1390) killed by TERM signal
[   25.690528] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[   25.690532] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO
[   26.480761] systemd-logind[1107]: Failed to start unit user@1000.service: Unknown unit: user@1000.service
[   26.480767] systemd-logind[1107]: Failed to start user service: Unknown unit: user@1000.service
[   26.483470] systemd-logind[1107]: New session c1 of user kumaresh.
[   26.483486] systemd-logind[1107]: Linked /tmp/.X11-unix/X0 to /run/user/1000/X11-display.
[   32.467932] init: /etc/init/plymouth-upstart-bridge.conf:18: Unknown stanza
[  637.288606] e1000e: eth1 NIC Link is Down
[  637.660709] init: /etc/init/plymouth-upstart-bridge.conf:18: Unknown stanza
[  637.836530] init: /etc/init/plymouth-upstart-bridge.conf:18: Unknown stanza
[  637.998508] PM: Syncing filesystems ... done.
[  638.153509] PM: Preparing system for mem sleep
[  638.203657] Freezing user space processes ... (elapsed 0.001 seconds) done.
[  638.205119] Freezing remaining freezable tasks ... (elapsed 0.001 seconds) done.
[  638.206189] PM: Entering mem sleep
[  638.206246] Suspending console(s) (use no_console_suspend to debug)
[  638.206407] sd 5:0:0:0: [sda] Synchronizing SCSI cache
[  638.206606] sd 5:0:0:0: [sda] Stopping disk
[  638.209524] serial 00:05: disabled
[  639.023512] PM: suspend of devices complete after 816.796 msecs
[  639.023710] PM: late suspend of devices complete after 0.197 msecs
[  639.024090] ehci-pci 0000:00:1d.0: System wakeup enabled by ACPI
[  639.024109] ehci-pci 0000:00:1a.0: System wakeup enabled by ACPI
[  639.039439] PM: noirq suspend of devices complete after 15.720 msecs
[  639.039837] ACPI: Preparing to enter system sleep state S3
[  639.039984] PM: Saving platform NVS memory
[  639.040564] Disabling non-boot CPUs ...
[  639.040614] intel_pstate CPU 1 exiting
[  639.041764] kvm: disabling virtualization on CPU1
[  639.143482] smpboot: CPU 1 is now offline
[  639.143712] intel_pstate CPU 2 exiting
[  639.144848] kvm: disabling virtualization on CPU2
[  639.247531] smpboot: CPU 2 is now offline
[  639.247764] intel_pstate CPU 3 exiting
[  639.248886] kvm: disabling virtualization on CPU3
[  639.351582] smpboot: CPU 3 is now offline
[  639.351808] intel_pstate CPU 4 exiting
[  639.352921] kvm: disabling virtualization on CPU4
[  639.455628] smpboot: CPU 4 is now offline
[  639.455861] intel_pstate CPU 5 exiting
[  639.455959] Broke affinity for irq 23
[  639.456963] kvm: disabling virtualization on CPU5
[  639.559670] smpboot: CPU 5 is now offline
[  639.559896] intel_pstate CPU 6 exiting
[  639.559984] Broke affinity for irq 42
[  639.560986] kvm: disabling virtualization on CPU6
[  639.663718] smpboot: CPU 6 is now offline
[  639.663934] intel_pstate CPU 7 exiting
[  639.665009] kvm: disabling virtualization on CPU7
[  639.767767] smpboot: CPU 7 is now offline
[  639.769125] ACPI: Low-level resume complete
[  639.769164] PM: Restoring platform NVS memory
[  639.769663] Enabling non-boot CPUs ...
[  639.769699] x86: Booting SMP configuration:
[  639.769700] smpboot: Booting Node 0 Processor 1 APIC 0x2
[  639.780948] kvm: enabling virtualization on CPU1
[  639.783193] Intel pstate controlling: cpu 1
[  639.783235] CPU1 is up
[  639.783251] smpboot: Booting Node 0 Processor 2 APIC 0x4
[  639.794510] kvm: enabling virtualization on CPU2
[  639.796705] Intel pstate controlling: cpu 2
[  639.796744] CPU2 is up
[  639.796760] smpboot: Booting Node 0 Processor 3 APIC 0x6
[  639.808022] kvm: enabling virtualization on CPU3
[  639.810227] Intel pstate controlling: cpu 3
[  639.810265] CPU3 is up
[  639.810280] smpboot: Booting Node 0 Processor 4 APIC 0x1
[  639.821522] kvm: enabling virtualization on CPU4
[  639.823731] Intel pstate controlling: cpu 4
[  639.823763] CPU4 is up
[  639.823776] smpboot: Booting Node 0 Processor 5 APIC 0x3
[  639.835011] kvm: enabling virtualization on CPU5
[  639.837140] Intel pstate controlling: cpu 5
[  639.837174] CPU5 is up
[  639.837188] smpboot: Booting Node 0 Processor 6 APIC 0x5
[  639.848433] kvm: enabling virtualization on CPU6
[  639.850648] Intel pstate controlling: cpu 6
[  639.850679] CPU6 is up
[  639.850694] smpboot: Booting Node 0 Processor 7 APIC 0x7
[  639.861943] kvm: enabling virtualization on CPU7
[  639.864161] Intel pstate controlling: cpu 7
[  639.864193] CPU7 is up
[  639.870829] ACPI: Waking up from system sleep state S3
[  639.885688] ehci-pci 0000:00:1d.0: System wakeup disabled by ACPI
[  639.885812] ehci-pci 0000:00:1a.0: System wakeup disabled by ACPI
[  639.885875] PM: noirq resume of devices complete after 14.668 msecs
[  639.886044] PM: early resume of devices complete after 0.149 msecs
[  639.886075] mei_me 0000:00:16.0: irq 43 for MSI/MSI-X
[  639.886312] snd_hda_intel 0000:00:1b.0: irq 45 for MSI/MSI-X
[  639.886420] snd_hda_intel 0000:01:00.1: irq 46 for MSI/MSI-X
[  639.886927] serial 00:05: activated
[  639.890403] sd 5:0:0:0: [sda] Starting disk
[  639.896953] [drm] probing gen 2 caps for device 8086:151 = 261ad03/e
[  639.896955] [drm] PCIE gen 3 link speeds already enabled
[  639.899516] [drm] PCIE GART of 1024M enabled (table at 0x0000000000276000).
[  639.899621] radeon 0000:01:00.0: WB enabled
[  639.899622] radeon 0000:01:00.0: fence driver on ring 0 use gpu addr 0x0000000080000c00 and cpu addr 0xffff880034d6cc00
[  639.899623] radeon 0000:01:00.0: fence driver on ring 1 use gpu addr 0x0000000080000c04 and cpu addr 0xffff880034d6cc04
[  639.899624] radeon 0000:01:00.0: fence driver on ring 2 use gpu addr 0x0000000080000c08 and cpu addr 0xffff880034d6cc08
[  639.899625] radeon 0000:01:00.0: fence driver on ring 3 use gpu addr 0x0000000080000c0c and cpu addr 0xffff880034d6cc0c
[  639.899626] radeon 0000:01:00.0: fence driver on ring 4 use gpu addr 0x0000000080000c10 and cpu addr 0xffff880034d6cc10
[  639.900232] radeon 0000:01:00.0: fence driver on ring 5 use gpu addr 0x0000000000075a18 and cpu addr 0xffffc90004eb5a18
[  640.050949] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[  640.056282] [drm] ring test on 0 succeeded in 4 usecs
[  640.056285] [drm] ring test on 1 succeeded in 1 usecs
[  640.056288] [drm] ring test on 2 succeeded in 1 usecs
[  640.056297] [drm] ring test on 3 succeeded in 6 usecs
[  640.056304] [drm] ring test on 4 succeeded in 5 usecs
[  640.217620] ata5: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[  640.228981] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  640.228983] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  640.228984] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  640.241965] [drm] ring test on 5 succeeded in 3 usecs
[  640.241969] [drm] UVD initialized successfully.
[  640.242026] [drm] ib test on ring 0 succeeded in 0 usecs
[  640.242076] [drm] ib test on ring 1 succeeded in 0 usecs
[  640.242126] [drm] ib test on ring 2 succeeded in 0 usecs
[  640.242150] [drm] ib test on ring 3 succeeded in 0 usecs
[  640.242172] [drm] ib test on ring 4 succeeded in 0 usecs
[  640.250649] ata5.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  640.250650] ata5.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  640.250651] ata5.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  640.256399] ata5.00: configured for UDMA/133
[  640.393206] [drm] ib test on ring 5 succeeded
[  640.445007] PM: resume of devices complete after 558.704 msecs
[  640.445094] input: Microsoft X-Box 360 pad as /devices/pci0000:00/0000:00:1a.0/usb1/1-1/1-1.4/1-1.4:1.0/input/input20
[  640.445306] PM: Finishing wakeup.
[  640.445307] Restarting tasks ... 
[  640.445477] pci_bus 0000:03: Allocating resources
[  640.445497] pci 0000:02:00.0: bridge window [io  0x1000-0x0fff] to [bus 03] add_size 1000
[  640.445500] pci 0000:02:00.0: bridge window [mem 0x00100000-0x000fffff 64bit pref] to [bus 03] add_size 200000
[  640.445501] pci 0000:02:00.0: bridge window [mem 0x00100000-0x000fffff] to [bus 03] add_size 200000
[  640.445504] pci 0000:02:00.0: res[14]=[mem 0x00100000-0x000fffff] get_res_add_size add_size 200000
[  640.445505] pci 0000:02:00.0: res[15]=[mem 0x00100000-0x000fffff 64bit pref] get_res_add_size add_size 200000
[  640.445506] pci 0000:02:00.0: res[13]=[io  0x1000-0x0fff] get_res_add_size add_size 1000
[  640.445508] pci 0000:02:00.0: BAR 14: can't assign mem (size 0x200000)
[  640.445510] pci 0000:02:00.0: BAR 15: can't assign mem pref (size 0x200000)
[  640.445511] pci 0000:02:00.0: BAR 13: can't assign io (size 0x1000)
[  640.445513] pci 0000:02:00.0: BAR 14: can't assign mem (size 0x200000)
[  640.445514] pci 0000:02:00.0: BAR 15: can't assign mem pref (size 0x200000)
[  640.445515] pci 0000:02:00.0: BAR 13: can't assign io (size 0x1000)
[  640.445517] pci 0000:02:00.0: PCI bridge to [bus 03]
[  640.447980] done.
[  644.075409] ata6: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[  644.076042] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  644.076047] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  644.076051] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  644.077476] ata6.00: ACPI cmd ef/10:06:00:00:00:00 (SET FEATURES) succeeded
[  644.077478] ata6.00: ACPI cmd f5/00:00:00:00:00:00 (SECURITY FREEZE LOCK) filtered out
[  644.077480] ata6.00: ACPI cmd b1/c1:00:00:00:00:00 (DEVICE CONFIGURATION OVERLAY) filtered out
[  644.078174] ata6.00: configured for UDMA/133
[  644.271868] init: /etc/init/plymouth-upstart-bridge.conf:18: Unknown stanza
[  644.356664] init: /etc/init/plymouth-upstart-bridge.conf:18: Unknown stanza
[  644.438389] systemd-logind[1107]: Operation finished.
[  644.582153] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[  644.683751] e1000e 0000:00:19.0: irq 47 for MSI/MSI-X
[  647.306010] e1000e: eth1 NIC Link is Up 100 Mbps Full Duplex, Flow Control: Rx/Tx
[  647.306015] e1000e 0000:00:19.0 eth1: 10/100 speed: disabling TSO

```
Contrary to what it says, the boot did not take 647 seconds. It only took 32 seconds. I left it in suspend for some time. I am using the open source drivers and find no difference between them and the fglrx drivers other than the open source drivers are properly updated. I checked VLC media player preferences and it has the options automatic, vaapi or disabled. What other logs do you guys want ?

---

### Post by kumareshy on 2015-05-16
My general CPU usage is extremely high. I think it's because of the antialiasing work of compiz being offloaded to the cpu, just my theory. Look at the attached screenshot. The CPU usage spikes to that much just by me scrolling. It scrolls extremely fast and smooth. Video playback is extremely smooth. By the way, should I upgrade to 15.04 ?[ATTACH=CONFIG]261998[/ATTACH]

---

### Post by monkeybrain20122 on 2015-05-16
> **kumareshy said:**
> 
I checked VLC media player preferences and it has the options automatic, vaapi or disabled. What other logs do you guys want ?

Which version of VLC are you using?  If on 14.04 try upgrade vlc with this ppa [https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media](https://launchpad.net/~mc3man/+archive/ubuntu/trusty-media)

edited: actually Smplayer with any of the backends  is more efficient than vlc in vdpau decoding.

---

### Post by monkeybrain20122 on 2015-05-16
> **kumareshy said:**
> My general CPU usage is extremely high. I think it's because of the antialiasing work of compiz being offloaded to the cpu, just my theory. Look at the attached screenshot. The CPU usage spikes to that much just by me scrolling. 

To see what is eating your cpu, open the terminal and type 
```
top
```

Check the output. My compiz usage is around 3% when idle on a few machines with intel, Nvidia and Adm cards.

---

### Post by kumareshy on 2015-05-16
Yes, I have confirmed it with top. Here's my output screen. Compiz usage ranges from 150-200%. 
[ATTACH=CONFIG]262000[/ATTACH]

---

### Post by monkeybrain20122 on 2015-05-16
Hi, does it sound like this bug? [https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1268146](https://bugs.launchpad.net/ubuntu/+source/mesa/+bug/1268146)

If this describes your problem it is a bug in mesa. There are two options, either do a clean install of 15.04 which comes with current mesa (10.5) (Don't "upgrade", do a clean install) or upgrade mesa to 10.6 (beta) with this [https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa), which also has the up to date fglrx driver should you need it.

---

### Post by dino99 on 2015-05-16
in case you have installed some compiz packages, not installed by default, then it can be the main reason of such trouble.Only the default compiz packages are maintained nowadays; better to forget about all others.

---

### Post by kumareshy on 2015-05-16
Yes, you guys are right. That is the bug that is affecting me :D. I'll install the beta and report it here. Thank you all very much for helping me :D I already had that page in my software sources. How do I specifically install the beta mesa 10.6 ? Could you please give the instructions ? I don't want to mess up my system.

---

### Post by kumareshy on 2015-05-16
Yes, I have found the solution to the problem. Instead of installing beta mesa drivers, all I had to do is
```
sudo apt-get install xserver-xorg-video-ati
```.
I'll mark this thread as solved. Now my CPU usage is maxing out at 5-7% when watching full HD videos :D

---

