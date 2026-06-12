---
title: "zenity deps."
date: 2013-05-02
forum: General Help
---

### Post by anv on 2013-05-02
tried to remove zenity package from Lubuntu 64-bit 13.04 :

```
$ sudo apt-get purge zenity
[sudo] password for local: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  cryptsetup-bin docbook-xml docbook-xsl gstreamer0.10-alsa
  gstreamer0.10-pulseaudio icoutils kate-data katepart kde-baseapps-bin
  kde-baseapps-data kde-runtime kde-runtime-data kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools kubuntu-debug-installer libasound2-plugins
  libattica0.4 libaudio2 libcanberra-pulse libcanberra0 libclucene-core1
  libcryptsetup4 libdbusmenu-qt2 libdevmapper-event1.02.1 libdlrestrictions1
  libexiv2-12 libfftw3-single3 libgomp1 libilmbase6 libkactivities-bin
  libkactivities-models1 libkactivities6 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libkxmlrpcclient4 liblcms1 liblvm2app2.2 libmng1
  libmysqlclient18 libnepomuk4 libnepomukcore4abi1 libnepomukquery4a
  libnepomukutils4 libntrack-qt4-1 libntrack0 libopenexr6 libphonon4
  libplasma3 libpolkit-qt-1-1 libpoppler-qt4-4 libpulsedsp libqapt2
  libqapt2-runtime libqca2 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtgui4 libqtwebkit4 libsgutils2-2 libsolid4 libsoprano4 libspeexdsp1
  libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0
  libxml2-utils mysql-common nepomuk-core nepomuk-core-data
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript pulseaudio
  pulseaudio-module-x11 pulseaudio-utils qapt-batch qdbus qtchooser rtkit
  sgml-data shared-desktop-ontologies soprano-daemon sound-theme-freedesktop
  udisks virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common
Suggested packages:
  docbook docbook-dsssl docbook-defguide docbook-xsl-doc-html
  docbook-xsl-doc-pdf docbook-xsl-doc-text docbook-xsl-doc libsaxon-java
  libxalan2-java libxslthl-java docbook-xsl-saxon fop xalan dbtoepub
  libterm-readline-gnu-perl libterm-readline-perl-perl djvulibre-bin finger
  nas libcanberra-gtk0 exiv2 libfftw3-bin libfftw3-dev hspell liblcms-utils
  libqca2-plugin-cyrus-sasl libqca2-plugin-gnupg libqca2-plugin-ossl
  libqt4-declarative-folderlistmodel libqt4-declarative-gestures
  libqt4-declarative-particles libqt4-declarative-shaders qt4-qmlviewer
  libqt4-dev qt4-qtconfig sg3-utils media-player-info phonon-backend-vlc
  phonon-backend-xine phonon-backend-mplayer gstreamer0.10-plugins-ugly
  pavumeter paman pavucontrol paprefs pulseaudio-module-raop
  pulseaudio-esound-compat avahi-daemon qt4-default qt5-default perlsgml
  w3-recs opensp xfsprogs reiserfsprogs mdadm
The following packages will be REMOVED:
  zenity*
The following NEW packages will be installed:
  cryptsetup-bin docbook-xml docbook-xsl gstreamer0.10-alsa
  gstreamer0.10-pulseaudio icoutils kate-data katepart kde-baseapps-bin
  kde-baseapps-data kde-runtime kde-runtime-data kdelibs-bin kdelibs5-data
  kdelibs5-plugins kdoctools kubuntu-debug-installer libasound2-plugins
  libattica0.4 libaudio2 libcanberra-pulse libcanberra0 libclucene-core1
  libcryptsetup4 libdbusmenu-qt2 libdevmapper-event1.02.1 libdlrestrictions1
  libexiv2-12 libfftw3-single3 libgomp1 libilmbase6 libkactivities-bin
  libkactivities-models1 libkactivities6 libkatepartinterfaces4 libkcmutils4
  libkde3support4 libkdeclarative5 libkdecore5 libkdesu5 libkdeui5
  libkdewebkit5 libkdnssd4 libkemoticons4 libkfile4 libkhtml5 libkidletime4
  libkio5 libkjsapi4 libkjsembed4 libkmediaplayer4 libknewstuff3-4
  libknotifyconfig4 libkntlm4 libkparts4 libkpty4 libkrosscore4
  libktexteditor4 libkxmlrpcclient4 liblcms1 liblvm2app2.2 libmng1
  libmysqlclient18 libnepomuk4 libnepomukcore4abi1 libnepomukquery4a
  libnepomukutils4 libntrack-qt4-1 libntrack0 libopenexr6 libphonon4
  libplasma3 libpolkit-qt-1-1 libpoppler-qt4-4 libpulsedsp libqapt2
  libqapt2-runtime libqca2 libqt4-dbus libqt4-declarative libqt4-designer
  libqt4-network libqt4-opengl libqt4-qt3support libqt4-script libqt4-sql
  libqt4-sql-mysql libqt4-svg libqt4-xml libqt4-xmlpatterns libqtcore4
  libqtgui4 libqtwebkit4 libsgutils2-2 libsolid4 libsoprano4 libspeexdsp1
  libssh-4 libstreamanalyzer0 libstreams0 libthreadweaver4 libvirtodbc0
  libxml2-utils mysql-common nepomuk-core nepomuk-core-data
  ntrack-module-libnl-0 odbcinst odbcinst1debian2 oxygen-icon-theme phonon
  phonon-backend-gstreamer plasma-scriptengine-javascript pulseaudio
  pulseaudio-module-x11 pulseaudio-utils qapt-batch qdbus qtchooser rtkit
  sgml-data shared-desktop-ontologies soprano-daemon sound-theme-freedesktop
  udisks virtuoso-minimal virtuoso-opensource-6.1-bin
  virtuoso-opensource-6.1-common
0 upgraded, 128 newly installed, 1 to remove and 0 not upgraded.
Need to get 92,4 MB of archives.
After this operation, 277 MB of additional disk space will be used.
Do you want to continue [Y/n]? 

```

why there is so much dependencies to be installed if I just want to uninstall it ?

---

