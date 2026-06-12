---
title: "Help Please!!"
date: 2007-10-26
forum: General Help
---

### Post by koolbob1872 on 2007-10-26
I need lots of help. I cant seem to get ANYTHING right in this. Every time I try to install any applications, a window pops up and says " E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. E: _cache->open() failed, please report." I also am trying to run a game called "Baldurs Gate 2: Shadows of Amn", and I don't know how to get that working either, so if some one could help me I would REALLY appreciate it. Beggars cant be choosers but if you would please explain in simple terms, I'm new at this.

---

### Post by taurus on 2007-10-26
Open a terminal and run

Applications -> Accessories -> Terminal
```
sudo dpkg --configure -a
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by koolbob1872 on 2007-10-26
Thanks but what exactly did that do?

---

