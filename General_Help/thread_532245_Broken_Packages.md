---
title: "Broken Packages"
date: 2007-08-22
forum: General Help
---

### Post by hraposo on 2007-08-22
I've a big problem.
I've 4 broken packages: libc6-dev, libgcc1, libstdc++6 and locales.

When I trie unistall it the system unistall a lot of packages fundamental for system...
How can I remove this broken packages?

---

### Post by ajgreeny on 2007-08-22
Try fixing the broken packages first with synaptic or apt-get.  In synaptic it's Edit> Fix Broken Packages, in apt-get I think it's **sudo apt-get install -f package_name1 package_name2** etc. etc. but I am not totally certain of the command for this method and **man apt-get** is not a great deal of help to me at least, on this detail.

---

