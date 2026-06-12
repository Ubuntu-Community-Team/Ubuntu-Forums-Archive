---
title: "Ubuntu 18.04 Monitor won't come on after suspend"
date: 2018-07-03
forum: General Help
---

### Post by ultragamer2 on 2018-07-03
Since Ubuntu 17 was upgraded to 18.04 the monitor stays off and it won't wake from suspend.
I'm using an Nvidia GTX 970 video card.

It used to work fine with Ubuntu 17.

I did read a couple of threads and tried a few things but nothing worked so far.

---

### Post by ultragamer2 on 2018-08-23
It seems to only be a problem with the Nvidia driver (390) now, the Nouvea one works ok.

Any ideas, I did try one thing in another thread to change a file but the file didn't seem to exist.

---

### Post by farlander762 on 2018-11-27
I have the same issue.  Nvidia GeForce GT 420.  Was doing it with the generic driver and is still doing it with the proprietary driver.

---

### Post by Marco_Ros on 2018-12-03
[I]have the same problem, but my graphics chip is
[/I]Intel® 965GM

I've had this problem since ver 14.04 LTS, except when using a USB Keychain installation, but the installed SO behaves differently.

---

### Post by Marco_Ros on 2018-12-03
Following are the details about my computer:
```

**sudo lspci -vnn | grep -A12 VGA**
00:02.0 VGA compatible controller [0300]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (primary) [8086:2a02] (rev 03) (prog-if 00 [VGA controller])
    Subsystem: Acer Incorporated [ALI] Mobile GM965/GL960 Integrated Graphics Controller (primary) [1025:0135]
    Flags: bus master, fast devsel, latency 0, IRQ 16
    Memory at fc000000 (64-bit, non-prefetchable) [size=1M]
    Memory at d0000000 (64-bit, prefetchable) [size=256M]
    I/O ports at 1800 [size=8]
    [virtual] Expansion ROM at 000c0000 [disabled] [size=128K]
    Capabilities: [90] MSI: Enable- Count=1/1 Maskable- 64bit-
    Capabilities: [d0] Power Management version 3
    Kernel driver in use: i915
    Kernel modules: i915, intelfb

00:02.1 Display controller [0380]: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (secondary) [8086:2a03] (rev 03)

**cat /proc/cmdline**
BOOT_IMAGE=/boot/vmlinuz-4.15.0-42-generic root=UUID=695eeecd-54b7-4705-8791-60aa47a19fcf ro quiet splash noresume video=SVIDEO-1:d

```

note: I cannot find pm-suspend.log file

---

