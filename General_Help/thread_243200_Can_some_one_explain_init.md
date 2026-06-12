---
title: "Can some one explain init?"
date: 2006-08-24
forum: General Help
---

### Post by Clunsford on 2006-08-24
can some one explain to me what and how init works?

and could some one explain to me the different init options? like i understand there is init, init.d, initng and like other stuff (or am i lost in the dark?)

i would appreciate help on this, thanks.

---

### Post by sisooktom on 2006-08-24
What exactly do you need help with?  init is the first process that spawns when the system boots.  It is the ancestor of all other processes and also controls system runlevels.  init.d is the directory that holds the scripts that are run for each service in each of those runlevels.  initng IIRC is a new init system that would basically replace the init.d script system.

---

### Post by kpkeerthi on 2006-08-24
(deleted by the poster)

---

