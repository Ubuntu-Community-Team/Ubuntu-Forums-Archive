---
title: "Nautilus to 100% bug dependencies broken"
date: 2006-11-23
forum: General Help
---

### Post by juantovarm on 2006-11-23
HELP! I was getting my cpu up to 100% because of nautilus. I went to [https://launchpad.net/distros/ubuntu...lus/+bug/54684](https://launchpad.net/distros/ubuntu...lus/+bug/54684) and installed libgnomevfs2-common_2.16.1-0ubuntu3_all.deb and it gave me an error saying breohken dependencies and that i should run sudo apt-get install -f, i did it. It killed my installation. I had to reinstall completely and i reinstalled the package. I have the same problem now, but i am not going to run sudo apt-get install -f. What can i do???

Here's the sudo apt-get install -f

(The following packages were installed automatically and are no longer needed)
Los siguientes paquetes fueron instalados automáticamente y ya no son necesarios:
  f-spot libgnomecupsui1.0-1c2a libcamel1.2-8 libgtkhtml3.8-15 tomboy
  evolution-webcal ekiga openoffice.org-gnome libgnomevfs2-0 gcalctool gthumb
  python-gnome2 gnome-media nautilus libgnome2-0 python-gnome2-extras
  gucharmap gnome-games hwdb-client-gnome evolution-exchange evolution
  gnome-power-manager libexchange-storage1.2-2 gnome-screensaver rhythmbox
  alacarte gedit gnome-menus gnome-control-center libbonoboui2-0
  ubuntu-desktop libgnome2-perl gnome-pilot-conduits gnome-pilot
  libedata-cal1.2-6 update-notifier libgnome-menu2 gnome-terminal
  libpanel-applet2-0 libgnome2.0-cil gnome-utils gnome-btdownload gnome-orca
  gnome-about gnome-volume-manager nautilus-cd-burner eog libgnome2-vfs-perl
  gnome-spell bug-buddy libgnomeui-0 libecal1.2-7 tsclient vino
  gnome-keyring-manager gnome-system-monitor firefox-gnome-support evince
  libebook1.2-9 evolution-plugins gtkhtml3.8 libedataserverui1.2-8
  totem-gstreamer contact-lookup-applet libgnome-window-settings1
  libedata-book1.2-2 evolution-data-server libgnomevfs2-bin libgnomevfs2-extra
  liblpint-bonobo0 yelp libeel2-2 gnome-netstatus-applet hal-device-manager
  libgucharmap5 gnome-applets python-gmenu gconf-editor libtotem-plparser1
  gnome-system-tools libgnomebt0 gnome-panel gstreamer0.10-gnomevfs totem
  deskbar-applet python-gnome2-desktop libnautilus-extension1 gnome-session
  libgnome-desktop-2 totem-mozilla libgdl-1-0 file-roller serpentine
  nautilus-sendto gnome-cups-manager sound-juicer libgdl-1-common
Use «apt-get autoremove» para desinstalarlos.
Los siguientes paquetes se ELIMINARÁN:
  alacarte bug-buddy contact-lookup-applet deskbar-applet ekiga eog evince
  evolution evolution-data-server evolution-exchange evolution-plugins
  evolution-webcal f-spot file-roller firefox-gnome-support gcalctool
  gconf-editor gedit gnome-about gnome-applets gnome-btdownload
  gnome-control-center gnome-cups-manager gnome-games gnome-keyring-manager
  gnome-media gnome-menus gnome-netstatus-applet gnome-orca gnome-panel
  gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver
  gnome-session gnome-spell gnome-system-monitor gnome-system-tools
  gnome-terminal gnome-utils gnome-volume-manager gstreamer0.10-gnomevfs
  gthumb gtkhtml3.8 gucharmap hal-device-manager hwdb-client-gnome
  libbonoboui2-0 libcamel1.2-8 libebook1.2-9 libecal1.2-7 libedata-book1.2-2
  libedata-cal1.2-6 libedataserverui1.2-8 libeel2-2 libexchange-storage1.2-2
  libgdl-1-0 libgdl-1-common libgnome-desktop-2 libgnome-menu2
  libgnome-window-settings1 libgnome2-0 libgnome2-perl libgnome2-vfs-perl
  libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0
  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-extra libgtkhtml3.8-15
  libgucharmap5 liblpint-bonobo0 libnautilus-extension1 libpanel-applet2-0
  libtotem-plparser1 nautilus nautilus-cd-burner nautilus-sendto
  openoffice.org-gnome python-gmenu python-gnome2 python-gnome2-desktop
  python-gnome2-extras rhythmbox serpentine sound-juicer tomboy totem
  totem-gstreamer totem-mozilla tsclient ubuntu-desktop update-notifier vino
  yelp
0 actualizados, 0 se instalarán, 97 para eliminar y 0 no actualizados.
Necesito descargar 0B de archivos.
Se liberarán 225MB después de desempaquetar.

---

### Post by RAOF on 2006-11-23
I don't speak that language, so I can't decipher the messages from apt-get install -f.  It looks, however, like "ELIMINARÁN" means "Removed".  In that case, yes, you should not say "yes".  That's most of the desktop packages there!

If you **only** installed libgnomevfs2-common_2.16.1-0ubuntu3_all.deb, then you'll have a problem.  You should probably install at least the packages:
[http://people.ubuntu.com/~seb128/debug/54684/libgnomevfs2-0_2.16.1-0ubuntu3_i386.deb](http://people.ubuntu.com/~seb128/debug/54684/libgnomevfs2-0_2.16.1-0ubuntu3_i386.deb)
[http://people.ubuntu.com/~seb128/debug/54684/libgnomevfs2-bin_2.16.1-0ubuntu3_i386.deb](http://people.ubuntu.com/~seb128/debug/54684/libgnomevfs2-bin_2.16.1-0ubuntu3_i386.deb)
[http://people.ubuntu.com/~seb128/debug/54684/libgnomevfs2-common_2.16.1-0ubuntu3_all.deb](http://people.ubuntu.com/~seb128/debug/54684/libgnomevfs2-common_2.16.1-0ubuntu3_all.deb)

And possibly the others from that page, not just the -common one.

---

### Post by juantovarm on 2006-11-23
doesn't let me. as soon as i install the common one i cannot install anything else. and in order to install the other ones, i need to install that one first...go figure ](*,) :confused: :-k

---

### Post by RAOF on 2006-11-23
You might want to try installing them with ```
sudo dpkg --install --force-depends *.deb
```

That should work.

---

### Post by juantovarm on 2006-11-23
went back to Dapper, i'll try that later on or in another pc.
Thank you anyways:D

---

