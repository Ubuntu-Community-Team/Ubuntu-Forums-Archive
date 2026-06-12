---
title: "compiz plugin trouble"
date: 2007-10-08
forum: General Help
---

### Post by patmalcolm91 on 2007-10-08
hello, i just installed gutsy, and i love it, compiz is much more stable than my previous beryl setup. One problem though, i am trying to install the 3d plugin from the compiz website, and when i try to "make" the directory, it gives me a bunch of errors:

patrick@malcolm-laptop:~/Desktop/3d$ make
[: 1: ==: unexpected operator
-e compiling : 3d.c -> build/lib3d.loPackage libxml-2.0 was not found in the pkg-config search path.
Perhaps you should add the directory containing `libxml-2.0.pc'
to the PKG_CONFIG_PATH environment variable
Package 'libxml-2.0', required by 'compiz', not found
3d.c:37:20: error: compiz.h: No such file or directory
3d.c:50: error: expected specifier-qualifier-list before 'Bool'
3d.c:100: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'windowIs3D'
3d.c:191: error: expected ')' before '*' token
3d.c:248: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdPaintWindow'
3d.c:282: error: expected ')' before '*' token
3d.c:298: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdPaintScreen'
3d.c:315: error: expected ')' before '*' token
3d.c:501: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInitDisplay'
3d.c:525: error: expected ')' before '*' token
3d.c:538: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInitScreen'
3d.c:570: error: expected ')' before '*' token
3d.c:587: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInitWindow'
3d.c:667: error: expected ')' before '*' token
3d.c:689: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'tdInit'
3d.c:699: error: expected ')' before '*' token
3d.c:706: error: expected ')' before '*' token
3d.c:713: error: expected '=', ',', ';', 'asm' or '__attribute__' before 'opacityVTable'
3d.c:736: error: expected '=', ',', ';', 'asm' or '__attribute__' before '*' token
make: *** [build/lib3d.lo] Error 1


the problem is though, that i can't seem to be able to find libxml-2.0 to install it. Anyone have any idea what to do? is there an easier way to install the 3d plugin for compiz?

---

### Post by patmalcolm91 on 2007-10-08
Anyone???

---

### Post by Badjaccur on 2007-10-08
You can find libxml using the Synaptic package manager (System -> Administration -> Synaptic Package Manager) but what 3D plugin do you mean?

---

### Post by patmalcolm91 on 2007-10-08
it's just called "3d", it's the one that makes the windows come off the cube into space. In synaptic, i installed the libxml and the libxml2 packages, but there is no libxml-2.0 in the repositories, and the make process gives the same error still.

---

### Post by mmcev106 on 2007-11-29
The package is named "libxml2-dev" in Ubuntu.

---

