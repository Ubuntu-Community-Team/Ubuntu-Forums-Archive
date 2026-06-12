---
title: "Problem with Synaptic / apt"
date: 2008-02-28
forum: General Help
---

### Post by ShadouX3 on 2008-02-28
Hi there, I'm a very new user to ubuntu [from windows], and i've been trying to use Synaptic to get get a package, (Primarily so I can play MP3 files in totem / rhythmbox)

but no matter which packages in SPM I mark, it always 'forces' me to choose to remove a whole load, upgrade a load, and install a load which are all unrelated... Getting fed up of this I tried to just click ok, it downloaded 90mb, at 20kbs [took a while!] and then came up with an error that it couldnt remove one of them... back to square 1

I tried to use terminal to do it instead, and came up with same thing, this is what it says:

185 upgraded, 171 newly installed, 183 to remove and 482 not upgraded.
Need to get 99.4MB/167MB of archives.
After unpacking 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]

=S All I want is Gstreamer plugin for MP3 functionality... any advice appreciated, thankyou!

---

### Post by taurus on 2008-02-28
Can you at least post the whole message from the time you type "sudo apt-get install pacakge" instead only the last few lines?

---

### Post by ShadouX3 on 2008-02-28
root@osiris:~# sudo apt-get install totem
Reading package lists... Done
Building dependency tree... Done
The following extra packages will be installed:
  app-install-data apt apt-utils aptitude avahi-daemon bicyclerepair
  bittorrent cdrdao cdrecord console-terminus consolekit coreutils cupsys
  cupsys-common cupsys-driver-gimpprint cupsys-driver-gutenprint dbus dcraw
  dpkg e2fslibs e2fsprogs fontconfig fontconfig-config gcc-3.4-base
  gcc-4.2-base gconf2 gconf2-common gdebi-core genisoimage ghostscript
  ghostscript-x gimp gimp-data gnome-applets-data gnome-icon-theme
  gnome-keyring gnome-keyring-manager gnome-media gnome-media-common
  gnome-panel-data gnome-system-monitor gnome-system-tools gnome-utils
  gs-common gs-esp gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps
  gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x
  gtk2-engines-pixbuf hal-info hplip-data iso-codes klibc-utils
  language-selector-common lapack3 launchpad-integration libao2 libart-2.0-2
  libasound2 libatk1.0-0 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libavc1394-0 libbeagle0 libbluetooth2 libbonobo2-0 libbonobo2-common
  libbonoboui2-0 libbonoboui2-common libc6 libc6-i686 libcaca0 libcairo2
  libcairomm-1.0-1 libcamel1.2-10 libcdio6 libcroco3 libcucul0 libcupsimage2
  libcupsys2 libcurl3-gnutls libdaemon0 libdatrie0 libdb4.4 libdb4.5
  libdbus-1-3 libdbus-glib-1-2 libdmx1 libdrm2 libebook1.2-9 libecal1.2-7
  libedataserver1.2-9 libedataserverui1.2-8 libflac8 libfontconfig1
  libfontenc1 libfreetype6 libfs6 libg2c0 libgail-common libgail18 libgcc1
  libgconf2-4 libgcrypt11 libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common
  libgdl-gnome-1-0 libgeoip1 libgimp2.0 libglade2-0 libglib2.0-0
  libglib2.0-data libglibmm-2.4-1c2a libgnome-keyring0 libgnome-media0
  libgnome-menu2 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnomecanvas2-0 libgnomecanvas2-common
  libgnomekbd-common libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common
  libgnomevfs2-extra libgnutls13 libgpg-error0 libgs8 libgsf-1-114
  libgsf-1-common libgstreamer-plugins-base0.10-0 libgstreamer0.10-0
  libgtk2.0-0 libgtk2.0-common libgtkmm-2.4-1c2a libgtksourceview-common
  libgtksourceview1.0-0 libgtop2-7 libgtop2-common libgucharmap6
  libgutenprint2 libhal-storage1 libhal1 libhtml-parser-perl
  libhtml-tagset-perl libhtml-tree-perl libhunspell-1.1-0 libice6 libicu36
  libidn11 libiec61883-0 libiw29 libkeyutils1 libklibc libkrb53 liblcms1
  liblzo2-2 libmetacity0 libmysqlclient15off libnautilus-burn4
  libnautilus-extension1 libncurses5 libncursesw5 libneon26 libnet-dbus-perl
  libnotify1 libnspr4-0d libnss3-0d libogg0 liboil0.3 liboobs-1-3 libopencdk8
  liborbit2 libpam-foreground libpam0g libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpcre3 libpcrecpp0 libperl5.8 libpisock9 libpng12-0
  libpoppler-glib2 libpoppler2 libpopt0 libpq4 libraw1394-8 libreadline5
  librsvg2-2 librsvg2-common libselinux1 libsepol1 libsigc++-2.0-0c2a
  libslang2 libsm6 libspeex1 libsqlite0 libsqlite3-0 libssl0.9.8 libstdc++6
  libtag1c2a libtasn1-3 libthai-data libthai0 libtotem-plparser7
  libtrackerclient0 liburi-perl libusb-0.1-4 libusplash0 libvisual-0.4-0
  libvolume-id0 libvorbis0a libvorbisenc2 libvorbisfile3 libwavpack1
  libwmf0.2-7 libwnck-common libwnck22 libwww-perl libx11-6 libx11-data
  libx86-1 libxau6 libxaw7 libxcomposite1 libxdamage1 libxdmcp6 libxext6
  libxfixes3 libxfont1 libxi6 libxinerama1 libxkbfile1 libxml-parser-perl
  libxml-twig-perl libxml2 libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxres1
  libxslt1.1 libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1
  libxxf86misc1 libxxf86vm1 lsb-base metacity metacity-common mkisofs
  module-init-tools mysql-common nautilus-data openoffice.org-hyphenation
  openprinting-ppds openssl perl perl-base perl-modules poppler-utils python
  python-apt python-bittorrent python-cddb python-central python-cups
  python-epydoc python-examples python-gdchart python-genetic python-geoip
  python-gnomecanvas python-gnupginterface python-gobject python-gst0.10
  python-minimal python-numarray python-pisock python-pqueue python-pyao
  python-pyogg python-pyvorbis python-stats python-support python-twisted-bin
  python-twisted-core python-twisted-lore python-twisted-mail
  python-twisted-names python-twisted-news python-twisted-runner
  python-twisted-web python-twisted-words python-xdg python-zopeinterface
  python2.5 python2.5-examples python2.5-minimal readline-common refblas3
  screensaver-default-images ssl-cert system-tools-backends sysv-rc
  tangerine-icon-theme totem-gstreamer ttf-dejavu-core ttf-kochi-gothic
  ttf-kochi-mincho tzdata update-manager-core wodim x11-common xbitmaps
  xdg-user-dirs xdg-user-dirs-gtk xfonts-100dpi xfonts-75dpi xfonts-base
  xfonts-encodings xfonts-scalable xfonts-utils xkb-data xkeyboard-config
  xserver-xorg-input-wacom xserver-xorg-video-psb xterm xvnc4viewer zlib1g
Suggested packages:
  dpkg-dev apt-doc lzma tasksel debtags avahi-autoipd vim-python idle pymacs
  bittorrent-gui xcdroast cdrtools-doc console-setup xpdf-korean xpdf-japanese
  xpdf-chinese-traditional xpdf-chinese-simplified cups-pdf hplip foomatic-bin
  gimpprint-doc gimpprint-locales gutenprint-doc gutenprint-locales gphoto2
  netpbm gpart e2fsck-static cdrkit-doc gimp-help-en gimp-help libgimp-perl
  gimp-data-extras ntp gtk-engines-pixmap libpulse0 libasound2-plugins
  glibc-doc libfreetype6-dev rng-tools libgda3-mysql libgda3-postgres
  libgda3-odbc libgda3-sqlite libgda3-freetds geoip-bin desktop-base
  gnutls-bin libvisual-0.4-plugins gstreamer0.10-plugins krb5-doc krb5-user
  liblcms-utils libpam-doc ttf-thryomanes jpilot pilot-link kpilot claws-mail
  sylpheed libraw1394-doc librsvg2-bin speex libio-socket-ssl-perl
  libunicode-map8-perl xml-twig-tools hpijs-ppds openprinting-ppds-extra
  libterm-readline-gnu-perl libterm-readline-perl-perl python-doc
  python-profiler python-apt-dbg epydoc-doc python-gnomecanvas-dbg
  python-gst0.10-dbg python-numarray-doc python-numarray-dbg python-pisock-dbg
  python-pyao-dbg python-pyogg-dbg python-pyvorbis-dbg python-twisted-bin-dbg
  python-qt3 python-wxgtk2.8 python-wxgtk2.6 python-twisted-runner-dbg
  python-zopeinterface-dbg python2.5-doc sysv-rc-conf bum
  gstreamer0.10-plugins-ugly gstreamer0.10-ffmpeg xserver-xfree86 xfs-xtt xfs
  xserver xfonts-cyrillic vnc4-common
Recommended packages:
  aptitude-doc-en aptitude-doc libparse-debianchangelog-perl libnss-mdns
  cdda2wav libpam-ck-connector gnome-gv postscript-viewer psfontmgr
  gimp-gnomevfs gimp-libcurl gimp-svg libgksu2-0 libatk1.0-data
  ca-certificates libgda3-bin gnome-mount libpng-dev libmailtools-perl
  libhtml-format-perl libcompress-zlib-perl libtie-ixhash-perl
  libxml-xpath-perl perl-doc texlive-latex-base texlive-latex-extra
  texlive-latex-recommended texlive-fonts-recommended graphviz tetex-extra
  python-serial totem-mozilla
The following packages will be REMOVED:
  bluez-pcmcia-support bluez-pin bluez-utils cupsys-driver-gimpprint-data
  dbus-1-utils evince evolution-plugins gdm gimp-python gksu gnome-app-install
  gnome-applets gnome-btdownload gnome-control-center gnome-menus
  gnome-netstatus-applet gnome-panel gnome-session gnome-terminal
  gnome-volume-manager hal hal-device-manager hotplug hplip-base hwdb-client
  ifrename initramfs-tools language-pack-en language-pack-en-base
  language-pack-gnome-en language-pack-gnome-en-base language-selector
  libdbus-1-1 libdbus-glib-1-1 libgksu1.2-0 libgksuui1.0-0 libnautilus-burn2
  libnotify0 linux-386 linux-image-2.6.12-9-386 linux-image-386
  linux-restricted-modules-2.6.12-9-386 linux-restricted-modules-386 locales
  nautilus nautilus-cd-burner notification-daemon openoffice.org2
  openoffice.org2-writer pmount python-adns python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-eunuchs python-gadfly python-gd python-gdbm
  python-glade2 python-gmenu python-gnome2 python-gnome2-extras python-gst
  python-gtk2 python-htmlgen python-htmltmpl python-id3lib python-imaging
  python-imaging-sane python-jabber python-kjbuckets python-ldap
  python-musicbrainz python-mysqldb python-netcdf python-newt python-numeric
  python-osd python-pam python-parted python-pexpect python-pgsql
  python-pylibacl python-pyopenssl python-pyorbit python-pyxattr
  python-reportlab python-simpletal python-soappy python-sqlite python-syck
  python-tk python-unit python-uno python-xml python-xmpp python2.4-apt
  python2.4-dbus python2.4-gd python2.4-gnome2-extras rhythmbox serpentine
  smeg sound-juicer synaptic ttf-arphic-bkai00mp ttf-arphic-bsmi00lp
  ttf-arphic-gbsn00lp ttf-arphic-gkai00mp ubuntu-desktop ubuntu-minimal udev
  update-manager update-notifier usplash x-common x-ttcidfont-conf
  x-window-system-core xbase-clients xorg-common xorg-driver-synaptics
  xserver-common xserver-xorg xserver-xorg-core xserver-xorg-driver-apm
  xserver-xorg-driver-ark xserver-xorg-driver-ati xserver-xorg-driver-chips
  xserver-xorg-driver-cirrus xserver-xorg-driver-cyrix
  xserver-xorg-driver-dummy xserver-xorg-driver-fbdev
  xserver-xorg-driver-glide xserver-xorg-driver-glint xserver-xorg-driver-i128
  xserver-xorg-driver-i740 xserver-xorg-driver-i810 xserver-xorg-driver-imstt
  xserver-xorg-driver-mga xserver-xorg-driver-neomagic
  xserver-xorg-driver-newport xserver-xorg-driver-nsc xserver-xorg-driver-nv
  xserver-xorg-driver-rendition xserver-xorg-driver-s3
  xserver-xorg-driver-s3virge xserver-xorg-driver-savage
  xserver-xorg-driver-siliconmotion xserver-xorg-driver-sis
  xserver-xorg-driver-tdfx xserver-xorg-driver-tga xserver-xorg-driver-trident
  xserver-xorg-driver-tseng xserver-xorg-driver-v4l xserver-xorg-driver-vesa
  xserver-xorg-driver-vga xserver-xorg-driver-via xserver-xorg-driver-vmware
  xserver-xorg-input-acecad xserver-xorg-input-aiptek
  xserver-xorg-input-calcomp xserver-xorg-input-citron
  xserver-xorg-input-digitaledge xserver-xorg-input-dmc
  xserver-xorg-input-dynapro xserver-xorg-input-elographics
  xserver-xorg-input-fpit xserver-xorg-input-hyperpen xserver-xorg-input-kbd
  xserver-xorg-input-magellan xserver-xorg-input-microtouch
  xserver-xorg-input-mouse xserver-xorg-input-mutouch
  xserver-xorg-input-palmax xserver-xorg-input-penmount
  xserver-xorg-input-spaceorb xserver-xorg-input-summa
  xserver-xorg-input-tek4957 xserver-xorg-input-void xutils
The following NEW packages will be installed:
  app-install-data avahi-daemon cdrdao console-terminus consolekit
  cupsys-common cupsys-driver-gutenprint dcraw fontconfig-config gcc-3.4-base
  gcc-4.2-base gconf2-common gdebi-core genisoimage ghostscript ghostscript-x
  gnome-keyring-manager gnome-media-common gstreamer0.10-alsa
  gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good
  gstreamer0.10-tools gstreamer0.10-x hal-info iso-codes
  language-selector-common lapack3 libavahi-client3 libavahi-common-data
  libavahi-common3 libavahi-compat-libdnssd1 libavahi-core5 libavahi-glib1
  libbeagle0 libbluetooth2 libcaca0 libcairomm-1.0-1 libcamel1.2-10 libcdio6
  libcucul0 libcupsys2 libcurl3-gnutls libdaemon0 libdatrie0 libdb4.4 libdb4.5
  libdbus-1-3 libdbus-glib-1-2 libdmx1 libdrm2 libebook1.2-9 libecal1.2-7
  libedataserver1.2-9 libedataserverui1.2-8 libflac8 libg2c0 libgail18
  libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0
  libglibmm-2.4-1c2a libgnome-media0 libgnome-window-settings1
  libgnomekbd-common libgnomevfs2-bin libgnomevfs2-extra libgnutls13 libgs8
  libgsf-1-114 libgsf-1-common libgstreamer-plugins-base0.10-0
  libgstreamer0.10-0 libgtkmm-2.4-1c2a libgtop2-7 libgtop2-common
  libgucharmap6 libgutenprint2 libhtml-parser-perl libhtml-tagset-perl
  libhtml-tree-perl libhunspell-1.1-0 libicu36 libiec61883-0 libiw29
  libkeyutils1 liblzo2-2 libmysqlclient15off libnautilus-burn4 libneon26
  libnet-dbus-perl libnotify1 libnspr4-0d libnss3-0d liboobs-1-3
  libpam-foreground libpcre3 libpcrecpp0 libpisock9 libpoppler-glib2
  libpoppler2 libraw1394-8 libsepol1 libsigc++-2.0-0c2a libssl0.9.8 libtag1c2a
  libtasn1-3 libthai-data libthai0 libtotem-plparser7 libtrackerclient0
  liburi-perl libusplash0 libvisual-0.4-0 libvolume-id0 libwavpack1 libwnck22
  libwww-perl libx11-data libx86-1 libxcomposite1 libxfont1 libxml-parser-perl
  libxml-twig-perl metacity-common openoffice.org-hyphenation
  openprinting-ppds openssl poppler-utils python-bittorrent python-central
  python-cups python-gnomecanvas python-gobject python-gst0.10 python-numarray
  python-support python-twisted-bin python-twisted-core python-twisted-lore
  python-twisted-mail python-twisted-names python-twisted-news
  python-twisted-runner python-twisted-web python-twisted-words
  python-zopeinterface python2.5 python2.5-examples python2.5-minimal
  readline-common refblas3 screensaver-default-images ssl-cert
  tangerine-icon-theme ttf-dejavu-core tzdata update-manager-core wodim
  x11-common xbitmaps xdg-user-dirs xdg-user-dirs-gtk xfonts-encodings
  xkb-data xserver-xorg-video-psb xvnc4viewer
The following packages will be upgraded:
  apt apt-utils aptitude bicyclerepair bittorrent cdrecord coreutils cupsys
  cupsys-driver-gimpprint dbus dpkg e2fslibs e2fsprogs fontconfig gconf2 gimp
  gimp-data gnome-applets-data gnome-icon-theme gnome-keyring gnome-media
  gnome-panel-data gnome-system-monitor gnome-system-tools gnome-utils
  gs-common gs-esp gtk2-engines-pixbuf hplip-data klibc-utils
  launchpad-integration libao2 libart-2.0-2 libasound2 libatk1.0-0
  libavc1394-0 libbonobo2-0 libbonobo2-common libbonoboui2-0
  libbonoboui2-common libc6 libc6-i686 libcairo2 libcroco3 libcupsimage2
  libfontconfig1 libfontenc1 libfreetype6 libfs6 libgail-common libgcc1
  libgconf2-4 libgcrypt11 libgeoip1 libgimp2.0 libglade2-0 libglib2.0-0
  libglib2.0-data libgnome-keyring0 libgnome-menu2 libgnome2-0
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnomecanvas2-0
  libgnomecanvas2-common libgnomeprint2.2-0 libgnomeprint2.2-data
  libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-common libgpg-error0
  libgtk2.0-0 libgtk2.0-common libgtksourceview-common libgtksourceview1.0-0
  libhal-storage1 libhal1 libice6 libidn11 libklibc libkrb53 liblcms1
  libmetacity0 libnautilus-extension1 libncurses5 libncursesw5 libogg0
  liboil0.3 libopencdk8 liborbit2 libpam0g libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libperl5.8 libpng12-0 libpopt0 libpq4 libreadline5
  librsvg2-2 librsvg2-common libselinux1 libslang2 libsm6 libspeex1 libsqlite0
  libsqlite3-0 libstdc++6 libusb-0.1-4 libvorbis0a libvorbisenc2
  libvorbisfile3 libwmf0.2-7 libwnck-common libx11-6 libxau6 libxaw7
  libxdamage1 libxdmcp6 libxext6 libxfixes3 libxi6 libxinerama1 libxkbfile1
  libxml2 libxmu6 libxmuu1 libxp6 libxpm4 libxrandr2 libxres1 libxslt1.1
  libxss1 libxt6 libxtrap6 libxtst6 libxv1 libxxf86dga1 libxxf86misc1
  libxxf86vm1 lsb-base metacity mkisofs module-init-tools mysql-common
  nautilus-data perl perl-base perl-modules python python-apt python-cddb
  python-epydoc python-examples python-gdchart python-genetic python-geoip
  python-gnupginterface python-minimal python-pisock python-pqueue python-pyao
  python-pyogg python-pyvorbis python-stats python-xdg system-tools-backends
  sysv-rc totem totem-gstreamer ttf-kochi-gothic ttf-kochi-mincho
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xfonts-utils
  xkeyboard-config xserver-xorg-input-wacom xterm zlib1g
185 upgraded, 171 newly installed, 183 to remove and 482 not upgraded.
Need to get 99.4MB/167MB of archives.
After unpacking 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]?

---

### Post by taurus on 2008-02-28
Which release are you running?  Did you install the server version?

---

### Post by ShadouX3 on 2008-02-28
Am using Desktop version,  but I guess I have to upgrade, since someone said this version [breezy] isnt supported anymore, but then that comes on to a whole other issue, of why v7 isnt working when I try to install that.. so I'd rather that be a last resort

---

### Post by taurus on 2008-02-28
You are running Breezy right now?  I think that release is no longer support.

What's the spec of your machine?  What kind of problems when you tried to install Gutsy, 7.10?

---

### Post by ShadouX3 on 2008-02-28
I dont know the stats greatly but:

ATi Radeon 9550 (Supported and working)
Onboard Sound (Supported and working)
1GB DDR Ram
Intel Pentium 4 2.6ghz cpu

Though I dont really see how the specs would affect the packages? anyway.

I've got 3 CD's now of  Gutsy, all burned on different brands of CD, (I tried max burn speed and slow speed) and did the MD5Sum thing to check all the CD's were burnt correctly (Which they were) 

but when I boot from it, i get the startup screen that says "Install", "Check CD integrity" etc, I press Install, it freezes for a moment and then a little error pops up saying something along the lines of cannot read from bootable something or other, and says it needs to reboot. on all 3 cd's

---

### Post by taurus on 2008-02-28
At the first screen, why don't you use the down arrow and move down to Check Disc for Defects to make sure the disk is good before you run it!

---

### Post by ShadouX3 on 2008-02-28
I have.. and it freezes and comes up with the same error there too... on all 3 cd's

---

### Post by taurus on 2008-02-28
I would download and try the alternate CD.  Make sure you burn it at a slow speed like 4x.

---

### Post by ShadouX3 on 2008-02-28
> (I tried max burn speed and slow speed) Guess I'll try the alternate CD... /sigh

---

