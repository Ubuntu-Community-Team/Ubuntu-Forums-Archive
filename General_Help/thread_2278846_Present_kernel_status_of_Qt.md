---
title: "Present kernel status of Qt?"
date: 2015-05-19
forum: General Help
---

### Post by Kurt_Alan on 2015-05-19
My kernel:

Linux lucas-desktop** 3.16.0-38**-generic #52~14.04.1-Ubuntu SMP Fri May 8 09:43:57 UTC 2015 x86_64 x86_64 x86_64 GNU/Linux


I need Qt 5.3.  How do I query if my kernel utilizes Qt. + version?  Synaptic reveals about 50+ uninstalled Qt items but I don't understand what they are in relationship to Qt 5.3.

---

### Post by tgalati4 on 2015-05-19
Qt has a lot of parts.  Open a terminal:

> tgalati4@Mint17 ~ $ apt-cache search libqt5
libqt53d5 - Qt 3D module
libqt5clucene5 - Qt 5 CLucene module
libqt5concurrent5 - Qt 5 concurrent module
libqt5contacts5 - Qt PIM module, Contacts library
libqt5core5a - Qt 5 core module
libqt5dbus5 - Qt 5 D-Bus module
libqt5designer5 - Qt 5 designer module
libqt5designercomponents5 - Qt 5 Designer components module
libqt5feedback5 - Qt Feedback module
libqt5gui5 - Qt 5 GUI module
libqt5help5 - Qt 5 help module
libqt5location5 - Qt Location module
libqt5location5-plugins - Qt Location module - geolocation plugins
libqt5multimedia5 - Qt 5 Multimedia module
libqt5multimedia5-plugins - Qt 5 Multimedia module plugins
libqt5multimediaquick-p5 - Qt 5 Multimedia Quick module
libqt5multimediawidgets5 - Qt 5 Multimedia Widgets module
libqt5network5 - Qt 5 network module
libqt5opengl5 - Qt 5 OpenGL module
libqt5opengl5-dev - Qt 5 OpenGL library development files
libqt5organizer5 - Qt PIM module, Organizer library
libqt5positioning5 - Qt Positioning module
libqt5positioning5-plugins - Qt Positioning module - position plugins
libqt5printsupport5 - Qt 5 print support module
libqt5qml-graphicaleffects - Qt 5 Graphical Effects module
libqt5qml5 - Qt 5 QML module
libqt5quick5 - Qt 5 Quick library
libqt5quickparticles5 - Qt 5 Quick particules module
libqt5quicktest5 - Qt 5 Quick Test library
libqt5scintilla2-11 - Qt5 port of the Scintilla source code editing widget
libqt5scintilla2-dev - Scintilla source code editing widget for Qt5, development files
libqt5scintilla2-l10n - Scintilla source code editing widget for Qt5, translation files
libqt5script5 - Qt 5 script module
libqt5scripttools5 - Qt 5 script tools module
libqt5sensors5 - Qt Sensors module
libqt5sensors5-dev - Qt 5 Sensors development files
libqt5serialport5 - Qt 5 serial port support
libqt5serialport5-dev - Qt 5 serial port development files
libqt5sql5 - Qt 5 SQL module
libqt5sql5-sqlite - Qt 5 SQLite 3 database driver
libqt5svg5 - Qt 5 SVG module
libqt5svg5-dev - Qt 5 SVG module development files
libqt5svg5-private-dev - Qt 5 SVG module private development files
libqt5test5 - Qt 5 test module
libqt5versit5 - Qt PIM module, Versit library
libqt5versitorganizer5 - Qt PIM module, Versit Organizer library
libqt5webkit5 - Web content engine library for Qt
libqt5webkit5-dbg - Web content engine library for Qt - debugging symbols
libqt5webkit5-dev - Web content engine library for Qt - development files
libqt5webkit5-qmlwebkitplugin - Qt WebKit QML plugin
libqt5widgets5 - Qt 5 widgets module
libqt5x11extras5 - Qt 5 X11 extras
libqt5x11extras5-dev - Qt 5 X11 extras development files
libqt5xml5 - Qt 5 XML module
libqt5xmlpatterns5 - Qt 5 XML patterns module
libqt5xmlpatterns5-dev - Qt 5 XML patterns development files
libqt5xmlpatterns5-private-dev - Qt 5 XML patterns private development files
qtsensors5-dev - transitional dummy package
libqt5bluetooth5 - Qt Connectivity Bluetooth module
libqt5declarative5 - Qt Quick 1 module for Qt 5
libqt5multimedia5-touch - Qt 5 Multimedia module
libqt5multimedia5-touch-plugins - Qt 5 Multimedia module plugins
libqt5multimediaquick-p5-touch - Qt 5 Multimedia Quick module
libqt5nfc5 - Qt Connectivity NFC module
libqt5publishsubscribe5 - Qt Systems module - publish subscribe
libqt5qml-quickcontrols - transitional dummy package for Qt 5 Quick Controls module plugin
libqt5serviceframework5 - Qt Systems module - service framework
libqt5sql5-mysql - Qt 5 MySQL database driver
libqt5sql5-odbc - Qt 5 ODBC database driver
libqt5sql5-psql - Qt 5 PostgreSQL database driver
libqt5sql5-tds - Qt 5 FreeTDS database driver
libqt5systeminfo5 - Qt Systems module - system info
tgalati4@Mint17 ~ $ apt-cache policy libqt5core5a
libqt5core5a:
  Installed: 5.2.1+dfsg-1ubuntu14.2
  Candidate: 5.2.1+dfsg-1ubuntu14.2
  Version table:
 *** 5.2.1+dfsg-1ubuntu14.2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty-updates/main amd64 Packages
        100 /var/lib/dpkg/status
     5.2.1+dfsg-1ubuntu14 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) trusty/main amd64 Packages


You can have multiple versions and libraries installed, unless there is a dependency issue:

> 
tgalati4@Mint17 ~ $ apt-cache depends libqt5core5a
libqt5core5a
  Depends: libc6
  Depends: libgcc1
  Depends: libglib2.0-0
  Depends: libicu52
  Depends: libstdc++6
  Depends: zlib1g
  PreDepends: dpkg
    dpkg:i386
  PreDepends: multiarch-support
    multiarch-support:i386
  Suggests: libthai0
  Breaks: <libqt5core5>
  Breaks: <libqt5core5:i386>
  Replaces: <libqt5core5>
  Replaces: <libqt5core5:i386>
  Replaces: libqt5core5a:i386
  Breaks: libqt5core5a:i386


It looks like 5.2 is the stable version on 14.04.1.  Perhaps these instructions may work for 5.3:  [http://askubuntu.com/questions/279421/how-can-i-install-qt-5-x-on-12-04-lts](http://askubuntu.com/questions/279421/how-can-i-install-qt-5-x-on-12-04-lts)

---

