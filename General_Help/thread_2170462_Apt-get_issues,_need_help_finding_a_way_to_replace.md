---
title: "Apt-get issues, need help finding a way to replace files"
date: 2013-08-26
forum: General Help
---

### Post by Scrumps on 2013-08-26
I had some issues with my list files for dpkg/apt-get being corrupt or having issues. The recommendation made to me was to backup the entire folder and then remove all the files listed in that folder.

However now when I use apt-get or dpkg, I get the following error messages (though they are harmless, it is just a lot of screen use)

```

andrew@server:~$ sudo apt-get install openjdk-7-jdk openjdk-7-jre
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  at-spi2-core ca-certificates-java colord desktop-file-utils gvfs gvfs-common
  gvfs-daemons gvfs-libs icedtea-7-jre-jamvm java-common libatk-bridge2.0-0
  libatk-wrapper-java libatk-wrapper-java-jni libatspi2.0-0 libavahi-glib1
  libbonobo2-0 libbonobo2-common libcolord1 libcolorhug1 libexif12 libgconf2-4
  libgd2-xpm libgnome2-0 libgnome2-bin libgnome2-common libgnomevfs2-0
  libgnomevfs2-common libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgusb2 libice-dev libidl-common libidl0
  libieee1284-3 liborbit2 libpthread-stubs0 libpthread-stubs0-dev libsane
  libsane-common libsecret-1-0 libsecret-common libsm-dev libudisks2-0
  libx11-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev libxkbcommon0
  libxt-dev openjdk-7-jre-headless openjdk-7-jre-lib policykit-1-gnome
  ttf-dejavu-extra tzdata-java udisks2 x11proto-core-dev x11proto-input-dev
  x11proto-kb-dev xorg-sgml-doctools xtrans-dev
Suggested packages:
  gvfs-backends default-jre equivs libbonobo2-bin libgd-tools desktop-base
  libgnomevfs2-bin libgnomevfs2-extra gamin fam gnome-mime-data gphoto2 gtkam
  librsvg2-common libice-doc avahi-daemon hpoj hplip libsane-extras sane-utils
  libsm-doc libxcb-doc libxt-doc openjdk-7-demo openjdk-7-source visualvm
  icedtea-7-plugin libnss-mdns sun-java6-fonts fonts-ipafont-gothic
  fonts-ipafont-mincho ttf-wqy-microhei ttf-wqy-zenhei ttf-indic-fonts-core
  ttf-telugu-fonts ttf-oriya-fonts ttf-kannada-fonts ttf-bengali-fonts
  xfsprogs reiserfsprogs exfat-utils btrfs-tools mdadm
The following NEW packages will be installed:
  at-spi2-core ca-certificates-java colord desktop-file-utils gvfs gvfs-common
  gvfs-daemons gvfs-libs icedtea-7-jre-jamvm java-common libatk-bridge2.0-0
  libatk-wrapper-java libatk-wrapper-java-jni libatspi2.0-0 libavahi-glib1
  libbonobo2-0 libbonobo2-common libcolord1 libcolorhug1 libexif12 libgconf2-4
  libgd2-xpm libgnome2-0 libgnome2-bin libgnome2-common libgnomevfs2-0
  libgnomevfs2-common libgphoto2-2 libgphoto2-l10n libgphoto2-port0 libgtk-3-0
  libgtk-3-bin libgtk-3-common libgusb2 libice-dev libidl-common libidl0
  libieee1284-3 liborbit2 libpthread-stubs0 libpthread-stubs0-dev libsane
  libsane-common libsecret-1-0 libsecret-common libsm-dev libudisks2-0
  libx11-dev libx11-doc libxau-dev libxcb1-dev libxdmcp-dev libxkbcommon0
  libxt-dev openjdk-7-jdk openjdk-7-jre openjdk-7-jre-headless
  openjdk-7-jre-lib policykit-1-gnome ttf-dejavu-extra tzdata-java udisks2
  x11proto-core-dev x11proto-input-dev x11proto-kb-dev xorg-sgml-doctools
  xtrans-dev
0 upgraded, 67 newly installed, 0 to remove and 0 not upgraded.
Need to get 75.9 MB of archives.
After this operation, 143 MB of additional disk space will be used.
Do you want to continue [Y/n]? 
Get:1 http://us.archive.ubuntu.com/ubuntu/ raring/main libatspi2.0-0 amd64 2.8.0-1 [58.7 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ raring/main libatk-bridge2.0-0 amd64 2.8.1-1 [59.5 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main openjdk-7-jre-lib all 7u25-2.3.10-1ubuntu0.13.04.2 [5,541 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ raring/main ca-certificates-java all 20121112+nmu2 [13.6 kB]
Get:5 http://us.archive.ubuntu.com/ubuntu/ raring/main tzdata-java all 2013b-1ubuntu1 [141 kB]
Get:6 http://us.archive.ubuntu.com/ubuntu/ raring/main java-common all 0.43ubuntu4 [134 kB]
Get:7 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main openjdk-7-jre-headless amd64 7u25-2.3.10-1ubuntu0.13.04.2 [35.5 MB]
Get:8 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main openjdk-7-jre amd64 7u25-2.3.10-1ubuntu0.13.04.2 [227 kB]
Get:9 http://us.archive.ubuntu.com/ubuntu/ raring/main libatk-wrapper-java all 0.30.4-0ubuntu4 [29.8 kB]
Get:10 http://us.archive.ubuntu.com/ubuntu/ raring/main libatk-wrapper-java-jni amd64 0.30.4-0ubuntu4 [31.1 kB]
Get:11 http://us.archive.ubuntu.com/ubuntu/ raring/main libavahi-glib1 amd64 0.6.31-1ubuntu3 [8,860 B]
Get:12 http://us.archive.ubuntu.com/ubuntu/ raring/main libbonobo2-common all 2.32.1-0ubuntu3 [34.1 kB]
Get:13 http://us.archive.ubuntu.com/ubuntu/ raring/main libidl-common all 0.8.14-0.2ubuntu3 [8,536 B]
Get:14 http://us.archive.ubuntu.com/ubuntu/ raring/main libidl0 amd64 0.8.14-0.2ubuntu3 [81.6 kB]
Get:15 http://us.archive.ubuntu.com/ubuntu/ raring/main liborbit2 amd64 1:2.14.19-0.1ubuntu2 [147 kB]
Get:16 http://us.archive.ubuntu.com/ubuntu/ raring/main libbonobo2-0 amd64 2.32.1-0ubuntu3 [216 kB]
Get:17 http://us.archive.ubuntu.com/ubuntu/ raring/main libgusb2 amd64 0.1.5-0ubuntu1 [18.5 kB]
Get:18 http://us.archive.ubuntu.com/ubuntu/ raring/main libcolord1 amd64 0.1.30-0ubuntu3 [85.7 kB]
Get:19 http://us.archive.ubuntu.com/ubuntu/ raring/main libexif12 amd64 0.6.21-1 [93.4 kB]
Get:20 http://us.archive.ubuntu.com/ubuntu/ raring/main libgd2-xpm amd64 2.0.36~rc1~dfsg-6.1ubuntu1 [202 kB]
Get:21 http://us.archive.ubuntu.com/ubuntu/ raring/main libgnomevfs2-common amd64 1:2.24.4-1ubuntu5 [23.1 kB]
Get:22 http://us.archive.ubuntu.com/ubuntu/ raring/main libgnomevfs2-0 amd64 1:2.24.4-1ubuntu5 [210 kB]
Get:23 http://us.archive.ubuntu.com/ubuntu/ raring/main libgnome2-common all 2.32.1-2ubuntu4 [33.3 kB]
Get:24 http://us.archive.ubuntu.com/ubuntu/ raring/main libgnome2-bin amd64 2.32.1-2ubuntu4 [15.0 kB]
Get:25 http://us.archive.ubuntu.com/ubuntu/ raring/main libgnome2-0 amd64 2.32.1-2ubuntu4 [43.1 kB]
Get:26 http://us.archive.ubuntu.com/ubuntu/ raring/main libgphoto2-port0 amd64 2.4.14-2 [45.4 kB]
Get:27 http://us.archive.ubuntu.com/ubuntu/ raring/main libgphoto2-2 amd64 2.4.14-2 [1,009 kB]
Get:28 http://us.archive.ubuntu.com/ubuntu/ raring/main libgtk-3-common all 3.6.4-0ubuntu8 [148 kB]
Get:29 http://us.archive.ubuntu.com/ubuntu/ raring/main libxkbcommon0 amd64 0.2.0-0ubuntu3 [138 kB]
Get:30 http://us.archive.ubuntu.com/ubuntu/ raring/main at-spi2-core amd64 2.8.0-1 [50.7 kB]
Get:31 http://us.archive.ubuntu.com/ubuntu/ raring/main libgtk-3-0 amd64 3.6.4-0ubuntu8 [1,811 kB]
Get:32 http://us.archive.ubuntu.com/ubuntu/ raring/main libieee1284-3 amd64 0.2.11-10build2 [23.6 kB]
Get:33 http://us.archive.ubuntu.com/ubuntu/ raring/main libsane-common amd64 1.0.23-0ubuntu1 [514 kB]
Get:34 http://us.archive.ubuntu.com/ubuntu/ raring/main libsane amd64 1.0.23-0ubuntu1 [3,789 kB]
Get:35 http://us.archive.ubuntu.com/ubuntu/ raring/main libsecret-common all 0.15-0ubuntu1 [3,878 B]
Get:36 http://us.archive.ubuntu.com/ubuntu/ raring/main libsecret-1-0 amd64 0.15-0ubuntu1 [116 kB]
Get:37 http://us.archive.ubuntu.com/ubuntu/ raring/main libudisks2-0 amd64 2.1.0-2 [127 kB]
Get:38 http://us.archive.ubuntu.com/ubuntu/ raring/main ttf-dejavu-extra all 2.33-3ubuntu2 [1,680 kB]
Get:39 http://us.archive.ubuntu.com/ubuntu/ raring/main udisks2 amd64 2.1.0-2 [201 kB]
Get:40 http://us.archive.ubuntu.com/ubuntu/ raring/main libcolorhug1 amd64 0.1.30-0ubuntu3 [25.4 kB]
Get:41 http://us.archive.ubuntu.com/ubuntu/ raring/main colord amd64 0.1.30-0ubuntu3 [263 kB]
Get:42 http://us.archive.ubuntu.com/ubuntu/ raring/main desktop-file-utils amd64 0.21-0ubuntu3 [66.1 kB]
Get:43 http://us.archive.ubuntu.com/ubuntu/ raring/main gvfs-common all 1.16.1-0ubuntu1 [40.3 kB]
Get:44 http://us.archive.ubuntu.com/ubuntu/ raring/main gvfs-libs amd64 1.16.1-0ubuntu1 [103 kB]
Get:45 http://us.archive.ubuntu.com/ubuntu/ raring/main gvfs-daemons amd64 1.16.1-0ubuntu1 [109 kB]
Get:46 http://us.archive.ubuntu.com/ubuntu/ raring/main gvfs amd64 1.16.1-0ubuntu1 [89.0 kB]
Get:47 http://us.archive.ubuntu.com/ubuntu/ raring/main libgconf2-4 amd64 3.2.6-0ubuntu1 [2,046 B]
Get:48 http://us.archive.ubuntu.com/ubuntu/ raring/main libgphoto2-l10n all 2.4.14-2 [7,470 B]
Get:49 http://us.archive.ubuntu.com/ubuntu/ raring/main libgtk-3-bin amd64 3.6.4-0ubuntu8 [18.2 kB]
Get:50 http://us.archive.ubuntu.com/ubuntu/ raring/main xorg-sgml-doctools all 1:1.10-1 [12.0 kB]
Get:51 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-core-dev all 7.0.23-1 [744 kB]
Get:52 http://us.archive.ubuntu.com/ubuntu/ raring/main libice-dev amd64 2:1.0.8-2 [57.6 kB]
Get:53 http://us.archive.ubuntu.com/ubuntu/ raring/main libpthread-stubs0 amd64 0.3-3 [3,258 B]
Get:54 http://us.archive.ubuntu.com/ubuntu/ raring/main libpthread-stubs0-dev amd64 0.3-3 [2,866 B]
Get:55 http://us.archive.ubuntu.com/ubuntu/ raring/main libsm-dev amd64 2:1.2.1-2 [19.9 kB]
Get:56 http://us.archive.ubuntu.com/ubuntu/ raring/main libxau-dev amd64 1:1.0.7-1 [10.2 kB]
Get:57 http://us.archive.ubuntu.com/ubuntu/ raring/main libxdmcp-dev amd64 1:1.1.1-1 [26.9 kB]
Get:58 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-input-dev all 2.2.99.1-0ubuntu1 [139 kB]
Get:59 http://us.archive.ubuntu.com/ubuntu/ raring/main x11proto-kb-dev all 1.0.6-2 [269 kB]
Get:60 http://us.archive.ubuntu.com/ubuntu/ raring/main xtrans-dev all 1.2.7-1 [84.3 kB]
Get:61 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libxcb1-dev amd64 1.8.1-2ubuntu2.1 [82.6 kB]
Get:62 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libx11-dev amd64 2:1.5.0-1ubuntu1.1 [911 kB]
Get:63 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libx11-doc all 2:1.5.0-1ubuntu1.1 [2,448 kB]
Get:64 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main libxt-dev amd64 1:1.1.3-1ubuntu0.13.04.1 [493 kB]
Get:65 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main openjdk-7-jdk amd64 7u25-2.3.10-1ubuntu0.13.04.2 [16.6 MB]
Get:66 http://us.archive.ubuntu.com/ubuntu/ raring/main policykit-1-gnome amd64 0.105-1ubuntu4 [27.8 kB]
Get:67 http://us.archive.ubuntu.com/ubuntu/ raring-updates/main icedtea-7-jre-jamvm amd64 7u25-2.3.10-1ubuntu0.13.04.2 [586 kB]
Fetched 75.9 MB in 34s (2,204 kB/s)                                            
Extracting templates from packages: 100%
Selecting previously unselected package libatspi2.0-0:amd64.
dpkg: warning: files list file for package 'libio-string-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'znc-python' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kde-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxau6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblockfile1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython2.7-minimal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qapt-batch' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lsof' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5-3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkjsembed4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwrap0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'usbmuxd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtorrent11' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnfnetlink0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkemoticons4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'upower' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'policykit-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapr1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinyxml2-0.0.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-sound-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'readline-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libntrack0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxt6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-charwidth-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmessaging-menu0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgomp1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasyncns0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libglib2.0-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'less' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dconf-service' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'nepomuk-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kvirc-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-alsa:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkalarmcal2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ssh-import-id' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-qt-1-1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'binutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-siliconmotion' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-ati' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-debian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-tiny' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'strace' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'update-notifier-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ca-certificates' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'isc-dhcp-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pulseaudio' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhtml-tagset-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'hardening-includes' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cryptsetup-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmpfr4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'plasma-scriptengine-javascript' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'klipper' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkabc4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'zip' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatkmm-1.6-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcsclite1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvisual-0.4-plugins:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstdc++6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'powermgmt-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cpio' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'konqueror' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'installation-report' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'rsyslog' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfontenc1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'freespacenotifier' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libakonadiprotocolinternals1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libppl12:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apparmor' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'popularity-contest' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-minimal' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-x:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mysql-server-core-5.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisccfg90' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qtchooser' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgbm1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xfonts-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcursor1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhunspell-1.3-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'patchutils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-levenshtein-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'util-linux' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmp10:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'make' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'bash' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbusmenu-qt2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lightdm-kde-greeter' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqt4-xmlpatterns:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iptables' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libisc92' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgee2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libyajl2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnuma1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxklavier16' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'znc-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpixman-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwayland0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libclone-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmediainfo0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'udev' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkonqsidebarplugin4a' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'nepomuk-core-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kdepim-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdee-1.0-4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-image-extra-3.8.0-19-generic' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpng12-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-plugins-good:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxxf86vm1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsolidcontrol4abi2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'php5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-ck-connector:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'language-selector-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'oxygen-cursor-theme' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'w3m' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdmtx0a:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsm6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtalloc2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaa1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vim-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ntpdate' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libiw30:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libevent-2.0-5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-openssl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'vbetool' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaudit-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openssh-client' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython2.7-stdlib:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkdesu5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-software-properties' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libselinux1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'time' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libx11-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnettle4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnih-dbus1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libatk1.0-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcb-shape0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'firefox' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'znc-tcl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtk2.0-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libplasmagenericshell4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libparse-debianchangelog-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libp11-kit0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkgapi0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'landscape-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libjson0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'pppoeconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libice6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcryptsetup4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-input-mouse' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libemail-valid-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'aspell' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libipc-run-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dconf-gsettings-backend:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'nano' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libegl1-mesa:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcdparanoia0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxtst6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libedit2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'fontconfig-config' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'multiarch-support' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xchat' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-input-all' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libakonadi-kmime4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqt4-xml:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cron' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libicu48:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkdeclarative5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'sysvinit-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xml-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnss3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'biosdevname' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdbusmenu-gtk4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'phonon:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmhash2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkrb5-26-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-plugins-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxcb-xfixes0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libldap-2.4-2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'cifs-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apache2.2-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libapache2-mod-php5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'alsa-base' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mime-support' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkatepartinterfaces4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gconf2' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tdb-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'librasqal3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'linux-firmware' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'php5-cli' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libc-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libavahi-client3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqt4-qt3support:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gcc-4.7-base:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libexiv2-12' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpciaccess0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'unzip' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apache2.2-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mediainfo' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-pkg-resources' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'chromium-browser-l10n' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xul-ext-ubufox' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsub-name-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvorbis0a:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libx11-xcb1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libio-pty-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'konqueror-nsplugins' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtag1c2a:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-apt-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtinfo5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'oxygen-icon-theme' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblightdm-qt-2-0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'wireless-tools' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdrm-intel1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfftw3-single3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'chromium-codecs-ffmpeg-extra' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhtml-parser-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'friendly-recovery' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcaca0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-mach64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-problem-report' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkpimutils4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-intel' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbind9-90' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libvisual-0.4-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libbz2-1.0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'aptitude-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasn1-8-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkcal4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgssapi3-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'qdbus' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgettextpo-dev:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-tracepath' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-trident' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 't1utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libheimbase1-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ttf-dejavu-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkdecore5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblcms1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iputils-ping' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'diffstat' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'lightdm' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-s3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kde-workspace-kgreet-plugins' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libio-socket-ssl-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libilmbase6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'busybox-initramfs' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'alsa-utils' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gir1.2-glib-2.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'irqbalance' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmtdev1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkolabxml0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfile-copy-recursive-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libcap-ng0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kde-base-artwork' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'eject' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gstreamer0.10-pulseaudio:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'samba-common-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmsetup' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'aptdaemon' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'crda' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libheimntlm0-heimdal:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-twisted-core' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'software-properties-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libencode-locale-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-pam' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqalculate5-data' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'glib-networking-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-apport' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-xapian' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libqapt2-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ubuntu-keyring' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblocale-gettext-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libncursesw5:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'iso-codes' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libmailtransport4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'aptitude' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpcre3:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libv4lconvert0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnet-ssleay-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-chardet' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'grub-pc' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dpkg' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libwww-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gzip' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'insserv' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python3-distupgrade' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkcalutils4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libdb5.1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgpm2:amd64' missing; assuming package has no files currently installed


```

This happens for all packages that I have installed, so I was wondering if there was any form of script that I could use to resolve this. I had someone suggest this to me:

for package in $(apt-get upgrade 2>&1 | grep "warning: files list file" | sed "s/.*'//; s/://"); do apt-get install --reinstall "$package"; done


But that didn't seem to do anything, it just returns to a new line after being executed.

Thanks for any assistance.

---

### Post by GwL3eNC on 2013-08-26
Hmm, i have never seen that. I would like to test the --fix-missing option

sudo apt-get -f --fix-missing install

I dont know if it helps.

---

### Post by David_Pecot on 2013-08-26
> I had some issues with my list files for dpkg/apt-get being corrupt or  having issues. The recommendation made to me was to backup the entire  folder and then remove all the files listed in that folder.

I'd assume this was bad advice.  What was the original problem?

---

### Post by tgalati4 on 2013-08-27
What is the output of:

```
sudo apt-get check
sudo apt-get clean
```

---

### Post by Scrumps on 2013-08-27
sudo apt-get -f --fix-missing install doesn't do anything either, since no packages are missing.

The original problem was that the files were all corrupted (or were mistreated someway that caused them to be corrupted) which didn't allow me to install any packages. Moving them allows me to install packages now.

If I do the two commands:
andrew@server:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree       
Reading state information... Done
andrew@server:~$ sudo apt-get clean
andrew@server:~$

EDIT: Multi-quote did not work

---

### Post by Scrumps on 2013-08-30
Bump, would greatly appreciate some help, as I was trying to install okular, and was running into some more issues (a long with the others reported in this thread)

---

### Post by David_Pecot on 2013-08-31
I'm really not an expert as such.  I'd probably re-install my O/S at this point - in fact I do that about once a year anyway (it's maybe an hour of work getting settings as I like them and installing my favorite programs but then all is well and I'm up to the latest and greatest version of *buntu (Xubuntu, in my case).  It's not really so hard to do.  Probably not a good solution in the technical sense but does have the virtue of "cutting the gordian knot".  Personally I've used *buntu for the last 7 years or more and never had the slightest trouble installing anything so you may be overdue for a big "cleaning".

---

### Post by Scrumps on 2013-09-01
That would be great except for a few things:
1) This is a new install (with a newly burned disc, which I did verify was burned correctly)
2) Reinstalling an OS every year is ridiculous, especially when this is a server install.
3) I am a little over two hours away from the machine, and I don't have the time to go back and re-install the system, again. So... I need to work with what I have and fix what is wrong.

There isn't anything broken, so much as that it just doesn't think the packages are installed, even though they are. So if I were to find a script that would reinstall them, that would fix all the errors.

---

### Post by Bashing-om on 2013-09-01
Scrumps; Hi !

Yeah, I would also think it is but a config problem.
This output however does not indicate a "expected" direction to look to.
> 
If I do the two commands:
andrew@server:~$ sudo apt-get check
Reading package lists... Done
Building dependency tree 
Reading state information... Done
andrew@server:~$ sudo apt-get clean
andrew@server:~$

Back to square 1 and see what apt reports from:
```

sudo apt-get update
sudo apt-get upgrade

```
then we can look at cleaning up the system and look for errors.

[INDENT][INDENT]it's all in the process
[/INDENT][/INDENT]

---

### Post by steeldriver on 2013-09-02
> **Scrumps said:**
> There isn't anything broken, so much as that it just doesn't think the packages are installed, even though they are. So if I were to find a script that would reinstall them, that would fix all the errors.

I don't know if reinstalling the packages *will* fix everything, but I think the reason your previous attempt didn't do so is that the 'sed' expression is incorrect (it doesn't extract the package names from the apt-get upgrade output). There are other ways to do it but assuming the original intent was to replace everything up to and including the 1st ' and then replace everything from the 2nd ' on, it needs to be something like sed "s/**[^']*'**//; s/**'[^']***//"

Rather than parsing the stderr from another upgrade attempt directly, I'd start by pasting the warnings from your first post into a separate text file e.g. *warnlist.txt*, then try

```
while read pkg; do echo sudo apt-get install --reinstall "$pkg"; done < <(sed "s/[^']*'//; s/'[^']*//" warnlist.txt)
```

or (a bit easier on the eye - and harder to mistype) use 'awk' instead of 'sed'  - this is the way I'd actually recommend

```
while read pkg; do echo sudo apt-get install --reinstall "$pkg"; done < <(awk '{print $8}' warnlist.txt)
```

(field $8 includes the single-quotes, whereas the sed expression strips them, but that's OK). Note that I have left an 'echo' in - neither expression will actually execute the apt-get installs until you remove that - try it first and make sure it produces the correct command lines. You may need to add a -y to the apt-get to skip confirmations.

---

### Post by Scrumps on 2013-09-02
> **Bashing-om said:**
> Scrumps; Hi !

Yeah, I would also think it is but a config problem.
This output however does not indicate a "expected" direction to look to.

Back to square 1 and see what apt reports from:
```

sudo apt-get update
sudo apt-get upgrade

```
then we can look at cleaning up the system and look for errors.
[INDENT][INDENT]it's all in the process
[/INDENT]
[/INDENT]


sudo apt-get update and sudo apt-get upgrade both work as expected, there is no errors displayed, but no upgrades processed.

> **steeldriver said:**
> I don't know if reinstalling the packages *will* fix everything, but I think the reason your previous attempt didn't do so is that the 'sed' expression is incorrect (it doesn't extract the package names from the apt-get upgrade output). There are other ways to do it but assuming the original intent was to replace everything up to and including the 1st ' and then replace everything from the 2nd ' on, it needs to be something like sed "s/**[^']*'**//; s/**'[^']***//"

Rather than parsing the stderr from another upgrade attempt directly, I'd start by pasting the warnings from your first post into a separate text file e.g. *warnlist.txt*, then try

```
while read pkg; do echo sudo apt-get install --reinstall "$pkg"; done < <(sed "s/[^']*'//; s/'[^']*//" warnlist.txt)
```

or (a bit easier on the eye - and harder to mistype) use 'awk' instead of 'sed'  - this is the way I'd actually recommend

```
while read pkg; do echo sudo apt-get install --reinstall "$pkg"; done < <(awk '{print $8}' warnlist.txt)
```

(field $8 includes the single-quotes, whereas the sed expression strips them, but that's OK). Note that I have left an 'echo' in - neither expression will actually execute the apt-get installs until you remove that - try it first and make sure it produces the correct command lines. You may need to add a -y to the apt-get to skip confirmations.


So I just want to make sure I understand what you are saying.

The commands that you posted will check the file "warnlist.txt" for the commands to process, and the commands you posted won't do anything in the first place until I remove the echo command that is listed there. Correct?

---

### Post by steeldriver on 2013-09-02
[COLOR=#0000ff]Oops I just checked it again and the single quotes around the package name do need to be stripped off - see my edit below if you use the awk version[/COLOR] but yes, you paste the *dpkg: warning* lines into warnlist.txt i.e.

```
dpkg: warning: files list file for package 'libio-string-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'znc-python' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kde-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxau6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblockfile1:amd64' missing; assuming package has no files currently installed
.
.
.

```

and then 

```

$ while read pkg; do sudo apt-get install --reinstall "$pkg"; done < <(awk '{[COLOR=#0000ff]**gsub("\047","",$8);**[/COLOR] print $8}' warnlist.txt)
sudo apt-get install --reinstall libio-string-perl
sudo apt-get install --reinstall znc-python
sudo apt-get install --reinstall kde-runtime
sudo apt-get install --reinstall libxau6:amd64
sudo apt-get install --reinstall liblockfile1:amd64
.
.
.

```

---

### Post by Scrumps on 2013-09-03
> **steeldriver said:**
> [COLOR=#0000ff]Oops I just checked it again and the single quotes around the package name do need to be stripped off - see my edit below if you use the awk version[/COLOR] but yes, you paste the *dpkg: warning* lines into warnlist.txt i.e.

```
dpkg: warning: files list file for package 'libio-string-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'znc-python' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kde-runtime' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxau6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'liblockfile1:amd64' missing; assuming package has no files currently installed
.
.
.

```

and then 

```

$ while read pkg; do sudo apt-get install --reinstall "$pkg"; done < <(awk '{[COLOR=#0000ff]**gsub("\047","",$8);**[/COLOR] print $8}' warnlist.txt)
sudo apt-get install --reinstall libio-string-perl
sudo apt-get install --reinstall znc-python
sudo apt-get install --reinstall kde-runtime
sudo apt-get install --reinstall libxau6:amd64
sudo apt-get install --reinstall liblockfile1:amd64
.
.
.

```

For some that did work, but others seem to still be producing the error. Though, the list has definitely by far shrunk:

The end of the original list:
> 
[....]
dpkg: warning: files list file for package 'libnl-3-200:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libattica0.4:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgl1-mesa-dri:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpoppler28:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libxdmcp6:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnepomukwidgets4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'shared-mime-info' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libraw1394-11:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kdelibs5-plugins' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpolkit-gobject-1-0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-six' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsocket6-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kdepimlibs-kio-plugins' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dash' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'memtest86+' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libelf1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libasprintf0c2:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kdepasswd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-common' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'debconf' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libhttp-date-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-winbind:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgmpxx4ldbl:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsyndication4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libustr-1.0-1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libtext-wrapi18n-perl' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libnotify-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-urllib3' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'mysql-client-core-5.5' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tcpd' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python-pkg-resources' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'kde-baseapps-bin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkfile4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-input-vmmouse' missing; assuming package has no files currently installed


The end of the new list:
> 
[....]
dpkg: warning: files list file for package 'xserver-xorg-input-wacom' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libfontconfig1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'gettext' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkwinglutils1abi1' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libboost-program-options1.49.0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libkldap4' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'python' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libudev1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'tzdata' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-vmware' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-modules:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libelfg0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'apt-transport-https' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgtkmm-2.4-1c2a:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpam-smbpass:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'dmidecode' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libaspell15' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libsepol1:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpulse-mainloop-glib0:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'ntfs-3g' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libstreams0' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'xserver-xorg-video-openchrome' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'whiptail' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libpython-stdlib:amd64' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'webmin' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'openvpn-as' missing; assuming package has no files currently installed




I know some of these are .deb files that I would need to reinstall (like webmin or openvpn-as) but others, I think are part of the base install for ubuntu. Would it be safe to just do this again, and see if they are added?

---

### Post by steeldriver on 2013-09-03
I don't see why it wouldn't be safe to run again - but did you notice what errors the first run produced? were those packages not found the first time?

---

