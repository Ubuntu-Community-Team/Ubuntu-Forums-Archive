---
title: "GDM low down in run level list?"
date: 2005-10-31
forum: General Help
---

### Post by Randy Sparks on 2005-10-31
Just a quick non-essential query about how Ubuntu works...

I want to make run level 3 into a non-GUI run level so I can boot straight into the command prompt (and start the GUI later with startx if need be).

So I looked in /etc/rc3.d/ with the intention of finding and eliminating the shortcut to GDM, which I believe is what kicks off X. Sure enough, I found it, but it was 

S13GDM

Bearing in mind that it's the last thing that appears, why is it so low-down in the run level list? Shouldn't it be S99GDM?

---

### Post by az on 2005-10-31
It starts earlier so that the whole boot process can multi-task and be more efficient.

---

