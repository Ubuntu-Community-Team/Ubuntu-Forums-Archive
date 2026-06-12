---
title: "msn4lin"
date: 2005-06-16
forum: General Help
---

### Post by ciocanel on 2005-06-16
Hello, dunno if this is the place to ask, but... maybe you can help.
I'm trying to compile msn4lin(don't ask why) and I get a stupid error when i run configure:

checking for Qt... configure: error: Qt (>= Qt 3.0.1) (headers and libraries) not found. Please check your installation!
For more details about this problem, look at the end of config.log.

And this is the end of the config.log :
configure:6853: checking for Qt
configure: 6917: /usr/lib/qt3/include/qstyle.h
configure: 6917: /usr/lib/qt3/qstyle.h
configure: 6917: /usr/lib/qt/include/qstyle.h
configure: 6917: /usr/lib/qt/qstyle.h
configure: 6917: /usr/local/qt/include/qstyle.h
configure: 6917: /usr/include/qt/qstyle.h
configure: 6917: /usr/include/qstyle.h
configure: 6917: /usr/X11R6/include/X11/qt/qstyle.h
configure: 6917: /usr/X11R6/include/qt/qstyle.h
configure: 6917: /usr/X11R6/include/qt2/qstyle.h
configure: 6917: /usr/X11R6/include/qstyle.h
tried NO
tried /usr/lib/qt3/lib
tried /usr/lib/qt3
tried /usr/lib/qt/lib
tried /usr/lib/qt
tried /usr/X11R6/lib
configure:7029: rm -rf SunWS_cache; c++ -o conftest -O2 -fno-exceptions -fno-check-new -INO -I/usr/X11R6/include  -DQT_THREAD_SUPPORT  -D_REENTRANT  -L/usr/lib -L/usr/X11R6/lib   conftest.C  -lqt-mt -lpng -lz -lm -ljpeg -ldl  -lXext -lX11 -lSM -lICE  -lresolv -lpthread 1>&5
conftest.C:2:21: qglobal.h: No such file or directory
conftest.C:3:26: qapplication.h: No such file or directory
conftest.C:4:21: qcursor.h: No such file or directory
conftest.C:5:27: qstylefactory.h: No such file or directory
conftest.C:6:34: private/qucomextra_p.h: No such file or directory
conftest.C:8:2: #error 1
conftest.C: In function `int main()':
conftest.C:12: error: `QStyleFactory' undeclared (first use this function)
conftest.C:12: error: (Each undeclared identifier is reported only once for
   each function it appears in.)
conftest.C:12: error: parse error before `::' token
conftest.C:13: error: `QCursor' undeclared (first use this function)
configure: failed program was:
#include "confdefs.h"
#include <qglobal.h>
#include <qapplication.h>
#include <qcursor.h>
#include <qstylefactory.h>
#include <private/qucomextra_p.h>
#if ! (QT_VERSION >= 301)
#error 1
#endif

int main() {
    (void)QStyleFactory::create(QString::null);
    QCursor c(Qt::WhatsThisCursor);
    return 0;
}


I've installed all qt libs ... any help would be nice.
Thanks.

---

### Post by SGC on 2005-06-16
Most QT/KDE based applications requires the following packages to be compiled:

libqt3-mt-dev

kdelibs4-dev

---

