---
title: "Qt compiling help"
date: 2005-07-02
forum: General Help
---

### Post by zorbie on 2005-07-02
Hi there. New to Ubuntu and have been figuring most things out so far. However, I like to use qcomicbook for my comic viewing and I'm having trouble compiling it. Best I can guess, I'm missing a header file and I can't figure out what package I'm missing.

```

root@Desktop:/home/zor/qcomicbook-0.2.2 # ./configure
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... gawk
checking whether make sets $(MAKE)... yes
checking for g++... g++
checking for C++ compiler default output file name... a.out
checking whether the C++ compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking for style of include used by make... GNU
checking dependency style of g++... gcc3
checking for gcc... gcc
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking whether gcc needs -traditional... no
checking for vprintf... yes
checking for _doprnt... no
checking for X... libraries /usr/X11R6/lib, headers /usr/X11R6/include
checking for gethostbyname... yes
checking for connect... yes
checking for remove... yes
checking for shmat... yes
checking for IceConnectionNumber in -lICE... yes
checking for Qt... ls: /lib/libqt*: No such file or directory
/usr/lib/libqt-mt.so.3      /usr/lib/libqt.so.3        /usr/lib/libqte-mt.so.3.1.2  /usr/lib/libqthreads.so.12.3.0  /usr/lib/libqttestrunner.so.1.0
/usr/lib/libqt-mt.so.3.3    /usr/lib/libqt.so.3.3      /usr/lib/libqte.so           /usr/lib/libqtmcop.so.1         /usr/lib/libqttestrunner.so.1.0.0
/usr/lib/libqt-mt.so.3.3.3  /usr/lib/libqt.so.3.3.3    /usr/lib/libqte.so.2         /usr/lib/libqtmcop.so.1.0.0
/usr/lib/libqt.la           /usr/lib/libqte-mt.so      /usr/lib/libqte.so.2.3       /usr/lib/libqtopiakonnector.la
/usr/lib/libqt.prl          /usr/lib/libqte-mt.so.3    /usr/lib/libqte.so.2.3.7     /usr/lib/libqtopiakonnector.so
/usr/lib/libqt.so           /usr/lib/libqte-mt.so.3.1  /usr/lib/libqthreads.so.12   /usr/lib/libqttestrunner.so.1
yes:
    QT_CXXFLAGS=-I/usr/include/qte2
    QT_DIR=
    QT_LIBS=-l/usr/lib -l  -lSM -lICE  -L/usr/X11R6/lib -lX11 -lXext -lXmu -lXt -lXi
    QT_UIC=/usr/bin/uic
    QT_MOC=/usr/bin/moc
**checking correct functioning of Qt installation... cat: bnv_qt_test.c: No such file or directory**
failure
configure: error: Failed to find matching components of a complete
                  Qt installation. Try using more options,
                  see ./configure --help.

```

Any ideas?

---

### Post by Leif on 2005-09-10
this is a bit old, so I guess you're aware that the site for qcomicbook now has ubuntu packages ? [http://qcomicbook.horisone.com/](http://qcomicbook.horisone.com/)

---

