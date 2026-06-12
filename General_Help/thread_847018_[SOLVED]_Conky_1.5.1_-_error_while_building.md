---
title: "[SOLVED] Conky 1.5.1 - error while building"
date: 2008-07-02
forum: General Help
---

### Post by LinuX-M@n1@k on 2008-07-02
I'm building Conky 1.5.1 from source with xmms2 support and I get an error while building it.

First how I configured it:
```
$ ./configure --enable-xmms2 --prefix=/usr
```
Then:
```
$ make
Making all in src
make[1]: Entering directory `/home/boris/conky/conky-1.5.1/src'
...
...
...
mv -f .deps/x11.Tpo .deps/x11.Po
gcc -DHAVE_CONFIG_H -I. -DSYSTEM_CONFIG_FILE=\"/usr/etc/conky/conky.conf\"    -I/usr/include/xmms2         -I/usr/include/freetype2   -I/usr/include/glib-2.0 -I/usr/lib/glib-2.0/include   -Wall -W -MT xmms2.o -MD -MP -MF .deps/xmms2.Tpo -c -o xmms2.o xmms2.c
xmms2.c: In function &#8216;xmms_alloc&#8217;:
xmms2.c:42: error: &#8216;TEXT_BUFFER_SIZE&#8217; undeclared (first use in this function)
xmms2.c:42: error: (Each undeclared identifier is reported only once
xmms2.c:42: error: for each function it appears in.)
xmms2.c: In function &#8216;handle_curent_id&#8217;:
xmms2.c:135: error: &#8216;TEXT_BUFFER_SIZE&#8217; undeclared (first use in this function)
xmms2.c: In function &#8216;handle_playback_state_change&#8217;:
xmms2.c:240: error: &#8216;TEXT_BUFFER_SIZE&#8217; undeclared (first use in this function)
xmms2.c: In function &#8216;handle_playlist_loaded&#8217;:
xmms2.c:257: error: &#8216;TEXT_BUFFER_SIZE&#8217; undeclared (first use in this function)
make[2]: *** [xmms2.o] Error 1
make[2]: Leaving directory `/home/boris/conky/conky-1.5.1/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/boris/conky/conky-1.5.1/src'
make: *** [all-recursive] Error 1
$ 
```
I get the same error while building 1.5.0 (again, with xmms2 support), but I don't get any errors with 1.4.9 ?

What to do?

---

### Post by LinuX-M@n1@k on 2008-07-02
bump

---

### Post by Gunman1982 on 2008-07-02
Seems to be a bug with because of a missing header file, try version 1.5.2_pre01107 as suggested in [http://bugs.gentoo.org/217813]("http://bugs.gentoo.org/217813")

---

### Post by LinuX-M@n1@k on 2008-07-02
> **Gunman1982 said:**
> Seems to be a bug with because of a missing header file, try version 1.5.2_pre01107 as suggested in [http://bugs.gentoo.org/217813]("http://bugs.gentoo.org/217813")

Okay, I'll try, thanks!

---

