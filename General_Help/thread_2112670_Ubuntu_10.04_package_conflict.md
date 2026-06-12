---
title: "Ubuntu 10.04 package conflict"
date: 2013-02-05
forum: General Help
---

### Post by artishox on 2013-02-05
Hi, i installed libgtk2.0-0_2.20.0-0ubuntu4_amd64.deb with dpkg.
But as it looks like my machine already had libgtk2.0-0_2.20.1-0ubuntu4_amd64.
Now Synaptic package manager offers me to uninstall almost everything on my system.

Is there a way to remove that libgtk2.0-0_2.20.0-0ubuntu4_amd64 package without uninstalling everything else?

Thanks in advance.

---

### Post by raja.genupula on 2013-02-05
Remove what you have installed and then remove what you dont want . then install what you want.

---

### Post by ibjsb4 on 2013-02-05
That looks to be an upgrade offered in 10o4, so maybe you could just upgrade it.

```
sudo apt-get update && sudo apt-get upgrade
```

[http://packages.ubuntu.com/lucid-updates/libgtk2.0-0](http://packages.ubuntu.com/lucid-updates/libgtk2.0-0)

---

### Post by raja.genupula on 2013-02-05
> **ibjsb4 said:**
> That looks to be an upgrade offered in 10o4, so maybe you could just upgrade it.

```
sudo apt-get update && sudo apt-get upgrade
```[http://packages.ubuntu.com/lucid-updates/libgtk2.0-0](http://packages.ubuntu.com/lucid-updates/libgtk2.0-0)

Hi 
I am not getting what you actaully want to say,because He mentioned like he has installed it from .deb , its not came with any upgrade .

so whats the matter of trying sudo apt-get update and all. 

please explain more about what you'd like to convey so that we all can understand .

Thank you.

---

### Post by ibjsb4 on 2013-02-05
Hi (uncle) raja :)

OP has install libgtk2.0-0_2.20.0-0ubuntu4_amd64 package.  Instead of removing the package I think he can just upgrade it to libgtk2.0-0_2.20.1-0ubuntu4_amd64.

It is an offered upgrade.

---

### Post by furything on 2013-02-05
Sorry I think raja is probably right.

If the package manger can now see 2 versions of the same thing and is confused then how does it know what to update. 
```
sudo dpkg --remove -P libgtk2.0-0_2.20.0-0ubuntu4_amd64

```

---

### Post by artishox on 2013-02-06
Thanks for quick response.
I tried both suggestions:

sudo dpkg --remove -P libgtk2.0-0_2.20.0-0ubuntu4_amd64
didn't work as package libgtk2.0-0_2.20.0-0ubuntu4_amd64 couldn't be found when I try with just libgtk2.0-0  I get following message:
```
dpkg: dependency problems prevent removal of libgtk2.0-0:
 gnome-power-manager depends on libgtk2.0-0 (>= 2.18.0).
 liblaunchpad-integration1 depends on libgtk2.0-0 (>= 2.8.2).
 libgnome-media0 depends on libgtk2.0-0 (>= 2.15.1).
 aisleriot depends on libgtk2.0-0 (>= 2.20.0).
 gnome-session-bin depends on libgtk2.0-0 (>= 2.14.0).
 libgnome-bluetooth7 depends on libgtk2.0-0 (>= 2.20.0).
 evolution-indicator depends on libgtk2.0-0 (>= 2.10.0).
 nautilus-sendto depends on libgtk2.0-0 (>= 2.12.0).
 network-manager-gnome depends on libgtk2.0-0 (>= 2.16.0).
 rhythmbox-plugin-cdrecorder depends on libgtk2.0-0 (>= 2.16.0).
 libindicator0 depends on libgtk2.0-0 (>= 2.16.0).
 libmetacity-private0 depends on libgtk2.0-0 (>= 2.10.0).
 adobe-flashplugin depends on libgtk2.0-0 (>= 2.14.0).
 gstreamer0.10-plugins-good depends on libgtk2.0-0 (>= 2.8.0).
 notify-osd depends on libgtk2.0-0 (>= 2.18.0).
 evolution-couchdb depends on libgtk2.0-0 (>= 2.8.0).
 gnome-applets depends on libgtk2.0-0 (>= 2.18.0).
 firefox depends on libgtk2.0-0 (>= 2.18.0).
 libgtk2.0-bin depends on libgtk2.0-0 (>= 2.20.1-0ubuntu2.1).
 libvte9 depends on libgtk2.0-0 (>= 2.14.0).
 network-manager-pptp-gnome depends on libgtk2.0-0 (>= 2.8.0).
 gnome-mag depends on libgtk2.0-0 (>= 2.20.0).
 libdbusmenu-gtk1 depends on libgtk2.0-0 (>= 2.16.0).
 python-pygoocanvas depends on libgtk2.0-0 (>= 2.17.5).
 zenity depends on libgtk2.0-0 (>= 2.16.0).
 liblpint-bonobo0 depends on libgtk2.0-0 (>= 2.8.2).
 libwnck22 depends on libgtk2.0-0 (>= 2.20.0).
 python-notify depends on libgtk2.0-0 (>= 2.10.0).
 libgucharmap7 depends on libgtk2.0-0 (>= 2.16.0).
 gnome-system-tools depends on libgtk2.0-0 (>= 2.18.0).
 python-virtkey depends on libgtk2.0-0 (>= 2.8.0).
 evolution depends on libgtk2.0-0 (>= 2.18.0).
 libnautilus-extension1 depends on libgtk2.0-0 (>= 2.20).
 libpolkit-gtk-1-0 depends on libgtk2.0-0 (>= 2.17.1).
 indicator-messages depends on libgtk2.0-0 (>= 2.16.0).
 libnautilus-burn4 depends on libgtk2.0-0 (>= 2.8.0).
 indicator-application depends on libgtk2.0-0 (>= 2.12.0).
 gnome-user-share depends on libgtk2.0-0 (>= 2.14.0).
 totem-plugins depends on libgtk2.0-0 (>= 2.19.5).
 nspluginwrapper depends on libgtk2.0-0 (>= 2.18.0).
 gksu depends on libgtk2.0-0 (>= 2.8.0).
 vino depends on libgtk2.0-0 (>= 2.16.0).
 libcanberra-gtk0 depends on libgtk2.0-0 (>= 2.14.0).
 gnome-utils depends on libgtk2.0-0 (>= 2.18.0).
 libwebkit-1.0-2 depends on libgtk2.0-0 (>= 2.20.0).
 gnome-mahjongg depends on libgtk2.0-0 (>= 2.18.0).
 libgail-gnome-module depends on libgtk2.0-0 (>= 2.8.0).
 libbrasero-media0 depends on libgtk2.0-0 (>= 2.20.0).
 gnomine depends on libgtk2.0-0 (>= 2.18.0).
 evolution-plugins depends on libgtk2.0-0 (>= 2.16.0).
 libgtkhtml3.14-19 depends on libgtk2.0-0 (>= 2.18.0).
 nautilus depends on libgtk2.0-0 (>= 2.20.0).
 tsclient depends on libgtk2.0-0 (>= 2.8.0).
 python-gtk2 depends on libgtk2.0-0 (>= 2.19.1); however:
  Package libgtk2.0-0 is to be removed.
 libido-0.1-0 depends on libgtk2.0-0 (>= 2.19.7).
 assogiate depends on libgtk2.0-0 (>= 2.17.10).
 at-spi depends on libgtk2.0-0 (>= 2.10.0).
 libgtksourceview2.0-0 depends on libgtk2.0-0 (>= 2.16.0).
 libunique-1.0-0 depends on libgtk2.0-0 (>= 2.12.0).
 gucharmap depends on libgtk2.0-0 (>= 2.14.0).
 dropbox depends on libgtk2.0-0 (>= 2.12.0).
 gnome-disk-utility depends on libgtk2.0-0 (>= 2.18.0).
 python-gtksourceview2 depends on libgtk2.0-0 (>= 2.12.0); however:
  Package libgtk2.0-0 is to be removed.
 librsvg2-common depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 librsvg2-common depends on libgtk2.0-0 (>= 2.16); however:
  Package libgtk2.0-0 is to be removed.
 python-webkit depends on libgtk2.0-0 (>= 2.10.0).
 evolution-exchange depends on libgtk2.0-0 (>= 2.10.0).
 libgnome2.24-cil depends on libgtk2.0-0 (>= 2.19.4).
 python-ubuntuone depends on libgtk2.0-0 (>= 2.8.0).
 yelp depends on libgtk2.0-0 (>= 2.18.0).
 libgnome-pilot2 depends on libgtk2.0-0 (>= 2.8.0).
 tomboy depends on libgtk2.0-0 (>= 2.20.0).
 python-glade2 depends on libgtk2.0-0 (>= 2.19.0).
 google-chrome-stable depends on libgtk2.0-0 (>= 2.18.0).
 libgail18 depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1).
 libcryptui0 depends on libgtk2.0-0 (>= 2.10.0).
 libubuntuone-1.0-1 depends on libgtk2.0-0 (>= 2.8.0).
 libpoppler-glib4 depends on libgtk2.0-0 (>= 2.12).
 gnome-bluetooth depends on libgtk2.0-0 (>= 2.20.0).
 libgtk2-perl depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is to be removed.
 update-notifier depends on libgtk2.0-0 (>= 2.14.0).
 libedataserverui1.2-8 depends on libgtk2.0-0 (>= 2.14.0).
 ibus depends on libgtk2.0-0 (>= 2.8.0).
 file-roller depends on libgtk2.0-0 (>= 2.20.0).
 librsvg2-2 depends on libgtk2.0-0 (>= 2.16).
 transmission-gtk depends on libgtk2.0-0 (>= 2.16.0).
 indicator-applet-session depends on libgtk2.0-0 (>= 2.18.0).
 nautilus-sendto-empathy depends on libgtk2.0-0 (>= 2.18.0).
 libgtkhtml-editor0 depends on libgtk2.0-0 (>= 2.18.0).
 indicator-sound depends on libgtk2.0-0 (>= 2.14.0).
 openoffice.org-gtk depends on libgtk2.0-0 (>= 2.14.0).
 python-vte depends on libgtk2.0-0 (>= 2.14.0).
 evince depends on libgtk2.0-0 (>= 2.16.0).
 pinentry-gtk2 depends on libgtk2.0-0 (>= 2.8.0).
 gtk2-engines-pixbuf depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 gtk2-engines-pixbuf depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is to be removed.
 openoffice.org-core depends on libgtk2.0-0 (>= 2.10).
 nvidia-settings depends on libgtk2.0-0 (>= 2.8.0).
 synaptic depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is to be removed.
 gcalctool depends on libgtk2.0-0 (>= 2.18.0).
 libevview2 depends on libgtk2.0-0 (>= 2.20.0).
 indicator-me depends on libgtk2.0-0 (>= 2.12.0).
 gnome-control-center depends on libgtk2.0-0 (>= 2.18.0).
 ubuntuone-client-gnome depends on libgtk2.0-0 (>= 2.14.0).
 simple-scan depends on libgtk2.0-0 (>= 2.18.0).
 libevdocument2 depends on libgtk2.0-0 (>= 2.14.0).
 python-appindicator depends on libgtk2.0-0 (>= 2.12.0).
 libgksu2-0 depends on libgtk2.0-0 (>= 2.12.0).
 libappindicator0 depends on libgtk2.0-0 (>= 2.18.0).
 gtk2-engines depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 gtk2-engines depends on libgtk2.0-0 (>= 2.12.0); however:
  Package libgtk2.0-0 is to be removed.
 evolution-webcal depends on libgtk2.0-0 (>= 2.8.0).
 gbrainy depends on libgtk2.0-0 (>= 2.20.0).
 mousetweaks depends on libgtk2.0-0 (>= 2.18.0).
 gnome-games-common depends on libgtk2.0-0 (>= 2.18.0).
 policykit-1-gnome depends on libgtk2.0-0 (>= 2.17.1).
 libavahi-ui0 depends on libgtk2.0-0 (>= 2.8.0).
 python-gnomecanvas depends on libgtk2.0-0 (>= 2.8.0).
 libindicate-gtk2 depends on libgtk2.0-0 (>= 2.14.0).
 vinagre depends on libgtk2.0-0 (>= 2.18.0).
 indicator-session depends on libgtk2.0-0 (>= 2.16.0).
 totem depends on libgtk2.0-0 (>= 2.20.0).
 indicator-applet depends on libgtk2.0-0 (>= 2.18.0).
 rhythmbox depends on libgtk2.0-0 (>= 2.18.0).
 libpanel-applet2-0 depends on libgtk2.0-0 (>= 2.20.0).
 gnome-keyring depends on libgtk2.0-0 (>= 2.20.0).
 evolution-data-server depends on libgtk2.0-0 (>= 2.10.0).
 gnome-nettool depends on libgtk2.0-0 (>= 2.14.0).
 libgimp2.0 depends on libgtk2.0-0 (>= 2.12.0).
 libgcr0 depends on libgtk2.0-0 (>= 2.18.0).
 xulrunner-1.9.2 depends on libgtk2.0-0 (>= 2.18.0).
 libgnome2-perl depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is to be removed.
 gnomebaker depends on libgtk2.0-0 (>= 2.8.0).
 libglade2-0 depends on libgtk2.0-0 (>= 2.8.0).
 ssh-askpass-gnome depends on libgtk2.0-0 (>= 2.8.0).
 libgnome-window-settings1 depends on libgtk2.0-0 (>= 2.15.0).
 rhythmbox-plugins depends on libgtk2.0-0 (>= 2.18.0).
 libgnomecanvas2-0 depends on libgtk2.0-0 (>= 2.8.17).
 libgdu-gtk0 depends on libgtk2.0-0 (>= 2.18.0).
 libgtkmm-2.4-1c2a depends on libgtk2.0-0 (>= 2.20.0).
 adobe-flash-properties-gtk depends on libgtk2.0-0 (>= 2.14.0).
 python-indicate depends on libgtk2.0-0 (>= 2.8.0).
 libgnomeui-0 depends on libgtk2.0-0 (>= 2.14).
 gedit depends on libgtk2.0-0 (>= 2.20.0).
 gnome-panel depends on libgtk2.0-0 (>= 2.20.0).
 libatspi1.0-0 depends on libgtk2.0-0 (>= 2.10.0).
 libexchange-storage1.2-3 depends on libgtk2.0-0 (>= 2.10.0).
 libgnome2-canvas-perl depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is to be removed.
 libnotify1 depends on libgtk2.0-0 (>= 2.10.0).
 libcanberra-gtk-module depends on libgtk2.0-0 (>= 2.14.0).
 xdg-user-dirs-gtk depends on libgtk2.0-0 (>= 2.8.0).
 libgpod4 depends on libgtk2.0-0 (>= 2.8.0).
 libgweather1 depends on libgtk2.0-0 (>= 2.11.0).
 libgtk-vnc-1.0-0 depends on libgtk2.0-0 (>= 2.10.0).
 libgdict-1.0-6 depends on libgtk2.0-0 (>= 2.18.0).
 seahorse depends on libgtk2.0-0 (>= 2.18.0).
 nautilus-cd-burner depends on libgtk2.0-0 (>= 2.8.0).
 python-gnomeapplet depends on libgtk2.0-0 (>= 2.8.0).
 nautilus-share depends on libgtk2.0-0 (>= 2.12.0).
 ibus-gtk depends on libgtk2.0-0 (>= 2.8.0).
 ibus-gtk depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 libgnome-desktop-2-17 depends on libgtk2.0-0 (>= 2.18.0).
 metacity depends on libgtk2.0-0 (>= 2.18.0).
 gnome-settings-daemon depends on libgtk2.0-0 (>= 2.18.0).
 gconf-editor depends on libgtk2.0-0 (>= 2.20.0).
 libgtk2.0-cil depends on libgtk2.0-0 (>= 2.19.4).
 gnome-system-monitor depends on libgtk2.0-0 (>= 2.16.0).
 python-wnck depends on libgtk2.0-0 (>= 2.8.0).
 plymouth-x11 depends on libgtk2.0-0 (>= 2.10.0).
 libgegl-0.0-0 depends on libgtk2.0-0 (>= 2.8.0).
 eog depends on libgtk2.0-0 (>= 2.18.0).
 xscreensaver-data depends on libgtk2.0-0 (>= 2.12.0).
 libgoocanvas3 depends on libgtk2.0-0 (>= 2.12.0).
 gdm depends on libgtk2.0-0 (>= 2.16.0).
 python-gtkspell depends on libgtk2.0-0 (>= 2.8.0).
 gnome-terminal depends on libgtk2.0-0 (>= 2.18.0).
 libwxgtk2.8-0 depends on libgtk2.0-0 (>= 2.18.0).
 empathy depends on libgtk2.0-0 (>= 2.18.0).
 python-gnome2 depends on libgtk2.0-0 (>= 2.8.0); however:
  Package libgtk2.0-0 is to be removed.
 gimp depends on libgtk2.0-0 (>= 2.20.0).
 gtk2-engines-murrine depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 gtk2-engines-murrine depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is to be removed.
 libgnomekbd4 depends on libgtk2.0-0 (>= 2.20.0).
 libbonoboui2-0 depends on libgtk2.0-0 (>= 2.18.0).
 libgtkspell0 depends on libgtk2.0-0 (>= 2.8.0).
 libwmf0.2-7-gtk depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 librsvg2-common depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 librsvg2-common depends on libgtk2.0-0 (>= 2.16); however:
  Package libgtk2.0-0 is to be removed.
 gtk2-engines-pixbuf depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 gtk2-engines-pixbuf depends on libgtk2.0-0 (= 2.20.1-0ubuntu2.1); however:
  Package libgtk2.0-0 is to be removed.
 gtk2-engines depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 gtk2-engines depends on libgtk2.0-0 (>= 2.12.0); however:
  Package libgtk2.0-0 is to be removed.
 ibus-gtk depends on libgtk2.0-0 (>= 2.8.0).
 ibus-gtk depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 gtk2-engines-murrine depends on gtk2.0-binver-2.10.0; however:
  Package gtk2.0-binver-2.10.0 is not installed.
  Package libgtk2.0-0 which provides gtk2.0-binver-2.10.0 is to be removed.
 gtk2-engines-murrine depends on libgtk2.0-0 (>= 2.18.0); however:
  Package libgtk2.0-0 is to be removed.
dpkg: error processing libgtk2.0-0 (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 libgtk2.0-0

```

after sudo apt-get upgrade i get this output
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  apturl at-spi empathy eog evince evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins furiusisomount
  gbrainy gdebi gdm gdm-guest-session gimp gnome-about gnome-applets
  gnome-codec-install gnome-control-center gnome-icon-theme gnome-mag
  gnome-orca gnome-panel gnome-power-manager gnome-session
  gnome-themes-selected gnome-themes-ubuntu gnome-utils gnomebaker
  gtk2-engines-pixbuf gucharmap gwibber humanity-icon-theme indicator-applet
  indicator-applet-session indicator-me libbonoboui2-0 libgail-common
  libgail-gnome-module libgail18 libgnome-pilot2 libgnome2-canvas-perl
  libgnome2-perl libgnome2.24-cil libgnomecanvas2-0 libgnomepanel2.24-cil
  libgnomeui-0 libgtk2.0-bin libgtkhtml-editor0 libgtkhtml3.14-19
  liblpint-bonobo0 libpanel-applet2-0 libubuntuone-1.0-1 libwebkit-1.0-2
  light-themes mousetweaks nautilus nautilus-cd-burner nautilus-sendto-empathy
  nautilus-share pitivi python-gnome2 python-gnomeapplet python-gnomecanvas
  python-pyatspi python-ubuntuone python-webkit rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store simple-scan software-center
  system-config-printer-gnome tomboy totem totem-mozilla totem-plugins
  tsclient ubufox ubuntu-artwork ubuntu-mono usb-creator-gtk vinagre
  xul-ext-ubufox
The following packages have been kept back:
  dropbox
The following packages will be upgraded:
  firefox firefox-locale-en google-chrome-stable nautilus-dropbox
4 upgraded, 0 newly installed, 86 to remove and 1 not upgraded.
Need to get 61.2MB of archives.
After this operation, 260MB disk space will be freed.
```

and after sudo apt-get -f install
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libnautilus-burn4 libxprintapputil1 libqt4-script libqt4-designer
  libqt4-dbus libxcb-xv0 libiso9660-7 libmaloc1 libxfontp1 apbs
  libqt4-xmlpatterns libbabl-0.0-0 libgegl-0.0-0 python-pmw blt python-tk
  fuseiso9660 xprint-utils libopenmpi1.3 icedax libxprintutil1 libao2
  libxine1-console libphonon4 libqt4-xml cdrdao fuseiso tcl8.5 libgimp2.0
  libxine1-misc-plugins libibverbs1 tk8.5 libumlib0 libqt4-webkit
  libxcb-shape0 gimp-data libxcb-shm0 libaudit0 libxine1-bin
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  apturl at-spi empathy eog evince evolution evolution-couchdb
  evolution-exchange evolution-indicator evolution-plugins furiusisomount
  gbrainy gdebi gdm gdm-guest-session gimp gnome-about gnome-applets
  gnome-codec-install gnome-control-center gnome-icon-theme gnome-mag
  gnome-orca gnome-panel gnome-power-manager gnome-session
  gnome-themes-selected gnome-themes-ubuntu gnome-utils gnomebaker
  gtk2-engines-pixbuf gucharmap gwibber humanity-icon-theme indicator-applet
  indicator-applet-session indicator-me libbonoboui2-0 libgail-common
  libgail-gnome-module libgail18 libgnome-pilot2 libgnome2-canvas-perl
  libgnome2-perl libgnome2.24-cil libgnomecanvas2-0 libgnomepanel2.24-cil
  libgnomeui-0 libgtk2.0-bin libgtkhtml-editor0 libgtkhtml3.14-19
  liblpint-bonobo0 libpanel-applet2-0 libubuntuone-1.0-1 libwebkit-1.0-2
  light-themes mousetweaks nautilus nautilus-cd-burner nautilus-sendto-empathy
  nautilus-share pitivi python-gnome2 python-gnomeapplet python-gnomecanvas
  python-pyatspi python-ubuntuone python-webkit rhythmbox
  rhythmbox-plugin-cdrecorder rhythmbox-plugins
  rhythmbox-ubuntuone-music-store simple-scan software-center
  system-config-printer-gnome tomboy totem totem-mozilla totem-plugins
  tsclient ubufox ubuntu-artwork ubuntu-mono usb-creator-gtk vinagre
  xul-ext-ubufox
0 upgraded, 0 newly installed, 86 to remove and 5 not upgraded.
After this operation, 260MB disk space will be freed.

```

Any suggestions?

---

### Post by furything on 2013-02-06
what happens if you try ```
sudo dpkg-reconfigure -a
```
This should reconfigure all deb packages.

Or maybe the answer is to do a complete upgrade to 11.04. This would of course remove old redundant packages and install the new.

Back up personal data first.

Is there any reason why you want to stick with 10.04?

---

### Post by artishox on 2013-02-06
> **furything said:**
> what happens if you try ```
sudo dpkg-reconfigure -a
```This should reconfigure all deb packages.

Or maybe the answer is to do a complete upgrade to 11.04. This would of course remove old redundant packages and install the new.

Back up personal data first.

Is there any reason why you want to stick with 10.04?

This went through some dialogs but issue wasn't fixed.

I am considering to upgrade to 11.04 or to 12.04 - but I don't have time to do that right now. Thanks for suggestion.

---

### Post by raja.genupula on 2013-02-06
> **ibjsb4 said:**
> Hi (uncle) raja :)

OP has install libgtk2.0-0_2.20.0-0ubuntu4_amd64 package.  Instead of removing the package I think he can just upgrade it to libgtk2.0-0_2.20.1-0ubuntu4_amd64.

It is an offered upgrade.

Lol you calling a 23-Years man as Uncle. 

Ok @OP could you mention whats those dialog data. every small thing can help us to help you.

---

### Post by ibjsb4 on 2013-02-06
> **furything said:**
> Or maybe the answer is to do a complete upgrade to 11.04.

11o4 reached end of life last year, go to 12o4.

@raja:  No not my uncle, you been an uncle for about two years now :)

---

### Post by furything on 2013-02-06
> 11o4 reached end of life last year, go to 12o4Agreed but don't you have to upgrade one at a time so 11.04 then 12.04

If artishox still has issues after an upgrade to 11.04 then it would be simpler to back up important data - format - install 12.04 from iso (cd/usb)

---

