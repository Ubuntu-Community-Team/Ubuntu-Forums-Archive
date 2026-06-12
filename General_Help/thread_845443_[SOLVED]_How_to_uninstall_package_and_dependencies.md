---
title: "[SOLVED] How to uninstall package and dependencies"
date: 2008-06-30
forum: General Help
---

### Post by Harry Muscle on 2008-06-30
How can I uninstall a package and any dependencies that it installed (that are obviously not needed by any other package that's installed)?

I noticed that in the Synaptics Package Manager there's an option to Mark for Complete Removal ... does that do what I'm looking for?  What about the apt-get purge option?

Thanks,
Harry

---

### Post by russlar on 2008-06-30
sudo apt-get autoremove *package*

removes the package, and all it's dependencies.

---

