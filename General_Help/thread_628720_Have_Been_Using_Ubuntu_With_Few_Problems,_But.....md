---
title: "Have Been Using Ubuntu With Few Problems, But...."
date: 2007-12-01
forum: General Help
---

### Post by Strfie89 on 2007-12-01
I have been using Ubuntu with relatively few problems since September 2007. My thanks to everyone behind it for making the OS!

However, my computer's hardware is sorely lacking, and I learned of Xubuntu a little too late....
Most applications load and run with a lag. 3D games don't want to run at all, achieving a maximum amazing 1 frame per 5 seconds.

Basic System Specifications:
Gateway GT ("designed for Windows NT"; Phoenix BIOS (c) 1985-1999)
Pentium III 800 MHz processor
320 MB RAM
60 GB HDD (currently split as follows: ~29 GB Windows ME, ~15 GB Ubuntu, ~12 GB personal data (some personal data is on the other partitions, however))
NVidia TNT2 graphics card (which has paltry performance at best; it's using the Restricted Drivers)

All this adds up to a computer that has trouble doing anything without notable lag.

Since Ubuntu and Xubuntu are **similar** operating systems, is it possible to simply overwrite an Ubuntu installation and not lose any installed applications, personal data, etc., on the same partition? 

Or am I going to have to start making a list of said apps, back up my data, format (that one partition) and load up again?

---

### Post by mikewhatever on 2007-12-01
You could try this link [http://psychocats.net/ubuntu/purexfce](http://psychocats.net/ubuntu/purexfce) for removing ubuntu-desktop and this [http://psychocats.net/ubuntu/xubuntu](http://psychocats.net/ubuntu/xubuntu) to install xubuntu. I am afraid you are going to loose the programs installed with Ubuntu by default, such as Open Office, Totem, etc. It is,however possible to reinstall them on Xubuntu later.

---

### Post by atomkarinca on 2007-12-01
You can install xubuntu on your ubuntu install. Just open up a terminal and type:

```
sudo apt-get install xubuntu-desktop
```After the installation is finished, log out and on the login screen hit f10, click on change session, select xfce from the menu and log in. That should be about it.

---

### Post by elliotjreed on 2007-12-01
You can replace GNOME Ubuntu with Xubuntu by running the command:

```
sudo apt-get install xubuntu-desktop
```

If you want the complete Xfce desktop with no GNOMEy things, type this into the terminal when you are in Xubuntu:

```
sudo apt-get remove alacarte aspell bittorrent bluez-cups bluez-gnome bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsh bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet dcraw deskbar-applet dictionaries-common diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet firefox-gnome-support fping gcj-4.2-base gconf-editor gedit gedit-common gij gij-4.2 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data gnome-doc-utils gnome-keyring-manager gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-spell gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 hal-device-manager hwdb-client-common hwdb-client-gnome libalut0 libao2 libart2.0-cil libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcucul0 libdecoration0 libdeskbar-tracker libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj8-1 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa-dri libglade2.0-cil libglew1.4 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpod2 libgsl0 libgtk2.0-cil libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtksourceview2.0-0 libgtksourceview2.0-common libhsqldb-java libicu36 libiec61883-0 libjaxp1.3-java libjline-java liblpint-bonobo0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp6 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 liboil0.3 libopal-2.2 libopenal0a libpam-gnome-keyring libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librarian0 libraw1394-8 librsvg2.0-cil libservlet2.4-java libshout3 libsndfile1 libsoup2.2-8 libsvg1 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvorbisenc2 libvorbisfile3 libwavpack1 libwpg-0.1-1 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto o3read openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-extras python-pygtksourceview python-uno rdesktop rhythmbox rss-glx serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc yelp && sudo apt-get install xubuntu-desktop
```

There is a guide, the same as what I have put her (and where I got the info.) here:

[http://www.psychocats.net/ubuntu/purexfce]("http://www.psychocats.net/ubuntu/purexfce")

---

### Post by Strfie89 on 2007-12-01
Before I proceed, what exactly do I lose/ gain by replacing GNOME with Xfce (or Ubuntu with Xubuntu, for that matter)?

---

### Post by Strfie89 on 2007-12-01
So, in doing this, I'm **not** losing any apps, notable functionality, or data, **and** getting a speed boost.

Correct? :)

---

### Post by atomkarinca on 2007-12-01
If you just do a Xubuntu install, yes that's pretty much just like a software install. About speed boost, most probably, it's one of the most liteweight DE's.

---

### Post by Strfie89 on 2007-12-01
Thanks to everyone for their assistance. :) I'll start trying the conversion now.

---

### Post by Strfie89 on 2007-12-02
I have done the first suggested part (thanks again to elliotjreed):

sudo apt-get install xubuntu-desktop

But the second part leaves me wary. What exactly will I gain and lose by executing this code (plain English, please!)?

---

