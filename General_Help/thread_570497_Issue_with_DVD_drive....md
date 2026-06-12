---
title: "Issue with DVD drive..."
date: 2007-10-08
forum: General Help
---

### Post by LaRoza on 2007-10-08
> 
 DVD drive not recognized

The ata_piix SATA driver grabs ownership over the IDE ports when it is loaded, but (by default) does not support PATA ATAPI devices such as the Ultrabay optical drives. Thus, if the ide driver is compiled as a module and loaded after ata_piix, the DVD drive will not be recognized by either driver.

Either of the following configurations will work:

* For kernel 2.6.14 and newer: enable ATAPI support in the SATA system using libata.atapi_enabled=1 (see below; this is experimental).
* Compile IDE into the kernel (non-module).
* Compile both IDE and SATA as modules and make sure IDE is loaded first (the module is called 'ide_generic').

Note that the optical drive must be in the Ultrabay during system boot (Ultrabay device swapping is currently unsupported).


This is for my new laptop, and I found the above guide. I don't know what to do exactly. Can someone help with one of the options?

[http://www.thinkwiki.org/wiki/Proble...SATA_and_Linux](http://www.thinkwiki.org/wiki/Proble...SATA_and_Linux)

---

### Post by ddrichardson on 2007-10-09
You should be able to add libata.atapi_enabled=1 to the boot line in gurb to see if it works, if it does then add it to grub.lst

---

### Post by LaRoza on 2007-10-09
> **ddrichardson said:**
> You should be able to add libata.atapi_enabled=1 to the boot line in gurb to see if it works, if it does then add it to grub.lst

Thanks! I'll try it. I thought it involved compiling the kernel.

---

