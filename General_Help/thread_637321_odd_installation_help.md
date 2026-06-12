---
title: "odd installation help"
date: 2007-12-10
forum: General Help
---

### Post by sleejay on 2007-12-10
i would like to install ubuntu on my usb drive, using QEMU so i can run from inside of windows.

BUT i do not want X or any window managers. i just want command line ubuntu, also i want it to be persistant so i can save changes, install software, etc

how can i do this? ive spent the last 2 hours reading about how to install and use qemu but not how to only install command line with this method

---

### Post by PmDematagoda on 2007-12-10
If you want to run Ubuntu within Windows at all then you will need to use it as a Virtual Machine, you can use either [Virtual Box]("http://www.virtualbox.org/wiki/Downloads") or [VM Ware.]("http://www.vmware.com/")

---

### Post by amugofcoffee on 2007-12-10
You could install the full Ubuntu then apt-get remove stuff.

---

### Post by sleejay on 2007-12-11
> **PmDematagoda said:**
> If you want to run Ubuntu within Windows at all then you will need to use it as a Virtual Machine, you can use either [Virtual Box]("http://www.virtualbox.org/wiki/Downloads") or [VM Ware.]("http://www.vmware.com/")

no, ive been toying with QEMU and its working fine once you make a disk image

---

### Post by zvacet on 2007-12-12
It sounds like you want Ubuntu server im VM.if you don´t have server Cd you can remove ubuntu desktop after install.

```
sudo aptitude remove ubuntu-desktop
```

or

```
sudo apt-get remove alacarte app-install-data-commercial apport-gtk apturl at-spi bittorrent bluez-gnome brltty-x11 bug-buddy capplets-data cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet cupsys-driver-gutenprint dcraw deskbar-applet displayconfig-gtk diveintopython doc-base docbook-xml ekiga eog espeak espeak-data evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal example-content f-spot fast-user-switch-applet feisty-gdm-themes file-roller firefox firefox-gnome-support gamin gcalctool gconf-editor gconf2 gconf2-common gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-cards-data gnome-control-center gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-mount gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14 gucharmap guile-1.6-libs gutsy-wallpapers hal-cups-utils hal-device-manager human-icon-theme human-theme hwdb-client-gnome language-selector libaa1 libalut0 libart2.0-cil libatspi1.0-0 libavahi-glib1 libavc1394-0 libbeagle0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libcaca0 libcairo-perl libcairomm-1.0-1 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcroco3 libcucul0 libdecoration0 libdeskbar-tracker libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libenchant1c2a libespeak1 libexchange-storage1.2-3 libgail-common libgail-gnome-module libgail18 libgamin0 libgconf2-4 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libglade2-0 libglade2.0-cil libglew1.4 libglib-perl libglib2.0-cil libglibmm-2.4-1c2a libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech7 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2-perl libgtk2.0-bin libgtk2.0-cil libgtkhtml2-0 libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtkmm-2.4-1c2a libgtksourceview-common libgtksourceview1.0-0 libgtksourceview2.0-0 libgtksourceview2.0-common libgtkspell0 libgtop2-7 libgtop2-common libgucharmap6 libguile-ltdl-1 libgutenprintui2-1 libhesiod0 libhsqldb-java libidl0 libiec61883-0 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libnautilus-burn4 libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libnet-dbus-perl libnm-glib0 libnotify1 liboil0.3 liboobs-1-3 libopal-2.2 libopenal0a liborbit2 libpam-gnome-keyring libpanel-applet2-0 libpcrecpp0 libpisock9 libpisync0 libpoppler-glib2 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libpurple0 libqthreads-12 librarian0 librsvg2-2 librsvg2-common librsvg2.0-cil libscrollkeeper0 libservlet2.4-java libsexy2 libshout3 libsoup2.2-8 libtotem-plparser7 libtracker-gtk0 libtrackerclient0 libvte-common libvte9 libwavpack1 libwmf0.2-7 libwnck-common libwnck22 libxevie1 libxklavier11 libxml-twig-perl libxml2-utils libxres1 libzephyr3 metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto network-manager-gnome notification-daemon o3read onboard openoffice.org openoffice.org-base openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk pidgin pidgin-data pkg-config python-at-spi python-bittorrent python-cairo python-cups python-gconf python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gobject python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-notify python-numeric python-orca-brlapi python-pygtksourceview python-pyorbit python-sexy python-virtkey python-vte python-xml restricted-manager rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket scim-modules-table scim-tables-additional screensaver-default-images scrollkeeper serpentine sgml-data shared-mime-info software-properties-gtk sound-juicer ssh-askpass-gnome synaptic system-config-printer system-tools-backends tangerine-icon-theme tomboy totem totem-gstreamer totem-mozilla tracker tracker-search-tool tsclient ubufox ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds update-manager update-notifier usplash-theme-ubuntu vino whois xbitmaps xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xterm xvnc4viewer yelp zenity && sudo apt-get install kubuntu-desktop
```

or in** synaptic>edit>mark by task>unchek ubuntu desktop**

---

