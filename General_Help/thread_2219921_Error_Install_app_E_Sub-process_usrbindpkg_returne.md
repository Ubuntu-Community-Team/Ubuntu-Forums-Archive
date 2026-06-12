---
title: "Error Install app E: Sub-process /usr/bin/dpkg returned an error code (2)"
date: 2014-04-25
forum: General Help
---

### Post by Ibnuul on 2014-04-25
How to fix this ? 
ibnuul@ibnuul-K43E ~ $ sudo apt-get upgrade
[sudo] password for ibnuul: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be upgraded:
  apparmor-easyprof apt-xapian-index aptdaemon cups cups-bsd cups-client cups-common cups-daemon cups-ppdc cups-server-common dh-python duplicity fern-wifi-cracker friends-dispatcher gdebi gdebi-core gimp
  gir1.2-dbusmenu-glib-0.4 gnome-menus hplip-data language-selector-common language-selector-gnome libcups2 libcupscgi1 libcupsimage2 libcupsmime1 libcupsppdc1 libdbusmenu-glib4 libdbusmenu-gtk3-4 libdbusmenu-gtk4
  libgcj-common linux-firmware linux-libc-dev python-aptdaemon python-cupshelpers python-dirspec python-gi python-gnome2 python-imaging python-imaging-compat python-openssl python-protobuf python-pyatspi python-qt4
  python-sip python-software-properties python-ubuntu-sso-client python3-aptdaemon python3-aptdaemon.gtk3widgets python3-aptdaemon.pkcompat python3-dirspec python3-gi python3-pyatspi python3-uno sessioninstaller
  ubuntu-minimal ubuntu-system-service update-notifier-common xserver-xorg-core xserver-xorg-glamoregl xserver-xorg-video-intel xserver-xorg-video-openchrome
62 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/33,8 MB of archives.
After this operation, 53,6 MB disk space will be freed.
Do you want to continue [Y/n]? y
Extracting templates from packages: 100%
Preconfiguring packages ...
dpkg: file triggers record mentions illegal package name `mime-support/noawait' (for interest in file `/usr/lib/mime/packages'): character `/' not allowed (only letters, digits and characters `-+._')
E: Sub-process /usr/bin/dpkg returned an error code (2)
ibnuul@ibnuul-K43E ~ $

---

