---
title: "Ubuntu 16.04 LTS VCE Init Error (-110)"
date: 2016-04-27
forum: General Help
---

### Post by b-keskin91 on 2016-04-27
Hello everyone

i installed Ubuntu 16.04 on my Notebook. I Have an dedicated graphic Card the AMD HD8600M.
While booting (which takes a long time) I get a Error Message called: VCE Init Error (-110).

I made a few Terminal calls to figure out why it happens but i don't get it :( 

ouptut for : lspci -vnk | grep -iA20 vga

```

00:02.0 0300: 8086:0166 (rev 09) (prog-if 00 [VGA controller])
    Subsystem: 17aa:3800
    Flags: bus master, fast devsel, latency 0, IRQ 28
    Memory at d8000000 (64-bit, non-prefetchable) [size=4M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 4000 [size=64]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [90] MSI: Enable+ Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 2
    Capabilities: [a4] PCI Advanced Features
    Kernel driver in use: i915
    Kernel modules: i915

00:14.0 0c03: 8086:1e31 (rev 04) (prog-if 30 [XHCI])
    Subsystem: 17aa:3977
    Flags: bus master, medium devsel, latency 0, IRQ 25
    Memory at d8700000 (64-bit, non-prefetchable) [size=64K]
    Capabilities: [70] Power Management version 2
    Capabilities: [80] MSI: Enable+ Count=1/8 Maskable- 64bit+
    Kernel driver in use: xhci_hcd

```

Output for : dmesg | egrep -i 'vce|error'

```

[    0.259628] acpi PNP0A08:00: _OSC failed (AE_ERROR); disabling ASPM
[    4.376977] [drm] Found VCE firmware/feedback version 50.0.1 / 17!
[    4.481489] radeon 0000:01:00.0: VCE init error (-110).
[   28.003468] EXT4-fs (sda2): re-mounted. Opts: errors=remount-ro
[   37.756122] radeon 0000:01:00.0: VCE init error (-110).
[   47.996185] radeon 0000:01:00.0: VCE init error (-110).


```

Anybody knows how to fix this?

Thanks in advance =)

---

### Post by QDR06VV9 on 2016-04-27
It is a known bug see this:[https://duckduckgo.com/?q=37.756122]+radeon+0000%3A01%3A00.0%3A+VCE+init+error+%28-110%29&t=seamonkey](https://duckduckgo.com/?q=37.756122]+radeon+0000%3A01%3A00.0%3A+VCE+init+error+%28-110%29&t=seamonkey)

---

