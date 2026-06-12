---
title: "Restore Grub"
date: 2006-07-20
forum: General Help
---

### Post by gruvsyco on 2006-07-20
I've been playing around with other distros while keeping Ubuntu as my primary Linux but in the process, for example, SuSE is running the grub config from it's install so, I've got...

Windows on hda1
Ubuntu on hdb1
SuSE on hdb3

I think grub is actually installed to hda1 but is reading it's config from hdb3...  /boot/grub.  I still have a grub config on hdb1 /boot/grub.

Basically, I want to get rid of SuSE now and revert back completely to Ubuntu.

---

### Post by Ramses de Norre on 2006-07-20
in terminal:```
sudo grub
root (hd1,2)
setup (hd0)
quit
```

---

### Post by gruvsyco on 2006-07-20
Thanks, you got me in the ballpark.  What I wanted was actually root (hd1,0).

Appreciate the help though :)

---

