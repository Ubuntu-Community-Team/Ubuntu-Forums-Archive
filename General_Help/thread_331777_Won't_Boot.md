---
title: "Won't Boot"
date: 2007-01-05
forum: General Help
---

### Post by gibbylinks on 2007-01-05
Hi Folks,

My linux system has suddenly stopped booting, I don't think it's Linux related as it's prompting me for a floppy disk, or CD saying it can't see a hard drive. But the strange thing is if I boot from the live CD I can mount the hard drive, and see all the files ?

Oh I should also say that the first time it did it I'd left a USB drive connected. Could it be looking for that ? Although the USB only has data files on it and no OS and not capable of being booted.

Can anyone give me any pointers on where to look. 

It's running Edgy & Beryl, linux being the only OS on the machine. GRUB is installed but I think that's just for kernel updates. It doesn't get as far as GRUB though.

Thanks :confused:

---

### Post by reclusivemonkey on 2007-01-05
Did you make any changes in your BIOS? Check the BIOS can see all the hard drives and make sure all your cables or fully pushed in.

---

### Post by gibbylinks on 2007-01-06
Hi

Sorted it out. It appears I'd lost grub, I followed the instructions on this thread [http://www.ubuntuforums.org/showthread.php?t=224351](http://www.ubuntuforums.org/showthread.php?t=224351) reinstalled grub and now it works fine.

It pays to keep a copy of the live CD to hand just in case anything like this happens. At least then you can get internet access to sort things out.

Thanks:mrgreen:

---

