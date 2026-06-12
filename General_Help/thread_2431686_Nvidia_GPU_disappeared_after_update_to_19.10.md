---
title: "Nvidia GPU disappeared after update to 19.10"
date: 2019-11-20
forum: General Help
---

### Post by setheal on 2019-11-20
Good morning,

I got a little issue for some weeks now, I've tried to fix it but no result so far.

So I've upgrade my Kubuntu from 19.04 to 19.10, my nvidia card was fully functional at this moment. After the update, I've found that my HDMI port stopped working.
After some research, I've found that my GPU was not listed anymore in lspci..
I've already tried to purge nvidia from the system, if this can help.

Result of my lspci:
```

00:00.0 Host bridge: Intel Corporation 8th Gen Core Processor Host Bridge/DRAM Registers (rev 07)00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v5/E3-1500 v5/6th Gen Core Processor PCIe Controller (x16) (rev 07)
00:02.0 VGA compatible controller: Intel Corporation UHD Graphics 630 (Mobile)
00:08.0 System peripheral: Intel Corporation Xeon E3-1200 v5/v6 / E3-1500 v5 / 6th/7th Gen Core Processor Gaussian Mixture Model
00:12.0 Signal processing controller: Intel Corporation Cannon Lake PCH Thermal Controller (rev 10)
00:14.0 USB controller: Intel Corporation Cannon Lake PCH USB 3.1 xHCI Host Controller (rev 10)
00:14.2 RAM memory: Intel Corporation Cannon Lake PCH Shared SRAM (rev 10)
00:16.0 Communication controller: Intel Corporation Cannon Lake PCH HECI Controller (rev 10)
00:1b.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #19 (rev f0)
00:1b.3 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #20 (rev f0)
00:1d.0 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #9 (rev f0)
00:1d.4 PCI bridge: Intel Corporation Cannon Lake PCH PCI Express Root Port #13 (rev f0)
00:1f.0 ISA bridge: Intel Corporation Device a30d (rev 10)
00:1f.3 Audio device: Intel Corporation Cannon Lake PCH cAVS (rev 10)
00:1f.4 SMBus: Intel Corporation Cannon Lake PCH SMBus Controller (rev 10)
00:1f.5 Serial bus controller [0c80]: Intel Corporation Cannon Lake PCH SPI Controller (rev 10)
02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168/8411 PCI Express Gigabit Ethernet Controller (rev 16)
03:00.0 Network controller: Intel Corporation Wireless 8265 / 8275 (rev 78)
04:00.0 Non-Volatile memory controller: Intel Corporation SSD Pro 7600p/760p/E 6100p Series (rev 03)

```

Thank you for helping me.

---

### Post by Autodave on 2019-11-20
First off, problems like this often occur during updates from one release to another.  What Nvidia card do you have?  What driver did you install and where did you get the driver from?

---

### Post by setheal on 2019-11-21
I have a GTX1070 Max-Q. I've tested the driver 430, 435 and the 390. And i've installed them from the ubuntu repository, some with the ubuntu-drivers tool.

---

### Post by setheal on 2019-11-27
Ok, so I got some news. I've removed the Nvidia drivers one more time and changed the grub parameter "nouveau.modeset=0" to "nouveau.runpm=0", and now it seems that the GPU is used. But nothing in lspci or lshw..

From 'dmesg | grep 0000:01'
```

[FONT=monospace][COLOR=#000000][    2.466651] nouveau [/COLOR][COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: enabling device (0000 -> 0003)[/COLOR]
[    2.467279] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: NVIDIA GP104 (134000a1)[/COLOR]
[    2.789891] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: bios: version 86.04.80.00.7f[/COLOR]
[    2.832406] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: fb: 8192 MiB GDDR5[/COLOR]
[    2.896441] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: VRAM: 8192 MiB[/COLOR]
[    2.896444] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: GART: 536870912 MiB[/COLOR]
[    2.896449] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: BIT table 'A' not found[/COLOR]
[    2.896453] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: BIT table 'L' not found[/COLOR]
[    2.896456] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: TMDS table version 2.0[/COLOR]
[    2.896460] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: DCB version 4.1[/COLOR]
[    2.896465] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: DCB outp 00: 04000f82 00020010[/COLOR]
[    2.896469] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: DCB outp 01: 04011f96 04600020[/COLOR]
[    2.896472] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: DCB outp 02: 04011f92 00020020[/COLOR]
[    2.896475] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: DCB conn 00: 01000061[/COLOR]
[    2.896477] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: DCB conn 01: 02000146[/COLOR]
[    2.897990] nouveau [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0: DRM: MM: using COPY for buffer copies[/COLOR]
[    2.989123] [drm] Initialized nouveau 1.3.1 20120801 for [COLOR=#FF5454]**0000:01**[/COLOR][COLOR=#000000]:00.0 on minor 0[/COLOR]
[/FONT]
```

[FONT=monospace]From 'sudo lshw -C display'

[/FONT]```


*-display description: VGA compatible controller
product: UHD Graphics 630 (Mobile)
vendor: Intel Corporation
physical id: 2
bus info: pci@0000:00:02.0
version: 00
width: 64 bits
clock: 33MHz
capabilities: pciexpress msi pm vga_controller bus_master cap_list rom
configuration: driver=i915 latency=0
resources: irq:143 memory:ab000000-abffffff memory:40000000-4fffffff ioport:5000(size=64) memory:c0000-dffff


```

Thank you.

---

