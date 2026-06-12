---
title: "cd writer not recognized by gnome"
date: 2005-10-17
forum: General Help
---

### Post by shadowhunter on 2005-10-17
Hi, this is my first post on this forum...

Just installed breezy on my laptop, and my dvd writer doesn't seem to recognized by gnome, nautilus en serpentine don't find one, cdrecord and growisofs do. 

The result of dmesg | grep hdc
```
[4294672.172000]     ide1: BM-DMA at 0xbfa8-0xbfaf, BIOS settings: hdc:DMA, hdd:pio
[4294673.721000] hdc: PHILIPS DVD+RW SDVD6004, ATAPI CD/DVD-ROM drive
[4294676.236000] hdc: ATAPI 24X DVD-ROM CD-R/RW drive, 8192kB Cache

```

this is not running under scsi emulation.

Anyone who knows a solution to this problem?

---

