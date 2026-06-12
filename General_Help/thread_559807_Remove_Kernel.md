---
title: "Remove Kernel"
date: 2007-09-25
forum: General Help
---

### Post by dje on 2007-09-25
Ive seen other threads on this but they are not really what i want. I was using kernel 2.6.20-16 until updates stopped me from connecting to any wireless networks. I booted into the default 15 kernel and the wireless works fine, great. But i still get updates for the 16 kernel, and when it updates it makes itself the default kernel. So i either want to completely, and safely remove the 16 kernel or stop it changing to the default kernel whenever it gets updated. thanks in advance

---

### Post by SPr on 2007-09-25
Update then edit /boot/grub/menu.lst

Remove the references to the latest kernel from menu.lst so it doesn't appear in the Grub menu when booting the computer.

---

### Post by dje on 2007-09-25
Thanks but thats what i did today (well i moved 15 back to the top) but if i delete it off the menu will it just appear again next time it updates?

---

### Post by SPr on 2007-09-25
Yes, it will return when the update takes place so remove the reference afterwards :)

Edit:
Are you saying that if you remove the latest version from menu.lst Ubuntu will say there is an updated kernel even though the update has already been downloaded and installed?

---

### Post by dje on 2007-09-25
Yeah but that could get quite annoying ! ;)
Could i just do sudo apt-get --purge remove?

EDIT: What i'm saying is, if i remove the 16 entry from the menu will the entry be put back (at the top) when it is updated

---

### Post by dje on 2007-09-25
Anyone?

---

### Post by zvacet on 2007-09-25
In synaptic find linux-image-2.6.20-16 and mark it for removal.After that find linux-image-2.6.20-15 and mark it.Go to the package and lock version.That way you will not get any upgrades to  your kernel.

---

