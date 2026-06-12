---
title: "snap window"
date: 2015-03-17
forum: General Help
---

### Post by joriadams65 on 2015-03-17
I am trying to disable the snap window in 14.04 but have no idea how to do this. i have looked into system settings and thought sticky window might help but that did not turn off the snap. I have also searched some threads here for ideas but nothing that i found pertains to 14.04 or worked for me. I am also not very technically savvy so will need to be walked through it step by step.

---

### Post by CantankRus on 2015-03-18
If you mean the resizing and positioning of windows when dragged to screen edges
you can use compizconfig-settings-manager (ccsm) to disable screen edges or the grid plugin entirely.
```
sudo apt-get install compizconfig-settings-manager
```
Search in dash ccsm to run.

---

### Post by joriadams65 on 2015-03-18
thank you, that worked. I was trying to start compiz in terminal with compiz (which gave errors) not ccsm.

---

