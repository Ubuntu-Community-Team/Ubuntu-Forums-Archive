---
title: "Building a RAID-enabled server from older bits..."
date: 2007-12-02
forum: General Help
---

### Post by rotaryracer on 2007-12-02
All, I'm fairly new to Linux (running Ubuntu 7.10 Desktop) and have a few questions about building another Ubuntu box.

Currently I have Ubuntu 7.10 Desktop running on an Athlon 1.0gHz with 768MB of RAM.  Primary use is a file and print server.  I have a 20GB IDE drive for filesystem and swap, 2x160GB software RAID0 for temp storage (plugged into the HPT370 but not using Highpoint for RAID), and 4x200GB software RAID5 off a Promise Ultra133 controller.  For awhile, I had 2x250GB software RAID0 on the other two HPT370 ports, but the drives failed and I got to experience a RAID0 crash in all it's glory.  This is all running on an ancient ABIT KT7-RAID mobo with a VIA KT133 chipset that just about defined instability in Windows.  :)

I have another PC I'm thinking about upgrading and could use some feedback on the spec.  This would become the primary file and print server for my house (about 6-8 PCs total) and be used for backups, serving up video and music files, etc.

[LIST]
[*]ABIT IC-7G Intel 845 chipset
[*]2GB RAM
[*]Pentium IV 3.0gHz
[*]3ware 9500s PCI SATA hardware RAID card
[*]2x36GB Raptors in RAID1 using Linux software RAID (Intel ICH5 ports) for filesystem
[*]4x500GB Seagates in hardware RAID5 (3ware ports)
[*]IDE optical drives (DVD-ROM and DVD-RW)
[*]Intel Pro 1000CT 10/100/1000 Ethernet (onboard; running at 100bT)
[/LIST]

I'd probably yank and sell the 7800GS AGP card that's in there and replace it with a passively-cooled low budget card.

I'm curious as to whether it's worth it to pop for the 3ware card versus getting a lower budget SATA PCI controller card and using Linux software RAID (I would not use the card's softRAID).  Right now I'm doing Linux software RAID5 on the Athlon and have had some weird glitches - not sure if it's due to softRAID, the VIA chipset, the Promise IDE controller, or some evil collaboration of all.

Any thoughts or feedback for a Ubuntu newb trying to ween off XP would be greatly appreciated!

Thanks...

Jason

---

### Post by njparton on 2007-12-02
I've run a 3ware 9500S card in the past and I run a 9650SE card now (see sig).

They're excellent cards but expensive unless you can find a used one on ebay. They're far superior to software raid, especially if you have a slow cpu.

Never tired one in raid 0, but under raid 1 I've tried their re-build capabilities on 2x750GB SATA drives and I'm impressed.

3ware cards also have the advantage of having drivers built into the linux kernel unlike software raid. If you choose the latter make sure the manufacurer has drivers available, not all have (Highpoint do for e.g.).

---

### Post by njparton on 2007-12-02
PS just re-read your post - raid 5 is quite intensive so definitely go for hardware raid if you're planning to attempt that. With 3ware cards you can migrate from raid 1 to raid 5 too without losing your data.

---

