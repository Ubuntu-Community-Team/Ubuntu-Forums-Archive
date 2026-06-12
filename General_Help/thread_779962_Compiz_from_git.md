---
title: "Compiz from git"
date: 2008-05-03
forum: General Help
---

### Post by talsemgeest on 2008-05-03
When compiling compiz from git, I run ```
./autogen
``` then ```
make
``` but end up with the following error:
```
Making all in kde
make[2]: Entering directory `/home/tommy/compiz-scripts/compiz/kde'
Making all in window-decorator
make[3]: Entering directory `/home/tommy/compiz-scripts/compiz/kde/window-decorator'
/bin/bash ../../libtool --tag=CXX   --mode=link g++  -g -O2 -Wall -D_FORTIFY_SOURCE=2   -o kde-window-decorator decorator.moc.o window.moc.o KWinInterface_skel.o main.o utils.o decorator.o window.o options.o ../../libdecoration/libdecoration.la -ldbus-1 -lXdamage -lXcomposite -lXfixes   -L/usr/lib -L/usr/lib -lkdecore -lkdecorations -ldbus-qt-1 
g++ -g -O2 -Wall -D_FORTIFY_SOURCE=2 -o .libs/kde-window-decorator decorator.moc.o window.moc.o KWinInterface_skel.o main.o utils.o decorator.o window.o options.o  ../../libdecoration/.libs/libdecoration.so -ldbus-1 -lXdamage -lXcomposite -lXfixes -L/usr/lib /usr/lib/libkdecore.so /usr/lib/libkdecorations.so -ldbus-qt-1 
decorator.o: In function `~Decorator':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~KWinInterface':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `~Decorator':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~KWinInterface':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `~Decorator':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:251: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `KWinInterface':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `Decorator':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:196: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:196: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:196: undefined reference to `vtable for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:196: undefined reference to `vtable for KWD::Decorator'
decorator.o: In function `~KWinInterface':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/KWinInterface.h:9: undefined reference to `VTT for KWD::Decorator'
decorator.o: In function `Decorator':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/decorator.cpp:196: undefined reference to `vtable for KWD::Decorator'
window.o: In function `Window':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/window.cpp:87: undefined reference to `vtable for KWD::Window'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/window.cpp:87: undefined reference to `vtable for KWD::Window'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/window.cpp:87: undefined reference to `vtable for KWD::Window'
window.o: In function `~Window':
/home/tommy/compiz-scripts/compiz/kde/window-decorator/window.cpp:135: undefined reference to `vtable for KWD::Window'
/home/tommy/compiz-scripts/compiz/kde/window-decorator/window.cpp:135: undefined reference to `vtable for KWD::Window'
window.o:/home/tommy/compiz-scripts/compiz/kde/window-decorator/window.cpp:135: more undefined references to `vtable for KWD::Window' follow
collect2: ld returned 1 exit status
make[3]: *** [kde-window-decorator] Error 1
make[3]: Leaving directory `/home/tommy/compiz-scripts/compiz/kde/window-decorator'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tommy/compiz-scripts/compiz/kde'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tommy/compiz-scripts/compiz'
make: *** [all] Error 2

```

I have all of the dependancies installed, but still get the error.

Any suggestions?

---

### Post by Zorael on 2008-05-03
I'll go ahead and promote the compiz-git script about which there's a thread (currently) a few pages back on this forum.

[http://ubuntuforums.org/showthread.php?t=763829](http://ubuntuforums.org/showthread.php?t=763829)

---

### Post by talsemgeest on 2008-05-07
All good, with a couple of different scripts I got it all working. Thanks!

---

