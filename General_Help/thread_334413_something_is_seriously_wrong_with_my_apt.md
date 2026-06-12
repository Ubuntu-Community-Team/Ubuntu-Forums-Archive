---
title: "something is seriously wrong with my apt"
date: 2007-01-08
forum: General Help
---

### Post by band-aid on 2007-01-08
Ok I am reinstalling software after a reformat but almost half the things I try to get fail because something on sourceforge keeps timing out. I can see in the terminal that it is trying a url like

something.sourceforge.net/corefonts/andale32.exe 
connection timed out

Apparently I am missing some rather important fonts and it is preventing a TON of stuff from installing on apt-get or synaptic. What can I do to fix this.

---

### Post by taurus on 2007-01-08
How did you install the corefonts?  And what does your /etc/apt/sources.list look like?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```

---

### Post by band-aid on 2007-01-08
I didn't install the corefonts. Most of the time I end up getting them as a dependency through synaptic whenever I install the first program after a reinstall of ubuntu. My sources list has not been touched other than adding a automatix repo.

Me thinks the servers that host  the  fonts are down...

---

