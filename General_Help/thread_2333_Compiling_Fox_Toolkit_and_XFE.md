---
title: "Compiling Fox Toolkit and XFE"
date: 2004-10-27
forum: General Help
---

### Post by scias on 2004-10-27
Hi all,

i tried to compile and install Fox Toolkit, following instructions from their install.txt,  because it is needed to compile XFE [http://roland65.free.fr/xfe/](http://roland65.free.fr/xfe/) but it ended with errors (some missing files named somthing like X11)

i got gcc and the build-essential pacakages. is there something i missed (or messed) ?

---

### Post by scias on 2004-10-29
bump  :confused:

---

### Post by cacofonix on 2004-10-29
Could you post the error messages you got :D

---

### Post by scias on 2004-10-30
here are the messages:

```
juca@blah:~/fox-1.2.11 $ sudo make
Making all in utils
make[1]: Entrando no diretório `/home/juca/fox-1.2.11/utils'
make[1]: Nada a ser feito para `all'.
make[1]: Saindo do diretório `/home/juca/fox-1.2.11/utils'
Making all in include
make[1]: Entrando no diretório `/home/juca/fox-1.2.11/include'
make[1]: Nada a ser feito para `all'.
make[1]: Saindo do diretório `/home/juca/fox-1.2.11/include'
Making all in src
make[1]: Entrando no diretório `/home/juca/fox-1.2.11/src'
/bin/sh ../libtool --mode=compile c++ -DPACKAGE=\"fox\" -DVERSION=\"1.2.11\" -DHAVE_DLFCN_H=1 -DX_DISPLAY_MISSING=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_DIRENT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_VSSCANF=1 -DHAVE_VSNPRINTF=1 -DHAVE_LIBDL=1  -I. -I.  -I../include -I../include    -D_GNU_SOURCE -Wall -W -Wmissing-prototypes -Woverloaded-virtual -Wformat  -c FX4Splitter.cpp
rm -f .libs/FX4Splitter.lo
c++ -DPACKAGE=\"fox\" -DVERSION=\"1.2.11\" -DHAVE_DLFCN_H=1 -DX_DISPLAY_MISSING=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_SYS_WAIT_H=1 -DHAVE_DIRENT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_SYS_PARAM_H=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_VSSCANF=1 -DHAVE_VSNPRINTF=1 -DHAVE_LIBDL=1 -I. -I. -I../include -I../include -D_GNU_SOURCE -Wall -W -Wmissing-prototypes -Woverloaded-virtual -Wformat -c FX4Splitter.cpp    -fPIC -DPIC -o .libs/FX4Splitter.lo
In file included from FX4Splitter.cpp:24:
../include/xincs.h:164:19: X11/X.h: No such file or directory
../include/xincs.h:165:22: X11/Xlib.h: No such file or directory
../include/xincs.h:166:22: X11/Xcms.h: No such file or directory
../include/xincs.h:167:23: X11/Xutil.h: No such file or directory
../include/xincs.h:168:27: X11/Xresource.h: No such file or directory
../include/xincs.h:169:23: X11/Xatom.h: No such file or directory
../include/xincs.h:170:28: X11/cursorfont.h: No such file or directory
make[1]: ** [FX4Splitter.lo] Erro 1
make[1]: Saindo do diretório `/home/juca/fox-1.2.11/src'
make: ** [all-recursive] Erro 1

```

---

