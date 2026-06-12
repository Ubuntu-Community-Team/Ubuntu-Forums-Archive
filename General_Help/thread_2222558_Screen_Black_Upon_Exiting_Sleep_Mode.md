---
title: "Screen Black Upon Exiting Sleep Mode"
date: 2014-05-07
forum: General Help
---

### Post by Justin_Priester on 2014-05-07
I have the latest version of Ubuntu installed on my laptop. When I close the lid, the laptop goes into sleep mode successfully. When I reopen it, it does exit sleep mode but the screen is completely black. Replugging the charge cable does nothing.

---

### Post by kc1di on 2014-05-07
Could you give us a little more information about your machine.  It would help us in finding a solution for you.
Go to a terminal and type the following commands and post the out put here.

```
pastebinit /var/log/pm-suspend.log
sudo lspci -vnn | grep -A12 VGA
```

you could try booting with the nomodeset parameter - with some hardware this can be the cure , see [here]("https://wiki.ubuntu.com/Kernel/KernelBootParameters") for more details on how to do that.

---

### Post by Justin_Priester on 2014-05-07
justin@justin-HP-Pavilion-g6-Notebook-PC:~$ pastebinit /var/log/pm-suspend.log
Unable to read from: /var/log/pm-suspend.log
justin@justin-HP-Pavilion-g6-Notebook-PC:~$ sudo lspci -vnn | grep -A12 VGA
00:01.0 VGA compatible controller [0300]: Advanced Micro Devices, Inc. [AMD/ATI] Trinity [Radeon HD 7520G] [1002:9990] (prog-if 00 [VGA controller])
    Subsystem: Hewlett-Packard Company Device [103c:1849]
    Flags: bus master, fast devsel, latency 0, IRQ 49
    Memory at e0000000 (32-bit, prefetchable) [size=256M]
    I/O ports at 3000 [size=256]
    Memory at f0300000 (32-bit, non-prefetchable) [size=256K]
    Expansion ROM at <unassigned> [disabled]
    Capabilities: [50] Power Management version 3
    Capabilities: [58] Express Root Complex Integrated Endpoint, MSI 00
    Capabilities: [a0] MSI: Enable+ Count=1/1 Maskable- 64bit+
    Capabilities: [100] Vendor Specific Information: ID=0001 Rev=1 Len=010 <?>
    Kernel driver in use: radeon

---

