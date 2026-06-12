---
title: "Restoring init? (kernel panic)"
date: 2008-02-17
forum: General Help
---

### Post by lapsey on 2008-02-17
Hi, It seems that a SATA crash has mangled my system once again and now the kernel cannot find init.

It says something like "Kernel Panic - not syncing: No init found; Attempting to kill init!" and halts. I only have one kernel - 2.6.22-14-generic, so booting into another one is not an option

I don't want to reinstall. the root partition is mapped correctly to grub and /boot/grub/device.map. I've run fsck on / ..

This is the third time I have tried and failed to get help on this issue, and I'm getting very close to resorting to a reinstall. :( Thanks in advance!

---

### Post by drocko on 2008-02-17
Did you recompile your kernel? Have you changed settings in your bios?

On my machine I have to set my SATA settings to compatible mode to avoid problems like this.

---

### Post by lapsey on 2008-02-17
> **drocko said:**
> Did you recompile your kernel? Have you changed settings in your bios?

On my machine I have to set my SATA settings to compatible mode to avoid problems like this.

> a SATA crash has mangled my system once again

it seems to be a driver issue with the 64-bit kernel, therefore unavoidable. I'm trying to find out how to restore init, but thanks

---

