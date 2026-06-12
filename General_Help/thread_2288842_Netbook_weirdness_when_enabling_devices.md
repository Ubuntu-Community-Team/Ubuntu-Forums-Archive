---
title: "Netbook weirdness when enabling devices"
date: 2015-07-30
forum: General Help
---

### Post by vertigo420 on 2015-07-30
I have an Acer Aspire One netbook. When I enable bluetooth, or plug in a USB device, it enters suspend. Why? How can I fix this?

Running 14.04. Can provide more information and logs. What do you need?

---

### Post by halfnote52 on 2015-07-31
That's WEIRD!  I've got an AspireONE AAO ZG5 (Running Mint, mind you) that I LOVE!

Have you tried checking the contents of, say, dmesg right as you plug in the USB/etc?  After you've resumed from suspend, that is.

---

### Post by vertigo420 on 2015-08-01
Here is dmesg after plugging in a USB drive.

```


[11300.276182] usb 1-1: new high-speed USB device number 9 using ehci-pci
[11300.415312] usb 1-1: New USB device found, idVendor=058f, idProduct=6387
[11300.415332] usb 1-1: New USB device strings: Mfr=1, Product=2, SerialNumber=3
[11300.415346] usb 1-1: SerialNumber: 14022459000074
[11300.417115] usb-storage 1-1:1.0: USB Mass Storage device detected
[11300.418232] scsi7 : usb-storage 1-1:1.0
[11300.454586] wlan0: deauthenticating from 00:1c:df:83:93:d5 by local choice (reason=3)
[11300.458042] cfg80211: Calling CRDA to update world regulatory domain
[11300.485051] cfg80211: World regulatory domain updated:
[11300.485062] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11300.485071] cfg80211:   (2402000 KHz - 2472000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11300.485079] cfg80211:   (2457000 KHz - 2482000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11300.485087] cfg80211:   (2474000 KHz - 2494000 KHz @ 20000 KHz), (300 mBi, 2000 mBm)
[11300.485095] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11300.485103] cfg80211:   (5735000 KHz - 5835000 KHz @ 40000 KHz), (300 mBi, 2000 mBm)
[11301.418954] scsi 7:0:0:0: Direct-Access                               8.07 PQ: 0 ANSI: 4
[11301.421247] sd 7:0:0:0: [sdb] 15482880 512-byte logical blocks: (7.92 GB/7.38 GiB)
[11301.422507] sd 7:0:0:0: [sdb] Write Protect is off
[11301.422522] sd 7:0:0:0: [sdb] Mode Sense: 23 00 00 00
[11301.423753] sd 7:0:0:0: [sdb] Write cache: disabled, read cache: enabled, doesn't support DPO or FUA
[11301.424627] sd 7:0:0:0: Attached scsi generic sg1 type 0
[11301.444332]  sdb: sdb1
[11301.448524] sd 7:0:0:0: [sdb] Attached SCSI removable disk
[11303.147060] init: anacron main process (11952) killed by TERM signal
[11303.459735] PM: Syncing filesystems ... done.
[11303.688905] PM: Preparing system for mem sleep
[11303.689192] Freezing user space processes ... (elapsed 0.004 seconds) done.
[11303.694116] Freezing remaining freezable tasks ... (elapsed 4.610 seconds) done.
[11308.304187] PM: Entering mem sleep
[11308.304270] Suspending console(s) (use no_console_suspend to debug)
[11308.304790] sd 2:0:0:0: [sda] Synchronizing SCSI cache
[11308.305632] sd 2:0:0:0: [sda] Stopping disk
[11308.852229] PM: suspend of devices complete after 547.681 msecs
[11308.868259] PM: late suspend of devices complete after 16.013 msecs
[11308.900300] ehci-pci 0000:00:1d.7: System wakeup enabled by ACPI
[11308.916123] uhci_hcd 0000:00:1d.3: System wakeup enabled by ACPI
[11308.916209] uhci_hcd 0000:00:1d.2: System wakeup enabled by ACPI
[11308.916294] uhci_hcd 0000:00:1d.1: System wakeup enabled by ACPI
[11308.916379] uhci_hcd 0000:00:1d.0: System wakeup enabled by ACPI
[11308.916604] PM: noirq suspend of devices complete after 48.336 msecs
[11308.916651] ACPI: Preparing to enter system sleep state S3
[11308.916796] PM: Saving platform NVS memory
[11308.918156] Disabling non-boot CPUs ...
[11309.020031] smpboot: CPU 1 is now offline
[11309.020330] ACPI: Low-level resume complete
[11309.020330] ACPI Exception: AE_NOT_FOUND, While evaluating Sleep State [\_S0_] (20131115/hwxface-580)
[11309.020330] PM: Restoring platform NVS memory
[11309.020330] Enabling non-boot CPUs ...
[11309.020330] x86: Booting SMP configuration:
[11309.020330] smpboot: Booting Node 0 Processor 1 APIC 0x1
[11308.919769] Initializing CPU#1
[11308.919769] Disabled fast string operations
[11309.032867] CPU1 is up
[11309.033502] ACPI: Waking up from system sleep state S3
[11309.068412] uhci_hcd 0000:00:1d.0: System wakeup disabled by ACPI
[11309.068502] uhci_hcd 0000:00:1d.1: System wakeup disabled by ACPI
[11309.068588] uhci_hcd 0000:00:1d.2: System wakeup disabled by ACPI
[11309.068674] uhci_hcd 0000:00:1d.3: System wakeup disabled by ACPI
[11309.084128] ehci-pci 0000:00:1d.7: System wakeup disabled by ACPI
[11309.132275] PM: noirq resume of devices complete after 95.230 msecs
[11309.132541] PM: early resume of devices complete after 0.217 msecs
[11309.133171] snd_hda_intel 0000:00:1b.0: irq 44 for MSI/MSI-X
[11309.133510] usb usb2: root hub lost power or was reset
[11309.133562] usb usb3: root hub lost power or was reset
[11309.133611] usb usb4: root hub lost power or was reset
[11309.133660] usb usb5: root hub lost power or was reset
[11309.135545] ata2: port disabled--ignoring
[11309.456169] ata5: SATA link down (SStatus 0 SControl 300)
[11309.504208] usb 1-2: reset high-speed USB device number 2 using ehci-pci
[11309.780160] usb 5-1: reset full-speed USB device number 5 using uhci_hcd
[11310.524145] ata3: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
[11310.525614] ata3.00: ACPI cmd ef/10:03:00:00:00:a0 (SET FEATURES) filtered out
[11310.540801] ata3.00: ACPI cmd 00/00:00:00:00:00:a0 (NOP) rejected by device (Stat=0x51 Err=0x04)
[11310.541322] ata3.00: configured for UDMA/133
[11310.556519] sd 2:0:0:0: [sda] Starting disk
[11310.712295] PM: resume of devices complete after 1579.741 msecs
[11310.713380] PM: Finishing wakeup.
[11310.713386] Restarting tasks ... done.
[11311.384238] video LNXVIDEO:00: Restoring backlight state
[11312.408660] init: anacron main process (12171) killed by TERM signal
[11312.536396] IPv6: ADDRCONF(NETDEV_UP): wlan0: link is not ready
[11312.555491] atl1c 0000:03:00.0: irq 45 for MSI/MSI-X
[11312.582207] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[11313.716258] wlan0: authenticate with 00:1c:df:83:93:d5
[11313.716613] wlan0: send auth to 00:1c:df:83:93:d5 (try 1/3)
[11313.726722] wlan0: authenticated
[11313.728163] wlan0: associate with 00:1c:df:83:93:d5 (try 1/3)
[11313.777932] wlan0: RX AssocResp from 00:1c:df:83:93:d5 (capab=0x431 status=0 aid=13)
[11313.779190] wlan0: associated
[11313.779321] IPv6: ADDRCONF(NETDEV_CHANGE): wlan0: link becomes ready
[11313.779749] cfg80211: Calling CRDA for country: GB
[11313.797807] ath: EEPROM regdomain: 0x833a
[11313.797815] ath: EEPROM indicates we should expect a country code
[11313.797820] ath: doing EEPROM country->regdmn map search
[11313.797825] ath: country maps to regdmn code: 0x37
[11313.797829] ath: Country alpha2 being used: GB
[11313.797833] ath: Regpair used: 0x37
[11313.797838] ath: regdomain 0x833a dynamically updated by country IE
[11313.797842] cfg80211: Regulatory domain changed to country: GB
[11313.797845] cfg80211:   (start_freq - end_freq @ bandwidth), (max_antenna_gain, max_eirp)
[11313.797851] cfg80211:   (2402000 KHz - 2482000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[11313.797856] cfg80211:   (5170000 KHz - 5250000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[11313.797861] cfg80211:   (5250000 KHz - 5330000 KHz @ 40000 KHz), (N/A, 2000 mBm)
[11313.797865] cfg80211:   (5490000 KHz - 5710000 KHz @ 40000 KHz), (N/A, 2700 mBm)
[11313.797871] cfg80211:   (57240000 KHz - 65880000 KHz @ 2160000 KHz), (N/A, 4000 mBm)
[11327.632638] FAT-fs (sdb1): Volume was not properly unmounted. Some data may be corrupt. Please run fsck.


```

---

### Post by halfnote52 on 2015-08-01
Okay, so it IS going to sleep as you plug in what appears to be in this case a USB hard drive. Weird!

Question: Do you have any custom scripts you've added/written that execute when aything's attached to your system? Anything that could, for example, be mistakenly calling the suspend?

---

