---
title: "Wine appearing in menu after installation"
date: 2013-01-21
forum: General Help
---

### Post by aykoola on 2013-01-21
Hi!

So as i stated, the problem is that an option for wine was automatically added to my menu after installation. I tried removing it, but it can not be done via the GUI that's available. And the big problem is that even after uninstalling everything that has anything to do with wine, it's still there, only without logo and options inside it. How can i fix this?

Thank you!

Running Xubuntu 12.04 on a 64bit machine!


Edit: SOLVED! Anyone having the same issues, do the following: Find a hidden folder in your home directory. It's located here: ~/.local/share/applications  - And just delete anything that has to do anything with wine. That way, you'll remove wine from the menu!!!!

---

