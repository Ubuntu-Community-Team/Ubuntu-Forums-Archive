---
title: "[HELP] Problem with qmake and Makefile"
date: 2018-09-20
forum: General Help
---

### Post by jrefusta on 2018-09-20
Hello I have a problem with OpenGL or qmake...
When I make qmake-qt4, everything is ok, a new Makefile is created. But when i make "make" to do the Makefile works, the terminal send me this message:

/usr/lib/x86_64-linux-gnu/qt4/bin/uic MyForm.ui -o ui_MyForm.h
make: /usr/lib/x86_64-linux-gnu/qt4/bin/uic: Command not found
Makefile:210: recipe for target 'ui_MyForm.h' failed
make: *** [ui_MyForm.h] Error 127

I have Ubuntu 18.04, thanks for your time!

---

### Post by TheFu on 2018-09-20
```
make: /usr/lib/x86_64-linux-gnu/qt4/bin/uic: Command not found 
```is the problem. Fix that.  BTW, it doesn't appear to be a make problem, rather some dependency isn't being met. You need to fix that.  I've never heard of uic.

---

### Post by steeldriver on 2018-09-20
It appears to be provided by the [libqt4-dev-bin](https://packages.ubuntu.com/bionic/amd64/libqt4-dev-bin/filelist) package

---

### Post by jrefusta on 2018-09-20
Thank you for your answers! 
What should I do now? How can I fix that? I have no experience with ubuntu...

---

### Post by TheFu on 2018-09-20
Install the package steeldriver listed and try again?

The error messages are actually clear. Just have to read them.

---

### Post by jrefusta on 2018-09-22
Ok, I think that I solved that problem, but now appears another one.
Once I do "qmake-qt4", everything is fine, but then, when I do "make", this appears:
/usr/lib/x86_64-linux-gnu/qt4/bin/uic MyForm.ui -o ui_MyForm.h
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DQT_NO_DEBUG -DQT_OPENGL_LIB -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4/QtOpenGL -I/usr/include/qt4 -I/usr/include/glm -I/usr/X11R6/include -I. -I. -o main.o main.cpp
In file included from ui_MyForm.h:22:0,
                 from MyForm.h:1,
                 from main.cpp:2:
MyGLWidget.h:1:10: fatal error: QOpenGLFunctions_3_3_Core: No such file or directory
 #include <QOpenGLFunctions_3_3_Core>
          ^~~~~~~~~~~~~~~~~~~~~~~~~~~
compilation terminated.
Makefile:231: recipe for target 'main.o' failed
make: *** [main.o] Error 1

Can you help me again? Thanks!

---

### Post by spjackson on 2018-09-24
Can you provide a link to whatever it is you are trying to build along with any build instructions?

I have so far failed to find a package that provides QOpenGLFunctions_3_3_Core in /usr/include/qt4/QtOpenGL. (qtbase5-dev provides /usr/include/x86_64-linux-gnu/qt5/QtGui/QOpenGLFunctions_3_3_Core but that is obviously for Qt5 not Qt4.)

---

### Post by tomsten on 2019-03-22
has same problem with *make* command - I've tried to install unetbootin from sources on 18.10
> /usr/lib/x86_64-linux-gnu/qt4/bin/uic unetbootin.ui -o ui_unetbootin.h
make: /usr/lib/x86_64-linux-gnu/qt4/bin/uic: Command not found
make: *** [Makefile:200: ui_unetbootin.h] Error 127

any ideas?

---

### Post by spjackson on 2019-03-23
> **tomsten said:**
> has same problem with *make* command - I've tried to install unetbootin from sources on 18.10

Are you sure you need to do that?
> 
```

/usr/lib/x86_64-linux-gnu/qt4/bin/uic unetbootin.ui -o ui_unetbootin.h
make: /usr/lib/x86_64-linux-gnu/qt4/bin/uic: Command not found
make: *** [Makefile:200: ui_unetbootin.h] Error 127

```
any ideas?
The problem of missing uic is diagnosed in Steeldriver's post above. Install it with:
```

sudo apt install libqt4-dev-bin

```

---

