---
title: "HELP! Errors with gconf"
date: 2008-06-13
forum: General Help
---

### Post by eljaco on 2008-06-13
Hi. I was trying to uninstall some files as a sort of "spring cleaning", but it seems like I touched something I shouldn't have and can't figure out how to fix it.

I cannot open GNOME (currently running KDE) and I get all these errors:

** Tried doing a dist-upgrade
```
jaco@Mickey:~$ sudo apt-get update; sudo apt-get dist-upgrade
Hit http://archive.canonical.com hardy Release.gpg
Ign http://archive.canonical.com hardy/partner Translation-en_US
Ign http://ppa.launchpad.net hardy Release.gpg
Ign http://ppa.launchpad.net hardy/main Translation-en_US
Ign http://ppa.launchpad.net hardy/universe Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release.gpg
Ign http://us.archive.ubuntu.com hardy/main Translation-en_US
Hit http://security.ubuntu.com hardy-security Release.gpg
Ign http://security.ubuntu.com hardy-security/main Translation-en_US
Ign http://security.ubuntu.com hardy-security/restricted Translation-en_US
Hit http://packages.medibuntu.org hardy Release.gpg
Ign http://packages.medibuntu.org hardy/free Translation-en_US
Hit http://archive.canonical.com hardy Release
Ign http://us.archive.ubuntu.com hardy/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy/universe Translation-en_US
Ign http://us.archive.ubuntu.com hardy/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-updates Release.gpg
Ign http://us.archive.ubuntu.com hardy-updates/main Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-updates/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/universe Translation-en_US
Ign http://security.ubuntu.com hardy-security/multiverse Translation-en_US
Hit http://security.ubuntu.com hardy-security Release
Get:1 http://ppa.launchpad.net hardy Release [27.6kB]
Ign http://packages.medibuntu.org hardy/non-free Translation-en_US
Hit http://packages.medibuntu.org hardy Release
Ign http://us.archive.ubuntu.com hardy-updates/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy-backports Release.gpg
Ign http://us.archive.ubuntu.com hardy-backports/main Translation-en_US
Ign http://ppa.launchpad.net hardy/main Packages
Hit http://archive.canonical.com hardy/partner Sources
Hit http://security.ubuntu.com hardy-security/main Packages
Hit http://packages.medibuntu.org hardy/free Packages
Ign http://us.archive.ubuntu.com hardy-backports/restricted Translation-en_US
Ign http://us.archive.ubuntu.com hardy-backports/universe Translation-en_US
Ign http://ppa.launchpad.net hardy/universe Packages
Hit http://archive.canonical.com hardy/partner Packages
Hit http://security.ubuntu.com hardy-security/restricted Packages
Hit http://security.ubuntu.com hardy-security/main Sources
Hit http://security.ubuntu.com hardy-security/restricted Sources
Ign http://us.archive.ubuntu.com hardy-backports/multiverse Translation-en_US
Hit http://us.archive.ubuntu.com hardy Release
Hit http://us.archive.ubuntu.com hardy-updates Release
Hit http://us.archive.ubuntu.com hardy-backports Release
Hit http://packages.medibuntu.org hardy/non-free Packages
Hit http://ppa.launchpad.net hardy/main Packages
Hit http://security.ubuntu.com hardy-security/universe Packages
Hit http://security.ubuntu.com hardy-security/universe Sources
Hit http://security.ubuntu.com hardy-security/multiverse Packages
Hit http://security.ubuntu.com hardy-security/multiverse Sources
Hit http://us.archive.ubuntu.com hardy/main Packages
Hit http://ppa.launchpad.net hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/restricted Packages
Hit http://us.archive.ubuntu.com hardy/main Sources
Hit http://us.archive.ubuntu.com hardy/restricted Sources
Hit http://us.archive.ubuntu.com hardy/universe Packages
Hit http://us.archive.ubuntu.com hardy/universe Sources
Hit http://us.archive.ubuntu.com hardy/multiverse Packages
Hit http://us.archive.ubuntu.com hardy/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-updates/main Packages
Hit http://us.archive.ubuntu.com hardy-updates/restricted Packages
Hit http://us.archive.ubuntu.com hardy-updates/main Sources
Hit http://us.archive.ubuntu.com hardy-updates/restricted Sources
Hit http://us.archive.ubuntu.com hardy-updates/universe Packages
Hit http://us.archive.ubuntu.com hardy-updates/universe Sources
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-updates/multiverse Sources
Hit http://us.archive.ubuntu.com hardy-backports/main Packages
Hit http://us.archive.ubuntu.com hardy-backports/restricted Packages
Hit http://us.archive.ubuntu.com hardy-backports/universe Packages
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Packages
Hit http://us.archive.ubuntu.com hardy-backports/main Sources
Hit http://us.archive.ubuntu.com hardy-backports/restricted Sources
Hit http://us.archive.ubuntu.com hardy-backports/universe Sources
Hit http://us.archive.ubuntu.com hardy-backports/multiverse Sources
Fetched 1B in 0s (1B/s)
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.
```

** It aborted, so I ran a dpkg configure
```
jaco@Mickey:~$ sudo dpkg --configure -a
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-extra:
 libgnomevfs2-extra depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-extra depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-extra (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of nautilus:
 nautilus depends on gnome-control-center (>= 2.6); however:
  Package gnome-control-center is not configured yet.
dpkg: error processing nautilus (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-vfs2.0-cil:
 libgnome-vfs2.0-cil depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-vfs2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-gnome:
 policykit-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing policykit-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdl-1-0:
 libgdl-1-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgdl-1-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgdl-1-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-extras:
 python-gnome2-extras depends on libgdl-1-0; however:
  Package libgdl-1-0 is not configured yet.
 python-gnome2-extras depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-extras depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2-extras (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2.0-cil:
 libgnome2.0-cil depends on libgnome-vfs2.0-cil (>= 2.20.0); however:
  Package libgnome-vfs2.0-cil is not configured yet.
 libgnome2.0-cil depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing libgnome2.0-cil (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-3 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-panel depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-panel depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-panel depends on libgweather1; however:
  Package libgweather1 is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser10:
 libtotem-plparser10 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gstreamer0.10-gnomevfs:
 gstreamer0.10-gnomevfs depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gstreamer0.10-gnomevfs (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-perl:
 libgnome2-perl depends on libbonoboui2-0 (>= 2.5.4); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome2-perl depends on libgnome2-0 (>= 2.8.0); however:
  Package libgnome2-0 is not configured yet.
 libgnome2-perl depends on libgnomeui-0 (>= 2.13.0); however:
  Package libgnomeui-0 is not configured yet.
 libgnome2-perl depends on libgnomevfs2-0 (>= 2.13.92-0ubuntu4); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-7 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-9 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 2.22.2); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 2.22.2); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 2.22.2); however:
  Package libedata-cal1.2-6 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgoffice-0-6:
 libgoffice-0-6 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgoffice-0-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgoffice-0-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.14 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.14 depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2-desktop depends on libebook1.2-9 (>= 2.21.92); however:
  Package libebook1.2-9 is not configured yet.
 python-gnome2-desktop depends on libecal1.2-7 (>= 2.21.92); however:
  Package libecal1.2-7 is not configured yet.
 python-gnome2-desktop depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 python-gnome2-desktop depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2-desktop depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 python-gnome2-desktop depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
 python-gnome2-desktop depends on libtotem-plparser10 (>= 2.21.92); however:
  Package libtotem-plparser10 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-vfs-perl:
 libgnome2-vfs-perl depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-vfs-perl (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libeel2-2:
 libeel2-2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libeel2-2 depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 libeel2-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libeel2-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libeel2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libeel2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-gecko:
 epiphany-gecko depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 epiphany-gecko depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 epiphany-gecko depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 epiphany-gecko depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 epiphany-gecko depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing epiphany-gecko (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 libedataserverui1.2-8 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libedataserverui1.2-8 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-9 (>= 2.22.1.1); however:
  Package libebook1.2-9 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on python-gnome2 (>= 2.12.4-1); however:
  Package python-gnome2 is not configured yet.
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-11:
 libcamel1.2-11 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libcamel1.2-11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgdl-gnome-1-0:
 libgdl-gnome-1-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgdl-1-0; however:
  Package libgdl-1-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgdl-gnome-1-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgdl-gnome-1-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgsf-gnome-1-114:
 libgsf-gnome-1-114 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgsf-gnome-1-114 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libslab0:
 libslab0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libslab0 depends on libeel2-2 (>= 2.21.90); however:
  Package libeel2-2 is not configured yet.
 libslab0 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libslab0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libslab0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libslab0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libslab0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 gnome-control-center
 libgnomevfs2-extra
 libgnomevfs2-0
 nautilus
 libgtkhtml3.14-19
 xulrunner-1.9-gnome-support
 libedata-book1.2-2
 libedata-cal1.2-6
 libgnome-vfs2.0-cil
 libgnome2-0
 policykit-gnome
 libgdl-1-0
 python-gnome2-extras
 libbonoboui2-0
 python-gnome2
 libgnome2.0-cil
 libgweather1
 libexchange-storage1.2-3
 gnome-panel
 libgnomeui-0
 libtotem-plparser10
 gstreamer0.10-gnomevfs
 libgnome-window-settings1
 libgnome2-perl
 libecal1.2-7
 libebook1.2-9
 evolution-data-server
 libpanel-applet2-0
 libgoffice-0-6
 firefox-3.0-gnome-support
 libgnome-desktop-2
 gtkhtml3.14
 python-gnome2-desktop
 libgnome2-vfs-perl
 libeel2-2
 epiphany-gecko
 libedataserverui1.2-8
 deskbar-applet
 libcamel1.2-11
 libgdl-gnome-1-0
 libgsf-gnome-1-114
 libslab0
 firefox-gnome-support
 liblpint-bonobo0
```

** It kept refusing, so I tried to run dist-upgrade again
```
jaco@Mickey:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
76 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]?
Setting up libgnomevfs2-common (1:2.22.0-2ubuntu1) ...

(gconftool-2:15652): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:15652): GConf-WARNING **: Failed to load source "xml:readwrite:/var/lib/gconf/defaults": Failed: Couldn't locate backend module for `xml:readwrite:/var/lib/gconf/defaults'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
dpkg: error processing libgnomevfs2-common (--configure):
 subprocess post-installation script returned error exit status 250
dpkg: dependency problems prevent configuration of libgnomevfs2-0:
 libgnomevfs2-0 depends on libgnomevfs2-common (>= 1:2.22); however:
  Package libgnomevfs2-common is not configured yet.
 libgnomevfs2-0 depends on libgnomevfs2-common (<< 1:2.23); however:
  Package libgnomevfs2-common is not configured yet.
dpkg: error processing libgnomevfs2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome2-0:
 libgnome2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnome2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libbonoboui2-0:
 libbonoboui2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libbonoboui2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libbonoboui2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libcamel1.2-11:
 libcamel1.2-11 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libcamel1.2-11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libebook1.2-9:
 libebook1.2-9 depends on libcamel1.2-11 (>= 2.22.2); however:
  Package libcamel1.2-11 is not configured yet.
 libebook1.2-9 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libebook1.2-9 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libebook1.2-9 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnomeui-0:
 libgnomeui-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnomeui-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnomeui-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgnomeui-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-desktop-2:
 libgnome-desktop-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-desktop-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing libgnome-desktop-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2:
 python-gnome2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing python-gnome2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libecal1.2-7:
 libecal1.2-7 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libecal1.2-7 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libecal1.2-7 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpanel-applet2-0:
 libpanel-applet2-0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libpanel-applet2-0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libpanel-applet2-0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libtotem-plparser10:
 libtotem-plparser10 depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 libtotem-plparser10 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libtotem-plparser10 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-gnome2-desktop:
 python-gnome2-desktop depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 python-gnome2-desktop depends on libebook1.2-9 (>= 2.21.92); however:
  Package libebook1.2-9 is not configured yet.
 python-gnome2-desktop depends on libecal1.2-7 (>= 2.21.92); however:
  Package libecal1.2-7 is not configured yet.
 python-gnome2-desktop depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 python-gnome2-desktop depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 python-gnome2-desktop depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 python-gnome2-desktop depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 python-gnome2-desktop depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
 python-gnome2-desktop depends on libtotem-plparser10 (>= 2.21.92); however:
  Package libtotem-plparser10 is not configured yet.
dpkg: error processing python-gnome2-desktop (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of deskbar-applet:
 deskbar-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 deskbar-applet depends on libebook1.2-9 (>= 2.22.1.1); however:
  Package libebook1.2-9 is not configured yet.
 deskbar-applet depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 deskbar-applet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 deskbar-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 deskbar-applet depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 deskbar-applet depends on python-gnome2 (>= 2.12.4-1); however:
  Package python-gnome2 is not configured yet.
 deskbar-applet depends on python-gnome2-desktop; however:
  Package python-gnome2-desktop is not configured yet.
dpkg: error processing deskbar-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-book1.2-2:
 libedata-book1.2-2 depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 libedata-book1.2-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libedata-book1.2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-book1.2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedata-cal1.2-6:
 libedata-cal1.2-6 depends on libecal1.2-7 (>= 2.22.2); however:
  Package libecal1.2-7 is not configured yet.
 libedata-cal1.2-6 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libedata-cal1.2-6 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedata-cal1.2-6 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-data-server:
 evolution-data-server depends on libcamel1.2-11 (>= 2.22.2); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-data-server depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 evolution-data-server depends on libecal1.2-7 (>= 2.22.2); however:
  Package libecal1.2-7 is not configured yet.
 evolution-data-server depends on libedata-book1.2-2 (>= 2.22.2); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-data-server depends on libedata-cal1.2-6 (>= 2.22.2); however:
  Package libedata-cal1.2-6 is not configured yet.
 evolution-data-server depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evolution-data-server depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-data-server (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ekiga:
 ekiga depends on evolution-data-server; however:
  Package evolution-data-server is not configured yet.
 ekiga depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 ekiga depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 ekiga depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 ekiga depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 ekiga depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing ekiga (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of eog:
 eog depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 eog depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 eog depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 eog depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing eog (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-gecko:
 epiphany-gecko depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 epiphany-gecko depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 epiphany-gecko depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 epiphany-gecko depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 epiphany-gecko depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing epiphany-gecko (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of epiphany-extensions:
 epiphany-extensions depends on epiphany-gecko (>= 2.22.0); however:
  Package epiphany-gecko is not configured yet.
 epiphany-extensions depends on python-gnome2; however:
  Package python-gnome2 is not configured yet.
dpkg: error processing epiphany-extensions (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evince:
 evince depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 evince depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evince depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 evince depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evince (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgtkhtml3.14-19:
 libgtkhtml3.14-19 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgtkhtml3.14-19 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgtkhtml3.14-19 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgtkhtml3.14-19 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgtkhtml3.14-19 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gtkhtml3.14:
 gtkhtml3.14 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gtkhtml3.14 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gtkhtml3.14 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gtkhtml3.14 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gtkhtml3.14 depends on libgtkhtml3.14-19 (>= 3.18.2); however:
  Package libgtkhtml3.14-19 is not configured yet.
dpkg: error processing gtkhtml3.14 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libedataserverui1.2-8:
 libedataserverui1.2-8 depends on libebook1.2-9 (>= 2.22.2); however:
  Package libebook1.2-9 is not configured yet.
 libedataserverui1.2-8 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libedataserverui1.2-8 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libedataserverui1.2-8 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libexchange-storage1.2-3:
 libexchange-storage1.2-3 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libexchange-storage1.2-3 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libexchange-storage1.2-3 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of liblpint-bonobo0:
 liblpint-bonobo0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 liblpint-bonobo0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
dpkg: error processing liblpint-bonobo0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution:
 evolution depends on evolution-data-server (>= 2.21.92); however:
  Package evolution-data-server is not configured yet.
 evolution depends on gtkhtml3.14 (>= 3.17.5); however:
  Package gtkhtml3.14 is not configured yet.
 evolution depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 evolution depends on libcamel1.2-11 (>= 2.22.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 evolution depends on libecal1.2-7 (>= 2.22.1); however:
  Package libecal1.2-7 is not configured yet.
 evolution depends on libedataserverui1.2-8 (>= 2.22.1); however:
  Package libedataserverui1.2-8 is not configured yet.
 evolution depends on libexchange-storage1.2-3 (>= 2.22.1); however:
  Package libexchange-storage1.2-3 is not configured yet.
 evolution depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evolution depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 evolution depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 evolution depends on libgtkhtml3.14-19 (>= 3.18.1); however:
  Package libgtkhtml3.14-19 is not configured yet.
 evolution depends on liblpint-bonobo0; however:
  Package liblpint-bonobo0 is not configured yet.
dpkg: error processing evolution (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-exchange:
 evolution-exchange depends on evolution (>= 2.22.1.1); however:
  Package evolution is not configured yet.
 evolution-exchange depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 evolution-exchange depends on libcamel1.2-11 (>= 2.22.1.1); however:
  Package libcamel1.2-11 is not configured yet.
 evolution-exchange depends on libebook1.2-9 (>= 2.22.1.1); however:
  Package libebook1.2-9 is not configured yet.
 evolution-exchange depends on libecal1.2-7 (>= 2.22.1.1); however:
  Package libecal1.2-7 is not configured yet.
 evolution-exchange depends on libedata-book1.2-2 (>= 2.22.1.1); however:
  Package libedata-book1.2-2 is not configured yet.
 evolution-exchange depends on libedata-cal1.2-6 (>= 2.22.1.1); however:
  Package libedata-cal1.2-6 is not configured yet.
 evolution-exchange depends on libedataserverui1.2-8 (>= 2.22.1.1); however:
  Package libedataserverui1.2-8 is not configured yet.
 evolution-exchange depends on libexchange-storage1.2-3 (>= 2.22.1.1); however:
  Package libexchange-storage1.2-3 is not configured yet.
 evolution-exchange depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evolution-exchange depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 evolution-exchange depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing evolution-exchange (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of evolution-webcal:
 evolution-webcal depends on libecal1.2-7 (>= 2.21.91); however:
  Package libecal1.2-7 is not configured yet.
 evolution-webcal depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 evolution-webcal depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing evolution-webcal (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-settings-daemon:
 gnome-settings-daemon depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-settings-daemon depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-settings-daemon depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-settings-daemon depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-settings-daemon depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-settings-daemon (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgnome-window-settings1:
 libgnome-window-settings1 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 libgnome-window-settings1 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libgnome-window-settings1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 libgnome-window-settings1 depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing libgnome-window-settings1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-control-center:
 gnome-control-center depends on gnome-settings-daemon; however:
  Package gnome-settings-daemon is not configured yet.
 gnome-control-center depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-control-center depends on libebook1.2-9 (>= 2.22.1); however:
  Package libebook1.2-9 is not configured yet.
 gnome-control-center depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-control-center depends on libgnome-window-settings1 (= 1:2.22.1-0ubuntu4.1); however:
  Package libgnome-window-settings1 is not configured yet.
 gnome-control-center depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-control-center depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-control-center depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-control-center depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing gnome-control-center (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libgweather1:
 libgweather1 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libgweather1 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-panel:
 gnome-panel depends on gnome-control-center (>= 1:2.8.2-3); however:
  Package gnome-control-center is not configured yet.
 gnome-panel depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-panel depends on libebook1.2-9 (>= 2.22.1.1); however:
  Package libebook1.2-9 is not configured yet.
 gnome-panel depends on libecal1.2-7 (>= 2.22.1.1); however:
  Package libecal1.2-7 is not configured yet.
 gnome-panel depends on libedataserverui1.2-8 (>= 2.22.1.1); however:
  Package libedataserverui1.2-8 is not configured yet.
 gnome-panel depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-panel depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-panel depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-panel depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-panel depends on libgweather1; however:
  Package libgweather1 is not configured yet.
 gnome-panel depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing gnome-panel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of fast-user-switch-applet:
 fast-user-switch-applet depends on gnome-panel; however:
  Package gnome-panel is not configured yet.
 fast-user-switch-applet depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 fast-user-switch-applet depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 fast-user-switch-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 fast-user-switch-applet depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 fast-user-switch-applet depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing fast-user-switch-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of file-roller:
 file-roller depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 file-roller depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 file-roller depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing file-roller (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 xulrunner-1.9-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gconf-editor:
 gconf-editor depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gconf-editor depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
dpkg: error processing gconf-editor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gedit:
 gedit depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gedit depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gedit depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gedit (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-launch-box:
 gnome-launch-box depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-launch-box depends on libebook1.2-9 (>= 2.21.3); however:
  Package libebook1.2-9 is not configured yet.
 gnome-launch-box depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-launch-box depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-launch-box depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-launch-box depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-launch-box (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libeel2-2:
 libeel2-2 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libeel2-2 depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 libeel2-2 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libeel2-2 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libeel2-2 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libeel2-2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libslab0:
 libslab0 depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 libslab0 depends on libeel2-2 (>= 2.21.90); however:
  Package libeel2-2 is not configured yet.
 libslab0 depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 libslab0 depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 libslab0 depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 libslab0 depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing libslab0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-main-menu:
 gnome-main-menu depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-main-menu depends on libeel2-2 (>= 2.21.90); however:
  Package libeel2-2 is not configured yet.
 gnome-main-menu depends on libgnome-desktop-2 (>= 2.11.1); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-main-menu depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-main-menu depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-main-menu depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-main-menu depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
 gnome-main-menu depends on libslab0; however:
  Package libslab0 is not configured yet.
dpkg: error processing gnome-main-menu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of policykit-gnome:
 policykit-gnome depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing policykit-gnome (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-mount:
 gnome-mount depends on policykit-gnome; however:
  Package policykit-gnome is not configured yet.
dpkg: error processing gnome-mount (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-netstatus-applet:
 gnome-netstatus-applet depends on libgnome2-0 (>= 2.14.1); however:
  Package libgnome2-0 is not configured yet.
 gnome-netstatus-applet depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-netstatus-applet depends on libpanel-applet2-0 (>= 1:2.18.1); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing gnome-netstatus-applet (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-system-monitor:
 gnome-system-monitor depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
dpkg: error processing gnome-system-monitor (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-utils:
 gnome-utils depends on libbonoboui2-0 (>= 2.15.1); however:
  Package libbonoboui2-0 is not configured yet.
 gnome-utils depends on libgnome-desktop-2 (>= 1:2.22); however:
  Package libgnome-desktop-2 is not configured yet.
 gnome-utils depends on libgnome2-0 (>= 2.17.3); however:
  Package libgnome2-0 is not configured yet.
 gnome-utils depends on libgnomeui-0 (>= 2.17.1); however:
  Package libgnomeui-0 is not configured yet.
 gnome-utils depends on libgnomevfs2-0 (>= 1:2.17.90); however:
  Package libgnomevfs2-0 is not configured yet.
 gnome-utils depends on libpanel-applet2-0 (>= 2.19.3); however:
  Package libpanel-applet2-0 is not configured yet.
dpkg: error processing gnome-utils (--configure):
 dependency problems - leaving unconfigured
dpkg: too many errors, stopping
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly
```

Something that caught my eye was the following:
```
(gconftool-2:15652): GConf-CRITICAL **: No such file `/usr/lib/libgconf2-4/2/libgconfbackend-xml.so'


(gconftool-2:15652): GConf-WARNING **: Failed to load source "xml:readwrite:/var/lib/gconf/defaults": Failed: Couldn't locate backend module for `xml:readwrite:/var/lib/gconf/defaults'
**
** GConf:ERROR:(gconftool.c:918):main: assertion failed: (err == NULL)
```

Please help as I am utterly stuck and would love to go back to my familiar Gnome (no disrespect to the KDE folks, I just feel more comfortable with Gnome.)

---

### Post by eljaco on 2008-06-30
*bump*

---

### Post by Motorhead Kaze on 2008-06-30
definitely bump!

---

### Post by rubicon on 2008-06-30
[re]Install libgconf2-4?

---

### Post by eljaco on 2008-07-01
I can't install anything because of all the errors. I've tried installing every single package that is depended on, but it just never does anything.

---

### Post by rubicon on 2008-07-01
OKay, okay, get package ([http://packages.ubuntu.com/hardy/libgconf2-4](http://packages.ubuntu.com/hardy/libgconf2-4)), unpack that file and place it into /usr/lib/libgconf2-4/2/

---

### Post by eljaco on 2008-07-01
Awesome! Thanks!

I also had to manually install libgnomevfs2-common and then run ```
sudo dpkg --configure -a
```, but aside from that, it seems to all be working now. Now I know not to randomly uninstall stuff...

---

### Post by diamanthunden on 2008-09-15
Hello

I have a similar problem after upgrading to Hardy.

But how do you install the libgconf2-4 by hand? Download the .deb file, unpack it and then what should i do with the two tar balls control and data? What exactly should i copy to the /usr/lib/libgconf2-4/2/?

Thanks ;)

Ben

---

