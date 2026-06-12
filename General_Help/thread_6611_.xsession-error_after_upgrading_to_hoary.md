---
title: ".xsession-error after upgrading to hoary"
date: 2004-11-29
forum: General Help
---

### Post by macewan on 2004-11-29
ran dpkg-reconfigure xserver-xorg

getting this error 

/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/X11/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x “/var/lib/gdm/:0.Xservers” -h “” -l “:0&#8243; “macewan”
/etc/gdm/Xsession: Beginning session setup…
Failed to start message bus: Attribute “if_selinux_enabled” is invalid on element in this context
EOF in dbus-launch reading address from bus daemon

---

### Post by daniels on 2004-11-30
Whoops, will look into it.  Thanks a lot.  Which version of D-BUS are you running?  You can find this out with dpkg -l dbus-1.

---

### Post by macewan on 2004-11-30
[QUOTE=daniels]Whoops, will look into it.  Thanks a lot.  Which version of D-BUS are you running?  You can find this out with dpkg -l dbus-1.[/QUOTE]

Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-files/Unpacked/Failed-config/Half-installed
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  dbus-1         0.22-3ubuntu1  simple interprocess messaging system

---

### Post by macewan on 2004-11-30
Please disregard this post as it does not apply to Xorg or dbus from Hoary install.

Turns out the problem was a previously installed cvs version of dbus. Once I uninstalled that version everything worked fine.

---

