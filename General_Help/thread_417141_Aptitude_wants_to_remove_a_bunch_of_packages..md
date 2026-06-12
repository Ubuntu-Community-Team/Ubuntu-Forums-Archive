---
title: "Aptitude wants to remove a bunch of packages."
date: 2007-04-21
forum: General Help
---

### Post by mikerobinson on 2007-04-21
I'm running kubuntu. When I run aptitude it wants to remove a whole lot of things it deems are "unused". > mike@mike:~$ sudo aptitude upgrade
Password:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done
The following packages are unused and will be REMOVED:
  apport-gtk arj at-spi bittorrent brltty-x11 bug-buddy
  contact-lookup-applet dbus-1-utils edgy-community-wallpapers
  edgy-gdm-themes edgy-session-splashes edgy-wallpapers ekiga eog esound
  evolution-exchange evolution-webcal f-spot festival festlex-cmu
  festlex-poslex festvox-kallpc16k file-roller firefox-gnome-support
  gcalctool gconf-editor gdebi gdm gedit gedit-common gimp gimp-data
  gimp-print gimp-python gnome-accessibility-themes gnome-bluetooth
  gnome-btdownload gnome-cups-manager gnome-games gnome-games-data
  gnome-games-extra-data gnome-keyring-manager gnome-mag gnome-nettool
  gnome-orca gnome-screensaver gnome-spell gnome-system-tools gnome-themes
  gnome-volume-manager gnome2-user-guide gray-theme gstreamer0.10-gnomevfs
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-ugly
  gstreamer0.10-tools gthumb gtk2-engines gtk2-engines-ubuntulooks
  gucharmap guile-1.6-libs gutenprint-locales hal-device-manager
  human-cursors-theme human-icon-theme human-theme hwdb-client-gnome
  im-switch industrialtango-theme language-selector legacyhuman-theme
  libbtctl4 libdbus-1-cil libdv-bin libestools1.2 libgimp2.0 libgnome-mag2
  libgnome-speech3 libgnomebt0 libgnomecupsui1.0-1c2a libgnomevfs2-bin
  libgucharmap5 libguile-ltdl-1 libgutenprintui2-1 libmono-data-tds1.0-cil
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil
  libmono-system-data1.0-cil libmono-system-web1.0-cil libmono1.0-cil
  liboobs-1-2 libopal-2.2.0 libpt-1.10.0 libpt-plugins-alsa
  libpt-plugins-v4l libpt-plugins-v4l2 libsidplay1 libwavpack0 libwmf0.2-7
  libxevie1 libxine-main1 libxml-grove-perl libxml-perl lzop
  nautilus-sendto onboard openoffice.org-gnome openoffice.org-gtk
  outdoors-theme p7zip python-at-spi python-gst0.10 python-virtkey
  python-vte rdesktop resilience-theme rhythmbox rss-glx scim
  scim-gtk2-immodule scim-modules-socket screensaver-default-images
  serpentine sharutils silicon-theme sound-juicer ssh-askpass-gnome
  tangerine-icon-theme tango-icon-theme tango-icon-theme-common tsclient
  ubuntu-artwork ubuntu-docs ubuntu-sounds update-manager update-notifier
  usplash-theme-ubuntu vino whois xsane xsane-common zenity
0 packages upgraded, 0 newly installed, 143 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 368MB will be freed.
Do you want to continue? [Y/n/?]   

Why does it think so many are unused? Going through the list, I know there are many of them that I DO use, like gimp, openoffice.org, firefox, etc. It almost looks like it wants to remove gnome. How do I set them as "used"? Or would there be any harm in removing them?

---

### Post by peebly on 2007-04-21
what are you trying to do ?

---

### Post by mikerobinson on 2007-04-21
> **peebly said:**
> what are you trying to do ?I was trying to set these packages as "used", like I said. I figured it out though. I just ran apt-get install ubuntu-desktop again and it downloaded a few other things and then the list of unused packages went down to about 50, and some of them were from edgy (I'm on feisty now) and others looked like things I would never use, so i just removed them.

---

