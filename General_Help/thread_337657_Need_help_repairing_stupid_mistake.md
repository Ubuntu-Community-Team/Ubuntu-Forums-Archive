---
title: "Need help repairing stupid mistake"
date: 2007-01-13
forum: General Help
---

### Post by jimbob on 2007-01-13
I mistakenly ran the following code on my Dapper machine instead of my Feisty machine to try to fix a release problem with the latter.

[COLOR="Blue"]wget [http://librarian.launchpad.net/5317874/python_2.4.4-1ubuntu2_all.deb](http://librarian.launchpad.net/5317874/python_2.4.4-1ubuntu2_all.deb)
wget [http://librarian.launchpad.net/5317875/python-minimal_2.4.4-1ubuntu2_all.deb](http://librarian.launchpad.net/5317875/python-minimal_2.4.4-1ubuntu2_all.deb)
sudo dpkg -i python-minimal_2.4.4-1ubuntu2_all.deb
sudo dpkg -i python_2.4.4-1ubuntu2_all.deb
[/COLOR]

The code failed at the first dpkg -i step but now Dapper has a bunch of packages marked as broken and will neither repair them nor allow me to install any more Dapper upgrades until they are removed.

Dapper is running fine but I know if I remove them nothing will work after that.

Is there some way that I can clear these remove flags or re-install the original Dapper python stuff over the top of what I have now?
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by bigken on 2007-01-13
go into synaptic and select custom filters then remove broken packages

---

### Post by jimbob on 2007-01-13
That doesn't work.  It tells me that it is an essential package and should not be removed.

It also wants to remove about 40 other packages including ubuntu-desktop and synaptic which it warns will destroy the system.

There must be a way to get the original Dapper python .deb from the repository and do a force install over the top of the current bad one. 

Please if anyone knows how let me know.
&#65279;________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Stochastic on 2007-01-13
I know apt-get has the ability to specify version numbers for a force install but I don't have any direct experience with doing that.  It may be helpful to look at debian help pages for things like that too, I find ubuntu is too quick to use synaptic all the time.  Read up on apt-get forced versions.

---

### Post by jimbob on 2007-01-13
Take a look at this:

apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies...Done
The following packages will be REMOVED
  alacarte alsa-utils anjuta bicyclerepair bittornado bittornado-gui bittorrent bluefish bug-buddy bum capplets-data compiz-gnome contact-lookup-applet deskbar-applet ekiga eog evince
  evolution evolution-data-server evolution-exchange evolution-plugins evolution-webcal file-roller firefox-gnome-support firestarter gaim gcalctool gconf-editor gconf2 gcontrol gdebi
  gdesklets gdesklets-data gdm gedit gimp-python gksu gnome-about gnome-app-install gnome-applets gnome-applets-data gnome-btdownload gnome-control-center gnome-cups-manager
  gnome-doc-utils gnome-games gnome-games-data gnome-media gnome-menus gnome-netstatus-applet gnome-nettool gnome-panel gnome-panel-data gnome-pilot gnome-pilot-conduits
  gnome-power-manager gnome-screensaver gnome-session gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal gnome-terminal-data gnome-utils gnome-volume-manager gnomebaker
  gnopernicus gok gparted gstreamer0.10-gnomevfs gstreamer0.10-plugins-good gthumb gtkhtml3.8 gucharmap hal-device-manager hplip hwdb-client kate kcontrol kdebase-bin kdebase-dev
  kdebase-kio-plugins kdelibs-bin kdelibs4-dev kdelibs4c2a kdesdk-scripts kdesktop kfind kicker konqueror konqueror-nsplugins ksysguard kwin language-selector language-selector-common
  launchpad-integration libbonoboui2-0 libebook1.2-5 libecal1.2-3 libedata-book1.2-2 libedata-cal1.2-1 libedataserverui1.2-6 libeel2-2 libexchange-storage1.2-1 libgail-gnome-module
  libgdl-1-0 libgdl-1-common libgnome-desktop-2 libgnome-menu2 libgnome2-0 libgnome2-common libgnome2-perl libgnome2-vfs-perl libgnomecupsui1.0-1c2a libgnomeui-0 libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgtkhtml3.8-15 libgucharmap4 libkonq4 liblaunchpad-integration0 liblpint-bonobo0 libnautilus-extension1 libpanel-applet2-0
  libswt3.1-gtk-java libswt3.1-gtk-jni libtotem-plparser1 listen lsb-release metacity nautilus nautilus-cd-burner nautilus-sendto notification-daemon nvu openoffice.org
  openoffice.org-gnome openoffice.org-gtk openoffice.org-writer python python-adns python-apt python-cddb python-clientcookie python-crypto python-egenix-mxproxy python-egenix-mxstack
  python-egenix-mxtexttools python-egenix-mxtools python-epydoc python-eunuchs python-examples python-gadfly python-gd python-gdbm python-genetic python-geoip python-gmenu python-gnome2
  python-gnome2-desktop python-gnome2-extras python-gnupginterface python-gst0.10 python-htmlgen python-htmltmpl python-id3lib python-imaging python-imaging-sane python-jabber
  python-kjbuckets python-launchpad-integration python-ldap python-libxml2 python-minimal python-mysqldb python-netcdf python-newt python-numeric python-pam python-parted python-pexpect
  python-pgsql python-pisock python-pqueue python-pyao python-pylibacl python-pyogg python-pyopenssl python-pyorbit python-pyvorbis python-pyxattr python-reportlab python-simpletal
  python-soappy python-sqlite python-stats python-syck python-tk python-unit python-uno python-vte python-xdg python-xml python-xmpp python2.4-gd python2.4-gnome2
  python2.4-gnome2-desktop python2.4-gnome2-extras python2.4-imaging-sane python2.4-soappy rhythmbox rhythmbox-dbg sbackup screem serpentine sound-juicer streamtuner synaptic totem
  totem-xine tsclient ubuntu-desktop ubuntu-minimal unattended-upgrades update-manager update-notifier vino yelp
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  python-minimal
0 upgraded, 0 newly installed, 230 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 540MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase ‘Yes, do as I say!’
 ?]

That doesn't look like something I really want to do ...
________________________________       
  If I can't be Mr. Root I won't play ...

[COLOR="Red"][SIZE="2"]*Registered Linux User #400396*[/SIZE][/COLOR]

---

### Post by Stochastic on 2007-01-13
what does your /etc/apt/sources.list look like? is there any fiesty entries?  run an apt-get update - those never hurt.  From what you've shown, I'd be inclined to search for the Dapper version of python-minimal and attempt to force install that version through apt-get.  Then I would retry the apt-get -f install.

I warn you though, I'm not an experienced developer; don't take this as your only advice.  Do some reading through google searches, man pages, apt-get wiki pages etc... to make sure you know what you're doing.  One of the first steps to recovering any broken system I find is to backup the /home directory.

---

