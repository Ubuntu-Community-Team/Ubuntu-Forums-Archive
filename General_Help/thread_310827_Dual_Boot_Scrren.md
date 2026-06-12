---
title: "Dual Boot Scrren"
date: 2006-12-01
forum: General Help
---

### Post by Dambrosio on 2006-12-01
I just recently updated from 6.06 to 6.10 and when i boot up my computer it shows the dual boot screen but it has 3 sets of ubuntu and ubuntu recover and then my windows boot option. Is it possible to remove 2 of those boot things?
Thanks,
Dan Ambrosio

---

### Post by styracosaurus on 2006-12-01
You should be able to comment some of the options out of /boot/grub/menu.lst.
(that's where it is on my system, I think it's default, you might have installed grub elsewhere)
Back it up first!
Then put #'s in front of each line of the choices you don't want, and be careful not to comment out anything important.

---

### Post by CatKiller on 2006-12-02
You can remove old kernels using Synaptic if your new one is working. This will also remove their entries from the list for you.

---

