---
title: "Search index in ubuntu 18.04"
date: 2019-07-21
forum: General Help
---

### Post by icegood on 2019-07-21
Hello there. 
i wonder how search tracker or whatever works in ubuntu 18.04. I have problem that i have too many result for my query "Qt". It displays in particular "Qt (Community)" and such an appropriate  *desktop file existed long time ago but now don't.
For now i have two files in /usr/share/applications with the next content:

qtcreator-4.9-stable-community.desktop:
```

[Desktop Entry]
Type=Application
Exec=/opt/Qt/Tools/QtCreator/bin/qtcreator
Name=Qt Creator 4.9
GenericName=The IDE of choice for Qt development.
Icon=QtProject-qtcreator
StartupWMClass=qtcreator
Terminal=false
Categories=Development;IDE;Qt;
MimeType=text/x-c++src;text/x-c++hdr;text/x-xsrc;application/x-designer;application/vnd.qt.qmakeprofile;application/vnd.qt.xml.resource;text/x-qml;text/x-qt.qml;text/x-qt.qbs;
```

qtcreator-4.10-beta-community.desktop
```

[Desktop Entry]
Type=Application
Exec="/opt/Qt/Tools/Preview/Qt Creator 4.10.0-beta2/bin/qtcreator"
Name=QtCreator 4.10.0 beta2
GenericName=The IDE of choice for Qt development.
Icon=QtProject-qtcreator
StartupWMClass=qtcreator2
Terminal=false
Categories=Development;IDE;Qt;
MimeType=text/x-c++src;text/x-c++hdr;text/x-xsrc;application/x-designer;application/vnd.qt.qmakeprofile;application/vnd.qt.xml.resource;text/x-qml;text/x-qt.qml;text/x-qt.qbs;

```

I see both these files in search however i see two more files, one of which i described above. 

**What i did**:
1) i found my freedesktop org environment.
env | grep XDG:
```
XDG_MENU_PREFIX=gnome-
XDG_VTNR=1
XDG_SESSION_ID=1
XDG_SESSION_TYPE=x11
XDG_DATA_DIRS=/usr/share/ubuntu:/usr/local/share:/usr/share:/var/lib/snapd/desktop
XDG_SESSION_DESKTOP=ubuntu
XDG_CURRENT_DESKTOP=ubuntu:GNOME
XDG_SEAT=seat0
XDG_RUNTIME_DIR=/run/user/1000
XDG_CONFIG_DIRS=/etc/xdg/xdg-ubuntu:/etc/xdg

```
2) i checked all *desktop files in $1/applications  where $1 from XDG_DATA_DIRS. Found no extra files.
3) In dconf-editor in org.freedesktop.Tracker.Miner.Files i removed both index-single-directories and index-reccursive-directories
settings.
4) In  Settings/Searcher i removed all but Files. And After that i removed Files as well. 
After all actions i relogged.
But i still have in search menu all files.
As for me it doesn't  seem i working with tracker but with some another searcher instead. What i can do more sophisticated than grepping from / for "Qt \(Community)\" pattern?

---

### Post by icegood on 2019-09-14
Anyone? For this moment i removed all old files that related to qt and update mimeinfo.cache files in applications. However anyway i see two entries related to in searcher. These entries are new one. So i wonder, how things became to work with /without XDG?

---

