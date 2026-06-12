---
title: "grub constantly sets wrong root option"
date: 2008-03-05
forum: General Help
---

### Post by cokehabit on 2008-03-05
debconf (or whatever) sets the wrong boot= option after every kernel upgrade.

Although i am well used to writing my own grub.conf files i find it a nuisance to have to keep changing hd0,0 to hd0,3 after an upgrade. 

Is there a way to tell the automagical configurer to stop being so damn stupid and use hd0,3 ?

---

### Post by louieb on 2008-03-05
Look in the automagic section for **groot=  **
It not stupid. Its ignorant  and just doing what it was told to do. :)

---

