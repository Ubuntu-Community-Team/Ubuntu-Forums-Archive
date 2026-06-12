---
title: "Strange Graphical Behavior"
date: 2015-04-16
forum: General Help
---

### Post by Silyus on 2015-04-16
Since when I have installed xubuntu **14.04.2 LTS** on my new laptop I got this strange behavior that you can see in these screens (the black bars are inserted to remove private data, the screens otherwise represent what I actually see on my desktop):
[LIST=1]
[*][Text disappear]("http://i.imgur.com/dY4pf8K.jpg") (sorry for the crappy quality, but it was taken by my mobile camera)
[*][Odd windows behavior]("http://i.imgur.com/Z0tMlG2.png") (In this pic the central windows was supposed to be a terminal :/)
[/LIST]

It happens when I log in, without any specific action on my side, and the problem intensifies when I use the browser or when many windows are opened at the same time.

Here's my laptop's specifications:
[LIST]
[*][COLOR=#262626][FONT=arial]Acer aspire V15 (code V3-572G-75CA)[/FONT][/COLOR]
[*][COLOR=#262626][FONT=arial]intel core i7 5500U 2.4GHz [/FONT][/COLOR]
[*][COLOR=#262626][FONT=arial]Nvidia GeForce 840M  2GB  VRAM [/FONT][/COLOR]
[*][COLOR=#262626][FONT=arial]8GB DDR3 [/FONT][/COLOR]
[*][COLOR=#262626][FONT=arial]1000 GB HDD[/FONT][/COLOR]
[/LIST]

Here's what i get from lspci (the graphic devices are in bold):
```

[COLOR=#262626][FONT=arial]00:00.0 Host bridge: Intel Corporation Broadwell-U Host Bridge -OPI (rev 09)[/FONT][/COLOR]
**[COLOR=#262626][FONT=arial]00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09)[/FONT][/COLOR]**
[COLOR=#262626][FONT=arial]00:03.0 Audio device: Intel Corporation Broadwell-U Audio Controller (rev 09)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:14.0 USB controller: Intel Corporation Wildcat Point-LP USB xHCI Controller (rev 03)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:16.0 Communication controller: Intel Corporation Wildcat Point-LP MEI Controller #1 (rev 03)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1b.0 Audio device: Intel Corporation Wildcat Point-LP High Definition Audio Controller (rev 03)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1c.0 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #1 (rev e3)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1c.2 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #3 (rev e3)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1c.3 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #4 (rev e3)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1c.4 PCI bridge: Intel Corporation Wildcat Point-LP PCI Express Root Port #5 (rev e3)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1f.0 ISA bridge: Intel Corporation Wildcat Point-LP LPC Controller (rev 03)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1f.2 SATA controller: Intel Corporation Wildcat Point-LP SATA Controller [AHCI Mode] (rev 03)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1f.3 SMBus: Intel Corporation Wildcat Point-LP SMBus Controller (rev 03)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]00:1f.6 Signal processing controller: Intel Corporation Wildcat Point-LP Thermal Management Controller (rev 03)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]02:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. Device 5287 (rev 01)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]02:00.1 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 12)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]03:00.0 Network controller: Intel Corporation Wireless 7260 (rev bb)[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]**04:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)**
[/FONT][/COLOR]
``` 
Here are the -v -s details of the bolded devices:
```

**[COLOR=#262626][FONT=arial]00:02.0 VGA compatible controller: Intel Corporation Broadwell-U Integrated Graphics (rev 09) (prog-if 00 [VGA controller])[/FONT][/COLOR]**
[COLOR=#262626][FONT=arial]Subsystem: Acer Incorporated [ALI] Device 0940[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Flags: bus master, fast devsel, latency 0, IRQ 69[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Memory at c2000000 (64-bit, non-prefetchable) [size=16M][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Memory at d0000000 (64-bit, prefetchable) [size=256M][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]I/O ports at 5000 [size=64][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Expansion ROM at <unassigned> [disabled][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [d0] Power Management version 2[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [a4] PCI Advanced Features[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Kernel driver in use: i915[/FONT][/COLOR]

```
```

**[COLOR=#262626][FONT=arial]04:00.0 3D controller: NVIDIA Corporation GM108M [GeForce 840M] (rev a2)[/FONT][/COLOR]**
[COLOR=#262626][FONT=arial]Subsystem: Acer Incorporated [ALI] Device 0942[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Flags: fast devsel, IRQ 16[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Memory at c3000000 (32-bit, non-prefetchable) [size=16M][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Memory at b0000000 (64-bit, prefetchable) [size=256M][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Memory at c0000000 (64-bit, prefetchable) [size=32M][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]I/O ports at 3000 [size=128][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Expansion ROM at <ignored> [disabled][/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [60] Power Management version 3[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [68] MSI: Enable- Count=1/1 Maskable- 64bit+[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [78] Express Endpoint, MSI 00[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [100] Virtual Channel[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [250] Latency Tolerance Reporting[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [258] L1 PM Substates[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [128] Power Budgeting <?>[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [600] Vendor Specific Information: ID=0001 Rev=1 Len=024 <?>[/FONT][/COLOR]
[COLOR=#262626][FONT=arial]Capabilities: [900] #19[/FONT][/COLOR]

```
I also got these strange messages in dmsg that are worth reporting:
```

[   11.359540] fbcon: inteldrmfb (fb0) is primary device
[   11.359591] Console: switching to colour frame buffer device 170x48
[   11.359607] i915 0000:00:02.0: fb0: inteldrmfb frame buffer device
[   11.359608] i915 0000:00:02.0: registered panic notifier
[   11.383686] ACPI: Video Device [GFX0] (multi-head: yes  rom: no  post: no)
[   11.383759] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/LNXVIDEO:00/input/input12
[   11.383891] [Firmware Bug]: ACPI(PXSX) defines _DOD but not _DOS
[   11.383898] ACPI: Video Device [PXSX] (multi-head: yes  rom: yes  post: no)
[   11.383929] input: Video Bus as /devices/LNXSYSTM:00/LNXSYBUS:00/PNP0A08:00/device:52/LNXVIDEO:01/input/input13
[   11.383991] [drm] Initialized i915 1.6.0 20080730 for 0000:00:02.0 on minor 0
[   11.384356] snd_hda_intel 0000:00:03.0: irq 70 for MSI/MSI-X
[   11.393858] input: HDA Intel HDMI HDMI/DP,pcm=3 as /devices/pci0000:00/0000:00:03.0/sound/card0/input14
[   11.393923] input: HDA Intel HDMI HDMI/DP,pcm=7 as /devices/pci0000:00/0000:00:03.0/sound/card0/input15
[   11.393980] input: HDA Intel HDMI HDMI/DP,pcm=8 as /devices/pci0000:00/0000:00:03.0/sound/card0/input16
[   11.116752] VGA switcheroo: detected Optimus DSM method \_SB_.PCI0.RP05.PXSX handle
[   11.116774] checking generic (d0000000 410000) vs hw (b0000000 10000000)
[   11.116776] checking generic (d0000000 410000) vs hw (c0000000 2000000)
[   11.116805] nouveau 0000:04:00.0: enabling device (0106 -> 0107)
[   11.117047] nouveau ![  DEVICE][0000:04:00.0] unknown Maxwell chipset
[   11.117051] nouveau E[  DEVICE][0000:04:00.0] unknown chipset, 0x118010a2
[   11.117053] nouveau E[     DRM] failed to create 0x80000080, -22
[   11.117273] nouveau: probe of 0000:04:00.0 failed with error -22
[   11.117658] iwlwifi 0000:03:00.0: Unsupported splx structure
[   11.118163] input: Acer BMA150 accelerometer as /devices/virtual/input/input8
[   11.125464] [drm] Memory usable by graphics device = 4096M
[   11.125468] checking generic (d0000000 410000) vs hw (d0000000 10000000)
[   11.125469] fb: switching to inteldrmfb from EFI VGA
[   11.125482] Console: switching to colour dummy device 80x25
[   11.125545] [drm] Replacing VGA console driver
[   11.126214] [drm] ACPI BIOS requests an excessive sleep of 10000 ms, using 1500 ms instead
[   11.146760] i915 0000:00:02.0: irq 69 for MSI/MSI-X
[   11.146771] [drm] Supports vblank timestamp caching Rev 2 (21.10.2013).
[   11.146773] [drm] Driver supports precise vblank timestamp query.
[   11.146802] vgaarb: device changed decodes: PCI:0000:00:02.0,olddecodes=io+mem,decodes=io+mem:owns=io+mem
[   11.187004] [drm] VBT doesn't support DRRS

```

---

