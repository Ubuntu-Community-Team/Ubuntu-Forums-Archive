---
title: "apt-get needs a cd??"
date: 2005-07-12
forum: General Help
---

### Post by pacz on 2005-07-12
apt-get tells me it needs the install cd, which isn't a problem.  the problem is that it never recognizes the cd once i put it in.

I've tried apt-setup and editing /etc/apt/sources.list but it keeps asking me to put in the cd and it's very sucky.

any suggestions? thank you

---

### Post by az on 2005-07-12
In synaptic, remove the cd repository entry and add another cd repository entry.

Synaptic - Edit - Add CdRom.

The installer caches packages ont your harddrive, but if you clear your cache, you keep getting asked for the cd.

You can just delete the cd repository and use the online ones for everything, though.

---

