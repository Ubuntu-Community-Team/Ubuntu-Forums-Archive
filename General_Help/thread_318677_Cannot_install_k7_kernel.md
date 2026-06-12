---
title: "Cannot install k7 kernel"
date: 2006-12-14
forum: General Help
---

### Post by pthanos on 2006-12-14
Hello everyone,

I am not able to install the k7 kernel in a fresh(well, almost) edgy install. I have installed the
linux-image-k7 and linux-k7 packages. Nothing happens though, something very tiny is 
downloaded and no changes are made in Grub.

The k7 packages are marked as obsoleted by linux-generic.

What should I do?

---

### Post by mcduck on 2006-12-14
In edgy there's no need for K7 kernel, the generic one handles all 32-bit CPU's and multicore/multi-cpu systems. The k7 kernel has been removed, and the packages that are available are just metapackages pointing to the generic kernel, for people upgrading from Dapper.

---

### Post by pthanos on 2006-12-14
Ooh...So no need for a special kernel anymore? The generic one will use the correct "optimizations" for an Athlon-type processor?

---

### Post by mcduck on 2006-12-14
exactly.

---

### Post by javroch on 2007-02-12
just as a note i am experiencing trouble with the fact that there is no -k7 kernel.. the -generic kernel messes with my graphics card drivers and video does not show up properly on the second display.. in dapper, the only way i could get rid of the problem was install the -k7 kernel, which was not installed by default.. in edgy, there seems to be no way around it as the -k7 kernel is gone

---

### Post by bionnaki on 2007-02-12
you can always compile your own kernel

---

