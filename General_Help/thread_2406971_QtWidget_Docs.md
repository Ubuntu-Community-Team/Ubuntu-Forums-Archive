---
title: "QtWidget Docs"
date: 2018-11-28
forum: General Help
---

### Post by gk3334 on 2018-11-28
I've installed Qt Creator 4.6.2 based on Qt 5.11.1.
QtCreator's docs do not show any docs for QtWidgets.
I have installed: qt5-doc, qt5-doc-html, qtdeclaritive5-doc, qtdeclaritive-doc-html, qtbase5-doc, qtbase5-doc-html.
I don't know what else to install to get the documentation.

---

### Post by dragonfly41 on 2018-11-28
Looking at Synaptic Package Manager I can see .. qtcreator-doc

---

### Post by spjackson on 2018-11-28
I'm on Ubuntu 18.04 so have lower versions than you, but qt5-doc is the right package and installs the docs for all of Qt in the format for assistant and QtCreator. The html docs are not used by QtCreator, as I understand it. You should have a lot of .qch files in /usr/share/qt5/doc/. What is listed in the Contents in QtCreator's help?

---

### Post by gk3334 on 2018-11-28
Here is the contents of /usr/share/qt5/doc/
```

global                  qtlocation             qtsensors.qch
qdoc                    qtlocation.qch         qtserialport
qdoc.qch                qtmultimedia           qtserialport.qch
qmake                   qtmultimedia.qch       qtsql
qmake.qch               qtnetwork              qtsql.qch
qt3d                    qtnetwork.qch          qtsvg
qt3d.qch                qtnfc                  qtsvg.qch
qtassistant             qtnfc.qch              qttestlib
qtassistant.qch         qtopengl               qttestlib.qch
qtbluetooth             qtopengl.qch           qtuitools
qtbluetooth.qch         qtplatformheaders      qtuitools.qch
qtcharts                qtplatformheaders.qch  qtvirtualkeyboard
qtcharts.qch            qtpositioning          qtvirtualkeyboard.qch
qtconcurrent            qtpositioning.qch      qtwaylandcompositor
qtconcurrent.qch        qtprintsupport         qtwaylandcompositor.qch
qtcore                  qtprintsupport.qch     qtwebchannel
qtcore.qch              qtqml                  qtwebchannel.qch
qtdbus                  qtqml.qch              qtwebengine
qtdbus.qch              qtqmltest              qtwebengine.qch
qtdesigner              qtqmltest.qch          qtwebkit
qtdesigner.qch          qtquick                qtwebkitexamples
qtdoc                   qtquickcontrols        qtwebkitexamples.qch
qtdoc.qch               qtquickcontrols2       qtwebkit.qch
qtgraphicaleffects      qtquickcontrols2.qch   qtwebsockets
qtgraphicaleffects.qch  qtquickcontrols.qch    qtwebsockets.qch
qtgui                   qtquickdialogs         qtwebview
qtgui.qch               qtquickdialogs.qch     qtwebview.qch
qthelp                  qtquickextras          qtwidgets
qthelp.qch              qtquickextras.qch      qtwidgets.qch
qtlabscalendar          qtquick.qch            qtx11extras
qtlabscalendar.qch      qtscript               qtx11extras.qch
qtlabsplatform          qtscript.qch           qtxml
qtlabsplatform.qch      qtscripttools          qtxmlpatterns
qtlinguist              qtscripttools.qch      qtxmlpatterns.qch
qtlinguist.qch          qtsensors              qtxml.qch



```

---

### Post by spjackson on 2018-11-29
On a fresh install of Ubuntu 18.10 I installed just qtcreator qt5-doc. None of the docs for Qt5 classes showed in QtCreator, just the help for QtCreator itself. However, I then installed qttools5-dev and then the help for the Qt5 classes appeared in QtCreator.

Presumably, when QtCreator does not know what version of Qt you are going to be using, it doesn't know which docs to show. This may provide a clue as to what is happening for you.

---

