---
title: "Installing Inq"
date: 2013-05-14
forum: General Help
---

### Post by dryder on 2013-05-14
Hi 
12.04-2 AMD64 Classic

I've been trying to install [Inq]("http://www.fioreltech.net/project/inq/version-1.0.0/doc/en/doc-installation") as it recognizes my Epson Stylus Photo P50 (I want to be able to see the ink levels which I can't with mtink).

I have installed:
libinklevel5 vers 0.8.0-1.1
libpoppler-qt4-3
libpoppler-qt4-dev
and downloaded inq-1.0.0.tar.gz.

Following the instructions to install inq, I can't get it to QMAKE=<path-to-qmake> ./configure
```
QMAKE=/usr/share/perl5/Debian/Debhelper/Buildsystem ./configure
``` and obviously can't go further (qmake fails too.)

I have tried:
QMAKE=/usr/share/perl5/Debian/Debhelper/Buildsystem ./configure
qmake=/usr/share/perl5/Debian/Debhelper/Buildsystem ./configure
qmake_qt4=/usr/share/perl5/Debian/Debhelper/Buildsystem ./configure

Please can anybody help?

David

---

### Post by pdc on 2013-05-15
I am not clear what you wish to install:

many would use ink

[http://ink.sourceforge.net/](http://ink.sourceforge.net/)

that uses Libinklevel

the page that lists supported printers

[http://libinklevel.sourceforge.net/index.html#supported](http://libinklevel.sourceforge.net/index.html#supported)

says your printer is supported

this page

[http://libinklevel.sourceforge.net/#installation](http://libinklevel.sourceforge.net/#installation)

seems to suggest that you install libinklevel first; and then choose some interface to interact with it; ..........the best seems ink that uses CLI 

............what is this Ing you refer to please?

---

### Post by dryder on 2013-05-17
I wanted a gui based interface - inq is a gui.

Not meaning to be trite, I'm trying to install inq as per the instructions [here]("http://www.fioreltech.net/project/inq/version-1.0.0/doc/en/doc-installation")

[This page]("http://www.fioreltech.net/project/start") is the gui

I can't ```
 QMAKE=<path-to-qmake> ./configure
```


Thanks

---

### Post by pdc on 2013-05-17
I think you are missing some packages including libqt4-dev and qt4-qmake

try 

> [COLOR="#FF0000"]sudo apt-get install libxtst-dev build-essential libqt4-dev qt4-qmake[/COLOR]

(In your title, I seenow you spelt it as INQ but in your post it seems to me you spelt it as ING .......which I couldn't find on google!)

---

### Post by dryder on 2013-05-17
Apologies for the misspelling - how can I change the title?

---

### Post by steeldriver on 2013-05-17
> **dryder said:**
> 
I can't ```
 QMAKE=<path-to-qmake> ./configure
```


Thanks

You're more likely to get help if you post the actual error that you are getting - saying "I can't" doesn't really give us any clue what the problem might be

---

### Post by dryder on 2013-05-17
Point taken  steeldriver and thanks pdc - your suggestion enabled me to do [HTML]QMAKE=/usr/bin/qmake-qt4 ./configure[/HTML]

On the next step:
make

I get:[HTML]/usr/bin/qmake-qt4 -o MyMakefile inq.pro
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o devicedialog.o devicedialog.cpp
In file included from devicedialog.cpp:4:0:
helpbrowser.h:5:29: fatal error: boost/utility.hpp: No such file or directory
compilation terminated.
make: *** [devicedialog.o] Error 1
[/HTML]

I appreciate your help very much.

---

### Post by steeldriver on 2013-05-17
Do you have the boost C++ libraries installed ( [http://www.boost.org/](http://www.boost.org/) )? or at least the base libboost-dev?

```
apt-cache policy libboost-dev
```

---

### Post by dryder on 2013-05-18
I have installed libboost-dev. It helped but 'make' then resulted in:[HTML]~/Desktop/inq-1.0.0$ make
/usr/bin/qmake-qt4 -o MyMakefile inq.pro
/usr/bin/uic-qt4 devicedialog.ui -o ui_devicedialog.h
/usr/bin/uic-qt4 centralwidget.ui -o ui_centralwidget.h
/usr/bin/uic-qt4 helpbrowser.ui -o ui_helpbrowser.h
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o devicedialog.o devicedialog.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o main.o main.cpp
g++ -c -m64 -pipe -O2 -Wall -W -D_REENTRANT -DQT_WEBKIT -DQT_NO_DEBUG -DQT_GUI_LIB -DQT_NETWORK_LIB -DQT_CORE_LIB -DQT_SHARED -I/usr/share/qt4/mkspecs/linux-g++-64 -I. -I/usr/include/qt4/QtCore -I/usr/include/qt4/QtNetwork -I/usr/include/qt4/QtGui -I/usr/include/qt4 -I. -I. -I. -o mainwindow.o mainwindow.cpp
mainwindow.cpp:15:22: fatal error: inklevel.h: No such file or directory
compilation terminated.
make: *** [mainwindow.o] Error 1
[/HTML] and I can't figure out what inklevel.h is.

libinklevel5 is installed.

I've not had so much difficulty installing before - usually I have identified the missing files. Here, I am just lost.

Thanks for your help.

---

### Post by steeldriver on 2013-05-18
There's a package you can install called 'apt-file' which is perfect for winkling out things like this - in this case:

```
$ apt-file search 'inklevel.h'
libinklevel-**dev**: /usr/include/inklevel.h

```

meaning you need the libinklevel-**dev** (i.e. development) package because you're trying to build stuff with libinklevel rather than just use it.

---

### Post by dryder on 2013-05-18
Thanks! apt-file is a useful tool.

It did 'make' successfully.

I'm stuck on the last two commands:```
$ su -c "make install"
Parola d'ordine: <tua password> 
```

su - is it really a good idea to create a su password for this or even log in as su to do it? There must be a reason for su but, well, I'm only installing a package - a common occurrence.  

Parola d'ordine: <tua password> - I haven't got there yet but it looks like trouble!

---

### Post by steeldriver on 2013-05-18
For Ubuntu, you would usually do 

```
sudo make install
```

instead - see [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by dryder on 2013-05-18
steeldriver and pdc

Thanks!

It is installed and working.

I am particularly grateful for your, **patience, help and explanations, enabling me to learn**.

I hope the community see this post.

'Thanks' seems inadequate - but it is very sincere.

David

---

### Post by pdc on 2013-05-18
thanks David; glad it is all working for you; I have greatly appreciated the expert input of steeldriver; very valuable;

till now I have used [COLOR="#0000FF"]ink[/COLOR] as CLI but ..having never heard of [COLOR="#FF8C00"]inq[/COLOR].... I also have now installed it!

it would seem the full list of packages needed would be

> [COLOR="#FF0000"]sudo apt-get install libxtst-dev build-essential libqt4-dev qt4-qmake libinklevel-dev[/COLOR]

......if anyone else searches this post and looks for what to do:

---

