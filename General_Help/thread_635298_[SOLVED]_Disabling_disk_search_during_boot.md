---
title: "[SOLVED] Disabling disk search during boot"
date: 2007-12-08
forum: General Help
---

### Post by rich257 on 2007-12-08
My system is fairly slow to boot.  It seems that this is because modprobe is searching for disks on ide0 during boot, but there aren't any on that channel, only on ide1 and on the SATA interface.

While I could go and unplug and replug the cables so that the both IDE interfaces have devices on them, is there a way to instruct modprobe not to look on ide0?

Here's an excerpt from dmesg:
```

[   49.449959] Floppy drive(s): fd0 is 1.44M
[   49.522755] FDC 0 is a post-1991 82077
[   54.636675] hda: IRQ probe failed (0xffffedb8)
[   59.857576] hda: IRQ probe failed (0xffffedb8)
[   59.857586] hda: no response (status = 0x0a), resetting drive
[   65.190411] hda: IRQ probe failed (0xffffedb8)
[   65.190419] hda: no response (status = 0x0a)
[   70.691149] hdb: IRQ probe failed (0xffffedb8)
[   75.912051] hdb: IRQ probe failed (0xffffedb8)
[   75.912061] hdb: no response (status = 0x0a), resetting drive
[   81.244881] hdb: IRQ probe failed (0xffffedb8)
[   81.244890] hdb: no response (status = 0x0a)
[   81.300807] Probing IDE interface ide1...
[   81.716751] hdc: ST33210A, ATA DISK drive
[   82.164484] hdd: HL-DT-ST RW/DVD GCC-4120B, ATAPI CD/DVD-ROM drive
[   82.221010] ide1 at 0x170-0x177,0x376 on irq 15

```

---

### Post by rich257 on 2007-12-09
And I have found how to do it, see [this post]("http://lkml.org/lkml/2007/6/12/156").

It's knocked about a hundred seconds off my boot time!

---

