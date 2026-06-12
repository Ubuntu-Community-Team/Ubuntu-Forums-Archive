---
title: "Error during boot"
date: 2022-05-06
forum: General Help
---

### Post by mickee384 on 2022-05-06
HI

I get the following error during boot, and this happens prior to Plymouth displaying splash screen and I am hoping to get some help to fix the issue:

```
May 06 09:21:24 mickeymouse kernel: ata1: SATA link up 3.0 Gbps (SStatus 123 SControl 300)
May 06 09:21:24 mickeymouse kernel: **ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT0._GTF.DSSP], AE_NOT_FOUND (20210730/psargs-330)**
May 06 09:21:24 mickeymouse kernel: fbcon: Taking over console
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: No Local Variables are initialized for Method [_GTF]
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: No Arguments are initialized for method [_GTF]
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: **ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT0._GTF due to previous error (AE_NOT_FOUND) (20210730/psparse-529)**
May 06 09:21:24 mickeymouse kernel: Console: switching to colour frame buffer device 240x67
May 06 09:21:24 mickeymouse kernel: ata6: SATA link down (SStatus 4 SControl 300)
May 06 09:21:24 mickeymouse kernel: ata2: SATA link up 1.5 Gbps (SStatus 113 SControl 300)
May 06 09:21:24 mickeymouse kernel: ata5: SATA link down (SStatus 4 SControl 300)
May 06 09:21:24 mickeymouse kernel: usb 1-1.4: New USB device found, idVendor=04f2, idProduct=1061, bcdDevice= 4.00
May 06 09:21:24 mickeymouse kernel: usb 1-1.4: New USB device strings: Mfr=1, Product=2, SerialNumber=0
May 06 09:21:24 mickeymouse kernel: usb 1-1.4: Product: Wireless Device
May 06 09:21:24 mickeymouse kernel: usb 1-1.4: Manufacturer: Chicony
May 06 09:21:24 mickeymouse kernel: **ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT1._GTF.DSSP], AE_NOT_FOUND (20210730/psargs-330)**
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: No Local Variables are initialized for Method [_GTF]
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: No Arguments are initialized for method [_GTF]
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel:** ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT1._GTF due to previous error (AE_NOT_FOUND) (20210730/psparse-529)**
May 06 09:21:24 mickeymouse kernel: ata2.00: ATAPI: hp       DVDRAM GT50N, R703, max UDMA/100
May 06 09:21:24 mickeymouse kernel: hid: raw HID events driver (C) Jiri Kosina
May 06 09:21:24 mickeymouse kernel: **ACPI BIOS Error (bug): Could not resolve symbol [\_SB.PCI0.SAT0.SPT1._GTF.DSSP], AE_NOT_FOUND (20210730/psargs-330)**
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: No Local Variables are initialized for Method [_GTF]
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: No Arguments are initialized for method [_GTF]
May 06 09:21:24 mickeymouse kernel: 
May 06 09:21:24 mickeymouse kernel: **ACPI Error: Aborting method \_SB.PCI0.SAT0.SPT1._GTF due to previous error (AE_NOT_FOUND) (20210730/psparse-529)**

```

Please let me know if you can assist me with this. The above is from the boot log

---

