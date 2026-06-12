---
title: "10 second sessions?"
date: 2007-06-08
forum: General Help
---

### Post by dk1 on 2007-06-08
Hi there, I seem to have somehow botched up my install.  After running fsck to repair my filesystem, I thought all was well.  Then I tried to log in.

It flashed the wallpaper for a second and then I got a box, telling me that the current session lasted less than 10 seconds.  Here's the rest of the info that it gave me.

```


/etc/gdm/PreSession/Default: Registering your session with wtmp and utmp

/etc/gdm/PreSession/Default: running: /usr/X11R6/bin/sessreg -a -w /var/log/wtmp -u /var/run/utmp -x "/var/lib/gdm/: 0.Xservers" -h "" -1 ":0" "USER"

/etc/gdm/Xsession: Beginning session setup...

/usr/bin/gnome -session: error while loading shared libraries: libgnutls.so.13: cannot open shared object file: No such file or directory


```

Any ideas?  I've never seen this one before.  Should I just try to reinstall Gnome?

---

### Post by dk1 on 2007-06-09
I tried doing an
```


sudo apt-get install libgnutls.co.13


```

To see if I could just reinstall the missing library, but no luck.

---

### Post by vanadium on 2007-06-09
Can you boot with a previous kernel? When your computer starts up, go into the GRUB menu (with dual boot systems, the grub menu is displayed, with single boot systems, you have to go into it pressing Esc at the right time during booting) and select a previous kernel.

---

### Post by dk1 on 2007-06-09
I tried it, but no luck.  It's still logging me right back out as soon as I log in and still showing the same error that I posted above.

---

