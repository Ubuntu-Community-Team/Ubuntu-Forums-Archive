---
title: "ubuntu doesn't display the shutdown or restart, i installed kubuntu"
date: 2007-07-25
forum: General Help
---

### Post by sarahsilverman on 2007-07-25
i installed kubuntu, didn't like it so i changed the session back to gnome. but now there isn't any restart or shutdown buttons showing when i click on quit. how can i fix this?

also, my power management settings don't work. like suspend when i close the laptop lid or ask me what to do when i press the power button. any way to fix this also?

thanks any help is greatly appreciated :popcorn:

---

### Post by strabes on 2007-07-26
I hope you used aptitude to install the kubuntu-desktop package. Anyway, run ```
sudo aptitude remove kubuntu-desktop
``` Then restart your X server.

---

