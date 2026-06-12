---
title: "Linking OpenGL libraries (GLUT)"
date: 2005-09-15
forum: General Help
---

### Post by benash on 2005-09-15
Hi,

I am trying to build a program that uses the GLUT library, but I am getting some linker errors:

g++ -o smview -rdynamic -L/home/ben/jot/lib/linux/D -L/usr/X11R6/lib  -fPIC -g  -Wall    -DGL_GLEXT_PROTOTYPES  smview.o  -L/usr/lib -Wl,-rpath /usr/lib  -lGLU -lGL -lpthread  -lglut  -lX11 -lXext  -ldl -lm   -lbase_jotapp -lglut_winsys -lglui -lwidgets -lmanip -lgest -lgeom -ldisp -lgtex -lmesh -lnet -ldev -lstd -lmlib -ldlhandler -llibpng -lzlib -lglew -lbase_jotapp -lglut_winsys -lglui -lwidgets -lmanip -lgest -lgeom -ldisp -lgtex -lmesh -lnet -ldev -lstd -lmlib -ldlhandler -llibpng -lzlib -lglew
/home/ben/jot/lib/linux/D/libglut_winsys.a(glut_winsys.o)(.text+0x12e1): In function `GLUT_WINSYS::set_focus()':
/home/ben/jot/glut_winsys/glut_winsys.C:443: undefined reference to `__glutCurrentWindow'
/home/ben/jot/lib/linux/D/libglut_winsys.a(glut_winsys.o)(.text+0x12ff):/home/ben/jot/glut_winsys/glut_winsys.C:444: undefined reference to `__glutCurrentWindow'
/home/ben/jot/lib/linux/D/libglut_winsys.a(glut_winsys.o)(.text+0x130e):/home/ben/jot/glut_winsys/glut_winsys.C:444: undefined reference to `__glutDisplay'
collect2: ld returned 1 exit status

I already had to add the "-lpthread" to the Makefile to get it to resolve some other references correctly.  Does anyone know if I need to include another library like this or if I have some other problem?

Thanks,
Ben

---

