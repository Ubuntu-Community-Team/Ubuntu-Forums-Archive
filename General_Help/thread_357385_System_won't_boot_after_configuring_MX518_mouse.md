---
title: "System won't boot after configuring MX518 mouse"
date: 2007-02-09
forum: General Help
---

### Post by LycoLoco on 2007-02-09
Hi all - I'm having a bit of a problem. Ubuntu doesn't want to boot anymore - the system hangs when it gets to this line in the boot process:
```
[17179574.168000] hdb: hdb1 hdb2 hdb3
```
The line after that should be dealing with my DVD drives, but I tried commenting both of those out of fstab and the OS still wouldn't boot. As of right now, I have no way to get to a command line of any kind, so commands are of no help.
Here's where the system hangs - [http://lycoloco.thephlogiston.com/files/images/linux.jpg](http://lycoloco.thephlogiston.com/files/images/linux.jpg) At this point I can't get to a terminal or anything, including ctrl-alt-del to reboot the system. The only thing I can do at this point is press the power or reset button.

I poked around in /var/log and found out this is what should be happening on boot right after where it hangs

```
[17179574.776000] hdb: cache flushes supported
[17179574.776000]  hdb: hdb1 hdb2 hdb3 ###(this is the line where it fails)###
[17179574.808000] hdd: ATAPI 48X DVD-ROM DVD-R CD-R/RW drive, 2048kB Cache, UDMA(66)
[17179574.808000] Uniform CD-ROM driver Revision: 3.20
[17179575.320000] sata_sil 0000:05:0a.0: version 0.9
[17179575.320000] ACPI: PCI Interrupt Link [APC4] enabled at IRQ 19
[17179575.320000] ACPI: PCI Interrupt 0000:05:0a.0[A] -> Link [APC4] -> GSI 19 (level, low) -> IRQ 233
[17179575.320000] sata_sil 0000:05:0a.0: Applying R_ERR on DMA activate FIS errata fix
[17179575.320000] ata5: SATA max UDMA/100 cmd 0xF8864080 ctl 0xF886408A bmdma 0xF8864000 irq 233
[17179575.320000] ata6: SATA max UDMA/100 cmd 0xF88640C0 ctl 0xF88640CA bmdma 0xF8864008 irq 233
[17179575.320000] ata7: SATA max UDMA/100 cmd 0xF8864280 ctl 0xF886428A bmdma 0xF8864200 irq 233
[17179575.320000] ata8: SATA max UDMA/100 cmd 0xF88642C0 ctl 0xF88642CA bmdma 0xF8864208 irq 233
```

Sometimes it boots fine (usually after I've booted into Windows for a significant number of hours, for some reason), other times I just get halted at that point. If I reboot and try it multiple different times, it usually won't work, but if I boot into Windows for a while then try Ubuntu again, it boots just fine. I don't understand what's going on, but as far as I can see, the filesystem is fine and the drive doesn't seem to have any problems in Windows (using the Ext3 driver).

Any help would be greatly appreciated. Thanks in advance!

Edit: Removed notes about configuring the mouse because apparently it was just a strange coincidence

---

### Post by LycoLoco on 2007-02-10
*Bump*

Anyone have any clue what might be going on?

---

### Post by LycoLoco on 2007-02-10
*bump* 

I changed the subject because apparently it's just an oddity that happened to occur at the same time I tried to set up my mouse. Any help would be greatly appreciated.

---

### Post by gradedcheese on 2007-02-10
will it boot in recovery mode?

---

### Post by LycoLoco on 2007-02-10
Nope, it won't boot in recovery, which is why I knew exactly where it was failing and how I could take the snapshot. It just freezes there, and I have waited to see if it'll eventually boot, but waiting even 10 minutes does nothing.

---

### Post by gradedcheese on 2007-02-10
Sounds like a hardware problem.  I believe that you can use the Ubuntu CD to boot up in a rescue mode, allowing you to inspect your file system and run fsck on the hard disks.  Before that, try booting with an older kernel (you can select them from the grub menu).

---

### Post by LycoLoco on 2007-02-11
Alrighty - I got back into Ubuntu after spending an hour in XP, so you say I should just run fsck on all of my drives? Also, when this problem occurs, I have tried the three kernels that I have and it has the same problem with every one of them.

---

