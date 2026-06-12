---
title: "LIRC: error while loading shared libraries"
date: 2007-05-12
forum: General Help
---

### Post by rbm0307 on 2007-05-12
Hi,

I need some general Linux help related to shared libraries.

On my MythTV frontend, I was working on getting LIRC to function properly. The first thing I tried was apt-get install lirc and it loaded 0.8.1 as expected but I had configuration problems (my lack of knowledge).  Anyway, I removed LIRC 0.8.1 and installed LIRC 0.8.2pre2 from source. Most everything functioned properly except irrecord.  To correct the problem, I performed a "make uninstall" from the 0.8.2pre2 source tree and returned to 0.8.1 again.  I managed in the end to get everything functioning properly with this version of LIRC.

However, when I fired up mythtv, I got the following error in .xsession-errors:
```
/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp
/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/:0.Xservers" -h "" -l ":0" "mythtv"
/etc/gdm/Xsession: Beginning session setup...
I/O warning : failed to load external entity "/home/mythtv/.config/openbox/rc.xml"
I/O warning : failed to load external entity "/var/lib/openbox/debian-menu.xml"

(openbox:10211): ObParser-WARNING **: unable to find a valid menu file '/var/lib/openbox/debian-menu.xml'
I/O warning : failed to load external entity "/home/mythtv/.config/openbox/debian-menu.xml"
I/O warning : failed to load external entity "/etc/xdg/openbox/debian-menu.xml"

(openbox:10211): ObParser-WARNING **: unable to find a valid menu file 'debian-menu.xml'
/usr/bin/mythfrontend.real: error while loading shared libraries: liblirc_client.so.0: cannot open shared object file: No such file or directory
```  Result is I can't login and therefore use my MythTV frontend as it is rendered useless.

Last line in the error log says mythfrontend is looking for a 0.8.2pre2 shared library which is no longer there.  How do I de-register this file so mythfrontend won't search for it?

Thanks.

Robert.

---

