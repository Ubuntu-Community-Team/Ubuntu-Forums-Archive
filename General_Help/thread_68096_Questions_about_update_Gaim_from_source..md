---
title: "Questions about update Gaim from source."
date: 2005-09-22
forum: General Help
---

### Post by ppl on 2005-09-22
Try to make/complie from source, after ./configure I get this information:
"
Gaim will be installed in /usr/local/bin.
Warning: You have an old copy of gaim at /usr/bin/gaim."

Is that mean my old and the new one will be installed in different directory?

Could my old data from gaim like plug-in still  be uesed in new version ? and could updater in Ubuntu will recongnize it so it will not be update again later?

---

### Post by fordfan753 on 2005-09-22
Did you build the gaim already installed from source? If it is a .deb done through dpkg  or synaptic/aptitude/apt-get get uninstall it before you build gaim from source. Also get rid of the gaim-data package if it is installed. If it is a source package you may be able to make uninstall it, but it *should* be safe to install straight over the top of it.

As far as plugins, I use guifications, and every time I compile a new gaim version guifications is picked up fine, but this could be because it is installed in a different directory...

Correct me anyone if I'm wrong, but synaptic/aptitude/apt-get will not recognise source packages as being installed since they only work with .debs, so it is not as easy to update source packages. Still, I always like to compile my gaim. :P

---

