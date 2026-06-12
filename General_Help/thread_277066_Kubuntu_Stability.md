---
title: "Kubuntu Stability"
date: 2006-10-13
forum: General Help
---

### Post by StreetSmart on 2006-10-13
Does Kubuntu have any stability problems? I've been talking to a few people on IRC who's opinion is that kubuntu is unstable and that I shouldn't use it.

---

### Post by gila_monster on 2006-10-13
It's worked pretty well for me so far. I notice no more problems than I had under Ubuntu with Gnome.

---

### Post by aysiu on 2006-10-13
No stability problems that I know of. It's a bit sluggish, though. I prefer *kde-core* to *kubuntu-desktop*.

---

### Post by StreetSmart on 2006-10-13
how would you go about installing kde-core rather than kubuntu-desktop? Would this need to be done after installing ubuntu in apt-get?

---

### Post by aysiu on 2006-10-13
Hm. That's a good question. *kde-core* has fewer packages than Kubuntu... so I'm not sure what packages you'd have to uninstall. Let me look into this.

---

### Post by StreetSmart on 2006-10-13
Thanks alot. I believe it would be faster if i were to install kde-core instead of the kubuntu-desktop because of the amount of packages are included with kubuntu.

---

### Post by aysiu on 2006-10-13
Okay. I have to warn you--it'll uninstall **a lot**. There may be an essential application or two you want to reinstall after you do this, but all your settings for those programs will still be there.

Paste this command into the terminal and watch the sparks fly: ```
sudo apt-get remove acpi-support adept akregator amarok amarok-xine apmd app-install-data arj ark artsbuilder avahi-daemon bc bicyclerepair blt bluez-cups bluez-pcmcia-support bluez-utils brltty bsh cdparanoia cdrdao cdrecord cupsys-driver-gutenprint dc dcraw debtags diveintopython doc-base doc-debian docbook-xml dvd+rw-tools example-content fastjar finger flac foo2zjs foomatic-db-gutenprint foomatic-db-hpijs foomatic-filters-ppds fortune-mod fortunes-min gcc-3.3-base gcj-4.1 gcj-4.1-base gettext gij-4.1 gtk2-engines-gtk-qt gwenview hotkey-setup hpijs hplip hplip-data hplip-ppds ijsgutenprint imagemagick intltool-debian irssi java-common java-gcj-compat k3b kaffeine kaffeine-xine karm katapult kaudiocreator kcron kde-guidance kde-style-lipstik kde-systemsettings kdeadmin-kfile-plugins kdebluetooth kdegraphics-kfile-plugins kdemultimedia-kfile-plugins kdenetwork-filesharing kdenetwork-kfile-plugins kdepim-kresources kdepim-wizards kdnssd keep kio-apt kio-locate kipi-plugins kitchensync klaptopdaemon kmailcvt kmilo kmix kmplayer-base kmplayer-konq-plugins knetworkconf knode knotes koffice-data koffice-libs konq-plugins kontact konversation kooka kopete korganizer kpdf kpf kppp krdc krfb krita krita-data kscd kscreensaver kscreensaver-xsavers ksplash-engine-moodin ksvg ksystemlog ktorrent kubuntu-artwork-usplash kubuntu-default-settings kubuntu-desktop kubuntu-docs kubuntu-konqueror-shortcuts kwalletmanager kwin-style-crystal landscape-client language-selector-common language-selector-qt laptop-mode-tools latex-xft-fonts lftp libadns1 libadns1-bin libakode2 libao2 libapm1 libarts1-akode libavahi-core4 libbluetooth1 libbrlapi1 libcdio6 libcurl3 libcurl3-gnutls libdaemon0 libflac++5c2 libgcj-common libgcj7 libgcj7-awt libgcj7-dev libgcj7-jar libgcj7-src libgd2-noxpm libgeoip1 libgmp3c2 libgnucrypto-java libgpod-common libgpod0 libgstreamer-plugins-base0.10-0 libgstreamer0.10-0 libgutenprint2 libhsqldb-java libicu34 libid3-3.8.3c2a libieee1284-3 libifp4 libijs-0.35 libimlib2 libiso9660-4 libjasper-runtime libjaxp1.2-java libjessie-java libjline-java libjpeg-progs libk3b2 libkexif1 libkipi0 libkpimexchange1 libkscan1 liblockdev1 libmagick9 libmail-sendmail-perl libmdbtools libmodplug0c2 libmpcdec3 libmusicbrainz4c2a libmysqlclient15off libneon25 libnetcdf3 libnss-mdns liboggflac3 libopenobex-1.0-0 libpoppler1-qt libportaudio0 libpq4 libpythonize0 libqt-perl libraptor1 librasqal0 librdf0 librecode0 librsync1 libruby1.8 libsamplerate0 libsane libscim8c2a libscrollkeeper0 libsdl1.2debian libsdl1.2debian-alsa libservlet2.3-java libskim0 libsmokeqt1 libsndfile1 libsnmp-base libsnmp9 libspeex1 libsqlite0 libsqlite3-0 libstdc++5 libstlport4.6c2 libt1-5 libtdb1 libtheora0 libtunepimp3 libunicode-string-perl libuniconf4.2 libvcdinfo0 libvisual-0.4-0 libvisual-0.4-plugins libwpd8c2a libwvstreams4.2-base libwvstreams4.2-extras libxalan2-java libxerces2-java libxine-main1 libxml-parser-perl libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxp6 libxplc0.3.13 libxt-java libxvmc1 min12xxw miscfiles mkisofs mysql-common ncompress ocrad openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-impress openoffice.org-java-common openoffice.org-kde openoffice.org-l10n-en-us openoffice.org-math openoffice.org-writer pcmcia-cs perl-tk pnm2ppa po-debconf powermanagement-interface powermgmt-base powernowd pykdeextensions python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxdatetime python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gnupginterface python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber python-kde3 python-kjbuckets python-ldap python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-qt3 python-reportlab python-simpletal python-soappy python-sqlite python-stats python-syck python-tk python-unit python-uno python-xdg python-xml python-xmpp python2.4-adns python2.4-apt python2.4-clientcookie python2.4-crypto python2.4-dbus python2.4-dev python2.4-dictclient python2.4-egenix-mxdatetime python2.4-egenix-mxproxy python2.4-egenix-mxstack python2.4-egenix-mxtexttools python2.4-egenix-mxtools python2.4-epydoc python2.4-eunuchs python2.4-examples python2.4-gadfly python2.4-gd python2.4-gdbm python2.4-geoip python2.4-htmlgen python2.4-htmltmpl python2.4-id3lib python2.4-imaging python2.4-imaging-sane python2.4-jabber python2.4-kde3 python2.4-kjbuckets python2.4-ldap python2.4-librdf python2.4-libxml2 python2.4-libxslt1 python2.4-mysqldb python2.4-numeric python2.4-pam python2.4-pexpect python2.4-pgsql python2.4-pycurl python2.4-pylibacl python2.4-pyopenssl python2.4-pyorbit python2.4-pyxattr python2.4-qt3 python2.4-reportlab python2.4-reportlab-accel python2.4-simpletal python2.4-sip4-qt3 python2.4-soappy python2.4-sqlite python2.4-syck python2.4-tk python2.4-unit python2.4-xml python2.4-xmpp qca-tls qobex radeontool raptor-utils rdesktop rdiff-backup readahead redland-utils ruby ruby1.8 sane-utils scim-qtimm screen scrollkeeper sgml-data skim slocate smartdimmer speedcrunch tcl8.4 tetex-base tetex-bin tetex-doc tetex-extra tex-common tk8.4 toshset ttf-arabeyes ttf-arphic-uming ttf-baekmuk ttf-bengali-fonts ttf-devanagari-fonts ttf-gentium ttf-gujarati-fonts ttf-indic-fonts ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao ttf-malayalam-fonts ttf-mgopen ttf-opensymbol ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg unzip usplash vbetool vcdimager vorbis-tools wlassistant wvdial xcursor-themes xli xscreensaver xscreensaver-data xscreensaver-gl xserver-xorg-input-synaptics xterm zip zlib1g-dev zoo && sudo aptitude update && sudo aptitude install kde-core
```

---

### Post by StreetSmart on 2006-10-14
Will this also reinstall those apps you are talking about that are removed by this installation?

If not, what essential applications are you talking about that I would need to reinstall?

---

### Post by aysiu on 2006-10-14
I don't mean "essential" in some general, universal sense. I mean *essential to you, personally*.

For example, if you look at the command, you'll see it removes AmaroK. Well, a lot of people like AmaroK. You may like AmaroK. In that case, you may want to reinstall it.

---

### Post by StreetSmart on 2006-10-14
Would I be doing this after installing kubuntu or ubuntu?

---

### Post by aysiu on 2006-10-14
Well, **if you haven't installed *anything* yet**, your best bet is to do a server install from the Alternate CD and then ```
sudo aptitude update
sudo aptitude install kde-core
sudo /etc/init.d/kdm start
``` **If you already have Ubuntu installed**, just do this: ```
sudo aptitude update
sudo aptitude install kde-core
``` and then log out, pick KDE from the login screen's session options, and log back in again.

**If you already have Kubuntu installed**, then you would paste in the code I gave you.

---

### Post by StreetSmart on 2006-10-14
Im overwhelmed with all the help youve given me. To tell you the truth I've actually been using Linux for a while. Im going to university now and the fact is, I want a system I can install on my laptop and have absolutly no problems. The answer to this is Ubuntu, as it detects all the hardware I have other than my ATI graphics card which isnt so hard to install. 

I have one more question for you. On my laptop, (Lenovo Thinkpad R60) would you recommend me running the server edition of ubuntu as aposed to the Ubuntu LTS 6.06? My laptop has a T2300 1.66mhz duo core, with 2gigs of ram. So it will pretty much handle any OS.

Thanks again for all the help.

---

### Post by aysiu on 2006-10-14
I don't think you should use the Server Edition unless you want to run a server.

What I was suggesting is slightly different--it's called a "server install" (and it's from the Alternate CD, not the Server CD). The language is a bit confusing, but there is a distinction.

You could probably well handle Kubuntu, but *kde-core* is still faster.

---

