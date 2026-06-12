---
title: "feisty boot hangs &quot;device too small for target&quot;"
date: 2007-06-18
forum: General Help
---

### Post by RobertLos on 2007-06-18
After years of happy use of ubuntu linux, I ran into a boot problem.

A few weeks ago I upgraded my edgy installation on a 500 GB disk to Feisty. It worked perfectly until yesterday. During boot the systems seemed to hang. Since I always have a small separate partition where dapper is still running I was abble to boot into the system en change the grub startup and deleted the quiet en spash option. This enabled me to look at the problem while all boot messages scrolled over the screen. There I discovered the system did oot, but had to wait for several minutes for a timeout on a harddisk device. When the systems booted 5 minutes later I took the following lines from the /var/log/messages file:
-----------------------
Jun 18 20:35:47 max-linux kernel: [   37.367797] DC10plus[0]: zr36057_init() - initializing card[0], zr=f8b756c0
Jun 18 20:35:47 max-linux kernel: [   37.614672] parport: PnPBIOS parport detected.
Jun 18 20:35:47 max-linux kernel: [   37.614845] parport0: PC-style at 0x378 (0x778), irq 7, dma 3 [PCSPP,TRISTATE,COMPAT,EPP,ECP,DMA]
Jun 18 20:35:47 max-linux kernel: [   37.701617] drivers/usb/class/usblp.c: usblp0: USB Bidirectional printer dev 3 if 0 alt 0 proto 2 vid 0x04F9 pid 0x0193
Jun 18 20:35:47 max-linux kernel: [   37.701703] usbcore: registered new interface driver usblp
Jun 18 20:35:47 max-linux kernel: [   37.701751] drivers/usb/class/usblp.c: v0.13: USB Printer Device Class driver
Jun 18 20:35:47 max-linux kernel: [   38.133989] ACPI: PCI Interrupt Link [LNKD] enabled at IRQ 19
Jun 18 20:35:47 max-linux kernel: [   38.134052] ACPI: PCI Interrupt 0000:02:07.0[A] -> Link [LNKD] -> GSI 19 (level, high) -> IRQ 20
Jun 18 20:35:47 max-linux kernel: [   38.364738] input: ImPS/2 Logitech Wheel Mouse as /class/input/input3


J[B]un 18 20:35:47 max-linux kernel: [   38.900234] device-mapper: table: device /dev/mapper/1ATA_WDC_WD2000JD-00GBB0_WD-WMAEP1588874p1 too small for target
Jun 18 20:35:47 max-linux kernel: [   38.900363] device-mapper: ioctl: error adding target to table
Jun 18 20:35:47 max-linux kernel: [   38.901138] device-mapper: table: device /dev/mapper/1ATA_WDC_WD2000JD-00GBB0_WD-WMAEP1588874p1 too small for target
Jun 18 20:35:47 max-linux kernel: [   38.901257] device-mapper: ioctl: error adding target to table
Jun 18 20:35:47 max-linux kernel: [  218.628437] device-mapper: table: device /dev/mapper/1ATA_WDC_WD2000JD-00GBB0_WD-WMAEP1588874p1 too small for target
Jun 18 20:35:47 max-linux kernel: [  218.628568] device-mapper: ioctl: error adding target to table
Jun 18 20:35:47 max-linux kernel: [  218.652390] device-mapper: table: device /dev/mapper/1ATA_WDC_WD2000JD-00GBB0_WD-WMAEP1588874p1 too small for target
Jun 18 20:35:47 max-linux kernel: [  218.652520] device-mapper: ioctl: error adding target to table[/B]


Jun 18 20:35:47 max-linux kernel: [  239.283381] lp0: using parport0 (interrupt-driven).
Jun 18 20:35:47 max-linux kernel: [  239.374050] Adding 3028212k swap on /dev/disk/by-uuid/fd9b7cf5-6fa5-421c-9f1c-23634bf98707.  Priority:-1 extents:1 across:3028212k
Jun 18 20:35:47 max-linux kernel: [  239.420958] EXT3 FS on sdb1, internal journal
Jun 18 20:35:47 max-linux kernel: [  240.559026] kjournald starting.  Commit interval 5 seconds
Jun 18 20:35:47 max-linux kernel: [  240.559147] EXT3 FS on hdb1, internal journal
Jun 18 20:35:47 max-linux kernel: [  240.559154] EXT3-fs: mounted filesystem with ordered data mode.


Can ou please help. Booting takes a long time now.

---

