---
title: "GDE error"
date: 2007-04-27
forum: General Help
---

### Post by Vashypooh on 2007-04-27
I installed imwheel and found it was not nessecary to get my mouse work and removed it, and it left this error in its wake.


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "vash"
/etc/gdm/Xsession: Beginning session setup...
.: 2: Can't open /etc/X11/imwheel/startup.conf

how do i remove this reference?

---

### Post by Vashypooh on 2007-04-27
all that time to figure out if i use --purge on removeing, it smuch better

---

