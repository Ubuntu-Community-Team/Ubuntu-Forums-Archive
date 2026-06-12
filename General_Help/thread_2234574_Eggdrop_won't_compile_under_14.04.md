---
title: "Eggdrop won't compile under 14.04"
date: 2014-07-15
forum: General Help
---

### Post by Mike_Sheridan on 2014-07-15
I have tried everything, and I have done this on previous versions of ubuntu no problems. I installed tcl and tcl-dev, and I still get the error 

```
checking for Tcl library... not foundchecking for Tcl header... found /usr/include/tcl8.5/tcl.h
checking whether the Tcl system has changed... yes
configure: error:


  Tcl cannot be found on this system.


  Eggdrop requires Tcl and the Tcl development files to compile.
  If you already have Tcl installed on this system, make sure you
  also have the development files (common package names include
  'tcl-dev' and 'tcl-devel'). If I just wasn't looking
  in the right place for it, re-run ./configure using the
  --with-tcllib='/path/to/libtcl.so' and
  --with-tclinc='/path/to/tcl.h' options.


  See doc/COMPILE-GUIDE's 'Tcl Detection and Installation' section for more
  information.



```

Now I know it's missing files, I'm just not sure what to do here. Any and all help would be appreciated.

whereis tcl returns
```
tcl: /usr/lib/tcl8.4 /usr/lib/tcl8.5 /usr/lib/tcl8.6 /usr/include/tcl8.4 /usr/include/tcl8.5 /usr/include/tcl /usr/include/tcl8.6
```

but nothing is actually working.

---

### Post by Mike_Sheridan on 2014-07-15
FIGURED IT OUT! I found this on another site, but for the sake of this thread, the command in 14.04 is

```
./configure --with-tclinc=/usr/include/tcl8.6/tcl.h --with-tcllib=/usr/lib/x86_64-linux-gnu/libtcl8.6.so
```

---

### Post by topolab on 2014-11-15
last command fix my issue in lubuntu, too!!

---

