---
title: "System error after running dpkg"
date: 2015-06-28
forum: General Help
---

### Post by Tim_English on 2015-06-28
Any time i try to update or install a package manually using the terminal or whether it be through the automated update program dpkg always fails

I tried running: "sudo apt-get upgrade" all packages downloaded fine and it failed when dpkg tried to run, here is the terminal output at point of failure, this has been going on for a while and i hope someone can help me come to a solution:


Preconfiguring packages ...
dpkg: malloc.c:2372: sysmalloc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 *(sizeof(size_t))) - 1)) & ~((2 *(sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long) old_end & pagemask) == 0)' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly

---

### Post by llamabr on 2015-06-28
I don't know.  Perhaps copy the entire output, and not just this bit?

---

### Post by Tim_English on 2015-06-28
Here is the entire output of "sudo apt-get upgrade" also should note this was done after "sudo apt-get update" and that completed with no errors

```
tim@tim-Presario-A900:~$ sudo apt-get upgrade
[sudo] password for tim: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages were automatically installed and are no longer required:
  account-plugin-windows-live libupstart1
Use 'apt-get autoremove' to remove them.
The following packages have been kept back:
  linux-generic-lts-utopic linux-headers-generic-lts-utopic
  linux-image-generic-lts-utopic
The following packages will be upgraded:
  account-plugin-aim account-plugin-facebook account-plugin-flickr
  account-plugin-google account-plugin-jabber account-plugin-salut
  account-plugin-twitter account-plugin-windows-live account-plugin-yahoo
  accountsservice apparmor apport apport-gtk apt apt-transport-https apt-utils
  aptdaemon aptdaemon-data binutils compiz compiz-core compiz-gnome
  compiz-plugins-default compizconfig-settings-manager cpp-4.8 cups cups-bsd
  cups-client cups-common cups-core-drivers cups-daemon cups-ppdc
  cups-server-common curl dnsmasq-base dpkg dpkg-dev empathy empathy-common
  firefox firefox-locale-en fonts-droid fonts-opensymbol fuse g++-4.8 gcc-4.8
  gcc-4.8-base gcc-4.8-base:i386 gdisk ghostscript ghostscript-x
  gir1.2-gtk-3.0 gir1.2-gudev-1.0 gir1.2-networkmanager-1.0 gir1.2-udisks-2.0
  gir1.2-wnck-3.0 gnome-desktop3-data gnome-session-bin gnome-session-common
  google-chrome-stable grub-common grub-pc grub-pc-bin grub2-common gvfs
  gvfs-backends gvfs-bin gvfs-common gvfs-daemons gvfs-fuse gvfs-libs
  indicator-session initscripts isc-dhcp-client isc-dhcp-common lib32stdc++6
  libaccount-plugin-generic-oauth libaccount-plugin-google libaccountsservice0
  libapparmor-perl libapparmor1 libapt-inst1.5 libapt-pkg4.12 libasan0
  libatomic1 libcompizconfig0 libcups2 libcups2:i386 libcupscgi1 libcupsimage2
  libcupsmime1 libcupsppdc1 libcurl3 libcurl3-gnutls libdecoration0
  libdpkg-perl libdrm-intel1 libdrm-intel1:i386 libdrm-nouveau2
  libdrm-nouveau2:i386 libdrm-radeon1 libdrm-radeon1:i386 libdrm2 libdrm2:i386
  libfuse2 libgail-3-0 libgail-common libgail18 libgcc-4.8-dev
  libgnome-desktop-3-7 libgnutls28 libgomp1 libgs9 libgs9-common libgtk-3-0
  libgtk-3-bin libgtk-3-common libgtk2.0-0 libgtk2.0-bin libgtk2.0-common
  libgudev-1.0-0 libicu52 libitm1 libldap-2.4-2 libldap-2.4-2:i386
  libmetacity-private0a libnautilus-extension1a libnm-glib-vpn1 libnm-glib4
  libnm-util2 libnuma1 liboxideqt-qmlplugin liboxideqtcore0 liboxideqtquick0
  libpam-systemd libpolkit-agent-1-0 libpolkit-backend-1-0
  libpolkit-gobject-1-0 libpython2.7 libpython2.7-minimal libpython2.7-stdlib
  libpython3.4 libpython3.4-minimal libpython3.4-stdlib libqt4-dbus
  libqt4-declarative libqt4-designer libqt4-help libqt4-network libqt4-opengl
  libqt4-script libqt4-scripttools libqt4-sql libqt4-sql-sqlite libqt4-svg
  libqt4-test libqt4-xml libqt4-xmlpatterns libqt5core5a libqt5dbus5
  libqt5gui5 libqt5network5 libqt5opengl5 libqt5printsupport5 libqt5sql5
  libqt5sql5-sqlite libqt5test5 libqt5widgets5 libqt5xml5 libqtcore4
  libqtdbus4 libqtgui4 libquadmath0 libreoffice-avmedia-backend-gstreamer
  libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core
  libreoffice-draw libreoffice-gnome libreoffice-gtk libreoffice-help-en-us
  libreoffice-impress libreoffice-math libreoffice-ogltrans
  libreoffice-pdfimport libreoffice-presentation-minimizer
  libreoffice-style-human libreoffice-writer libssl1.0.0 libssl1.0.0:i386
  libstdc++-4.8-dev libstdc++6 libstdc++6:i386 libsystemd-daemon0
  libsystemd-journal0 libsystemd-login0 libtasn1-6 libtasn1-6:i386 libtsan0
  libudev1 libudev1:i386 libudisks2-0 libunity-core-6.0-9 libwnck-3-0
  libwnck-3-common libxext6 libxext6:i386 libxfixes3 libxfixes3:i386 libxi6
  libxi6:i386 libxrender1 libxrender1:i386 linux-firmware linux-libc-dev
  mcp-account-manager-uoa metacity metacity-common nautilus nautilus-data
  nautilus-sendto-empathy network-manager ntpdate openjdk-7-jre
  openjdk-7-jre-headless openssl oxideqt-codecs patch policykit-1 ppp
  python-aptdaemon python-aptdaemon.gtk3widgets python-compizconfig
  python-pkg-resources python-requests python-six python-urllib3 python2.7
  python2.7-minimal python3-apport python3-aptdaemon
  python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-chardet
  python3-pkg-resources python3-problem-report python3-requests python3-six
  python3-uno python3-update-manager python3-urllib3 python3.4
  python3.4-minimal qdbus qtcore4-l10n rsyslog systemd-services sysv-rc
  sysvinit-utils t1utils tcpdump thunderbird thunderbird-gnome-support
  thunderbird-locale-en thunderbird-locale-en-us tzdata tzdata-java
  ubuntu-drivers-common ubuntu-session udev udisks2 unity unity-services
  uno-libs3 unrar update-manager update-manager-core ure usb-creator-common
  usb-creator-gtk wpasupplicant xserver-xorg-video-intel-lts-utopic
283 upgraded, 0 newly installed, 0 to remove and 3 not upgraded.
Need to get 0 B/395 MB of archives.
After this operation, 21.1 MB of additional disk space will be used.
Do you want to continue? [Y/n] y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: malloc.c:2372: sysmalloc: Assertion `(old_top == (((mbinptr) (((char *) &((av)->bins[((1) - 1) * 2])) - __builtin_offsetof (struct malloc_chunk, fd)))) && old_size == 0) || ((unsigned long) (old_size) >= (unsigned long)((((__builtin_offsetof (struct malloc_chunk, fd_nextsize))+((2 *(sizeof(size_t))) - 1)) & ~((2 *(sizeof(size_t))) - 1))) && ((old_top)->size & 0x1) && ((unsigned long) old_end & pagemask) == 0)' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

---

### Post by llamabr on 2015-07-04
That's weird.  Post the contents of your /etc/apt/sources.list (and possibly, /etc/apt/sources.list.d/).  It looks like there may be some trash in there that's screwing up dpkg

---

