---
title: "ImportError: No module named QtWebKit"
date: 2014-11-19
forum: General Help
---

### Post by monkeybrain20122 on 2014-11-19
Hi, I am trying to test run spyder IDE 2.3.1 without installing 
[https://code.google.com/p/spyderlib/](https://code.google.com/p/spyderlib/)
Following the instruction I extracted the source zip file, cd into it and ran 
```
python bootstrap.py
```

and got the error in the title

```
File "/home/monkeybrain/spyder-2.3.1/spyderlib/qt/QtWebKit.py", line 10, in <module>
    from PyQt4.QtWebKit import *  # analysis:ignore
ImportError: No module named QtWebKit
```


I found /usr/lib/python2.7/dist-packages/PySide/QtWebKit.so installed from the package python-pyside-qtwebkit

Same result in both Trusty and Utopic

Meanwhile there is a package called python3-pyqt5.qtwebqit in Trusty and an additional one called python-pyqt5.qtwebkit, but the output suggests that it is looking for pyqt4.qtwebkt. 

Pleaas advise, thanks.

---

### Post by mc4man on 2014-11-20
works here though tried just a plain ./bootstrap first. So you may be missing a lib package, if so shouldn't be that hard to track down
Ex.'s

> ~/Downloads/spyder-2.3.1$ ./bootstrap.py
Executing Spyder from source checkout
Revision None:None, Branch: None
01. Patched sys.path with /home/doug/Downloads/spyder-2.3.1
02. No PySide detected, using PyQt4 if available
03. Imported Spyder 2.3.1
    [Python 2.7.6 64bits, Qt 4.8.6, PyQt4 (API v1) 4.10.4 on Linux]
04. Executing spyder.main()
Bootstrap completed in 00:00:00.3309

doug@doug-Lenovo-IdeaPad-Y510P:~/Downloads/spyder-2.3.1$ python ./bootstrap.py
Executing Spyder from source checkout
Revision None:None, Branch: None
01. Patched sys.path with /home/doug/Downloads/spyder-2.3.1
02. No PySide detected, using PyQt4 if available
03. Imported Spyder 2.3.1
    [Python 2.7.6 64bits, Qt 4.8.6, PyQt4 (API v1) 4.10.4 on Linux]
04. Executing spyder.main()
Bootstrap completed in 00:00:00.0876

Edit: is the absense of PySide an issue??

---

### Post by monkeybrain20122 on 2014-11-20
Hi, I was trying ./bootstrap but got the error 
```
File "/home/monkeybrain/spyder-2.3.1/spyderlib/qt/QtWebKit.py", line 10, in <module>
    from PyQt4.QtWebKit import *  # analysis:ignore
ImportError: No module named QtWebKit
```

python-pyside.qtwebkit was installed already. What other package may provide qtwebkit?

---

### Post by dragonfly41 on 2014-11-20
Recently I've been playing with Qt for python .. 

e.g. the package cutycapt required QtWebKit.

Looking through Synaptic Package Manager list I see these installed ...

libqt4-dev
libqt4-webkit
libqt4-dev
libqt5webkit5
libqt5webkit5-dev

You might only be interested in Qt4.

---

### Post by monkeybrain20122 on 2014-11-20
Those qt4 packages are all installed, there is a package called python3-qt5.webkit, but there is no python2 + qt4 version. According to some old posts on the internet it seems to require python-qt4.webkit but there is no such thing in the repo.

The full log for running bootstrap
```
$ python bootstrap.py
Executing Spyder from source checkout
Revision None:None, Branch: None
01. Patched sys.path with /home/monkeybrain/Downloads/spyder-2.3.1
02. No PySide detected, using PyQt4 if available
03. Imported Spyder 2.3.1
    [Python 2.7.3 64bits, Qt 4.8.4, PyQt4 (API v2) 4.10 on Linux]
04. Executing spyder.main()
Bootstrap completed in 00:00:02.0318
Traceback (most recent call last):
  File "/home/monkeybrain/Downloads/spyder-2.3.1/spyderlib/spyder.py", line 2346, in main
    mainwindow = run_spyder(app, options, args)
  File "/home/monkeybrain/Downloads/spyder-2.3.1/spyderlib/spyder.py", line 2234, in run_spyder
    main.setup()
  File "/home/monkeybrain/Downloads/spyder-2.3.1/spyderlib/spyder.py", line 773, in setup
    message=_("Spyder Internal Console\n\n"
  File "/home/monkeybrain/Downloads/spyder-2.3.1/spyderlib/plugins/console.py", line 74, in __init__
    self.find_widget.set_editor(self.shell)
  File "/home/monkeybrain/Downloads/spyder-2.3.1/spyderlib/widgets/findreplace.py", line 261, in set_editor
    from spyderlib.qt.QtWebKit import QWebView
  File "/home/monkeybrain/Downloads/spyder-2.3.1/spyderlib/qt/QtWebKit.py", line 10, in <module>
    from PyQt4.QtWebKit import *  # analysis:ignore
ImportError: No module named QtWebKit
```

---

### Post by dragonfly41 on 2014-11-20
Other packages found in my setup .. I have Qt4 and Qt5 installed.

qt4-dev-tools
qt4-qtconfig


I've used **sudo locate QtWebKit** and it is scattered throughout .. e.g. some samples ..

/opt/Qt/5.3/gcc/imports/QtWebKit
/opt/Qt/5.3/gcc/include/QtWebKitWidgets
/opt/Qt/5.3/gcc/qml/QtWebKit
/opt/Qt/Tools/QtCreator/bin/qml/QtWebKit
/usr/include/qt4/QtWebkit
/usr/include/qt5/QtWebKit

/usr/lib/i386-linux-gnu/libQtWebKit.prl
/usr/lib/i386-linux-gnu/libQtWebKit.so
/usr/lib/i386-linux-gnu/libQtWebKit.so.4
/usr/lib/i386-linux-gnu/libQtWebKit.so.4.10
/usr/lib/i386-linux-gnu/libQtWebKit.so.4.10.2

/usr/lib/python2.7/dist-packages/PyQt4/QtWebKit.so

...

I've just installed Spyder from Ubuntu Software Centre .. no problems so far.

---

### Post by dragonfly41 on 2014-11-20
Also try ...

libqtwebkit-dev
libqtwebkit4

---

### Post by monkeybrain20122 on 2014-11-20
These is my output
 ```
$locate QtWebKit
/home/monkeybrain/MATLAB/R2014a/bin/glnxa64/libQtWebKit.so.4
/home/monkeybrain/MATLAB/R2014a/bin/glnxa64/libQtWebKit.so.4.9
/home/monkeybrain/MATLAB/R2014a/bin/glnxa64/libQtWebKit.so.4.9.3
/opt/calibre/lib/python2.7/site-packages/PyQt5/QtWebKit.so
/opt/calibre/lib/python2.7/site-packages/PyQt5/QtWebKitWidgets.so
/opt/google/earth/free/libQtWebKit.so.4
/usr/include/qt4/QtWebKit
/usr/include/qt4/QtWebKit/QGraphicsWebView
/usr/include/qt4/QtWebKit/QWebDatabase
/usr/include/qt4/QtWebKit/QWebElement
/usr/include/qt4/QtWebKit/QWebElementCollection
/usr/include/qt4/QtWebKit/QWebFrame
/usr/include/qt4/QtWebKit/QWebFullScreenVideoHandler
/usr/include/qt4/QtWebKit/QWebHapticFeedbackPlayer
/usr/include/qt4/QtWebKit/QWebHistory
/usr/include/qt4/QtWebKit/QWebHistoryInterface
/usr/include/qt4/QtWebKit/QWebHistoryItem
/usr/include/qt4/QtWebKit/QWebHitTestResult
/usr/include/qt4/QtWebKit/QWebInspector
/usr/include/qt4/QtWebKit/QWebKitPlatformPlugin
/usr/include/qt4/QtWebKit/QWebNotificationData
/usr/include/qt4/QtWebKit/QWebNotificationPresenter
/usr/include/qt4/QtWebKit/QWebPage
/usr/include/qt4/QtWebKit/QWebPluginFactory
/usr/include/qt4/QtWebKit/QWebScriptWorld
/usr/include/qt4/QtWebKit/QWebSecurityOrigin
/usr/include/qt4/QtWebKit/QWebSelectData
/usr/include/qt4/QtWebKit/QWebSelectMethod
/usr/include/qt4/QtWebKit/QWebSettings
/usr/include/qt4/QtWebKit/QWebSpellChecker
/usr/include/qt4/QtWebKit/QWebTouchModifier
/usr/include/qt4/QtWebKit/QWebView
/usr/include/qt4/QtWebKit/QtWebKit
/usr/include/qt4/QtWebKit/qgraphicswebview.h
/usr/include/qt4/QtWebKit/qwebdatabase.h
/usr/include/qt4/QtWebKit/qwebelement.h
/usr/include/qt4/QtWebKit/qwebframe.h
/usr/include/qt4/QtWebKit/qwebhistory.h
/usr/include/qt4/QtWebKit/qwebhistoryinterface.h
/usr/include/qt4/QtWebKit/qwebinspector.h
/usr/include/qt4/QtWebKit/qwebkitglobal.h
/usr/include/qt4/QtWebKit/qwebkitplatformplugin.h
/usr/include/qt4/QtWebKit/qwebkitversion.h
/usr/include/qt4/QtWebKit/qwebpage.h
/usr/include/qt4/QtWebKit/qwebpluginfactory.h
/usr/include/qt4/QtWebKit/qwebscriptworld.h
/usr/include/qt4/QtWebKit/qwebsecurityorigin.h
/usr/include/qt4/QtWebKit/qwebsettings.h
/usr/include/qt4/QtWebKit/qwebview.h
/usr/lib/i386-linux-gnu/libQtWebKit.so.4
/usr/lib/i386-linux-gnu/libQtWebKit.so.4.10
/usr/lib/i386-linux-gnu/libQtWebKit.so.4.10.2
/usr/lib/python2.7/dist-packages/PyQt4/QtWebKit.so
/usr/lib/python2.7/dist-packages/PySide/QtWebKit.so
/usr/lib/python2.7/dist-packages/spyderlib/qt/QtWebKit.py
/usr/lib/python2.7/dist-packages/spyderlib/qt/QtWebKit.pyc
/usr/lib/rstudio/bin/libQtWebKit.so.4
/usr/lib/rstudio/bin/libQtWebKit.so.4.9.0
/usr/lib/x86_64-linux-gnu/libQtWebKit.prl
/usr/lib/x86_64-linux-gnu/libQtWebKit.so
/usr/lib/x86_64-linux-gnu/libQtWebKit.so.4
/usr/lib/x86_64-linux-gnu/libQtWebKit.so.4.10
/usr/lib/x86_64-linux-gnu/libQtWebKit.so.4.10.2
/usr/lib/x86_64-linux-gnu/pkgconfig/QtWebKit.pc
/usr/lib/x86_64-linux-gnu/qt5/imports/QtWebKit
/usr/lib/x86_64-linux-gnu/qt5/imports/QtWebKit/libqmlwebkitplugin.so
/usr/lib/x86_64-linux-gnu/qt5/imports/QtWebKit/plugins.qmltypes
/usr/lib/x86_64-linux-gnu/qt5/imports/QtWebKit/qmldir
/usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit
/usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/experimental
/usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/libqmlwebkitplugin.so
/usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/qmldir
/usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/experimental/libqmlwebkitexperimentalplugin.so
/usr/lib/x86_64-linux-gnu/qt5/qml/QtWebKit/experimental/qmldir
/usr/share/sip/PyQt4/QtWebKit
/usr/share/sip/PyQt4/QtWebKit/QtWebKitmod.sip
/usr/share/sip/PyQt4/QtWebKit/qgraphicswebview.sip
/usr/share/sip/PyQt4/QtWebKit/qwebdatabase.sip
/usr/share/sip/PyQt4/QtWebKit/qwebelement.sip
/usr/share/sip/PyQt4/QtWebKit/qwebframe.sip
/usr/share/sip/PyQt4/QtWebKit/qwebhistory.sip
/usr/share/sip/PyQt4/QtWebKit/qwebhistoryinterface.sip
/usr/share/sip/PyQt4/QtWebKit/qwebinspector.sip
/usr/share/sip/PyQt4/QtWebKit/qwebkitglobal.sip
/usr/share/sip/PyQt4/QtWebKit/qwebkitversion.sip
/usr/share/sip/PyQt4/QtWebKit/qwebpage.sip
/usr/share/sip/PyQt4/QtWebKit/qwebpluginfactory.sip
/usr/share/sip/PyQt4/QtWebKit/qwebsecurityorigin.sip
/usr/share/sip/PyQt4/QtWebKit/qwebsettings.sip
/usr/share/sip/PyQt4/QtWebKit/qwebview.sip
```

---

### Post by dragonfly41 on 2014-11-22
Sorry this topic dropped off my radar screen.  I'm no expert in Python since I'm learning as I go.  And you might get better response from Programming thread.

However some more ideas.

First in command terminal run python

I get this ...

:~$ python
Python 2.7.6 (default, Mar 22 2014, 22:59:38) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

then ...
>>> import PyQt4
>>> print PyQt4.__path__
['/usr/lib/python2.7/dist-packages/PyQt4']

...

Look in path to see if you have QtWebKit.so (I do).

...

Note that (out of curiosity) I have installed spyder from Ubuntu Software Centre and various other Python goodies but I can't remember what I used to install QtWebKit for my own Qt experiments.

I do have Qt4 Designer and Qt Creator installed. Perhaps from there. 
        
...

See also this spyder issue reported which appears relevant.    

[https://code.google.com/p/spyderlib/issues/detail?id=1602](https://code.google.com/p/spyderlib/issues/detail?id=1602)

---

### Post by mc4man on 2014-11-22
What release of Ubuntu are you using?
(only asking because it works fine here in 14.04 using  - 
03. Imported Spyder 2.3.1
    [Python 2.7.[COLOR="#FF0000"]6[/COLOR] 64bits, Qt 4.8.[COLOR="#FF0000"]6[/COLOR]
you show - 
Python 2.7.3 64bits, Qt 4.8.4

---

### Post by monkeybrain20122 on 2014-11-22
> **mc4man said:**
> What release of Ubuntu are you using?
(only asking because it works fine here in 14.04 using  - 
03. Imported Spyder 2.3.1
    [Python 2.7.[COLOR=#FF0000]6[/COLOR] 64bits, Qt 4.8.[COLOR=#FF0000]6[/COLOR]
you show - 
Python 2.7.3 64bits, Qt 4.8.4

Same I am using Ubuntu 14.04 64 bit.

Checked synaptic, I have both python 2.7.5-5ubuntu3 and python 2.7.6-8. The first one is just named python, the second python 2.7 Both from standard repo

Not sure which Qt package to check, but my qt4-devtools is listed as 4.8.5

---

### Post by monkeybrain20122 on 2014-11-22
> **dragonfly41 said:**
> Sorry this topic dropped off my radar screen.  I'm no expert in Python since I'm learning as I go.  And you might get better response from Programming thread.

However some more ideas.

First in command terminal run python

I get this ...

:~$ python
Python 2.7.6 (default, Mar 22 2014, 22:59:38) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>>

then ...
>>> import PyQt4
>>> print PyQt4.__path__
['/usr/lib/python2.7/dist-packages/PyQt4']

...

Look in path to see if you have QtWebKit.so (I do).

...

Note that (out of curiosity) I have installed spyder from Ubuntu Software Centre and various other Python goodies but I can't remember what I used to install QtWebKit for my own Qt experiments.

I do have Qt4 Designer and Qt Creator installed. Perhaps from there. 
        
...

See also this spyder issue reported which appears relevant.    

[https://code.google.com/p/spyderlib/issues/detail?id=1602](https://code.google.com/p/spyderlib/issues/detail?id=1602)
```

>>> print PyQt4.__path__
['/home/monkeybrain/EMAN2/extlib/lib/python2.7/site-packages/PyQt4']
>>> 
```

Hmm.. I see. I  installed EMAN2 just to answer some guy's thread on this forum. Looks like somehow its python was taken to be default. I will try to uninstall it and check again.

Thanks.

---

### Post by monkeybrain20122 on 2014-11-22
OK, turns out EMAN2 puts a line in my .bashrc to default to its version of python, I removed it and now I have
```
~$ python
Python 2.7.6 (default, Mar 22 2014, 22:59:56) 
[GCC 4.8.2] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import PyQt4
>>> print PyQt4.__path__
['/usr/lib/python2.7/dist-packages/PyQt4']
```

Ran bootstrap again  for spyder, it works now.

Thanks everyone  for the help, dragonfly41's two commands are most helpful :)

I am marking this as solved.

---

