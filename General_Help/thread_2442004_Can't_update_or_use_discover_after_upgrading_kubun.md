---
title: "Can't update or use discover after upgrading kubuntu to 20.04"
date: 2020-04-28
forum: General Help
---

### Post by luisocla on 2020-04-28
I just upgraded to kubuntu 20.04 and when I run sudo apt upgrade the terminal reads:

```
Calculando la actualización... Hecho
Los siguientes paquetes se han retenido:
  accountwizard akonadi-backend-mysql akonadi-server blender blender-data fwupd fwupd-signed gdal-data gir1.2-freedesktop gir1.2-glib-2.0 gir1.2-pango-1.0 glib-networking glib-networking-services hplip hplip-data kaddressbook kde-config-mailtransport
  kde-style-oxygen-qt5 kdepim-addons kdepim-runtime kdeplasma-addons-data kf5-kdepim-apps-libs-data kf5-messagelib-data kinfocenter kio-gdrive kio-ldap kmail knotes korganizer kubuntu-settings-desktop kwin-addons kwin-common kwin-data kwin-x11 libalgorithm-diff-xs-perl
  libcairo-gobject-perl libcairo-perl libfile-fcntllock-perl libgirepository-1.0-1 libglib-object-introspection-perl libglib-perl libglib2.0-0 libglib2.0-bin libhpmud0 libhtml-parser-perl libhttp-message-perl libimage-magick-q16-perl libkdecorations2-5v5
  libkf5akonadiagentbase5 libkf5akonadicalendar-data libkf5akonadicalendar5abi2 libkf5akonadicontact-data libkf5akonadicontact5abi1 libkf5akonadimime-data libkf5akonadimime5 libkf5akonadiprivate5abi2 libkf5akonadisearch-bin libkf5akonadisearch-plugins
  libkf5akonadisearchcore5 libkf5akonadisearchdebug5 libkf5akonadisearchpim5 libkf5akonadiwidgets5abi1 libkf5alarmcalendar-data libkf5alarmcalendar5abi2 libkf5calendarsupport-data libkf5calendarsupport5abi1 libkf5followupreminder5 libkf5incidenceeditor-bin
  libkf5incidenceeditor-data libkf5incidenceeditor5abi2 libkf5kaddressbookgrantlee5 libkf5kaddressbookimportexport5 libkf5kcmutils-data libkf5kcmutils5 libkf5kdepimdbusinterfaces5 libkf5ldap-data libkf5libkdepim5abi2 libkf5libkdepimakonadi5 libkf5mailcommon5abi4
  libkf5mailimporterakonadi5 libkf5mailtransport-data libkf5mailtransport5abi2 libkf5mailtransportakonadi5 libkf5messagecomposer5abi2 libkf5messagecore5abi2 libkf5messagelist5abi1 libkf5messageviewer5abi5 libkf5mimetreeparser5abi3 libkf5pimcommonakonadi5
  libkf5sendlater5 libkf5templateparser5abi2 libkf5webengineviewer5abi3 libkf5xmlgui-data libkf5xmlgui5 libkpimgapi-data libkpimgapicalendar5 libkpimgapicontacts5 libkpimgapidrive5 libkpimgapitasks5 libkpimimportwizard5 libkpimkdav-data libkwin4-effect-builtins1
  libkwineffects12 libkwinglutils12 libkwinxrenderutils12 liblocale-gettext-perl libnet-dbus-perl libnet-ssleay-perl libpango-1.0-0 libpangocairo-1.0-0 libpangoft2-1.0-0 libpangoxft-1.0-0 libpython2-stdlib libpython3-stdlib libqt5core5a libqt5dbus5 libqt5designer5
  libqt5gui5 libqt5hunspellinputmethod5 libqt5multimedia5 libqt5multimedia5-plugins libqt5multimediagsttools5 libqt5multimediaquick5 libqt5multimediawidgets5 libqt5network5 libqt5networkauth5 libqt5opengl5 libqt5positioning5 libqt5printsupport5 libqt5qml5 libqt5quick5
  libqt5quickcontrols2-5 libqt5quicktemplates2-5 libqt5quickwidgets5 libqt5script5 libqt5sensors5 libqt5sql5 libqt5sql5-mysql libqt5sql5-sqlite libqt5svg5 libqt5test5 libqt5texttospeech5 libqt5virtualkeyboard5 libqt5waylandclient5 libqt5waylandcompositor5
  libqt5webchannel5 libqt5webengine-data libqt5webengine5 libqt5webenginecore5 libqt5webenginewidgets5 libqt5webkit5 libqt5widgets5 libqt5x11extras5 libqt5xml5 libqt5xmlpatterns5 libreoffice-base libreoffice-base-core libreoffice-base-drivers libreoffice-calc
  libreoffice-common libreoffice-core libreoffice-draw libreoffice-help-common libreoffice-help-en-us libreoffice-help-es libreoffice-impress libreoffice-java-common libreoffice-kde5 libreoffice-l10n-es libreoffice-math libreoffice-qt5 libreoffice-sdbc-firebird
  libreoffice-sdbc-hsqldb libreoffice-style-galaxy libreoffice-style-tango libreoffice-writer libsane libsane-common libsane-hpaio libsane1 libsasl2-modules-kdexoauth2 libsmbclient libtalloc2 libtdb1 libtevent0 libtext-charwidth-perl libtext-iconv-perl libwbclient0
  libxml-parser-perl mbox-importer mpd partitionmanager perl perl-base phonon-backend-gstreamer-common phonon4qt5-backend-gstreamer pim-data-exporter plasma-dataengines-addons plasma-desktop plasma-desktop-data plasma-framework plasma-integration plasma-runners-addons
  plasma-wallpapers-addons plasma-widgets-addons plasma-workspace printer-driver-hpcups python-gi python2 python2-minimal python3 python3-apt python3-cairo python3-cffi-backend python3-crypto python3-cups python3-dbus python3-dbus.mainloop.pyqt5 python3-gdbm python3-gi
  python3-ldb python3-minimal python3-netifaces python3-pil python3-pyqt5 python3-renderpm python3-reportlab python3-reportlab-accel python3-samba python3-simplejson python3-sip python3-systemd python3-talloc python3-tdb python3-uno python3-xapian python3-yaml
  qdbus-qt5 qml-module-qtgraphicaleffects qml-module-qtmultimedia qml-module-qtqml-models2 qml-module-qtquick-controls qml-module-qtquick-controls2 qml-module-qtquick-dialogs qml-module-qtquick-layouts qml-module-qtquick-privatewidgets qml-module-qtquick-templates2
  qml-module-qtquick-virtualkeyboard qml-module-qtquick-window2 qml-module-qtquick-xmllistmodel qml-module-qtquick2 qml-module-qtwebengine qml-module-qtwebkit qt5-gtk-platformtheme qt5-image-formats-plugins qtspeech5-flite-plugin qtvirtualkeyboard-plugin qtwayland5
  samba-common samba-common-bin samba-libs scribus scribus-data smbclient systemsettings unattended-upgrades ure virtualbox virtualbox-dkms virtualbox-qt xdg-desktop-portal xdg-desktop-portal-kde
0 actualizados, 0 nuevos se instalarán, 0 para eliminar y 272 no actualizados.
```

When I try to open discover the screen freezes and I can't open it.

edit: I ran sudo apt dist-upgrade and now sudo apt upgrade reads:

```
Leyendo lista de paquetes... Hecho
Creando árbol de dependencias       
Leyendo la información de estado... Hecho
Tal vez quiera ejecutar «apt --fix-broken install» para corregirlo.
Los siguientes paquetes tienen dependencias incumplidas:
 libcairo-gobject-perl : Depende: perlapi-5.30.0
 libglib-object-introspection-perl : Depende: perlapi-5.30.0
 libglib-perl : Depende: perlapi-5.30.0
 libimage-magick-q16-perl : Depende: perlapi-5.30.0
 libnet-dbus-perl : Depende: perlapi-5.30.0
 libnet-ssleay-perl : Depende: perlapi-5.30.0
 libperl5.30 : Depende: perl-modules-5.30 (>= 5.30.0-9build1) pero no está instalado
 libreoffice-base : Depende: libreoffice-common (>= 1:6.4.0~beta1-2~) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
                    Rompe: libreoffice-common (< 1:6.4.2~rc1~) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
 libreoffice-calc : Rompe: libreoffice-common (< 1:6.4.2~rc1~) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
 libreoffice-common : Rompe: libreoffice-core (>= 1:6.4~) pero 1:6.4.2-0ubuntu3 está instalado
                      Rompe: libreoffice-style-galaxy (>= 1:6.4~) pero 1:6.4.2-0ubuntu3 está instalado
                      Rompe: libreoffice-style-tango (>= 1:6.4~) pero 1:6.4.2-0ubuntu3 está instalado
 libreoffice-core : Depende: libreoffice-common (> 1:6.4.2) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
 libreoffice-draw : Rompe: libreoffice-common (< 1:6.4.2~rc1~) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
 libreoffice-impress : Rompe: libreoffice-common (< 1:6.4.2~rc1~) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
 libreoffice-math : Rompe: libreoffice-common (< 1:6.4.2~rc1~) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
 libreoffice-writer : Rompe: libreoffice-common (< 1:6.4.2~rc1~) pero 1:6.3.5-0ubuntu0.19.10.1 está instalado
 libtext-charwidth-perl : Depende: perl-base (>= 5.30.0-8) pero 5.28.1-6build1 está instalado
                          Depende: perlapi-5.30.0
 libtext-iconv-perl : Depende: perl-base (>= 5.30.0-8) pero 5.28.1-6build1 está instalado
                      Depende: perlapi-5.30.0
 libxml-parser-perl : Depende: perlapi-5.30.0
 perl : Depende: perl-base (= 5.30.0-9build1) pero 5.28.1-6build1 está instalado
        Depende: perl-modules-5.30 (>= 5.30.0-9build1) pero no está instalado
 python3 : PreDepende: python3-minimal (= 3.7.5-1) pero 3.8.2-0ubuntu2 está instalado
           Depende: libpython3-stdlib (= 3.7.5-1) pero 3.8.2-0ubuntu2 está instalado
 python3-gi : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-samba : Depende: samba-libs (= 2:4.10.7+dfsg-0ubuntu2.5) pero 2:4.11.6+dfsg-0ubuntu1.1 está instalado
                 Depende: libwbclient0 (= 2:4.10.7+dfsg-0ubuntu2.5) pero 2:4.11.6+dfsg-0ubuntu1.1 está instalado
 python3-simplejson : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-sip : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-systemd : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-talloc : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-tdb : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-uno : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-xapian : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 python3-yaml : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
 samba-libs : Depende: libldb2 (>= 2:2.0.10~) pero no está instalado
 virtualbox : Depende: python3 (>= 3.8~) pero 3.7.5-1 está instalado
E: Dependencias incumplidas. Intente «apt --fix-broken install» sin paquetes (o especifique una solución).
```

---

### Post by CelticWarrior on 2020-04-28
Check the PPAs you still have active before anything else.

---

### Post by luisocla on 2020-04-28
I ran apt --fix-broken install and now I can't even open konsole, i think I will reinstall kubuntu.

---

