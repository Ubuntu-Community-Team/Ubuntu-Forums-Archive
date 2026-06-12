---
title: "Disable Commands"
date: 2008-06-29
forum: General Help
---

### Post by Vince4Amy on 2008-06-29
Is it possible to disable certain commands from being run for example the one in my signature?

---

### Post by p_quarles on 2008-06-29
Well, you could always make the "rm" command non-executable, but I imagine that this would have a disastrous impact on a number of system housekeeping scripts.

More reasonable would be removing the ability of your user to run "rm" with sudo. I believe that can be done (by adding "!/bin/rm" to the sudoers file), but it's not something I've tested.

As with most things in this category, it is better to give users limited permissions rather than disable essential system functionality.

---

