---
title: "Boot hanging temporarily on ata1 and ata2"
date: 2008-06-16
forum: General Help
---

### Post by BandD on 2008-06-16
I recently been experiencing a rather long boot time with 2.6.24-18 generic.  This problem existed for me on 2.6.24-16 but seemed to be fixed with 2.6.24.18--but it's back.  

It is possible that it's a hardware issue I suppose, but I'm not really savvy enough to trouble shoot this on my own.  This is a laptop.  The only thing I've replaced is the hard drive, but I didn't mess with any of the ata plugs.   

These are the lines where the hang seems to occur from dmesg:

```
[   33.707787] ata1: PATA max UDMA/100 cmd 0x1f0 ctl 0x3f6 bmdma 0x1810 irq 14
[   33.707861] ata2: PATA max UDMA/100 cmd 0x170 ctl 0x376 bmdma 0x1818 irq 15
[   34.037244] ata1.00: ATA-7: WDC WD800BEVE-00UYT0, 01.04A01, max UDMA/100
[   34.037324] ata1.00: 156301488 sectors, multi 16: LBA48 
[   34.037420] ata1.01: ATAPI: QSI CD-RW/DVD-ROM SBW-243, TS07, max UDMA/33
[   34.052850] ata1.00: configured for UDMA/100
[   34.224588] ata1.01: configured for UDMA/33
[   34.224700] ata2: port disabled. ignoring.
```


I notice that it is trying to load two ata ports, yet I only need one.  Is there a way to tell the boot process to not even bother with ata2 at all?  This hang eats up about 30 seconds or so and it happen before the 'actual' boot processes  (i.e. if splash is enabled it happen during the ping-pong type screen, rather than the actual progress bar; if splash is not a boot option, then it happens well before the 'reading files needed to boot' process).

Any help would be greatly appreciated!

---

### Post by plucky on 2008-06-17
Why have you got your CD and Hard disk on the same controller?

Is it easy to have them on separate controllers?

Sorry ,don't know about laptops,but on desktops,it is always better to separate Cd drives and Hard drives.

If you separate them,remember to make them both master drives.


Good Luck

---

### Post by BandD on 2008-06-17
I'm not really sure.  I haven't modified anything, it's how Sony shipped the machine.  

I've always been a little nervous about popping open laptops.  But I'd be willing to give it a shot if someone could walk me through it or point me a a good guide.

If anyone is curious, it's a Sony Vaio FS620.

---

