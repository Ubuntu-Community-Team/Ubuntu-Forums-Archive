---
title: "Remove ubuntu and grub"
date: 2006-08-16
forum: General Help
---

### Post by Typo on 2006-08-16
Hello I need to uninstall ubuntu and the grub bootloader from my pc.

I'm on a duel boot with xp,
i have 2 hard disks but when I wipe the one wid ubuntu on the grub bootloader is still there.

so how do i remove both ubuntu and the grub bootloader without messing it up.

Cheers

---

### Post by PacShady on 2006-08-23
You'll need to use your XP CD to boot up into Rescue mode. At the prompt, type
```
fixmbr
```

That should rewrite Windows boot loader overtop of GRUB.

'Shady

---

### Post by bigken on 2006-08-23
in the repair console 

type fixmbr
then fixboot 
then exit 

your back into windows ;)

---

