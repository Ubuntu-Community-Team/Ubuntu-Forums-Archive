---
title: "Kate, kile and other KDE applications crash in Ubuntu"
date: 2013-10-04
forum: General Help
---

### Post by akm3 on 2013-10-04
I seem to have some issues with gtk libraries when trying to open KDE applications on my Ubnutu. Including Kate, Kile, etc (also the problem was observed when opening Mendeley desktop)

The system is a **64-bit Ubuntu 12.04**

Attached are error messages:

For Kate:
```

QDBusConnection: session D-Bus connection created before QCoreApplication.              Application may misbehave.
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Gtk-Message: Failed to load module "canberra-gtk-module"
Enchant dict for "en_US" 0x195af30 
kate(4995)/Kate (On-The-Fly Spellcheck) KateOnTheFlyChecker::KateOnTheFlyChecker:         created
kate(4995)/Kate (On-The-Fly Spellcheck) KateOnTheFlyChecker::updateConfig:
Enchant dict for "en_US" 0x19644b0 
kate(4995)/Kate (On-The-Fly Spellcheck) KateOnTheFlyChecker::freeDocument:
kate(4995)/kate-filetree KateFileTreePluginView::KateFileTreePluginView: BEGIN: mw:         Kate::MainWindow(0x17d6af0)
kate(4995)/kate-filetree ProxyItem::ProxyItem:         ProxyItem(0x2139b60,0x0,-1,QObject(0x0) ,"m_root")
kate(4995)/kate-filetree ProxyItem::ProxyItem:         ProxyItem(0x213a4f0,0x0,-1,QObject(0x0) ,"Untitled")
kate(4995)/kate-filetree KateFileTreeModel::documentOpened: before add:         ProxyItem(0x213a4f0,0x0,-1,KateDocument(0x19387a0) , "Untitled" )
kate(4995)/kate-filetree KateFileTreeModel::setupIcon: BEGIN!
kate(4995)/kate-filetree KateFileTreeModel::setupIcon: END!
kate(4995)/kate-filetree KateFileTreeModel::handleInsert: BEGIN!
kate(4995)/kate-filetree KateFileTreeModel::handleInsert: empty item
kate(4995)/kate-filetree ProxyItem::addChild: added         ProxyItem(0x213a4f0,0x2139b60,0,KateDocument(0x19387a0) , "Untitled" )   to         ProxyItemDir(0x2139b60,0x0,-1,"m_root", children:1)
kate(4995)/kate-filetree KateFileTreeModel::documentOpened: after add:         ProxyItem(0x213a4f0,0x2139b60,0,KateDocument(0x19387a0) , "Untitled" )
kate(4995)/kate-filetree KateFileTreeProxyModel::KateFileTreeProxyModel: BEGIN!
kate(4995)/kate-filetree KateFileTreePluginView::setListMode: BEGIN
kate(4995)/kate-filetree KateFileTreePluginView::setListMode: treeMode
kate(4995)/kate-filetree KateFileTreePluginView::setListMode: END
Cannot mix incompatible Qt library (version 0x40801) with this library (version         0x40804)
KCrash: Application 'kate' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/alireza/.kde/socket-alireza-OptiPlex-755/kdeinit4__0
```


for Kile:

```
QDBusConnection: session D-Bus connection created before QCoreApplication.     Application may misbehave.
kile(5037)/kdecore (KLibrary) findLibraryInternal: plugins should not have a 'lib'     prefix: "libkonsolepart.so"
Enchant dict for "en_US" 0x25a1300 
kile(5037)/Kate (On-The-Fly Spellcheck) KateOnTheFlyChecker::KateOnTheFlyChecker:     created
kile(5037)/Kate (On-The-Fly Spellcheck) KateOnTheFlyChecker::updateConfig:
Enchant dict for "en_US" 0x25aa650 
kile(5037)/Kate (On-The-Fly Spellcheck) KateOnTheFlyChecker::freeDocument:
kile(5037)/Kate (On-The-Fly Spellcheck) KateOnTheFlyChecker::updateConfig:
Enchant dict for "en_US" 0x25da0d0 
kile(5037)/konsole Konsole::Session::run: Attempted to re-run an already running     session. 
Cannot mix incompatible Qt library (version 0x40801) with this library (version     0x40804)
KCrash: Application 'kile' crashing...
KCrash: Attempting to start /usr/lib/kde4/libexec/drkonqi from kdeinit
sock_file=/home/alireza/.kde/socket-alireza-OptiPlex-755/kdeinit4__0
Any ideas of a fix?
```

For Mendeley:

```
Using system Qt version 4.8.1 in /usr/lib/x86_64-linux-gnu
/usr/bin/../../opt/mendeleydesktop/bin/mendeleydesktop: symbol lookup error: /usr/bin/../../opt/mendeleydesktop/bin/mendeleydesktop: undefined symbol: _ZN10QSslSocket16staticMetaObjectE
```

---

### Post by enterdavertex on 2013-10-04
Go into CLI mode , try re-installing the GTK Librairy

---

### Post by akm3 on 2013-10-04
Thanks, 
Reinstalled all gtk2.0 libraries
But problem still persists, in all cases :(

---

