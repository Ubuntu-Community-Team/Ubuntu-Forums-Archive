---
title: "get rid of spinner next to pointer, get rid of Gnome"
date: 2006-11-15
forum: General Help
---

### Post by will47 on 2006-11-15
I just switched to Ubuntu from FC5 on my work desktop; I used to work at a Debian shop, so I know a decent bit about the normal Debian utils etc.


I have a kind of dumb question - the same thing drove me nuts about Fedora. The default theme has some sort of little spinner thingie that shows up next to the pointer (for example when a page is loading in Firefox, and possibly in other applications). I think this is a Gnome-ism, but I could be wrong. Anyway, is there a safe way to get rid of this (on FC, I removed the redhat-artwork package, which took care of it).

Also, is there a safe way to get rid of Gnome entirely?

I'm using Windowmaker as my window manager.

---

### Post by TheRingmaster on 2006-11-15
run this command that i got from here [http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
 
> 
sudo apt-get remove alacarte app-install-data-commercial apport apport-gtk at-spi binfmt-support bittorrent brltty-x11 bug-buddy capplets-data cli-common contact-lookup-applet dbus-1-utils deskbar-applet desktop-file-utils edgy-community-wallpapers edgy-gdm-themes edgy-session-splashes edgy-wallpapers ekiga eog esound evince evolution evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot festival festlex-cmu festlex-poslex festvox-kallpc16k file-roller firefox firefox-gnome-support gaim gaim-data gamin gcalctool gconf-editor gconf2 gdebi gdm gedit gedit-common gimp gimp-data gimp-print gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games gnome-games-data gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager gnome2-user-guide gray-theme gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtk2-engines gtk2-engines-ubuntulooks gtkhtml3.8 gucharmap guile-1.6-libs hal-device-manager human-cursors-theme human-gtk-theme human-icon-theme human-theme hwdb-client-gnome industrialtango-theme language-selector legacyhuman-theme libaa1 libatspi1.0-0 libavahi-glib1 libavc1394-0 libbeagle0 libbonobo2-0 libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl4 libcairo-perl libcamel1.2-8 libcdio6 libcroco3 libdbus-1-cil libdjvulibre15 libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-12 libenchant1c2a libestools1.2 libexchange-storage1.2-2 libgadu3 libgail-common libgail18 libgamin0 libgconf2.0-cil libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 libgnome-keyring0 libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 libgnome-speech3 libgnome-window-settings1 libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomebt0 libgnomecanvas2-0 libgnomecanvas2-common libgnomecups1.0-1 libgnomecupsui1.0-1c2a libgnomeprint2.2-0 libgnomeprint2.2-data libgnomeprintui2.2-0 libgnomeprintui2.2-common libgnomeui-0 libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgsf-1-114 libgsf-1-common libgtk2-perl libgtk2.0-cil libgtkhtml2-0 libgtkhtml3.8-15 libgtksourceview-common libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgtop2-common libgucharmap5 libguile-ltdl-1 libgutenprintui2-1 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl libiec61883-0 libkpathsea4 liblaunchpad-integration0 liblircclient0 liblpint-bonobo0 libmeanwhile1 libmetacity0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil libmono-system-web1.0-cil libmono-system1.0-cil libmono0 libmono1.0-cil libmyspell3c2 libnautilus-burn4 libnautilus-extension1 libnet-dbus-perl libnotify1 libnspr4 libnss3 liboil0.3 liboobs-1-2 libopal-2.2.0 libpanel-applet2-0 libpisock9 libpisync0 libpoppler1-glib libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 libqthreads-12 librsvg2-2 librsvg2-common libsexy2 libshout3 libsoup2.2-8 libtotem-plparser1 liburi-perl libvte-common libvte9 libwmf0.2-7 libwnck-common libwnck18 libwww-perl libxevie1 libxklavier11 libxml-grove-perl libxml-parser-perl libxml-perl libxml2-utils libxres1 metacity metacity-common mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto notification-daemon onboard openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-style-industrial outdoors-theme python-apport-utils python-at-spi python-cairo python-gconf python-gdbm python-glade2 python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas python-gnupginterface python-gobject python-gst0.10 python-gtk2 python-gtkhtml2 python-launchpad-integration python-numeric python-problem-report python-pyorbit python-virtkey python-vte python-xdg python-xml rdesktop resilience-theme rhythmbox rss-glx scim scim-gtk2-immodule scim-modules-socket screensaver-default-images serpentine shared-mime-info silicon-theme sound-juicer ssh-askpass-gnome synaptic system-tools-backends tangerine-icon-theme tango-icon-theme tango-icon-theme-common tomboy totem totem-gstreamer totem-mozilla tsclient ubuntu-artwork ubuntu-desktop ubuntu-docs ubuntu-sounds unattended-upgrades update-manager update-notifier usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xscreensaver-data xscreensaver-gl xsltproc xvncviewer yelp zenity


---

### Post by strabes on 2006-11-15
aside from the above command, which I suspect would break your system (just a hunch) you could download a different mouse cursor theme from gnome-look.org or something.

---

### Post by TheRingmaster on 2006-11-15
no it doesn't break your system I've tried it. 
 
ps. I thought he wanted to get rid of gnome entirely?

---

### Post by strabes on 2006-11-15
oh ok lol. i just realized that you wanted to remove gnome so gnome-look.org wouldn't help you too much.

---

### Post by TheRingmaster on 2006-11-15
> **strabes said:**
> oh ok lol. i just realized that you wanted to remove gnome so gnome-look.org wouldn't help you too much.
lol

---

### Post by DavidTangye on 2006-11-15
>some sort of little spinner thingie
Isn't that the 'wait I'm working' icon, and its animated. In this case then changing or customising desktop/windows themes should be the best way? You way sounds like a hack.

>is there a safe way to get rid of Gnome entirely?
Why not go into Synaptic and remove the Gnome packages. This will tell you about application packages that depend on it and give you the opportunity to either rid of them all or cancel. I certainly would never consider hacking files or directories. There are thousands of dependencies in a system these days (Windows or Linux), and hacking is usually the quickest way to stuff the whole system. It also leads to myriad complaints on these  forums about 'xyz does not seem to work properly anymore' ;-)

---

### Post by TheRingmaster on 2006-11-15
> **DavidTangye said:**
> >some sort of little spinner thingie
Isn't that the 'wait I'm working' icon, and its animated. In this case then changing or customising desktop/windows themes should be the best way? You way sounds like a hack.
 
>is there a safe way to get rid of Gnome entirely?
Why not go into Synaptic and remove the Gnome packages. This will tell you about application packages that depend on it and give you the opportunity to either rid of them all or cancel. I certainly would never consider hacking files or directories. There are thousands of dependencies in a system these days (Windows or Linux), and hacking is usually the quickest way to stuff the whole system. It also leads to myriad complaints on these forums about 'xyz does not seem to work properly anymore' ;-)
 
 
my code up above is exactly the same thing you just said in the second paragraph.

---

### Post by ynnhoj on 2006-11-15
it seems to me that if you use the ubuntu server install cd, you can install just the base system (sans window manager), and then choose whatever packages you'd like to add afterwards using aptitude.  that way you'd avoid gnome altogether.  but somebody else will be needed to confirm/deny this, 'cause i've never done it before.

or maybe you could be using xubuntu?  (that is, if you're down with xfce)

---

### Post by DavidTangye on 2006-11-15
> **TheRingmaster said:**
> my code up above is exactly the same thing you just said in the second paragraph.

Agreed, its the same thing more or less, using the command line. I missed your post as I was typing mine, and on the phone etc. :-)

---

### Post by DavidTangye on 2006-11-15
> **strabes said:**
> aside from the above command, which I suspect would break your system (just a hunch)  I agree with Ringmaster. As long as you use apt-get or Synaptic, I believe/trust/hope that a system cannot be broken. If you lose an ability to do something, because a facility is removed, then simply re-install it. That is the whole idea behind a very robust package manager like debian and is what jumps you into an entirely better world compared to installing and hacking tarballs or Windoze systems. 

> **strabes said:**
> you could download a different mouse cursor theme from gnome-look.org or something. Agreed: if yo do not like the theme, install another or learn how to make changes to what you have, ie customise the theme (and save it as your own?)

---

