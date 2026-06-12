---
title: "kiax? broken packages?"
date: 2005-07-22
forum: General Help
---

### Post by pek on 2005-07-22
hello everyone!

I'm trying to use [kiax](http://kiax.sourceforge.net/) , in order to use my voipbuster account.
the problem is that kiax uses an newer version of libc6 than the one i can get via apt-get.

so i did a dpkg --force-all -i . the program is running flawlessy, but every time I try to use synaptic or apt-get to install something else it complains about a broken package (and that is kiax) and it won't let me do anything but uninstall that thing.

what should I do? is there any work around for this issue?

I searched the forums for a similar problem but it ended up in nothing I could use, so maybe you can either tell me how to resolve or teach me the right searchwords.

thanks in advance.

ps
i'm sorry for my poor english

---

### Post by Xian on 2005-07-22
What is the output of the following terminal command:

```
$ sudo apt-get -f install
```

---

### Post by pek on 2005-07-22
[QUOTE=Xian]What is the output of the following terminal command:

```
$ sudo apt-get -f install
```[/QUOTE]
 here it is

```

root@mindless:/home/pek # apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  abiword-common abiword-gnome affix alien alsamixergui alsaplayer
  alsaplayer-common alsaplayer-gtk alsaplayer-oss amsn amule anacron at
  base-config beep-media-player bicyclerepair bittorrent bluez-pin bluez-utils
  bug-buddy capplets capplets-data celestia-gnome cmap-adobe-japan1
  console-common console-data console-tools contact-lookup-applet cramfsprogs
  cupsys cupsys-bsd cupsys-client cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data cvs dbus-1 dbus-1-utils dbus-glib-1 debhelper
  defoma dia-common dia-gnome dia-libs doc-base dvd+rw-tools eog evolution
  evolution-data-server evolution-webcal fglrx-control file file-roller
  firefox firefox-gnome-support flashplayer-mozilla fontconfig
  foomatic-db-engine foomatic-db-gimp-print foomatic-db-hpijs
  foomatic-filters-ppds gaim gcalctool gconf-editor gconf2 gdesklets
  gdk-imlib1 gdm gdm-themes gedit gedit-common gftp gftp-gtk gimp
  gimp-help-zh-cn gimp-python gksu gnoise-gnome gnome-about gnome-app-install
  gnome-applets gnome-applets-data gnome-bin gnome-bluetooth gnome-btdownload
  gnome-control-center gnome-core gnome-cups-manager gnome-doc-utils
  gnome-games gnome-gv gnome-keyring gnome-libs-data gnome-media gnome-menus
  gnome-netstatus-applet gnome-nettool gnome-office gnome-panel
  gnome-panel-data gnome-phone-manager gnome-pilot gnome-pilot-conduits
  gnome-pkgview gnome-session gnome-spell gnome-system-monitor
  gnome-system-tools gnome-terminal gnome-themes gnome-themes-extras
  gnome-utils gnome-volume-manager gnome2-user-guide gnomebaker gnomemeeting
  gnumeric gnumeric-common gnupg gs-common gs-esp gsfonts gstreamer0.8-alsa
  gstreamer0.8-audiofile gstreamer0.8-cdparanoia gstreamer0.8-dv
  gstreamer0.8-dvd gstreamer0.8-esd gstreamer0.8-flac gstreamer0.8-gnomevfs
  gstreamer0.8-gsm gstreamer0.8-hermes gstreamer0.8-jpeg gstreamer0.8-mad
  gstreamer0.8-misc gstreamer0.8-oss gstreamer0.8-plugin-apps gstreamer0.8-sdl
  gstreamer0.8-speex gstreamer0.8-theora gstreamer0.8-tools
  gstreamer0.8-vorbis gstreamer0.8-x gthumb gtk2-engines-clearlooks
  gtk2-engines-industrial gtk2-engines-mist gtk2-engines-pixbuf
  gtk2-engines-redmond95 gtk2-engines-smooth gtk2-engines-spherecrystal
  gtk2-engines-thinice gtkhtml3.6 gtoaster gucharmap hal hal-device-manager
  hpijs hwdb-client ifupdown ijsgimpprint imlib1 initrd-tools initscripts
  inkscape kdelibs-bin kdelibs4 kiax language-support-it lftp libarts1
  libbonobo2-0 libbonobo2-common libbonoboui2-0 libcairo1 libcamel1.2-3
  libcroco3 libcupsimage2 libcupsys2-gnutls10 libcurl3 libdirectfb-0.9-20
  libebook1.2-3 libecal1.2-2 libedata-book1.2-2 libedata-cal1.2-1
  libedataserver1.2-4 libedataserverui1.2-4 libeel2-2 libegroupwise1.2-5
  libexpat1 libfltk1.1c102 libfontconfig1 libfreetype6 libgail-common
  libgail17 libgal2.4-0 libgal2.4-common libgconf2-4 libgd1-noxpm libgd2-noxpm
  libgda2-1 libgda2-common libgdchart-gd1-noxpm libgeoip1 libgimp2.0
  libgimpprint1 libgksu1.2-0 libgksuui1.0-0 libglade2-0 libgnome-desktop-2
  libgnome-keyring0 libgnome-menu0 libgnome2-0 libgnome2-canvas-perl
  libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome32
  libgnomecanvas2-0 libgnomecups1.0-1 libgnomecupsui1.0-1 libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomesupport0 libgnomeui-0 libgnomeui32
  libgnomevfs2-0 libgnomevfs2-common libgnorba27 libgnorbagtk0 libgnutls11
  libgsf-1 libgsf-gnome-1 libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0
  libgstreamer0.8-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgtkhtml2-0 libgtkhtml3.6-18 libgtkmm-2.4-1 libgtksourceview1.0-0
  libgtkspell0 libgucharmap4 libhal-storage0 libhal0 libid3-3.8.3 libid3tag0
  libldap2 libmagic1 libmagick6 libmetacity0 libmng1 libmultisync-plugin-irmc
  libmultisync-plugin-irmc-bluetooth libmusicbrainz2 libmusicbrainz4
  libmysqlclient10 libmysqlclient12 libnautilus-burn1 libnautilus-extension1
  libneon23 libopencdk8 libopenh323-1.15.2 libpanel-applet2-0 libpango1.0-0
  libpango1.0-common libpng10-0 libpng12-0 libpt-1.8.3 libpt-plugins-alsa
  libpt-plugins-v4l2 libqt3c102-mt libraptor1 librasqal0 librdf0 librpm4
  librsvg2-2 librsvg2-common libscrollkeeper0 libsmbclient libsoup2.2-7
  libtiff4 libtunepimp2 libvte4 libwmf0.2-7 libwnck16 libwvstreams3-base
  libwxbase2.4 libwxgtk2.4 libxft2 libxine1 libxklavier10 libxml2
  libxml2-utils libxslt1.1 linux-image-2.6.10-5-386
  linux-restricted-modules-2.6.10-5-386 linux-restricted-modules-386 lvm10
  mailx metacity mkisofs mozilla-browser mozilla-firefox
  mozilla-firefox-gnome-support mozilla-firefox-locale-it mozilla-thunderbird
  mozilla-thunderbird-locale-it mpg321 mplayer-386 msttcorefonts multisync
  mutt nautilus nautilus-cd-burner nautilus-data nautilus-sendto netbase
  netpbm oooqs-kde openoffice.org openoffice.org-bin
  openoffice.org-debian-files openoffice.org-gtk-gnome openoffice.org-help-it
  openoffice.org-hyphenation-it openoffice.org-l10n-it
  openoffice.org-thesaurus-it openssh-client planner pmount pnm2ppa postfix
  postfix-tls ppp pppconfig pppoeconf python python-adns python-apt
  python-cddb python-clientcookie python-crypto python-egenix-mxproxy
  python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools
  python-epydoc python-eunuchs python-examples python-gadfly python-gd
  python-gdbm python-gdchart python-genetic python-geoip python-glade2
  python-gnome2 python-gnome2-extras python-gnupginterface python-gst
  python-gtk2 python-gtk2-dev python-htmlgen python-htmltmpl python-id3lib
  python-imaging python-imaging-sane python-jabber python-kjbuckets
  python-ldap python-minimal python-musicbrainz python-mysqldb python-netcdf
  python-newt python-numarray python-numeric python-opengl python-osd
  python-pam python-parted python-pexpect python-pgsql python-pisock
  python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl
  python-pyorbit python-pyvorbis python-pyxattr python-reportlab
  python-simpletal python-soappy python-sqlite python-stats python-syck
  python-tk python-twisted python-unit python-xdg python-xml python-xmpp
  python2.3 python2.4 python2.4-adns python2.4-clientcookie python2.4-crypto
  python2.4-dbus python2.4-dictclient python2.4-egenix-mxdatetime
  python2.4-egenix-mxproxy python2.4-egenix-mxstack
  python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-eunuchs
  python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm
  python2.4-geoip python2.4-glade2 python2.4-gnome2 python2.4-gnome2-extras
  python2.4-gtk2 python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib
  python2.4-imaging python2.4-imaging-sane python2.4-jabber
  python2.4-kjbuckets python2.4-ldap python2.4-libbtctl python2.4-librdf
  python2.4-libxml2 python2.4-libxslt1 python2.4-minimal python2.4-musicbrainz
  python2.4-mysqldb python2.4-numarray python2.4-numeric python2.4-opengl
  python2.4-osd python2.4-pam python2.4-pexpect python2.4-pgsql
  python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit
  python2.4-pyxattr python2.4-reportlab python2.4-samba python2.4-simpletal
  python2.4-sqlite python2.4-syck python2.4-tk python2.4-twisted
  python2.4-twisted-bin python2.4-unit python2.4-xml python2.4-xmpp rep-gtk
  reportbug rhythmbox rpm rss-glx samba-common sawfish scrollkeeper
  shared-mime-info smbclient sodipodi sound-juicer ssh-askpass-gnome
  streamtuner synaptic sysvinit telnet totem totem-xine tsclient ttf-arabeyes
  ttf-arphic-bkai00mp ttf-arphic-bsmi00lp ttf-arphic-gbsn00lp
  ttf-arphic-gkai00mp ttf-baekmuk ttf-bitstream-vera ttf-freefont
  ttf-indic-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-malayalam-fonts
  ubuntu-artwork ubuntu-docs ubuntu-keyring ubuntu-quickguide udev
  update-manager update-notifier util-linux vino vorbis-tools w3m wvdial
  x-ttcidfont-conf x-window-system-core xbase-clients xchat xchat-common
  xfonts-100dpi xfonts-75dpi xfonts-base xfonts-scalable xine-ui
  xorg-driver-fglrx xorg-driver-synaptics xpdf xpdf-japanese xpdf-reader xsane
  xscreensaver xscreensaver-gl xserver-xorg xsltproc xterm xutils xvncviewer
  yelp zenity zlib1g
WARNING: The following essential packages will be removed
This should NOT be done unless you know exactly what you are doing!
  python-minimal python2.4-minimal (due to python-minimal) sysvinit
  initscripts (due to sysvinit) util-linux zlib1g (due to util-linux)
0 upgraded, 0 newly installed, 537 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 1383MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase 'Yes, do as I say!'
 ?]


```

---

### Post by Xian on 2005-07-22
If you force install a package into apt and prevent it from managing the conflicting dependencies, it will respond by only showing breakages from that point forward, which means that it basically become inoperable.

To fix this you will either have to replace your current version of libc6 with the original release or try the newer package from the Breezy repo and hope to have a better result.

---

### Post by Typhoon on 2005-07-23
You can also use iaxclient: [http://iaxclient.sourceforge.net/](http://iaxclient.sourceforge.net/)

I use the binary - you may need to apt-get a library (run it from a terminal to see how it goes).

I have found the sound a little scratchy, but it works.

Cheers,
Typhoon

---

### Post by Typhoon on 2005-07-23
Sorry, that should have been iaxComm.

[http://iaxclient.sourceforge.net/iaxcomm/index.html](http://iaxclient.sourceforge.net/iaxcomm/index.html)

Typhoon

---

### Post by pek on 2005-07-23
[QUOTE=Typhoon]Sorry, that should have been iaxComm.

[http://iaxclient.sourceforge.net/iaxcomm/index.html](http://iaxclient.sourceforge.net/iaxcomm/index.html)

Typhoon[/QUOTE]
 iaxclient is working very bad, i'll try the breezy.

---

### Post by speckone on 2005-10-19
I am also having trouble installing Kiax in Kubuntu 5.10:

```
speckone@Laptop:~$ sudo dpkg -i kiax_0.8.4-1debian_i386.deb
Selecting previously deselected package kiax.
(Reading database ... 58745 files and directories currently installed.)
Unpacking kiax (from kiax_0.8.4-1debian_i386.deb) ...
dpkg: dependency problems prevent configuration of kiax:
 kiax depends on libqt3c102-mt (>= 3:3.3.4); however:
  Package libqt3c102-mt is not installed.
dpkg: error processing kiax (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 kiax

```

Breezy has libqt3-mt instead of libqt3c102-mt, hence the broken package.  Is there any way to resolve this?

---

### Post by mvandeg on 2005-11-08
Yes, you can fix it as follows:

Install fakeroot and alien:
```
sudo apt-get install fakeroot alien
```

Convert the downloaded deb to tgz and back:
```
fakeroot alien --to-tgz kiax_0.8.4-1debian_i386.deb
fakeroot alien --to-deb kiax-0.8.4.tgz
```

Install the new package:
```
sudo dpkg -i kiax_0.8.4-2_all.deb
```

---

### Post by speckone on 2005-11-14
Worked like a charm! Thanks!

---

### Post by Dutch on 2006-01-01
oke I followed this thread and it worked out till i try to start kiax.
I've got the message:

```

paul@Paul:/$ kiax
zo jan 1 17:32:05 2006 Using IAXClient ver. CVS-2005/04/14-16:33
zo jan 1 17:32:07 2006 IaxWrapper::iaxc_initialize() result = -1
Error message:cannot initialize iaxclient!

Exitting application. Possible reason: Device initialization failed.

Geannuleerd

```

---

### Post by Harry_Sack on 2006-02-17
Yeah, I'm getting the same. HOW COME?

---

