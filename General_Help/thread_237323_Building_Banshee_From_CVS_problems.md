---
title: "Building Banshee From CVS problems"
date: 2006-08-16
forum: General Help
---

### Post by rekahsoft on 2006-08-16
I have built banshee from CVS all the time but just today i ran into a problem i can't figure out...i have all the dependancies installed but for some reason this checkout of the 0.11.x-cvs version won't work...(Note i already have Banshee 0.11.x-cvs installed but i was just upgrading to the cutting edge). When i do this:```
./autogen.sh --prefix=/usr
``` i get this:```
checking for AVAHISHARP... configure: error: Package requirements (avahi-sharp) were not met:

No package 'avahi-sharp' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables AVAHISHARP_CFLAGS
and AVAHISHARP_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

``` I Checked around and have found that i have libavahi installed but that there is not sharp one...where do i get it or what am i doing wrong? Thanks

---

### Post by AngryMallard on 2007-12-19
```
sudo apt-get install libavahi1.0-cil
```

Fixed it for me.

---

