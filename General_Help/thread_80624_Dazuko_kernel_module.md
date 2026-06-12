---
title: "Dazuko kernel module"
date: 2005-10-22
forum: General Help
---

### Post by abandoned_hussam on 2005-10-22
I installed dazuko kernel module in breezy. but it won't load because of a kernel module called "capability" 
I looked for capability in /etc/modules but its not there. 
I found on google that I have to load dazuko before capability. 
How would I do that? I would appreciate help on this one.

---

### Post by fannymites on 2005-10-24
I worked out a way to do it.  It's probably not the best way but it does work.  See the last post in this thread - [http://www.ubuntuforums.org/showthread.php?t=78794&page=2&highlight=dazuko](http://www.ubuntuforums.org/showthread.php?t=78794&page=2&highlight=dazuko)

---

### Post by nixclusive on 2006-02-26
You'll have to recompile the kernel from source with "Linux Capabilities" as an external module.

---

