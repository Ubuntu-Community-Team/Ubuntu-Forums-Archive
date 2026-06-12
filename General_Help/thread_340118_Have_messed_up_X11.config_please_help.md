---
title: "Have messed up X11.config please help"
date: 2007-01-16
forum: General Help
---

### Post by mrwooster on 2007-01-16
Hi,

Have just installed Ubuntu, used apt-get upgrade and then attempted to install beryl but have seemed to have screwed it up and now when I boot I get an error and the X11.config file is messed up, so the desktop wont load. Tried to use the original X11.config file but get the same problem.

What can I do, do I need to re-install X11 or is there another way around it?

Thanks

Guy

---

### Post by taurus on 2007-01-16
Boot into recovery mode from GRUB menu and at the prompt, type

```
dpkg-reconfigure -phigh xserver-xorg
startx
```

---

