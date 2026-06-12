---
title: "HOW TO: Install kubuntu-/ubuntu-desktop successfully on Xubuntu Edgy"
date: 2006-11-14
forum: General Help
---

### Post by Velotix on 2006-11-14
You may think this is a very simple process that doesn't deserve a how-to. Well, it should be, but it isn't, so for the benefit of every poor Xubuntu user who just wants to try out the other desktops without dual/triple-booting, I present to you all this how-to guide.



This computer initially had Xubuntu installed on it. After a few days, though, I got a bit fed up of Xfce and wanted to see what the other Ubuntu desktops are like. So, first I fired up aptitude and installed *kubuntu-desktop*. 

Kubuntu installs without any problems whatsoever, so long as you remember to **set the default display manager to *"gdm"* during the kubuntu-desktop install** otherwise you'll break your Xubuntu session manager, which only seems capable of coping with GDM. I set it to KDM initially thinking I was setting the default desktop session. Silly me - GDM and KDM are the login managers, so by setting the default to KDM, whenever I logged out of Xfce sessions, I expected to get back to the login screen - lo and behold, the computer shuts down instead. On top of that, it won't turn off automatically either. That got annoying until I realised what I'd done.

Again, **set the default display manager to *"gdm"* during the kubuntu-desktop install** to prevent grief and a broken session manager.

You'll be surprised to learn that installing *ubuntu-desktop* is even worse. This is what happened when I tried:

```
$ sudo aptitude install ubuntu-desktop
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
[b][i][color="red"]The following packages are BROKEN:
  evince-gtk xubuntu-system-tools[/color][/i][/b] 
The following packages have been automatically kept back:
  libavahi-client3 libavahi-compat-libdnssd1 libavahi-qt3-1 
  linux-restricted-modules-2.6.17-10-generic 
  linux-restricted-modules-common 
The following NEW packages will be automatically installed:
  alacarte aspell aspell-en at-spi binfmt-support bittorrent brltty-x11 
  bug-buddy capplets-data cli-common contact-lookup-applet deskbar-applet 
  desktop-base ekiga eog esound evince evolution evolution-data-server 
  evolution-data-server-common evolution-exchange evolution-plugins 
  evolution-webcal f-spot festival festlex-cmu festlex-poslex 
  festvox-kallpc16k file-roller firefox-gnome-support gcalctool 
  gconf-editor gedit gedit-common gimp-python gnome-about gnome-applets 
  gnome-applets-data gnome-btdownload gnome-control-center 
  gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games 
  gnome-games-data gnome-keyring-manager gnome-mag gnome-media 
  gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet 
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot 
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session 
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal 
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager 
  gnome2-user-guide gstreamer0.10-alsa gstreamer0.10-esd 
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base 
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good 
  gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.8 gucharmap 
  guile-1.6-libs hal-device-manager hwdb-client-gnome libatspi1.0-0 
  libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl4 
  libcairo-perl libcamel1.2-8 libcdio6 libdbus-1-cil libdjvulibre15 libdv4 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libeel2-data 
  libegroupwise1.2-12 libestools1.2 libexchange-storage1.2-2 
  libgconf2.0-cil libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common 
  libgksu1.2-1 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl 
  libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 
  libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 
  libgnome-speech3 libgnome-window-settings1 libgnome2-0 
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl 
  libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common 
  libgnomevfs2-extra libgtk2-perl libgtk2.0-cil libgtkhtml3.8-15 
  libgtksourceview-common libgtksourceview1.0-0 libgucharmap5 
  libguile-ltdl-1 libiec61883-0 liblpint-bonobo0 libmetacity0 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnautilus-burn4 
  libnautilus-extension1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 
  libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l 
  libpt-plugins-v4l2 libqthreads-12 librpm4 libshout3 libsoup2.2-8 
  libtotem-plparser1 libxevie1 libxklavier11 libxml2-utils metacity 
  metacity-common mono-common mono-gac mono-jit mono-runtime nautilus 
  nautilus-cd-burner nautilus-data nautilus-sendto openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk python-at-spi python-gmenu 
  python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gst0.10 rdesktop rhythmbox rpm rss-glx 
  screensaver-default-images serpentine sharutils sound-juicer 
  ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer 
  totem-mozilla tsclient ubuntu-docs update-notifier usplash-theme-ubuntu 
  vino vnc-common whois xsane xsane-common xsltproc xvncviewer yelp zenity 
The following packages will be automatically REMOVED:
  gcalctool-gtk 
The following packages have been kept back:
  avahi-daemon info libavahi-common-data libavahi-common3 libavahi-core4 
  screen 
The following NEW packages will be installed:
  alacarte aspell aspell-en at-spi binfmt-support bittorrent brltty-x11 
  bug-buddy capplets-data cli-common contact-lookup-applet deskbar-applet 
  desktop-base ekiga eog esound evince evolution evolution-data-server 
  evolution-data-server-common evolution-exchange evolution-plugins 
  evolution-webcal f-spot festival festlex-cmu festlex-poslex 
  festvox-kallpc16k file-roller firefox-gnome-support gcalctool 
  gconf-editor gedit gedit-common gimp-python gnome-about gnome-applets 
  gnome-applets-data gnome-btdownload gnome-control-center 
  gnome-cups-manager gnome-desktop-data gnome-doc-utils gnome-games 
  gnome-games-data gnome-keyring-manager gnome-mag gnome-media 
  gnome-media-common gnome-menus gnome-mime-data gnome-netstatus-applet 
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot 
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session 
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal 
  gnome-terminal-data gnome-themes gnome-utils gnome-volume-manager 
  gnome2-user-guide gstreamer0.10-alsa gstreamer0.10-esd 
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-base 
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good 
  gstreamer0.10-tools gstreamer0.10-x gthumb gtkhtml3.8 gucharmap 
  guile-1.6-libs hal-device-manager hwdb-client-gnome libatspi1.0-0 
  libavahi-glib1 libavc1394-0 libbeagle0 libbeecrypt6 libbonobo2-0 
  libbonobo2-common libbonoboui2-0 libbonoboui2-common libbtctl4 
  libcairo-perl libcamel1.2-8 libcdio6 libdbus-1-cil libdjvulibre15 libdv4 
  libebook1.2-9 libecal1.2-7 libedata-book1.2-2 libedata-cal1.2-6 
  libedataserver1.2-7 libedataserverui1.2-8 libeel2-2 libeel2-data 
  libegroupwise1.2-12 libestools1.2 libexchange-storage1.2-2 
  libgconf2.0-cil libgda2-3 libgda2-common libgdl-1-0 libgdl-1-common 
  libgksu1.2-1 libgksuui1.0-1 libglade2.0-cil libglew1 libglib-perl 
  libglib2.0-cil libgmime-2.0-2 libgmime2.2-cil libgnome-desktop-2 
  libgnome-mag2 libgnome-media0 libgnome-menu2 libgnome-pilot2 
  libgnome-speech3 libgnome-window-settings1 libgnome2-0 
  libgnome2-canvas-perl libgnome2-common libgnome2-perl libgnome2-vfs-perl 
  libgnome2.0-cil libgnomebt0 libgnomecupsui1.0-1c2a libgnomeui-0 
  libgnomeui-common libgnomevfs2-0 libgnomevfs2-bin libgnomevfs2-common 
  libgnomevfs2-extra libgtk2-perl libgtk2.0-cil libgtkhtml3.8-15 
  libgtksourceview-common libgtksourceview1.0-0 libgucharmap5 
  libguile-ltdl-1 libiec61883-0 liblpint-bonobo0 libmetacity0 
  libmono-cairo1.0-cil libmono-corlib1.0-cil libmono-data-tds1.0-cil 
  libmono-security1.0-cil libmono-sharpzip0.84-cil libmono-sqlite1.0-cil 
  libmono-system-data1.0-cil libmono-system-web1.0-cil 
  libmono-system1.0-cil libmono0 libmono1.0-cil libnautilus-burn4 
  libnautilus-extension1 liboil0.3 libopal-2.2.0 libpanel-applet2-0 
  libpisock9 libpisync0 libpt-1.10.0 libpt-plugins-alsa libpt-plugins-v4l 
  libpt-plugins-v4l2 libqthreads-12 librpm4 libshout3 libsoup2.2-8 
  libtotem-plparser1 libxevie1 libxklavier11 libxml2-utils metacity 
  metacity-common mono-common mono-gac mono-jit mono-runtime nautilus 
  nautilus-cd-burner nautilus-data nautilus-sendto openoffice.org-evolution 
  openoffice.org-gnome openoffice.org-gtk python-at-spi python-gmenu 
  python-gnome2 python-gnome2-desktop python-gnome2-extras 
  python-gnomecanvas python-gst0.10 rdesktop rhythmbox rpm rss-glx 
  screensaver-default-images serpentine sharutils sound-juicer 
  ssh-askpass-gnome tangerine-icon-theme tomboy totem totem-gstreamer 
  totem-mozilla tsclient ubuntu-desktop ubuntu-docs update-notifier 
  usplash-theme-ubuntu vino vnc-common whois xsane xsane-common xsltproc 
  xvncviewer yelp zenity 
The following packages will be REMOVED:
  gcalctool-gtk 
0 packages upgraded, 233 newly installed, 1 to remove and 11 not upgraded.
Need to get 119MB of archives. After unpacking 567MB will be used.
[b][i][color="red"]The following packages have unmet dependencies:
  xubuntu-system-tools: Conflicts: gnome-system-tools but 2.15.5-0ubuntu2 is to be installed.
  evince-gtk: Conflicts: evince but 0.6.1-0ubuntu1 is to be installed.
Resolving dependencies...
The following actions will resolve these dependencies:

Keep the following packages at their current version:
deskbar-applet [Not Installed]
evince [Not Installed]
file-roller [Not Installed]
gedit [Not Installed]
gnome-applets [Not Installed]
gnome-games [Not Installed]
gnome-games-data [Not Installed]
gnome-media [Not Installed]
gnome-media-common [Not Installed]
gnome-panel [Not Installed]
gnome-panel-data [Not Installed]
gnome-session [Not Installed]
gnome-system-tools [Not Installed]
gnome-volume-manager [Not Installed]
gstreamer0.10-plugins-good [Not Installed]
libdv4 [Not Installed]
libgda2-3 [Not Installed]
libgda2-common [Not Installed]
libgnome-media0 [Not Installed]
nautilus [Not Installed]
nautilus-cd-burner [Not Installed]
nautilus-data [Not Installed]
nautilus-sendto [Not Installed]
python-gnome2-desktop [Not Installed]
python-gnome2-extras [Not Installed]
rhythmbox [Not Installed]
serpentine [Not Installed]
sound-juicer [Not Installed]
totem [Not Installed]
totem-gstreamer [Not Installed]
totem-mozilla [Not Installed]
[/color][color="blue"]ubuntu-desktop [Not Installed][/color][color="red"]

Leave the following dependencies unresolved:
gnome-control-center recommends gnome-session[/color][/i][/b]
Score is 80

Accept this solution? [Y/n/q/?]
```

Yes, to resolve the dependency problem, in the end it wouldn't install *ubuntu-desktop* at all! Fantastic! And what's worse, one of the packages clashes with a critical Xubuntu system file!

You can probably see where this is going. Yes, to install Ubuntu from a default Xubuntu install, ***you have to break your Xubuntu install completely***.

At this point, then, you'll probably be very, very worried. Fear not, this problem can be solved. I was lucky; I ran the install through my Kubuntu desktop. If you don't feel like installing Kubuntu just to install Ubuntu, then you'll need to run the install outside of a desktop environment.

First, though, you have to rid yourself of the offending Xubuntu file. (You'll be glad to know that the Ubuntu file it clashes with replaces it completely once you're ready to restore your Xubuntu install.)

In a break with typical procedure, we're deliberately not going to uninstall the entire Xubuntu desktop just to install Ubuntu - so you need to load up Synaptic/Adept.

Search for the file *xubuntu-system-tools* and select it for removal. Remove it. You'll notice that it takes *xubuntu-desktop* with it. Congratulations! Your Xubuntu install is ruined!

Now, go to command line to run the rest of the procedure safely: press <Ctrl><Alt><F1>. From here, it's time to do another bit of weeding. Type:

```
sudo aptitude remove evince-gtk
```

By removing this you'll have weeded out the two files that cause this whole mess. NOW you can get on with the install. However, you need to do it in two parts, because aptitude refuses to install *gnome-session* unless you install *gnome-session* manually. Type:

```
sudo aptitude install gnome-session
```

Start the install and wait for the download to finish and *gnome-session* to be configured. **NOW** type:

```
sudo aptitude install ubuntu-desktop
```

Hooray! The install now works! Wait for it to download and configure itself.

Now that Ubuntu and GNOME are installed, Xubuntu can be safely restored. Type:

```
sudo aptitude install xubuntu-desktop
```

Wait for the download to complete and configure itself, and then reboot X.

Enjoy! :)

---

### Post by frodon on 2006-11-14
Please fill a bug report if you think there's a bug, it would help more if this "bug" would be fixed in the repos.
Here are some explanations on how to fill a bug report :
[http://ubuntuforums.org/showthread.php?t=284595](http://ubuntuforums.org/showthread.php?t=284595)

Nice workaround however.

---

