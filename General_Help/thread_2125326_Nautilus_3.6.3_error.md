---
title: "Nautilus 3.6.3 error"
date: 2013-03-13
forum: General Help
---

### Post by soulrain on 2013-03-13
Hi guys. I'm trying to compile nautilus 3.6 in 12.10 with gnome-shell (because I want a different thumbnail border, so the one in gnome 3 ppa doesn't fit for me). After the "make" command I get this "... CC       nautilus-file-operations.lonautilus-file-operations.c:69:23: fatal error: zeitgeist.h: No such file or directory
compilation terminated". The package libzeitgeist-dev is installed, so I don't know what to do. Can anyone help?

---

### Post by pavi_elex on 2013-06-13
Have you solved this problem because I am getting the same error too?

whenever I try to run make I get this error.
I am following these steps to implement up, home & reload button in nautilus.
[http://ubuntuforums.org/showthread.php?t=1904510](http://ubuntuforums.org/showthread.php?t=1904510)

> nautilus-file-operations.c:69:23: fatal error: zeitgeist.h: No such file or directory
compilation terminated.
make[3]: *** [nautilus-file-operations.lo] Error 1
make[3]: Leaving directory `/root/nautilus-mod/nautilus-3.5.90.really.3.4.2/libnautilus-private'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/root/nautilus-mod/nautilus-3.5.90.really.3.4.2/libnautilus-private'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/nautilus-mod/nautilus-3.5.90.really.3.4.2'
make: *** [all] Error 2

---

