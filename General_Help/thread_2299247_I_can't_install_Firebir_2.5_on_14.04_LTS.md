---
title: "I can't install Firebir 2.5 on 14.04 LTS"
date: 2015-10-16
forum: General Help
---

### Post by RafaelOGRANDE431168 on 2015-10-16
Friends, excuse me if this subject has been treated before, most have not found similar question mine and could not reproduce the solutions I found on the web elsewhere.
I have a desktop with Ubuntu 4.14 LTS and tried to install Firebird firebird2.5-classic to use in my study with Pascal Lazarus 1.4.4.

I used the command:

sudo apt-get installfirebird2.5-classic

but the command returns an error message so I tried to force it to reinstall with the command:


sudo apt-get install-f

but I got the following message, saying it lacked several files:


```
dpkg: aviso: faltaficheiro de lista de ficheiros 'libytnef0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libpathplan4'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'friends-dispatcher'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'tk8.6'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libspandsp2'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unity'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libkidletime4'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libavahi-client-dev'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unpaper'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libaio1:i386'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libedataserver-1.2-18'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'account-plugin-facebook'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgtk2.0-cil'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fonts-horai-umefont'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgtop2-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libuuid1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gnome-system-monitor'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libatomic1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxinerama1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libsdl1.2debian:i386'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'evolution-data-server-common';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-wnck'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libwebkitgtk-1.0-0:i386'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros'evolution-data-server-online-accounts'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-tz'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libc6-dbg:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'isc-dhcp-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'eog'; assumindo que o pacote não temactualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libwildmidi-config'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libmpdec2:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libnet-http-perl'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-tk'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'xserver-xorg-video-sis'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gstreamer1.0-pulseaudio:i386';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'desktop-base'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxshmfence1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-dbus'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'signon-plugin-oauth2'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'xcursor-themes'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unity-scope-virtualbox'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxine2-doc'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'lightsoff'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libaccounts-qt5-1'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libogg-dev:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libframe6:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libjs-jquery'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgcrypt11:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libsox-fmt-alsa:i386'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libexif12:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgdbm3:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libkdewebkit5'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'pulseaudio-utils'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libhtml-format-perl'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fonts-liberation'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libcairo2:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxcb-shape0-dev:i386'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'sound-theme-freedesktop'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'myspell-en-au'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libbrasero-media3-1'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fp-units-fv-2.6.2'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'man-db'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libffi6:i386'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libpango-perl'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libenca0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'compiz-plugins-default'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'module-init-tools'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libreoffice-l10n-pt-br'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libflac8:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libvorbis-dev:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gettext-base'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libvorbisfile3:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python3-uno'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libperl5.18'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libpeas-1.0-0'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gnome-user-guide'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libdbus-1-3:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libzvbi-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'cups-ppdc'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libicc2:i386'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libfm-data'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgnome-control-center1'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libssl1.0.0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'desktop-file-utils'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'example-content'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python3-dbus'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gpgv'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'appmenu-qt'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unity-scope-home'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unity-tweak-tool'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'login'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgoocanvas3'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'telnet'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'x11-xkb-utils'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libfarstream-0.1-0:i386'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gstreamer0.10-plugins-base-apps';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxml2:i386'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'laptop-detect'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libimdi0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-uniconvertor'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'p11-kit'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'makedev'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'initramfs-tools'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'x11proto-input-dev'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'openjdk-7-jre-headless:i386';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libprotobuf8:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-twisted-bin'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gdb'; assumindo que o pacote não temactualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgsoap4:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-requests-oauthlib'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libsdl1.2-dev'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'duplicity'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gnome-terminal'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'numix-gtk-theme'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gir1.2-gconf-2.0'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxmuu1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libjpeg8-dev:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libclass-accessor-perl'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libmikmod2-dev:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libportsmf0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxcb-shm0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libwxgtk2.8-0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'samba'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'pulseaudio-module-x11'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gstreamer1.0-plugins-good:i386';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'openprinting-ppds'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gnome-video-effects'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fonts-tlwg-typo'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libtracker-sparql-0.16-0'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 're2c'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'xfonts-mathml'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'printer-driver-pxljr'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'debianutils'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libfreetype6:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python3-aptdaemon.gtk3widgets';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'sudo'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libsane:i386'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gir1.2-secret-1'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxpm-dev:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libmtp-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libzip2'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gstreamer1.0-plugins-bad-faad:i386';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libqt5organizer5:i386'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libva-glx1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'coreutils'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'xserver-xephyr'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'skype'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libsane-hpaio'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'ure'; assumindo que o pacote não temactualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libnl-3-200:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libevview3-3'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libatk1.0-dev'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gnome-robots'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'empathy'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'webbrowser-app'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libavahi-ui-gtk3-0:i386'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libattica0.4:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libaccount-plugin-google'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gvfs-bin'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgl1-mesa-dri:i386'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libjavascriptcoregtk-1.0-0:i386';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libxdmcp6:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libtry-tiny-perl'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libt1-5'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libreoffice-style-human'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'shared-mime-info'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'iproute2'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libthumbnailer0:i386'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libraw1394-11:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'kdelibs5-plugins'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unity-greeter'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fp-units-net-2.6.2'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libpolkit-gobject-1-0:i386';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libpam-cap:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-sip'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unity-settings-daemon'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-six'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgtk-3-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'ibus-gtk3:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libart-2.0-2:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libatspi2.0-0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'jackd'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libsocket6-perl'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libmagickcore5:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'mono-runtime'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'hoichess'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-gnome2'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gimp'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libffado2'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'dash'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libltdl-dev:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgjs0e'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'memtest86+'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libelf1:i386'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libasprintf0c2:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gtk2-engines-murrine:i386'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libpanel-applet-4-0'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-aptdaemon'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'shotwell'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'adwaita-icon-theme-full'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'unity-scope-devhelp'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gir1.2-goa-1.0'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'xserver-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libtbb2'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'debconf'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gnome-screenshot'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libhttp-date-perl'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libio-stringy-perl'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgnomekbd8'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'compiz-plugins-main-default';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libbluray1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'gir1.2-ebookcontacts-1.2'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libjson-glib-1.0-0:i386'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgssdp-1.0-3'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fonts-tlwg-waree'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fonts-kacst'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'ubuntu-restricted-addons'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'liblangtag1'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'apturl-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libpam-winbind:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'hwdata'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libqt5qml-graphicaleffects:i386';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-lxml'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'java-common'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'ubuntu-ui-toolkit-theme'; assumindoque o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'fonts-freefont-ttf'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libustr-1.0-1:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgpod-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'empathy-common'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'sane-utils'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libclutter-1.0-0:i386'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libtext-wrapi18n-perl'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libnotify-bin'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-urllib3'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libbonoboui2-0:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'mac-icons-v3'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python3-aptdaemon.pkcompat';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'linux-image-3.13.0-53-generic';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'deja-dup-backend-gvfs'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'tcpd'; assumindo que o pacote nãotem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'python-pkg-resources'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libgtkspell0'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'ubuntu-release-upgrader-gtk';assumindo que o pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libkfile4'; assumindo que o pacotenão tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'libexempi3:i386'; assumindo que opacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'librygel-server-2.0-1'; assumindo queo pacote não tem actualmente ficheiros instalados
dpkg: aviso: faltaficheiro de lista de ficheiros 'xserver-xorg-input-vmmouse';assumindo que o pacote não tem actualmente ficheiros instalados
(Lendo banco dedados ... 96 ficheiros e directórios actualmente instalados.)
Preparing to unpack.../libfbembed2.5_2.5.2.26540.ds4-9ubuntu1_i386.deb ...
Unpackinglibfbembed2.5 (2.5.2.26540.ds4-9ubuntu1) ...
A seleccionar pacoteanteriormente não seleccionado firebird2.5-classic-common.
Preparing to unpack.../firebird2.5-classic-common_2.5.2.26540.ds4-9ubuntu1_i386.deb ...
Unpackingfirebird2.5-classic-common (2.5.2.26540.ds4-9ubuntu1) ...
Configurandolibfbembed2.5 (2.5.2.26540.ds4-9ubuntu1) ...
Configurandofirebird2.5-classic-common (2.5.2.26540.ds4-9ubuntu1) ...
Configurandofirebird2.5-classic (2.5.2.26540.ds4-9ubuntu1) ...
debconf: DbDriver"config": /var/cache/debconf/config.dat is locked byanother process: Recurso temporariamente indisponível
dpkg: errorprocessing package firebird2.5-classic (--configure):
 sub-processo scriptpost-installation instalado retornou estado de saída de erro 1
Processing triggersfor libc-bin (2.19-0ubuntu6.6) ...
Erros foramencontrados durante o processamento de:
 firebird2.5-classic
E: Sub-process/usr/bin/dpkg returned an error code (1)
:~$  
```

I am seeing it tried to remove the application with the command:


```
sudo apt-get remove--purge firebird2.5-classic
```
but also could not because returning an error message, charging the files and ending like this:


```
Removingfirebird2.5-classic (2.5.2.26540.ds4-9ubuntu1) ...
debconf: DbDriver"config": /var/cache/debconf/config.dat is locked byanother process: Recurso temporariamente indisponível
dpkg: errorprocessing package firebird2.5-classic (--purge):
 sub-processo scriptpre-removal instalado retornou estado de saída de erro 1
debconf: DbDriver"config": /var/cache/debconf/config.dat is locked byanother process: Recurso temporariamente indisponível
dpkg: erro enquantoefetuava a limpeza:
 sub-processo scriptpost-installation instalado retornou estado de saída de erro 1
Erros foramencontrados durante o processamento de:
 firebird2.5-classic
E: Sub-process/usr/bin/dpkg returned an error code (1)
```


I've tried deleting the files in  /var/lib/dpkg/info/*.* but nothing worked.


If someone has a tip on how to solve the problem, so help me please!

---

### Post by blm-ubunet on 2015-10-16
Messing with system files like /var/lib/dpkg/* is a bad idea.

I would make sure the PC has the latest updates first..
Sometimes your problem is caused by dependencies on versions of packages that are not available anymore.

Make sure software-centre is closed/not running
Make sure update-manager is closed.
Make sure synaptic package manager is not running.
Make sure apt-get or aptitude are not running in another terminal or console login..

Then
sudo apt-get autoclean
sudo apt-get update
sudo apt-get upgrade

sudo apt-get dist-upgrade  (optional if you want to upgrade to latest **point** release of 14.04LTS; I would)
sudo apt-get autoremove
sudo apt-get autoclean

---

### Post by Bucky Ball on 2015-10-17
*Thread moved to **General Help**.*

***Installations and Upgrades*** is for issues installing and upgrading the OS.

Please use code tags for terminal posting. Thanks. See the last link in my signature. :)

---

