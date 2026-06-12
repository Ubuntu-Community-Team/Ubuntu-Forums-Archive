---
title: "Trying to compile KTorrent from source"
date: 2012-10-24
forum: General Help
---

### Post by Stonecold1995 on 2012-10-24
I want to install KTorrent 4.3.0 from source.  This is exactly what I did:
```
cd /tmp
sudo apt-get build-dep ktorrent
wget http://ktorrent.org/downloads/4.3.0/ktorrent-4.3.0.tar.bz2
atool -x ktorrent-4.3.0.tar.bz2
cd ktorrent-4.3.0
mkdir build
cd build
cmake -DCMAKE_INSTALL_PREFIX=$(kde4-config --prefix) ..
make
```

But that gave me this error:
```
alex@kubuntu:/tmp/ktorrent-4.3.0/build$ make
Scanning dependencies of target ktcore_automoc
Generating torrentfilelistmodel.moc
Generating prefpageinterface.moc
Generating coreinterface.moc
Generating queuemanager.moc
Generating torrentfiletreemodel.moc
Generating torrentfilemodel.moc
Generating plugin.moc
Generating chunkbar.moc
Generating moc_itemselectionmodel.cpp
Generating moc_group.cpp
Generating moc_dbustorrentfilestream.cpp
Generating moc_groupmanager.cpp
Generating moc_centralwidget.cpp
Generating moc_tabbarwidget.cpp
Generating moc_extender.cpp
Generating moc_dbus.cpp
Generating moc_dbusgroup.cpp
Generating moc_pluginactivity.cpp
Generating moc_basicjobprogresswidget.cpp
Generating moc_activity.cpp
Generating moc_torrentgroup.cpp
Generating moc_stringcompletionmodel.cpp
Generating moc_dbussettings.cpp
Generating moc_dbustorrent.cpp
Generating moc_jobtracker.cpp
Generating moc_jobprogresswidget.cpp
[  0%] Built target ktcore_automoc
[  0%] Generating settings.h, settings.cpp
[  1%] Generating ui_basicjobprogresswidget.h
Scanning dependencies of target ktcore
[  1%] Building CXX object libktcore/CMakeFiles/ktcore.dir/ktcore_automoc.o
[  1%] Building CXX object libktcore/CMakeFiles/ktcore.dir/util/mmapfile.o
[  2%] Building CXX object libktcore/CMakeFiles/ktcore.dir/util/itemselectionmodel.o
[  2%] Building CXX object libktcore/CMakeFiles/ktcore.dir/util/stringcompletionmodel.o
[  2%] Building CXX object libktcore/CMakeFiles/ktcore.dir/util/treefiltermodel.o
[  2%] Building CXX object libktcore/CMakeFiles/ktcore.dir/interfaces/functions.o
/tmp/ktorrent-4.3.0/libktcore/interfaces/functions.cpp:35:34: fatal error: peer/connectionlimit.h: No such file or directory
compilation terminated.
make[2]: *** [libktcore/CMakeFiles/ktcore.dir/interfaces/functions.o] Error 1
make[1]: *** [libktcore/CMakeFiles/ktcore.dir/all] Error 2
make: *** [all] Error 2
```

---

### Post by Stonecold1995 on 2012-10-27
bump

---

### Post by ankspo71 on 2012-10-30
Hi, 
The error says that it can not find the file called "connectionlimit.h" which is a file found in the package libktorrent-1.3.0.tar.bz2, and the instructions at the ktorrent site says that libktorrent must be compiled first.

Here are the downloads and instructions
[http://ktorrent.org/?q=downloads](http://ktorrent.org/?q=downloads)

Also don't forget the dependencies of libktorrent4:
```
sudo apt-get build-dep ktorrent libktorrent4
```

---

### Post by Stonecold1995 on 2012-10-30
I had forgotten about libktorrent.  Thank you.

---

### Post by susanin on 2013-03-20
Guys, what if I had successfully installed dependenses by command ```
sudo apt-get build-dep ktorrent
``` and built libktorrent from sources, but still have error 
```
ktorrent-4.3.1/libktcore/interfaces/functions.cpp:35:34: fatal error: peer/connectionlimit.h: No such file or directory
compilation terminated.
make[2]: *** [libktcore/CMakeFiles/ktcore.dir/interfaces/functions.o] Error 1
make[1]: *** [libktcore/CMakeFiles/ktcore.dir/all] Error 2
make: *** [all] Error 2

```
during building of ktorrent. What should I do to fix that?

---

### Post by oldos2er on 2013-03-20
Read post #3.

---

### Post by susanin on 2013-03-20
As I've said, I've built libktorrent and have installed dependenses, but still have error. It's strange that missed file is placed in source directory in libktorrent folder, but isn't placed in ktorrent folder...

---

### Post by oldos2er on 2013-03-21
Which version of libktorrent did you build? And what version of KDE are you running?

---

### Post by susanin on 2013-03-21
ktorrent-4.3.1
libktorrent-1.3.1
kde  4.9.5

---

### Post by oldos2er on 2013-03-21
You don't have an older libktorrent file somewhere in your system? I'm kind of at a loss to explain the error.

---

### Post by oldos2er on 2013-04-07
> **susanin said:**
> As I've said, I've built libktorrent and have installed dependenses, but still have error. It's strange that missed file is placed in source directory in libktorrent folder, but isn't placed in ktorrent folder...

I ran into this same problem myself. The solution that worked for me was to uninstall the older repository versions of both ktorrent and libktorrent; then I was able to compile and install the new ones.

---

