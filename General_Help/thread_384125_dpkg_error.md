---
title: "dpkg error"
date: 2007-03-14
forum: General Help
---

### Post by hearty on 2007-03-14
root@hertz:~# apt-get upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages have been kept back:
  apport apport-gtk apt apt-utils aptitude at-spi avahi-daemon bind9-host bittorrent brltty brltty-x11 capplets-data
  cdrecord contact-lookup-applet cupsys-bsd cupsys-client deskbar-applet dia-common dia-gnome dia-libs dnsutils
  dvd+rw-tools ecj-bootstrap ekiga evince evolution evolution-data-server evolution-data-server-common evolution-exchange
  evolution-plugins f-spot file-roller gaim gaim-data gdebi gdm gedit gedit-common gftp-common gftp-gtk gimp-print gksu
  gnome-app-install gnome-applets gnome-applets-data gnome-control-center gnome-cups-manager gnome-games gnome-games-data
  gnome-keyring gnome-mag gnome-media gnome-media-common gnome-netstatus-applet gnome-orca gnome-panel gnome-panel-data
  gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-utils
  gnome-volume-manager gnupg gs-esp gstreamer0.10-alsa gstreamer0.10-plugins-base gstreamer0.10-plugins-good
  gstreamer0.10-x gthumb gtk2-engines gtkhtml3.8 gucharmap hal human-theme language-support-en libatspi1.0-0 libbind9-0
  libbonoboui2-0 libbonoboui2-common libbtctl4 libdevmapper1.02 libedataserverui1.2-8 libeel2-2 libeel2-data
  libgail-common libgail18 libgksu2-0 libgksuui1.0-1 libglade2.0-cil libgnome-desktop-2 libgnome-keyring0 libgnome-media0
  libgnome-speech3 libgnome-window-settings1 libgnome2-canvas-perl libgnome2.0-cil libgnomecanvas2-0
  libgnomecanvas2-common libgnomecupsui1.0-1c2a libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeprintui2.2-0
  libgnomeprintui2.2-common libgnomeui-0 libgstreamer-plugins-base0.10-0 libgtk2-perl libgtk2.0-0 libgtk2.0-bin
  libgtk2.0-cil libgtksourceview1.0-0 libgutenprintui2-1 libisccfg1 liblaunchpad-integration0 libldap2 liblpint-bonobo0
  libmetacity0 libmono-system1.0-cil libnautilus-burn4 libnautilus-extension1 libopal-2.2.0 libpanel-applet2-0
  libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libsasl2 libsasl2-modules libsdl1.2debian
  libsdl1.2debian-alsa libsexy2 libtotem-plparser1 libvte-common libvte9 libwnck-common libwnck18 libx11-6 libx11-dev
  libxalan2-java libxerces2-java libxrandr-dev libxrandr2 linux-headers-generic linux-image-generic
  linux-restricted-modules-generic metacity mkisofs mozilla-thunderbird mplayer nautilus nautilus-cd-burner nautilus-data
  nautilus-sendto notification-daemon openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-gnome openoffice.org-gtk openoffice.org-help-en-us
  openoffice.org-impress openoffice.org-l10n-en-gb openoffice.org-l10n-en-za openoffice.org-math
  openoffice.org-style-default openoffice.org-style-industrial openoffice.org-writer python-apt python-at-spi
  python-glade2 python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gtk2 python-gtkhtml2
  python-uno python-vte rhythmbox scim scim-gtk2-immodule scim-modules-socket synaptic tomboy totem totem-gstreamer
  totem-mozilla tsclient ubuntu-artwork ubuntu-desktop udev update-manager update-notifier usplash vbetool vim-common
  vim-gui-common vim-runtime vim-tiny vmware-server-kernel-modules vmware-tools-kernel-modules volumeid xfce4-mcs-plugins
  xfdesktop4 xfwm4 zenity
0 upgraded, 0 newly installed, 0 to remove and 212 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up acpid (1.0.4-5ubuntu5) ...
 * Loading ACPI modules...                                                                                                  
Message from syslogd@hertz at Wed Mar 14 13:23:56 2007 ...
hertz kernel: [ 7337.015337] Using specific hotkey driver
                                                                                                                     [ OK ]
 * Starting ACPI services...                                                                                                invoke-rc.d: initscript acpid, action "start" failed.
dpkg: error processing acpid (--configure):
 subprocess post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of acpi-support:
 acpi-support depends on acpid (>= 1.0.4-1ubuntu4); however:
  Package acpid is not configured yet.
dpkg: error processing acpi-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of powermanagement-interface:
 powermanagement-interface depends on acpi-support (>= 0.17); however:
  Package acpi-support is not configured yet.
dpkg: error processing powermanagement-interface (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acpid
 acpi-support
 powermanagement-interface
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by Kateikyoushi on 2007-03-14
Could you give us a littlebit more information when did it happen did you change anything before this ?
Try this.

```
sudo aptitude dist-upgrade
```

---

### Post by dannyboy79 on 2007-03-16
you always want to do an 

sudo aptitude update

prior to running any upgrade or dist-upgrade

also, if you have broken packages, you can go into synaptic, and click on fix broken packages and it should straighten them out. sometimes, that won't do it and you'll have to try to remove them and or purge them, sometimes you have to look for badsymlinks etc etc to fix them. sometimes you'll have to remove dependencies first but for the most part this won't happen IF you use the trusted and official repositories.

---

