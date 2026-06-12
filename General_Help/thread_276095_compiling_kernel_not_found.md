---
title: "compiling: kernel not found"
date: 2006-10-12
forum: General Help
---

### Post by F3nr1L on 2006-10-12
Well my network card is not naturally supported by ubuntu, so I was going about installing a driver myself. I installed all the gcc packages from the live CD(after making it a rep), rebooted, and tried the "make" command(after the other correct commands, of course). It comes up with an error that it cannot find the kernel.(I do not recall the exact error and am on my windows partition.) So what do I need to install to no longer get this error?

---

### Post by F3nr1L on 2006-10-13
No Reply? Pity. Is there an insufficient amount of information?

---

### Post by nikhilk on 2006-10-13
Please specify the make and model of the NIC you are trying to setup.
My friend had the same problem with a DLink card.

---

### Post by F3nr1L on 2006-10-13
Oh. I have a VIA Rhine 2 Ethernet Adapter, sorry about forgetting that.

---

### Post by nikhilk on 2006-10-14
The driver for the chipset "VIA Rhine" is already present in the "/lib/modules/<KERNEL_VERSION>/kernel/drivers/net/" directory. I guess you should be able to use that. Let us know if it works or not.

---

