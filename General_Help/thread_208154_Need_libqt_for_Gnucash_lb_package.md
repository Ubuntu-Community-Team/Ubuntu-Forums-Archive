---
title: "Need libqt for Gnucash lb package?"
date: 2006-07-03
forum: General Help
---

### Post by ryan76 on 2006-07-03
I'm trying to install lb, the little budget tool for Gnucash. 

[http://www.teuton.org/~gabriel/lb/]("http://www.teuton.org/~gabriel/lb/")

I get to where I run ./configure but get this:


checking for Qt... ls: /lib/libqt*: No such file or directory
/usr/lib/libqt-mt.la   /usr/lib/libqt-mt.so    /usr/lib/libqt-mt.so.3.3    /usr/lib/libqthreads.so.12      /usr/lib/libqtmcop.so.1
/usr/lib/libqt-mt.prl  /usr/lib/libqt-mt.so.3  /usr/lib/libqt-mt.so.3.3.4  /usr/lib/libqthreads.so.12.3.0  /usr/lib/libqtmcop.so.1.0.0
./configure: line 21871: test: =: unary operator expected
yes:
    QT_CXXFLAGS=-I/include
    QT_DIR=
    QT_LIBS=-l/usr/lib -l  -lSM -lICE  -L/usr/X11R6/lib -lX11 -lXext -lXmu -lXt -lXi
    QT_UIC=
    QT_MOC=/bin/moc
checking correct functioning of Qt installation... failure
configure: error: Failed to find matching components of a complete
                  Qt installation. Try using more options,
                  see ./configure --help.

It's looking for libqt and I have installed every qt package I can find that looks vaguely relevant in synaptic plus a few others. If I install EVERY libqt package it will use 200MB!

Can anyone help please? What do I need to install?

Thanks

---

