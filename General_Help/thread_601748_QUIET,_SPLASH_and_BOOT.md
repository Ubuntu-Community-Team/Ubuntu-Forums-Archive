---
title: "QUIET, SPLASH and BOOT"
date: 2007-11-03
forum: General Help
---

### Post by stef56 on 2007-11-03
On my dell latitude D810 boot takes almost 180 seconds :( with the two mains steps :.

[   23.053414] EXT3-fs: mounted filesystem with ordered data mode.
[  119.249610] pci_hotplug: PCI Hot Plug PCI Core version: 0.5

[  128.606263] EXT3 FS on sda5, internal journal
[  152.632762] input: Lid Switch as /class/input/input5

i should notice that during the boot sequence Usplash doesn't appear :(

If I delete SPLASH and QUIET instructions in the boot, boot time is 60 seconds :)
But the recording events obtained with DMESG are totally different and of course Ubuntu splash doesn't appear.

Does anyone is able to explain the relation between SPLASH, QUIET, boot time and how to optimize the boot sequence ?

Thanks,

Stef

---

