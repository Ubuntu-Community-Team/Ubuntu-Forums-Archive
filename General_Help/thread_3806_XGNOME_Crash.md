---
title: "X/GNOME Crash"
date: 2004-11-09
forum: General Help
---

### Post by beeldings on 2004-11-09
I know I did something to cause this to occur, but I do not remember what I did. It appears that now when I try to log on to my system as the non-root account (spikentm), I receive a prompt stating that my session lasted less than 10 seconds and it outputs the error message to the .xsession-errors file. This occurs when I try to use GNOME as spikentm, however I can log in as root and use GNOME without any problems.

Here is the output from the .xsession-errors file:

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "spikentm"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied

---

### Post by beeldings on 2004-11-09
I fixed it, I fixed it!

It turns out that I deleted /tmp as root, and when the directory was created, the user account did not have permission to write to that directory. So, I just changed the permissions for spikentm to read and write to /tmp, and now everything is up and running.

---

