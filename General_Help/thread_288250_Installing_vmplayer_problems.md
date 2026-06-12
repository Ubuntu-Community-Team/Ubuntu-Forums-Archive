---
title: "Installing vmplayer problems"
date: 2006-10-29
forum: General Help
---

### Post by dr.lnx on 2006-10-29
hi, if i try to install vmplayer(after my upgrade to edgy) that's what my system says:
```

root@rix:/home/rix/tmp# apt-get install vmware-player
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
I seguenti pacchetti verranno inoltre installati:
  capplets-data gnome-applets-data gnome-control-center gnome-media gnome-media-common gnome-system-tools gstreamer0.10-plugins-good gucharmap
  hal-device-manager libcamel1.2-8 libebook1.2-9 libgnome-media0 libgnome-window-settings1 libgucharmap5 libiec61883-0 libmetacity0 libnautilus-burn4
  libnet-dbus-perl liboobs-1-2 libxklavier11 libxml-grove-perl libxml-perl metacity metacity-common nautilus-cd-burner python-dbus sound-juicer
  system-tools-backends vmware-player-kernel-modules vmware-player-kernel-modules-2.6.17-10 xchat-common
Pacchetti suggeriti:
  esound-clients ntp
I seguenti pacchetti saranno RIMOSSI:
  banshee bluez-pcmcia-support bluez-pin bluez-utils deskbar-applet ekiga evolution evolution-data-server evolution-exchange evolution-plugins gedit
  gnome-app-install gnome-applets gnome-power-manager gnome-session ipod libdbus-1-2 libipod-cil libipoddevice0 libnautilus-burn3 libxklavier10
  notification-daemon python-gnome2-desktop python-gnome2-extras python2.4-dbus python2.4-gnome2-desktop python2.4-gnome2-extras rhythmbox rhythmbox-dbg
  serpentine ubuntu-desktop update-notifier xchat xchat-systray
I seguenti pacchetti NUOVI (NEW) saranno installati:
  gnome-media-common libebook1.2-9 libgnome-media0 libgnome-window-settings1 libgucharmap5 libiec61883-0 libnautilus-burn4 libnet-dbus-perl liboobs-1-2
  libxklavier11 libxml-grove-perl libxml-perl metacity-common python-dbus vmware-player vmware-player-kernel-modules vmware-player-kernel-modules-2.6.17-10
I seguenti pacchetti saranno aggiornati:
  capplets-data gnome-applets-data gnome-control-center gnome-media gnome-system-tools gstreamer0.10-plugins-good gucharmap hal-device-manager
  libcamel1.2-8 libmetacity0 metacity nautilus-cd-burner sound-juicer system-tools-backends xchat-common
15 aggiornati, 17 installati, 34 da rimuovere e 117 non aggiornati.
È necessario prendere 11,9MB/31,3MB di archivi.
Dopo l'estrazione, verranno liberati 58,6MB di spazio su disco.
Continuare [S/n]? n

```
how could thats possible? have i to uninstall all those packets? i don't think!

what coul i do to install vmplayer?

tanks bye

---

### Post by dr.lnx on 2006-10-30
if i try to do apt-get update that's what he say
```

root@rix:/usr/lib/firefox/plugins# apt-get upgrade
Lettura della lista dei pacchetti in corso... Fatto
Generazione dell'albero delle dipendenze in corso... Fatto
I seguenti pacchetti sono stati mantenuti alla versione attuale:
  acroread acroread-plugins anjuta apt apt-utils aptitude banshee bluez-cups
  bluez-pcmcia-support bluez-pin bluez-utils bug-buddy build-essential
  capplets-data cheops contact-lookup-applet cupsys cupsys-bsd cupsys-client
  deskbar-applet ekiga ethereal ethereal-common evolution
  evolution-data-server evolution-exchange evolution-plugins evolution-webcal
  g++ gaim gaim-data gcc gksu gnome-app-install gnome-applets
  gnome-applets-data gnome-control-center gnome-media gnome-panel
  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-system-tools
  gnome-terminal gnome-terminal-data gpc grub gstreamer0.10-plugins-base
  gstreamer0.10-plugins-good gucharmap hal-device-manager hpijs hplip
  hplip-data initramfs-tools initscripts ipod kismet libcamel1.2-8
  libedata-book1.2-2 libggi2 libgnomebt0 libgtk2-perl libgtkmm-2.4-1c2a
  libgtop2-7 libipod-cil libipoddevice0 libmac-ipod-gnupod-perl
  libmail-spf-query-perl libmetacity0 libpisync0 libqt3-headers libqt3-mt
  libqt3-mt-dev libsexy2 libsnmp9 libvte-common linux-image-386
  linux-restricted-modules-386 metacity mozilla-acroread mp3roaster mplayer
  nautilus-cd-burner nautilus-sendto nfs-common notification-daemon parted
  pciutils python-adns python-apt python-clientcookie python-crypto
  python-egenix-mxproxy python-egenix-mxstack python-egenix-mxtexttools
  python-egenix-mxtools python-gadfly python-glade2 python-gnome2
  python-gnome2-desktop python-gnome2-extras python-gtk2 python-htmlgen
  python-htmltmpl python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-ldap python-libxml2 python-mysqldb python-netcdf
  python-numeric python-osd python-pam python-parted python-pexpect
  python-pgsql python-pisock python-pylibacl python-pyopenssl python-pyorbit
  python-pyxattr python-reportlab python-simpletal python-soappy
  python-sqlite python-syck python-vte python-xml python-xmpp qt3-dev-tools
  rhythmbox rhythmbox-dbg serpentine sound-juicer spamassassin synaptic
  system-tools-backends sysvinit tethereal ubuntu-artwork ubuntu-minimal udev
  update-manager w3c-markup-validator wpagui xchat xchat-common xmms xmms-dev
  xpenguins-applet xterm
0 aggiornati, 0 installati, 0 da rimuovere e 154 non aggiornati.

```
maybe the two problemas are related?
what could i do to install vmplayer=?

---

