---
title: "Login problem"
date: 2004-12-06
forum: General Help
---

### Post by Artiom on 2004-12-06
after installing k3b, I'm having login problems, this error from .xsession-errors :
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "artiom"
/etc/gdm/Xsession: Beginning session setup...

** (gnome-session:4772): WARNING **: Unable to read ICE authority file: /home/artiom/.ICEauthority
``` 

any ideas?

---

### Post by Artiom on 2004-12-06
I think, I fixed it by myself.

I just changed the permisions on the .ICE**** file. (they were set to root user),
and it worked. =D> (<-- suppose to be applause ?!?)

---

