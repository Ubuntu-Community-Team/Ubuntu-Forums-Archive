---
title: "ubuntu freezes because of pci / intel problem?"
date: 2015-12-18
forum: General Help
---

### Post by pc-6 on 2015-12-18
Hello,

I installed ubuntu several times, but despite my efforts it is not working. The computer freezes randomly: sometimes after 5 minutes, sometimes after two hours. It happens when playing a movie or reading a pdf file. I cannot reproduce it neither solve it. I do not see any error reports when it happens or when I reset the computer. The computers starts up, shuts down easily without problems.

I had some problems with the i915 drivers so I intalled the newest stable Ubuntu 15.10 64 bit.

possible causes of freezing:
1. PCI drivers:
[    0.278069] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    0.328723] pci 0000:00:1c.0: BAR 15: failed to assign [mem size 0x00200000 64bit pref]
[    0.328732] pci 0000:00:1c.1: BAR 14: failed to assign [mem size 0x00200000]

2. intel motherboard?
[    3.767663] intel_soc_dts_thermal: request_threaded_irq ret -22

Any one any clue how to solve it?

kind regards,
Robert

=====================
motherboard: ASrock Q2900-itx

[LIST]
[*]Intel[SUP]®[/SUP] Quad-Core Pentium[SUP]®[/SUP] Processor J2900 
[*]All Solid Capacitor design 
[*]Supports DDR3 1333 memory, 2 SO-DIMM slots 
[*]1 PCIe 2.0 x1, 1 mini-PCIe 
[*]Graphics Output Options : D-Sub, DVI-D, HDMI 
[*]Built-in Intel[SUP]®[/SUP] 7[SUP]th[/SUP] generation (Gen 7) graphics, DirectX 11.0, Pixel Shader 5.0 
[*]7.1 CH HD Audio with Content Protection (Realtek ALC892 Audio Codec) 
[*]2 SATA3, 2 SATA2, 4 USB 3.0 (2 Front, 2 Rear), 4 USB 2.0 (2 Front, 2 Rear) 
[*]1 x Print Port Header, 1 x COM Port Header 
[*]Supports ASRock Cloud, APP Shop, Full Spike Protection 
[/LIST]

8 Gb of memory

[http://www.robertsplannen.nl/dmesg.txt](http://www.robertsplannen.nl/dmesg.txt)

---

### Post by bswarm2 on 2016-02-20
I have the same CPU and had the same freezeups in Ubuntu, but not while dual booting into Windows. I found a few forum posts that suggested changing the CPU max cstate to "C1" in the bios. I haven't had a problem since then.
[This]("http://ubuntuforums.org/showthread.php?t=2284615") and [this]("https://bugs.freedesktop.org/show_bug.cgi?id=88012") pointed me in the right direction after trying other fixes.

---

