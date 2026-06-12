---
title: "What's better? hda or emuled scsi (sda)"
date: 2007-06-21
forum: General Help
---

### Post by saul_2110 on 2007-06-21
Misteriosly  my hard disk drive, being an IDE device, got the DMA feature activated to its maximun (ultra dma mode 5) in Feisty... yet, I wonder if using UDMAmode5 in emuled SCSI (as does Feisty) reaches the same or very close to the performance achieved using true IDE device driver.
Should I go back to Dapper? (so I get the best performance?)
Thanks.

---

### Post by spartan777 on 2007-06-21
i really doubt using the emulated scsi mode would speed up anything up. anyways, unless you have a 15k rpm, your hard drive isn't going to be going so fast that dma5 would limit it. and if you don't know what 15k rpm means, then you don't have that kind of hard drive. don't worry about being in the dma mode you mentioned, I don't really know what 'emulated scsi mode' is, but emulated anything isn't ever faster than the normal.

---

### Post by Sencer on 2007-06-21
> **saul_2110 said:**
> in emuled SCSI (as does Feisty) reaches the same or very close to the performance achieved using true IDE device driver.
Should I go back to Dapper? (so I get the best performance?)

There is no emulation involved, it's simply a different driver using a different interface. There were mainly implementation reasons for the "change". Looking into the future you can be sure that the libata drivers will be better maintained (since they apparently have cleaner code etc.), so unless you have a thing for legacy code, or you experienced concrete driver problems there is no reason to try to force the older drivers. (Any you wouldn't need to go back to dapper, since the legacy drivers will continue t be in the kernel for a long time to come)

---

### Post by saul_2110 on 2007-06-21
Thanks for your answers!

> **Sencer said:**
>  so unless you have a thing for legacy code, or you experienced concrete driver problems there is no reason to try to force the older drivers. 

What do you mean by forcing them?

> **Sencer said:**
> (Any you wouldn't need to go back to dapper, since the legacy drivers will continue t be in the kernel for a long time to come)

But how can I choose to use those legacy drivers? It's really for my peace of mind. ;)

[CODE=spartan777;2885659]your hard drive isn't going to be going so fast that dma5 would limit it[/CODE]

I actually want my hard drive with udma5 activated. The thing is, when I first installed Feisty, it was at udma3. And giving that the hard drive was recognized as a scsi disk, I coulnd't use hdparm to change the dma mode.

Bottom line is... should I expected a decrease in performance that Feisty uses 'sda' instead of the 'hda' driver (giving that my hard disk is IDE/pata)?

---

