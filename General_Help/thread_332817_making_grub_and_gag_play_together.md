---
title: "making grub and gag play together?"
date: 2007-01-06
forum: General Help
---

### Post by jclmusic on 2007-01-06
i had grub installed, and tried to replace it with gag. after i installed gag, it would not boot. i assume this is because gag writed over grub? how can i install both so they either work together, or get gag to work without grub?

---

### Post by K.Mandla on 2007-01-15
I don't think that can be done straightaway. Gag wants the boot sector for itself, but then wants to jump to another bootloader -- and I think it prefers LILO -- in another partition. I haven't played with it enough to be sure how it works, but it would require installing LILO to your root partition, then installing Gag over the MBR ... and I need more free time to get any further. 

Sorry I couldn't be of more help. :roll:

---

