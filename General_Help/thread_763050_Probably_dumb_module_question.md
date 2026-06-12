---
title: "Probably dumb module question"
date: 2008-04-22
forum: General Help
---

### Post by shingalated on 2008-04-22
What is the difference between modprobe -r and rmmod?  Also how do I list all available (not all loaded) modules?

---

### Post by Tim Sharitt on 2008-04-22
modprobe -r and rmmod both remove modules and as far as I know there's really no difference, although I've been told that it's better to use modprobe -r ( the rmmod man page actually says the same thing). As for listing modules I believe modprobe -l should show all available modules.

---

