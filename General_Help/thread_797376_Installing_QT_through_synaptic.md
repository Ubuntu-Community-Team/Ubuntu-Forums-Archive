---
title: "Installing QT through synaptic"
date: 2008-05-17
forum: General Help
---

### Post by Bucephalus01 on 2008-05-17
Hi

newbie here new to c++ and QT and linux.
I installed the following packages from synaptic, but I don't really know what I'm doing.
libqt4-core
libqt4-debug
libqt4-dev
libqt4-gui
libqt4-qt3support
libqt4-sql
libqthreads-12
qt4-designer
qt4-dev-tools
qt4-doc

I really don't know how to check if is installed correctly and operational so I just started doing the tutorial on the trolltech site here: [http://doc.trolltech.com/4.4/tutorials-tutorial-t1.html](http://doc.trolltech.com/4.4/tutorials-tutorial-t1.html)

When I write this program in netbeans, the packages in the include get underlined red and they aren't found. When I try and do it in vi, and use qmake as it says down at the bottom of the page of the tutorial and I try to make the file, once again I get complaints about not being able to find these packages. Is there something that I have missed?

buce
thanks.

---

### Post by Irony on 2008-05-17
Enable universe in your repository list - then reload.

Or go here; [http://linuxappfinder.com/package/qt4-dev-tools](http://linuxappfinder.com/package/qt4-dev-tools)

---

### Post by Bucephalus01 on 2008-05-17
Well it seems that i had already had the latest version in my synaptic.
I had universe already selected. and I have the versions that were stated on that website. 

What I did find is that I had to put the includes statements like this:

#include <qt4/Qt/qapplication.h>
#include <qt4/Qt/qpushbutton.h>

rather than this:
#include <QApplication.h>
#include <QPushButton.h>

The red lines went, but I'm still not out of the woods. When I try and compile in netbeans, which I know the cpp compiler works in because I have tested it, the following errors are spat out.

g++    -c -g -o build/Debug/GNU-Linux-x86/main.o main.cpp
In file included from main.cpp:9:
/usr/include/qt4/Qt/qapplication.h:47:37: error: QtCore/qcoreapplication.h: No such file or directory
/usr/include/qt4/Qt/qapplication.h:48:31: error: QtGui/qwindowdefs.h: No such file or directory
/usr/include/qt4/Qt/qapplication.h:49:27: error: QtCore/qpoint.h: No such file or directory
/usr/include/qt4/Qt/qapplication.h:50:26: error: QtCore/qsize.h: No such file or directory
/usr/include/qt4/Qt/qapplication.h:51:27: error: QtGui/qcursor.h: No such file or directory
In file included from main.cpp:10:
/usr/include/qt4/Qt/qpushbutton.h:47:35: error: QtGui/qabstractbutton.h: No such file or directory
In file included from main.cpp:9:
/usr/include/qt4/Qt/qapplication.h:64: error: ‘QT_BEGIN_HEADER’ does not name a type
/usr/include/qt4/Qt/qapplication.h:84: error: function definition does not declare parameters
/usr/include/qt4/Qt/qapplication.h:363: error: ‘QT_END_HEADER’ does not name a type
In file included from main.cpp:10:
/usr/include/qt4/Qt/qpushbutton.h:57: error: function definition does not declare parameters
In file included from main.cpp:11:
/usr/include/jmorecfg.h:64: error: expected constructor, destructor, or type conversion before ‘typedef’
main.cpp: In function ‘int main(int, char**)’:
main.cpp:18: error: ‘qapplication’ was not declared in this scope
main.cpp:18: error: expected `;' before ‘app’
main.cpp:19: error: ‘qpushbutton’ was not declared in this scope
main.cpp:19: error: expected `;' before ‘hello’
main.cpp:20: error: ‘hello’ was not declared in this scope
main.cpp:21: error: ‘app’ was not declared in this scope
make[1]: *** [build/Debug/GNU-Linux-x86/main.o] Error 1
make[1]: Leaving directory `/home/bucephalus/NetBeansProjects/qt_test'
make: *** [.build-impl] Error 2

Build failed. Exit value 2.


I think this has something to do with the same reason I have to put the path in the include statements.

---

