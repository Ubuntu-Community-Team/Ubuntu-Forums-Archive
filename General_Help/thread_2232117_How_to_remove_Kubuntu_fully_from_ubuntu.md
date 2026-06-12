---
title: "How to remove Kubuntu fully from ubuntu?"
date: 2014-06-29
forum: General Help
---

### Post by Lafci on 2014-06-29
Hello title says much but i will give more info

Well first i thought why not give kde another try ?

```
Sudo apt-get install kubuntu-desktop
```

after few minutes in kde environment , i wanted to switch back to unity 
That succeeded but the apps are still remaining like amarok and alot others
I would like to fully remove kubuntu from ubuntu :).
Very little info i found on internet
How do i remove it fully?

I am using ubuntu 14.04

Thanks in advance

UPDATE

[http://askubuntu.com/questions/451620/how-to-completely-remove-kubuntu-desktop-from-ubuntu](http://askubuntu.com/questions/451620/how-to-completely-remove-kubuntu-desktop-from-ubuntu)

---

### Post by oldos2er on 2014-06-30
```
sudo apt-get remove kubuntu-desktop && sudo apt-get autoremove
```

---

### Post by HermanAB on 2014-07-01
That is a bit like unscrambling an egg.  Don't be too surprised if some things are ****-eyed after trying to uninstall KDE.

---

### Post by kaim4u-6 on 2014-07-02
Lafci

Run the following command



```

sudo aptitude purge kde-telepathy-minimal:amd64 libkde3support4:amd64 k3b-data:amd64 ntrack-module-libnl-0:amd64 libkrosscore4:amd64 libgpgme++2:amd64   libqapt2:amd64 oxygen-icon-theme:amd64 libktexteditor4:amd64   libtaskmanager4abi5:amd64   kdenetwork-filesharing:amd64   kdelibs5-data:amd64   libkblog4:amd64 libchm1:amd64 plasma-widgets-addons:amd64 libmuonprivate2:amd64 libkimap4:amd64 plasma-netbook:amd64   libnepomukcleaner4:amd64  libkdeui5:amd64 libkdeclarative5:amd64  ttf-oxygen-font-family:amd64 kde-base-artwork:amd64   gtk3-engines-oxygen:amd64   freerdp-x11:amd64   user-manager:amd64 libksieve4:amd64   gpgsm:amd64   kwalletmanager:amd64   mysql-server-core-5.5:amd64 quassel:amd64   libthreadweaver4:amd64   libakonadi-kcal4:amd64   kdepim-kresources:amd64   phonon-backend-gstreamer:amd64  ark:amd64   kmail:amd64   libokularcore4:amd64   libruby1.9.1:amd64  plymouth-theme-kubuntu-logo:amd64 ksysguard:amd64 libqt4-sql-mysql:amd64  libmailtransport4:amd64   kde-telepathy-filetransfer-handler:amd64   kde-zeroconf:amd64   akonadi-backend-mysql:amd64   libkpimtextedit4:amd64   libaio1:amd64   konsole:amd64   kde-runtime:amd64   mysql-client-core-5.5:amd64    liblastfm1:amd64   libqjson0:amd64   libtag-extras1:amd64   libkdecorations4abi1:amd64   libkdcraw23:amd64   libkpeople3:amd64   kdepimlibs-kio-plugins:amd64   libqrencode3:amd64   libkparts4:amd64   libakonadiprotocolinternals1:amd64   libbalooxapian4:amd64   akonadi-server:amd64   nepomuk-core-data:amd64   libqca2:amd64   kubuntu-notification-helper:amd64    kdemultimedia-kio-plugins:amd64   libntrack0:amd64    kde-runtime-data:amd64   libphonon4:amd64   cdparanoia:amd64    libplasma-geolocation-interface4:amd64   quassel-data:amd64   libkemoticons4:amd64   libmessagecomposer4:amd64   libweather-ion6:amd64   cdrdao:amd64   libibus-qt1:amd64   libnepomukquery4a:amd64   bluedevil:amd64    kde-telepathy-desktop-applets:amd64   liblightdm-qt-3-0:amd64   libzip2:amd64   libakonadi-notes4:amd64   libkmediaplayer4:amd64   libksieveui4:amd64   muon-discover:amd64    libeventviews4:amd64   libmicroblog4:amd64   libnetworkmanagerqt1:amd64    libqt4-qt3support:amd64    libkcddb4:amd64   amarok-utils:amd64   libmailcommon4:amd64   libktpcommoninternalsprivate7:amd64   libprocessui4a:amd64   katepart:amd64   libmusicbrainz5-0:amd64   libkwineffects1abi4:amd64   libreoffice-base:amd64   consolekit:amd64    libkdepim4:amd64   kaddressbook:amd64   libkdnssd4:amd64   soprano-daemon:amd64    phonon:amd64   libmessageviewer4:amd64   libkwinglesutils1:amd64   libsoprano4:amd64    libqapt2-runtime:amd64    vcdimager:amd64    libcln6:amd64   libvirtodbc0:amd64    libbaloopim4:amd64   okular:amd64   libkatepartinterfaces4:amd64   libqca2-plugin-ossl:amd64    libkonq5abi1:amd64   ubuntu-release-upgrader-qt:amd64    python3-pyqt4:amd64    libkephal4abi1:amd64   libksba8:amd64   kdesudo:amd64    libqoauth1:amd64   gnupg-agent:amd64   libkscreensaver5:amd64   libxerces-c3.1:amd64   kde-telepathy-data:amd64   kdelibs5-plugins:amd64   phonon-backend-gstreamer-common:amd64    kcalc:amd64   cryptsetup-bin:amd64   libqmobipocket1:amd64   systemsettings:amd64   libilmbase6:amd64   libkolabxml1:amd64   libsyndication4:amd64   libkjsapi4:amd64   libplasmagenericshell4:amd64   libksane0:amd64   libkprintutils4:amd64   knotes:amd64   scdaemon:amd64   libkactivities6:amd64   libincidenceeditorsng4:amd64   lightdm-kde-greeter:amd64    libreoffice-sdbc-firebird:amd64   kubuntu-docs:amd64    libk3b6:amd64   amarok:amd64   kde-telepathy-contact-list:amd64   kubuntu-desktop:amd64    ruby:amd64    gwenview:amd64   libcalendarsupport4:amd64   libkcalcore4:amd64   virtuoso-opensource-6.1-common:amd64    libkmbox4:amd64   virtuoso-opensource-6.1-bin:amd64    libakonadi-contact4:amd64   libakonadi-socialutils4:amd64   plasma-widget-kimpanel:amd64   muon-notifier:amd64    libkholidays4:amd64   kde-touchpad:amd64    virtuoso-minimal:amd64    python3-dbus.mainloop.qt:amd64    libqtscript4-gui:amd64   python3-pykde4:amd64   plasma-widget-menubar:amd64   libxcb-record0:amd64   libkcompactdisc4:amd64   kde-config-telepathy-accounts:amd64   plasma-widget-folderview:amd64   kio-audiocd:amd64   libkabc4:amd64   libkunitconversion4:amd64   okular-extra-backends:amd64   kde-telepathy-auth-handler:amd64   plasma-runner-telepathy-contact:amd64   libkwinglutils1abi3:amd64   plymouth-theme-kubuntu-text:amd64    libqimageblitz4:amd64   libcryptsetup4:amd64   ktorrent-data:amd64   libknewstuff3-4:amd64   kde-workspace-kgreet-plugins:amd64   kde-config-tablet:amd64   kde-window-manager:amd64   libbaloowidgets4:amd64   gstreamer0.10-qapt:amd64    kmenuedit:amd64   akregator:amd64   plasma-widgets-workspace:amd64   libxcb-xtest0:amd64   libnepomukutils4:amd64   odbcinst1debian2:amd64    kate:amd64   libkresources4:amd64   libkmanagesieve4:amd64   libprocesscore4abi1:amd64   libqtscript4-network:amd64   libksane-data:amd64   ibus-qt4:amd64   kdoctools:amd64   sgml-data:amd64   libyaml-0-2:amd64   libkxmlrpcclient4:amd64   plasma-nm:amd64    apturl-kde:amd64    libkpty4:amd64   libpam-ck-connector:amd64    libqgpgme1:amd64   print-manager:amd64   libkjsembed4:amd64   libksignalplotter4:amd64   libkipi-data:amd64   klipper:amd64   libakonadi-kmime4:amd64   gtk2-engines-oxygen:amd64   korganizer:amd64   kde-telepathy-text-ui:amd64   libsolid4:amd64   libkhtml5:amd64   libkcal4:amd64   libkmime4:amd64   ksysguardd:amd64   kontact:amd64   kde-workspace-bin:amd64   libmailimporter4:amd64   libakonadi-calendar4:amd64   libprison0:amd64    libsendlater4:amd64   libntrack-qt4-1:amd64    libsignon-qt1:amd64    libkldap4:amd64   libkfile4:amd64   kubuntu-settings-desktop:amd64    kde-telepathy-approver:amd64   libkonq-common:amd64   libpoppler-qt4-4:amd64   kamera:amd64   libbaloofiles4:amd64   libtelepathy-qt4-2:amd64   libnoteshared4:amd64   libakonadi-kde4:amd64   libreoffice-kde:amd64   plasma-dataengines-workspace:amd64   mysql-common:amd64    icoutils:amd64   libgrantlee-gui0:amd64   socat:amd64    libkdepimdbusinterfaces4:amd64   audiocd-kio:amd64   apport-kde:amd64    kio-mtp:amd64    ksystemlog:amd64   libboost-program-options1.54.0:amd64   libmodemmanagerqt1:amd64   liboath0:amd64   libmessagecore4:amd64   libqtglib-2.0-0:amd64   kde-baseapps-bin:amd64   kde-window-manager-common:amd64   kubuntu-driver-manager:amd64    libattica0.4:amd64   libmygpo-qt1:amd64   libkdesu5:amd64   libknewstuff2-4:amd64   dragonplayer:amd64   libnepomukcore4abi1:amd64   libmysqlclient18:amd64    libdlrestrictions1:amd64    libgps20:amd64   kde-telepathy-send-file:amd64   libstreams0:amd64   libkidletime4:amd64   libkateinterfaces4:amd64   libknotifyconfig4:amd64   qapt-deb-installer:amd64    plasma-dataengines-addons:amd64   libtemplateparser4:amd64   docbook-xml:amd64   about-distro:amd64   polkit-kde-1:amd64   libindicate-qt1:amd64    dolphin:amd64   libbluedevil1:amd64    kinfocenter:amd64   libplasmaclock4abi4:amd64   amarok-common:amd64   kaccessible:amd64   libreoffice-sdbc-hsqldb:amd64   libqtscript4-uitools:amd64   libkcalutils4:amd64   libreoffice-java-common:amd64   libopenexr6:amd64   usb-creator-kde:amd64    libbaloocore4:amd64   libkdecore5:amd64   kdelibs-bin:amd64   plasma-desktop:amd64   skanlite:amd64   libkactivities-bin:amd64   kmag:amd64   libindicate5:amd64   kdegraphics-strigi-analyzer:amd64   libdmtx0a:amd64   nepomuk-core-runtime:amd64   plasma-scriptengine-javascript:amd64   libperl4-corelibs-perl:amd64   qapt-batch:amd64    kde-wallpapers-default:amd64   libloudmouth1-0:amd64   libqaccessibilityclient0:amd64    libktnef4:amd64   libflac++6:amd64   libnepomuk4:amd64   libkleo4:amd64   odbcinst:amd64    pam-kwallet:amd64    kde-workspace:amd64   libqalculate5-data:amd64   libstreamanalyzer0:amd64   libkdcraw-data:amd64   docbook-xsl:amd64    libkntlm4:amd64   libopenconnect2:amd64   software-properties-kde:amd64    pinentry-gtk2:amd64   ktorrent:amd64   gnupg2:amd64   krdc:amd64   libksgrd4:amd64   kmousetool:amd64   kde-baseapps-data:amd64   kde-workspace-data:amd64   libqtscript4-core:amd64   partitionmanager:amd64   libkdewebkit5:amd64   cryptsetup:amd64   kscreen:amd64    libpimactivity4:amd64   libboost-thread1.54.0:amd64   libkfbapi1:amd64   libxcb-damage0:amd64   ruby1.9.1:amd64    libkcmutils4:amd64   libkpimidentities4:amd64   libreoffice-style-oxygen:amd64   k3b:amd64   libkipi11:amd64   libkworkspace4abi2:amd64   colord-kde:amd64   libkfilemetadata4:amd64   kde-style-oxygen:amd64   libdebconf-kde0:amd64   libktorrent-l10n:amd64   libpolkit-qt-1-1:amd64   libkolab0:amd64   libepub0:amd64   libkdgantt2-0:amd64   kubuntu-settings-netbook:amd64    libhsqldb1.8.0-java:amd64    libqtscript4-xml:amd64   kubuntu-web-shortcuts:amd64    libpth20:amd64   libtelepathy-logger-qt4-1:amd64   libkactivities-models1:amd64   libkpimutils4:amd64   libck-connector0:amd64    freespacenotifier:amd64   pinentry-qt4:amd64   kde-config-gtk-style:amd64   libkalarmcal2:amd64   libkgapi2-2:amd64   baloo:amd64   libkubuntu0:amd64    python3-sip:amd64   kmix:amd64   libqalculate5:amd64   libkio5:amd64   libxml2-utils:amd64    ksnapshot:amd64   kate-data:amd64   libktorrent5:amd64   libakonadi-kabc4:amd64   phonon-backend-gstreamer1.0:amd64    libpimcommon4:amd64   kde-config-whoopsie:amd64    libreoffice-base-drivers:amd64   libkpgp4:amd64   khelpcenter4:amd64   kubuntu-debug-installer:amd64    oxygen-cursor-theme:amd64    shared-desktop-ontologies:amd64   libkexiv2-data:amd64   libplasma3:amd64   muon-updater:amd64    kde-config-pimactivity:amd64   kde-telepathy:amd64    kde-telepathy-declarative:amd64   libaccounts-qt1:amd64    kdepasswd:amd64   libkonq5-templates:amd64   libqtscript4-sql:amd64   libkexiv2-11:amd64   libkontactinterface4:amd64   libmessagelist4:amd64   kde-telepathy-integration-module:amd64   libgrantlee-core0:amd64   kdepim-runtime:amd64   libkscreen1:amd64
```
[B]
Note : Use this only for Ubunut 14.04 (amd64) [/B]
In case you have 32-bit version of ubuntu installed then use i386 instead of amd64 after  **:**

Instead of aptitude apt-get can be used

**This command will revert all the changes made by  'sudo aptitude install kubuntu-desktop' **

---

