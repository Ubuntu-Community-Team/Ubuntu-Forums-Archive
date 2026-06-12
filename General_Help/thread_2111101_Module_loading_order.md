---
title: "Module loading order"
date: 2013-02-01
forum: General Help
---

### Post by thesoothsayer on 2013-02-01
Is there any documentation on the order that modules are loaded during startup and how I can select which particular module to load?

For example, I have a directory /lib/modules/`uname -r`. There are 2 directories called kernel and updates in it. kernel contains the original modules and updates contains modules from a backport-cw package.

How can I choose which modules from a particular directory to load at startup? depmod automatically points to the newer updates directory, but I need to load some of the modules from the original kernel directory.

---

