---
title: "need help deleting file [Resolved]"
date: 2007-01-07
forum: General Help
---

### Post by cptjaben on 2007-01-07
I followed [this guide]("http://ubuntuforums.org/showthread.php?t=333501") hoping that it would allow me to successfully run compiz. unfortunately, now when i boot up ubuntu it loads in as though it's starting up gnome after the login screen (i have it set to auto-login) except the screen is greyish-black and it loads forever without ever finishing. I need to delete this file :/etc/gdm/gdm.conf-custom however I cannot log on to ubuntu, how can I do this? Thanks.

---

### Post by taurus on 2007-01-07
Can you boot into recovery mode from GRUB menu and delete it from a prompt?

```
rm /etc/gdm/gdm.conf-custom
```

---

### Post by SkyIsFalling on 2007-01-07
Log in at a virtual terminal (press Ctrl-Alt-F1).

---

### Post by cptjaben on 2007-01-07
Thanks much for the help everyone, everything worked out nicely.

---

