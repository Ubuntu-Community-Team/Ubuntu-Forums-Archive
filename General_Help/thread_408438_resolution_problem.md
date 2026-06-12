---
title: "resolution problem"
date: 2007-04-13
forum: General Help
---

### Post by itstito on 2007-04-13
hey all.
during the ubuntu 6.1 live cd installation, i'm faced with a weird problem. during the installation process, the resolution is 640x480...i tried changing it in the live cd mode, but theres no other option other than 640x480! so that makes the windows in the installation procedure suddenly huge, and i can't access the 'next' buttons and therefore, can't install!


HELP!

---

### Post by m.musashi on 2007-04-13
You should be able to use alt+left click to move a window around. That might help you "see" the next buttons and such but fixing the resolution would be better. However, it might not be a lot of fun. Resolution problems can be a hassle.

Normally, you would edit the /etc/X11/xorg.conf file to add the resolutions your monitor supports but I don't know if you can do that with a live CD. Even if you can, I think you would have to restart X for the change to take effect and running live that might cause you to lose the changes. There is a way to run with a live CD and have changes saved to a flash drive but I've never tried that.

What graphics hardware / monitor do you have. It's possible it's not well supported.

---

### Post by zvacet on 2007-04-13
[https://help.ubuntu.com/community/FixVideoResolutionHowto]("https://help.ubuntu.com/community/FixVideoResolutionHowto")

---

