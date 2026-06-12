---
title: "Compiz Settimgs on reboot"
date: 2008-06-25
forum: General Help
---

### Post by lanchka on 2008-06-25
If I run the command ```
compiz --replace
``` using Alt+F2, metacity gets replaced by compiz with the settings I have chosen in the Advanced Desktop Effects Settings.Further it respects my present metacity window decoration (Human Squared).
But it seems that metacity starts up on reboot as default since none of these settings are still valid.How do I ensure my changes are permanent?

(PS-Running compiz --replace from a terminal causes my window decoration to change to the default human theme and I don't want that to happen)

Cheers
Thanks in advance!

---

### Post by dexter.deepak on 2008-06-25
go to system->preferences->sessions->startup
add a new startup item named anything you want..with for the command
"compiz --replace"

---

