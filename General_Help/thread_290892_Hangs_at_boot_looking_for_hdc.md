---
title: "Hangs at boot looking for hdc"
date: 2006-11-01
forum: General Help
---

### Post by Disco Cat on 2006-11-01
I installed Edgy Eft and everything worked perfectly well.  I later discovered my CD Drive was causing problems, so I disabled it along with the floppy drive a few days later.  Since then the system hangs for about one minutes during boot-up, just after this point:

> 
Nov  1 15:47:49 server kernel: [17179573.572000] Probing IDE interface ide0...
Nov  1 15:47:49 server kernel: [17179573.988000] hda: ST380011A, ATA DISK drive
Nov  1 15:47:49 server kernel: [17179574.660000] ide0 at 0x1f0-0x1f7,0x3f6 on irq 14


When it begins probing ide1 it stops and waits, obviously because ide1 does not physically exist.  When it finally gives up it continus with the following:

> 
Nov  1 15:47:49 server kernel: [17179609.460000] ide1: Wait for ready failed before probe !
Nov  1 15:47:49 server kernel: [17179614.908000] hdc: IRQ probe failed (0xffffbdf8)
Nov  1 15:47:49 server kernel: [17179620.132000] hdc: IRQ probe failed (0xffffbdf8)
Nov  1 15:47:49 server kernel: [17179620.132000] hdc: no response (status = 0x0a), resetting drive
Nov  1 15:47:49 server kernel: [17179625.468000] hdc: IRQ probe failed (0xffffbdf8)
Nov  1 15:47:49 server kernel: [17179625.468000] hdc: no response (status = 0x0a)
Nov  1 15:47:49 server kernel: [17179630.972000] hdd: IRQ probe failed (0xffffbdf8)
Nov  1 15:47:49 server kernel: [17179636.196000] hdd: IRQ probe failed (0xffffbdf8)
Nov  1 15:47:49 server kernel: [17179636.196000] hdd: no response (status = 0x0a), resetting drive
Nov  1 15:47:49 server kernel: [17179641.532000] hdd: IRQ probe failed (0xffffbdf8)
Nov  1 15:47:49 server kernel: [17179641.532000] hdd: no response (status = 0x0a)


hdc was the cd-rom, hdd never existed at all.  I have commented out /dev/hdc and /dev/fd0 in fstab but obviously some file still asks for those devices at boot and I can't find which one.

Does anyone know what I have to do to make it forget about the old drives and just boot up normally?

(this is the 2.6.17-10-386 kernel, by the way)

---

### Post by chalex on 2006-11-01
The above messages seem to indicate a hardware problem. You should probably disable your cd-rom drive in the BIOS (or just physically remove it from your system).

---

### Post by Disco Cat on 2006-11-01
The drive has been phsyically removed from the system, that's where the problem lies.  The kernel still probes for it during bootup and because it's not plugged in it never finds it, causing a delay during boot.  There is only one drive plugged in, which is hda.

---

### Post by autocrosser on 2006-11-01
You might also take a look at your /etc/fstab & see if the unit is still listed there--if so, sudo gedit the file & remove it.

--Sorry-I should have read your post all the way thru--As the prior post said--take a look in your bios

---

### Post by Disco Cat on 2006-11-01
I went through the bios and the way I have it set up for now is the primary master is manually set as the only hard drive and to ignore secondary master, primary slave, secondary slave and floppies.  Also, going through the kernal log a bit more I noticed these lines.  It's the first time it references ide1 and hdc/hdd.  It's all greek to me, but maybe one of you guys can get something out of it.

> 
Nov  1 08:22:54 server kernel: [17179578.684000] VP_IDE: IDE controller at PCI slot 0000:00:07.1
Nov  1 08:22:54 server kernel: [17179578.684000] PCI: Via IRQ fixup for 0000:00:07.1, from 255 to 0
Nov  1 08:22:54 server kernel: [17179578.684000] VP_IDE: chipset revision 6
Nov  1 08:22:54 server kernel: [17179578.684000] VP_IDE: not 100%% native mode: will probe irqs later
Nov  1 08:22:54 server kernel: [17179578.684000] VP_IDE: VIA vt82c596b (rev 12) IDE UDMA66 controller on pci0000:00:07.1
Nov  1 08:22:54 server kernel: [17179578.684000]     ide0: BM-DMA at 0xe000-0xe007, BIOS settings: hda:DMA, hdb:pio
Nov  1 08:22:54 server kernel: [17179578.684000]     ide1: BM-DMA at 0xe008-0xe00f, BIOS settings: hdc:pio, hdd:pio


---

### Post by Disco Cat on 2006-11-01
I've found what seems to be a temporary fix for me.  I added "ide1=noprobe" to menu.lst after reading some vaguely related problems elsewhere and it has solved all my problems, until I next install a disc drive.  Thanks for the help autocrosser and chalex.

---

