---
title: "Can not log in"
date: 2007-08-09
forum: General Help
---

### Post by df9517 on 2007-08-09
Hi,

I am now logged in as root.

The other day I was trying to share my home directory using samba. But it never worked perfectly so I gave up. But after starting Linux again I got a message that my home directory should have at least 644 and not write access for others. I got this message everytime I logged in.

Then I changed my home directory to 644. Now I can not log in at all and .xsessionsfault give following fault code:


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "daniel"
/etc/gdm/Xsession: Beginning session setup...
SESSION_MANAGER=local/Ubuntu:/tmp/.ICE-unix/6115


What to do?

---

### Post by Super TWiT on 2007-08-09
I guess you could make sure that Samba isn't sharing it at all.  That's the only thing I can think of.

---

