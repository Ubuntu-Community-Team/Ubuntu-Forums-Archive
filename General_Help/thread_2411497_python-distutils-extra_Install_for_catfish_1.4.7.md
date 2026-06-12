---
title: "python-distutils-extra Install for catfish 1.4.7"
date: 2019-01-31
forum: General Help
---

### Post by Redalien0304 on 2019-01-31
Installed python-distutils-extra from Synaptic package Manager
got all this

```
craig@craig-Latitude-E6500:~/Downloads/catfish-1.4.7$ sudo python setup.py install
[sudo] password for craig: 
To build catfish you need [https://launchpad.net/python-distutils-extra](https://launchpad.net/python-distutils-extra)
craig@craig-Latitude-E6500:~/Downloads/catfish-1.4.7$ sudo python setup.py install
ERROR: Python module helpers not found
ERROR: Python module catfishconfig not found
ERROR: Python module helpers not found
ERROR: Python module catfishconfig not found
ERROR: Python module gi not found
ERROR: Python module zeitgeist.client not found
ERROR: Python module zeitgeist.datamodel not found
ERROR: Python module zeitgeist not found
ERROR: Python module gi not found
ERROR: Python module catfishconfig not found
ERROR: Python module Builder not found
ERROR: Python module pexpect not found
ERROR: Python module gi not found
ERROR: Python module pexpect not found
ERROR: Python module helpers not found
ERROR: Python module Window not found
ERROR: Python module catfishconfig not found
running install
intltool-merge -d po --xml-style data/metainfo/catfish.appdata.xml.in data/metainfo/catfish.appdata.xml
Merging translations into data/metainfo/catfish.appdata.xml.
CREATED data/metainfo/catfish.appdata.xml
running build
running build_py
creating build
creating build/lib.linux-x86_64-2.7
creating build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/Window.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/catfishconfig.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/__init__.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/SudoDialog.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/helpers.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/Thumbnailer.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/CatfishSettings.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/AboutDialog.py -> build/lib.linux-x86_64-2.7/catfish_lib
copying catfish_lib/Builder.py -> build/lib.linux-x86_64-2.7/catfish_lib
creating build/lib.linux-x86_64-2.7/catfish
copying catfish/CatfishSearchEngine.py -> build/lib.linux-x86_64-2.7/catfish
copying catfish/__init__.py -> build/lib.linux-x86_64-2.7/catfish
copying catfish/AboutCatfishDialog.py -> build/lib.linux-x86_64-2.7/catfish
copying catfish/CatfishWindow.py -> build/lib.linux-x86_64-2.7/catfish
running build_scripts
creating build/scripts-2.7
copying and adjusting bin/catfish -> build/scripts-2.7
changing mode of build/scripts-2.7/catfish from 644 to 755
running build_i18n
intltool-update -p -g catfish
msgfmt po/th.po -o build/mo/th/LC_MESSAGES/catfish.mo
msgfmt po/ca.po -o build/mo/ca/LC_MESSAGES/catfish.mo
msgfmt po/si.po -o build/mo/si/LC_MESSAGES/catfish.mo
msgfmt po/ml.po -o build/mo/ml/LC_MESSAGES/catfish.mo
msgfmt po/ko.po -o build/mo/ko/LC_MESSAGES/catfish.mo
msgfmt po/sr.po -o build/mo/sr/LC_MESSAGES/catfish.mo
msgfmt po/af.po -o build/mo/af/LC_MESSAGES/catfish.mo
msgfmt po/nn.po -o build/mo/nn/LC_MESSAGES/catfish.mo
msgfmt po/hu.po -o build/mo/hu/LC_MESSAGES/catfish.mo
msgfmt po/ms.po -o build/mo/ms/LC_MESSAGES/catfish.mo
msgfmt po/uk.po -o build/mo/uk/LC_MESSAGES/catfish.mo
msgfmt po/sv.po -o build/mo/sv/LC_MESSAGES/catfish.mo
msgfmt po/pt_BR.po -o build/mo/pt_BR/LC_MESSAGES/catfish.mo
msgfmt po/ku.po -o build/mo/ku/LC_MESSAGES/catfish.mo
msgfmt po/cs.po -o build/mo/cs/LC_MESSAGES/catfish.mo
msgfmt po/nl.po -o build/mo/nl/LC_MESSAGES/catfish.mo
msgfmt po/he.po -o build/mo/he/LC_MESSAGES/catfish.mo
msgfmt po/be.po -o build/mo/be/LC_MESSAGES/catfish.mo
msgfmt po/id.po -o build/mo/id/LC_MESSAGES/catfish.mo
msgfmt po/fi.po -o build/mo/fi/LC_MESSAGES/catfish.mo
msgfmt po/fr.po -o build/mo/fr/LC_MESSAGES/catfish.mo
msgfmt po/bg.po -o build/mo/bg/LC_MESSAGES/catfish.mo
msgfmt po/pt.po -o build/mo/pt/LC_MESSAGES/catfish.mo
msgfmt po/it.po -o build/mo/it/LC_MESSAGES/catfish.mo
msgfmt po/el.po -o build/mo/el/LC_MESSAGES/catfish.mo
msgfmt po/tr.po -o build/mo/tr/LC_MESSAGES/catfish.mo
msgfmt po/ja.po -o build/mo/ja/LC_MESSAGES/catfish.mo
msgfmt po/ar.po -o build/mo/ar/LC_MESSAGES/catfish.mo
msgfmt po/eu.po -o build/mo/eu/LC_MESSAGES/catfish.mo
msgfmt po/en_AU.po -o build/mo/en_AU/LC_MESSAGES/catfish.mo
msgfmt po/ru.po -o build/mo/ru/LC_MESSAGES/catfish.mo
msgfmt po/sq.po -o build/mo/sq/LC_MESSAGES/catfish.mo
msgfmt po/zh_TW.po -o build/mo/zh_TW/LC_MESSAGES/catfish.mo
msgfmt po/nb.po -o build/mo/nb/LC_MESSAGES/catfish.mo
msgfmt po/zh_CN.po -o build/mo/zh_CN/LC_MESSAGES/catfish.mo
msgfmt po/de.po -o build/mo/de/LC_MESSAGES/catfish.mo
msgfmt po/sk.po -o build/mo/sk/LC_MESSAGES/catfish.mo
msgfmt po/is.po -o build/mo/is/LC_MESSAGES/catfish.mo
msgfmt po/lt.po -o build/mo/lt/LC_MESSAGES/catfish.mo
msgfmt po/gl.po -o build/mo/gl/LC_MESSAGES/catfish.mo
msgfmt po/pl.po -o build/mo/pl/LC_MESSAGES/catfish.mo
msgfmt po/es.po -o build/mo/es/LC_MESSAGES/catfish.mo
msgfmt po/eo.po -o build/mo/eo/LC_MESSAGES/catfish.mo
msgfmt po/lv.po -o build/mo/lv/LC_MESSAGES/catfish.mo
msgfmt po/hr.po -o build/mo/hr/LC_MESSAGES/catfish.mo
msgfmt po/da.po -o build/mo/da/LC_MESSAGES/catfish.mo
intltool-merge -d po org.xfce.Catfish.desktop.in build/share/applications/org.xfce.Catfish.desktop
Merging translations into build/share/applications/org.xfce.Catfish.desktop.
running build_icons
running build_help
running install_lib
creating /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/Window.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/catfishconfig.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/__init__.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/SudoDialog.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/helpers.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/Thumbnailer.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/CatfishSettings.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/AboutDialog.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
copying build/lib.linux-x86_64-2.7/catfish_lib/Builder.py -> /usr/local/lib/python2.7/dist-packages/catfish_lib
creating /usr/local/lib/python2.7/dist-packages/catfish
copying build/lib.linux-x86_64-2.7/catfish/CatfishSearchEngine.py -> /usr/local/lib/python2.7/dist-packages/catfish
copying build/lib.linux-x86_64-2.7/catfish/__init__.py -> /usr/local/lib/python2.7/dist-packages/catfish
copying build/lib.linux-x86_64-2.7/catfish/AboutCatfishDialog.py -> /usr/local/lib/python2.7/dist-packages/catfish
copying build/lib.linux-x86_64-2.7/catfish/CatfishWindow.py -> /usr/local/lib/python2.7/dist-packages/catfish
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/Window.py to Window.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/catfishconfig.py to catfishconfig.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/__init__.py to __init__.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/SudoDialog.py to SudoDialog.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/helpers.py to helpers.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/Thumbnailer.py to Thumbnailer.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/CatfishSettings.py to CatfishSettings.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/AboutDialog.py to AboutDialog.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/Builder.py to Builder.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish/CatfishSearchEngine.py to CatfishSearchEngine.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish/__init__.py to __init__.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish/AboutCatfishDialog.py to AboutCatfishDialog.pyc
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish/CatfishWindow.py to CatfishWindow.pyc
running install_scripts
copying build/scripts-2.7/catfish -> /usr/local/bin
changing mode of /usr/local/bin/catfish to 755
running install_data
creating /usr/local/share/man/man1
copying catfish.1 -> /usr/local/share/man/man1
creating /usr/local/share/metainfo
copying data/metainfo/catfish.appdata.xml -> /usr/local/share/metainfo/
creating /usr/local/share/catfish
creating /usr/local/share/catfish/metainfo
copying data/metainfo/catfish.appdata.xml.in -> /usr/local/share/catfish/metainfo
creating /usr/local/share/catfish/ui
copying data/ui/about_catfish_dialog.xml -> /usr/local/share/catfish/ui
copying data/ui/AboutCatfishDialog.ui -> /usr/local/share/catfish/ui
copying data/ui/catfish_window.xml -> /usr/local/share/catfish/ui
creating /usr/local/share/catfish/media
copying data/media/catfish.svg -> /usr/local/share/catfish/media
copying data/ui/CatfishWindow.ui -> /usr/local/share/catfish/ui
creating /usr/local/share/doc
creating /usr/local/share/doc/catfish
copying README -> /usr/local/share/doc/catfish
creating /usr/local/share/locale
creating /usr/local/share/locale/th
creating /usr/local/share/locale/th/LC_MESSAGES
copying build/mo/th/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/th/LC_MESSAGES
creating /usr/local/share/locale/ca
creating /usr/local/share/locale/ca/LC_MESSAGES
copying build/mo/ca/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ca/LC_MESSAGES
creating /usr/local/share/locale/si
creating /usr/local/share/locale/si/LC_MESSAGES
copying build/mo/si/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/si/LC_MESSAGES
creating /usr/local/share/locale/ml
creating /usr/local/share/locale/ml/LC_MESSAGES
copying build/mo/ml/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ml/LC_MESSAGES
creating /usr/local/share/locale/ko
creating /usr/local/share/locale/ko/LC_MESSAGES
copying build/mo/ko/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ko/LC_MESSAGES
creating /usr/local/share/locale/sr
creating /usr/local/share/locale/sr/LC_MESSAGES
copying build/mo/sr/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/sr/LC_MESSAGES
creating /usr/local/share/locale/af
creating /usr/local/share/locale/af/LC_MESSAGES
copying build/mo/af/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/af/LC_MESSAGES
creating /usr/local/share/locale/nn
creating /usr/local/share/locale/nn/LC_MESSAGES
copying build/mo/nn/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/nn/LC_MESSAGES
creating /usr/local/share/locale/hu
creating /usr/local/share/locale/hu/LC_MESSAGES
copying build/mo/hu/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/hu/LC_MESSAGES
creating /usr/local/share/locale/ms
creating /usr/local/share/locale/ms/LC_MESSAGES
copying build/mo/ms/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ms/LC_MESSAGES
creating /usr/local/share/locale/uk
creating /usr/local/share/locale/uk/LC_MESSAGES
copying build/mo/uk/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/uk/LC_MESSAGES
creating /usr/local/share/locale/sv
creating /usr/local/share/locale/sv/LC_MESSAGES
copying build/mo/sv/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/sv/LC_MESSAGES
creating /usr/local/share/locale/pt_BR
creating /usr/local/share/locale/pt_BR/LC_MESSAGES
copying build/mo/pt_BR/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/pt_BR/LC_MESSAGES
creating /usr/local/share/locale/ku
creating /usr/local/share/locale/ku/LC_MESSAGES
copying build/mo/ku/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ku/LC_MESSAGES
creating /usr/local/share/locale/cs
creating /usr/local/share/locale/cs/LC_MESSAGES
copying build/mo/cs/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/cs/LC_MESSAGES
creating /usr/local/share/locale/nl
creating /usr/local/share/locale/nl/LC_MESSAGES
copying build/mo/nl/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/nl/LC_MESSAGES
creating /usr/local/share/locale/he
creating /usr/local/share/locale/he/LC_MESSAGES
copying build/mo/he/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/he/LC_MESSAGES
creating /usr/local/share/locale/be
creating /usr/local/share/locale/be/LC_MESSAGES
copying build/mo/be/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/be/LC_MESSAGES
creating /usr/local/share/locale/id
creating /usr/local/share/locale/id/LC_MESSAGES
copying build/mo/id/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/id/LC_MESSAGES
creating /usr/local/share/locale/fi
creating /usr/local/share/locale/fi/LC_MESSAGES
copying build/mo/fi/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/fi/LC_MESSAGES
creating /usr/local/share/locale/fr
creating /usr/local/share/locale/fr/LC_MESSAGES
copying build/mo/fr/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/fr/LC_MESSAGES
creating /usr/local/share/locale/bg
creating /usr/local/share/locale/bg/LC_MESSAGES
copying build/mo/bg/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/bg/LC_MESSAGES
creating /usr/local/share/locale/pt
creating /usr/local/share/locale/pt/LC_MESSAGES
copying build/mo/pt/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/pt/LC_MESSAGES
creating /usr/local/share/locale/it
creating /usr/local/share/locale/it/LC_MESSAGES
copying build/mo/it/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/it/LC_MESSAGES
creating /usr/local/share/locale/el
creating /usr/local/share/locale/el/LC_MESSAGES
copying build/mo/el/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/el/LC_MESSAGES
creating /usr/local/share/locale/tr
creating /usr/local/share/locale/tr/LC_MESSAGES
copying build/mo/tr/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/tr/LC_MESSAGES
creating /usr/local/share/locale/ja
creating /usr/local/share/locale/ja/LC_MESSAGES
copying build/mo/ja/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ja/LC_MESSAGES
creating /usr/local/share/locale/ar
creating /usr/local/share/locale/ar/LC_MESSAGES
copying build/mo/ar/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ar/LC_MESSAGES
creating /usr/local/share/locale/eu
creating /usr/local/share/locale/eu/LC_MESSAGES
copying build/mo/eu/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/eu/LC_MESSAGES
creating /usr/local/share/locale/en_AU
creating /usr/local/share/locale/en_AU/LC_MESSAGES
copying build/mo/en_AU/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/en_AU/LC_MESSAGES
creating /usr/local/share/locale/ru
creating /usr/local/share/locale/ru/LC_MESSAGES
copying build/mo/ru/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/ru/LC_MESSAGES
creating /usr/local/share/locale/sq
creating /usr/local/share/locale/sq/LC_MESSAGES
copying build/mo/sq/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/sq/LC_MESSAGES
creating /usr/local/share/locale/zh_TW
creating /usr/local/share/locale/zh_TW/LC_MESSAGES
copying build/mo/zh_TW/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/zh_TW/LC_MESSAGES
creating /usr/local/share/locale/nb
creating /usr/local/share/locale/nb/LC_MESSAGES
copying build/mo/nb/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/nb/LC_MESSAGES
creating /usr/local/share/locale/zh_CN
creating /usr/local/share/locale/zh_CN/LC_MESSAGES
copying build/mo/zh_CN/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/zh_CN/LC_MESSAGES
creating /usr/local/share/locale/de
creating /usr/local/share/locale/de/LC_MESSAGES
copying build/mo/de/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/de/LC_MESSAGES
creating /usr/local/share/locale/sk
creating /usr/local/share/locale/sk/LC_MESSAGES
copying build/mo/sk/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/sk/LC_MESSAGES
creating /usr/local/share/locale/is
creating /usr/local/share/locale/is/LC_MESSAGES
copying build/mo/is/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/is/LC_MESSAGES
creating /usr/local/share/locale/lt
creating /usr/local/share/locale/lt/LC_MESSAGES
copying build/mo/lt/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/lt/LC_MESSAGES
creating /usr/local/share/locale/gl
creating /usr/local/share/locale/gl/LC_MESSAGES
copying build/mo/gl/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/gl/LC_MESSAGES
creating /usr/local/share/locale/pl
creating /usr/local/share/locale/pl/LC_MESSAGES
copying build/mo/pl/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/pl/LC_MESSAGES
creating /usr/local/share/locale/es
creating /usr/local/share/locale/es/LC_MESSAGES
copying build/mo/es/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/es/LC_MESSAGES
creating /usr/local/share/locale/eo
creating /usr/local/share/locale/eo/LC_MESSAGES
copying build/mo/eo/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/eo/LC_MESSAGES
creating /usr/local/share/locale/lv
creating /usr/local/share/locale/lv/LC_MESSAGES
copying build/mo/lv/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/lv/LC_MESSAGES
creating /usr/local/share/locale/hr
creating /usr/local/share/locale/hr/LC_MESSAGES
copying build/mo/hr/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/hr/LC_MESSAGES
creating /usr/local/share/locale/da
creating /usr/local/share/locale/da/LC_MESSAGES
copying build/mo/da/LC_MESSAGES/catfish.mo -> /usr/local/share/locale/da/LC_MESSAGES
creating /usr/local/share/applications
copying build/share/applications/org.xfce.Catfish.desktop -> /usr/local/share/applications
running install_egg_info
Writing /usr/local/lib/python2.7/dist-packages/catfish-1.4.7.egg-info
=== Installing catfish, version 1.4.7 ===
Root: 
Prefix: /usr


Target Data:    /usr/local
Target Scripts: /usr/local/bin


Catfish Data Directory: /usr/local/share/catfish
Desktop File: /usr/local/share/applications/org.xfce.Catfish.desktop


Moving icon file: /usr/local/share/catfish/media/catfish.svg -> /usr/local/share/icons/hicolor/scalable/apps/catfish.svg
Removing empty directory: /usr/local/share/catfish/media
WARNING: the following files are not recognized by DistUtilsExtra.auto:
  ChangeLog
  INSTALL
  PKG-INFO
craig@craig-Latitude-E6500:~/Downloads/catfish-1.4.7$ catdish


Command 'catdish' not found, did you mean:


  command 'catfish' from deb catfish


Try: sudo apt install <deb name>


craig@craig-Latitude-E6500:~/Downloads/catfish-1.4.7$ catfish
Traceback (most recent call last):
  File "/usr/local/bin/catfish", line 25, in <module>
    import gi
ImportError: No module named gi
craig@craig-Latitude-E6500:~/Downloads/catfish-1.4.7$
```

so i geuss i need help to instlall Python to install Catfish 1.4.7

---

### Post by wildmanne39 on 2019-01-31
Please use code tags - if you are using New Reply button - highlight text and use the # button in the text box header. 
 
If using Quick Reply then [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.

---

### Post by Redalien0304 on 2019-01-31
Bump Anyone for Python to Install catfish 1.4.7

---

### Post by again? on 2019-02-01
Try installing these packages...
```
sudo apt install python-cairo python-gi-cairo python-gobject python-xdg python-pexpect
```

Then in your catfish-1.4.7 directory run the install command again.
Should just see a zeitgeist error which is optional.
I tested in a fresh Ubuntu 18.04 and was able to run the catfish GUI after installing those packages and python-distutils-extra.

---

### Post by Redalien0304 on 2019-02-01
Thanks worked for me. got this at the end though 
"WARNING: the following files are not recognized by DistUtilsExtra.auto:  ChangeLog
  INSTALL
  PKG-INFO"

---

### Post by again? on 2019-02-01
Got similar. I think that's normal for those types of files.
```
**[COLOR="#006400"]glen@ubutest:~/Downloads/catfish-1.4.7$[/COLOR] sudo python setup.py install**
[sudo] password for glen: 
ERROR: Python module zeitgeist.client not found
ERROR: Python module zeitgeist.datamodel not found
ERROR: Python module zeitgeist not found
running install
intltool-merge -d po --xml-style data/metainfo/catfish.appdata.xml.in data/metainfo/catfish.appdata.xml
Merging translations into data/metainfo/catfish.appdata.xml.
CREATED data/metainfo/catfish.appdata.xml
running build
running build_py
running build_scripts
running build_i18n
intltool-update -p -g catfish
running build_icons
running build_help
running install_lib
byte-compiling /usr/local/lib/python2.7/dist-packages/catfish_lib/catfishconfig.py to catfishconfig.pyc
running install_scripts
changing mode of /usr/local/bin/catfish to 755
running install_data
copying data/metainfo/catfish.appdata.xml -> /usr/local/share/metainfo/
creating /usr/local/share/catfish/media
copying data/media/catfish.svg -> /usr/local/share/catfish/media
creating /usr/local/share/catfish/metainfo
copying data/metainfo/catfish.appdata.xml.in -> /usr/local/share/catfish/metainfo
running install_egg_info
Removing /usr/local/lib/python2.7/dist-packages/catfish-1.4.7.egg-info
Writing /usr/local/lib/python2.7/dist-packages/catfish-1.4.7.egg-info
=== Installing catfish, version 1.4.7 ===
Root: 
Prefix: /usr

Target Data:    /usr/local
Target Scripts: /usr/local/bin

Catfish Data Directory: /usr/local/share/catfish
Desktop File: /usr/local/share/applications/org.xfce.Catfish.desktop

Moving icon file: /usr/local/share/catfish/media/catfish.svg -> /usr/local/share/icons/hicolor/scalable/apps/catfish.svg
Removing empty directory: /usr/local/share/catfish/media
WARNING: the following files are not recognized by DistUtilsExtra.auto:
  ChangeLog
  HACKING
  INSTALL
**[COLOR="#006400"]glen@ubutest:~/Downloads/catfish-1.4.7$[/COLOR] catfish**

(catfish:1966): Gtk-WARNING **: 21:21:42.831: ../../../../gtk/gtkwidget.c:8584: widget not within a GtkWindow

(catfish:1966): Atk-CRITICAL **: 21:21:42.950: atk_object_set_description: assertion 'ATK_IS_OBJECT (accessible)' failed

```

---

