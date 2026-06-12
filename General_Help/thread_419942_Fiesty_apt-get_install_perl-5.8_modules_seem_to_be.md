---
title: "Fiesty:: apt-get install:: perl-5.8 modules seem to be broken :("
date: 2007-04-23
forum: General Help
---

### Post by da5id. on 2007-04-23
Hi all Ubuntu Forum people..

I have just recently completed the install of Ubuntu 7.04 Desktop-CD on my Dell laptop, well that was yesterday, today i have been configuring the native bcm43xx wireless driver module to control my wifi card, which took quite a lot of online research (here and in other linux forums) but ultimately was simply a case of extracting the firmware to /lib/firmware and /lib/hotplug/firmware, I also did the 915resolution tweaks in /etc/X11/xorg.conf and now i'm running 1280x800 GDM which looks very nice.

I am extremely impressed with this distro, after struggling for weeks with Knoppix and Debian installs, I think i have finally found my 'happy linux place' in Ubuntu and i look forward to exploring further what is at first impression an incredible Linux OS package.

This is my first post on the forum so i feel i should say a little about my knowledge, I am not new to Linux, i was a linux fan many years ago and learned the basics plus a bit from early releases of RedHat and Debian email and website server setups. I also program in Perl and C++. By no means an expert, but i do kind of know what i'm doing most of the time ;)

My first instinct after a successful desktop and wireless setup was to run 
```
sudo apt-get update
```
and see what packages i can add to this system, i would certainly like to have apache running, this is where i run into a few problems
```
user@hostname:~$ sudo apt-get install apache
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  apache-common
Suggested packages:
  apache-doc apache-ssl apache-perl
The following NEW packages will be installed:
  apache apache-common
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B/1243kB of archives.
After unpacking 3920kB of additional disk space will be used.
Do you want to continue [Y/n]? y
WARNING: The following packages cannot be authenticated!
  apache-common apache
Install these packages without verification [y/N]? y
Semicolon seems to be missing at /usr/share/perl/5.8/FileHandle.pm line 2.
Semicolon seems to be missing at /usr/share/perl/5.8/FileHandle.pm line 3.
Unquoted string "particles" may clash with future reserved word at /usr/share/perl/5.8/FileHandle.pm line 5.
Unquoted string "busyspheres" may clash with future reserved word at /usr/share/perl/5.8/FileHandle.pm line 7.
debconf: Perl may be unconfigured (syntax error at /usr/share/perl/5.8/FileHandle.pm line 3, near "Encoding"
Compilation failed in require at (eval 1) line 3.
BEGIN failed--compilation aborted at (eval 1) line 3.
) -- aborting
Selecting previously deselected package apache-common.
(Reading database ... 91948 files and directories currently installed.)
Unpacking apache-common (from .../apache-common_1.3.34-4.1_i386.deb) ...
Selecting previously deselected package apache.
Unpacking apache (from .../apache_1.3.34-4.1_i386.deb) ...
Setting up apache-common (1.3.34-4.1) ...
Semicolon seems to be missing at /usr/share/perl/5.8/base.pm line 2.
Semicolon seems to be missing at /usr/share/perl/5.8/base.pm line 3.
Unquoted string "fish" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Bareword found where operator expected at /usr/share/perl/5.8/base.pm line 5, near ")like"
        (Missing operator before like?)
Unquoted string "tobias" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Unquoted string "sargeant" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Array found where operator expected at /usr/share/perl/5.8/base.pm line 5, at end of line
Unquoted string "com" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Possible unintended interpolation of @mac in string at /usr/share/perl/5.8/base.pm line 5.
Bareword found where operator expected at /usr/share/perl/5.8/base.pm line 5, near "<calumr@mac.com> http"
        (Missing operator before http?)
Unquoted string "http" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Bareword found where operator expected at /usr/share/perl/5.8/base.pm line 5, near "//homepage"
        (Missing operator before homepage?)
Unquoted string "homepage" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Unquoted string "mac" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Unquoted string "com" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 5.
Unquoted string "flurry" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 7.
Unquoted string "xscreensaver" may clash with future reserved word at /usr/share/perl/5.8/base.pm line 12.
syntax error at /usr/share/perl/5.8/base.pm line 3, near "Encoding"
Compilation failed in require at /usr/share/perl5/Debconf/Log.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Log.pm line 7.
Compilation failed in require at /usr/share/perl5/Debconf/Db.pm line 7.
BEGIN failed--compilation aborted at /usr/share/perl5/Debconf/Db.pm line 7.
Compilation failed in require at /usr/share/debconf/frontend line 6.
BEGIN failed--compilation aborted at /usr/share/debconf/frontend line 6.
dpkg: error processing apache-common (--configure):
 subprocess post-installation script returned error exit status 255
dpkg: dependency problems prevent configuration of apache:
 apache depends on apache-common (>= 1.3.34-4.1); however:
  Package apache-common is not configured yet.
 apache depends on apache-common (<< 1.3.35); however:
  Package apache-common is not configured yet.
dpkg: error processing apache (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 apache-common
 apache
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
it seems to me that somehow the Perl modules and not working, or the Perl install itself is broken ? I'm really not too sure and i am hoping that someone has already tackled this or can provide some insight into how i can fix this.. my first idea is to remove the Perl 5.8 package and reinstall, i'm not so sure this is the best idea as 
```
sudo apt-get remove perl
```
advises that this will seriously break over 700 installed packages
after a bit more man reading i assume i can quickly remove perl with 
```
dpkg --remove -force-all perl
```
hoping the dependant packages won't notice if i quickly do 
```
sudo apt-get install perl
```
immediately after, sadly apt-get tells me that "perl is already the newest version."
i am now in the position where perl 5.8 status is 
```
*from sudo dpkg -s perl*
Status: deinstall ok installed
```
i cannot reinstall nor upgrade perl and i'm also very concerned that now apt-get is complaining that i have 660 broken dependancy package... WHOOOOOOPS !!!
```
user@hostname:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  acpi-support adduser alacarte alsa-base alsa-utils apache apache-common
  apache2-utils apmd apport apport-gtk appres aspell aspell-en at-spi
  avahi-autoipd avahi-daemon beforelight bind9-host binfmt-support bitmap
  bittorrent bluez-cups bluez-pin bluez-utils brltty-x11 bug-buddy
  ca-certificates capplets-data casper cdrecord command-not-found compiz
  compiz-core compiz-gnome compiz-gtk compiz-plugins console-setup
  console-terminus console-tools contact-lookup-applet cron cupsys cupsys-bsd
  cupsys-client cupsys-driver-gutenprint dbus dbus-1-utils debconf
  debconf-i18n defoma deskbar-applet desktop-effects dhcdbd dhcp3-client
  dictionaries-common dnsutils doc-base docbook-xml editres ekiga eog evince
  evolution evolution-data-server evolution-exchange evolution-plugins
  evolution-webcal f-spot fdutils file-roller firefox firefox-gnome-support
  fontconfig fontconfig-config foomatic-db-engine foomatic-db-hpijs
  foomatic-filters freeglut3 fstobdf ftp fuse-utils gaim gaim-data gcalctool
  gconf-editor gconf2 gconf2-common gdebi gdebi-core gdm gedit gimp gimp-print
  gimp-python gksu gnome-about gnome-accessibility-themes gnome-app-install
  gnome-applets gnome-applets-data gnome-btdownload gnome-control-center
  gnome-cups-manager gnome-doc-utils gnome-games gnome-games-data
  gnome-icon-theme gnome-keyring gnome-keyring-manager gnome-mag gnome-media
  gnome-media-common gnome-menus gnome-mount gnome-netstatus-applet
  gnome-nettool gnome-orca gnome-panel gnome-panel-data gnome-pilot
  gnome-pilot-conduits gnome-power-manager gnome-screensaver gnome-session
  gnome-spell gnome-system-monitor gnome-system-tools gnome-terminal
  gnome-terminal-data gnome-themes gnome-user-guide gnome-utils
  gnome-volume-manager gnupg gparted gs-common gs-esp gs-esp-x gsfonts
  gstreamer0.10-gnomevfs gstreamer0.10-plugins-bad gstreamer0.10-plugins-base
  gstreamer0.10-plugins-base-apps gstreamer0.10-plugins-good gstreamer0.10-x
  gthumb gtk2-engines gtk2-engines-pixbuf gtk2-engines-ubuntulooks gtkhtml3.14
  gucharmap hal hal-device-manager hpijs hplip human-theme hwdb-client-common
  hwdb-client-gnome iceauth ico ifupdown klogd language-selector
  language-selector-common language-support-en launchpad-integration lftp
  libaa1 libaprutil1 libatspi1.0-0 libaudio2 libbind9-0 libbonoboui2-0
  libbrlapi1 libcairo-perl libcairo2 libcairomm-1.0-1 libcamel1.2-10 libcurl3
  libdevel-symdump-perl libdmx1 libdns22 libebook1.2-9 libecal1.2-7
  libedata-book1.2-2 libedata-cal1.2-6 libedataserver1.2-9
  libedataserverui1.2-8 libeel2-2 libegroupwise1.2-13 libexchange-storage1.2-3
  libfontconfig1 libfontenc1 libfs6 libgail-common libgail-gnome-module
  libgail18 libgconf2-4 libgconf2.0-cil libgdiplus libgdl-1-0 libgdl-1-common
  libgimp2.0 libgksu1.2-1 libgksu2-0 libgksuui1.0-1 libgl1-mesa-dri
  libgl1-mesa-glx libglade2-0 libglade2.0-cil libglew1 libglib-perl
  libglib2.0-cil libglu1-mesa libglut3 libgmime2.2-cil libgnome-desktop-2
  libgnome-keyring0 libgnome-media0 libgnome-menu2 libgnome-window-settings1
  libgnome2-0 libgnome2-canvas-perl libgnome2-common libgnome2-perl
  libgnome2-vfs-perl libgnome2.0-cil libgnomecanvas2-0 libgnomecupsui1.0-1c2a
  libgnomekbd-common libgnomekbd1 libgnomekbdui1 libgnomeprint2.2-0
  libgnomeprintui2.2-0 libgnomeui-0 libgnomeui-common libgnomevfs2-0
  libgnomevfs2-bin libgnomevfs2-common libgnomevfs2-extra libgphoto2-2
  libgpod1 libgs-esp8 libgtk2-perl libgtk2.0-0 libgtk2.0-bin libgtk2.0-cil
  libgtk2.0-common libgtkhtml2-0 libgtkhtml3.14-19 libgtkmm-2.4-1c2a
  libgtksourceview1.0-0 libgtkspell0 libgtop2-7 libgucharmap6
  libgutenprintui2-1 libhtml-parser-perl libhtml-tagset-perl libhtml-tree-perl
  libice6 libisccfg1 liblaunchpad-integration0 libldap2 liblocale-gettext-perl
  liblpint-bonobo0 libmagick9 libmetacity0 libmono-cairo1.0-cil
  libmono-corlib1.0-cil libmono-corlib2.0-cil libmono-data-tds2.0-cil
  libmono-security2.0-cil libmono-sharpzip2.84-cil libmono-sqlite2.0-cil
  libmono-system-data2.0-cil libmono-system-web2.0-cil libmono-system1.0-cil
  libmono-system2.0-cil libmono2.0-cil libnautilus-burn4
  libnautilus-extension1 libndesk-dbus-glib1.0-cil libndesk-dbus1.0-cil
  libneon25 libnet-dbus-perl libnotify1 libnss-mdns liboobs-1-3 libopal-2.2.0
  libpanel-applet2-0 libpango1.0-0 libpango1.0-common libpaper1 libperl5.8
  libpoppler1 libpoppler1-glib libpq5 libpt-1.10.0 libpt-plugins-alsa
  libpt-plugins-v4l libpt-plugins-v4l2 librsvg2-2 librsvg2-common libsane
  libsasl2-2 libsasl2-modules libscim8c2a libsexy2 libslab0 libslp1 libsm6
  libsmbclient libsnmp9 libssl0.9.8 libstartup-notification0 libswfdec0.3
  libtext-charwidth-perl libtext-iconv-perl libtext-wrapi18n-perl
  libtotem-plparser1 libuniconf4.2 liburi-perl libvte9 libwmf0.2-7 libwnck18
  libwvstreams4.2-extras libwww-perl libx11-6 libx11-data libxau6 libxaw7
  libxcomposite1 libxcursor1 libxdamage1 libxdmcp6 libxevie1 libxext6
  libxfixes3 libxfont1 libxft2 libxi6 libxinerama1 libxkbfile1 libxklavier11
  libxml-parser-perl libxml-twig-perl libxmu6 libxmuu1 libxp6 libxpm4
  libxrandr2 libxrender1 libxres1 libxss1 libxt6 libxtrap6 libxtst6 libxv1
  libxxf86dga1 libxxf86misc1 libxxf86vm1 linux-sound-base listres lsb-release
  man-db mesa-utils metacity metacity-common mono-common mono-gac mono-jit
  mono-runtime mozilla-firefox-locale-en-gb myspell-en-gb myspell-en-us
  myspell-en-za nautilus nautilus-cd-burner nautilus-data nautilus-sendto
  netbase network-manager network-manager-gnome nmap nmapfe
  notification-daemon ntfsprogs ntpdate oclock onboard openoffice.org
  openoffice.org-base openoffice.org-calc openoffice.org-common
  openoffice.org-core openoffice.org-draw openoffice.org-evolution
  openoffice.org-filter-mobiledev openoffice.org-gnome openoffice.org-gtk
  openoffice.org-help-en-us openoffice.org-hyphenation openoffice.org-impress
  openoffice.org-java-common openoffice.org-l10n-en-gb
  openoffice.org-l10n-en-za openoffice.org-math openoffice.org-style-human
  openoffice.org-thesaurus-en-us openoffice.org-writer openssh-client openssl
  perl perl-base perl-modules pnm2ppa poppler-utils popularity-contest
  powermanagement-interface ppp pppconfig pppoeconf python python-apport
  python-apt python-at-spi python-bittorrent python-cairo python-central
  python-dbus python-gconf python-gdbm python-glade2 python-gmenu
  python-gnome2 python-gnome2-desktop python-gnome2-extras python-gnomecanvas
  python-gnupginterface python-gobject python-gst0.10 python-gtk2
  python-gtkhtml2 python-launchpad-bugs python-launchpad-integration
  python-libxml2 python-notify python-numeric python-orca-brlapi
  python-problem-report python-software-properties python-support python-uno
  python-virtkey python-vte python-xdg python-xml python2.5 rdesktop
  restricted-manager rhythmbox rss-glx samba-common scim scim-gtk2-immodule
  scim-modules-socket scim-modules-table scim-tables-additional screen
  screensaver-default-images scrollkeeper serpentine sgml-base sgml-data
  slocate smbclient smproxy software-properties-gtk sound-juicer
  ssh-askpass-gnome ssl-cert synaptic sysklogd system-tools-backends
  tangerine-icon-theme tango-icon-theme-common tasksel tasksel-data tcpdump
  telnet thunderbird-locale-en-gb tomboy totem totem-gstreamer totem-mozilla
  tsclient ttf-arabeyes ttf-arphic-ukai ttf-arphic-uming ttf-baekmuk
  ttf-bengali-fonts ttf-bitstream-vera ttf-dejavu ttf-devanagari-fonts
  ttf-freefont ttf-gentium ttf-gujarati-fonts ttf-indic-fonts
  ttf-kannada-fonts ttf-kochi-gothic ttf-kochi-mincho ttf-lao
  ttf-malayalam-fonts ttf-mgopen ttf-oriya-fonts ttf-punjabi-fonts
  ttf-tamil-fonts ttf-telugu-fonts ttf-thai-tlwg ubiquity
  ubiquity-frontend-gtk ubuntu-artwork ubuntu-desktop ubuntu-docs
  ubuntu-keyring ubuntu-minimal ubuntu-standard ucf unattended-upgrades
  update-inetd update-manager update-manager-core update-notifier user-setup
  usplash usplash-theme-ubuntu viewres vino vnc-common w3m wamerican wbritish
  wget wpasupplicant wvdial x-ttcidfont-conf x11-common x11perf xauth
  xbase-clients xbiff xbitmaps xcalc xclipboard xclock xconsole xcursorgen
  xditview xdpyinfo xdriinfo xev xeyes xf86dga xfd xfonts-100dpi xfonts-75dpi
  xfonts-base xfonts-encodings xfonts-scalable xfonts-utils xfontsel xgamma
  xgc xhost xinit xkbutils xkill xload xlogo xlsatoms xlsclients xlsfonts xmag
  xman xmessage xml-core xmodmap xmore xorg xpmutils xprop xrandr xrdb
  xrefresh xsane xscreensaver-data xscreensaver-gl xserver-xorg
  xserver-xorg-core xserver-xorg-input-all xserver-xorg-input-elographics
  xserver-xorg-input-evdev xserver-xorg-input-kbd xserver-xorg-input-mouse
  xserver-xorg-input-synaptics xserver-xorg-video-all xserver-xorg-video-apm
  xserver-xorg-video-ark xserver-xorg-video-ati xserver-xorg-video-chips
  xserver-xorg-video-cirrus xserver-xorg-video-cyrix xserver-xorg-video-dummy
  xserver-xorg-video-fbdev xserver-xorg-video-glint xserver-xorg-video-i128
  xserver-xorg-video-i740 xserver-xorg-video-i810 xserver-xorg-video-imstt
  xserver-xorg-video-mga xserver-xorg-video-neomagic
  xserver-xorg-video-newport xserver-xorg-video-nsc xserver-xorg-video-nv
  xserver-xorg-video-rendition xserver-xorg-video-s3
  xserver-xorg-video-s3virge xserver-xorg-video-savage
  xserver-xorg-video-siliconmotion xserver-xorg-video-sis
  xserver-xorg-video-sisusb xserver-xorg-video-tdfx xserver-xorg-video-tga
  xserver-xorg-video-trident xserver-xorg-video-tseng xserver-xorg-video-v4l
  xserver-xorg-video-vesa xserver-xorg-video-vga xserver-xorg-video-via
  xserver-xorg-video-vmware xserver-xorg-video-voodoo xset xsetmode
  xsetpointer xsetroot xsm xstdcmap xterm xtrap xutils xutils-dev xvidtune
  xvinfo xvncviewer xwd xwininfo xwud yelp zenity
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  perl-base
0 upgraded, 0 newly installed, 660 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 1381MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] no
Abort.

```

Please can anybody point me in the right direction, i'm a bit lost !?!

Thanks in advance (sorry for the huge post - i thought it best to be verbose)



.

---

### Post by da5id. on 2007-04-23
```
dpkg --configure -a
dpkg: unable to access dpkg status area: Read-only file system
```

I am now a bit concerned what may happen when i reboot.. any reply would be extremely helpful

Thanks

---

### Post by zvacet on 2007-04-23
```
sudo dpkg --configure -a
```

---

### Post by da5id. on 2007-04-23
Gnome started to behave really strangely.. couldn't click buttons in firefox, couldn't launch a terminal, so i was basically forced to restart GDM, which then complained some more and wouldn't let me log back into the desktop, 

so rebooted into 'recovery mode' and did a manual 
```
/sbin/fsck
``` 
after the auto check failed. 

reboot back into normal kernel and did 
```
sudo dpkg --configure -a
```
twice .. apache installed itself - WOW amazed at that :D

everything seems to be ok with the desktop and apt-get now..

but 
```
sudo dpkg -s perl
Package: perl
Status: [COLOR="Red"]deinstall[/COLOR] ok installed
```

would like to get this back to 
```
Status: install ok installed
```

i'm looking thru mans and infos but pointers appreciated.

Really impressed with the systems ability to recover from what seemed to me to be a pretty big mess (i shall be more careful from now on thats for sure)

Ubuntu for the win !!




:D

---

### Post by da5id. on 2007-04-23
double-posted sorry

---

