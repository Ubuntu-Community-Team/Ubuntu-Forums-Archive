---
title: "Cant restart after sleep"
date: 2008-02-16
forum: General Help
---

### Post by fatmano on 2008-02-16
Help!!!  I am running Kubuntu Gutsy and recently installed kpowermanager to allow my laptop to sleep when I closed the the lid.  Last night it hung while trying to sleep.  Now when I restart I cant get past boot up.  The error that I see that stands out is :

RAMDISK: Couldn't find valid RAM disk image starting at 0.
VFS: Cannot open root device "801"m or unknown-block(8,1)

I am downloading a knoppix ISO now in hopes that I can remove the sleep image and just get it to boot.  What I need I think is some directions to where the file might be and if there are any flags that I need to reset.

TIA

---

### Post by kuja on 2008-02-16
Did you just put it to sleep or did you put it in hibernate? When you put it to sleep it only moves everything into RAM .. there shouldn't be any image file involved for that. When hibernating it should move everything into **swap** afaik.

---

### Post by fatmano on 2008-02-16
Isnt RAMDISK where it writes the ram for sleep.  I did put it to sleep, not hiberante.

---

