---
title: "HP Stream SD Flash Controller"
date: 2018-03-18
forum: General Help
---

### Post by faulky86 on 2018-03-18
I recently went from windows to linux, and now I can access my SD card. Can somebody help please?

I tried to follow instructions already posted online and am still stuck

typed in lspci and got this

```
00:14.7 SD Host controller: Advanced Micro Devices, Inc. [AMD] FCH SD Flash Controller (rev 01) (prog-if 01)
    Subsystem: Hewlett-Packard Company FCH SD Flash Controller
    Flags: bus master, 66MHz, medium devsel, latency 39, IRQ 16
    Memory at fea6c000 (64-bit, non-prefetchable) [size=256]
    Capabilities: <access denied>
    Kernel driver in use: sdhci-pci
    Kernel modules: sdhci_pci
```

I'm guessing this is my Sd card reader?

---

### Post by coffeecat on 2018-03-18
Welcome to the forum.

I'm assuming you mean you **can't** access your SD card rather than "can access" as you wrote.

My guess is that it might be the way the SD card is formatted rather than the SD reader itself that is the problem. If you have an SDXC card, greater than 32GB, it will almost certainly be formatted exfat rather than FAT32. You need to install a couple of packages to be able to read and write to exfat.

What is the capacity of the SD card?

Also - which release and flavour of Ubuntu are you running?

Oh, and *Thread moved to **General Help**.* The Installation & Upgrades sub-forum is for help with installing or upgrading your operating system.

---

### Post by faulky86 on 2018-03-18
Thank you for moving, yes I mean't "can't access". I've tried an 8gb and a 32gb card in it so far and neither is visible.

I'm using ubuntu 17.10

---

### Post by faulky86 on 2018-04-04
Bump

---

