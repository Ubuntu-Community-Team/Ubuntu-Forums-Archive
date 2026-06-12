---
title: "Reinstall GRUB"
date: 2007-01-26
forum: General Help
---

### Post by icehammer on 2007-01-26
I had to format and reinstall windows recently, and as expected, my MBR got overweritten, so i tried to reinstall GRUB by following a couple of methods available online. However, none of them works.!!! Is there any certified way?? I'm using Edgy.

Also, how do i find my (hd?,?) values?? they're required.. but even after trying all possible values, nothing works.. please advise.

---

### Post by Ramses de Norre on 2007-01-26
Boot a live cd and run this:```
sudo grub
root (hd?,?)
setup (hd0)
quit
sudo update-grub
```
The numbers start counting from zero: (hd0) is your mbr, hda1=(hd0,0), hda2=(hd0,1), hdb1=(hd1,0), ...

---

### Post by cdwts9227 on 2007-01-26
soory,i do'nt known.:(

---

