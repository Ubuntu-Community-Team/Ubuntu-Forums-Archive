---
title: "Compile Error"
date: 2008-02-01
forum: General Help
---

### Post by arettinger on 2008-02-01
I am attempting to install GraphCalc upon Ubuntu 7.10 via source. I have installed all known dependencies; however, I consistently receive the following error:

```
root@arettinger:/home/arettinger/Downloads/graphcalc/linux# make
/usr/share/qt3/bin/uic about.ui -o .ui/about.h
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/share/qt3/bin/uic graph2doptions.ui -o .ui/graph2doptions.h
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/share/qt3/bin/uic graph3doptions.ui -o .ui/graph3doptions.h
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/share/qt3/bin/uic mainform.ui -o .ui/mainform.h
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/share/qt3/bin/uic graph3drendermodes.ui -o .ui/graph3drendermodes.h
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
/usr/share/qt3/bin/uic outputmode.ui -o .ui/outputmode.h
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/main.o main.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/expression.o expression.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph2d.o graph2d.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph3d.o graph3d.cpp
/usr/share/qt3/bin/uic mainform.ui -i mainform.h -o .ui/mainform.cpp
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/mainform.o .ui/mainform.cpp
/usr/share/qt3/bin/uic about.ui -i about.h -o .ui/about.cpp
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/about.o .ui/about.cpp
/usr/share/qt3/bin/uic graph2doptions.ui -i graph2doptions.h -o .ui/graph2doptions.cpp
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph2doptions.o .ui/graph2doptions.cpp
/usr/share/qt3/bin/uic graph3doptions.ui -i graph3doptions.h -o .ui/graph3doptions.cpp
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph3doptions.o .ui/graph3doptions.cpp
.ui/../graph3doptions.ui.h:10: warning: unused parameter ‘p’
/usr/share/qt3/bin/uic graph3drendermodes.ui -i graph3drendermodes.h -o .ui/graph3drendermodes.cpp
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph3drendermodes.o .ui/graph3drendermodes.cpp
/usr/share/qt3/bin/uic outputmode.ui -i outputmode.h -o .ui/outputmode.cpp
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/outputmode.o .ui/outputmode.cpp
/usr/share/qt3/bin/uic  -embed graphcalc images/zoomin.png images/zoomout.png images/zoomprevious.png images/zoomstandard.png images/idr_main.png -o .ui/qmake_image_collection.cpp
Session management error: Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/qmake_image_collection.o .ui/qmake_image_collection.cpp
/usr/share/qt3/bin/moc graph3d.h -o .moc/moc_graph3d.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph3d.o .moc/moc_graph3d.cpp
/usr/share/qt3/bin/moc .ui/mainform.h -o .moc/moc_mainform.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_mainform.o .moc/moc_mainform.cpp
/usr/share/qt3/bin/moc .ui/about.h -o .moc/moc_about.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_about.o .moc/moc_about.cpp
/usr/share/qt3/bin/moc .ui/graph2doptions.h -o .moc/moc_graph2doptions.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph2doptions.o .moc/moc_graph2doptions.cpp
/usr/share/qt3/bin/moc .ui/graph3doptions.h -o .moc/moc_graph3doptions.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph3doptions.o .moc/moc_graph3doptions.cpp
/usr/share/qt3/bin/moc .ui/graph3drendermodes.h -o .moc/moc_graph3drendermodes.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph3drendermodes.o .moc/moc_graph3drendermodes.cpp
/usr/share/qt3/bin/moc .ui/outputmode.h -o .moc/moc_outputmode.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_outputmode.o .moc/moc_outputmode.cpp
g++  -o graphcalc .obj/main.o .obj/expression.o .obj/graph2d.o .obj/graph3d.o .obj/mainform.o .obj/about.o .obj/graph2doptions.o .obj/graph3doptions.o .obj/graph3drendermodes.o .obj/outputmode.o .obj/qmake_image_collection.o .obj/moc_graph3d.o .obj/moc_mainform.o .obj/moc_about.o .obj/moc_graph2doptions.o .obj/moc_graph3doptions.o .obj/moc_graph3drendermodes.o .obj/moc_outputmode.o   -L/usr/share/qt3/lib -L/usr/X11R6/lib -L/usr/lib -L/usr/kde/3.1/lib -lginac -lcln -lgmp -lqt-mt -lXext -lX11 -lm -lpthread
.obj/graph3d.o: In function `graph3d::zoomStandard()':
graph3d.cpp:(.text+0x2e1): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x2fb): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x315): undefined reference to `glRotatef'
.obj/graph3d.o: In function `graph3d::resizeGL(int, int)':
graph3d.cpp:(.text+0x391): undefined reference to `glViewport'
graph3d.cpp:(.text+0x39d): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x3a2): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x3e2): undefined reference to `glFrustum'
.obj/graph3d.o: In function `graph3d::initializeGL()':
graph3d.cpp:(.text+0x42e): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x433): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x43f): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x444): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x450): undefined reference to `glDrawBuffer'
graph3d.cpp:(.text+0x45c): undefined reference to `glEnable'
graph3d.cpp:(.text+0x468): undefined reference to `glShadeModel'
graph3d.cpp:(.text+0x47c): undefined reference to `glClearDepth'
.obj/graph3d.o: In function `graph3d::paintGL()':
graph3d.cpp:(.text+0x857): undefined reference to `glClear'
graph3d.cpp:(.text+0x863): undefined reference to `glClear'
graph3d.cpp:(.text+0x880): undefined reference to `glClearColor'
graph3d.cpp:(.text+0x88c): undefined reference to `glClear'
graph3d.cpp:(.text+0x8a0): undefined reference to `glPolygonMode'
graph3d.cpp:(.text+0x8a5): undefined reference to `glPushMatrix'
graph3d.cpp:(.text+0x8aa): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x8cc): undefined reference to `glTranslatef'
graph3d.cpp:(.text+0x8f2): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x918): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x93e): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x9a6): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9bf): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9d3): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9e7): undefined reference to `glCallList'
graph3d.cpp:(.text+0xa10): undefined reference to `glNewList'
graph3d.cpp:(.text+0xa33): undefined reference to `glLineWidth'
graph3d.cpp:(.text+0xa3f): undefined reference to `glBegin'
graph3d.cpp:(.text+0xa5b): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xa73): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xa8b): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xaa7): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xabf): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xad7): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xaf3): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xb0b): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xb23): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xb28): undefined reference to `glEnd'
graph3d.cpp:(.text+0xb2d): undefined reference to `glEndList'
graph3d.cpp:(.text+0xc07): undefined reference to `glNewList'
graph3d.cpp:(.text+0xc2a): undefined reference to `glLineWidth'
graph3d.cpp:(.text+0xc5a): undefined reference to `glBegin'
graph3d.cpp:(.text+0xc76): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xcda): undefined reference to `glVertex3d'
graph3d.cpp:(.text+0xcee): undefined reference to `glEnd'
graph3d.cpp:(.text+0xd4c): undefined reference to `glBegin'
graph3d.cpp:(.text+0xd68): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xdcc): undefined reference to `glVertex3d'
graph3d.cpp:(.text+0xde0): undefined reference to `glEnd'
graph3d.cpp:(.text+0xe13): undefined reference to `glEndList'
.obj/graph3d.o: In function `graph3d::resizeGL(int, int)':
graph3d.cpp:(.text+0x3ef): undefined reference to `glMatrixMode'
[B][I][U]collect2: ld returned 1 exit status
[/U][/I][/B]make: *** [graphcalc] Error 1
```
(Note the penultimate line.)
Make, and ld, accordingly, function as normal in other installations.
I have configured the application.

---

### Post by Jeffery Mewtamer on 2008-02-12
I too am having trouble with compile this application.

Here is the information I can provide for helping to discover a solution(Note: I am using Kubuntu Hardy):

The original tarball can be found at this URL:
[http://prdownloads.sourceforge.net/gcalc/graphcalc-0.0.1.tar.bz2?download](http://prdownloads.sourceforge.net/gcalc/graphcalc-0.0.1.tar.bz2?download)

Based on the instructions in the INSTALL text file, I believe I have installed all the necessary dependencies.

qmake, the first command that INSTALL tells me to execute after installing dependencies, fails when using libqt4-dev, but the version of qmake included in qt3-dev-tools runs with no output. Following a successful qmake with qt3-dev-tools, I execute make and get the following output:

```
jeffery@ubuntu:~/graphcalc-0.0.1/graphcalc/linux$ make
/usr/share/qt3/bin/uic about.ui -o .ui/about.h
/usr/share/qt3/bin/uic graph2doptions.ui -o .ui/graph2doptions.h
/usr/share/qt3/bin/uic graph3doptions.ui -o .ui/graph3doptions.h
/usr/share/qt3/bin/uic mainform.ui -o .ui/mainform.h
/usr/share/qt3/bin/uic graph3drendermodes.ui -o .ui/graph3drendermodes.h
/usr/share/qt3/bin/uic outputmode.ui -o .ui/outputmode.h
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/share/qt3/include -I.ui/ -I. -I.moc/ -o .obj/main.o main.cpp
main.cpp:1:26: error: qapplication.h: No such file or directory
In file included from main.cpp:2:
.ui/mainform.h:12:22: error: qvariant.h: No such file or directory
.ui/mainform.h:13:21: error: qpixmap.h: No such file or directory
.ui/mainform.h:14:25: error: qmainwindow.h: No such file or directory
In file included from .ui/mainform.h:15,
                 from main.cpp:2:
.ui/about.h:13:21: error: qdialog.h: No such file or directory
In file included from .ui/mainform.h:16,
                 from main.cpp:2:
./expression.h:16:21: error: qstring.h: No such file or directory
In file included from .ui/mainform.h:17,
                 from main.cpp:2:
.ui/graph2doptions.h:14:26: error: qcolordialog.h: No such file or directory
In file included from .ui/mainform.h:15,
                 from main.cpp:2:
.ui/about.h:24: error: expected class-name before ‘{’ token
.ui/about.h:25: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
.ui/about.h:27: error: expected ‘;’ before ‘public’
.ui/about.h:38: error: expected `:' before ‘slots’
.ui/about.h:39: error: expected primary-expression before ‘virtual’
.ui/about.h:39: error: ISO C++ forbids declaration of ‘slots’ with no type
.ui/about.h:39: error: expected ‘;’ before ‘virtual’
In file included from .ui/mainform.h:16,
                 from main.cpp:2:
./expression.h:23: error: expected `)' before ‘in_expression’
./expression.h:28: error: ‘QString’ does not name a type
./expression.h:34: error: ‘QString’ does not name a type
In file included from .ui/mainform.h:17,
                 from main.cpp:2:
.ui/graph2doptions.h:35: error: expected class-name before ‘{’ token
.ui/graph2doptions.h:36: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
.ui/graph2doptions.h:38: error: expected ‘;’ before ‘public’
.ui/graph2doptions.h:156: error: expected `:' before ‘slots’
.ui/graph2doptions.h:157: error: expected primary-expression before ‘virtual’
.ui/graph2doptions.h:157: error: ISO C++ forbids declaration of ‘slots’ with no type
.ui/graph2doptions.h:157: error: expected ‘;’ before ‘virtual’
.ui/graph2doptions.h:212: error: expected `:' before ‘slots’
.ui/graph2doptions.h:213: error: expected primary-expression before ‘virtual’
.ui/graph2doptions.h:213: error: ISO C++ forbids declaration of ‘slots’ with no type
.ui/graph2doptions.h:213: error: expected ‘;’ before ‘virtual’
In file included from .ui/mainform.h:18,
                 from main.cpp:2:
.ui/graph3doptions.h:31: error: expected class-name before ‘{’ token
.ui/graph3doptions.h:32: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
.ui/graph3doptions.h:34: error: expected ‘;’ before ‘public’
.ui/graph3doptions.h:139: error: expected `:' before ‘slots’
.ui/graph3doptions.h:140: error: expected primary-expression before ‘virtual’
.ui/graph3doptions.h:140: error: ISO C++ forbids declaration of ‘slots’ with no type
.ui/graph3doptions.h:140: error: expected ‘;’ before ‘virtual’
.ui/graph3doptions.h:168: error: expected `:' before ‘slots’
.ui/graph3doptions.h:169: error: expected primary-expression before ‘virtual’
.ui/graph3doptions.h:169: error: ISO C++ forbids declaration of ‘slots’ with no type
.ui/graph3doptions.h:169: error: expected ‘;’ before ‘virtual’
In file included from main.cpp:2:
.ui/mainform.h:39: error: expected class-name before ‘{’ token
.ui/mainform.h:40: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
.ui/mainform.h:42: error: expected ‘;’ before ‘public’
.ui/mainform.h:91: error: ISO C++ forbids declaration of ‘QMenuBar’ with no type
.ui/mainform.h:91: error: expected ‘;’ before ‘*’ token
.ui/mainform.h:122: error: ‘QString’ has not been declared
.ui/mainform.h:125: error: expected `:' before ‘slots’
.ui/mainform.h:126: error: expected primary-expression before ‘virtual’
.ui/mainform.h:126: error: ISO C++ forbids declaration of ‘slots’ with no type
.ui/mainform.h:126: error: expected ‘;’ before ‘virtual’
.ui/mainform.h:159: error: expected ‘,’ or ‘...’ before ‘&’ token
.ui/mainform.h:159: error: ISO C++ forbids declaration of ‘QString’ with no type
.ui/mainform.h:182: error: expected `:' before ‘slots’
.ui/mainform.h:183: error: expected primary-expression before ‘virtual’
.ui/mainform.h:183: error: ISO C++ forbids declaration of ‘slots’ with no type
.ui/mainform.h:183: error: expected ‘;’ before ‘virtual’
.ui/mainform.h:188: error: ‘QPixmap’ does not name a type
main.cpp: In function ‘int main(int, char**)’:
main.cpp:6: error: ‘QApplication’ was not declared in this scope
main.cpp:6: error: expected `;' before ‘a’
.ui/mainform.h:44: error: ‘mainform::~mainform()’ is private
main.cpp:7: error: within this context
main.cpp:8: error: ‘class mainform’ has no member named ‘show’
main.cpp:9: error: ‘a’ was not declared in this scope
main.cpp:9: error: ‘lastWindowClosed’ was not declared in this scope
main.cpp:9: error: ‘SIGNAL’ was not declared in this scope
main.cpp:9: error: ‘quit’ was not declared in this scope
main.cpp:9: error: ‘SLOT’ was not declared in this scope
main.cpp: At global scope:
main.cpp:4: warning: unused parameter ‘argc’
main.cpp:4: warning: unused parameter ‘argv’
make: *** [.obj/main.o] Error 1
jeffery@ubuntu:~/graphcalc-0.0.1/graphcalc/linux$      
```

I am guessing that the problem is either incompatibility between the newer versions of qmake/make and the 4 year old source code I am trying to compile or possibly some dependencies I am missing that are not mentioned in INSTALL.

Any help would be greatly appreciated.

---

### Post by mc4man on 2008-02-12
sorry -wrong app

---

### Post by mc4man on 2008-02-13
Took a look at it, doesn't seem possible to make, as far as depends there were some obscure things like libgmp3-dev, x-11, somewhat like  libqt3-mt-dev and such. The end result is it fails on opengl - can't see a resolution
here's a post on alt. apps  [http://ubuntuforums.org/showthread.php?t=282936](http://ubuntuforums.org/showthread.php?t=282936)
log if you want to try to find resolution
```

doug@doug-desktop:~/Desktop/graphcalc/linux$ make
/usr/share/qt3/bin/uic about.ui -o .ui/about.h
/usr/share/qt3/bin/uic graph2doptions.ui -o .ui/graph2doptions.h
/usr/share/qt3/bin/uic graph3doptions.ui -o .ui/graph3doptions.h
/usr/share/qt3/bin/uic mainform.ui -o .ui/mainform.h
/usr/share/qt3/bin/uic graph3drendermodes.ui -o .ui/graph3drendermodes.h
/usr/share/qt3/bin/uic outputmode.ui -o .ui/outputmode.h
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/main.o main.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/expression.o expression.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph2d.o graph2d.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph3d.o graph3d.cpp
/usr/share/qt3/bin/uic mainform.ui -i mainform.h -o .ui/mainform.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/mainform.o .ui/mainform.cpp
/usr/share/qt3/bin/uic about.ui -i about.h -o .ui/about.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/about.o .ui/about.cpp
/usr/share/qt3/bin/uic graph2doptions.ui -i graph2doptions.h -o .ui/graph2doptions.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph2doptions.o .ui/graph2doptions.cpp
/usr/share/qt3/bin/uic graph3doptions.ui -i graph3doptions.h -o .ui/graph3doptions.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph3doptions.o .ui/graph3doptions.cpp
.ui/../graph3doptions.ui.h:10: warning: unused parameter 
/usr/share/qt3/bin/uic graph3drendermodes.ui -i graph3drendermodes.h -o .ui/graph3drendermodes.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/graph3drendermodes.o .ui/graph3drendermodes.cpp
/usr/share/qt3/bin/uic outputmode.ui -i outputmode.h -o .ui/outputmode.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/outputmode.o .ui/outputmode.cpp
/usr/share/qt3/bin/uic  -embed graphcalc images/zoomin.png images/zoomout.png images/zoomprevious.png images/zoomstandard.png images/idr_main.png -o .ui/qmake_image_collection.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/qmake_image_collection.o .ui/qmake_image_collection.cpp
/usr/share/qt3/bin/moc graph3d.h -o .moc/moc_graph3d.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph3d.o .moc/moc_graph3d.cpp
/usr/share/qt3/bin/moc .ui/mainform.h -o .moc/moc_mainform.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_mainform.o .moc/moc_mainform.cpp
/usr/share/qt3/bin/moc .ui/about.h -o .moc/moc_about.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_about.o .moc/moc_about.cpp
/usr/share/qt3/bin/moc .ui/graph2doptions.h -o .moc/moc_graph2doptions.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph2doptions.o .moc/moc_graph2doptions.cpp
/usr/share/qt3/bin/moc .ui/graph3doptions.h -o .moc/moc_graph3doptions.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph3doptions.o .moc/moc_graph3doptions.cpp
/usr/share/qt3/bin/moc .ui/graph3drendermodes.h -o .moc/moc_graph3drendermodes.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_graph3drendermodes.o .moc/moc_graph3drendermodes.cpp
/usr/share/qt3/bin/moc .ui/outputmode.h -o .moc/moc_outputmode.cpp
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -DQT_SHARED -DQT_TABLET_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/kde/3.1/include -I/usr/include/qt3 -I.ui/ -I. -I.moc/ -o .obj/moc_outputmode.o .moc/moc_outputmode.cpp
g++  -o graphcalc .obj/main.o .obj/expression.o .obj/graph2d.o .obj/graph3d.o .obj/mainform.o .obj/about.o .obj/graph2doptions.o .obj/graph3doptions.o .obj/graph3drendermodes.o .obj/outputmode.o .obj/qmake_image_collection.o .obj/moc_graph3d.o .obj/moc_mainform.o .obj/moc_about.o .obj/moc_graph2doptions.o .obj/moc_graph3doptions.o .obj/moc_graph3drendermodes.o .obj/moc_outputmode.o   
-L/usr/share/qt3/lib -L/usr/X11R6/lib -L/usr/lib -L/usr/kde/3.1/lib -lginac -lcln -lgmp -lqt-mt -lXext -lX11 -lm -lpthread
.obj/graph3d.o: In function `graph3d::zoomStandard()':
graph3d.cpp:(.text+0x2e1): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x2fb): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x315): undefined reference to `glRotatef'
.obj/graph3d.o: In function `graph3d::resizeGL(int, int)':
graph3d.cpp:(.text+0x391): undefined reference to `glViewport'
graph3d.cpp:(.text+0x39d): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x3a2): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x3e2): undefined reference to `glFrustum'
.obj/graph3d.o: In function `graph3d::initializeGL()':
graph3d.cpp:(.text+0x42e): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x433): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x43f): undefined reference to `glMatrixMode'
graph3d.cpp:(.text+0x444): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x450): undefined reference to `glDrawBuffer'
graph3d.cpp:(.text+0x45c): undefined reference to `glEnable'
graph3d.cpp:(.text+0x468): undefined reference to `glShadeModel'
graph3d.cpp:(.text+0x47c): undefined reference to `glClearDepth'
.obj/graph3d.o: In function `graph3d::paintGL()':
graph3d.cpp:(.text+0x857): undefined reference to `glClear'
graph3d.cpp:(.text+0x863): undefined reference to `glClear'
graph3d.cpp:(.text+0x880): undefined reference to `glClearColor'
graph3d.cpp:(.text+0x88c): undefined reference to `glClear'
graph3d.cpp:(.text+0x8a0): undefined reference to `glPolygonMode'
graph3d.cpp:(.text+0x8a5): undefined reference to `glPushMatrix'
graph3d.cpp:(.text+0x8aa): undefined reference to `glLoadIdentity'
graph3d.cpp:(.text+0x8cc): undefined reference to `glTranslatef'
graph3d.cpp:(.text+0x8f2): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x918): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x93e): undefined reference to `glRotatef'
graph3d.cpp:(.text+0x9a6): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9bf): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9d3): undefined reference to `glCallList'
graph3d.cpp:(.text+0x9e7): undefined reference to `glCallList'
graph3d.cpp:(.text+0xa10): undefined reference to `glNewList'
graph3d.cpp:(.text+0xa33): undefined reference to `glLineWidth'
graph3d.cpp:(.text+0xa3f): undefined reference to `glBegin'
graph3d.cpp:(.text+0xa5b): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xa73): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xa8b): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xaa7): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xabf): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xad7): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xaf3): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xb0b): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xb23): undefined reference to `glVertex3f'
graph3d.cpp:(.text+0xb28): undefined reference to `glEnd'
graph3d.cpp:(.text+0xb2d): undefined reference to `glEndList'
graph3d.cpp:(.text+0xc07): undefined reference to `glNewList'
graph3d.cpp:(.text+0xc2a): undefined reference to `glLineWidth'
graph3d.cpp:(.text+0xc5a): undefined reference to `glBegin'
graph3d.cpp:(.text+0xc76): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xcda): undefined reference to `glVertex3d'
graph3d.cpp:(.text+0xcee): undefined reference to `glEnd'
graph3d.cpp:(.text+0xd4c): undefined reference to `glBegin'
graph3d.cpp:(.text+0xd68): undefined reference to `glColor3f'
graph3d.cpp:(.text+0xdcc): undefined reference to `glVertex3d'
graph3d.cpp:(.text+0xde0): undefined reference to `glEnd'
graph3d.cpp:(.text+0xe13): undefined reference to `glEndList'
.obj/graph3d.o: In function `graph3d::resizeGL(int, int)':
graph3d.cpp:(.text+0x3ef): undefined reference to `glMatrixMode'
collect2: ld returned 1 exit status
make: *** [graphcalc] Error 1

```

---

### Post by Christmas on 2008-02-13
Make sure you have all the development packages installed. Next, edit the Makefile inside the 'linux' directory, and on the line which has 'LINK     = g++'  add '-lGLU -lGL -lglut'. It should look like this:
```
LINK     = g++ -lGLU -lGL -lglut
```
(Look for it at the beginning of the file)
Next type:
```
qmake
make
```
I'll attach the binary compiled by me here. Just untar it to run.

---

### Post by mc4man on 2008-02-13
That editing works - though had to qmake,  edit, then just run make
What does glut mean or refer to?

---

### Post by Trail on 2008-02-14
It is some OpenGL helper library that can draw windows and stuff like that. "glu" is similar.

---

