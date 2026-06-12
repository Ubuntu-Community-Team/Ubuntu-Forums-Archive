---
title: "libpng.so.2: cannot open shared object file"
date: 2007-06-15
forum: General Help
---

### Post by hecato on 2007-06-15
Hi there, Im trying to run a program, but it fail with the follosing output

> 
error while loading shared libraries: libpng.so.2: cannot open shared object file: No such file or directory


I have installed libpng12-0 and libpng12-dev also I have installed libpng3 but none of this 2 solve the problem....


How I will go???

---

### Post by hecato on 2007-06-15
On guy in ubuntu-es helped me out

The app is Cgtutorial

> tyoc@pcbase:~/Desktop$ find / -iname "libpng*.so*" 2>/dev/null 
/usr/lib/libpng.so
/usr/lib/libpng12.so.0.15.0
/usr/lib/compiz/libpng.so
/usr/lib/gthumb/modules/libpngexporter.so
/usr/lib/libpng12.so
/usr/lib/libpng.so.3
/usr/lib/libpng12.so.0

tyoc@pcbase:~/Desktop$ sudo ln -s /usr/lib/libpng.so /usr/lib/libpng.so.2

tyoc@pcbase:~/Desktop$ CgTutorial 
CgTutorial: error while loading shared libraries: libtiff.so.3: cannot open shared object file: No such file or directory

tyoc@pcbase:~/Desktop$ find / -iname "libtiff*.so*" 2>/dev/null 
/usr/lib/libtiff.so.4.2.1
/usr/lib/libtiff.so.4

tyoc@pcbase:~/Desktop$ sudo ln -s /usr/lib/libtiff.so.4 /usr/lib/libtiff.so.3

tyoc@pcbase:~/Desktop$ CgTutorialAnd it work now...

---

