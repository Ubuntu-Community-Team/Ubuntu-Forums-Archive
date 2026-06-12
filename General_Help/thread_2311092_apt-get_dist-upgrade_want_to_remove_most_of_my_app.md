---
title: "apt-get dist-upgrade want to remove most of my apps"
date: 2016-01-24
forum: General Help
---

### Post by ivo2 on 2016-01-24
Hi,

I hope there is someone out here who can help me.

I am running ubuntu 14.04. Last week I got a dependency issue when trying to do apt-get dist-upgrade. This was regarding the latest of python3-aptdaemon. After uninstalling it and installing it again, nothing changed. After some tries I installed python3-aptdaemon.pkcompat.

After that I entered aot-get dist-upgrade again (also a new kernel was waiting for me), I entered 'Y' without reading all the text. Now I saw it started to remove a lot of apps. I installed them again manually (really a lot of work), but dist-upgrade still wants to remove all those apps. Of course I aborted.

I tried a lot of things, trying to fix depencencies, remove apt cache and update again but none helped.

```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get clean
sudo apt-get autoclean
sudo apt-get check

```[COLOR=#222222][FONT=Verdana]

I hope someone can help me fix this. I don't like to re-install ubuntu as it is a lot of work getting all my apps and settings correct again.

See below what dist-upgrade wants to remove.

Thanks,
Ivo.

```


```[/FONT][/COLOR]```
xxxxx@xxxxx-desktop:~$ sudo apt-get dist-upgrade
[sudo] password for xxxxx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  apport-symptoms cmake-data dmraid fp-compiler-2.6.2 fp-ide-2.6.2
  fp-units-base-2.6.2 fp-units-db-2.6.2 fp-units-fcl-2.6.2 fp-units-fv-2.6.2
  fp-units-gfx-2.6.2 fp-units-gnome1-2.6.2 fp-units-gtk-2.6.2
  fp-units-gtk2-2.6.2 fp-units-math-2.6.2 fp-units-misc-2.6.2
  fp-units-net-2.6.2 fp-units-rtl-2.6.2 geany-common gedit-common
  gir1.2-javascriptcoregtk-1.0 gir1.2-javascriptcoregtk-3.0 gir1.2-soup-2.4
  gir1.2-wnck-3.0 gnome-common kpartx kpartx-boot liba52-0.7.4-dev
  libasound2-dev libavresample1 libcaca-dev libchromaprint-tools
  libchromaprint0 libconfig-file-perl libdca-dev libdecoration0 libdiscid0
  libdmraid1.0.0.rc16 libdrm-dev libdts-dev libflac-dev libftdi1
  libgl1-mesa-dev libglew1.10 liblircclient0 liblockdev1 libmad0-dev
  libmikmod2 libmikmod2-dev libmirclient-dev libmirprotobuf-dev libmodplug-dev
  libprotobuf-dev libprotobuf-lite8 libpulse-dev libqscintilla2-l10n
  libregexp-assemble-perl libroman-perl libsoup2.4-dev libtext-format-perl
  libts-dev libx11-xcb-dev libxcb-dri2-0-dev libxcb-dri3-dev libxcb-glx0-dev
  libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-present-dev libxcb-randr0
  libxcb-randr0-dev libxcb-render-util0 libxcb-shape0-dev libxcb-sync-dev
  libxcb-xfixes0-dev libxcb-xkb1 libxkbcommon-x11-0 libxshmfence-dev
  libxss-dev libxv-dev libxxf86vm-dev mesa-common-dev mircommon-dev
  python-bluez python-defer python-imaging python-lxml python-mutagen
  python-pycurl python-sip python3-chardet python3-debian python3-packagekit
  python3-problem-report python3-six qtcore4-l10n setserial sqlite3
  sqliteman-doc ttf-dejavu-core ttf-liberation x11proto-dri2-dev
  x11proto-gl-dev x11proto-scrnsaver-dev x11proto-video-dev
  x11proto-xf86vidmode-dev
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  acpitool apport apport-gtk apt-file apt-transport-https apt-utils aptdaemon
  bum chromium-browser chromium-browser-l10n cmake compiz-core
  compiz-plugins-default cups cups-core-drivers cups-filters
  cups-filters-core-drivers cups-ppdc debiandoc-sgml devhelp docbook-to-man
  docbook-utils doxygen enchant flashplugin-installer
  fp-units-multimedia-2.6.2 fpc fpc-2.6.2 gdebi-core gdisk geany gedit
  germinate gimp gir1.2-webkit-1.0 gir1.2-webkit-3.0 git-cola
  gnome-control-center gnome-media gnome-user-guide google-chrome-stable
  gparted gperf grub-customizer gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-good gstreamer0.10-plugins-ugly gstreamer1.0-clutter
  gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gtk-doc-tools
  icu-devtools jade jadetex kodi kodi-bin kodi-pvr-hts libapt-inst1.5
  libapt-pkg-perl libatkmm-1.6-1 libatkmm-1.6-dev libboost-system1.54-dev
  libboost-thread-dev libboost-thread1.54-dev libboost-thread1.54.0
  libcairomm-1.0-1 libcairomm-1.0-dev libcec-dev libcec3 libcheese-gtk23
  libcheese7 libcholmod2.1.2 libclutter-1.0-0 libclutter-gst-2.0-0
  libclutter-gtk-1.0-0 libcogl-pango15 libcogl15 libcompizconfig0 libcupsppdc1
  libcurl4-gnutls-dev libdevhelp-3-2 libdirac-encoder0 libegl1-mesa
  libegl1-mesa-dev libegl1-mesa-drivers libenchant-dev libenchant1c2a
  libept1.4.12 libexempi3 libfluidsynth1 libgbm1 libgegl-0.2-0 libgegl-dev
  libgfortran3 libgles2-mesa-dev libglew-dev libglibmm-2.4-1c2a
  libglibmm-2.4-dev libglu1-mesa libglu1-mesa-dev libgme0 libgmp-dev
  libgmpxx4ldbl libgoa-backend-1.0-1 libgtkmm-2.4-1c2a libgtkmm-2.4-dev
  libgtkmm-3.0-1 libhunspell-1.3-0 libicu-dev libilmbase6 libjack-jackd2-0
  libjavascriptcoregtk-1.0-0 libjavascriptcoregtk-1.0-dev
  libjavascriptcoregtk-3.0-0 liblapack3 libmediainfo0 libofa0 libopenexr6
  libostyle1c2 libpangomm-1.4-1 libpangomm-1.4-dev libplatform-dev
  libplatform1 libportaudio2 libqpdf13 libqscintilla2-11 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-test libqt4-xml libqt4-xmlpatterns
  libqt5concurrent5 libqt5core5a libqt5dbus5 libqt5gui5 libqt5multimedia5
  libqt5multimediawidgets5 libqt5network5 libqt5opengl5
  libqt5qml-graphicaleffects libqt5qml5 libqt5script5 libqt5sql5
  libqt5sql5-sqlite libqt5widgets5 libqt5xml5 libqtassistantclient4 libqtcore4
  libqtdbus4 libqtgui4 libqtwebkit4 librarian0 librtmp-dev libsdl-mixer1.2
  libsdl-mixer1.2-dev libsdl1.2-dev libsdl2-2.0-0 libsdl2-dev libsidplay1
  libsigc++-2.0-0c2a libsigc++-2.0-dev libsoundtouch0 libsp1c2 libtinyxml-dev
  libtinyxml2-0.0.0 libtinyxml2.6.2 libumfpack5.6.2 libwayland-egl1-mesa
  libwebkitgtk-1.0-0 libwebkitgtk-3.0-0 libwebkitgtk-dev libwxbase2.8-0
  libwxgtk-media2.8-0 libwxgtk2.8-0 libxapian22 libyelp0 libzen0 lintian lirc
  lshw mediaelch menu mesa-vdpau-drivers metacity nautilus nettle-dev
  nvidia-304 openjade p7zip-full packagekit-backend-aptcc packagekit-tools
  picard po4a printer-driver-gutenprint pyqt4-dev-tools python-apt
  python-aptdaemon python-aptdaemon.gtk3widgets python-compizconfig python-qt4
  python-software-properties python-wxgtk2.8 python-wxtools python3-apport
  python3-apt python3-aptdaemon python3-aptdaemon.gtk3widgets
  python3-aptdaemon.pkcompat python3-distupgrade python3-germinate
  python3-software-properties python3-update-manager qdbus qpdf qtchooser
  rarian-compat software-properties-common software-properties-gtk sp
  sqliteman swig swig2.0 synaptic system-config-printer-gnome
  texlive-latex-recommended tipa toshset ubuntu-drivers-common ubuntu-minimal
  ubuntu-release-upgrader-core ubuntu-release-upgrader-gtk
  ubuntu-system-service ubuntu-tweak unattended-upgrades unrar update-manager
  update-manager-core update-notifier update-notifier-common vdpauinfo
  vnc4server xbmc xbmc-pvr-tvheadend-hts xorg yelp zeitgeist zeitgeist-core
  zeitgeist-datahub zenity
The following NEW packages will be installed:
  openjade1.3
The following packages have been kept back:
  gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386
0 upgraded, 1 newly installed, 259 to remove and 5 not upgraded.
Need to get 500 kB of archives.
After this operation, 1,302 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.


[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]
```[COLOR=#222222][FONT=Verdana]
[/FONT][/COLOR]

---

### Post by ian-weisser on 2016-01-24
Reinstalling won't help.
Your system isn't corrupted nor damaged.
You, the admin, told your system to install packages that conflict with the rest of your system. Your system is faithfully trying to obey.
You must resolve that conflict. Random apt incantations won't help until you fix your instructions to the system.
If you reinstall, you seem likely to merely reproduce the problem.

Look back through your /var/log/apt/term.log* logs and see if you can figure out exactly which packages caused the version conflict.
Uninstall those packages. Disable the source they came from. That source is not your friend anymore.

This is a moderately common issue that pops up with users who install a lot of PPAs and other non-Ubuntu software, especially on older releases of Ubuntu.
If you are one such user, and this is your first time deconfliting...then take notes, it may not be your last.

---

### Post by grahammechanical on 2016-01-24
You have discovered why it is not always advisable to use dist-upgrade. It will resolve package conflicts by removing packages. The command apt-get dist-upgrade will bring in packages that are held back. These packages are held back for a reason. Perhaps they are dependent on other packages that are not yet in the update channel.

Updating through Update Manager will not do this and neither will the apt-get update & apt-get upgrade commands.

Regards.

---

