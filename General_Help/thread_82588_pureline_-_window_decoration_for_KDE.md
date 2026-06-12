---
title: "pureline - window decoration for KDE"
date: 2005-10-26
forum: General Help
---

### Post by luna6 on 2005-10-26
was anybody successful in installing this ([http://www.kde-look.org/content/show.php?content=30501)?](http://www.kde-look.org/content/show.php?content=30501)?) I think I successfully compiled it but do not see an option for it in kcontrol or kubuntu's system setting.

---

### Post by ykpaiha on 2005-10-27
the exact name in kcontol is:
deckgen pureline

I found it there

---

### Post by Paulus on 2005-10-27
Did that sort it out for you...?
I had the exact same problem and I used:
```
./configure --prefix=`kde-config --prefix`

```
instead of just ./configure
then make && sudo make install
that solved it for me.

Did anyone get the taskbar link he provided to work properly?

---

### Post by luna6 on 2005-10-27
Hey..I did have to compile with ./configure --prefix=`kde-config --prefix` ....and worked fine. Thanks...

---

### Post by beefsprocket on 2005-10-27
Anyone get pureline to work with 3.5 beta2? I get some error about libkdecorations.la -- I take it compile works fine in 3.4.3?

---

### Post by Sankukai Monkey on 2005-10-28
OK...for a newbie like me what do I have to do to get this onto my Kubuntu install. I can see the .tar to download ?

What next after that please ? Anyone ? :D

---

### Post by luna6 on 2005-10-28
extract.... via console change dir into that extracted folder 
and do 3 steps....
1) ./configure --prefix=`kde-config --prefix`(usually can just do ./configure - but I had to add the extra prefix command so kde would load it)
2) make
3) sudo make install

then go into the control panel (system settings or kcontrol)...and your on your way...

p.s. - beefsprocket i compiled mine in kde3.5 beta 2 as well and did not get that error..i do recall having to install kdebase-dev to get it working...

---

### Post by beefsprocket on 2005-10-28
Edit: yeah,what luna6 said... and...

You want to have all the proper development files installed if you don't already. Keep running the ./configure command shown above and install the packages that it asks for. 

An alternative to sudo make install (if you want to uninstall later, not sure if the package supports make uninstall) is to run "make && checkinstall make install". This will create a .deb package that you can easily install/uninstall. You'll have to install the checkinstall package first.

luna6: I purged kdebase-dev and reinstalled -- seems to have worked -- not sure what corrupted it in the first place? Ah well. Thanks ;)

---

### Post by Sankukai Monkey on 2005-10-28
Sweeeeet ! :KS 
Nice one gents...heads off to thoroughly bu@@er up box :)

---

### Post by cwf on 2005-10-29
Hey guys,

Great post and it was instrumental and helping me to start trying to install this theme.

I finally got past the ./configure step...had to get a bunch of dev libs.

However, now when I run 'make' I get errors and I have no idea where to go from here.  Let me know if you can help.  

Here is the output of 'make':

```
make  all-recursive
make[1]: Entering directory `/home/siva/Desktop/pureline-1.1/pureline-0.1'
Making all in kwin
make[2]: Entering directory `/home/siva/Desktop/pureline-1.1/pureline-0.1/kwin'
make[3]: Entering directory `/home/siva/Desktop/pureline-1.1/pureline-0.1'
make[3]: Leaving directory `/home/siva/Desktop/pureline-1.1/pureline-0.1'
Making all in .
make[3]: Entering directory `/home/siva/Desktop/pureline-1.1/pureline-0.1/kwin'
make[4]: Entering directory `/home/siva/Desktop/pureline-1.1/pureline-0.1'
make[4]: Leaving directory `/home/siva/Desktop/pureline-1.1/pureline-0.1'
if /bin/sh ../libtool --silent --mode=compile g++ -DHAVE_CONFIG_H -I. -I. -I.. -I./../../lib -I/usr/include/kde -I/usr/share/qt3/include -I.   -DQT_THREAD_SUPPORT  -D_REENTRANT  -Wnon-virtual-dtor -Wno-long-long -Wundef -Wall -W -Wpointer-arith -Wwrite-strings -O2 -fno-exceptions -fno-check-new -fno-common -MT pureline.lo -MD -MP -MF ".deps/pureline.Tpo" -c -o pureline.lo pureline.cpp; \
then mv -f ".deps/pureline.Tpo" ".deps/pureline.Plo"; else rm -f ".deps/pureline.Tpo"; exit 1; fi
In file included from pureline.cpp:43:
pureline.h:49:25: error: kdecoration.h: No such file or directory
pureline.h:50:32: error: kdecorationfactory.h: No such file or directory
/usr/share/qt3/include/qtooltip.h:86: warning: 'class QToolTip' has virtual functions but non-virtual destructor
pureline.h:130: warning: non-local variable 'Pureline::<anonymous struct> Pureline::Settings_Param' uses anonymous type
pureline.h:143: error: expected class-name before '{' token
pureline.h:148: error: 'BorderSize' was not declared in this scope
pureline.h:148: error: template argument 1 is invalid
pureline.h:150: error: ISO C++ forbids declaration of 'KDecoration' with no type
pureline.h:150: error: 'KDecoration' declared as a 'virtual' field
pureline.h:150: error: expected ';' before '*' token
pureline.h:143: warning: 'class Pureline::PurelineHandler' has virtual functions but non-virtual destructor
pureline.h:307: error: expected class-name before '{' token
pureline.h:312: error: expected `)' before '*' token
pureline.h:326: error: 'Position' does not name a type
pureline.h:307: warning: 'class Pureline::PurelineClient' has virtual functions but non-virtual destructor
pureline.h: In member function 'int Pureline::PurelineClient::width() const':
pureline.h:358: error: 'widget' was not declared in this scope
pureline.h: In member function 'int Pureline::PurelineClient::height() const':
pureline.h:363: error: 'widget' was not declared in this scope
pureline.h: In member function 'bool Pureline::PurelineClient::maximizedVertical() const':
pureline.h:368: error: 'maximizeMode' was not declared in this scope
pureline.h:368: error: 'MaximizeVertical' was not declared in this scope
/usr/share/qt3/include/private/qucom_p.h: At global scope:
/usr/share/qt3/include/private/qucom_p.h:69: warning: 'struct QUBuffer' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:77: warning: 'struct QUType' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:104: warning: 'struct QUType_Null' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:287: warning: 'struct QUType_enum' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:307: warning: 'struct QUType_ptr' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:326: warning: 'struct QUType_iface' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:345: warning: 'struct QUType_idisp' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:364: warning: 'struct QUType_bool' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:383: warning: 'struct QUType_int' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:403: warning: 'struct QUType_double' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:423: warning: 'struct QUType_charstar' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucom_p.h:444: warning: 'struct QUType_QString' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:65: warning: 'struct QUType_QVariant' has virtual functions but non-virtual destructor
/usr/share/qt3/include/private/qucomextra_p.h:87: warning: 'struct QUType_varptr' has virtual functions but non-virtual destructor
pureline.moc: In static member function 'static QMetaObject* Pureline::PurelineClient::staticMetaObject()':
pureline.moc:54: error: 'KDecoration' has not been declared
pureline.moc: In member function 'virtual void* Pureline::PurelineClient::qt_cast(const char*)':
pureline.moc:78: error: 'KDecoration' has not been declared
pureline.moc: In member function 'virtual bool Pureline::PurelineClient::qt_invoke(int, QUObject*)':
pureline.moc:87: error: 'KDecoration' has not been declared
pureline.moc: In member function 'virtual bool Pureline::PurelineClient::qt_emit(int, QUObject*)':
pureline.moc:94: error: 'KDecoration' has not been declared
pureline.moc: In member function 'virtual bool Pureline::PurelineClient::qt_property(int, int, QVariant*)':
pureline.moc:100: error: 'KDecoration' has not been declared
pureline.cpp: In member function 'void Pureline::PurelineHandler::createPixmaps()':
pureline.cpp:101: error: 'options' was not declared in this scope
pureline.cpp:103: error: 'BorderLarge' was not declared in this scope
pureline.cpp:107: error: 'BorderVeryLarge' was not declared in this scope
pureline.cpp:111: error: 'BorderTiny' was not declared in this scope
pureline.cpp:112: error: 'BorderNormal' was not declared in this scope
pureline.cpp:118: error: 'options' was not declared in this scope
pureline.cpp:126: error: 'KDecoration' has not been declared
pureline.cpp:126: error: 'ColorTitleBar' was not declared in this scope
pureline.cpp:127: error: 'KDecoration' has not been declared
pureline.cpp:127: error: 'ColorTitleBlend' was not declared in this scope
pureline.cpp:157: error: 'KDecoration' has not been declared
pureline.cpp:158: error: 'KDecoration' has not been declared
pureline.cpp: In member function 'virtual bool Pureline::PurelineHandler::reset(long unsigned int)':
pureline.cpp:629: error: 'SettingBorder' was not declared in this scope
pureline.cpp:634: error: 'SettingFont' was not declared in this scope
pureline.cpp:640: error: 'SettingColors' was not declared in this scope
pureline.cpp:646: error: 'SettingButtons' was not declared in this scope
pureline.cpp:652: error: 'SettingTooltips' was not declared in this scope
pureline.cpp:673: error: 'resetDecorations' was not declared in this scope
pureline.cpp: At global scope:
pureline.cpp:748: error: expected constructor, destructor, or type conversion before '*' token
pureline.cpp:753: error: 'BorderSize' is not a member of 'Pureline::PurelineHandler'
pureline.cpp:753: error: 'BorderSize' is not a member of 'Pureline::PurelineHandler'
pureline.cpp:753: error: template argument 1 is invalid
pureline.cpp: In member function 'virtual int Pureline::PurelineHandler::borderSizes() const':
pureline.cpp:755: error: 'BorderSize' was not declared in this scope
pureline.cpp:755: error: template argument 1 is invalid
pureline.cpp:755: error: 'BorderNormal' was not declared in this scope
pureline.cpp:755: error: 'BorderLarge' was not declared in this scope
pureline.cpp:756: error: 'BorderVeryLarge' was not declared in this scope
pureline.cpp: In constructor 'Pureline::PurelineButton::PurelineButton(Pureline::PurelineClient*, const char*, Pureline::Button, const QString&, bool, int)':
pureline.cpp:760: error: 'class Pureline::PurelineClient' has no member named 'widget'
pureline.cpp:773: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp:774: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp: At global scope:
pureline.cpp:759: warning: unused parameter 'bttstate'
pureline.cpp:759: warning: unused parameter 'bttstate'
pureline.cpp: In member function 'virtual void Pureline::PurelineButton::drawButton(QPainter*)':
pureline.cpp:825: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp:825: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp:874: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp:878: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp:882: error: 'class Pureline::PurelineClient' has no member named 'maximizeMode'
pureline.cpp:882: error: 'MaximizeFull' is not a member of 'Pureline::PurelineClient'
pureline.cpp:882: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp:886: error: 'class Pureline::PurelineClient' has no member named 'isActive'
pureline.cpp: At global scope:
pureline.cpp:1018: error: expected `)' before '*' token
pureline.cpp: In member function 'virtual void Pureline::PurelineClient::init()':
pureline.cpp:1038: error: 'WStaticContents' was not declared in this scope
pureline.cpp:1038: error: 'WNoAutoErase' was not declared in this scope
pureline.cpp:1038: error: 'createMainWidget' was not declared in this scope
pureline.cpp:1039: error: 'widget' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::createLayout()':
pureline.cpp:1067: error: 'widget' was not declared in this scope
pureline.cpp:1082: error: 'isActive' was not declared in this scope
pureline.cpp:1112: error: 'options' was not declared in this scope
pureline.cpp:1152: error: 'isPreview' was not declared in this scope
pureline.cpp: In member function 'virtual void Pureline::PurelineClient::reset(long unsigned int)':
pureline.cpp:1175: error: 'widget' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::addButtons(QBoxLayout*, const QString&)':
pureline.cpp:1218: error: 'LeftButton' was not declared in this scope
pureline.cpp:1218: error: 'MidButton' was not declared in this scope
pureline.cpp:1218: error: 'RightButton' was not declared in this scope
pureline.cpp:1226: error: 'isMinimizable' was not declared in this scope
pureline.cpp:1229: error: 'connect' was not declared in this scope
pureline.cpp:1243: error: 'isMaximizable' was not declared in this scope
pureline.cpp:1246: error: 'connect' was not declared in this scope
pureline.cpp:1260: error: 'isCloseable' was not declared in this scope
pureline.cpp:1263: error: 'connect' was not declared in this scope
pureline.cpp:1281: error: 'providesContextHelp' was not declared in this scope
pureline.cpp:1284: error: 'connect' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::updateMask()':
pureline.cpp:1344: error: 'setMask' was not declared in this scope
pureline.cpp: In member function 'virtual void Pureline::PurelineClient::captionChange()':
pureline.cpp:1352: error: 'widget' was not declared in this scope
pureline.cpp:1352: error: 'isActive' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::iconChange()':
pureline.cpp:1374: error: 'widget' was not declared in this scope
pureline.cpp:1374: error: 'isActive' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::drawAppIcon(QPainter&)':
pureline.cpp:1386: error: 'isActive' was not declared in this scope
pureline.cpp:1389: error: 'class Pureline::PurelineClient' has no member named 'icon'
pureline.cpp:1389: error: incomplete type 'QIconSet' used in nested name specifier
pureline.cpp:1389: error: incomplete type 'QIconSet' used in nested name specifier
pureline.cpp:1396: error: 'class Pureline::PurelineClient' has no member named 'icon'
pureline.cpp:1396: error: incomplete type 'QIconSet' used in nested name specifier
pureline.cpp:1396: error: incomplete type 'QIconSet' used in nested name specifier
pureline.cpp:1425: error: 'isActive' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::drawCaptionText(QPainter&)':
pureline.cpp:1437: error: 'class Pureline::PurelineHandler' has no member named 'options'
pureline.cpp:1437: error: 'isActive' was not declared in this scope
pureline.cpp:1442: error: 'AlignLeft' was not declared in this scope
pureline.cpp:1442: error: 'AlignVCenter' was not declared in this scope
pureline.cpp:1442: error: 'SingleLine' was not declared in this scope
pureline.cpp:1445: error: 'AlignCenter' was not declared in this scope
pureline.cpp:1448: error: 'AlignRight' was not declared in this scope
pureline.cpp:1474: error: 'caption' was not declared in this scope
pureline.cpp:1491: error: 'options' was not declared in this scope
pureline.cpp:1491: error: 'ColorFont' was not declared in this scope
pureline.cpp:1496: error: 'caption' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::drawTitlebar(QPainter&, QRect&)':
pureline.cpp:1509: error: 'isActive' was not declared in this scope
pureline.cpp:1527: error: 'isActive' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::drawFrame(QPainter&, QRect&, QPaintEvent*)':
pureline.cpp:1553: error: 'isActive' was not declared in this scope
pureline.cpp: In member function 'int Pureline::PurelineClient::BttWidthOnLeft()':
pureline.cpp:1626: error: 'options' was not declared in this scope
pureline.cpp:1650: error: 'isMinimizable' was not declared in this scope
pureline.cpp:1651: error: 'isActive' was not declared in this scope
pureline.cpp:1652: error: 'isMaximizable' was not declared in this scope
pureline.cpp:1653: error: 'isActive' was not declared in this scope
pureline.cpp:1654: error: 'isCloseable' was not declared in this scope
pureline.cpp:1655: error: 'isActive' was not declared in this scope
pureline.cpp:1656: error: 'providesContextHelp' was not declared in this scope
pureline.cpp:1657: error: 'isActive' was not declared in this scope
pureline.cpp:1673: error: 'isActive' was not declared in this scope
pureline.cpp: In member function 'int Pureline::PurelineClient::BttWidthOnRight()':
pureline.cpp:1682: error: 'options' was not declared in this scope
pureline.cpp:1706: error: 'isMinimizable' was not declared in this scope
pureline.cpp:1707: error: 'isActive' was not declared in this scope
pureline.cpp:1708: error: 'isMaximizable' was not declared in this scope
pureline.cpp:1709: error: 'isActive' was not declared in this scope
pureline.cpp:1710: error: 'isCloseable' was not declared in this scope
pureline.cpp:1711: error: 'isActive' was not declared in this scope
pureline.cpp:1712: error: 'providesContextHelp' was not declared in this scope
pureline.cpp:1713: error: 'isActive' was not declared in this scope
pureline.cpp:1735: error: 'isActive' was not declared in this scope
pureline.cpp: In member function 'virtual void Pureline::PurelineClient::activeChange()':
pureline.cpp:1748: error: 'widget' was not declared in this scope
pureline.cpp: In member function 'virtual void Pureline::PurelineClient::maximizeChange()':
pureline.cpp:1768: error: 'maximizeMode' was not declared in this scope
pureline.cpp:1768: error: 'MaximizeFull' was not declared in this scope
pureline.cpp:1771: error: 'widget' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::slotMaximize()':
pureline.cpp:1811: error: 'MidButton' was not declared in this scope
pureline.cpp:1812: error: 'maximizeMode' was not declared in this scope
pureline.cpp:1812: error: 'MaximizeVertical' was not declared in this scope
pureline.cpp:1812: error: 'maximize' was not declared in this scope
pureline.cpp:1815: error: 'RightButton' was not declared in this scope
pureline.cpp:1816: error: 'MaximizeHorizontal' was not declared in this scope
pureline.cpp:1819: error: 'LeftButton' was not declared in this scope
pureline.cpp:1820: error: 'MaximizeFull' was not declared in this scope
pureline.cpp:1820: error: 'MaximizeRestore' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::paintEvent(QPaintEvent*)':
pureline.cpp:1863: error: 'widget' was not declared in this scope
pureline.cpp: In member function 'void Pureline::PurelineClient::resizeEvent(QResizeEvent*)':
pureline.cpp:1882: error: 'widget' was not declared in this scope
pureline.cpp:1908: error: no matching function for call to 'QApplication::postEvent(Pureline::PurelineClient* const, QPaintEvent*)'
/usr/share/qt3/include/qapplication.h:151: note: candidates are: static void QApplication::postEvent(QObject*, QEvent*)
pureline.cpp: In member function 'void Pureline::PurelineClient::mouseDoubleClickEvent(QMouseEvent*)':
pureline.cpp:1917: error: 'titlebarDblClickOperation' was not declared in this scope
pureline.cpp: At global scope:
pureline.cpp:1921: error: 'Position' in class 'Pureline::PurelineClient' does not name a type
pureline.cpp: In member function 'virtual void Pureline::PurelineClient::resize(const QSize&)':
pureline.cpp:2005: error: 'widget' was not declared in this scope
pureline.cpp: In member function 'virtual void Pureline::PurelineClient::borders(int&, int&, int&, int&) const':
pureline.cpp:2013: error: 'isActive' was not declared in this scope
pureline.cpp:2021: error: 'maximizeMode' was not declared in this scope
pureline.cpp:2021: error: 'MaximizeHorizontal' was not declared in this scope
pureline.cpp:2021: error: 'options' was not declared in this scope
pureline.cpp:2023: error: 'maximizeMode' was not declared in this scope
pureline.cpp:2023: error: 'MaximizeVertical' was not declared in this scope
pureline.cpp:2026: error: 'options' was not declared in this scope
pureline.cpp: In member function 'virtual QSize Pureline::PurelineClient::minimumSize() const':
pureline.cpp:2034: error: 'widget' was not declared in this scope
pureline.cpp: In member function 'virtual bool Pureline::PurelineClient::eventFilter(QObject*, QEvent*)':
pureline.cpp:2040: error: 'widget' was not declared in this scope
pureline.cpp:2058: error: 'processMousePressEvent' was not declared in this scope
pureline.cpp: At global scope:
pureline.cpp:2071: error: expected constructor, destructor, or type conversion before '*' token
make[3]: *** [pureline.lo] Error 1
make[3]: Leaving directory `/home/siva/Desktop/pureline-1.1/pureline-0.1/kwin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/siva/Desktop/pureline-1.1/pureline-0.1/kwin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/siva/Desktop/pureline-1.1/pureline-0.1'
make: *** [all] Error 2
```

Many thanks!

---

### Post by beefsprocket on 2005-10-29
As luna6 said, you need the kdebase-dev package installed for the kdecoration.h and kdecorationfactory.h. If you look at the error mesage you'll see that those two files are the first two errors and most (if not all?) subsequent errors derive from not having those two files.

---

### Post by cwf on 2005-10-29
[QUOTE=beefsprocket]As luna6 said, you need the kdebase-dev package installed for the kdecoration.h and kdecorationfactory.h. If you look at the error mesage you'll see that those two files are the first two errors and most (if not all?) subsequent errors derive from not having those two files.[/QUOTE]
 
Thanks beef....that worked.

Since I started from scratch to build this...here's a list of all packages you'll need to build this (ones you wouldn't have after doing a default Kubuntu install).

kdebase-dev
g++
build-essential
gawk
x-window-system-dev
libqt3-mt-dev
kdelibs-dev

I'm pretty sure that's all I had to install to get this working.  Someone correct me if I'm wrong...its hard to remember what all I did...I should've written it down while doing it!

---

### Post by beefsprocket on 2005-10-29
So you should try polymer as your style now :cool:

---

### Post by cwf on 2005-10-29
[QUOTE=beefsprocket]So you should try polymer as your style now :cool:[/QUOTE]

Done!  That was easy...and it looks sweet!

Note:  I had to use ./configure --prefix=`kde-config --prefix`

---

### Post by elgx on 2005-10-30
if you want, I did a mod of the Pureline color scheme. It is at kde-look, check it out!
[http://www.kde-look.org/content/show.php?content=30757](http://www.kde-look.org/content/show.php?content=30757)
my favourite style to go with it is Polymer, too.

(sorry, i'm not such an english-speaker!)

bye bye
Elena

---

