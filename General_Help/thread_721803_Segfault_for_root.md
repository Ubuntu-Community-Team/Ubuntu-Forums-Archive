---
title: "Segfault for root"
date: 2008-03-11
forum: General Help
---

### Post by mpgarate on 2008-03-11
I get a segfault for the super user for the following apps, possibly more

> mike@mike-laptop:~$ sudo synaptic 
Segmentation fault (core dumped)
mike@mike-laptop:~$ sudo gedit
Segmentation fault (core dumped)
mike@mike-laptop:~$ 


---

### Post by Nzer24 on 2008-03-11
That's really strange. Try and reinstall the offending programs, or compiling them from source if you have a uncommon system setup. Does it only happen with root? Root shouldn't have special segmentation properties.

---

### Post by mpgarate on 2008-03-11
yep just root. tried removing, then reinstalling gedit, same error. might just re-install?

---

