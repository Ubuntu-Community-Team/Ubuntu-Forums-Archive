---
title: "Can't get QT to compile and install to be able to install other software"
date: 2005-09-15
forum: General Help
---

### Post by photoworx on 2005-09-15
I have been trying to get QT to compile and install for 2 days now and it just keeps kicking out errors when I try to make it.
The errors are:

In file included from ../../include/QtGui/private/qt_x11_p.h:1,
                 from kernel/qapplication.cpp:51:
../../src/gui/kernel/qt_x11_p.h:50:22: X11/Xlib.h: No such file or directory
../../src/gui/kernel/qt_x11_p.h:55:23: X11/Xutil.h: No such file or directory
../../src/gui/kernel/qt_x11_p.h:56:21: X11/Xos.h: No such file or directory
../../src/gui/kernel/qt_x11_p.h:57:23: X11/Xatom.h: No such file or directory
In file included from ../../include/QtGui/private/qt_x11_p.h:1,
                 from kernel/qapplication.cpp:51:
../../src/gui/kernel/qt_x11_p.h:246: error: 'Colormap' is used as a type, but
   is not defined as a type.
../../src/gui/kernel/qt_x11_p.h:247: error: syntax error before `*' token
../../src/gui/kernel/qt_x11_p.h:260: error: `Window' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:260: error: `Atom' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:260: error: parse error before `)' token
../../src/gui/kernel/qt_x11_p.h:260: error: 'Window' is used as a type, but is
   not defined as a type.
../../src/gui/kernel/qt_x11_p.h:263: error: `Window' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:263: error: parse error before `,' token
../../src/gui/kernel/qt_x11_p.h:264: error: `Window' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:264: error: parse error before `,' token
../../src/gui/kernel/qt_x11_p.h:266: error: `Window' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:266: error: parse error before `,' token
../../src/gui/kernel/qt_x11_p.h:277: error: parse error before `*' token
../../src/gui/kernel/qt_x11_p.h:279: error: `Atom' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:279: error: parse error before `)' token
../../src/gui/kernel/qt_x11_p.h:280: error: parse error before `char'
In file included from ../../include/QtGui/private/qt_x11_p.h:1,
                 from kernel/qapplication.cpp:51:
../../src/gui/kernel/qt_x11_p.h:328: error: syntax error before `*' token
../../src/gui/kernel/qt_x11_p.h:330: error: syntax error before `*' token
../../src/gui/kernel/qt_x11_p.h:332: error: 'Window' is used as a type, but is
   not defined as a type.
../../src/gui/kernel/qt_x11_p.h:338: error: 'Time' is used as a type, but is
   not defined as a type.
../../src/gui/kernel/qt_x11_p.h:339: error: 'Time' is used as a type, but is
   not defined as a type.
../../src/gui/kernel/qt_x11_p.h:365: error: syntax error before `*' token
../../src/gui/kernel/qt_x11_p.h:366: error: 'Colormap' is used as a type, but
   is not defined as a type.
../../src/gui/kernel/qt_x11_p.h:511: error: parse error before `[' token
../../src/gui/kernel/qt_x11_p.h:521: error: `FocusOut' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:521: error: enumerator value for `XFocusOut'
   not integer constant
../../src/gui/kernel/qt_x11_p.h:522: error: `FocusIn' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:522: error: enumerator value for `XFocusIn' not
   integer constant
../../src/gui/kernel/qt_x11_p.h:523: error: `KeyPress' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:523: error: enumerator value for `XKeyPress'
   not integer constant
../../src/gui/kernel/qt_x11_p.h:524: error: `KeyRelease' was not declared in
   this scope
../../src/gui/kernel/qt_x11_p.h:524: error: enumerator value for `XKeyRelease'
   not integer constant
../../src/gui/kernel/qt_x11_p.h:525: error: `None' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:525: error: enumerator value for `XNone' not
   integer constant
../../src/gui/kernel/qt_x11_p.h:526: error: `RevertToParent' was not declared
   in this scope
../../src/gui/kernel/qt_x11_p.h:526: error: enumerator value for `
   XRevertToParent' not integer constant
../../src/gui/kernel/qt_x11_p.h:527: error: `GrayScale' was not declared in
   this scope
../../src/gui/kernel/qt_x11_p.h:527: error: enumerator value for `XGrayScale'
   not integer constant
../../src/gui/kernel/qt_x11_p.h:529: error: `CursorShape' was not declared in
   this scope
../../src/gui/kernel/qt_x11_p.h:529: error: enumerator value for `XCursorShape'
   not integer constant
../../src/gui/kernel/qt_x11_p.h:543: error: `XPoint' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:543: error: template argument 1 is invalid
../../src/gui/kernel/qt_x11_p.h:543: error: `XPoint' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:543: error: enumerator value for `isLarge' not
   integer constant
../../src/gui/kernel/qt_x11_p.h:543: error: can't make `name' into a method --
   not in a class
../../src/gui/kernel/qt_x11_p.h:544: error: `XRectangle' was not declared in
   this scope
../../src/gui/kernel/qt_x11_p.h:544: error: template argument 1 is invalid
../../src/gui/kernel/qt_x11_p.h:544: error: `XRectangle' was not declared in
   this scope
../../src/gui/kernel/qt_x11_p.h:544: error: enumerator value for `isLarge' not
   integer constant
../../src/gui/kernel/qt_x11_p.h:544: error: can't make `name' into a method --
   not in a class
../../src/gui/kernel/qt_x11_p.h:545: error: `XChar2b' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:545: error: template argument 1 is invalid
../../src/gui/kernel/qt_x11_p.h:545: error: `XChar2b' was not declared in this
   scope
../../src/gui/kernel/qt_x11_p.h:545: error: enumerator value for `isLarge' not
   integer constant
../../src/gui/kernel/qt_x11_p.h:545: error: can't make `name' into a method --
   not in a class
make[3]: *** [.obj/debug-shared/qapplication.o] Error 1
make[3]: Leaving directory `/home/daniel/temp/qt-x11-opensource-src-4.0.1/src/gui'
make[2]: *** [debug-all] Error 2
make[2]: Leaving directory `/home/daniel/temp/qt-x11-opensource-src-4.0.1/src/gui'
make[1]: *** [sub-gui-make_default-ordered] Error 2
make[1]: Leaving directory `/home/daniel/temp/qt-x11-opensource-src-4.0.1/src'
make: *** [sub-src-make_default-ordered] Error 2

Any help at all would be really great.

Thanx

---

### Post by mlomker on 2005-09-15
Is your ./configure completing without any errors?  I thought about downloading a copy to look at the INSTALL document for dependencies, but their servers are slow.

---

### Post by photoworx on 2005-09-15
Yes, the ./configure finishes just fine and tells me to run make and then make install.

---

