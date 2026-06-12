---
title: "libglib2.0-dev:i386 package corrupted my ubuntu!"
date: 2013-02-16
forum: General Help
---

### Post by labidus on 2013-02-16
I needed to install 32 bits lib on my 64 bits sytem, i saw a thread that say I needed to install some package including this : libglib2.0-dev:i386

so i started to install the package, I realised to late, that this package was removing very important packages that corrupted and even remove some app etc.. not related to dev, anyway what I can do to restore them since 

Here what he remove:

```

The following packages will be REMOVED:
  activity-log-manager-control-center aisleriot apt-xapian-index apturl compiz
  compiz-gnome deja-dup duplicity gconf2 gedit gir1.2-ubuntuoneui-3.0 gksu
  gnome-control-center gnome-control-center-signon gnome-media gnome-menus
  gnome-sudoku gnome-terminal gnome-terminal-data gnome-user-share
  gstreamer0.10-gconf gwibber gwibber-service gwibber-service-facebook
  gwibber-service-identica gwibber-service-twitter hplip hplip-data ibus
  ibus-pinyin ibus-table indicator-cpufreq indicator-datetime indicator-power
  landscape-client-ui-install libboost-mpi-python-dev
  libboost-mpi-python1.49-dev libboost-mpi-python1.49.0 libgksu2-0
  libgnome-media-profiles-3.0-0 libgwibber-gtk3 libgwibber3 libpurple-bin
  libreoffice-gnome libsyncdaemon-1.0-1 libubuntuoneui-3.0-1 light-themes
  lightdm-remote-session-uccsconfigure mysql-utilities mysql-workbench
  nautilus-share nmap oneconf printer-driver-postscript-hp
  printer-driver-sag-gdi python python-appindicator python-apport python-apt
  python-aptdaemon python-aptdaemon.gtk3widgets python-cairo python-chardet
  python-configglue python-crypto python-cups python-cupshelpers python-dbus
  python-debian python-debtagshw python-defer python-dev python-dirspec
  python-gconf python-gi python-gi-cairo python-gnomekeyring
  python-gnupginterface python-gobject python-gobject-2 python-gst0.10
  python-gtk2 python-httplib2 python-ibus python-imaging python-libxml2
  python-lxml python-mako python-markupsafe python-minimal
  python-mysql.connector python-notify python-oauth python-openssl python-pam
  python-paramiko python-pexpect python-piston-mini-client
  python-pkg-resources python-problem-report python-protobuf python-pycurl
  python-pyinotify python-pysqlite2 python-qt4 python-qt4-dbus python-renderpm
  python-reportlab python-reportlab-accel python-serial python-simplejson
  python-sip python-six python-smbc python-support python-twisted-bin
  python-twisted-core python-twisted-names python-twisted-web
  python-ubuntu-sso-client python-ubuntuone-client
  python-ubuntuone-control-panel python-ubuntuone-storageprotocol python-uno
  python-xapian python-xdg python-zeitgeist python-zope.interface rhythmbox
  rhythmbox-mozilla rhythmbox-plugin-cdrecorder rhythmbox-plugin-magnatune
  rhythmbox-plugin-zeitgeist rhythmbox-plugins rhythmbox-ubuntuone
  sessioninstaller software-center software-center-aptdaemon-plugins
  system-config-printer-common system-config-printer-gnome
  system-config-printer-udev totem totem-mozilla totem-plugins ubuntu-artwork
  ubuntu-desktop ubuntu-release-upgrader-gtk ubuntu-sso-client
  ubuntu-sso-client-qt ubuntu-system-service ubuntuone-client
  ubuntuone-client-gnome ubuntuone-control-panel ubuntuone-control-panel-qt
  ubuntuone-couch unity unity-common unity-lens-applications
  unity-lens-gwibber unity-lens-video unity-scope-musicstores
  unity-scope-video-remote update-manager update-notifier
  update-notifier-common usb-creator-common usb-creator-gtk xdiagnose
  zeitgeist zeitgeist-core zeitgeist-datahub
The following NEW packages will be installed:
  libglib2.0-dev:i386 libpcre3-dev:i386 libpcrecpp0:i386 python3-uno
0 upgraded, 4 newly installed, 171 to remove and 0 not upgraded.
Need to get 2,162 kB of archives.
After this operation, 193 MB disk space will be freed.
Do you want to continue [Y/n]? y
Get:1 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/universe python3-uno amd64 1:3.6.2~rc2-0ubuntu4 [160 kB]
Get:2 http://us.archive.ubuntu.com/ubuntu/ quantal/main libpcrecpp0 i386 1:8.30-5ubuntu1 [17.1 kB]
Get:3 http://us.archive.ubuntu.com/ubuntu/ quantal/main libpcre3-dev i386 1:8.30-5ubuntu1 [258 kB]
Get:4 http://us.archive.ubuntu.com/ubuntu/ quantal-updates/main libglib2.0-dev i386 2.34.1-1ubuntu1 [1,727 kB]
Fetched 2,162 kB in 4s (509 kB/s)           
(Reading database ... 171058 files and directories currently installed.)
Removing activity-log-manager-control-center ...
Removing aisleriot ...
Removing apt-xapian-index ...
Removing index /var/lib/apt-xapian-index...
Removing nautilus-share ...
Removing apturl ...
Removing ubuntu-desktop ...
Removing lightdm-remote-session-uccsconfigure ...
Removing unity ...
Removing compiz ...
Removing unity-lens-applications ...
Removing unity-common ...
Removing compiz-gnome ...
Removing deja-dup ...
Removing duplicity ...
Removing libreoffice-gnome ...
Removing gnome-media ...
Removing gstreamer0.10-gconf:amd64 ...
Removing ubuntuone-client-gnome ...
Removing ubuntu-artwork ...
Removing light-themes ...
Removing libgnome-media-profiles-3.0-0 ...
Removing xdiagnose ...
Removing ibus-table ...
Removing ibus-pinyin ...
Removing ibus ...
Removing gnome-user-share ...
Removing gnome-terminal ...
update-alternatives: using /usr/bin/lxterm to provide /usr/bin/x-terminal-emulator (x-terminal-emulator) in auto mode
Removing gnome-terminal-data ...
Removing gedit ...
Removing unity-scope-musicstores ...
Removing rhythmbox-ubuntuone ...
Removing gir1.2-ubuntuoneui-3.0 ...
Removing indicator-datetime ...
Removing indicator-power ...
Removing gnome-control-center-signon ...
Removing gnome-control-center

```

At this point I stopped the update with CTRL-z, so my ubuntu is kinda broked, a lot of stufs are no longer working, I did not reboot since I suspect It will not work

Also I tryed to reinstall the package, but i cannot, they are always dependency error

Someone can help or I need to reinstall :(?

---

### Post by labidus on 2013-02-16
I finally reinstalled ubuntu...

---

