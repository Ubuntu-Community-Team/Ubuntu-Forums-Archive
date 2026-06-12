---
title: "[SOLVED] Installing PCman &amp;quot;Fatal Error: no fam or gamin detected&amp;quot;"
date: 2008-05-19
forum: General Help
---

### Post by OdSquad64 on 2008-05-19
I'm currently running PCman 0.3.2.2 as my default file manager and I'm trying to install PCman 0.4.4.0. After I run ./configure it goes through its whole thing and gives me 

configure: error: Fatal Error: no fam or gamin detected.

I already have gamin and reinstalling it didn't help anything. I get the same error trying to install PCman 0.4.1.1.  Is there something I can do to fix this error?

---

### Post by y-lee on 2008-05-19
Have you installed the header files for those applications? They usually end in -dev look for them in synaptic.

---

### Post by OdSquad64 on 2008-05-19
thanks a bunch, installing libgamin-dev did the trick

---

### Post by y-lee on 2008-05-19
Glad I could help! Go ahead and mark this as solved it makes the forums easier to use (click on thread tools above) :)

---

