---
title: "Update Graphics Needed?"
date: 2013-11-03
forum: General Help
---

### Post by LinXNut on 2013-11-03
[SIZE=3]I have been using 12.04 LTS for awhile now and I love it. Everything is working perfectly fine. One thing I have noticed however, is the graphics updates? My lspci output for my card is:[/SIZE]
```
02:00.0 VGA compatible controller: NVIDIA Corporation GT218 [GeForce 210] (rev a2) (prog-if 00 [VGA controller])
    Subsystem: eVga.com. Corp. Device 1212
    Flags: bus master, fast devsel, latency 0, IRQ 18
    Memory at df000000 (32-bit, non-prefetchable) [size=16M]
    Memory at c0000000 (64-bit, prefetchable) [size=256M]
    Memory at dc000000 (64-bit, prefetchable) [size=32M]
    I/O ports at ec00 [size=128]
    [virtual] Expansion ROM at def80000 [disabled] [size=512K]
    Capabilities: <access denied>
    Kernel driver in use: nvidia
    Kernel modules: nvidia_current, nouveau, nvidiafb

```

[SIZE=3]When I goto "Additional Drivers", this is what pops up...[/SIZE]

[IMG]http://s24.postimg.org/pczu0p8ol/Screenshot_from_2013_11_03_10_58_08.png[/IMG]

[SIZE=3]Was just curious if I need any of these updates, or if it would help??

Thank You[/SIZE]

---

### Post by BBQdave on 2013-11-03
> **LinXNut said:**
> [SIZE=3]I have been using 12.04 LTS for awhile now and I love it. Everything is working perfectly fine. One thing I have noticed however, is the graphics updates?[/SIZE]

If your system is functioning fine with the included video driver, through the Kernel Linux, I would leave it :D

Sometimes applications, such as graphic intensive video games or video editing, require the proprietary video driver. In my humble opion, you are better off using the video driver provided by the Kernel Linux - which is updated normally as you update your system.

---

