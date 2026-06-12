---
title: "Synaptic reports 400+ upgrades available:  Pull the trigger on all of them?"
date: 2005-10-31
forum: General Help
---

### Post by Doc.Caliban on 2005-10-31
I'm so used to dealing with Windows security updates by the truckload that I'm in the habit of automatically installing every update that comes down the Pike.

Should I do the same with Ubuntu and Synaptic?

Please advise.

-Doc

---

### Post by Xian on 2005-10-31
400+ upgrades on the 5.10 version or an upgrade on 5.04?
Open a terminal and post the output of these commands:

```
$ cat /etc/issue
$ sudo apt-get dist-upgrade
```

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Xian]400+ upgrades on the 5.10 version or an upgrade on 5.04?
Open a terminal and post the output of these commands:

```
$ cat /etc/issue
$ sudo apt-get dist-upgrade
```[/QUOTE]

Thanks for the quick reply.  I was thinking it sounded a little odd....    2 day old install of 5.10.

Results:

<user>@Caliban:~$ cat /etc/issue
Ubuntu 5.10 "Breezy Badger" \n \l

<user>@Caliban:~$ sudo apt-get dist-upgrade
Password:
Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  cupsys-driver-gimpprint-data hotplug libgl1-mesa python-mysqldb
  ubuntu-desktop x-window-system-core xmodmap
The following NEW packages will be installed:
  ca-certificates courier-authdaemon courier-base courier-mta
  cupsys-driver-gutenprint foomatic-db-gutenprint ijsgutenprint libaspell15c2
  libcupsys2 libcurl3-gnutls libdb4.1 libdmx1 libdps1 libegroupwise1.2-5
  libglew1 libgmp3c2 libgnutls12 libgutenprint2 libicu34 libjline-java
  libmagick9 libnet1 libparted1.6-13 libpcap0.7 libroken16-kerberos4kth
  libsensors3 libsepol1 libsnmp9 libssl0.9.8 libxaw8 libxkbui1 libxmlsec1
  libxmlsec1-nss libxmlsec1-openssl linux-image-2.6-386
  linux-image-2.6.14-1-386 mklibs-copy netkit-inetd openssl python2.3
  python2.3-clientcookie python2.3-crypto python2.3-id3lib python2.3-libxml2
  python2.3-musicbrainz python2.3-mysqldb python2.3-numeric python2.3-osd
  python2.3-pyorbit python2.3-qt3 python2.3-sip4-qt3 python2.3-sqlite
  python2.3-syck python2.3-xml readline-common tcptraceroute xlibs xlibs-data
  xpdf-common xpdf-utils
The following packages have been kept back:
  bittorrent contact-lookup-applet gimp-python gksu gnome-doc-utils hplip-base
  hplip-data initramfs-tools python-cddb python-clientcookie python-crypto
  python-gst python-id3lib python-musicbrainz python-netcdf python-numeric
  python-osd python-pisock python-pyorbit python-soappy python-sqlite
  python-syck python-uno xserver-common xserver-xorg xutils
The following packages will be upgraded:
  acpid adduser apt apt-utils aptitude aspell at base-config base-files bash
  bind9-host bogofilter bogofilter-bdb bogofilter-common bsdutils bsh bzip2
  cdrecord console-common console-tools coreutils cpio cpp cpp-4.0 cron cupsys
  cupsys-bsd cupsys-client cupsys-driver-gimpprint d4x dash debconf
  debconf-i18n debianutils dhcp3-client dhcp3-common dictionaries-common
  discover1 discover1-data dmidecode dmsetup dnsutils doc-debian dpkg dselect
  dvd+rw-tools eject ethtool evince evms evms-ncurses fastjar fdutils
  fetchmail file findutils finger fontconfig foomatic-db-engine
  foomatic-db-gimp-print foomatic-filters fping freeglut3 gaim gaim-data gamin
  gcalctool gcc-4.0-base gij gij-4.0 gimp gimp-data gnome-cups-manager
  gnome-keyring gnome-nettool gnome-spell gnome-system-tools gnupg grep grub
  gs-common gs-esp gstreamer0.8-alsa gstreamer0.8-audiofile
  gstreamer0.8-cdparanoia gstreamer0.8-dv gstreamer0.8-dvd gstreamer0.8-esd
  gstreamer0.8-ffmpeg gstreamer0.8-flac gstreamer0.8-gnomevfs gstreamer0.8-gsm
  gstreamer0.8-hermes gstreamer0.8-jpeg gstreamer0.8-misc
  gstreamer0.8-musepack gstreamer0.8-oss gstreamer0.8-plugin-apps
  gstreamer0.8-sdl gstreamer0.8-speex gstreamer0.8-theora gstreamer0.8-vorbis
  gstreamer0.8-x gthumb gtk2-engines-crux gtk2-engines-lighthouseblue
  gtk2-engines-mist gtk2-engines-redmond95 gtk2-engines-thinice gtkhtml3.8
  guile-1.6-libs gzip hdparm hermes1 hicolor-icon-theme hostname hpijs
  hplip-ppds hwdata ifrename ijsgimpprint info initscripts installation-report
  iptables iputils-arping iputils-ping iputils-tracepath java-gcj-compat
  klibc-utils less lftp libaa1 libacl1 libao2 libasound2 libaspell15
  libatk1.0-0 libattr1 libaudio2 libavc1394-0 libbind9-0 libbonobo2-0
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbz2-1.0 libc6
  libc6-i686 libcairo2 libconsole libcupsimage2 libcupsys2-gnutls10 libcurl3
  libdb1-compat libdb3 libdb4.2 libdb4.3 libdevmapper1.01 libdiscover1
  libdjvulibre15 libdns20 libdrm1 libdv4 libdvdread3 libedit2 libevms-2.5
  libflac7 libfontconfig1 libfreetype6 libfribidi0 libgail-common libgail17
  libgamin0 libgc1c2 libgcc1 libgcj-common libgcj6 libgcj6-common libgcrypt11
  libgd2-noxpm libgda2-3 libgda2-common libgeoip1 libgimp2.0 libgksu1.2-0
  libgl1-mesa-dri libglib-perl libglib2.0-0 libglib2.0-data libglu1-mesa
  libgnome-keyring0 libgnome2-vfs-perl libgnomecups1.0-1 libgnomecupsui1.0-1
  libgnucrypto-java libgnujaxp-java libgnujaxp-jni libgnutls11 libgpg-error0
  libgphoto2-2 libgphoto2-port0 libgpmg1 libgsf-1 libgsl0
  libgstreamer-gconf0.8-0 libgstreamer-plugins0.8-0 libgtk2-perl
  libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0
  libguile-ltdl-1 libhsqldb-java libijs-0.35 libisc9 libisccc0 libisccfg1
  libiw28 libjessie-java libklibc libkpathsea3 libkrb53 liblircclient0
  libltdl3 liblwres1 libmagic1 libmdbtools libmpcdec3 libmpeg2-4
  libmusicbrainz2c2 libmusicbrainz4c2 libmyspell3c2 libmysqlclient14
  libncurses5 libncursesw5 libopenal0 libopencdk8 liborbit2 libpam-modules
  libpam-runtime libpam0g libpcap0.8 libperl5.8 libpisock8 libpisync0
  libpng12-0 libpoppler0c2 libpoppler0c2-glib libportaudio0 libpq4
  libqthreads-12 libreadline4 libreadline5 librecode0 libsane libsasl2
  libsasl2-modules libselinux1 libservlet2.3-java libshout3 libslang2 libslp1
  libsmbclient libsndfile1 libsnmp-base libspeex1 libsqlite3-0 libssl0.9.7
  libstdc++6 libtasn1-2 libtext-charwidth-perl libtext-iconv-perl
  libtext-wrapi18n-perl libtiff4 libusb-0.1-4 libvte-common libvte4
  libwmf0.2-7 libwpd8c2 libxalan2-java libxerces2-java libxml2 libxml2-utils
  libxp6 libxslt1.1 libxt-java linux-image-386 locales login logrotate
  lsb-base lsb-release lsof lvm-common lvm2 mdadm memtest86+ mime-support
  mkisofs module-init-tools mount mozilla-thunderbird myspell-en-gb
  myspell-en-us mysql-common nano ncurses-base ncurses-bin net-tools netbase
  ntpdate nvidia-kernel-common odbcinst1debian1 openssh-client parted passwd
  pciutils pcmcia-cs perl perl-base perl-modules pkg-config popularity-contest
  python2.4-crypto python2.4-id3lib python2.4-libxml2 python2.4-libxslt1
  python2.4-mysqldb python2.4-numeric python2.4-osd python2.4-pycurl
  python2.4-pyorbit python2.4-sqlite rdesktop reiser4progs reportbug rss-glx
  rsync samba-common sane-utils sed smbclient ssh-askpass-gnome sudo synaptic
  system-tools-backends sysv-rc sysvinit tcl8.4 tcpdump telnet tk8.4 toshset
  ttf-bengali-fonts ttf-devanagari-fonts ttf-gujarati-fonts ttf-indic-fonts
  ttf-kannada-fonts ttf-malayalam-fonts ttf-mgopen ttf-opensymbol
  ttf-oriya-fonts ttf-punjabi-fonts ttf-tamil-fonts ttf-telugu-fonts ucf udev
  usbutils util-linux vim vim-common vino w3m wget whois wireless-tools
  x-ttcidfont-conf xbase-clients xchat xchat-common xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-scalable xfsprogs xsane xsane-common xscreensaver
  xscreensaver-gl xsltproc zlib1g
392 upgraded, 60 newly installed, 7 to remove and 26 not upgraded.
Need to get 261MB of archives.
After unpacking 161MB of additional disk space will be used.
Do you want to continue [Y/n]?


I said 'No' at this point.

-Doc

---

### Post by Xian on 2005-10-31
Hmmm...please post the output of these commands:

```
$ sudo apt-get update
$ sudo apt-get -f install
```

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Xian]Hmmm...please post the output of these commands:

```
$ sudo apt-get update
$ sudo apt-get -f install
```[/QUOTE]

<user>@Caliban:~$ sudo apt-get update
Password:
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release.gpg
Get:1 [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable Release.gpg [189B]
Hit [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable Release
Ign [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable Release
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy Release
Hit [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable/main Packages
Hit [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable/contrib Packages
Hit [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable/non-free Packages
Hit [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable/main Sources
Hit [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable/contrib Sources
Hit [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable/non-free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Ign [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg [189B]
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release [19.6kB]
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Packages
Get:4 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg [189B]
Get:5 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg [189B]
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/free Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/multiverse Sources
Hit [http://antesis.freecontrib.org](http://antesis.freecontrib.org) breezy/non-free Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/universe Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/multiverse Sources
Fetched 20.0kB in 7s (2657B/s)
Reading package lists... Done
W: GPG error: [http://ftp-mirror.internap.com](http://ftp-mirror.internap.com) unstable Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY F1D53D8C4F368D5D
W: You may want to run apt-get update to correct these problems
<user>@Caliban:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
0 upgraded, 0 newly installed, 0 to remove and 421 not upgraded.

---

### Post by Xian on 2005-10-31
I would advise that you change your /etc/apt/sources.list file
to include the similar entries as below. After making the edits
do the following commands again:

```
$ sudo apt-get update
$ sudo apt-get dist-upgrade
```

Use this command to open the text editor:

```
$ sudo gedit /etc/apt/sources.list
```

Here is the sources.list file you should use as your base:

```
deb http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu breezy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu breezy universe
# deb-src http://us.archive.ubuntu.com/ubuntu breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu breezy-backports main restricted universe multiverse

# Security Updates
deb http://security.ubuntu.com/ubuntu breezy-security main restricted
deb-src http://security.ubuntu.com/ubuntu breezy-security main restricted

## Codecs & DVD 
deb http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
deb-src http://antesis.freecontrib.org/mirrors/ubuntu/plf/ breezy free non-free
```

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Xian]I would advise that you change your /etc/apt/sources.list file
to include the similar entries as below. After making the edits
do the following commands again:[/QUOTE]

0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Can I ask why it's now zero?

Before starting this thread, one of the things that had needed upgrading was Skype which I was having prblems with.  Upgrading it fixed the problem.  It was then that I noticed that there were so many upgrades being offered and decided to post this question.

What are the chances that I didn't need any of the other 400+ upgrades to fix issues I may find?

Very curious about this.

Thanks for the help,

-Doc

---

### Post by Xian on 2005-10-31
[QUOTE=Doc.Caliban]0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

Can I ask why it's now zero?[/quote]

Because now you are using only official and recommended Ubuntu repos. All those "upgrades" were coming from the mirror.internap.com pub. You see how when you removed them all the changes that were planned no longer appeared.

My guess is that internap.com may have some software which would be useful on an individual basis. However, it is probably not a good idea to do a system upgrade with that repo. The fact that it caused apt to want to remove things like hotplug and x-window-system-core would make me very nervous.

---

### Post by Doc.Caliban on 2005-10-31
[QUOTE=Xian]Because now you are using only official and recommended Ubuntu repos. All those "upgrades" were coming from the mirror.internap.com pub. You see how when you removed them all the changes that were planned no longer appeared.

My guess is that internap.com may have some software which would be useful on an individual basis. However, it is probably not a good idea to do a system upgrade with that repo. The fact that it caused apt to want to remove things like hotplug and x-window-system-core would make me very nervous.[/QUOTE]


Thank you for the explanation.  And thanks to both of you for the help!

Best regards,

-Doc

---

