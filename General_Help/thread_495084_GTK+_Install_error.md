---
title: "GTK+ Install error"
date: 2007-07-07
forum: General Help
---

### Post by iSecks on 2007-07-07
So this morning, I started to install GTK+, i got all the packages ready, went back and forth installing whatever i was missing, and i finally get everything ready to go, but when i make it, i get
```
make[3]: *** [gdkdrawable-x11.lo] Error 1
make[3]: Leaving directory `/home/andres/Desktop/gtk+-2.10.13/gdk/x11'
make[2]: *** [install-recursive] Error 1
make[2]: Leaving directory `/home/andres/Desktop/gtk+-2.10.13/gdk'
make[1]: *** [install] Error 2
make[1]: Leaving directory `/home/andres/Desktop/gtk+-2.10.13/gdk'
make: *** [install-recursive] Error 1
```

any help would be appreciated.

---

### Post by deepclutch on 2007-07-08
sorry,but why do u want to install from source,although gtk+ 2.0 is available in ubuntu repositories and Gnome :?

---

### Post by geraldm on 2007-07-08
Post enough lines to see the exact error.  Those lines come after the 
error was detected.

In a bash shell, redirect stdout and stderr to the same file.  Then 
the lines needed would come just before the lines you posted.  

make &> mk.log

Gerald

---

