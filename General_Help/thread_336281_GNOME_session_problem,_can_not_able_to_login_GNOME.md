---
title: "GNOME session problem, can not able to login GNOME"
date: 2007-01-11
forum: General Help
---

### Post by moonhk on 2007-01-11
When I turned off computer without shutdown the Ubuntu. Then below error shown can not able to login GNOME. How to fix ?


Your Session only lasted less than 10 seconds. If you have not logged out yourself. This could mean that there is some installation Problem... Try logging in with one of the failsafe sessions to see if you can fix this problem.

with following error.

moonhk@hex:~$ cat .xsession-errors
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x
"/var/lib/gdm/:0.Xservers" -h "" -l ":0" "moonhk"
/etc/gdm/Xsession: Beginning session setup...
mkdtemp: private socket dir: Permission denied
moonhk@hex:~$ directory containing default files

moonhk@hex:~$ uname -a
Linux hex 2.6.15-27-server #1 SMP Fri Dec 8 18:43:54 UTC 2006 i686 GNU/Linux
moonhk@hex:~$ shadow password suite configuration

---

