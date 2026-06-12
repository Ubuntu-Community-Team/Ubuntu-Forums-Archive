---
title: "Compiling Cutecom"
date: 2007-03-31
forum: General Help
---

### Post by aseem on 2007-03-31
Hi, this is my first post to this great forum.  I have searched for my problem, but found nothing, so I hope this is the correct place to post.

I have downloaded the source files for CuteCom [http://cutecom.sourceforge.net/]("http://cutecom.sourceforge.net/"), a graphical serial terminal for linux.

I have never compiled a program for linux before, but managed to run qmake after installing g++.  After running qmake, I'm supposed to run make and make install, but I get these errors when running make, so now i'm stuck.

btw, I'm currently working on 'the great switch' from XP to Ubuntu. I'm NOT going the Vi$ta road......

root@ase-ubu:/usr/local/src/cutecom-0.14.1# make
g++ -c -pipe -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I/usr/share/qt3/include -I./ -I. -I.moc/ -o .obj/main.o main.cpp
main.cpp:19:26: error: qapplication.h: No such file or directory
In file included from qcppdialogimpl.h:22,
                 from main.cpp:21:
cutecommdlg.h:13:22: error: qvariant.h: No such file or directory
cutecommdlg.h:14:21: error: qwidget.h: No such file or directory
In file included from main.cpp:21:
qcppdialogimpl.h:26:29: error: qsocketnotifier.h: No such file or directory
qcppdialogimpl.h:27:20: error: qtimer.h: No such file or directory
qcppdialogimpl.h:28:23: error: qdatetime.h: No such file or directory
qcppdialogimpl.h:29:19: error: qfile.h: No such file or directory
cutecommdlg.h:33: error: expected class-name before ‘{’ token
cutecommdlg.h:34: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
cutecommdlg.h:36: error: expected ‘;’ before ‘public’
cutecommdlg.h:93: error: expected `:' before ‘slots’
cutecommdlg.h:94: error: expected primary-expression before ‘virtual’
cutecommdlg.h:94: error: ISO C++ forbids declaration of ‘slots’ with no type
cutecommdlg.h:94: error: expected ‘;’ before ‘virtual’
qcppdialogimpl.h:41: error: ISO C++ forbids declaration of ‘Q_OBJECT’ with no type
qcppdialogimpl.h:42: error: expected ‘;’ before ‘public’
qcppdialogimpl.h:44: error: ‘QObject’ has not been declared
qcppdialogimpl.h:44: error: ‘QEvent’ has not been declared
qcppdialogimpl.h:45: error: expected `:' before ‘slots’
qcppdialogimpl.h:46: error: expected primary-expression before ‘void’
qcppdialogimpl.h:46: error: ISO C++ forbids declaration of ‘slots’ with no type
qcppdialogimpl.h:46: error: expected ‘;’ before ‘void’
qcppdialogimpl.h:66: error: expected ‘,’ or ‘...’ before ‘&’ token
qcppdialogimpl.h:66: error: ISO C++ forbids declaration of ‘QString’ with no type
qcppdialogimpl.h:72: error: expected ‘,’ or ‘...’ before ‘&’ token
qcppdialogimpl.h:72: error: ISO C++ forbids declaration of ‘QString’ with no type
qcppdialogimpl.h:73: error: expected ‘,’ or ‘...’ before ‘&’ token
qcppdialogimpl.h:73: error: ISO C++ forbids declaration of ‘QString’ with no type
qcppdialogimpl.h:80: error: ISO C++ forbids declaration of ‘QSocketNotifier’ with no type
qcppdialogimpl.h:80: error: expected ‘;’ before ‘*’ token
qcppdialogimpl.h:87: error: ‘QString’ does not name a type
qcppdialogimpl.h:89: error: ‘QTimer’ does not name a type
qcppdialogimpl.h:90: error: ‘QTime’ does not name a type
qcppdialogimpl.h:91: error: ‘QString’ does not name a type
qcppdialogimpl.h:93: error: ‘QTimer’ does not name a type
qcppdialogimpl.h:98: error: ‘QFile’ does not name a type
qcppdialogimpl.h:40: warning: ‘class QCPPDialogImpl’ has virtual functions but non-virtual destructor
main.cpp: In function ‘int main(int, char**)’:
main.cpp:26: error: ‘QApplication’ was not declared in this scope
main.cpp:26: error: expected `;' before ‘a’
main.cpp:27: error: no matching function for call to ‘QCPPDialogImpl::QCPPDialogImpl(int)’
qcppdialogimpl.h:40: note: candidates are: QCPPDialogImpl::QCPPDialogImpl()
qcppdialogimpl.h:40: note:                 QCPPDialogImpl::QCPPDialogImpl(const QCPPDialogImpl&)
cutecommdlg.h: In destructor ‘QCPPDialogImpl::~QCPPDialogImpl()’:
cutecommdlg.h:38: error: ‘CuteCommDlg::~CuteCommDlg()’ is private
qcppdialogimpl.h:40: error: within this context
main.cpp: In function ‘int main(int, char**)’:
main.cpp:27: note: synthesized method ‘QCPPDialogImpl::~QCPPDialogImpl()’ first required here 
main.cpp:28: error: ‘class QCPPDialogImpl’ has no member named ‘show’
main.cpp:29: error: ‘a’ was not declared in this scope
main.cpp:29: error: ‘lastWindowClosed’ was not declared in this scope
main.cpp:29: error: ‘SIGNAL’ was not declared in this scope
main.cpp:29: error: ‘quit’ was not declared in this scope
main.cpp:29: error: ‘SLOT’ was not declared in this scope
main.cpp: At global scope:
main.cpp:24: warning: unused parameter ‘argc’
main.cpp:24: warning: unused parameter ‘argv’
make: *** [.obj/main.o] Error 1

---

### Post by acormack on 2007-03-31
I am normally too lazy to compile programs.  

Have you searched for a .deb file e.g. this one: [http://debian.internet.gr/debian/pool/main/c/cutecom/cutecom_0.14.1-2_i386.deb](http://debian.internet.gr/debian/pool/main/c/cutecom/cutecom_0.14.1-2_i386.deb)

then sudo dpkg -i cutecom_0.14.1-2_i386.deb

If you want to fix the compile problem you could try running 

./configure

before the make command


Alec

---

### Post by Maestro23 on 2007-03-31
Also read Section 4: Installing from Source: [http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

*Compiling from source is not recommended for people new to linux.  As you have found out, you can run into a lot of dependency issues.

Good luck though.

---

