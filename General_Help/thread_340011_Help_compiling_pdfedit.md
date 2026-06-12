---
title: "Help compiling pdfedit"
date: 2007-01-16
forum: General Help
---

### Post by pg99 on 2007-01-16
pdfedit doesn't seem to be available as a package so I tried compiling it from source but I can't get past this QT problem where it can't find the QT headers even though I've installed libqt3-headers.

Here's the relevant part of the output
make[2]: Leaving directory `/home/phil/pkg/pdfedit-0.2.3/src/kernel'
cd kpdf-kde-3.3.2 && qmake && make staticlib
make[2]: Entering directory `/home/phil/pkg/pdfedit-0.2.3/src/kpdf-kde-3.3.2'
g++ -c -pipe -g -Wall -W -O2 -D_REENTRANT  -DQT_NO_DEBUG -DQT_THREAD_SUPPORT -I/usr/share/qt3/mkspecs/default -I. -I../xpdf -I../xpdf/xpdf -I../xpdf/goo -I../xpdf/splash -I../xpdf/fofi -I/usr/share/qt3/include -o QOutputDevPixmap.o QOutputDevPixmap.cpp
QOutputDevPixmap.cpp:25:21: error: qpixmap.h: No such file or directory
QOutputDevPixmap.cpp:26:20: error: qimage.h: No such file or directory

my problem seems to be that I can't get it to look in the directory where the headers actually are (/usr/include/qt3), it keeps using -I/usr/share/qt3/include even though I've set the QTDIR to the right location ...
>echo $QTDIR
/usr/include/qt3

anyone managed to compile this app, or even know of any pkgs for it?

I'm running 'edgy' BTW

thanks for any help
Phil

---

### Post by PetePhillips on 2007-06-13
Hi

You need to make sure that you have the various boost libraries installed - libboost-dev and libboost-iostreams-dev

then at the shell, type:

    export QMAKESPEC=linux-g++
    export QTDIR=/usr

After doing this on my Edgy Eft machine, pdfedit compiled cleanly.
 
If you get warnings about libraries not being installed, just search for them in synaptic and install them.

THis gave me a working binary (but, I have to say, very slow).

Pete

---

### Post by pg99 on 2007-06-13
jeez mate you must be kidding, i posted that q almost 6 months ago - why bother replying?  I could understand if you specifically had solved the problem i asked about but what's the point of your reply?  Do you think I would have got that far if I didn't know pdfedit needed boost libs???

you must be desperate to rack up your post count or something...

---

### Post by guardsman85 on 2007-06-20
> **pg99 said:**
> 
thanks for any help
Phil
Phil, you evidently forgot your sarcasm tags...  

If you know so much and don't need the suggestions at this point, then why are you still monitoring the thread anyway?  Don't be inconsiderate to people who are trying to help...especially when you're the one who asked for it.  Fact of the matter is that I needed this information.  If Pete hadn't replied last week it wouldn't be there.  If you're going to act inconsiderately then people are going to just stop helping you!

---

### Post by pg99 on 2007-06-20
so let's get this straight - it's fine for anyone to post anything in response to a question. doesn't matter if it does nothing to answer the original question as long as it helps you later. Fine I'll remember that in future.

Oh and thanks for reminding me to turn of my subscription to this thread.

---

### Post by stchman on 2007-06-20
> **pg99 said:**
> so let's get this straight - it's fine for anyone to post anything in response to a question. doesn't matter if it does nothing to answer the original question as long as it helps you later. Fine I'll remember that in future.

Oh and thanks for reminding me to turn of my subscription to this thread.

Go to [www.getdeb.net](www.getdeb.net).  They have PDFEdit as a .deb for Ubuntu.

---

