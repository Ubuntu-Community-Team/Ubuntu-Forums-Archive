---
title: "Restoring Ubuntu to Default State"
date: 2007-07-31
forum: General Help
---

### Post by alexv305 on 2007-07-31
Is it possilble to restore the entire OS without losing my files in my home directory? I recently installed some Ubuntu Studio package for the theme and it installed all these other programs I dont use, now i cant get rid of the programs.

Is this possible?

---

### Post by snooptodd on 2007-07-31
1. open synaptic
2. search for the progam you dont want
3. click on green box, select mark for removal
4. goto 2 until all the programs you want removed are marked for removal
5. click apply in toolbar

---

### Post by alexv305 on 2007-07-31
Seriously under sound and video it added like 30 programs and i have to remove them one by one after installing a single app? thats gay lol

---

### Post by aysiu on 2007-07-31
Remove the package and then do ```
sudo apt-get autoremove
``` That should remove its dependencies as well. Sexual orientation has nothing to do with it.

---

