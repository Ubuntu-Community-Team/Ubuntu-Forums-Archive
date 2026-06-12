---
title: "Problem removing amarok."
date: 2007-05-04
forum: General Help
---

### Post by Tadhg on 2007-05-04
I'm trying to reinstall amarok from source as I want mtp support for my creative mp3, but every time i try:

```
sudo apt-get remove amarok 
```

it tells me that it will also remove kubuntu-desktop, and basically everything to do with it.

```

timmy@ibo:~$ sudo apt-get remove amarok
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following packages were automatically installed and are no longer required:
  kpdf xkeyboard-config ksystemlog gcj-4.1-base krdc libopenobex-1.0-0 libwpd8c2a krfb libxmlsec1 kscd kppp libktnef1 konversation krita-data
  kubuntu-default-settings ttf-devanagari-fonts libmagick9 libkscan1 libjaxp1.2-java python2.4-dev pnm2ppa cupsys-common openoffice.org-core openoffice.org-writer
  adept-manager kmplayer-konq-plugins libgcj7-0 openoffice.org-style-default libneon25 ksvg kscreensaver cdparanoia xfonts-scalable openoffice.org-impress
  libgstreamer0.10-0 ttf-punjabi-fonts linux-headers-generic kaffeine-xine wvdial libgcj-bc ttf-indic-fonts kio-locate libpythonize0 vorbis-tools libicu34
  openoffice.org-draw smbclient ttf-thai-tlwg ttf-kochi-mincho ksnapshot liblockdev1 libxmlsec1-openssl kdebluetooth kooka iso-codes doc-base libkipi0
  avahi-daemon wlassistant cdrecord libxt-java ttf-mgopen openoffice.org-java-common libkcal2b fortunes-min openoffice.org-kde app-install-data
  libwvstreams4.2-base libmagick++9c2a libsane adept-installer unzip libkexif1 ttf-kannada-fonts ttf-gentium kdegraphics-kfile-plugins python-libxml2 gwenview
  bluez-cups libpoppler1-qt libtdb1 readahead scrollkeeper adept-updater hpijs dvd+rw-tools docbook-xml kdepim-kio-plugins brltty libieee1284-3 libstlport4.6c2
  libqt4-qt3support screen hwdb-client-kde libapm1 krita bc hplip acpi qca-tls dc libmimelib1c2a kubuntu-artwork-usplash libxmlsec1-nss libqt4-core python-apt
  kontact libsqlite0 cupsys-bsd libslp1 mysql-common kdeadmin-kfile-plugins powernowd libsqlite3-0 adept-batch fortune-mod koffice-data libgpod0 kde-icons-mono
  libscim8c2a libcurl3-gnutls ttf-lao dcraw foomatic-db-engine kubuntu-desktop libmdbtools toshset ttf-kochi-gothic pykdeextensions adept ksplash-engine-moodin
  kubuntu-konqueror-shortcuts libmysqlclient15off gij-4.1 apmd foomatic-db-hpijs ruby1.8 kaffeine libkleopatra1 xfonts-75dpi skim vbetool kipi-plugins korganizer
  k3b kdenetwork-kfile-plugins librecode0 kbstate akregator kio-apt acpid kwin-style-crystal finger bluez-utils diveintopython libmusicbrainz4c2a arts python-qt3
  python-qt4 ark laptop-mode-tools libexif-dev libgphoto2-2-dev ruby ttf-gujarati-fonts kcron libjasper-runtime powermgmt-base bsh hwdb-client-common adept-common
  libgmp3c2 openoffice.org-math libqt4-gui libcurl3 xfonts-base libgcj-common gij openoffice.org-common python-uno python-sip4 libksieve0 ttf-telugu-fonts digikam
  amarok-xine ttf-tamil-fonts libbrlapi1 libgutenprint2 kdm speedcrunch openoffice.org ttf-opensymbol libkpimidentities1 libpoppler1 amarok libskim0 kpf
  bogofilter-bdb libkdepim1a ssl-cert kdnssd libjline-java python-dbus cupsys-driver-gutenprint kdemultimedia-kfile-plugins katapult libxerces2-java libglade2-0
  kdenetwork-filesharing ttf-arphic-uming kubuntu-docs knotes bogofilter powermanagement-interface libtunepimp3 kde-guidance libqt4-sql libifp4 debtags fping
  ttf-malayalam-fonts libgsl0 apt-index-watcher landscape-client kaddressbook libxalan2-java libkpimexchange1 gtk2-engines-gtk-qt xfonts-100dpi cdrdao
  xcursor-themes kmailcvt acpi-support openoffice.org-style-crystal rdiff-backup foo2zjs ttf-arphic-ukai knetworkconf konq-plugins libkmime2
  libwvstreams4.2-extras libdaemon0 smartdimmer language-selector-qt zip libxplc0.3.13 language-selector-common qobex ttf-oriya-fonts foomatic-filters
  poppler-utils sgml-data slocate libsnmp-base xorg ktorrent foomatic-db libpq4 ttf-baekmuk libgpgme11 libhsqldb-java scim-qtimm kwalletmanager libsnmp9
  radeontool samba-common ttf-arabeyes kopete libuniconf4.2 cupsys-client libservlet2.3-java openoffice.org-base python-elementtree karm hotkey-setup kmail
  libruby1.8 libvisual-0.4-0 mkisofs keep koffice-libs cupsys adept-notifier bogofilter-common libimlib2 openoffice.org-calc kde-guidance-powermanager
  ttf-bengali-fonts libjpeg-progs min12xxw libgstreamer-plugins-base0.10-0 kde-systemsettings libscrollkeeper0 librsync1 libavahi-core4 libsndfile1 kmousetool
  kmag bluez-pin example-content kdepim-kresources kdepim-wizards kmilo kmplayer-base usplash kaudiocreator python-kde3 hplip-data kdepasswd lftp kmix libxine1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  amarok amarok-xine kubuntu-desktop
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 32.3MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

```

Why would anyone want to do that?! Is it time for a feisty upgrade?

---

### Post by hyperair on 2007-05-04
Don't use that command. Use 
```
sudo apt-get --reinstall install amarok
``` if you want to reinstall your amarok. Amarok is a dependency of the kubuntu-desktop metapackage, and when you remove amarok, that metapackage will be uninstalled as well. That metapakcage was in charge of installing all the various KDE apps that you use, and these packages are considered "automatically installed" and will be removed should you do a "sudo apt-get autoremove".

---

