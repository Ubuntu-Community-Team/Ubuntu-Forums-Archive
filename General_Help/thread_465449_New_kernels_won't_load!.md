---
title: "New kernels won't load!"
date: 2007-06-05
forum: General Help
---

### Post by MindSpore on 2007-06-05
I'm not sure what happened but the *.15 and *.16 kernels won't load.  It starts to load (i get the progress bar) and it just stops a little before halfway and won't go any further.  Now, the *.14 kernel will load up, but when the Desktop comes up the nautilus loading screen stays on the screen for a while, then it goes away but i can't click on anything on the gnome-panel.  Then finally the rest of the icons on the gnome-panel come up everything works fine.

So, can anyone give me any tips on diagnosing this problem?

---

### Post by merlinus on 2007-06-05
Definitely look at /boot/grub/menu.lst  Something probably changed with the kernel upgrades.

It is also possible that grub root was switched.  This happened to me with the upgrade to -16.

-merlin

---

### Post by MindSpore on 2007-06-05
No this was the -15 upgrade (or something i did around that time).  The -16 upgrade did screw up my root entries but i fixed that.

---

### Post by scott_g on 2007-06-05
What if you try booting in recovery mode from the grub menu, and see what entry it stops on?

Just a thought,
Scott

---

