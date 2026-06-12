---
title: "apt-get dist-upgrade wants to remove 1/2 my system"
date: 2018-01-04
forum: General Help
---

### Post by pqwoerituytrueiwoq on 2018-01-04
I am running xubuntu 14.04 64bit
I decided to check my updates and saw this, well this is not right
any idea why it wants to remove all GUI software?
```
sudo apt-get dist-upgrade 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  audacity-data avidemux-common blender-data brasero-common
  ca-certificates-java default-jre default-jre-headless dvd+rw-tools dvdauthor
  easymp3gain-data extremetuxracer-data extremetuxracer-extras finger
  fonts-sil-gentium fonts-sil-gentium-basic fonts-wqy-zenhei geany-common
  gir1.2-keybinder-3.0 gir1.2-udisks-2.0 glmark2-data gnuchess gnuchess-book
  growisofs gstreamer1.0-pulseaudio hedgewars-data java-common lame
  libaccounts-glib0 libaften0 liballegro4.4 liballegro4.4-plugin-alsa libalut0
  libassuan0 libatk-wrapper-java libatk-wrapper-java-jni libavutil-extra-51
  libcddb2 libcolumbus1-common libdvbpsi8 libenet2a libevent-core-2.0-5
  libevent-pthreads-2.0-5 libexttextcat-2.0-0 libexttextcat-data libfaac0
  libffi6:i386 libfreerdp1 libgee-0.8-2 libglee0d1 libgles1-mesa libglew1.10
  libglewmx1.10 libgmime-2.6-0 libgnome-media-profiles-3.0-0
  libgoocanvas-common libgoocanvas3 libgpgme11 libhsqldb1.8.0-java libhud2
  libhyphen0 libiso9660-8 libkeybinder-3.0-0 liblangtag-common liblangtag1
  liblavfile-2.1-0 liblavjpeg-2.1-0 liblavplay-2.1-0 liblept4 liblua5.2-0
  libmjpegutils-2.1-0 libmlt-data libneon27-gnutls libphysfs1 libpocketsphinx1
  libpolarssl5 libpostproc52 libproxy-tools libqrencode3 libquicktime2
  libquvi-scripts libquvi7 libreoffice-style-galaxy libreoffice-style-human
  libsdl-image1.2 libsdl-mixer1.2 libsdl-net1.2 libsdl-ttf2.0-0
  libservlet3.0-java libsox-fmt-alsa libsox-fmt-base libsox2 libsphinxbase1
  libspnav0 libssh2-1 libtotem-plparser18 libupnp6 libusageenvironment1
  libvamp-hostsdk3 libvcdinfo0 libvlc5 libvlccore8 libvncclient0 libx264-123
  libxcb-composite0 libxcb-icccm4 libxcb-image0 libxcb-keysyms1 libxcb-randr0
  libxcb-render-util0 libxcb-xv0 libzzip-0-13 mencoder nvidia-375
  nvidia-opencl-icd-375 openjdk-7-jre openjdk-7-jre-headless
  owncloud-client-l10n psensor-common python-gnome2 python-gst0.10
  python-keyring python-launchpadlib python-lazr.restfulclient python-lazr.uri
  python-netifaces python-oauth python-problem-report python-psutil
  python-pygoocanvas python-pyorbit python-secretstorage python-simplejson
  python-wadllib python3-chardet python3-debian python3-sip python3-six
  qtdeclarative5-ubuntu-ui-extras-browser-plugin-assets realpath smc-data
  sphinx-voxforge-hmm-en sphinx-voxforge-lm-en supertuxkart-data
  syslinux-legacy tesseract-ocr-eng tesseract-ocr-equ tesseract-ocr-osd
  ttf-wqy-zenhei twolame tzdata-java ubuntu-ui-toolkit-theme
  usb-creator-common vcdimager vlc-data vorbisgain xfonts-mathml
  xul-ext-calendar-timezones
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  adobe-flash-properties-gtk adobe-flashplugin apport apport-gtk
  apt-transport-https apt-utils apt-xapian-index aptdaemon aptitude audacity
  audio-recorder avidemux avidemux-plugins-common avidemux-plugins-gtk
  bitcoin-qt bleachbit blender bluez-cups brasero brasero-cdrkit brltty
  brltty-x11 browser-plugin-freshplayer-pepperflash bum cairo-dock
  cairo-dock-core cairo-dock-plug-ins
  cairo-dock-plug-ins-dbus-interface-python cairo-dock-plug-ins-integration
  chrome-remote-desktop chromium-browser chromium-browser-l10n
  command-not-found cpp-4.7 cups cups-filters cups-pdf cups-ppdc devede
  dolphin-emu-master dupeguru easymp3gain-gtk emulationstation enchant evince
  extremetuxracer extundelete ffmpeg firefox frei0r-plugins gcc-4.6 gcc-4.7
  gdebi gdebi-core gdisk geany geany-plugin-spellcheck
  geany-plugin-treebrowser geany-plugin-webhelper geany-plugins-common geary
  gimp gimp-help-en gir1.2-dee-1.0 gir1.2-unity-5.0 gir1.2-webkit-3.0 glchess
  glmark2 gnome-chess gnome-control-center gnome-nettool gnucap
  google-talkplugin gparted gsmartcontrol gstreamer0.10-plugins-bad
  gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-good
  gstreamer0.10-plugins-ugly gstreamer1.0-libde265 gstreamer1.0-plugins-bad
  gstreamer1.0-plugins-good gstreamer1.0-plugins-ugly gthumb gthumb-data gufw
  handbrake-gtk hedgewars hplip hud ibus-pinyin icedtea-7-jre-jamvm iperf
  jackd jackd2 jackd2-firewire kazam landscape-common language-selector-common
  language-selector-gnome libaccounts-qt5-1 libapt-inst1.5 libapt-pkg-perl
  libatkmm-1.6-1 libav-tools libavcodec-extra-53 libavfilter5
  libavformat-extra-53 libavidemux0 libbasicusageenvironment0
  libboost-date-time1.54.0 libboost-filesystem1.53.0 libboost-filesystem1.54.0
  libboost-iostreams1.54.0 libboost-locale1.54.0
  libboost-program-options1.53.0 libboost-regex1.54.0 libboost-system1.53.0
  libboost-system1.54.0 libboost-thread1.53.0 libboost-thread1.54.0
  libbrasero-media3-1 libcairomm-1.0-1 libcdr-0.0-0 libcegui-mk2-0.7.6
  libcheese-gtk23 libcheese7 libcholmod2.1.2 libchromaprint0 libcloog-ppl1
  libclucene-contribs1 libclucene-core1 libcmis-0.4-4 libcolumbus1
  libconfig++9 libcupsppdc1 libcwidget3 libdb5.1++ libdbusmenu-qt5 libde265
  libdee-1.0-4 libdevil1c2 libdirac-encoder0 libdjvulibre21 libebml4
  libept1.4.12 libevdocument3-4 libevview3-3 libexiv2-12 libfarstream-0.1-0
  libffado2 libffmpegthumbnailer4 libflac++6 libframe6 libfreeimage3
  libgcc-4.7-dev libgdome2-cpp-smart0c2a libgegl-0.2-0 libgeis1 libgfortran3
  libglc0 libgldi3 libgle3 libglibmm-2.4-1c2a libglu1-mesa libgmpxx4ldbl
  libgrail6 libgrip0 libgroupsock1 libgsettings-qt1 libgsoap3 libgsoap4
  libgtkglext1 libgtkmm-2.4-1c2a libgtkmm-3.0-1 libicu48 libilmbase6
  libjack-jackd2-0 libjavascriptcoregtk-1.0-0 liblapack3 liblinear-tools
  liblinear1 liblivemedia23 libllvm3.2 libllvm3.5 libllvm3.5:i386
  libllvm3.6:i386 libmagickcore5-extra libmatroska6 libmlt++3 libmlt6
  libmpeg2encpp-2.1-0 libmplex2-2.1-0 libmspub-0.0-0 libmythes-1.2-0 libofa0
  libogre-1.8.0 libois-1.3.0 libopencolorio1 libopencv-calib3d2.4
  libopencv-contrib2.4 libopencv-core2.4 libopencv-features2d2.4
  libopencv-flann2.4 libopencv-highgui2.4 libopencv-imgproc2.4
  libopencv-legacy2.4 libopencv-ml2.4 libopencv-objdetect2.4
  libopencv-video2.4 libopenexr6 libopenimageio1.3 libopenraw1
  libopenrawgnome1 liborcus-0.6-0 libowncloudsync0 liboxideqt-qmlplugin
  liboxideqtcore0 liboxideqtquick0 libpangomm-1.4-1 libportsmf0 libppl-c4
  libppl12 libppl13 libpurple0 libpyzy-1.0-0 libqpdf10 libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-network libqt4-opengl
  libqt4-qt3support libqt4-script libqt4-sql libqt4-sql-mysql
  libqt4-sql-sqlite libqt4-svg libqt4-xml libqt4-xmlpatterns libqt5clucene5
  libqt5core5a libqt5dbus5 libqt5designer5 libqt5feedback5 libqt5gui5
  libqt5help5 libqt5multimedia5 libqt5network5 libqt5opengl5 libqt5organizer5
  libqt5positioning5 libqt5printsupport5 libqt5qml-graphicaleffects libqt5qml5
  libqt5quick5 libqt5sensors5 libqt5sql5 libqt5sql5-sqlite libqt5svg5
  libqt5test5 libqt5webkit5 libqt5webkit5-qmlwebkitplugin libqt5widgets5
  libqt5xml5 libqtcore4 libqtdbus4 libqtgui4 libqtkeychain0 libqtwebkit4
  librarian0 libraw9 libreoffice libreoffice-avmedia-backend-gstreamer
  libreoffice-base libreoffice-base-core libreoffice-base-drivers
  libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw
  libreoffice-gnome libreoffice-gtk libreoffice-impress
  libreoffice-java-common libreoffice-math libreoffice-pdfimport
  libreoffice-report-builder-bin libreoffice-sdbc-firebird
  libreoffice-sdbc-hsqldb libreoffice-writer libresid-builder0c2a libsbsms10
  libsfml-network2 libsfml-system2 libsidplay1 libsidplay2 libsigc++-2.0-0c2a
  libsignon-qt5-1 libsilly libsoundtouch0 libstdc++6:i386 libtagc0 libtbb2
  libtesseract3 libthumbnailer0 libtinyxml2.6.2 libumfpack5.6.2
  libunity-action-qt1 libunity-protocol-private0 libunity-webapps0 libunity9
  libunityvoice1 libvisio-0.0-0 libvisual-0.4-plugins libwebkit2gtk-3.0-25
  libwebkitgtk-1.0-0 libwpd-0.9-9 libwpg-0.2-2 libwps-0.2-2 libwxbase2.8-0
  libwxbase3.0-0 libwxgtk2.8-0 libwxgtk3.0-0 libxapian22 libxatracker1
  libxerces-c3.1 libxml++2.6-2 libyaml-cpp0.3 libzimg2 lintian love lshw melt
  menu mjpegtools mjpegtools-gtk mkvtoolnix mkvtoolnix-gui mp3gain nmap
  onboard onboard-data oneconf oneconf-common openshot openshot-doc
  owncloud-client p7zip-full parole partimage pavucontrol pidgin
  pidgin-libnotify pidgin-microblog printer-driver-gutenprint
  printer-driver-hpcups printer-driver-postscript-hp printer-driver-pxljr
  printer-driver-splix psensor python-apport python-apt python-aptdaemon
  python-aptdaemon.gtk3widgets python-commandnotfound python-mlt
  python-oneconf python-qt4-dbus python-xapian python3-apport python3-apt
  python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat
  python3-commandnotfound python3-distupgrade python3-oneconf python3-pyqt5
  python3-software-properties python3-uno python3-update-manager qdbus
  qjackctl qjoypad qpdf qtchooser qtdeclarative5-accounts-plugin
  qtdeclarative5-dialogs-plugin qtdeclarative5-privatewidgets-plugin
  qtdeclarative5-qtfeedback-plugin qtdeclarative5-qtquick2-plugin
  qtdeclarative5-ubuntu-ui-extras-browser-plugin
  qtdeclarative5-ubuntu-ui-toolkit-plugin qtdeclarative5-unity-action-plugin
  qtdeclarative5-window-plugin rarian-compat retroarch rss-glx scrollkeeper
  sessioninstaller smartmontools smc smc-music smplayer smplayer-skins
  smplayer-themes smtube software-center software-properties-common
  software-properties-gtk soundconverter sqlitebrowser supertuxkart synaptic
  system-config-printer-gnome tesseract-ocr thermald thunar-media-tags-plugin
  thunderbird thunderbird-locale-en thunderbird-locale-en-us timemachine
  toshset ttf-mscorefonts-installer tumbler-plugins-extra
  ubuntu-drivers-common ubuntu-minimal ubuntu-release-upgrader-core
  ubuntu-release-upgrader-gtk ubuntu-standard ubuntu-system-service
  unattended-upgrades unity-voice-service unity-webapps-qml
  unity-webapps-service uno-libs3 update-manager update-manager-core
  update-notifier update-notifier-common ure usb-creator-gtk virtualbox
  virtualbox-qt vlc vlc-nox vlc-plugin-libde265 vlc-plugin-notify
  vlc-plugin-samba webapp-container webbrowser-app woeusb xchat-indicator
  xfce4-whiskermenu-plugin xorg xscreensaver-data-extra xscreensaver-gl
  xscreensaver-gl-extra xubuntu-desktop xul-ext-gdata-provider
  xul-ext-lightning zeitgeist zeitgeist-core zeitgeist-datahub zenity
The following NEW packages will be installed:
  foomatic-filters jackd1 libjack0
The following packages have been kept back:
  gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386
0 upgraded, 3 newly installed, 466 to remove and 5 not upgraded.
Need to get 431 kB of archives.
After this operation, 2,687 MB disk space will be freed.
Do you want to continue? [Y/n] n
Abort.

```

---

### Post by Xian on 2018-01-04
How is the output different if you remove the dist-upgrade?

```
sudo apt-get upgrade
```

---

### Post by pqwoerituytrueiwoq on 2018-01-05
that looks normal, aside from kept back
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages have been kept back:
  gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.
```

---

### Post by mc4man on 2018-01-05
run this
```
apt-cache policy gcc-4.9-base gcc-4.9-base:i386 lib32gcc1 libgcc1 libgcc1:i386
```
(- ubuntu did it's final gcc-4.9 update over 2 years ago. The large app removal likely involves libgcc1

---

### Post by pqwoerituytrueiwoq on 2018-01-05
I removed the 32bit stuff (apt-get --purge)
i also removed the lock i put on those packages, i was asking myself why did i lock these, then something reminded me the nvidia driver would not compile/bild with the update
```
gcc-4.9-base:
  Installed: 4.9.2-1ubuntu1
  Candidate: 4.9.3-0ubuntu4
  Version table:
     4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
lib32gcc1:
  Installed: 1:4.9.2-1ubuntu1
  Candidate: 1:4.9.3-0ubuntu4
  Version table:
     1:4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 1:4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     1:4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
libgcc1:
  Installed: 1:4.9.2-1ubuntu1
  Candidate: 1:4.9.3-0ubuntu4
  Version table:
     1:4.9.3-0ubuntu4 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
 *** 1:4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     1:4.9-20140406-0ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```
at this point it no longer wants to remove 1/2 my system
but as soon as i tell synaptic i want to update gcc-4.9-base it wants to remove what looks like every GUI piece of software i have installed

---

### Post by mc4man on 2018-01-05
and I assume synaptic doesn't want to upgrade libgcc1 either?
Was this an orig. or 14.04.1 install from 2014 that you stopped gcc updates in 2015 or did you install from the 14.04.3 image? The gcc-4.9-base & libgcc1 you have are from then (package released in vivid in 04 Nov 2014, then included in the 14.04.3 image

Have you tried upgrading with aptitude?

---

### Post by mc4man on 2018-01-05
Do you still have the actual nvidia-375 package or is it a transitional to 384?

---

### Post by pqwoerituytrueiwoq on 2018-01-05
looks like no, but see for your self
[URL="http://i.imgur.com/OvmOKpC.png"]
  [IMG]http://imgur.com/OvmOKpCb.png[/IMG]
[/URL]
i think it was a clean install of 14.04, maybe it was a rc or beta, not sure (waiting for 18.04 to upgrade clean to)
but lets take a look
[FONT=courier new]~$ cat /var/log/installer/media-info 
Xubuntu 13.04 "Raring Ringtail" - Release amd64 (20130423.1)[/FONT]

---

### Post by mc4man on 2018-01-05
Bit of a mystery. i guess if you are going to do a fresh install of 18.04 you could live with this.

The issue does seem to be libgcc1, if you where to search it in synaptic, mark for removal you'll see what i mean.
gcc-4.9-base, libgcc1 & lib32gcc1 must always  be exact same versions. Something seems to be preventing libgcc1 from upgrading..
Out of curiousity what does this produce
```
sudo aptitude install libgcc1
```

---

### Post by pqwoerituytrueiwoq on 2018-01-05
```
The following packages will be upgraded: 
  gcc-4.9-base libgcc1 
2 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 54.3 kB of archives. After unpacking 0 B will be used.
The following packages have unmet dependencies:
 lib32gcc1 : Depends: gcc-4.9-base (= 4.9.2-1ubuntu1) but 4.9.3-0ubuntu4 is to be installed.
 libstdc++6 : Depends: gcc-4.9-base (= 4.9.2-1ubuntu1) but 4.9.3-0ubuntu4 is to be installed.
The following actions will resolve these dependencies:

     Keep the following packages at their current version:
1)     gcc-4.9-base [4.9.2-1ubuntu1 (now)]                
2)     libgcc1 [1:4.9.2-1ubuntu1 (now)]                   



Accept this solution? [Y/n/q/?] q
Abandoning all efforts to resolve these dependencies.
Abort.

```
edit:
wait, how did this happen
```
apt-cache policy libstdc++6
libstdc++6:
  Installed: 4.9.2-1ubuntu1
  Candidate: 4.9.2-1ubuntu1
  Version table:
 *** 4.9.2-1ubuntu1 0
        100 /var/lib/dpkg/status
     4.8.4-2ubuntu1~14.04.3 0
        500 http://archive.ubuntu.com/ubuntu/ trusty-updates/main amd64 Packages
        500 http://archive.ubuntu.com/ubuntu/ trusty-security/main amd64 Packages
     4.8.2-19ubuntu1 0
        500 http://archive.ubuntu.com/ubuntu/ trusty/main amd64 Packages
```
edit:
[IMG]http://imgur.com/v1HXF2ol.png[/IMG]
guess that explains it
```
(synaptic:1267): GLib-CRITICAL **: g_child_watch_add_full: assertion 'pid > 0' failed
(Reading database ... 991818 files and directories currently installed.)
Removing dolphin-emu-master (4.0-6450) ...
Processing triggers for desktop-file-utils (0.22-1ubuntu1.1) ...
Processing triggers for mime-support (3.54ubuntu1.1) ...
Processing triggers for gnome-menus (3.10.1-0ubuntu2) ...
Processing triggers for man-db (2.6.7.1-1ubuntu1) ...
(Reading database ... 990122 files and directories currently installed.)
Preparing to unpack .../lib32gcc1_1%3a4.9.3-0ubuntu4_amd64.deb ...
Unpacking lib32gcc1 (1:4.9.3-0ubuntu4) over (1:4.9.2-1ubuntu1) ...
dpkg: warning: downgrading libstdc++6:amd64 from 4.9.2-1ubuntu1 to 4.8.4-2ubuntu1~14.04.3
Preparing to unpack .../libstdc++6_4.8.4-2ubuntu1~14.04.3_amd64.deb ...
Unpacking libstdc++6:amd64 (4.8.4-2ubuntu1~14.04.3) over (4.9.2-1ubuntu1) ...
Setting up libstdc++6:amd64 (4.8.4-2ubuntu1~14.04.3) ...
Processing triggers for libc-bin (2.19-0ubuntu6.13) ...
/sbin/ldconfig.real: /usr/lib/nvidia-384/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-384/libEGL.so.1 is not a symbolic link

(Reading database ... 990122 files and directories currently installed.)
Preparing to unpack .../gcc-4.9-base_4.9.3-0ubuntu4_amd64.deb ...
Unpacking gcc-4.9-base:amd64 (4.9.3-0ubuntu4) over (4.9.2-1ubuntu1) ...
Setting up gcc-4.9-base:amd64 (4.9.3-0ubuntu4) ...
(Reading database ... 990122 files and directories currently installed.)
Preparing to unpack .../libgcc1_1%3a4.9.3-0ubuntu4_amd64.deb ...
Unpacking libgcc1:amd64 (1:4.9.3-0ubuntu4) over (1:4.9.2-1ubuntu1) ...
Setting up libgcc1:amd64 (1:4.9.3-0ubuntu4) ...
Setting up lib32gcc1 (1:4.9.3-0ubuntu4) ...
Processing triggers for libc-bin (2.19-0ubuntu6.13) ...
/sbin/ldconfig.real: /usr/lib/nvidia-384/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-384/libEGL.so.1 is not a symbolic link


```
edit:
```

sudo apt-get autoremove 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  libpolarssl5 libsfml-network2 libsfml-system2
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
After this operation, 752 kB disk space will be freed.
Do you want to continue? [Y/n] y
(Reading database ... 990121 files and directories currently installed.)
Removing libpolarssl5 (1.3.4-1) ...
Removing libsfml-network2:amd64 (2.1+dfsg-4ubuntu2) ...
Removing libsfml-system2:amd64 (2.1+dfsg-4ubuntu2) ...
Processing triggers for libc-bin (2.19-0ubuntu6.13) ...
/sbin/ldconfig.real: /usr/lib/nvidia-384/libEGL.so.1 is not a symbolic link

/sbin/ldconfig.real: /usr/lib32/nvidia-384/libEGL.so.1 is not a symbolic link
```

---

### Post by mc4man on 2018-01-05
That libstdc++6 package was from vivid, dolphin-emu-master from somewhere. Maybe when you installed it it also installed the vivid version of libstdc++6
In any event seems you're back on track.

---

### Post by pqwoerituytrueiwoq on 2018-01-05
my guess is i pulled it from vivid so i could install dolphin, maybe i built it from source idk
it did not break anything at the time and i forgot about it

---

