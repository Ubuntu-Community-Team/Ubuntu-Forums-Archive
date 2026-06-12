---
title: "Sypnatic not working"
date: 2007-12-23
forum: General Help
---

### Post by Sohn_of_a_Gunn on 2007-12-23
I just had a power surge in my area and I was installing a package while it happened, now, Sypnatic does not work and pops up this message.

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

I tried the run dpkg command but it said I do not have super user privileges, can someone PLEASE HELP!?

---

### Post by oldos2er on 2007-12-23
sudo dpkg --configure -a

---

### Post by Sohn_of_a_Gunn on 2007-12-23
Doing that but how big should the disk cache be?

---

### Post by oldos2er on 2007-12-24
'Fraid i have no idea. If there's a default choice, I'd take it.

---

