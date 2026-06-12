---
title: "Can't log into gnome session anymore"
date: 2007-02-04
forum: General Help
---

### Post by marcus174 on 2007-02-04
Hi, 

I've been trying to get the ati drivers working on which ill open another thread about that later, currently now i cannot log into a gnome session anymore (failsafe works). According to the xsession-errors file. The problem is

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mroy"
/etc/gdm/Xsession: Beginning session setup...
.: 106: Can't open /etc/profile

Anyone now how to fix it?

Cheers.

---

### Post by gradedcheese on 2007-02-04
/etc/profile is a settings file and init script for your shell.  From a text shell, check if the file exists and what its permissions are:

ls -l /etc/profile

---

### Post by marcus174 on 2007-02-04
mroy@mroy-desktop:/etc$ ls -la /etc/profile
-rw------- 1 root root 369 2007-02-04 04:01 /etc/profile

So it's there, permissions are set wrong?

---

### Post by gradedcheese on 2007-02-04
yep!  try:

sudo chmod a+r /etc/profile

(ie: everyone can read /etc/profile)

---

### Post by marcus174 on 2007-02-04
Thanks this has fix it.

Cheers.

---

### Post by nexnz on 2007-02-15
Hello...

Hate to jump on someone else's thread, however I have the exact same issue but recovery mode does not work.... 

drops me into maintenance mode

Anyone know how I can revive it from here, or is it reinstall time?

Thanks in advance

---

### Post by nexnz on 2007-02-16
lol nevermind....

Typing the above fix in maintenance mode... fixed it

regards,

---

