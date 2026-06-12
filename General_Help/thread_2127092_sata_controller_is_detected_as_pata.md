---
title: "sata controller is detected as pata"
date: 2013-03-19
forum: General Help
---

### Post by lvm on 2013-03-19
I've got asrock 990fx extreme4 motherboard with 8 sata channels, 6 on AMD SB950 and 2 on Marvell SE9120. Not only Marvell is detected as PATA, but also as PATA with a 40-wire cable, and limited to UDMA/33. 

/var/log$ grep<dmesg ata9
[    2.604134] ata9: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0xf000 irq 14
[    2.780511] ata9.00: ATA-8: Hitachi HDS722020ALA330, JKAOA20N, max UDMA/133
[    2.780513] ata9.00: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.780715] ata9.01: ATA-8: Hitachi HDS722020ALA330, JKAOA20N, max UDMA/133
[    2.780717] ata9.01: 3907029168 sectors, multi 16: LBA48 NCQ (depth 0/32)
[    2.780720] ata9.00: limited to UDMA/33 due to 40-wire cable
[    2.780722] ata9.01: limited to UDMA/33 due to 40-wire cable
[    2.796506] ata9.00: configured for UDMA/33
[    2.812517] ata9.01: configured for UDMA/33

There is an IDE/AHCI BIOS setting for Marvell controller, but changing it has no effect. Any ideas?

System is not the latest one - Linux server 3.0.0-32-generic-pae #50-Ubuntu SMP Thu Feb 28 22:53:48 UTC 2013 i686 athlon i386 GNU/Linux, I know that and looking for advice other that upgrading.

---

### Post by mocha on 2013-11-16
The problem is related to a BIOS setting and the SATA port the hard drive is connected to on the motherboard.  In your BIOS settings you will find a setting called "sata ide combined mode".  If it is enabled it causes SATA ports 4 and 5 (and possibly 6) to act like PATA compatible ports for SATA optical drives.  So if you have an SATA optical drive then keep the setting enabled and move your hard drives to SATA ports 1, 2, or 3 and optical drive to 4 or 5.  Anyway, I had the same problem and this solved it for me so hopefully you can try it out.

---

