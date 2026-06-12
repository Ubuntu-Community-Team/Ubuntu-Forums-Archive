---
title: "Lots of linux versions on GRUB..."
date: 2007-02-27
forum: General Help
---

### Post by Ritchstorm on 2007-02-27
I have just installed Ubuntu Dapper after windows xp. GRUB works fine, however updating it for the first time, in the GRUB menu there are more than one version of Ubuntu. There are two versions of the main kernel and two versions of the mem-test version. They both have different numbers after them but seem to boot into the same thing. Anyway of getting rid of the entries i don't want? Many thanks in advance.

---

### Post by chewearn on 2007-02-27
Everytime you update your kernel, new entries are added for the new kernel.  To remove old kernels, simply use Synaptic.  However, make sure the new kernel is 100% working before doing so.  The memtest is for troubleshooting; should leave it as it is.

---

### Post by Mateo on 2007-02-27
yeah, I always uninstall the old ones after making sure the new ones work well.

you can also edit /boot/grub/menu.lst and remove the old ones from your list (they'll still be on your hard drive though).

---

