---
title: "Compiling GTK+ 2.12.6 (libtool error)"
date: 2008-02-17
forum: General Help
---

### Post by GuDoN on 2008-02-17
Hey,

I need some help trying to compile GTK+ (latest)

I ./configure   - everything goes according to plan.

When I 'make'   (as root as well)  ; I think everything is going well, until about 2 minutes later, lol...


I copied the last bit.
```

mkdir .libs
gcc -g -O2 -Wall -o .libs/autotestfilechooser autotestfilechooser.o  ../gdk-pixbuf/.libs/libgdk_pixbuf-2.0.so -L/usr/local/lib ../gdk/.libs/libgdk-x11-2.0.so ../gtk/.libs/libgtk-x11-2.0.so /home/gudon/gtk+-2.12.6/gdk/.libs/libgdk-x11-2.0.so -lXext /home/gudon/gtk+-2.12.6/gdk-pixbuf/.libs/libgdk_pixbuf-2.0.so /usr/local/lib/libpangocairo-1.0.so /usr/local/lib/libpangoft2-1.0.so /usr/local/lib/libpango-1.0.so /usr/local/lib/libatk-1.0.so /usr/local/lib/libgobject-2.0.so /usr/local/lib/libgmodule-2.0.so -ldl /usr/local/lib/libglib-2.0.so /usr/lib/libcairo.so /usr/local/lib/libfreetype.so -lz -lfontconfig -lpng12 -lXrender -lX11 -lm 
creating autotestfilechooser
/bin/bash ../libtool --mode=link      -o autotestkeywords    
libtool: unrecognized option `-o'
Try `libtool --help' for more information.
make[2]: *** [autotestkeywords] Error 1
make[2]: Leaving directory `/home/gudon/gtk+-2.12.6/tests'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/gudon/gtk+-2.12.6'
make: *** [all] Error 2

```


I've been struggling with this damn gtk since last night, and now this morning too. Atleast I got further than last night, but still not working.

Thanks in advance for help regarding this issue.

Graham.

---

### Post by GuDoN on 2008-02-17
Oh, I am running Ubuntu Gutsy 7.10
:( At this point, I am stuck!

Anyone that can give me a hand? :KS

---

### Post by GuDoN on 2008-02-17
I found out from another forum, from someone else's previous post, that it might be a problem or a bug with libtool itself, when I get home, I will try to compile the latest libtool which can be found at:

[This Link]("http://ftp.gnu.org/gnu/libtool/libtool-1.5.tar.gz")

Will keep you guys posted, in the meantime, if you can give me further advice, it would be appreciated! :)

---

