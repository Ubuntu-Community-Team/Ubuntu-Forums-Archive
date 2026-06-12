---
title: "Big problem with gconf2 and libgconf2-4"
date: 2007-03-15
forum: General Help
---

### Post by Reschat on 2007-03-15
I have a big problem.

When I open "Software Updates" an error says:

> **Software index is broken**
It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

Then I opened the terminal and wrote "sudo apt-get install -f" and it removed 130 programs, including gedit and gnorme-terminal (not good).
I got the programs installed again using the already open terminal.
Now when I try "sudo apt-get install -f" it says:
> $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  f-spot libgnomecupsui1.0-1c2a libcamel1.2-8 libgtkhtml3.8-15 tomboy evolution-webcal
  openoffice.org-gnome notification-daemon libgnomevfs2-0 gcalctool gthumb update-manager  python-gnome2 gnome-nettool gnome-media metacity nautilus libgnome2-0 vorbis-tools xchat-common  python-gnome2-extras gucharmap gnome-games hwdb-client-gnome gdebi evolution-exchange  libgconf2.0-cil evolution openoffice.org-gtk liboggflac3 libgnome-media0 gnome-power-manager  libexchange-storage1.2-2 xchat gnome-screensaver rhythmbox alacarte gedit gnome-menus  gnome-control-center gconf2 libbonoboui2-0 metacity-common libgnome2-perl gnome-pilot-conduits  python-gconf gnome-pilot libedata-cal1.2-6 update-notifier gnome-media-common nautilus-data  libgnome-menu2 libcurl3-gnutls gstreamer0.10-plugins-good gnome-terminal libpanel-applet2-0  libgnome2.0-cil gnome-utils libgconf2-4 gnome-btdownload gnome-orca libgnome2-common gnome-about  gnome-volume-manager nautilus-cd-burner gcompris eog gdm capplets-data libgnome2-vfs-perl  libegroupwise1.2-12 gnome-spell bug-buddy billard-gl-data libgnomeui-0 libecal1.2-7 tsclient vino  gnome-keyring-manager gnome-system-monitor firefox-gnome-support gnome-games-data python-pysqlite2  gnome-app-install gnome-sudoku libebook1.2-9 evolution-plugins gtkhtml3.8 libedataserverui1.2-8  totem-gstreamer contact-lookup-applet libgnome-window-settings1 libmetacity0 libedata-book1.2-2  evolution-data-server libgnomevfs2-bin libgnomevfs2-extra liblpint-bonobo0 libedataserver1.2-7 yelp  monkey-bubble gksu libeel2-2 gnome-netstatus-applet hal-device-manager gnome-terminal-data  libgucharmap5 onboard libgksu2-0 gnome-applets python-gmenu libgcompris-1-0 gcompris-data  gconf-editor libtotem-plparser1 gnome-system-tools libgnomebt0 gnome-panel gstreamer0.10-gnomevfs  totem deskbar-applet python-gnome2-desktop libnautilus-extension1 gnome-applets-data gnome-session  libgnome-desktop-2 totem-mozilla libgdl-1-0 bluez-pin file-roller serpentine nautilus-sendto  gnome-cups-manager gnome-panel-data sound-juicer libgnomevfs2-common libgdl-1-common
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  alacarte bluez-pin bug-buddy capplets-data contact-lookup-applet deskbar-applet eog evolution  evolution-data-server evolution-exchange evolution-plugins evolution-webcal f-spot file-roller  firefox-gnome-support gcalctool gcompris gconf-editor gconf2 gdebi gdm gedit gksu gnome-about  gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center  gnome-cups-manager gnome-games gnome-games-data gnome-keyring-manager gnome-media  gnome-media-common gnome-menus gnome-netstatus-applet gnome-nettool gnome-orca gnome-panel  gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-screensaver  gnome-session gnome-spell gnome-sudoku gnome-system-monitor gnome-system-tools gnome-terminal  gnome-terminal-data gnome-utils gnome-volume-manager gstreamer0.10-gnomevfs  gstreamer0.10-plugins-good gthumb gtkhtml3.8 gucharmap hal-device-manager hwdb-client-gnome  libbonoboui2-0 libcamel1.2-8 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6  libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libegroupwise1.2-12 libexchange-storage1.2-2  libgconf2-4 libgconf2.0-cil libgdl-1-0 libgdl-1-common libgksu2-0 libgnome-desktop-2  libgnome-media0 libgnome-menu2 libgnome-window-settings1 libgnome2-0 libgnome2-common  libgnome2-perl libgnome2-vfs-perl libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0  libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15  libgucharmap5 liblpint-bonobo0 libmetacity0 libnautilus-extension1 libpanel-applet2-0  libtotem-plparser1 metacity metacity-common monkey-bubble nautilus nautilus-cd-burner nautilus-data  nautilus-sendto notification-daemon onboard openoffice.org-gnome openoffice.org-gtk python-gconf  python-gmenu python-gnome2 python-gnome2-desktop python-gnome2-extras rhythmbox serpentine  sound-juicer tomboy totem totem-gstreamer totem-mozilla tsclient update-manager update-notifier  vino xchat xchat-common yelp
0 upgraded, 0 newly installed, 130 to remove and 0 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 374MB disk space will be freed.
Do you want to continue [Y/n]? n
Abort.

I can't remove those 130 programs again. Especially not "gnome-terminal".

Now I think the problem (according to Synaptic Package Manager) is in these two files:
 gconf2 and libgconf2-4

Then I tryed "sudo apt-get install libgconf2-4" and it said:
> $ sudo apt-get install libgconf2-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgconf2-4 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  gconf2: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
          Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
          Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
          Depends: gconf2-common (>= 2.18) but 2.16.0-0ubuntu1 is to be installed
          Depends: python (>= 2.5) but 2.4.3-11ubuntu3 is to be installed
  libgconf2-4: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed
               Depends: libglib2.0-0 (>= 2.12.9) but 2.12.4-0ubuntu1 is to be installed
               Depends: libxml2 (>= 2.6.27) but 2.6.26.dfsg-2ubuntu4 is to be installed
               Depends: gconf2-common (>= 2.18) but 2.16.0-0ubuntu1 is to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).
(same thing with "sudo apt-get install gconf2")

What should I do? How can I fix this error?

---

### Post by bapoumba on 2007-03-15
Hello, could you paste your repository list ?
```
cat /etc/apt/sources.list
```

and check if ubuntu-desktop is installed:
```
aptitude show ubuntu-desktop
```

---

### Post by Reschat on 2007-03-16
**cat /etc/apt/sources.list**

> $ cat /etc/apt/sources.list
## Add comments (##) in front of any line to remove it from being checked.   
## Use the following sources.list at your own risk.  

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-proposed main restricted universe multiverse

## MAJOR BUG FIX UPDATES produced after the final release
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates main restricted universe multiverse

## UBUNTU SECURITY UPDATES
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

## BACKPORTS REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse
deb-src [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

## PLF REPOSITORY (Unsupported.  May contain illegal packages.  Use at own risk.)
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy free
deb-src [http://medibuntu.sos-sts.com/repo/](http://medibuntu.sos-sts.com/repo/) edgy non-free
                                                                                                                                         
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera, DesktopSecure and more to come.) 
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) edgy-commercial main

## Listen
#deb [http://theli.free.fr/packages/](http://theli.free.fr/packages/) edgy listen


**aptitude show ubuntu-desktop**

> $ aptitude show ubuntu-desktop
Package: ubuntu-desktop
State: not installed
Version: 1.30
Priority: optional
Section: metapackages
Maintainer: Matt Zimmerman <mdz@ubuntu.com>
Uncompressed Size: 45.1k
Depends: acpi, acpi-support, acpid, alacarte, anacron, apmd, apport-gtk,
         avahi-daemon, bc, bug-buddy, cdparanoia, cdrecord,
         contact-lookup-applet, cupsys, cupsys-bsd, cupsys-client,
         cupsys-driver-gutenprint, dc, deskbar-applet, desktop-file-utils,
         diveintopython, doc-base, dvd+rw-tools, ekiga, eog, esound, evince,
         evolution, evolution-exchange, evolution-plugins, evolution-webcal,
         f-spot, file-roller, firefox, firefox-gnome-support, foo2zjs,
         foomatic-db, foomatic-db-engine, foomatic-db-hpijs, foomatic-filters,
         fortune-mod, gaim, gcalctool, gconf-editor, gdebi, gdm, gedit, gimp,
         gimp-print, gimp-python, gnome-about, gnome-app-install, gnome-applets,
         gnome-btdownload, gnome-control-center, gnome-cups-manager,
         gnome-icon-theme, gnome-keyring-manager, gnome-media, gnome-menus,
         gnome-netstatus-applet, gnome-nettool, gnome-panel,
         gnome-pilot-conduits, gnome-power-manager, gnome-session, gnome-spell,
         gnome-system-monitor, gnome-system-tools, gnome-terminal, gnome-themes,
         gnome-utils, gnome-volume-manager, gnome2-user-guide, gs-esp,
         gstreamer0.10-alsa, gstreamer0.10-esd, gstreamer0.10-plugins-base-apps,
         gthumb, gtk2-engines, gucharmap, hal, hal-device-manager, hotkey-setup,
         hwdb-client-gnome, landscape-client, language-selector, lftp,
         libgl1-mesa-glx, libglut3, libgnome2-perl, libgnomevfs2-bin,
         libgnomevfs2-extra, libpam-foreground, libpt-plugins-v4l,
         libpt-plugins-v4l2, libsasl2-modules, libstdc++5, libxp6, metacity,
         min12xxw, mkisofs, nautilus, nautilus-cd-burner, nautilus-sendto,
         notification-daemon, openoffice.org, openoffice.org-evolution,
         openoffice.org-gnome, pnm2ppa, powermanagement-interface, readahead,
         rhythmbox, rss-glx, screen, screensaver-default-images, scrollkeeper,
         serpentine, slocate, smbclient, sound-juicer, ssh-askpass-gnome,
         synaptic, tangerine-icon-theme, tango-icon-theme,
         tango-icon-theme-common, tomboy, totem, totem-mozilla, tsclient,
         ttf-bitstream-vera, ttf-dejavu, ttf-freefont, ubuntu-artwork,
         ubuntu-docs, ubuntu-sounds, unzip, update-notifier, usplash,
         usplash-theme-ubuntu, vino, wvdial, x-ttcidfont-conf, xkeyboard-config,
         xorg, xsane, xscreensaver-data, xscreensaver-gl, xterm, xvncviewer,
         yelp, zenity, zip
Recommends: bluez-cups, bluez-pin, bluez-utils, brltty, brltty-x11,
            example-content, gcc, gnome-accessibility-themes, gnome-games,
            gnome-mag, gnome-orca, gnome-screensaver, hplip,
            linux-headers-generic, make, onboard, powernowd, scim,
            scim-gtk2-immodule, ttf-arabeyes, ttf-arphic-ukai, ttf-arphic-uming,
            ttf-baekmuk, ttf-gentium, ttf-indic-fonts, ttf-kochi-gothic,
            ttf-kochi-mincho, ttf-lao, ttf-malayalam-fonts, ttf-mgopen,
            ttf-thai-tlwg, xcursor-themes
Description: The Ubuntu desktop system
 This package depends on all of the packages in the Ubuntu desktop system 
 
 It is also used to help ensure proper upgrades, so it is recommended that it
 not be removed.


Should I try:
sudo apt-get install ubuntu-desktop 
or/and with all the "Depends" and "Recommends"?

---

### Post by bapoumba on 2007-03-16
> **Reschat said:**
> 
$ sudo apt-get install libgconf2-4
Reading package lists... Done
Building dependency tree
Reading state information... Done
libgconf2-4 is already the newest version.
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
**gconf2: Depends: libc6 (>= 2.5-0ubuntu1) but 2.4-1ubuntu12.3 is to be installed**

Hello :)

Have a look here:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libc6]("http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exact=1&keywords=libc6")
libc6 (>= 2.5-0ubuntu1) = feisty version
2.4-1ubuntu12.3 = edgy version

Please try to comment out the **edgy-proposed** repos, and may be the **backports** repos too, and then:
```
sudo aptitude update
sudo aptitude install ubuntu-desktop
```

edgy-proposed are tests repos, Packages make it there to be tested before they get to the main repos. I suppose you have installed some package from this repos, during a regular upgrade as they are in your source.list, and now you have dependencies conflicts that forced ubuntu-desktop to be removed.
I would also comment out the backports, and just use the regular edgy repos to fix your issue (I'm not 100% sure these have to be commented out, you can put them back in after).

---

### Post by Reschat on 2007-03-16
I think the problem is solved now. Thank you bapoumba.

I downloaded a package to edgy from:
[http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exac](http://packages.ubuntu.com/cgi-bin/search_packages.pl?searchon=names&version=all&exac) t=1&keywords=libc6
then I installed it with:
$ sudo dpkg -i libc6_2.4-1ubuntu12_i386.deb 
and then I did:
$ sudo aptitude update
and then
$ sudo aptitude install ubuntu-desktop

And now the system is updated.
And to "sudo apt-get install -f" it says:
> $ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  billard-gl-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
and to "sudo apt-get install libgconf2-4" it says:
> $ sudo apt-get install libgconf2-4
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgconf2-4 is already the newest version.
The following packages were automatically installed and are no longer required:
  billard-gl-data
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

So I think it works now. 
(But should I use the "apt-get autoremove"-command?)

---

### Post by bapoumba on 2007-03-16
Looks like billard-gl-data is a game. If not needing it, yes, yo can autoremove it :)

---

