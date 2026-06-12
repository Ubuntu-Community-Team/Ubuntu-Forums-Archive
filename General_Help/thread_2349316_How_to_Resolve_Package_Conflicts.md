---
title: "How to Resolve Package Conflicts?"
date: 2017-01-13
forum: General Help
---

### Post by noleks on 2017-01-13
I just upgraded from Ubuntu 14.04 to 16.04.

The software updater keeps giving me these popup mesages, which indicate that the packages are not playing 100% together:

Failure to download extra data files

The following packages requested additional data downloads after package installation, but the data could not be downloaded or could not be processed.

wine-silverlight5.1-installer, wine-browser-installer, ttf-mscorefonts-installer

The download will be attempted again later, or you can try the download again now. Running this command requires an active Internet connection.

I proceeded to try to uninstall these guys since I know I don't need them, right now.  That's when I ran into my "real" issue:


```
UBUNTU:~> sudo apt remove wine-silverlight5.1-installer
[sudo] password for noleks: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 python3-pil.imagetk : Depends: python3-tk (>= 3.4.1-2) but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
```

Earlier I tried to install python3-pil.imagetk as part of the instructions to my son's Christmas present (A Cozmo robot) which has a Linux SDK available.
sudo apt-get install python3-pil.imagetkI'm not sure how to clean out the old packages and resolve the conflict above.  If I try to install python3-tk, I get:

```
UBUNTU:~> sudo apt-get install python3-tk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core gnome-exe-thumbnailer icoutils kactivities kate-data katepart kde-runtime kde-runtime-data
  kde-style-breeze kde-style-breeze-qt4 kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools kpackagelauncherqml kpackagetool5
  libattica0.4 libdlrestrictions1 libgif7:i386 libjs-sphinxdoc libjs-underscore libkactivities6 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4 libkemoticons4 libkf5activities5
  libkf5archive5 libkf5calendarevents5 libkf5declarative-data libkf5declarative5 libkf5package-data libkf5package5 libkf5plasma5
  libkf5plasmaquick5 libkf5quickaddons5 libkf5style5 libkfile4 libkhtml5 libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4
  libknewstuff3-4 libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4 libktexteditor4 libkxmlrpcclient4 libntrack-qt4-1
  libntrack0 libp11-kit-gnome-keyring:i386 libphonon4 libplasma3 libpolkit-qt-1-1 libqca2 libqca2-plugins libqqwing2v5
  libqt4-qt3support libqt5quickwidgets5 libsolid4 libstreamanalyzer0v5 libstreams0v5 libthreadweaver4 libxcb-composite0
  libxcb-damage0 ntrack-module-libnl-0 ocl-icd-libopencl1:i386 odbcinst odbcinst1debian2 oxygen-icon-theme oxygen5-icon-theme
  p11-kit-modules:i386 p7zip phonon phonon-backend-gstreamer phonon-backend-gstreamer-common plasma-framework
  plasma-scriptengine-javascript python-pyxattr qml-module-org-kde-activities qml-module-org-kde-kquickcontrols
  qml-module-org-kde-kquickcontrolsaddons qml-module-qt-labs-folderlistmodel qml-module-qt-labs-settings
  qml-module-qtquick-controls unixodbc wine-browser-installer wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  wine-silverlight5.1-installer
Use 'sudo apt autoremove' to remove them.
Suggested packages:
  tix python3-tk-dbg
The following NEW packages will be installed:
  python3-tk
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0 B/25.1 kB of archives.
After this operation, 89.1 kB of additional disk space will be used.
(Reading database ... 422048 files and directories currently installed.)
Preparing to unpack .../python3-tk_3.5.1-1_amd64.deb ...
Unpacking python3-tk (3.5.1-1) ...
[B]dpkg: error processing archive /var/cache/apt/archives/python3-tk_3.5.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python3.5/lib-dynload/_tkinter.cpython-35m-x86_64-linux-gnu.so', which is also in package libpython3.5-tk:amd64 3.5.2-1~trusty1[/B]
Errors were encountered while processing:
 /var/cache/apt/archives/python3-tk_3.5.1-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

Help???

---

### Post by ajgreeny on 2017-01-13
Have you tried the command suggested by the first error you quote, ```
sudo apt-get -f install
``` to fix broken packages?

That might sort out your problem, but if not come back again with any further errors shown.

---

### Post by noleks on 2017-01-13
**UBUNTU:~> sudo apt-get -f install**
[sudo] password for noleks: 
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  fonts-horai-umefont fonts-unfonts-core gnome-exe-thumbnailer icoutils kactivities
  kate-data katepart kde-runtime kde-runtime-data kde-style-breeze kde-style-breeze-qt4
  kdelibs-bin kdelibs5-data kdelibs5-plugins kdoctools kpackagelauncherqml
  kpackagetool5 libattica0.4 libdlrestrictions1 libgif7:i386 libjs-sphinxdoc
  libjs-underscore libkactivities6 libkatepartinterfaces4 libkcmutils4 libkde3support4
  libkdeclarative5 libkdecore5 libkdesu5 libkdeui5 libkdewebkit5 libkdnssd4
  libkemoticons4 libkf5activities5 libkf5archive5 libkf5calendarevents5
  libkf5declarative-data libkf5declarative5 libkf5package-data libkf5package5
  libkf5plasma5 libkf5plasmaquick5 libkf5quickaddons5 libkf5style5 libkfile4 libkhtml5
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4 libknotifyconfig4
  libkntlm4 libkparts4 libkpty4 libkrosscore4 libktexteditor4 libkxmlrpcclient4
  libntrack-qt4-1 libntrack0 libp11-kit-gnome-keyring:i386 libphonon4 libplasma3
  libpolkit-qt-1-1 libqca2 libqca2-plugins libqqwing2v5 libqt4-qt3support
  libqt5quickwidgets5 libsolid4 libstreamanalyzer0v5 libstreams0v5 libthreadweaver4
  libxcb-composite0 libxcb-damage0 ntrack-module-libnl-0 ocl-icd-libopencl1:i386
  odbcinst odbcinst1debian2 oxygen-icon-theme oxygen5-icon-theme p11-kit-modules:i386
  p7zip phonon phonon-backend-gstreamer phonon-backend-gstreamer-common
  plasma-framework plasma-scriptengine-javascript python-pyxattr
  qml-module-org-kde-activities qml-module-org-kde-kquickcontrols
  qml-module-org-kde-kquickcontrolsaddons qml-module-qt-labs-folderlistmodel
  qml-module-qt-labs-settings qml-module-qtquick-controls unixodbc
  wine-browser-installer wine-gecko2.21 wine-gecko2.21:i386 wine-mono0.0.8
  wine-silverlight5.1-installer
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  python3-tk
Suggested packages:
  tix python3-tk-dbg
The following NEW packages will be installed:
  python3-tk
0 upgraded, 1 newly installed, 0 to remove and 19 not upgraded.
1 not fully installed or removed.
Need to get 0 B/25.1 kB of archives.
After this operation, 89.1 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 422048 files and directories currently installed.)
Preparing to unpack .../python3-tk_3.5.1-1_amd64.deb ...
Unpacking python3-tk (3.5.1-1) ...
dpkg: error processing archive /var/cache/apt/archives/python3-tk_3.5.1-1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python3.5/lib-dynload/_tkinter.cpython-35m-x86_64-linux-gnu.so', which is also in package libpython3.5-tk:amd64 3.5.2-1~trusty1
Errors were encountered while processing:
 /var/cache/apt/archives/python3-tk_3.5.1-1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

It's got something stuck in its craw, not sure why this conflict exists...

---

