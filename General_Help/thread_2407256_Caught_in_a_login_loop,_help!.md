---
title: "Caught in a login loop, help!"
date: 2018-12-01
forum: General Help
---

### Post by laserburn2 on 2018-12-01
Out of the blue and with no warning, I can no longer login to my Ubuntu 18.04 desktop. No changes made on the machine the previous day, only Unite Grome extension updated, I removed it from tty3, but no change. Checked the /var/log/Xorg.0.log, nothing much, the only error I saw there is ```
Failed to open DRM device for (null): -2
```

Tried deleting .Xauthority, it's not even created on the next attempt to login to Gnome. Doesn't make a change if I make it manually. File ~/.xsession-errors doesn't exist. I updated Nvidia drivers from 396 to 415, no change. Thinking it might be something with Gnome, I ran dconf reset -f /org/gnome to reset it, again nothing.

I'm completely out of ideas and just reinstalling the damn thing would take less time. First time in 10 years that Ubuntu fails like this on me.

---

### Post by laserburn2 on 2018-12-01
Never mind, I managed to mess things up completely, I'll need to reinstall.

---

