---
title: "Long boot time"
date: 2013-11-25
forum: General Help
---

### Post by arnold_layne2 on 2013-11-25
My last Ubuntu setup used to take barely 10-12 seconds to get up and ready, but this one takes around 35-40 seconds. Here is my /var/log/dmesg: [http://pastebin.com/fw3ZGcAt](http://pastebin.com/fw3ZGcAt)

One possible abnormality is this:
```
[    2.281163] usb 2-1.5: Product: Broadcom 2070 Bluetooth
[    2.281167] usb 2-1.5: Manufacturer: Broadcom Corp
[    2.281170] usb 2-1.5: SerialNumber: CC52AFA47679
[    2.688735] i915 0000:00:02.0: fb1: inteldrmfb frame buffer device
[    2.690079] [Firmware Bug]: ACPI(PEGP) defines _DOD but not _DOS
[    2.693382] ACPI: Video Device [PEGP] (multi-head: yes  rom: no  post: no)
[    2.694615] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:2c/LNXVIDEO:00/input/input6
[    2.696507] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[    2.697486] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:01/input/input7
[    2.698543] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 1
[    2.781451] xor: automatically using best checksumming function:
[    2.820340]    avx       : 15011.000 MB/sec
[    2.820597] [drm] Enabling RC6 states: RC6 on, RC6p off, RC6pp off
[    2.822344] device-mapper: dm-raid45: initialized v0.2594b
[    8.345714] kjournald starting.  Commit interval 5 seconds
[    8.345795] EXT3-fs (sda5): mounted filesystem with ordered data mode
[   27.452988] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   27.491930] udevd[515]: starting version 175
[   27.700475] microcode: CPU0 sig=0x206a7, pf=0x10, revision=0x1a
[   27.702930] lp: driver loaded but no devices found
[   27.703570] device-mapper: multipath: version 1.5.1 loaded
[   27.704473] mei 0000:00:16.0: setting latency timer to 64
[   27.704542] mei 0000:00:16.0: irq 54 for MSI/MSI-X
[   27.705328] Bluetooth: Core ver 2.16
[   27.705347] NET: Registered protocol family 31
[   27.705349] Bluetooth: HCI device and connection manager initialized
[   27.705357] Bluetooth: HCI socket layer initialized
[   27.705360] Bluetooth: L2CAP socket layer initialized
[   27.705366] Bluetooth: SCO socket layer initialized
[   27.707055] usbcore: registered new interface driver btusb
[   27.708654] bcma: bus0: Found chip with id 0x4313, rev 0x01 and package 0x08
[   27.708682] bcma: bus0: Core 0 found: ChipCommon (manuf 0x4BF, id 0x800, rev 0x24, class 0x0)
[   27.708705] bcma: bus0: Core 1 found: IEEE 802.11 (manuf 0x4BF, id 0x812, rev 0x18, class 0x0)
[   27.708749] bcma: bus0: Core 2 found: PCIe (manuf 0x4BF, id 0x820, rev 0x11, class 0x0)
[   27.720611] bcma: bus0: Bus registered

```

One, that 6 second gap after* device-mapper: dm-raid45: initialized v0.2594 *and much more alarmingly, the 20(!) second gap after [I]EXT3-fs (sda5): mounted filesystem with ordered data mode.
[/I]Can I do something to debug this further or speed it up? Earlier the 20-30 second gap used to occur after *scanning brtfs file systems *but then I disabled that feature. I think the boot times improved, but only by around 5 seconds, and I still have a 20 second gap.

---

### Post by oldfred on 2013-11-25
Are you using IPv6 or Bluetooth? If not turn those off.

---

