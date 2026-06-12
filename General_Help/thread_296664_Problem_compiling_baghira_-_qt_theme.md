---
title: "Problem compiling baghira - qt theme"
date: 2006-11-09
forum: General Help
---

### Post by Rahu on 2006-11-09
I'm having trouble installing the baghira theme for kde. I looked through some threads, and got(i think) all the necessary dependencies. I really have no idea what to do to solve this. Here's the last few lines from the compile log.

```
        then mv -f ".deps/starter.moc.Tpo" ".deps/starter.moc.Plo"; else rm -f "
.deps/starter.moc.Tpo"; exit 1; fi
/bin/bash ../libtool --silent --mode=link --tag=CXX g++-3.4  -Wno-long-long -Wun
def -ansi -D_XOPEN_SOURCE=500 -D_BSD_SOURCE -Wcast-align -Wconversion -Wchar-sub
scripts -Wall -W -Wpointer-arith -O2 -Wformat-security -Wmissing-format-attribut
e -Wno-non-virtual-dtor -fno-exceptions -fno-check-new -fno-common    -o libbagh
irastarter.la -rpath /usr/lib -module -avoid-version -L/usr/share/qt3/lib -L/usr
/lib    baghiralinkdrag.lo menu.lo starter.lo starteriface_skel.lo starterconfig
.lo starterhelp.lo config.lo help.lo linkconfig.lo baghiralinkdrag.moc.lo menu.m
oc.lo starter.moc.lo  -lXtst -lkdeui
/usr/bin/ld: cannot find -lXtst
collect2: ld returned 1 exit status
make[2]: *** [libbaghirastarter.la] Error 1
make[2]: Leaving directory `/home/jeff/baghira-0.8/starter'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jeff/baghira-0.8'
make: *** [all] Error 2

```

---

### Post by smdeep on 2006-11-23
Bump!

I just got the very same error. Could someone help?

---

### Post by neorush on 2006-11-30
sudo apt-get install xlibs-dev
./configure --prefix=`kde-config --prefix` --disable-debug
make clean
make

---

### Post by smdeep on 2006-12-28
> **neorush said:**
> sudo apt-get install xlibs-dev
./configure --prefix=`kde-config --prefix` --disable-debug
make clean
make

Hi

thanks a million. This worked like a charm.

:)

---

