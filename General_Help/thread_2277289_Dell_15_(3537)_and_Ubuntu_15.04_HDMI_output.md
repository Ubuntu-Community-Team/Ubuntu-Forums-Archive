---
title: "Dell 15 (3537) and Ubuntu 15.04 HDMI output"
date: 2015-05-07
forum: General Help
---

### Post by julian22 on 2015-05-07
Hi,

I'm trying to hook up a second monitor to my Dell 3537 using Ubuntu 15.04, but I am unable to get a signal from the monitor. I've tried hooking up multiple monitors and attempting the "Detect Displays" settings, but Ubuntu is unable to detect the monitor. I've had success with this laptop's HDMI output in Windows 8 in the past.

Output of [LEFT][COLOR=#222222][FONT=Helvetica Neue]lspci -v is as follows[/FONT][/COLOR][/LEFT]

```
00:02.0 VGA compatible controller: Intel Corporation Haswell-ULT Integrated Graphics Controller (rev 09) (prog-if 00 [VGA controller])
    Subsystem: Dell Device 05e9
    Flags: bus master, fast devsel, latency 0, IRQ 46
    Memory at b0000000 (64-bit, non-prefetchable) [size=4M]
    Memory at a0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915

```


I'm at a loss as to what to do next.

---

