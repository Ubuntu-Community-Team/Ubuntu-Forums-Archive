---
title: "wine app still exists in gnome menu, after complete removal of wine"
date: 2008-02-04
forum: General Help
---

### Post by seregaShishkilov on 2008-02-04
I wanted a clean slate of wine on my computer so I deleted the hidden directory, uninstalled the source and removed wine from synaptic, yet there is still a wine when I click the "applications" button on the gnome panel, saying that there is still a game which I installed using wine. I have checked numerous times, both in root and my directories that there is no more .wine/ directory.

Also when I right click on a file and choose "open with other application" wine is still in the list of the applications available.

I have found a thread saying to simply use "sudo alacarte" but the wine menu did not appear in the list...

Any Idea on how to remove this? it really annoys me.

---

### Post by luisromangz on 2008-02-04
That you remove .wine doesn't mean that the menu icons dissapear, as they are not stored there.

Try using alacarte, but without sudo, as wine apps aren't installed as root.

---

### Post by seregaShishkilov on 2008-02-04
Thank you very much, using alacarte without sudo solved it.

---

