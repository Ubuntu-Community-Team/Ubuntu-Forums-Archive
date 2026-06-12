---
title: "Cant find the correct dilesyst to recover ubuntu bootloader"
date: 2016-03-04
forum: General Help
---

### Post by Christos_Michael on 2016-03-04
I have windows 10 and Ubuntu 14.04 as dualboot on my laptop.

I deleted bootloader by mistake from disk management. and i am on the grub rescue.

When i tried ls i get this

hd0 hd0,msdos2 hd0,msdos1
I checked all of them by

set prefix=hd0,msdos..)
But when i type insmod normal i am getting unknown filesystem.

---

### Post by matt_symes on 2016-03-04
Thread moved to **General Help**

---

### Post by yancek on 2016-03-04
You will need to be more specific about how you "deleted the bootloader", exactly what you did.  Having windows 10, you probably have an EFI system which should have an EFI partition with windows/Linux boot files.  Is this what you deleted or did you just delete the Ubuntu files?  If you don't use EFI, did you delete a separate boot partition or the entire Ubuntu filesystem?

---

