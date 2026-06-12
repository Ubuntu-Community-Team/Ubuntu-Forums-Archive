---
title: "USB ports not working after sleep resume"
date: 2014-05-18
forum: General Help
---

### Post by josephellengar2 on 2014-05-18
Hi! I'm using Ubuntu 14.04 on an HP Envy touchsmart (laptop). My DE is Cinnamon, a spinoff of Gnome 3. I have had a lot of trouble with sleep/resume on this computer since upgrading to 14.04. I have had to add a number of scripts in /etc/pm/sleep.d in order to restart various modules on resume from sleep (which I suspect may be the problem here). The latest problem that I am having is that the USB ports are not working when I resume. They still exist, and the computer sees them, but they just don't work. I have tested this with three USB devices that work on another computer and none of them work after resume on this one. They do work in my other operating system.

For debugging purposes, here is some information that might be useful.

My lsusb output (post-sleep/resume):

```

Bus 002 Device 004: ID 0eef:a802 D-WAV Scientific Co., Ltd 
Bus 002 Device 002: ID 8087:8000 Intel Corp. 
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 001 Device 002: ID 8087:8008 Intel Corp. 
Bus 001 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
Bus 004 Device 001: ID 1d6b:0003 Linux Foundation 3.0 root hub
Bus 003 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub

```

The tail end of my dmesg output.

```

[36132.057984] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[36132.706750] ata5: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
[36132.709296] ata5.00: configured for UDMA/100
[36132.722783] sd 4:0:0:0: [sdb] Starting disk
[36133.171453] PM: resume of devices complete after 2555.670 msecs
[36133.171597] PM: Finishing wakeup.
[36133.171598] Restarting tasks ... done.
[36133.174819] video LNXVIDEO:00: Restoring backlight state
[36133.174822] video LNXVIDEO:01: Restoring backlight state
[36133.175475] pci 0000:07:00.0: no hotplug settings from platform
[36133.175525] rtsx_pci 0000:09:00.0: no hotplug settings from platform
[36133.175552] pci 0000:0f:00.0: no hotplug settings from platform
[36133.379777] usb 2-1.7: new full-speed USB device number 4 using ehci-pci
[36133.473814] usb 2-1.7: New USB device found, idVendor=0eef, idProduct=a802
[36133.473818] usb 2-1.7: New USB device strings: Mfr=1, Product=2, SerialNumber=0
[36133.473819] usb 2-1.7: Product: eGalaxTouch EXC7920-2003-11.03.02
[36133.473821] usb 2-1.7: Manufacturer: eGalax Inc.
[36133.475381] input: eGalax Inc. eGalaxTouch EXC7920-2003-11.03.02 as /devices/pci0000:00/0000:00:1d.0/usb2/2-1/2-1.7/2-1.7:1.0/input/input70
[36133.475479] hid-multitouch 0003:0EEF:A802.0012: input,hiddev0,hidraw0: USB HID v2.10 Device [eGalax Inc. eGalaxTouch EXC7920-2003-11.03.02] on usb-0000:00:1d.0-1.7/input0
[36136.391456] cfg80211: Calling CRDA to update world regulatory domain
[36136.393009] cfg80211: World regulatory domain updated:
[36136.393010] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[36136.393011] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[36136.393012] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[36136.393013] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[36136.393014] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[36136.393015] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[36136.399681] Intel(R) Wireless WiFi driver for Linux, in-tree:
[36136.399683] Copyright(c) 2003-2013 Intel Corporation
[36136.399800] iwlwifi 0000:07:00.0: can't disable ASPM; OS doesn't have ASPM control
[36136.399925] iwlwifi 0000:07:00.0: irq 48 for MSI/MSI-X
[36136.400261] iwlwifi 0000:07:00.0: loaded firmware version 18.168.6.1 op_mode iwldvm
[36136.402454] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUG disabled
[36136.402455] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEBUGFS enabled
[36136.402456] iwlwifi 0000:07:00.0: CONFIG_IWLWIFI_DEVICE_TRACING enabled
[36136.402458] iwlwifi 0000:07:00.0: Detected Intel(R) Centrino(R) Wireless-N 2230 BGN, REV=0xC8
[36136.402549] iwlwifi 0000:07:00.0: L1 Enabled; Disabling L0S
[36136.419272] ieee80211 phy0: Selected rate control algorithm 'iwl-agn-rs'
[36136.422072] r8169 Gigabit Ethernet driver 2.3LK-NAPI loaded
[36136.422077] r8169 0000:0f:00.0: can't disable ASPM; OS doesn't have ASPM control
[36136.422985] iwlwifi 0000:07:00.0: L1 Enabled; Disabling L0S
[36136.427693] r8169 0000:0f:00.0: irq 49 for MSI/MSI-X
[36136.430506] iwlwifi 0000:07:00.0: Radio type=0x2-0x0-0x0
[36136.674525] iwlwifi 0000:07:00.0: L1 Enabled; Disabling L0S
[36136.682068] iwlwifi 0000:07:00.0: Radio type=0x2-0x0-0x0
[36136.757652] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[36136.757798] r8169 0000:0f:00.0 eth0: RTL8168g/8111g at 0xffffc900018f6000, 9c:b6:54:43:a2:13, XID 0c000800 IRQ 49
[36136.757801] r8169 0000:0f:00.0 eth0: jumbo features [frames: 9200 bytes, tx checksumming: ko]
[36136.758239] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[36136.767752] systemd-udevd[32525]: renamed network interface eth0 to eth1
[36136.809789] r8169 0000:0f:00.0 eth1: link down
[36136.809842] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[36136.810052] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[36137.353149] wlan0: authenticate with 58:6d:8f:c2:c7:e6
[36137.358773] wlan0: send auth to 58:6d:8f:c2:c7:e6 (try 1/3)
[36137.361948] wlan0: authenticated
[36137.364322] wlan0: associate with 58:6d:8f:c2:c7:e6 (try 1/3)
[36137.367820] wlan0: RX AssocResp from 58:6d:8f:c2:c7:e6 (capab=0x411 status=0 aid=3)
[36137.384269] psmouse serio1: synaptics: Touchpad model: 1, fw: 8.1, id: 0x1e2b1, caps: 0xd00123/0x840300/0x127c00, board id: 2667, fw id: 1280283
[36137.388419] wlan0: associated
[36137.388458] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[36137.421129] input: SynPS/2 Synaptics TouchPad as /devices/platform/i8042/serio1/input/input73
[36136.771577] waiting module removal not supported: please upgrade
[36138.181342] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[36138.181448] ACPI Warning: \_SB_.PCI0.PEG0.PEGP._DSM: Argument #4 type mismatch - Found [Buffer], ACPI requires [Package] (20131115/nsarguments-95)
[37013.299321] type=1400 audit(1400426110.587:79): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/lib/cups/backend/cups-pdf" pid=14779 comm="apparmor_parser"
[37013.299331] type=1400 audit(1400426110.587:80): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=14779 comm="apparmor_parser"
[37013.299577] type=1400 audit(1400426110.587:81): apparmor="STATUS" operation="profile_replace" profile="unconfined" name="/usr/sbin/cupsd" pid=14779 comm="apparmor_parser"
[38447.720037] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[38447.723355] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[38447.724759] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[38447.726249] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[38447.727633] psmouse serio1: TouchPad at isa0060/serio1/input0 lost sync at byte 1
[38447.727636] psmouse serio1: issuing reconnect request

```

---

### Post by matt_symes on 2014-05-19
Hi

You could try unbinding the usb devices pre-sleep and rebind them after resume.

That may fix it as it only seems to be seeing one device during resume.

What bios settings have you got set ?

Kind regards

---

### Post by josephellengar2 on 2014-05-19
> **matt_symes said:**
> Hi

You could try unbinding the usb devices pre-sleep and rebind them after resume.

That may fix it as it only seems to be seeing one device during resume.

What bios settings have you got set ?

Kind regards

Thanks for your reply, Matt!

I have tried both with and without usb devices bound. I almost always keep devices unbound, since this is a laptop, so I don't think that's it. Would you like another dump of my log file from when I have nothing bound?

I don't have any weird bios settings. I have virtualization disabled, I have legacy boot on (which allows Ubuntu to bypass UEFI), and I have it set so that USB 3 drivers aren't loaded pre-OS (which allows me to boot from a USB 2 device). Otherwise, this is a pretty locked-down system since it's an HP laptop, so there's not much I can do. *shrug*

---

### Post by tgalati4 on 2014-05-20
Try installing acpitool and examine the power status of various parts of the bus before and after a sleep/resume cycle:

```
sudo apt-get install acpitool
acpitool -w
```

---

### Post by josephellengar2 on 2014-05-20
Well, I reinstalled my DE and now everything seems to be working. I can't imagine what the problem was, but I'll post back if it reappears. Thanks for the help!

---

