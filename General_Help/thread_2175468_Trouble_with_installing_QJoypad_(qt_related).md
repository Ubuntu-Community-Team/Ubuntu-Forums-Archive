---
title: "Trouble with installing QJoypad (qt related?)"
date: 2013-09-19
forum: General Help
---

### Post by Kymus on 2013-09-19
While installing QJoypadd, I encountered this problem:

```
kymus@HT:~/Downloads/qjoypad-4.1.0/src$ make
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o axis.o axis.cpp
In file included from axis.h:13:0,
                 from axis.cpp:1:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o axis_edit.o axis_edit.cpp
In file included from axis.h:13:0,
                 from axis_edit.h:5,
                 from axis_edit.cpp:1:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o axisw.o axisw.cpp
In file included from axis.h:13:0,
                 from axisw.h:6,
                 from axisw.cpp:1:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o button.o button.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o button_edit.o button_edit.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o buttonw.o buttonw.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o event.o event.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o flash.o flash.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o icon.o icon.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o joypad.o joypad.cpp
joypad.cpp:251:6: warning: unused parameter ‘fd’ [-Wunused-parameter]
joypad.cpp: In member function ‘void JoyPad::resetToDev(int)’:
joypad.cpp:58:30: warning: ignoring return value of ‘ssize_t read(int, void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o joypadw.o joypadw.cpp
In file included from axis.h:13:0,
                 from axisw.h:6,
                 from joypadw.h:8,
                 from joypadw.cpp:1:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o joyslider.o joyslider.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o keycode.o keycode.cpp
keycode.cpp: In function ‘const QString ktos(int)’:
keycode.cpp:10:37: warning: ‘KeySym XKeycodeToKeysym(Display*, KeyCode, int)’ is deprecated (declared at /usr/include/X11/Xlib.h:1695) [-Wdeprecated-declarations]
keycode.cpp:10:72: warning: ‘KeySym XKeycodeToKeysym(Display*, KeyCode, int)’ is deprecated (declared at /usr/include/X11/Xlib.h:1695) [-Wdeprecated-declarations]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o layout.o layout.cpp
layout.cpp: In member function ‘void LayoutManager::updateJoyDevs()’:
layout.cpp:360:42: warning: ignoring return value of ‘ssize_t read(int, void*, size_t)’, declared with attribute warn_unused_result [-Wunused-result]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o layout_edit.o layout_edit.cpp
layout_edit.cpp: In member function ‘void LayoutEdit::setLayout(QString)’:
layout_edit.cpp:105:42: warning: comparison between signed and unsigned integer expressions [-Wsign-compare]
In file included from axis.h:13:0,
                 from joypad.h:6,
                 from layout.h:21,
                 from layout_edit.h:10,
                 from layout_edit.cpp:1:
error.h: At global scope:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o main.o main.cpp
main.cpp: In function ‘int main(int, char**)’:
main.cpp:150:49: warning: suggest braces around empty body in an ‘if’ statement [-Wempty-body]
In file included from axis.h:13:0,
                 from joypad.h:6,
                 from layout.h:21,
                 from main.cpp:12:
error.h: At global scope:
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o quickset.o quickset.cpp
In file included from axis.h:13:0,
                 from joypad.h:6,
                 from quickset.h:14,
                 from quickset.cpp:1:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o getkey.o getkey.cpp
getkey.cpp: In member function ‘virtual bool GetKey::x11Event(XEvent*)’:
getkey.cpp:36:13: warning: ‘KeySym XKeycodeToKeysym(Display*, KeyCode, int)’ is deprecated (declared at /usr/include/X11/Xlib.h:1695) [-Wdeprecated-declarations]
getkey.cpp:36:55: warning: ‘KeySym XKeycodeToKeysym(Display*, KeyCode, int)’ is deprecated (declared at /usr/include/X11/Xlib.h:1695) [-Wdeprecated-declarations]
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. axis.h -o moc_axis.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_axis.o moc_axis.cpp
In file included from axis.h:13:0,
                 from moc_axis.cpp:10:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. axis_edit.h -o moc_axis_edit.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_axis_edit.o moc_axis_edit.cpp
In file included from axis.h:13:0,
                 from axis_edit.h:5,
                 from moc_axis_edit.cpp:10:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. button.h -o moc_button.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_button.o moc_button.cpp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. button_edit.h -o moc_button_edit.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_button_edit.o moc_button_edit.cpp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. flash.h -o moc_flash.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_flash.o moc_flash.cpp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. icon.h -o moc_icon.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_icon.o moc_icon.cpp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. joypad.h -o moc_joypad.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_joypad.o moc_joypad.cpp
In file included from axis.h:13:0,
                 from joypad.h:6,
                 from moc_joypad.cpp:10:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. joypadw.h -o moc_joypadw.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_joypadw.o moc_joypadw.cpp
In file included from axis.h:13:0,
                 from axisw.h:6,
                 from joypadw.h:8,
                 from moc_joypadw.cpp:10:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. keycode.h -o moc_keycode.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_keycode.o moc_keycode.cpp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. layout.h -o moc_layout.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_layout.o moc_layout.cpp
In file included from axis.h:13:0,
                 from joypad.h:6,
                 from layout.h:21,
                 from moc_layout.cpp:10:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. getkey.h -o moc_getkey.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_getkey.o moc_getkey.cpp
/usr/lib/x86_64-linux-gnu/qt4/bin/moc -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. layout_edit.h -o moc_layout_edit.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DDEVDIR=\"/dev/input\" -DICON24=\"/usr/local/share/pixmaps/qjoypad/icon24.png\" -DICON64=\"/usr/local/share/pixmaps/qjoypad/icon64.png\" -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -o moc_layout_edit.o moc_layout_edit.cpp
In file included from axis.h:13:0,
                 from joypad.h:6,
                 from layout.h:21,
                 from layout_edit.h:10,
                 from moc_layout_edit.cpp:10:
error.h:8:13: warning: ‘void error(QString, QString)’ defined but not used [-Wunused-function]
error.h:21:13: warning: ‘void debug_mesg(...)’ defined but not used [-Wunused-function]
g++ -m64 -Wl,-O1 -o qjoypad axis.o axis_edit.o axisw.o button.o button_edit.o buttonw.o event.o flash.o icon.o joypad.o joypadw.o joyslider.o keycode.o layout.o layout_edit.o main.o quickset.o getkey.o moc_axis.o moc_axis_edit.o moc_button.o moc_button_edit.o moc_flash.o moc_icon.o moc_joypad.o moc_joypadw.o moc_keycode.o moc_layout.o moc_getkey.o moc_layout_edit.o    -L/usr/lib/x86_64-linux-gnu -lXtst -lQtGui -lQtCore -lpthread 
/usr/bin/ld: keycode.o: undefined reference to symbol 'XKeycodeToKeysym'
/usr/bin/ld: note: 'XKeycodeToKeysym' is defined in DSO /usr/lib/x86_64-linux-gnu/libX11.so.6 so try adding it to the linker command line
/usr/lib/x86_64-linux-gnu/libX11.so.6: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make: *** [qjoypad] Error 1
kymus@HT:~/Downloads/qjoypad-4.1.0/src$ make install
g++ -m64 -Wl,-O1 -o qjoypad axis.o axis_edit.o axisw.o button.o button_edit.o buttonw.o event.o flash.o icon.o joypad.o joypadw.o joyslider.o keycode.o layout.o layout_edit.o main.o quickset.o getkey.o moc_axis.o moc_axis_edit.o moc_button.o moc_button_edit.o moc_flash.o moc_icon.o moc_joypad.o moc_joypadw.o moc_keycode.o moc_layout.o moc_getkey.o moc_layout_edit.o    -L/usr/lib/x86_64-linux-gnu -lXtst -lQtGui -lQtCore -lpthread 
/usr/bin/ld: keycode.o: undefined reference to symbol 'XKeycodeToKeysym'
/usr/bin/ld: note: 'XKeycodeToKeysym' is defined in DSO /usr/lib/x86_64-linux-gnu/libX11.so.6 so try adding it to the linker command line
/usr/lib/x86_64-linux-gnu/libX11.so.6: could not read symbols: Invalid operation
collect2: error: ld returned 1 exit status
make: *** [qjoypad] Error 1

```

I'm going to go out on a limb and guess that the problem is Qt related, but outside of that... no diea

---

### Post by Kirboosy on 2013-09-19
You are correct that is is QT related. Are you sure that you have QT4 installed on your system? In the documentation it says that QT4 is required for successful compile.


If it still doesn't want to compile there are prebuilt packages that you can install on your system.

[UbuntuUpdates Packages]("http://www.ubuntuupdates.org/pm/qjoypad")


Hope that helps!
~Caboose

---

### Post by Kymus on 2013-09-19
Thanks for the link, Caboose! 

When I was configuring it, it told me I needed qt, so when I googled for the command to add it to the ppa, the info was rather outdated (sudo *aptitude*) so I winged it. There were two commands listed for qt and I only did one (other one didn't work), so I guess my qt dependency was half met. The .deb installed fine.

---

### Post by kostkon on 2013-09-20
There's a [new more up-to-date replacement app for QJoypad]("http://www.webupd8.org/2013/09/map-keyboardmouse-input-to-your-gamepad.html"), you might want to check it out.

---

### Post by Kymus on 2013-09-20
oh wonderful, thanks!!

---

### Post by Kirboosy on 2013-09-20
That is a great link. Didn't know they had an active fork. Thanks kostkon!

---

