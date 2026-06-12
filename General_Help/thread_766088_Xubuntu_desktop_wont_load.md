---
title: "Xubuntu desktop wont load"
date: 2008-04-25
forum: General Help
---

### Post by bedake on 2008-04-25
I am running a hardy install and I've noticed it's been getting slower and slower on my laptop as time goes on, I think gnome may be too much for it now.  I decided to install xubuntu desktop.

I ran sudo aptitude install xubuntu-desktop

When I try to load an xfce session through the GDM, it hangs on a blue screen and won't go any farther.  Can anyone suggest anything? It would be a big help thanks!

---

### Post by xjgnsdof on 2008-04-25
To install XFCE, input the following:

```
sudo aptitude update && sudo aptitude install xubuntu-desktop 
```

Given your laptop's aging, you might want to remove GNOME, which will leave you with a true Xubuntu distro. To do that, input the following (look out, it's huge!):

```
sudo apt-get remove alacarte aspell bittorrent bluez-cups bluez-gnome bluez-utils bogofilter bogofilter-bdb bogofilter-common brltty brltty-x11 bsh bug-buddy capplets-data cdrdao cli-common compiz compiz-core compiz-fusion-plugins-extra compiz-fusion-plugins-main compiz-gnome compiz-plugins consolekit contact-lookup-applet dcraw deskbar-applet dictionaries-common diveintopython ekiga eog espeak evince evolution evolution-common evolution-data-server evolution-data-server-common evolution-exchange evolution-plugins evolution-webcal f-spot fast-user-switch-applet firefox-gnome-support fping gcj-4.2-base gconf-editor gedit gedit-common gij gij-4.2 gimp-python gnome-about gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-desktop-data gnome-doc-utils gnome-keyring-manager gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits gnome-power-manager gnome-session gnome-spell gnome-terminal gnome-terminal-data gnome-user-guide gnome-utils gnome-volume-manager gstreamer0.10-alsa gstreamer0.10-esd gstreamer0.10-gnomevfs gstreamer0.10-plugins-base gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.14 hal-device-manager hwdb-client-common hwdb-client-gnome libalut0 libao2 libart2.0-cil libavc1394-0 libbeagle0 libbluetooth2 libcaca0 libcamel1.2-10 libcdio6 libcompizconfig-backend-gconf libcompizconfig0 libcucul0 libdecoration0 libdeskbar-tracker libdv4 libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9 libedataserverui1.2-8 libeel2-2 libeel2-data libegroupwise1.2-13 libexchange-storage1.2-3 libgcj-bc libgcj-common libgcj8-1 libgconf2.0-cil libgda3-3 libgda3-common libgdl-1-0 libgdl-1-common libgdl-gnome-1-0 libgksu1.2-1 libgksuui1.0-1 libgl1-mesa-dri libglade2.0-cil libglew1.4 libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-pilot2 libgnome-vfs2.0-cil libgnome-window-settings1 libgnome2.0-cil libgnomevfs2-bin libgnomevfs2-extra libgpod2 libgsl0 libgtk2.0-cil libgtkhtml2.0-cil libgtkhtml3.14-19 libgtkhtml3.8-15 libgtksourceview2.0-0 libgtksourceview2.0-common libhsqldb-java libicu36 libiec61883-0 libjaxp1.3-java libjline-java liblpint-bonobo0 libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil libmono-system2.0-cil libmono0 libmono2.0-cil libmtp6 libmusicbrainz4c2a libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil libneon26 liboil0.3 libopal-2.2 libopenal0a libpam-gnome-keyring libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l libpt-plugins-v4l2 librarian0 libraw1394-8 librsvg2.0-cil libservlet2.4-java libshout3 libsndfile1 libsoup2.2-8 libsvg1 libtracker-gtk0 libtrackerclient0 libvisual-0.4-0 libvorbisenc2 libvorbisfile3 libwavpack1 libwpg-0.1-1 libwps-0.1-1 libxalan2-java libxerces2-java libxml2-utils mono-common mono-gac mono-jit mono-runtime nautilus nautilus-cd-burner nautilus-data nautilus-sendto o3read openoffice.org openoffice.org-base openoffice.org-calc openoffice.org-common openoffice.org-core openoffice.org-draw openoffice.org-evolution openoffice.org-gnome openoffice.org-gtk openoffice.org-hyphenation openoffice.org-impress openoffice.org-java-common openoffice.org-math openoffice.org-style-human openoffice.org-writer pkg-config python-bittorrent python-gmenu python-gnome2-extras python-pygtksourceview python-uno rdesktop rhythmbox rss-glx serpentine sound-juicer ssh-askpass-gnome tangerine-icon-theme tomboy totem-mozilla tracker tracker-search-tool tsclient ttf-opensymbol ubuntu-desktop ubuntu-docs ubuntu-sounds usplash-theme-ubuntu vino whois xdg-user-dirs xdg-user-dirs-gtk xsane xsane-common xsltproc yelp
```

If you're still getting weird reactions, there's always the panacea of a full install.

---

### Post by helgman on 2008-04-25
I had the exact same problem yesterday. Installed Ubuntu and the installed xubuntu-desktop, logged out and tried the xfce-session with the result of a blue-screen-of-nothing. Went back to the log in screen and headed into GNOME with no problem.

I'm not sure what fixed my problem, but it's working for me right now and the only thing that comes to mind is that I did a reboot ...

Good luck,
Helgman

---

### Post by bedake on 2008-04-25
Well crap, maybe it would be best if i just installed xubuntu from scratch...

---

### Post by helgman on 2008-05-03
I'm sad to say it wasn't that simple. Now, every time I boot the machine and try to login, first time ... nothing, just a blue screen. I have to retry one or two times before I get my desktop.

I'm not really sure what logs (if any) to investigate but so far I've found nothing that hints of the problem might be.

---

### Post by Mazza558 on 2008-05-03
My advice: go back to Gutsy.

---

### Post by haiji on 2008-05-05
Honestly, I think it's a 'minor' bug. I can live with it until the problem is fixed in the repos. Killing the x-server and trying again takes me 5 seconds. In fact, I can remember worse problems in previous xubuntu releases.

---

### Post by fudo81 on 2008-05-10
I think I have the same problem, except that I have a clean Xubuntu (no GNOME). I had no problems with Gutsy, but since I updated it to Hardy, desktop doesn't start. I haven't tried to just keep killing the x-server and retrying - I will soon.

Anyway, probably the weirdest fact is that something actually DOES start: if I press Alt+F2 during the blue (cyan) screen, a familiar "execute command" window appears.

Any ideas about what's going on?

---

