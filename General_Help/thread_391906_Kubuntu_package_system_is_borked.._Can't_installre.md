---
title: "Kubuntu package system is borked.. Can't install/remove anything"
date: 2007-03-23
forum: General Help
---

### Post by mfarley on 2007-03-23
I'm relatively new to linux desktop and have managed to screw my KDE/Kubuntu package dependencies.  Here's a simple log of what happens when I try to install something, any ideas on how to resolve this?  

Side note, Kopete is complaining because I had to install the package from kubuntu 7.04 when I'm running 6.10 (the upgrade provided some fix that allowed ICQ and AIM to pull contacts from the server).

Anyway, here's what's going on:

[Mar 23 07:57 PM][matt@ubuntu:~/Desktop]$ sudo apt-get install htop
Reading package lists... Done
Building dependency tree
Reading state information... Done
htop is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  kopete: Depends: kdelibs4c2a (>= 4:3.5.5-1) but 4:3.5.5-0ubuntu3.1 is to be installed
          Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12 is to be installed
          Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-7ubuntu2 is to be installed
          Depends: libgadu3 (>= 1:1.7~rc2) but it is not going to be installed
          Depends: libgcc1 (>= 1:4.1.2) but 1:4.1.1-13ubuntu5 is to be installed
          Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
          Depends: libmeanwhile1 (>= 1.0.2) but it is not going to be installed
          Depends: libpng12-0 (>= 1.2.13-4) but 1.2.8rel-5.1ubuntu0.1 is to be installed
          Depends: libqt3-mt (>= 3:3.3.8) but 3:3.3.6-3ubuntu3 is to be installed
          Depends: libstdc++6 (>= 4.1.2) but 4.1.1-13ubuntu5 is to be installed
          Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
          Depends: libxrandr2 (>= 2:1.2.0) but 2:1.1.1-0ubuntu1 is to be installed
          Depends: libxslt1.1 (>= 1.1.20) but 1.1.17-2build1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


[Mar 23 07:57 PM][matt@ubuntu:~/Desktop]$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  kpdf xkeyboard-config ksystemlog krdc libopenobex-1.0-0 libwpd8c2a krfb libxmlsec1 kscd kppp libktnef1 konversation krita-data kubuntu-default-settings ttf-devanagari-fonts libkscan1
  libjaxp1.2-java python2.4-dev pnm2ppa cupsys-common kdeprint openoffice.org-core openoffice.org-writer gs-esp adept-manager libgphoto2-port0 kmplayer-konq-plugins
  openoffice.org-style-default ksvg kscreensaver cdparanoia xfonts-scalable openoffice.org-impress kwin libportaudio0 ttf-punjabi-fonts linux-headers-generic kaffeine-xine libsensors3
  wvdial ttf-indic-fonts libavahi-compat-libdnssd1 kio-locate libk3b2 libpythonize0 vorbis-tools libicu34 openoffice.org-draw smbclient ttf-thai-tlwg ttf-kochi-mincho ksnapshot liblockdev1
  libxmlsec1-openssl kdebluetooth kooka iso-codes doc-base kcontrol libkipi0 libglib1.2 avahi-daemon wlassistant cdrecord libxt-java ttf-mgopen openoffice.org-java-common libkcal2b
  libflac++5c2 fortunes-min openoffice.org-kde app-install-data libwvstreams4.2-base libmagick++9c2a libsane adept-installer unzip libkexif1 ttf-kannada-fonts ttf-gentium
  kdegraphics-kfile-plugins konqueror-nsplugins python-libxml2 kdebase-data gwenview bluez-cups libpoppler1-qt libtdb1 readahead scrollkeeper adept-updater hpijs dvd+rw-tools docbook-xml
  kdepim-kio-plugins brltty libieee1284-3 libstlport4.6c2 screen hwdb-client-kde libapm1 krita hplip acpi qca-tls dc java-common libmimelib1c2a klipper kdemultimedia-kio-plugins
  kubuntu-artwork-usplash libxmlsec1-nss python-apt kontact cupsys-bsd libslp1 kdeadmin-kfile-plugins kicker ksmserver ksysguard powernowd libsqlite3-0 adept-batch fortune-mod koffice-data
  linux-headers-2.6.17-11-generic libkcddb1 libgpod0 kde-icons-mono libscim8c2a libcurl3-gnutls ttf-lao dcraw libgphoto2-2 foomatic-db-engine kmenuedit libmdbtools toshset ttf-kochi-gothic
  pykdeextensions adept ksplash-engine-moodin libnss-mdns kubuntu-konqueror-shortcuts ksplash apmd foomatic-db-hpijs ruby1.8 kaffeine libkleopatra1 xfonts-75dpi skim vbetool kipi-plugins
  korganizer k3b kdenetwork-kfile-plugins kdebase-kio-plugins librecode0 kbstate akregator kio-apt acpid kwin-style-crystal finger bluez-utils diveintopython libmusicbrainz4c2a arts
  python-qt3 python-qt4 kamera j2re1.4 ark laptop-mode-tools libexif-dev libgphoto2-2-dev ruby ttf-gujarati-fonts kcron libjasper-runtime powermgmt-base bsh hwdb-client-common adept-common
  libgmp3c2 openoffice.org-math gs-common libkonq4 gdb libcurl3 hal openoffice.org-common python-uno python-sip4 libksieve0 ttf-telugu-fonts digikam kfind amarok-xine kdebase-bin
  ttf-tamil-fonts libbrlapi1 dictionaries-common libgutenprint2 kdm speedcrunch openoffice.org ttf-opensymbol libkpimidentities1 libpoppler1 amarok libskim0 kpf bogofilter-bdb libkdepim1a
  ssl-cert kdnssd libjline-java python-dbus cupsys-driver-gutenprint kghostview kdemultimedia-kfile-plugins katapult libxerces2-java poster libao2 kdenetwork-filesharing ttf-arphic-uming
  kubuntu-docs knotes libbluetooth2 bogofilter powermanagement-interface libtunepimp3 kde-guidance libifp4 debtags libdbus-qt-1-1c2 fping ttf-malayalam-fonts libgsl0 khelpcenter
  apt-index-watcher kdesktop landscape-client konqueror kaddressbook libxalan2-java libkpimexchange1 gtk2-engines-gtk-qt xfonts-100dpi cdrdao xcursor-themes kmailcvt acpi-support
  openoffice.org-style-crystal rdiff-backup foo2zjs ttf-arphic-ukai knetworkconf ksysguardd konq-plugins libkmime2 libwvstreams4.2-extras libdaemon0 psutils smartdimmer language-selector-qt
  zip libcupsimage2 libxplc0.3.13 language-selector-common libtag1c2a qobex ttf-oriya-fonts foomatic-filters libmeanwhile1 poppler-utils sgml-data slocate libsnmp-base xorg ktorrent
  foomatic-db ttf-baekmuk libgpgme11 libhsqldb-java linux-headers-2.6.17-11 scim-qtimm pmount kwalletmanager libsnmp9 radeontool samba-common ttf-arabeyes kopete libuniconf4.2 cupsys-client
  libservlet2.3-java openoffice.org-base python-elementtree karm kate hotkey-setup kmail libruby1.8 libexif12 mkisofs keep koffice-libs cupsys adept-notifier bogofilter-common libimlib2
  openoffice.org-calc kde-guidance-powermanager ttf-bengali-fonts libjpeg-progs libxp6 min12xxw kde-systemsettings libscrollkeeper0 librsync1 libavahi-core4 freeglut3 libsndfile1 kmousetool
  libnjb5 kmag bluez-pin example-content kdepim-kresources kdepim-wizards kmilo kmplayer-base usplash libpaper1 kaudiocreator enscript python-kde3 hplip-data kdepasswd lftp kmix
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libmeanwhile1
The following packages will be REMOVED:
  kopete
The following NEW packages will be installed:
  libmeanwhile1
0 upgraded, 1 newly installed, 1 to remove and 0 not upgraded.
Need to get 0B/74.1kB of archives.
After unpacking 19.9MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

[Mar 23 07:57 PM][matt@ubuntu:~/Desktop]$

---

### Post by zvacet on 2007-03-24
Maybe I´m wrong but I don´t think you can install Feisty package in Edgy.If you realy need that package upgrade to Feisty beta.
[https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrades%29%7C%28feisty%29]("https://help.ubuntu.com/community/FeistyUpgrades?highlight=%28upgrades%29%7C%28feisty%29")

---

