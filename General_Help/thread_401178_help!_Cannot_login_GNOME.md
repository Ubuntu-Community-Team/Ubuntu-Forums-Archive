---
title: "help! Cannot login GNOME"
date: 2007-04-04
forum: General Help
---

### Post by kenyi25 on 2007-04-04
An alert box came out containing the message below, just after i typed my password.
I was asked to login into failsafe session to fix the installation problem.

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "kenyi"
/etc/gdm/Xsession: Beginning session setup...
/usr/bin/ssh-agent: error while loading shared libraries: libkrb5.so.3: cannot open shared object file: No such file or directory

---

### Post by phidia on 2007-04-04
Did this happen after an upgrade? Just asking because someone else here has had a login problem after upgrading.
You might try system rescue from the livecd.

---

