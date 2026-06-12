---
title: "how to hdparm usb harddrive"
date: 2008-03-27
forum: General Help
---

### Post by afeasfaerw23231233 on 2008-03-27
i have plugged in a usb harddrive. how can i do hdparm on it? thanks.

---

### Post by zamb on 2008-03-27
You don't!.

"hdparm" is a utility to set (or clear) parameters for hard disks  connected to a Parallel ATA, Serial ATA, and/or (in some cases) an SCSI bus.

Here's a quote from "hdparm" manual page:
> **DESCRIPTION**
**hdparm** provides a command line interface to various hard disk ioctls supported by the Linux SATA/PATA/SAS "libata" subsystem and the older IDE driver subsystem.  Some options may work correctly only with the latest kernels.

You don't need, nor you can, do that on a hard disk connected to a USB device.


Ziyad.

---

### Post by afeasfaerw23231233 on 2008-03-27
oh, thank. i am never able to do this on a usb disk. that means there's no way beside plug it into the box directly if i want to see the detail information of the disk!

---

### Post by zamb on 2008-03-27
Excuse me... but what, exactly, do you mean by> i want to see the detail information of the disk!

If all you want is to browser and open the files in that USB hard disk then just plug it in your system and a "USB hard disk" icon should appears on the desktop, double click on it, and there you go.

If you want some information about the USB disk then:
[LIST][*]use "Disk Usage Analyser" from "Applications" > "Accessories" menu, or
[*]use "Hardware Information" from "System" > "Preferences" menu.[/LIST]

"hdparm" is used to set up (or clear) some aspect of IDE hard disk drives features for performance and/or troubleshooting reasons.

Ziyad.

---

### Post by afeasfaerw23231233 on 2008-03-27
thanks

---

### Post by afeasfaerw23231233 on 2008-04-08
actually i want to view the information that i get in hdparm /dev/sd? such as :
>  Model=IC35L090AVV207-0                        , FwRev=V23OA63A, SerialNo=      VNVC00G3CASB7D
 Config={ HardSect NotMFM HdSw>15uSec Fixed DTR>10Mbs }
 RawCHS=16383/16/63, TrkSize=0, SectSize=0, ECCbytes=52
 BuffType=DualPortCache, BuffSize=1821kB, MaxMultSect=16, MultSect=?16?
 CurCHS=16383/16/63, CurSects=16514064, LBA=yes, LBAsects=160836480
 IORDY=on/off, tPIO={min:240,w/IORDY:120}, tDMA={min:120,rec:120}
 PIO modes:  pio0 pio1 pio2 pio3 pio4 
 DMA modes:  mdma0 mdma1 mdma2 
 UDMA modes: udma0 udma1 udma2 udma3 udma4 *udma5 
 AdvancedPM=yes: disabled (255) WriteCache=enabled
 Drive conforms to: ATA/ATAPI-6 T13 1410D revision 3a:  ATA/ATAPI-2,3,4,5,6


---

### Post by dcstar on 2008-04-08
> **afeasfaerw23231233 said:**
> actually i want to view the information that i get in hdparm /dev/sd? such as :

That is internal to the USB disk, Linux (or any other OS) only accesses the USB interface and the limited amount of info the standard USB disk interface protocol provides - it has little or no control about what the internal disk controller of the device does.

---

