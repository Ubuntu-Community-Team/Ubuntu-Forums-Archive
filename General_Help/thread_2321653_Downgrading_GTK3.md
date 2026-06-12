---
title: "Downgrading GTK3"
date: 2016-04-23
forum: General Help
---

### Post by MarkBauer on 2016-04-23
After installing GTK3.20, my Ubuntu 16.04 installation is now completely unusable.
The ambiance theme is broken, the password field in lightdm has the wrong coloring and the session switcher completely malfunctions (it crashes before showing even one entry). Furthermore, the option wheel in the upper right corner of lightdm is completely gone.

Is there any way I can downgrade back to GTK3.18? Purging libgtk-3-0 didn't help, as it installed libgtk3.20 again, once I tried re-adding ubuntu-desktop.

---

### Post by vasa1 on 2016-04-23
If you had read around a bit, you'd have found that gtk 3.20 causes a lot of breakage. Even the Arch guys are complaining.

I've seen a couple of *how to move to gtk 3.20 in 16.04* blogs but unless one is doing so on a non-production machine, I wouldn't recommend doing so.

---

