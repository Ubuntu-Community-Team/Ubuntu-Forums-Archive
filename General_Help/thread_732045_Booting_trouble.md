---
title: "Booting trouble"
date: 2008-03-22
forum: General Help
---

### Post by astyler on 2008-03-22
Searched around but couldn't find an old thread on this.

I am having trouble booting my Ubuntu 64 system.  It will only boot about 15-20% of the time, the other times, after I select it in grub, it starts to boot, screen loses video signal (standard) and the login screen never shows.

This is not a problem with my splash settings, I checked that and it did not help.

When I boot into recovery mode, I can see the problem, but I don't know how to access those logs to copy the text.  The jist is:

blah blah blah
22:  USB HID loaded
*long pause*
56:  ata3 failed to ....
56:  ata3 blah
56:  ata3 blah
56:  ata3 failed to recover some devices, retrying in 5s.

then in about 20s it fails again and cycles indefinately.

All I could find on google was other people with the exact  same problem, and somebody saying that the USB controller and SATA controller were on the same IRQ port.  My SATA drive shows up in BIOS just fine (and I tried 3 different SATA drives). 

I did find someone responded with a one word answer "irqpoller" but I don't know what that is supposed to mean.

Anyone know how to get this working? It is really frustrating.

---

### Post by astyler on 2008-03-22
It's very similiar to this fellow's output from another google search:

> 
> > [   25.126842] usb 1-1: new full speed USB device using ohci_hcd and
> > address 3
> > [   25.359792] usb 1-1: configuration #1 chosen from 1 choice
> > [   25.462838] ata2.00: ATAPI, max UDMA/33
> > [   25.462842] ata2.01: ATAPI, max MWDMA2
> > [   55.438931] ata2.00: qc timeout (cmd 0xef)
> > [   55.438939] ata2.00: failed to set xfermode (err_mask=0x4)
> > [   55.438944] ata2: failed to recover some devices, retrying in 5 secs
> > [   90.898976] ata2.00: qc timeout (cmd 0xef)
> > [   90.898982] ata2.00: failed to set xfermode (err_mask=0x4)
> > [   90.898988] ata2.00: limiting speed to UDMA/33:PIO3
> > [   90.898990] ata2: failed to recover some devices, retrying in 5 secs
> > [  126.359024] ata2.00: qc timeout (cmd 0xef)
> > [  126.359030] ata2.00: failed to set xfermode (err_mask=0x4)
> > [  126.359034] ata2.00: disabled
> > [  126.359036] ata2: failed to recover some devices, retrying in 5 secs
> > [  131.359086] ata2.01: failed to set xfermode (err_mask=0x40)
> > [  131.359090] ata2: failed to recover some devices, retrying in 5 secs
> > [  136.843003] ata2.01: configured for MWDMA2
> > [  136.843133] scsi 0:0:0:0: Direct-Access     ATA      ST3120026A
> > 3.06 PQ: 0 ANSI: 5
> > [  136.843510] scsi 0:0:1:0: Direct-Access     ATA      WDC WD600BB-32BS
> > 12.0 PQ: 0 ANSI: 5
> > [  136.844084] scsi 1:0:1:0: CD-ROM            CREATIVE  CD5233E
> > 2.05 PQ: 0 ANSI: 5
> > [  136.863844] SCSI device sda: 234441648 512-byte hdwr sectors (120034
> > MB)
> > [  136.863877] sda: Write Protect is off


---

### Post by astyler on 2008-03-22
Should I apply this patch?  I don't know if this is for my kernel or drivers but this "tejun" guy seems to be the only one who knows what to do about this.

Patch:
[http://marc.info/?l=linux-ide&m=119673687412094&q=p3](http://marc.info/?l=linux-ide&m=119673687412094&q=p3)

As per: 
[http://marc.info/?l=linux-ide&m=119673687412094&w=2](http://marc.info/?l=linux-ide&m=119673687412094&w=2)

---

### Post by astyler on 2008-03-22
Or, apply:

[http://bugzilla.kernel.org/attachment.cgi?id=13903&action=view](http://bugzilla.kernel.org/attachment.cgi?id=13903&action=view)

as per:
[http://bugzilla.kernel.org/show_bug.cgi?id=9505](http://bugzilla.kernel.org/show_bug.cgi?id=9505)
post #19

---

### Post by astyler on 2008-03-22
bump

---

