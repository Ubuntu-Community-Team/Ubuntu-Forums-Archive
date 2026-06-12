---
title: "dev's instead of UUID's in grub menu?"
date: 2007-06-15
forum: General Help
---

### Post by wags08 on 2007-06-15
Is there something I can change to make the grub menu have root=/dev/hda1 (or whatever) instead of root=UUID=XXXXXXXXX?

Everytime new kernel's are installed, it regenerates the grub menu after we've manually edited all the UUID's to dev's.  We regularly image our machines to others, so this causes a bit of a problem.

Thanks for your help.

---

### Post by confused57 on 2007-06-15
> **wags08 said:**
> Is there something I can change to make the grub menu have root=/dev/hda1 (or whatever) instead of root=UUID=XXXXXXXXX?

Everytime new kernel's are installed, it regenerates the grub menu after we've manually edited all the UUID's to dev's.  We regularly image our machines to others, so this causes a bit of a problem.

Thanks for your help.
Update-grub is run whenever a kernel is updated and it uses the groot entry to determine what to use for your kernel root...you can probably change it to /dev/hda1:
[http://users.bigpond.net.au/hermanzone/p15.htm#groot](http://users.bigpond.net.au/hermanzone/p15.htm#groot)

---

