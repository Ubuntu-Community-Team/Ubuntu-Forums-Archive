---
title: "borked my video driver settings, what do i edit to specify what driver to use?"
date: 2015-01-22
forum: General Help
---

### Post by dantose on 2015-01-22
After messing around with different video cards, i ended up screwing up the drivers. I also managed to break something with the usual roll back via safe graphical mode. I remember years ago you could muck around with xorg.conf directly, but now that's all changed. What do I muck around with now to specify a driver to use? Editing from a live CD right now.

---

### Post by ajgreeny on 2015-01-22
We need much more information to know what to tell you to try.

Which video cards; which drivers etc etc have you tried to get working and what do you now have?

You may simply be able to remove any proprietary drivers you have installed, rename the /etc/X11/xorg.conf, if there is one, so that the system does not use it, and then reboot, but depending on the hardware you may need some boot options in order to get to a GUI.

---

