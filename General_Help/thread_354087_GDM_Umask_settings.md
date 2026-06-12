---
title: "GDM Umask settings"
date: 2007-02-05
forum: General Help
---

### Post by compmodder26 on 2007-02-05
Can somebody tell me how to set the default file permissions for a gnome session?  I've changed the umask in every file I know of (/etc/login.defs, /etc/profile/, /etc/bash.bashrc, ~/.bash_profile, ~/.bashrc, ~/.gnomerc).  None of them seem to work.  Is there something I'm missing?

I'm running edgy

---

### Post by compmodder26 on 2007-02-05
Nevermind, it appears it's a bug with nautilus.  The devs apparently hard-coded the default permissions instead of drawing them from the user's settings.  I guess I'll just wait until the patch reaches the masses.

[http://bugzilla.gnome.org/show_bug.cgi?id=327249]("http://bugzilla.gnome.org/show_bug.cgi?id=327249")

---

