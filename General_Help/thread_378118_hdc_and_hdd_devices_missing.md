---
title: "hdc and hdd devices missing"
date: 2007-03-06
forum: General Help
---

### Post by rogeriovinhal on 2007-03-06
Hi, I haven't been able to mount my cdroms drivers lately. I am using Edgy with a 2.6.19.2 self compiled kernel and AMD64 version of Ubuntu.

I don't know why, I always used the devices hdc and hdd for my DVD-Rom and CD-RW drivers, but none of them now appear at the /dev/ folder.

I tried dmesg | grep ata, but all I find useful about the output is this:
```

ata4.00: ATAPI, max MWDMA2
ata4.01: ATAPI, max UDMA/33
ata4.00: configured for MWDMA2
ata4.01: configured for UDMA/33

```

These are my drivers. The MWDMA2 is the CDRW, and the UDMA/33 the DVD-Rom driver. But these 'ata4.0X' before them are confusing me. Shouldn't that be the names of the devices? There is no such device names like those.

Also, there aren't and hdXY devices, nor sdbY. Only sda, sdaX, which are my Sata HD and probably the device for pen-drivers.

What can I do?

---

### Post by seldenthuis on 2007-03-06
If you kernel is using the libata driver (lsmod | grep libata), your DVD-R and CD-RW will show up as /dev/sdaX. I don't know of an easy way to figure out which device is which.

---

### Post by rogeriovinhal on 2007-03-08
It is not using libata module, lsmod | grep libata returns nothing...

Is there anything else I can try?

---

### Post by rogeriovinhal on 2007-03-09
I have some reasons to believe that the cdroms drives are now at the devices /dev/sg1 and /dev/sg2.

But If I try to mount them, it says "is not a block device".
What now?

---

