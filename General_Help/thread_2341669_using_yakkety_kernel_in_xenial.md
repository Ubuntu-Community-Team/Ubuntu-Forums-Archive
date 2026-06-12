---
title: "using yakkety kernel in xenial"
date: 2016-10-30
forum: General Help
---

### Post by asgard2 on 2016-10-30
Hi,

I upgraded my kernel with the yakkety repositories, because if some issues with the 4.4. LTS Kernel.

The 4.8 Kernel from is working without problems, but the I needed to add security repository for the cow kernel fix and the multiverse and universe sources for a compatible virtualbox.

```
/etc/apt/sources.list.d/yakkety.list
deb http://archive.ubuntu.com/ubuntu/ yakkety main
deb http://security.ubuntu.com/ubuntu yakkety-security main restricted
deb http://archive.ubuntu.com/ubuntu/ yakkety multiverse
deb http://archive.ubuntu.com/ubuntu/ yakkety universe

```

```
/etc/apt/preferences.d/yakkety.pref 
Package: *
Pin: release a=yakkety
Pin-Priority: 100


```

At the beginning it worked fine, all the virtualbox and kernel packages and dependencies are upgraded, but for example apt received mysql-common, libmysqlclient20 yakkety upgrades. Now it try to upgrade firefox,  packages from yakkety.

I needed to deactivate these sources, otherwise this will end in mess.

Can I configure the yakkety.pref, that only virtualbox and the kernel packages are upgraded from yakkety?

I know mixing sources is not intended, but the LTS kernel caused too many problems.

After deactivation, this is the current support state:
```

You have 432 packages (17.5%) supported until April 2019 (3y)
You have 1693 packages (68.7%) supported until April 2021 (5y)
You have 57 packages (2.3%) supported until January 2017 (9m)
You have 1 packages (0.0%) supported until October 2021 (5y)

You have 60 packages (2.4%) that can not/no-longer be downloaded
You have 222 packages (9.0%) that are unsupported

No longer downloadable:
libgsoap9 libicu57 libkf5declarative-data libkf5declarative5 
libpng16-16 libqt5clucene5 libqt5core5a libqt5dbus5 libqt5designer5 
libqt5gui5 libqt5help5 libqt5network5 libqt5opengl5 
libqt5printsupport5 libqt5qml5 libqt5quick5 libqt5quickwidgets5 
libqt5script5 libqt5sql5 libqt5sql5-sqlite libqt5svg5 libqt5test5 
libqt5waylandclient5 libqt5webkit5 libqt5widgets5 libqt5x11extras5 
libqt5xml5 libwayland-client0 linux-generic linux-headers-4.8.0-22 
linux-headers-4.8.0-22-generic linux-headers-4.8.0-26 
linux-headers-4.8.0-26-generic linux-headers-generic 
linux-image-4.8.0-22-generic linux-image-4.8.0-26-generic 
linux-image-extra-4.8.0-22-generic linux-image-extra-4.8.0-26-generic 
linux-image-generic linux-libc-dev linux-signed-generic 
linux-signed-image-4.8.0-22-generic 
linux-signed-image-4.8.0-26-generic linux-signed-image-generic 
python3-pyqt5 python3-pyqt5.qtwebkit python3-sip 
qml-module-qtquick-controls qml-module-qtquick-dialogs 
qml-module-qtquick-layouts qml-module-qtquick-privatewidgets 
qml-module-qtquick-window2 qml-module-qtquick2 qtwayland5 virtualbox 
virtualbox-dkms virtualbox-guest-dkms virtualbox-guest-utils 
virtualbox-guest-x11 virtualbox-qt 

Unsupported: 
abiword-plugin-grammar aglfn arandr aspell-de asunder bluefish 
bluefish-data bluefish-plugins conky-all consolekit cpp-4.8 cups-pdf 
curlftpfs davfs2 dia dia-common dia-libs dia-shapes encfs enigmail 
extlinux fdupes filezilla filezilla-common flac fslint gcc-4.8 
gcc-4.8-base gcc-4.9-base gedit-plugins geogebra gfire 
gir1.2-git2-glib-1.0 gmpc gmpc-data gmusicbrowser gnomine gnuplot 
gnuplot-data gnuplot-tex gnuplot-x11 gnuplot5-data gnuplot5-qt 
gsfonts-x11 gstreamer0.10-alsa gstreamer0.10-gnomevfs 
gstreamer0.10-nice gstreamer0.10-plugins-base-apps 
gstreamer0.10-tools gthumb gthumb-data htop indicator-cpufreq ipython 
ipython-doc ipython-notebook ipython-notebook-common 
ipython-qtconsole ipython3 ipython3-notebook ipython3-qtconsole 
java-wrappers javahelp2 junit junit4 keepassx libapache-pom-java 
libarchive-extract-perl libasan0 libaudclient2 libautodie-perl 
libbcmail-java libbcpkix-java libbcprov-java libck-connector0 
libcloog-isl4 libcommons-codec-java libcommons-httpclient-java 
libcommons-logging-java libcommons-math-java libcommons-net-java 
libcommons-parent-java libcompress-raw-bzip2-perl 
libcompress-raw-lzma-perl libcompress-raw-zlib-perl 
libdigest-crc-perl libdom4j-java libextutils-depends-perl 
libextutils-pkgconfig-perl libfarstream-0.1-0 libfilezilla0 
libfreehep-export-java libfreehep-graphics2d-java 
libfreehep-graphicsio-emf-java libfreehep-graphicsio-java 
libfreehep-graphicsio-pdf-java libfreehep-graphicsio-svg-java 
libfreehep-graphicsio-tests-java libfreehep-io-java 
libfreehep-swing-java libfreehep-util-java libfreehep-xml-java 
libgcc-4.8-dev libgdome2-0 libgdome2-cpp-smart0v5 libgit2-glib-1.0-0 
libglib-object-introspection-perl libgnuinet-java libgnumail-java 
libgrip0 libgtk2-notify-perl libgtk2-trayicon-perl libgtkmathview0c2a 
libhamcrest-java libintl-perl libio-compress-lzma-perl 
libio-compress-perl libitext-java libjas-java libjas-plotter-java 
libjaxen-java libjcommon-java libjdom1-java libjfreechart-java 
libjfugue-java libjgoodies-common-java libjgoodies-looks-java 
libjlatexmath-java libjs-highlight libjs-highlight.js libjs-marked 
liblchown-perl liblink-grammar4 liblog-message-perl 
liblog-message-simple-perl liblog4j1.2-java libmodule-pluggable-perl 
libmpd1 libnb-org-openide-util-java 
libnb-org-openide-util-lookup-java libntdb1 libpam-ck-connector 
libpod-latex-perl libreoffice libreoffice-report-builder-bin 
librhino-java librlog5v5 libsexy2 libsub-identify-perl 
libtablelayout-java libterm-ui-perl libtext-soundex-perl 
libvisual-0.4-plugins libxmmsclient6 libxom-java libxpp2-java 
libxpp3-java link-grammar-dictionaries-en lshw-gtk markdown mathpiper 
menu module-init-tools mplayer2 nautilus-image-converter ncdu 
obex-data-server oneconf oneconf-common p7zip p7zip-rar pdfgrep 
pdfsam printer-driver-cups-pdf project-x python-commandnotfound 
python-cups python-cycler python-debtagshw python-matplotlib 
python-ntdb python-oneconf python-pexpect python-pip python-pip-whl 
python-ptyprocess python-renderpm python-reportlab 
python-reportlab-accel python-smbc python-tornado 
python-ubuntu-sso-client python-wheel python-zeitgeist python-zmq 
python3-enchant python3-markdown python3-markups python3-oneconf 
python3-piston-mini-client python3-simplegeneric python3-textile 
python3-zmq redshift retext rsnapshot s-nail software-center 
software-center-aptdaemon-plugins texlive-latex-extra texstudio 
texstudio-doc texstudio-l10n tree ubuntu-sso-client uget unetbootin 
unetbootin-translations wavpack x11-xfs-utils xournal zeitgeist 


```



Thanks for your help.

---

### Post by asgard2 on 2016-11-03
>  Can I configure the yakkety.pref, that only virtualbox and the kernel packages are upgraded from yakkety?


:confused:

---

### Post by asgard2 on 2016-11-07
If it's not possible to configure, what would be the best (secured) configuration with xenial 16.04 LTS and kernel >4.4 ?

---

