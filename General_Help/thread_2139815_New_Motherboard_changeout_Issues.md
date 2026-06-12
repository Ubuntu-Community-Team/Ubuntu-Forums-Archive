---
title: "New Motherboard changeout Issues"
date: 2013-04-27
forum: General Help
---

### Post by Cyborgoat on 2013-04-27
I changed out and upgraded my system to:

MSI NVIDIA GeForce GT 620 2GB GDDR3 VGA/DVI/HDMI Low Profile PCI-Express Video Card N620GT-MD2GD3/LP

G.SKILL Ares Series 16GB (2 x 8GB) 240-Pin SDRAM DDR3 1866 (PC3 14900) Desktop Memory F3-1866C10D-16GAB

MSI NVIDIA GeForce GT 620 2GB GDDR3 VGA/DVI/HDMI Low Profile PCI-Express Video Card N620GT-MD2GD3/LP

AMD FX 6100 6-Core Processor, 3.3 6 Socket AM3+ - FD6100WMGUSBX

GIGABYTE GA-970A-D3 AM3+ AMD 970 SATA 6Gb/s USB 3.0 ATX AMD Motherboard

The problems I've encountered were from the live boot usbs:
12.10 LTS 64 bit
12.05 LTS 32 bit
12.05 LTS 64 bit
10.05 remix
12.10 64 bit Pinguy

I have been getting initramfs errors and the ones that do boot to desktop will not either recognize my mouse and keyboard or just locks up. looking for some steps to do this change over.  I have pretty much found nothin for changing out hardware.

The drive that i have is a dual boot 2 partition containing windows 7 and ubuntu 10.04 LTS .  which is a wd 1 tb.

Thanks in advance for any help.

---

### Post by CatKiller on 2013-04-28
Sounds like either the RAM isn't seated/configured properly or is faulty. You can run memtest from any of the Ubuntu install discs.

---

### Post by Cyborgoat on 2013-04-28
I ran the memtest on the pinguy both before my post, then used the other 2 slots and ran again, still same issues..

---

### Post by Cyborgoat on 2013-04-28
I might add that the original ubuntu 10.04 on the HDD when booted into ends in the initramfs error if I could get it going I would simply updrade to 12.04 LTS from it.  Would this be the best way or new install?

---

### Post by Cyborgoat on 2013-04-28
I booted again into original ubuntu 10.04 it booted fine and mouse and keyboard works fine, however unresponsive to mouse clicks and after desktop opens keyboard does not seem to work. I _was_ able to type into the login screen.

---

