---
title: "/usr/bin/ld: cannot find -lsynaptics when compiling TouchFreeze"
date: 2008-04-22
forum: General Help
---

### Post by Zorael on 2008-04-22
I'm trying to compile TouchFreeze ([http://qsynaptics.sourceforge.net/index.html](http://qsynaptics.sourceforge.net/index.html)), and everything goes well up to the point where it complains about this and stops.
```
g++ -Wl,--no-undefined -o TouchFreeze main.o TouchFreezeApp.o TouchFreezeUI.o SynDaemon.o moc_TouchFreezeApp.o moc_TouchFreezeUI.o moc_SynDaemon.o qrc_stuff.o    -L/usr/lib -lsynaptics -lQtGui -lQtCore -lpthread
/usr/bin/ld: cannot find -lsynaptics
collect2: ld returned 1 exit status
make: *** [TouchFreeze] Error 1
```

What am I missing?

---

### Post by mc4man on 2008-04-22
search for libsynaptics0 in synaptic, try installing it and the -dev (if not installed)

---

