---
title: "Ubuntu 14.04 requires me to login twice"
date: 2015-12-02
forum: General Help
---

### Post by Oinos on 2015-12-02
So after I start my computer and enter my password, the desktop background gets distorted for a while and is actually drawn twice and after 5 or so seconds it just returns me to the login screen and again prompts me to enter my password. Only after I enter it for second time do I manage to actually log in. Also the computer is a bit slower than usual lately and it looks as if this coincided with the twice login problem. I have my doubts if this is due to a virus. How do I check if everything is correct?

---

### Post by Ricardo_Velasco on 2015-12-03
Cheers:

Lei could be your problem and that is your graphics card ..

Trafficking in recovery mode Ubuntu install drivers for your graphics card ..

Follow these steps, first install repositories:

> sudo apt-add-repository ppa:xorg-edgers/ppa

sudo apt-get update

Then check mark have graphic card and choose these commands to install the driver of yours :

Nvidia:
> 
sudo apt-get install nvidia-current nvidia-settings

ATI:

> sudo apt-get install xserver-xorg-video-ati

Intel:

> sudo apt-get install xserver-xorg-video-intel

---

### Post by QIII on 2015-12-03
I would recommend against rushing in to adding a PPA and installing a driver from there.  Drivers may be installed from the OEM's websites or the Ubuntu repo.

We don't even know what the OP's hardware is, and I can tell you that you have presented a very sketchy way to install the driver for AMD/ATI.

@Oinos:  PPA stands for "Personal Package Archive".  That is, someone like you or me maintains them.  This means that the contents are neither officially tested on Ubuntu nor guaranteed to be maintained.  Further, without knowing what is contained, you may unknowingly install dependencies that will cause problems with other software packages.  It is advisable to *avoid* PPAs to the greatest extent possible.

---

### Post by Bucky Ball on 2015-12-04
> **QIII said:**
> I would recommend against rushing in to adding a PPA and installing a driver from there.  Drivers may be installed from the OEM's websites or the Ubuntu repo.

We don't even know what the OP's hardware is, and I can tell you that you have presented a very sketchy way to install the driver for AMD/ATI.

+++1. Providing a supposed 'fix' without the required information can create a raft of other issues. :)

---

### Post by Oinos on 2015-12-06
I realised the login twice thing only happens when I have an external display connected so that ubutnu is shown on two displays. Still even with only one login it takes a few more seconds that it used to be and the computer is little bit slower. My graphics card is Intel® 945GM x86/MMX/SSE2.
Aren't there any quick prophylactic check routines?

---

### Post by Bucky Ball on 2015-12-06
Boot up. When it eventually gets to a desktop, before doing anything else, open a terminal and:

```
dmesg
```

Hit return and check for clues. You'll possibly find something near the end of the output pertaining to the issue. Post that output here between code tags (see last link in my signature).

I have two monitors and the laptop monitor works fine, normal speed, the attached monitor takes a little bit (a second or two) to 'catch up'. Apart from the double login issue, does this sound like you?

---

### Post by Oinos on 2015-12-07
> I have two monitors and the laptop monitor works fine, normal speed, the  attached monitor takes a little bit (a second or two) to 'catch up'.  Apart from the double login issue, does this sound like you? Mostly yes.


So I tried to find and copy every 'not found' and 'error' message, + all near the end.
```

....
[    1.421731] platform eisa.0: Probing EISA bus 0
[    1.421738] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.421742] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.421746] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.421750] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.421754] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.421758] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.421762] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.421766] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.421770] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.421774] platform eisa.0: EISA: Detected 0 cards
[    1.421807] cpufreq-nforce2: No nForce2 chipset.
[    1.421821] ledtrig-cpu: registered to indicate activity on CPUs
[    1.421843] PCCT header not found.
[    1.421845] ACPI PCC probe failed.
[    1.422059] TCP: cubic registered
.....
[    1.443011] EDD information not available.
[    1.443137] PM: Hibernation image not present or could not be loaded.
[    1.564716] ata1.00: ATA-6: TOSHIBA MK6008GAH, BU011A, max UDMA/100
[    1.564722] ata1.00: 117210240 sectors, multi 8: LBA48 
[    1.572478] ata1.00: configured for UDMA/100
[    1.685463] isapnp: No Plug & Play device found
[    1.685670] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6008GA 1A   PQ: 0 ANSI: 5
[    1.686066] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.686136] sd 0:0:0:0: [sda] Write Protect is off
[    1.686142] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.686145] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.686177] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.722465]  sda: sda1
[    1.722833] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.723406] Freeing unused kernel memory: 932K (c1a64000 - c1b4d000)
[    1.723525] Write protecting the kernel text: 6956k
[    1.723738] Write protecting the kernel read-only data: 3008k
[    1.723741] NX-protecting the kernel data: 5332k
[    1.747458] systemd-udevd[105]: starting version 204
[    1.805970] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.806510] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[    1.810792] [drm] Initialized drm 1.1.0 20060810
[    1.811023] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    1.831806] wmi: Mapper loaded
[    1.843472] pps_core: LinuxPPS API ver. 1 registered
[    1.843478] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.874275] sdhci: Secure Digital Host Controller Interface driver
[    1.874279] sdhci: Copyright(c) Pierre Ossman
[    1.890549] sdhci-pci 0000:02:01.2: SDHCI controller found [1180:0822] (rev 18)
[    1.891752] sdhci-pci 0000:02:01.2: No vmmc regulator found
[    1.891758] sdhci-pci 0000:02:01.2: No vqmmc regulator found
[    1.896888] PTP clock support registered
[    1.915152] mmc0: SDHCI controller on PCI [0000:02:01.2] using DMA
[    1.926264] [drm] Memory usable by graphics device = 256M
[    1.926272] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[    1.926275] fb: switching to inteldrmfb from VESA VGA
[    1.926314] Console: switching to colour dummy device 80x25
[    1.927583] [drm] Replacing VGA console driver
[    1.928734] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.928739] [drm] Driver supports precise vblank timestamp query.
[    1.928876] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.943403] tg3.c:v3.137 (May 11, 2014)
[    1.960055] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[    1.990600] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95752) rev 6002] (PCI Express) MAC address 00:1c:23:5a:17:06
[    1.990609] tg3 0000:09:00.0 eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.990614] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.990619] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    2.000091] firewire_ohci 0000:02:01.1: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    2.119146] usb 2-2: New USB device found, idVendor=413c, idProduct=a005
[    2.119153] usb 2-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.121205] hub 2-2:1.0: USB hub found
[    2.123113] hub 2-2:1.0: 4 ports detected
[    2.390936] [drm] initialized overlay support
[    2.391030] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[    2.421858] usb 2-2.3: new full-speed USB device number 3 using uhci_hcd
[    2.500309] firewire_core 0000:02:01.1: created device fw0: GUID 364fc0000f975c70, S400
[    2.547136] usb 2-2.3: New USB device found, idVendor=0b97, idProduct=7761
[    2.547149] usb 2-2.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.553140] hub 2-2.3:1.0: USB hub found
[    2.555822] hub 2-2.3:1.0: 3 ports detected
[    2.565933] fbcon: inteldrmfb (fb0) is primary device
[    2.565975] Console: switching to colour frame buffer device 128x48
[    2.566022] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.566026] i915 0000:00:02.0: registered panic notifier
[    2.836049] usb 2-2.3.2: new full-speed USB device number 4 using uhci_hcd
[    2.960125] usb 2-2.3.2: New USB device found, idVendor=0b97, idProduct=7762
[    2.960137] usb 2-2.3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.960148] usb 2-2.3.2: Product: O2Micro CCID SC Reader
[    2.960152] usb 2-2.3.2: Manufacturer: O2
[    3.077812] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.292467] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input7
[    3.313193] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input6
[    4.377663] random: init urandom read with 121 bits of entropy available
[    4.497845] random: nonblocking pool is initialized
[   22.555163] systemd-udevd[300]: starting version 204
[   22.876816] lp: driver loaded but no devices found
[   22.892902] ppdev: user-space parallel port driver
[   23.027570] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.262142] cfg80211: Calling CRDA to update world regulatory domain
[   23.306249] intel_rng: FWH not detected
[   23.398594] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   23.398600] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   23.398657] iwl3945 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   23.467193] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   23.467201] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   23.471627] yenta_cardbus 0000:02:01.0: enabling device (0000 -> 0003)
[   23.471829] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:0201]
[   23.477791] leds_ss4200: no LED devices found
[   23.506783] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   23.535863] sound hdaudioC0D0: autoconfig: line_outs=1 (0xe/0x0/0x0/0x0/0x0) type:speaker
[   23.535871] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.535876] sound hdaudioC0D0:    hp_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   23.535880] sound hdaudioC0D0:    mono: mono_out=0x0
[   23.535884] sound hdaudioC0D0:    inputs:
[   23.535888] sound hdaudioC0D0:      Mic=0xf
[   23.535892] sound hdaudioC0D0:      Line=0x10
[   23.557631] audit: type=1400 audit(1449472598.612:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=373 comm="apparmor_parser"
[   23.557645] audit: type=1400 audit(1449472598.612:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=373 comm="apparmor_parser"
[   23.557655] audit: type=1400 audit(1449472598.612:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=373 comm="apparmor_parser"
[   23.558576] audit: type=1400 audit(1449472598.612:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=373 comm="apparmor_parser"
[   23.558588] audit: type=1400 audit(1449472598.612:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=373 comm="apparmor_parser"
[   23.559059] audit: type=1400 audit(1449472598.612:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=373 comm="apparmor_parser"
[   23.600708] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   23.600717] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   23.600724] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   23.600738] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   23.600743] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   23.602330]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   23.604169] sound hdaudioC0D1: autoconfig: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   23.604175] sound hdaudioC0D1:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.604179] sound hdaudioC0D1:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   23.604183] sound hdaudioC0D1:    mono: mono_out=0x0
[   23.604186] sound hdaudioC0D1:    inputs:
[   23.614340] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input8
[   23.614663] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   23.654121] 
[   23.654135] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xefb00000-0xefbfffff]
[   23.654143] pcmcia_socket pcmcia_socket0: cs: memory probe 0xefb00000-0xefbfffff:
[   23.654162]  excluding 0xefbf0000-0xefbfffff
[   23.727314] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   23.825852] dell_laptop: Using i8042 filter function for receiving events
[   23.966699] input: Dell WMI hotkeys as /devices/virtual/input/input10
[   24.030015] gpio_ich: GPIO from 462 to 511 on gpio_ich
[   24.169932] systemd-udevd[326]: Error calling EVIOCSKEYCODE: Invalid argument
[   24.451015] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   24.452320]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   24.453246] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   24.453714]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   24.454156] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   24.454876]  clean.
[   24.454902] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   24.455415]  excluding 0xc80-0xcbf
[   24.455544] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   24.455556]  excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   24.455603] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   24.455631]  clean.
[   24.455657] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   24.455684]  excluding 0x60000000-0x60ffffff
[   24.455712] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   24.456567]  clean.
[   24.545271] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   24.653025] cfg80211: World regulatory domain updated:
[   24.653032] cfg80211:  DFS Master region: unset
[   24.653036] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   24.653041] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.653046] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.653050] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.653054] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.653058] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   26.280566] init: failsafe main process (560) killed by TERM signal
[   27.083423] audit: type=1400 audit(1449472602.136:8): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=696 comm="apparmor_parser"
[   27.083443] audit: type=1400 audit(1449472602.136:9): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=696 comm="apparmor_parser"
[   27.083454] audit: type=1400 audit(1449472602.136:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=696 comm="apparmor_parser"
[   27.084571] audit: type=1400 audit(1449472602.140:11): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/lightdm/lightdm-guest-session" pid=695 comm="apparmor_parser"
[   28.217675] Bluetooth: Core ver 2.20
[   28.217718] NET: Registered protocol family 31
[   28.217721] Bluetooth: HCI device and connection manager initialized
[   28.217732] Bluetooth: HCI socket layer initialized
[   28.217738] Bluetooth: L2CAP socket layer initialized
[   28.217752] Bluetooth: SCO socket layer initialized
[   28.233638] Bluetooth: RFCOMM TTY layer initialized
[   28.233653] Bluetooth: RFCOMM socket layer initialized
[   28.233664] Bluetooth: RFCOMM ver 1.11
[   28.603903] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   28.603910] Bluetooth: BNEP filters: protocol multicast
[   28.603921] Bluetooth: BNEP socket layer initialized
[   28.892412] audit_printk_skb: 147 callbacks suppressed
[   28.892420] audit: type=1400 audit(1449472603.948:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=945 comm="apparmor_parser"
[   29.066603] init: cups main process (741) killed by HUP signal
[   29.066630] init: cups main process ended, respawning
[   31.945729] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   32.015561] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.068188] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   35.834269] tg3 0000:09:00.0 eth0: Link is up at 1000 Mbps, full duplex
[   35.834278] tg3 0000:09:00.0 eth0: Flow control is on for TX and on for RX
[   35.834376] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   36.012844] init: plymouth-upstart-bridge main process ended, respawning
[   36.034630] init: plymouth-upstart-bridge main process ended, respawning
[   57.412662] audit: type=1400 audit(1449472631.631:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1618 comm="apparmor_parser"
[   57.412686] audit: type=1400 audit(1449472631.631:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1618 comm="apparmor_parser"
[   57.413601] audit: type=1400 audit(1449472631.631:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1618 comm="apparmor_parser"
```

---

### Post by KJKJKJ on 2015-12-07
Hi. 

I'm on 14.04 LTS, software is up to date, I have the issue and I first noticed it on 26/11/2015. It happens at 34s after boot (i7) when the Xserver apparently restarts without error so Oinos' observation may be a clue. Like Oinos I have dual display, in my case  on a desktop (Z97X-UD3H Gigabyte mobo Intel onboard graphics) 1920x1080 on HDMI and 1650x1050 on VGA. It happened twice this morning, here's dmesg

 ```

[   34.150721] audit_printk_skb: 153 callbacks suppressed
[   34.150723] type=1400 audit(1449474941.343:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=2163 comm="apparmor_parser"
[   34.150726] type=1400 audit(1449474941.343:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2163 comm="apparmor_parser"
[   34.150920] type=1400 audit(1449474941.343:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=2163 comm="apparmor_parser"
[   57.755166] unity-settings-[2354]: segfault at 18 ip 00007fc54e4c58f3 sp 00007ffd9e791330 error 4 in libc-2.19.so[7fc54e447000+1bb000]
[   60.252322] compiz[2556]: segfault at 0 ip           (null) sp 00007fffae06a4e8 error 14 in compiz[400000+3000]
[   60.580665] HDMI: ELD buf size is 0, force 128
[   60.580688] HDMI: invalid ELD data byte 0
[   60.580729] HDMI: ELD buf size is 0, force 128
[   60.580750] HDMI: invalid ELD data byte 0
[   72.057082] HDMI: ELD buf size is 0, force 128
[   72.057106] HDMI: invalid ELD data byte 0
[   72.057153] HDMI: ELD buf size is 0, force 128
[   72.057165] HDMI: invalid ELD data byte 0
[   80.715555] nf_conntrack: automatic helper assignment is deprecated and it will be removed soon. Use the iptables CT target to attach helpers instead.
[   88.903184] unity-settings-[3101]: segfault at 18 ip 00007f7b9ec218f3 sp 00007fff85f2aec0 error 4 in libc-2.19.so[7f7b9eba3000+1bb000]
[   89.197490] compiz[3304]: segfault at 0 ip           (null) sp 00007ffeafe9d0f8 error 14 in compiz[400000+3000]
[   89.512891] HDMI: ELD buf size is 0, force 128
[   89.512914] HDMI: invalid ELD data byte 0
[   89.512955] HDMI: ELD buf size is 0, force 128
[   89.512976] HDMI: invalid ELD data byte 0
[   90.256401] HDMI: ELD buf size is 0, force 128
[   90.256423] HDMI: invalid ELD data byte 0
[   90.256464] HDMI: ELD buf size is 0, force 128
[   90.256484] HDMI: invalid ELD data byte 0
[ 
```

I hope this helps to pin down the issue.

I agree about the sketchy fix, it's irresponsible "advice" without explanation. Let's get more bug reports so those who know what they are doing have facts and data to analyse.

Speculating, the compiz segfault seems to be the cause. Oinos, if you read this, can you post the next 30 seconds of your logfile please? To see if you get what I got  at 57 through 61 seconds.

---

### Post by Oinos on 2015-12-07
Those were the last seconds, if the first number on the line indicates them. I restarted my laptop, here's the complete log this time(or at least all what I can see in the terminal):
```
[    0.375706] pci 0000:02:01.0: res[13]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.375711] pci 0000:02:01.0: res[14]=[io  0x0100-0x00ff] get_res_add_size add_size 100
[    0.375718] pci 0000:02:01.0: BAR 0: assigned [mem 0x84000000-0x84000fff]
[    0.375730] pci 0000:02:01.0: BAR 15: assigned [mem 0x88000000-0x8bffffff pref]
[    0.375736] pci 0000:02:01.0: BAR 16: assigned [mem 0x8c000000-0x8fffffff]
[    0.375741] pci 0000:02:01.0: BAR 13: assigned [io  0x5000-0x50ff]
[    0.375746] pci 0000:02:01.0: BAR 14: assigned [io  0x5400-0x54ff]
[    0.375750] pci 0000:02:01.0: CardBus bridge to [bus 03-06]
[    0.375754] pci 0000:02:01.0:   bridge window [io  0x5000-0x50ff]
[    0.375761] pci 0000:02:01.0:   bridge window [io  0x5400-0x54ff]
[    0.375769] pci 0000:02:01.0:   bridge window [mem 0x88000000-0x8bffffff pref]
[    0.375777] pci 0000:02:01.0:   bridge window [mem 0x8c000000-0x8fffffff]
[    0.375785] pci 0000:00:1e.0: PCI bridge to [bus 02-03]
[    0.375790] pci 0000:00:1e.0:   bridge window [io  0x5000-0x5fff]
[    0.375800] pci 0000:00:1e.0:   bridge window [mem 0xefb00000-0xefbfffff]
[    0.375815] pci_bus 0000:00: resource 4 [io  0x0000-0x0cf7]
[    0.375820] pci_bus 0000:00: resource 5 [io  0x0d00-0xffff]
[    0.375824] pci_bus 0000:00: resource 6 [mem 0x000a0000-0x000bffff]
[    0.375828] pci_bus 0000:00: resource 7 [mem 0x000d0000-0x000dffff]
[    0.375832] pci_bus 0000:00: resource 8 [mem 0x80000000-0xefffffff]
[    0.375836] pci_bus 0000:00: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.375840] pci_bus 0000:00: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.375844] pci_bus 0000:00: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.375848] pci_bus 0000:00: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.375852] pci_bus 0000:00: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.375856] pci_bus 0000:00: resource 14 [mem 0xfee10000-0xffafffff]
[    0.375861] pci_bus 0000:0b: resource 0 [io  0x2000-0x2fff]
[    0.375865] pci_bus 0000:0b: resource 1 [mem 0x80000000-0x801fffff]
[    0.375869] pci_bus 0000:0b: resource 2 [mem 0x80200000-0x803fffff 64bit pref]
[    0.375873] pci_bus 0000:0c: resource 0 [io  0x3000-0x3fff]
[    0.375877] pci_bus 0000:0c: resource 1 [mem 0xefd00000-0xefdfffff]
[    0.375881] pci_bus 0000:0c: resource 2 [mem 0x80400000-0x805fffff 64bit pref]
[    0.375885] pci_bus 0000:09: resource 0 [io  0x4000-0x4fff]
[    0.375889] pci_bus 0000:09: resource 1 [mem 0xefc00000-0xefcfffff]
[    0.375893] pci_bus 0000:09: resource 2 [mem 0x80600000-0x807fffff 64bit pref]
[    0.375898] pci_bus 0000:02: resource 0 [io  0x5000-0x5fff]
[    0.375901] pci_bus 0000:02: resource 1 [mem 0xefb00000-0xefbfffff]
[    0.375906] pci_bus 0000:02: resource 4 [io  0x0000-0x0cf7]
[    0.375910] pci_bus 0000:02: resource 5 [io  0x0d00-0xffff]
[    0.375913] pci_bus 0000:02: resource 6 [mem 0x000a0000-0x000bffff]
[    0.375917] pci_bus 0000:02: resource 7 [mem 0x000d0000-0x000dffff]
[    0.375921] pci_bus 0000:02: resource 8 [mem 0x80000000-0xefffffff]
[    0.375925] pci_bus 0000:02: resource 9 [mem 0xf4007000-0xf4007fff]
[    0.375929] pci_bus 0000:02: resource 10 [mem 0xf400c000-0xfebfffff]
[    0.375933] pci_bus 0000:02: resource 11 [mem 0xfec10000-0xfecfffff]
[    0.375937] pci_bus 0000:02: resource 12 [mem 0xfed00400-0xfed1ffff]
[    0.375941] pci_bus 0000:02: resource 13 [mem 0xfed40000-0xfed44fff]
[    0.375945] pci_bus 0000:02: resource 14 [mem 0xfee10000-0xffafffff]
[    0.375949] pci_bus 0000:03: resource 0 [io  0x5000-0x50ff]
[    0.375953] pci_bus 0000:03: resource 1 [io  0x5400-0x54ff]
[    0.375957] pci_bus 0000:03: resource 2 [mem 0x88000000-0x8bffffff pref]
[    0.375961] pci_bus 0000:03: resource 3 [mem 0x8c000000-0x8fffffff]
[    0.376026] NET: Registered protocol family 2
[    0.376384] TCP established hash table entries: 8192 (order: 3, 32768 bytes)
[    0.376414] TCP bind hash table entries: 8192 (order: 4, 65536 bytes)
[    0.376464] TCP: Hash tables configured (established 8192 bind 8192)
[    0.376507] TCP: reno registered
[    0.376511] UDP hash table entries: 512 (order: 2, 16384 bytes)
[    0.376527] UDP-Lite hash table entries: 512 (order: 2, 16384 bytes)
[    0.376606] NET: Registered protocol family 1
[    0.376636] pci 0000:00:02.0: Video device with shadowed ROM
[    0.379116] PCI: CLS 64 bytes, default 64
[    0.379208] Trying to unpack rootfs image as initramfs...
[    1.331110] Freeing initrd memory: 27424K (f4a60000 - f6528000)
[    1.331689] microcode: CPU0 sig=0x6fd, pf=0x20, revision=0xa3
[    1.331705] microcode: CPU1 sig=0x6fd, pf=0x20, revision=0xa3
[    1.331839] microcode: Microcode Update Driver: v2.00 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
[    1.331900] Scanning for low memory corruption every 60 seconds
[    1.332573] futex hash table entries: 512 (order: 3, 32768 bytes)
[    1.332620] Initialise system trusted keyring
[    1.332665] audit: initializing netlink subsys (disabled)
[    1.332707] audit: type=2000 audit(1449490627.332:1): initialized
[    1.333286] HugeTLB registered 2 MB page size, pre-allocated 0 pages
[    1.337698] zpool: loaded
[    1.337703] zbud: loaded
[    1.337852] VFS: Disk quotas dquot_6.5.2
[    1.337942] VFS: Dquot-cache hash table entries: 1024 (order 0, 4096 bytes)
[    1.339106] fuse init (API version 7.23)
[    1.339468] Key type big_key registered
[    1.340155] Key type asymmetric registered
[    1.340162] Asymmetric key parser 'x509' registered
[    1.340198] bounce: pool size: 64 pages
[    1.340283] Block layer SCSI generic (bsg) driver version 0.4 loaded (major 252)
[    1.340345] io scheduler noop registered
[    1.340351] io scheduler deadline registered (default)
[    1.340429] io scheduler cfq registered
[    1.341944] pci_hotplug: PCI Hot Plug PCI Core version: 0.5
[    1.341984] pciehp: PCI Express Hot Plug Controller Driver version: 0.4
[    1.342064] vesafb: mode is 1024x768x32, linelength=4096, pages=0
[    1.342067] vesafb: scrolling: redraw
[    1.342072] vesafb: Truecolor: size=8:8:8:8, shift=24:16:8:0
[    1.343589] vesafb: framebuffer at 0xd0000000, mapped to 0xf8480000, using 3072k, total 3072k
[    1.343824] Console: switching to colour frame buffer device 128x48
[    1.343866] fb0: VESA VGA frame buffer device
[    1.343921] intel_idle: does not run on family 6 model 15
[    1.346661] ACPI: AC Adapter [AC] (on-line)
[    1.347877] input: Lid Switch as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0D:00/input/input0
[    1.348520] ACPI: Lid Switch [LID]
[    1.348623] input: Power Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0C:00/input/input1
[    1.348629] ACPI: Power Button [PBTN]
[    1.348728] input: Sleep Button as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0C0E:00/input/input2
[    1.348734] ACPI: Sleep Button [SBTN]
[    1.348933] ACPI: acpi_idle registered with cpuidle
[    1.355497] thermal LNXTHERM:00: registered as thermal_zone0
[    1.355502] ACPI: Thermal Zone [THM] (27 C)
[    1.355573] GHES: HEST is not enabled!
[    1.360166] Serial: 8250/16550 driver, 32 ports, IRQ sharing enabled
[    1.361155] isapnp: Scanning for PnP cards...
[    1.386280] Linux agpgart interface v0.103
[    1.386452] agpgart-intel 0000:00:00.0: Intel 945GM Chipset
[    1.386481] agpgart-intel 0000:00:00.0: detected gtt size: 262144K total, 262144K mappable
[    1.387120] agpgart-intel 0000:00:00.0: detected 8192K stolen memory
[    1.387298] agpgart-intel 0000:00:00.0: AGP aperture is 256M @ 0xd0000000
[    1.390478] brd: module loaded
[    1.392050] loop: module loaded
[    1.392376] ata_piix 0000:00:1f.1: version 2.13
[    1.404316] ACPI: Battery Slot [BAT0] (battery present)
[    1.404446] scsi host0: ata_piix
[    1.404634] scsi host1: ata_piix
[    1.404742] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xbfa0 irq 14
[    1.404746] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0xbfa8 irq 15
[    1.404953] libphy: Fixed MDIO Bus: probed
[    1.404959] tun: Universal TUN/TAP device driver, 1.6
[    1.404961] tun: (C) 1999-2004 Max Krasnyansky <maxk@qualcomm.com>
[    1.405222] PPP generic driver version 2.4.2
[    1.405384] ehci_hcd: USB 2.0 'Enhanced' Host Controller (EHCI) Driver
[    1.405394] ehci-pci: EHCI PCI platform driver
[    1.405710] ehci-pci 0000:00:1d.7: EHCI Host Controller
[    1.405723] ehci-pci 0000:00:1d.7: new USB bus registered, assigned bus number 1
[    1.405745] ehci-pci 0000:00:1d.7: debug port 1
[    1.409649] ehci-pci 0000:00:1d.7: cache line size of 64 is not supported
[    1.409682] ehci-pci 0000:00:1d.7: irq 20, io mem 0xffa80000
[    1.409742] ata2: port disabled--ignoring
[    1.420042] ehci-pci 0000:00:1d.7: USB 2.0 started, EHCI 1.00
[    1.420169] usb usb1: New USB device found, idVendor=1d6b, idProduct=0002
[    1.420174] usb usb1: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.420178] usb usb1: Product: EHCI Host Controller
[    1.420183] usb usb1: Manufacturer: Linux 3.19.0-33-generic ehci_hcd
[    1.420186] usb usb1: SerialNumber: 0000:00:1d.7
[    1.420439] hub 1-0:1.0: USB hub found
[    1.420456] hub 1-0:1.0: 8 ports detected
[    1.421122] ehci-platform: EHCI generic platform driver
[    1.421145] ohci_hcd: USB 1.1 'Open' Host Controller (OHCI) Driver
[    1.421154] ohci-pci: OHCI PCI platform driver
[    1.421183] ohci-platform: OHCI generic platform driver
[    1.421204] uhci_hcd: USB Universal Host Controller Interface driver
[    1.421485] uhci_hcd 0000:00:1d.0: UHCI Host Controller
[    1.421496] uhci_hcd 0000:00:1d.0: new USB bus registered, assigned bus number 2
[    1.421507] uhci_hcd 0000:00:1d.0: detected 2 ports
[    1.421536] uhci_hcd 0000:00:1d.0: irq 20, io base 0x0000bf80
[    1.421635] usb usb2: New USB device found, idVendor=1d6b, idProduct=0001
[    1.421640] usb usb2: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.421644] usb usb2: Product: UHCI Host Controller
[    1.421648] usb usb2: Manufacturer: Linux 3.19.0-33-generic uhci_hcd
[    1.421652] usb usb2: SerialNumber: 0000:00:1d.0
[    1.421892] hub 2-0:1.0: USB hub found
[    1.421907] hub 2-0:1.0: 2 ports detected
[    1.422402] uhci_hcd 0000:00:1d.1: UHCI Host Controller
[    1.422413] uhci_hcd 0000:00:1d.1: new USB bus registered, assigned bus number 3
[    1.422424] uhci_hcd 0000:00:1d.1: detected 2 ports
[    1.422466] uhci_hcd 0000:00:1d.1: irq 21, io base 0x0000bf60
[    1.422549] usb usb3: New USB device found, idVendor=1d6b, idProduct=0001
[    1.422553] usb usb3: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.422558] usb usb3: Product: UHCI Host Controller
[    1.422562] usb usb3: Manufacturer: Linux 3.19.0-33-generic uhci_hcd
[    1.422565] usb usb3: SerialNumber: 0000:00:1d.1
[    1.422802] hub 3-0:1.0: USB hub found
[    1.422815] hub 3-0:1.0: 2 ports detected
[    1.423302] uhci_hcd 0000:00:1d.2: UHCI Host Controller
[    1.423313] uhci_hcd 0000:00:1d.2: new USB bus registered, assigned bus number 4
[    1.423323] uhci_hcd 0000:00:1d.2: detected 2 ports
[    1.423366] uhci_hcd 0000:00:1d.2: irq 22, io base 0x0000bf40
[    1.423450] usb usb4: New USB device found, idVendor=1d6b, idProduct=0001
[    1.423454] usb usb4: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.423458] usb usb4: Product: UHCI Host Controller
[    1.423462] usb usb4: Manufacturer: Linux 3.19.0-33-generic uhci_hcd
[    1.423466] usb usb4: SerialNumber: 0000:00:1d.2
[    1.423700] hub 4-0:1.0: USB hub found
[    1.423713] hub 4-0:1.0: 2 ports detected
[    1.424221] uhci_hcd 0000:00:1d.3: UHCI Host Controller
[    1.424232] uhci_hcd 0000:00:1d.3: new USB bus registered, assigned bus number 5
[    1.424242] uhci_hcd 0000:00:1d.3: detected 2 ports
[    1.424284] uhci_hcd 0000:00:1d.3: irq 23, io base 0x0000bf20
[    1.424370] usb usb5: New USB device found, idVendor=1d6b, idProduct=0001
[    1.424374] usb usb5: New USB device strings: Mfr=3, Product=2, SerialNumber=1
[    1.424378] usb usb5: Product: UHCI Host Controller
[    1.424382] usb usb5: Manufacturer: Linux 3.19.0-33-generic uhci_hcd
[    1.424386] usb usb5: SerialNumber: 0000:00:1d.3
[    1.424617] hub 5-0:1.0: USB hub found
[    1.424630] hub 5-0:1.0: 2 ports detected
[    1.424979] i8042: PNP: PS/2 Controller [PNP0303:KBC,PNP0f13:PS2M] at 0x60,0x64 irq 1,12
[    1.427854] serio: i8042 KBD port at 0x60,0x64 irq 1
[    1.427864] serio: i8042 AUX port at 0x60,0x64 irq 12
[    1.428141] mousedev: PS/2 mouse device common for all mice
[    1.428456] rtc_cmos 00:05: RTC can wake from S4
[    1.428682] rtc_cmos 00:05: rtc core: registered rtc_cmos as rtc0
[    1.428723] rtc_cmos 00:05: alarms up to one month, y3k, 114 bytes nvram, hpet irqs
[    1.428743] i2c /dev entries driver
[    1.428849] device-mapper: uevent: version 1.0.3
[    1.428992] device-mapper: ioctl: 4.29.0-ioctl (2014-10-28) initialised: dm-devel@redhat.com
[    1.429049] platform eisa.0: Probing EISA bus 0
[    1.429056] platform eisa.0: EISA: Cannot allocate resource for mainboard
[    1.429060] platform eisa.0: Cannot allocate resource for EISA slot 1
[    1.429064] platform eisa.0: Cannot allocate resource for EISA slot 2
[    1.429068] platform eisa.0: Cannot allocate resource for EISA slot 3
[    1.429072] platform eisa.0: Cannot allocate resource for EISA slot 4
[    1.429077] platform eisa.0: Cannot allocate resource for EISA slot 5
[    1.429081] platform eisa.0: Cannot allocate resource for EISA slot 6
[    1.429084] platform eisa.0: Cannot allocate resource for EISA slot 7
[    1.429088] platform eisa.0: Cannot allocate resource for EISA slot 8
[    1.429092] platform eisa.0: EISA: Detected 0 cards
[    1.429124] cpufreq-nforce2: No nForce2 chipset.
[    1.429138] ledtrig-cpu: registered to indicate activity on CPUs
[    1.429161] PCCT header not found.
[    1.429163] ACPI PCC probe failed.
[    1.429376] TCP: cubic registered
[    1.429673] NET: Registered protocol family 10
[    1.430128] NET: Registered protocol family 17
[    1.430153] Key type dns_resolver registered
[    1.430558] Using IPI No-Shortcut mode
[    1.430853] Loading compiled-in X.509 certificates
[    1.437618] Loaded X.509 cert 'Magrathea: Glacier signing key: fc4145a9c3fce2bed267a0de8f7c951aa3e2f71c'
[    1.437649] registered taskstats version 1
[    1.438353] input: AT Translated Set 2 keyboard as /devices/platform/i8042/serio0/input/input3
[    1.441629] Key type trusted registered
[    1.448431] Key type encrypted registered
[    1.448442] AppArmor: AppArmor sha1 policy hashing enabled
[    1.448449] ima: No TPM chip found, activating TPM-bypass!
[    1.448486] evm: HMAC attrs: 0x1
[    1.449092]   Magic number: 11:553:278
[    1.449110] usb usb1-port6: hash matches
[    1.449154] tty tty15: hash matches
[    1.449247] rtc_cmos 00:05: setting system clock to 2015-12-07 12:17:08 UTC (1449490628)
[    1.450373] BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
[    1.450376] EDD information not available.
[    1.450505] PM: Hibernation image not present or could not be loaded.
[    1.568602] ata1.00: ATA-6: TOSHIBA MK6008GAH, BU011A, max UDMA/100
[    1.568608] ata1.00: 117210240 sectors, multi 8: LBA48 
[    1.576478] ata1.00: configured for UDMA/100
[    1.677216] isapnp: No Plug & Play device found
[    1.677405] scsi 0:0:0:0: Direct-Access     ATA      TOSHIBA MK6008GA 1A   PQ: 0 ANSI: 5
[    1.677818] sd 0:0:0:0: [sda] 117210240 512-byte logical blocks: (60.0 GB/55.8 GiB)
[    1.677915] sd 0:0:0:0: Attached scsi generic sg0 type 0
[    1.677936] sd 0:0:0:0: [sda] Write Protect is off
[    1.677941] sd 0:0:0:0: [sda] Mode Sense: 00 3a 00 00
[    1.678003] sd 0:0:0:0: [sda] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    1.704990]  sda: sda1
[    1.705587] sd 0:0:0:0: [sda] Attached SCSI disk
[    1.706168] Freeing unused kernel memory: 932K (c1a64000 - c1b4d000)
[    1.706277] Write protecting the kernel text: 6956k
[    1.706483] Write protecting the kernel read-only data: 3008k
[    1.706485] NX-protecting the kernel data: 5332k
[    1.730025] systemd-udevd[106]: starting version 204
[    1.779581] pps_core: LinuxPPS API ver. 1 registered
[    1.779586] pps_core: Software ver. 5.3.6 - Copyright 2005-2007 Rodolfo Giometti <giometti@linux.it>
[    1.783698] [drm] Initialized drm 1.1.0 20060810
[    1.797623] wmi: Mapper loaded
[    1.815623] ACPI: Video Device [VID] (multi-head: yes  rom: no  post: no)
[    1.816193] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A03:00/LNXVIDEO:00/input/input5
[    1.816792] [Firmware Bug]: Duplicate ACPI video bus devices for the same VGA controller, please try module parameter "video.allow_duplicates=1"if the current driver doesn't work.
[    1.819921] PTP clock support registered
[    1.858654] tg3.c:v3.137 (May 11, 2014)
[    1.889444] sdhci: Secure Digital Host Controller Interface driver
[    1.889449] sdhci: Copyright(c) Pierre Ossman
[    1.905755] [drm] Memory usable by graphics device = 256M
[    1.905763] checking generic (d0000000 300000) vs hw (d0000000 10000000)
[    1.905766] fb: switching to inteldrmfb from VESA VGA
[    1.905808] Console: switching to colour dummy device 80x25
[    1.906855] [drm] Replacing VGA console driver
[    1.908083] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[    1.908087] [drm] Driver supports precise vblank timestamp query.
[    1.908223] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[    1.920042] usb 2-2: new full-speed USB device number 2 using uhci_hcd
[    1.923434] tg3 0000:09:00.0 eth0: Tigon3 [partno(BCM95752) rev 6002] (PCI Express) MAC address 00:1c:23:5a:17:06
[    1.923442] tg3 0000:09:00.0 eth0: attached PHY is 5752 (10/100/1000Base-T Ethernet) (WireSpeed[1], EEE[0])
[    1.923447] tg3 0000:09:00.0 eth0: RXcsums[1] LinkChgREG[0] MIirq[0] ASF[0] TSOcap[1]
[    1.923452] tg3 0000:09:00.0 eth0: dma_rwctrl[76180000] dma_mask[64-bit]
[    1.976149] firewire_ohci 0000:02:01.1: added OHCI v1.10 device as card 0, 4 IR + 4 IT contexts, quirks 0x11
[    1.976279] sdhci-pci 0000:02:01.2: SDHCI controller found [1180:0822] (rev 18)
[    1.977507] sdhci-pci 0000:02:01.2: No vmmc regulator found
[    1.977512] sdhci-pci 0000:02:01.2: No vqmmc regulator found
[    1.980855] mmc0: SDHCI controller on PCI [0000:02:01.2] using DMA
[    2.072094] usb 2-2: New USB device found, idVendor=413c, idProduct=a005
[    2.072101] usb 2-2: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.074170] hub 2-2:1.0: USB hub found
[    2.076104] hub 2-2:1.0: 4 ports detected
[    2.374950] [drm] initialized overlay support
[    2.375038] [drm] Initialized i915 1.6.0 20141121 for 0000:00:02.0 on minor 0
[    2.392059] usb 2-2.3: new full-speed USB device number 3 using uhci_hcd
[    2.476263] firewire_core 0000:02:01.1: created device fw0: GUID 364fc0000f975c70, S400
[    2.525017] usb 2-2.3: New USB device found, idVendor=0b97, idProduct=7761
[    2.525023] usb 2-2.3: New USB device strings: Mfr=0, Product=0, SerialNumber=0
[    2.528195] hub 2-2.3:1.0: USB hub found
[    2.530103] hub 2-2.3:1.0: 3 ports detected
[    2.549714] fbcon: inteldrmfb (fb0) is primary device
[    2.549756] Console: switching to colour frame buffer device 128x48
[    2.549802] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[    2.549806] i915 0000:00:02.0: registered panic notifier
[    2.820048] usb 2-2.3.2: new full-speed USB device number 4 using uhci_hcd
[    2.943118] usb 2-2.3.2: New USB device found, idVendor=0b97, idProduct=7762
[    2.943126] usb 2-2.3.2: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[    2.943131] usb 2-2.3.2: Product: O2Micro CCID SC Reader
[    2.943135] usb 2-2.3.2: Manufacturer: O2
[    3.160145] EXT4-fs (sda1): mounted filesystem with ordered data mode. Opts: (null)
[    3.264318] input: DualPoint Stick as /devices/platform/i8042/serio1/input/input7
[    3.284885] input: AlpsPS/2 ALPS DualPoint TouchPad as /devices/platform/i8042/serio1/input/input6
[    4.460077] random: init urandom read with 121 bits of entropy available
[    4.531279] random: nonblocking pool is initialized
[   22.683478] systemd-udevd[302]: starting version 204
[   22.994642] lp: driver loaded but no devices found
[   23.016807] ppdev: user-space parallel port driver
[   23.172316] shpchp: Standard Hot Plug PCI Controller Driver version: 0.4
[   23.342922] yenta_cardbus 0000:02:01.0: enabling device (0000 -> 0003)
[   23.343574] yenta_cardbus 0000:02:01.0: CardBus bridge found [1028:0201]
[   23.395120] intel_rng: FWH not detected
[   23.445656] cfg80211: Calling CRDA to update world regulatory domain
[   23.494426] yenta_cardbus 0000:02:01.0: ISA IRQ mask 0x0cb8, PCI irq 19
[   23.494434] yenta_cardbus 0000:02:01.0: Socket status: 30000006
[   23.494442] pci_bus 0000:02: Raising subordinate bus# of parent bus (#02) from #03 to #06
[   23.500044] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [io  0x5000-0x5fff]
[   23.500052] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x5000-0x5fff:
[   23.501709]  excluding 0x5000-0x50ff 0x5400-0x54ff
[   23.559633] yenta_cardbus 0000:02:01.0: pcmcia: parent PCI bridge window: [mem 0xefb00000-0xefbfffff]
[   23.559641] pcmcia_socket pcmcia_socket0: cs: memory probe 0xefb00000-0xefbfffff:
[   23.559659]  excluding 0xefbf0000-0xefbfffff
[   23.566640] leds_ss4200: no LED devices found
[   23.627937] audit: type=1400 audit(1449490650.671:2): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/sbin/dhclient" pid=355 comm="apparmor_parser"
[   23.627953] audit: type=1400 audit(1449490650.671:3): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=355 comm="apparmor_parser"
[   23.627962] audit: type=1400 audit(1449490650.671:4): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[   23.628922] audit: type=1400 audit(1449490650.675:5): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/NetworkManager/nm-dhcp-client.action" pid=355 comm="apparmor_parser"
[   23.628933] audit: type=1400 audit(1449490650.675:6): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[   23.629401] audit: type=1400 audit(1449490650.675:7): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/connman/scripts/dhclient-script" pid=355 comm="apparmor_parser"
[   23.679436] iwl3945: Intel(R) PRO/Wireless 3945ABG/BG Network Connection driver for Linux, in-tree:s
[   23.679442] iwl3945: Copyright(c) 2003-2011 Intel Corporation
[   23.679519] iwl3945 0000:0c:00.0: can't disable ASPM; OS doesn't have ASPM control
[   23.739666] iwl3945 0000:0c:00.0: Tunable channels: 13 802.11bg, 23 802.11a channels
[   23.739675] iwl3945 0000:0c:00.0: Detected Intel Wireless WiFi Link 3945ABG
[   23.804559] ieee80211 phy0: Selected rate control algorithm 'iwl-3945-rs'
[   23.906670] dcdbas dcdbas: Dell Systems Management Base Driver (version 5.6.0-3.2)
[   24.012243] dell_laptop: Using i8042 filter function for receiving events
[   24.081589] gpio_ich: GPIO from 462 to 511 on gpio_ich
[   24.145403] input: Dell WMI hotkeys as /devices/virtual/input/input8
[   24.157957] systemd-udevd[334]: Error calling EVIOCSKEYCODE: Invalid argument
[   24.226181] sound hdaudioC0D0: autoconfig: line_outs=1 (0xe/0x0/0x0/0x0/0x0) type:speaker
[   24.226189] sound hdaudioC0D0:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   24.226194] sound hdaudioC0D0:    hp_outs=1 (0xd/0x0/0x0/0x0/0x0)
[   24.226198] sound hdaudioC0D0:    mono: mono_out=0x0
[   24.226201] sound hdaudioC0D0:    inputs:
[   24.226206] sound hdaudioC0D0:      Mic=0xf
[   24.226210] sound hdaudioC0D0:      Line=0x10
[   24.235917] sound hdaudioC0D1: autoconfig: line_outs=0 (0x0/0x0/0x0/0x0/0x0) type:line
[   24.235925] sound hdaudioC0D1:    speaker_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   24.235929] sound hdaudioC0D1:    hp_outs=0 (0x0/0x0/0x0/0x0/0x0)
[   24.235933] sound hdaudioC0D1:    mono: mono_out=0x0
[   24.235937] sound hdaudioC0D1:    inputs:
[   24.248693] input: HDA Intel Line as /devices/pci0000:00/0000:00:1b.0/sound/card0/input9
[   24.248936] input: HDA Intel Headphone as /devices/pci0000:00/0000:00:1b.0/sound/card0/input10
[   24.333335] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x100-0x3af:
[   24.335235]  excluding 0x170-0x177 0x1f0-0x1f7 0x370-0x377
[   24.337214] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x3e0-0x4ff:
[   24.337923]  excluding 0x3f0-0x3f7 0x4d0-0x4d7
[   24.338587] pcmcia_socket pcmcia_socket0: cs: IO port probe 0x820-0x8ff:
[   24.339691]  clean.
[   24.339717] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xc00-0xcf7:
[   24.341977]  excluding 0xc80-0xcbf
[   24.342179] pcmcia_socket pcmcia_socket0: cs: memory probe 0x0c0000-0x0fffff:
[   24.342191]  excluding 0xc0000-0xcffff 0xe0000-0xfffff
[   24.342241] pcmcia_socket pcmcia_socket0: cs: memory probe 0xa0000000-0xa0ffffff:
[   24.342269]  clean.
[   24.342297] pcmcia_socket pcmcia_socket0: cs: memory probe 0x60000000-0x60ffffff:
[   24.342324]  excluding 0x60000000-0x60ffffff
[   24.342354] pcmcia_socket pcmcia_socket0: cs: IO port probe 0xa00-0xaff:
[   24.343622]  clean.
[   24.792291] cfg80211: World regulatory domain updated:
[   24.792299] cfg80211:  DFS Master region: unset
[   24.792302] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp), (dfs_cac_time)
[   24.792307] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.792312] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.792316] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.792320] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   24.792324] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm), (N/A)
[   26.867605] EXT4-fs (sda1): re-mounted. Opts: errors=remount-ro
[   27.533539] init: failsafe main process (612) killed by TERM signal
[   27.890331] audit: type=1400 audit(1449490654.935:8): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=724 comm="apparmor_parser"
[   27.890351] audit: type=1400 audit(1449490654.935:9): apparmor="STATUS" operation="profile_load" profile="unconfined" name="/usr/sbin/cupsd" pid=724 comm="apparmor_parser"
[   27.891257] audit: type=1400 audit(1449490654.935:10): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=724 comm="apparmor_parser"
[   28.232760] audit: type=1400 audit(1449490655.279:11): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/sbin/dhclient" pid=778 comm="apparmor_parser"
[   28.870449] Bluetooth: Core ver 2.20
[   28.870491] NET: Registered protocol family 31
[   28.870494] Bluetooth: HCI device and connection manager initialized
[   28.870505] Bluetooth: HCI socket layer initialized
[   28.870511] Bluetooth: L2CAP socket layer initialized
[   28.870525] Bluetooth: SCO socket layer initialized
[   28.886680] Bluetooth: RFCOMM TTY layer initialized
[   28.886693] Bluetooth: RFCOMM socket layer initialized
[   28.886705] Bluetooth: RFCOMM ver 1.11
[   29.031660] init: cups main process (725) killed by HUP signal
[   29.031687] init: cups main process ended, respawning
[   29.230585] Bluetooth: BNEP (Ethernet Emulation) ver 1.3
[   29.230592] Bluetooth: BNEP filters: protocol multicast
[   29.230602] Bluetooth: BNEP socket layer initialized
[   29.671649] audit_printk_skb: 147 callbacks suppressed
[   29.671657] audit: type=1400 audit(1449490656.715:61): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cups-browsed" pid=927 comm="apparmor_parser"
[   32.313475] iwl3945 0000:0c:00.0: loaded firmware version 15.32.2.9
[   32.396960] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[   32.464138] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   36.168487] tg3 0000:09:00.0 eth0: Link is up at 1000 Mbps, full duplex
[   36.168495] tg3 0000:09:00.0 eth0: Flow control is on for TX and on for RX
[   36.168523] IPv6: ADDRCONF(NETDEV_CHANGE): eth0: link becomes ready
[   36.435937] init: plymouth-upstart-bridge main process ended, respawning
[   36.458168] init: plymouth-upstart-bridge main process ended, respawning
[   58.009066] audit: type=1400 audit(1449490685.055:62): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=1830 comm="apparmor_parser"
[   58.009087] audit: type=1400 audit(1449490685.055:63): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1830 comm="apparmor_parser"
[   58.009991] audit: type=1400 audit(1449490685.055:64): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=1830 comm="apparmor_parser"


```

---

### Post by KJKJKJ on 2015-12-08
I spent some time on Google and Launchpad and it seems there are plenty of similar looking bugs with unity settings daemon, hopefully it will get attention (which I never take for granted and do appreciate).

Today _I turned the monitors on before the PC _and logged in successfully the first time, maybe this is a _workaround_. It needs other people to confirm or deny, please post what happens to your system if you are interested and encounter this problem.

If this ever gets worse, and we can't login at all,  is it the case that unity settings daemon is unique to Unity, and that e.g. Xubuntu/Xfce4 doesn't suffer from this? I'd like to have a fallback option, because even fresh installs apparently have this problem.

Results using workaround:

2015-12-08  OK
2015-12-09  OK
2015-12-10 OK

---

### Post by Oinos on 2015-12-09
That doesn't seem to work for me. One thing I forgot to mention is that initially the displays are mirrored and only after I enter my password the first time do they synchronize in two different areas as they are supposed to be. So something is not initialised properly.

---

### Post by KJKJKJ on 2015-12-10
That's a shame.

Mine start off mirrored, then after login form a desktop with 1920x1080 next to 1680x1050 - now that is cool because 1080 != 1050. I don't think the mirroring is a bug, but a feature. The desktop is arranged when you login.

What happens if you login as another user?

---

### Post by Oinos on 2015-12-11
If I recall correctly when I logged in as guest this didn't happen but I won't be able to try it out again until Monday.

---

### Post by Oinos on 2015-12-14
Bad idea. When I clicked guest session, it took only once to log in correctly, but then when I switched accounts after 6 or so attempts I still couldn't log in to my main account, it kept prompting me for my password on that mirror screens thing. Then I decided to go back go the guest account, but this time it wouldn't even load correctly, just the plain background with nothing else, switching to black on random intervals.

The only way out of that was to shut it down via the button. When I started the computer again, the problem persisted without even trying to log in to the guest account. I figured out it was due to the manual shut down, so I shut it down properly this time.

Alas, no luck. The third time was not any better. I figured out I should plug out the monitor and only then was I able to log in. I reported some problem via the automated system, but it told me it was a system crash.

I've got no idea what's going on and I feel like ubuntu is buggy. Would system specs be of help?

---

### Post by KJKJKJ on 2015-12-29
Dagnabbit, 22 days without this happening, until today. Got in at 2nd attempt. I think I forgot to power up the monitor first as I have been doing as a workaround.

---

### Post by boiteamadmax on 2016-01-13
Same problem here since 3 days on 14.04 LTS. When I log the first time, the desktop appear briefly and I come back to the login screen. The second attemps works.

I've this on the dmesg:
> [   17.261508] compiz[2437]: segfault at 0 ip           (null) sp 00007ffdc8075978 error 14 in compiz[400000+3000]
[   17.504473] QXcbEventReader[2536]: segfault at 7fd823418729 ip 00007fd823418729 sp 00007fd820cb1d60 error 14 in locale-archive[7fd823697000+581000]




And on syslog:
> Jan 13 12:25:44 Ubuntu kernel: [   17.261508] compiz[2437]: segfault at 0 ip           (null) sp 00007ffdc8075978 error 14 in compiz[400000+3000]Jan 13 12:25:44 Ubuntu gnome-session[2288]: WARNING: Application 'compiz.desktop' killed by signal 11
Jan 13 12:25:44 Ubuntu gnome-session[2288]: WARNING: App 'compiz.desktop' respawning too quickly
Jan 13 12:25:44 Ubuntu gnome-session[2288]: CRITICAL: We failed, but the fail whale is dead. Sorry....
Jan 13 12:25:44 Ubuntu kernel: [   17.504473] QXcbEventReader[2536]: segfault at 7fd823418729 ip 00007fd823418729 sp 00007fd820cb1d60 error 14 in locale-archive[7fd823697000+5810$
Jan 13 12:25:44 Ubuntu colord: device removed: xrandr-Samsung Electric Company-SyncMaster-H1AK500000
Jan 13 12:25:44 Ubuntu colord: Profile removed: icc-797e68d63a35922a996d47a327c0f099
Jan 13 12:25:44 Ubuntu acpid: client 1409[0:0] has disconnected
Jan 13 12:25:44 Ubuntu acpid: client connected from 2645[0:0]
Jan 13 12:25:44 Ubuntu acpid: 1 client rule loaded
Jan 13 12:25:44 Ubuntu NetworkManager[925]: <info> WiFi hardware radio set enabled
Jan 13 12:25:45 Ubuntu colord: Device added: xrandr-Samsung Electric Company-SyncMaster-H1AK500000
Jan 13 12:25:45 Ubuntu colord: Automatic metadata add icc-f732c8831a29e7901d3b77fdc74fb492 to xrandr-Samsung Electric Company-SyncMaster-H1AK500000
Jan 13 12:25:45 Ubuntu colord: Profile added: icc-f732c8831a29e7901d3b77fdc74fb492
Jan 13 12:25:46 Ubuntu colord: device removed: xrandr-Samsung Electric Company-SyncMaster-H1AK500000
Jan 13 12:25:46 Ubuntu colord: Profile removed: icc-f732c8831a29e7901d3b77fdc74fb492
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Successfully made thread 3173 of process 3173 (n/a) owned by '1000' high priority at nice level -11.
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Supervising 4 threads of 2 processes of 2 users.
Jan 13 12:25:47 Ubuntu pulseaudio[3173]: [pulseaudio] pid.c: Stale PID file, overwriting.
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Successfully made thread 3217 of process 3173 (n/a) owned by '1000' RT at priority 5.
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Supervising 5 threads of 2 processes of 2 users.
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Successfully made thread 3218 of process 3173 (n/a) owned by '1000' RT at priority 5.
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Supervising 6 threads of 2 processes of 2 users.
Jan 13 12:25:47 Ubuntu goa[3213]: goa-daemon version 3.10.3 starting [main.c:117, main()]
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Successfully made thread 3229 of process 3229 (n/a) owned by '1000' high priority at nice level -11.
Jan 13 12:25:47 Ubuntu rtkit-daemon[1645]: Supervising 7 threads of 3 processes of 2 users.
Jan 13 12:25:47 Ubuntu pulseaudio[3229]: [pulseaudio] pid.c: Daemon already running.
Jan 13 12:25:47 Ubuntu colord: Device added: xrandr-Samsung Electric Company-SyncMaster-H1AK500000
Jan 13 12:25:48 Ubuntu colord: Automatic metadata add icc-797e68d63a35922a996d47a327c0f099 to xrandr-Samsung Electric Company-SyncMaster-H1AK500000
Jan 13 12:25:48 Ubuntu colord: Profile added: icc-797e68d63a35922a996d47a327c0f099




I've one screen connected on VGA Via a KVM Switch. 

I've tried to boot with monitor on. But it's doesn't solve the problem.

---

### Post by boiteamadmax on 2016-01-17
I've found the problem, I've recently unzip in the .fonts directory all the google fonts with the arborescence. And Ubuntu don't seems to like that.

---

### Post by Bucky Ball on 2016-01-17
You found the problem. Great. Have you fixed the problem by removing those fonts? If so and you are happy, please mark as solved (see first link in my signature below). ;)

---

### Post by boiteamadmax on 2016-01-17
Yes i've deleted the .fonts directory. But I wasn't created this topic. I've just invited me as i'm haved the same problem. (have to login Twice)

---

### Post by Bucky Ball on 2016-01-17
> **boiteamadmax said:**
> Yes i've deleted the .fonts directory. But I wasn't created this topic. I've just invited me as i'm haved the same problem. (have to login Twice)

Okay, well let's get back to fixing the OP's issue. Your problem wasn't the same so please post a new thread if this happens in future. Cross-posting only creates confusion, as evidenced here. Thanks.

---

### Post by KJKJKJ on 2016-04-29
It's back again.

Worryingly, one attempt took several retries.

The desktop appears, the desktop stutters, a drum sound is heard, then user is dumped back to login screen.

I don't autostart anything I've written. I've trimmed the list of autostart programs. Any suspects.

---

### Post by Bucky Ball on 2016-04-29
Still 14.04 LTS?

---

### Post by boiteamadmax on 2016-04-29
I've succeed to resolve my problem. It was because I put all the Google fonts directory (yes with all files and arborescence) in the ~/.fonts. And after removing it no more trouble.

---

### Post by KJKJKJ on 2017-01-22
FWIW I think you can work around this by closing all windows before logout. Over the space of a year I've monitored this carefully, it looks like something to do with saving or restoring the session. That's my deduction about the root cause. I'll speculate that unmapped windows cause it.

---

