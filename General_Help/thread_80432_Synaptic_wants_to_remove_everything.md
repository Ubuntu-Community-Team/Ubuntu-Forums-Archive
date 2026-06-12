---
title: "Synaptic wants to remove everything"
date: 2005-10-22
forum: General Help
---

### Post by Cud on 2005-10-22
Help! Synaptic wants to kill Hoary!!!
I tried to compile flight gear and had an unsuccesful install of libc6 >02.3.2.ds1-21 and lib gcc1 and fgfs base >0.9.8 . Before I had tried to install flightgear version 0.9.4 directly from synaptic which was also unsuccesful, due to dependency problems. When I restarted Synaptic I got an error telling me to fix 3 broken packages. So I did, and then was about to apply some other (minor) changes that I made when I read the fine print and saw that synaptic wants to

apt (essential) will be removed
dpkg (essential) will be removed
sysvinit (essential) will be removed
acroread will be removed
acroread-plugins will be removed
alien will be removed
amule will be removed
anacron will be removed
apt-utils will be removed
aptitude will be removed
aspell will be removed
aspell-bin will be removed
aspell-en will be removed
at will be removed
base-config will be removed
console-common will be removed
console-data will be removed
console-tools will be removed
cupsys will be removed
cupsys-bsd will be removed
cupsys-driver-gimpprint will be removed
cupsys-driver-gimpprint-data will

and so on... a total of 190 packages, including 3 essential packages.

What did I do??
What Can I do?
Thanks

EDIT-
It seems to be the broken packages Libgcc1, Libstdc++6, and Flightgear 0.9.8-3. When I mark them for removal synaptic tells me that the chosen action affects other packages, and then presents me with the list of 188 other packages. Still clueless as to how to solve this problem.
Any help greatly appreciated.

---

### Post by Xian on 2005-10-22
You need to install the Hoary version of libc6: [libc6_2.3.2.ds1-20ubuntu13]("http://archive.ubuntu.com/ubuntu/pool/main/g/glibc/libc6_2.3.2.ds1-20ubuntu13_i386.deb").
The one you are using is not system compatable.

---

### Post by Cud on 2005-10-22
O.K. I installed the hoary version of libc6 and then opend up Synaptic again. Unfortunately, I get more or less the same problem. 6 Broken packages.
flightgear 0.9.8-3
libc6dev 2.3.2.ds1-20ubuntu
libc6-i686
libgcc1 1:4.0.2-2
libstdc++6 4.0.2.2
locales 2.3.2ds1-20ubuntu
If I try to fix them Synaptic gives me that same message as before, about removing 191 packages.
If I try to remove them I get the same error.
Is this happening because I tried to install packages that aren't Hoary compatible?
And If so, how can I clean this mess up?
Thanks

---

### Post by Xian on 2005-10-22
[QUOTE=Cud]Is this happening because I tried to install packages that aren't Hoary compatible?
And If so, how can I clean this mess up?[/QUOTE]
Open Synaptic and click on the "Status" button in the lower left corner.
Then highlight the line in the tree that says "Installed (Local or Obsolete)"

Look through the list to pick out those applications or libraries you recently installed which are not from the official Hoary repositories. There will be some valid entries so you will need to weed them out of the mix. Next, just highlight and remove the applicable packages.

---

### Post by Cud on 2005-10-22
I think I'm trying to do what your describing. 3 of the 6 broken packages are in this list, and as far as I can tell these (Broken) packages are the only ones that I have recently tried to install. But when I highlight them and want to remove them, I get that same ol' message from synaptic telling me " Mark additional requieed changes?" and that "The chosen action also affects other packages. The following changes are required in order to proceed." 
To be removed
And then the 191 packages

So it seems to me that I am still stuck in the same place.
Thanks

---

### Post by Xian on 2005-10-22
Ugh. Let's start from scratch and see where it leads.
What is the output of this command: 

$ sudo apt-get -f install

---

### Post by Cud on 2005-10-22
jesse@finally:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following extra packages will be installed:
  libc6 ssh-krb5
Suggested packages:
  glibc-doc rssh
The following packages will be REMOVED:
  acroread acroread-plugins alien amule anacron apt apt-utils aptitude aspell
  aspell-bin aspell-en at base-config console-common console-data
  console-tools cupsys cupsys-bsd cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data d4x debhelper diveintopython docbook-dsssl dpkg
  dselect dvd+rw-tools dvdauthor faad flashplayer-mozilla flightgear
  foomatic-db-gimp-print foomatic-db-hpijs freeglut3 g++ g++-3.3 gaim gcc
  gcc-3.3 gdm gedit gedit-common gksu gnome-app-install gnome-cups-manager
  gnome-doc-tools gnome-games gnome-gv gnome-media gnome-netstatus-applet
  gnome-spell gnome-system-monitor gnome-system-tools gnome-volume-manager
  gnomemeeting gnubg groff-base gs-common gs-esp gstreamer0.8-misc
  gstreamer0.8-plugins gstreamer0.8-sid gstreamer0.8-vorbis gtranscode gxine
  hal hal-device-manager hpijs html2text hwdb-client ifupdown ijsgimpprint
  imagemagick initscripts language-pack-en language-pack-en-base
  language-support-en lftp libaspell15 libavifile-0.7c102 libdb4.2++ libgc1
  libgcc1 libgksu1.2-0 libgksuui1.0-0 libgle3 libglut3 libgnomecupsui1.0-1
  libgtk1.2 libgtkspell0 libid3-3.8.3 libmagick6 libmjpegtools0 libmodplug0
  libmusicbrainz2 libmusicbrainz4 libmyspell3 libopenal0 libopenh323-1.15.2
  libostyle1 libpt-1.8.3 libpt-plugins-alsa libpt-plugins-v4l2
  libsidplay1-c102 libsigc++-1.2-5c102 libsmpeg0 libstdc++5 libstdc++5-3.3-dev
  libstdc++6 libstlport4.6 libwvstreams3-base libwxgtk2.5.3
  libwxgtk2.5.3-python libxine1 lsb lshw mailx man-db mencoder-586 mjpegtools
  mozilla-acroread mozilla-firefox mozilla-firefox-gnome-support
  mozilla-firefox-locale-en-gb mozilla-mplayer mozilla-plugin-vlc
  mozilla-thunderbird mplayer-386 mplayer-fonts mutt nerolinux netbase
  openjade openoffice.org openoffice.org-bin openoffice.org-debian-files
  openoffice.org-gtk-gnome openoffice.org-help-en
  openoffice.org-hyphenation-en-gb openoffice.org-hyphenation-en-us
  openoffice.org-l10n-en openoffice.org-thesaurus-en-us openssh-client pnm2ppa
  popularity-contest postfix postfix-tls ppp pppconfig pppoeconf python-apt
  python-id3lib python-musicbrainz python-opengl python2.4-id3lib
  python2.4-musicbrainz python2.4-opengl rar rhythmbox rss-glx slocate
  sound-juicer synaptic sysvinit telnet totem-xine transcode ubuntu-base udev
  update-manager update-notifier vim vim-common vlc vnc-common w3m wvdial
  wxpython2.5.3 wxvlc x-window-system-core xbase-clients xlibmesa-glu xmms
  xorg-driver-synaptics xpdf xpdf-reader xpdf-utils xscreensaver-gl
  xserver-xorg xvncviewer yelp
The following NEW packages will be installed:
  ssh-krb5
The following packages will be upgraded:
  libc6
WARNING: The following essential packages will be removed
This should NOT be done unless you know exactly what you are doing!
  apt libgcc1 (due to apt) libstdc++5 (due to apt) dpkg dselect (due to dpkg)
  sysvinit initscripts (due to sysvinit)
1 upgraded, 1 newly installed, 191 to remove and 5 not upgraded.
3 not fully installed or removed.
Need to get 5528kB of archives.
After unpacking 786MB disk space will be freed.
You are about to do something potentially harmful
To continue type in the phrase 'Yes, do as I say!'

---

### Post by Xian on 2005-10-22
What does this command result in?

$ aptitude install libc6=2.3.2.ds1-20ubuntu13

---

### Post by Cud on 2005-10-22
jesse@finally:~$ sudo aptitude install libc6=2.3.2.ds1-20ubuntu13
Reading package lists... Done
Building dependency tree
Reading extended state information
Initializing package states... Done
The following packages are unused and will be REMOVED:
  myspell-en-gb myspell-en-us
The following NEW packages will be automatically installed:
  ssh-krb5
The following packages will be automatically REMOVED:
  acroread acroread-plugins alien amule anacron apt apt-utils aptitude
  aspell aspell-bin aspell-en at base-config console-common console-data
  console-tools cupsys cupsys-bsd cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data d4x debhelper diveintopython docbook-dsssl
  dpkg dselect dvd+rw-tools dvdauthor faad flashplayer-mozilla flightgear
  foomatic-db-gimp-print foomatic-db-hpijs freeglut3 gaim gdm gedit
  gedit-common gksu gnome-app-install gnome-cups-manager gnome-doc-tools
  gnome-games gnome-gv gnome-media gnome-netstatus-applet gnome-spell
  gnome-system-monitor gnome-system-tools gnome-volume-manager gnomemeeting
  gnubg groff-base gs-common gs-esp gstreamer0.8-misc gstreamer0.8-plugins
  gstreamer0.8-vorbis gtranscode gxine hal hal-device-manager hpijs
  html2text hwdb-client ifupdown ijsgimpprint initscripts language-pack-en
  language-pack-en-base language-support-en lftp libaspell15
  libavifile-0.7c102 libc6-dev libc6-i686 libdb4.2++ libgc1 libgcc1
  libgksu1.2-0 libgksuui1.0-0 libgle3 libglut3 libgnomecupsui1.0-1
  libgtk+2.0-directfb-udeb-dev libgtkspell0 libid3-3.8.3 liblive.com-dev
  libmagick6 libmjpegtools0 libmusicbrainz2 libmusicbrainz4 libmyspell3
  libopenal0 libopenh323-1.15.2 libostyle1 libpt-1.8.3 libpt-plugins-alsa
  libpt-plugins-v4l2 libsigc++-1.2-5c102 libsmpeg0 libstdc++5 libstlport4.6
  libwvstreams3-base libwxgtk2.5.3 libwxgtk2.5.3-python locales lsb lshw
  mailx man-db mencoder-586 mjpegtools mozilla-acroread mozilla-firefox
  mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
  mozilla-mplayer mozilla-plugin-vlc mplayer-386 mplayer-fonts mutt
  nerolinux netbase openjade openoffice.org openoffice.org-bin
  openoffice.org-debian-files openoffice.org-gtk-gnome
  openoffice.org-help-en openoffice.org-hyphenation-en-gb
  openoffice.org-hyphenation-en-us openoffice.org-l10n-en
  openoffice.org-thesaurus-en-us openssh-client pnm2ppa popularity-contest
  postfix postfix-tls ppp pppconfig pppoeconf python-apt python-id3lib
  python-musicbrainz python-opengl python2.4-id3lib python2.4-musicbrainz
  python2.4-opengl rar rhythmbox rss-glx slocate sound-juicer synaptic
  sysvinit telnet totem-xine transcode ubuntu-base udev update-manager
  update-notifier vim vim-common vlc vnc-common w3m wvdial wxpython2.5.3
  wxvlc x-window-system-core xbase-clients xlibmesa-glu
  xorg-driver-synaptics xpdf xpdf-reader xpdf-utils xscreensaver-gl
  xserver-xorg xvncviewer yelp
The following packages have been kept back:
  libcurl3 libssl0.9.7 linux-image-2.6.10-5-386 streamtuner
The following NEW packages will be installed:
  ssh-krb5
The following packages will be REMOVED:
  acroread acroread-plugins alien amule anacron apt apt-utils aptitude
  aspell aspell-bin aspell-en at base-config console-common console-data
  console-tools cupsys cupsys-bsd cupsys-driver-gimpprint
  cupsys-driver-gimpprint-data d4x debhelper diveintopython docbook-dsssl
  dpkg dselect dvd+rw-tools dvdauthor faad flashplayer-mozilla flightgear
  foomatic-db-gimp-print foomatic-db-hpijs freeglut3 g++ g++-3.3 gaim gcc
  gcc-3.3 gdm gedit gedit-common gksu gnome-app-install gnome-cups-manager
  gnome-doc-tools gnome-games gnome-gv gnome-media gnome-netstatus-applet
  gnome-spell gnome-system-monitor gnome-system-tools gnome-volume-manager
  gnomemeeting gnubg groff-base gs-common gs-esp gstreamer0.8-misc
  gstreamer0.8-plugins gstreamer0.8-sid gstreamer0.8-vorbis gtranscode
  gxine hal hal-device-manager hpijs html2text hwdb-client ifupdown
  ijsgimpprint imagemagick initscripts language-pack-en
  language-pack-en-base language-support-en lftp libaspell15 libatk1.0-dev
  libavifile-0.7c102 libc6-dev libc6-i686 libdb4.2++ libdirectfb-dev
  libdirectfb-udeb-dev libexpat1-dev libfontconfig1-dev libfreetype6-dev
  libgc1 libgcc1 libgksu1.2-0 libgksuui1.0-0 libgle3 libglib2.0-dev
  libglut3 libgnomecupsui1.0-1 libgtk+2.0-directfb-udeb-dev libgtk1.2
  libgtk2.0-dev libgtkspell0 libid3-3.8.3 liblive.com-dev libmagick6
  libmjpegtools0 libmodplug0 libmusicbrainz2 libmusicbrainz4 libmyspell3
  libncursesw5-dbg libncursesw5-dev libopenal0 libopenh323-1.15.2
  libostyle1 libpango1.0-dev libpng12-dev libpt-1.8.3 libpt-plugins-alsa
  libpt-plugins-v4l2 libsidplay1-c102 libsigc++-1.2-5c102 libsmpeg0
  libstdc++5 libstdc++5-3.3-dev libstdc++6 libstlport4.6 libwvstreams3-base
  libwxgtk2.5.3 libwxgtk2.5.3-python libx11-dev libxext-dev libxft-dev
  libxi-dev libxine1 libxrender-dev locales lsb lshw mailx man-db
  mencoder-586 mjpegtools mozilla-acroread mozilla-firefox
  mozilla-firefox-gnome-support mozilla-firefox-locale-en-gb
  mozilla-mplayer mozilla-plugin-vlc mozilla-thunderbird mplayer-386
  mplayer-fonts mutt nerolinux netbase openjade openoffice.org
  openoffice.org-bin openoffice.org-debian-files openoffice.org-gtk-gnome
  openoffice.org-help-en openoffice.org-hyphenation-en-gb
  openoffice.org-hyphenation-en-us openoffice.org-l10n-en
  openoffice.org-thesaurus-en-us openssh-client pnm2ppa popularity-contest
  postfix postfix-tls ppp pppconfig pppoeconf python-apt python-id3lib
  python-musicbrainz python-opengl python2.4-id3lib python2.4-musicbrainz
  python2.4-opengl rar rhythmbox rss-glx slocate sound-juicer synaptic
  sysvinit telnet totem-xine transcode ubuntu-base udev update-manager
  update-notifier vim vim-common vlc vnc-common w3m wvdial wxpython2.5.3
  wxvlc x-window-system-core xbase-clients xlibmesa-glu xmms
  xorg-driver-synaptics xpdf xpdf-reader xpdf-utils xscreensaver-gl
  xserver-xorg xvncviewer yelp zlib1g-dev
The following packages will be upgraded:
  ssh-askpass-gnome
1 packages upgraded, 1 newly installed, 216 to remove and 4 not upgraded.
Need to get 769kB of archives. After unpacking 884MB will be freed.
Do you want to continue? [Y/n/?]

---

### Post by Xian on 2005-10-22
I'd like to see what version of libc6 you have installed:
$ sudo apt-cache policy libc6

And please post the output of an update command:
$ sudo apt-get update

---

### Post by Cud on 2005-10-22
libc6:
  Installed: 2.3.2.ds1-20ubuntu13
  Candidate: 2.3.2.ds1-20ubuntu14
  Version table:
     2.3.2.ds1-20ubuntu14 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
 *** 2.3.2.ds1-20ubuntu13 0
        500 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
        100 /var/lib/dpkg/status
jesse@finally:~$ $ sudo apt-get update
bash: $: command not found
jesse@finally:~$ sudo apt-get update
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release.gpg [189B]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release.gpg [189B]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release.gpg [189B]
Get:4 [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security Release [16.9kB]
Get:5 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release.gpg [189B]
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary Release
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates Release [16.8kB]
Get:7 [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports Release [11.3kB]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/main Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-updates/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/universe Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/multiverse Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/multiverse Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary-backports/restricted Packages
Fetched 45.5kB in 1s (33.6kB/s)
Reading package lists.... done

thanks

---

### Post by Cud on 2005-10-22
Just in case this helps, heres what happened when I tried installing something completely unrelated to this whole problem. I don't understand too much about dependencies, but I#m sure this has something to do with the problem.
;) 
The following packages have unmet dependencies:
  flightgear: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be  installed
              Depends: plib1.8.4c2 but it is not installable
              Depends: simgear0 (>= 0.3.8-2) but it is not going to be installed
              Depends: fgfs-base (>= 0.9.8 ) but it is not going to be installed
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-20ubuntu13 is  to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-20ubuntu1 3 is to be installed
  libgcc1: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be in stalled
  libstdc++6: Depends: gcc-4.0-base (= 4.0.2-2) but it is not going to be instal led
              Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be  installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a s olution).

---

### Post by Xian on 2005-10-22
In some way you have to remove these packages:

flightgear
libc6-dev
libc6-i686
libgcc1

But the problem is all the cross dependencies.
Just keep trying them in some combination using apt-get.

Try the first two initially as they should be easier.

$ sudo apt-get remove flightgear

---

### Post by Cud on 2005-10-22
So I tried

jesse@finally:~$ [COLOR="Red"]sudo apt-get remove flightgear[/COLOR]
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  libc6-dev: Depends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-20ubuntu13 is to be installed
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-20ubuntu13 is to be installed
  libgcc1: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.2-2) but it is not going to be installed
              Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

Does this mean that flightgear is really removed?? I dont think so because the next package I tried I got..

jesse@finally:~$ [COLOR="Red"]sudo apt-get remove libc6-dev[/COLOR]
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these:
The following packages have unmet dependencies:
  [COLOR="Red"][COLOR="Red"]flightgear: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
              Depends: plib1.8.4c2 but it is not installable
              Depends: simgear0 (>= 0.3.8-2) but it is not going to be installed
              Depends: fgfs-base (>= 0.9.8) but it is not going to be installed[/COLOR][/COLOR]
  libc6-i686: PreDepends: libc6 (= 2.3.2.ds1-20ubuntu14) but 2.3.2.ds1-20ubuntu13 is to be installed
  libdirectfb-dev: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
  libexpat1-dev: Depends: libc6-dev but it is not going to be installed or
                          libc-dev
  libfreetype6-dev: Depends: libc6-dev but it is not going to be installed or
                             libc-dev
  libgcc1: Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  libglib2.0-dev: Depends: libc6-dev but it is not going to be installed or
                           libc-dev
  liblive.com-dev: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
  libncursesw5-dev: Depends: libc-dev
  libstdc++5-3.3-dev: Depends: libc6-dev (>= 2.3.2.ds1-16) but it is not going to be installed
  libstdc++6: Depends: gcc-4.0-base (= 4.0.2-2) but it is not going to be installed
              Depends: libc6 (>= 2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  libx11-dev: Depends: libc6-dev but it is not going to be installed or
                       libc-dev
  libxext-dev: Depends: libc6-dev but it is not going to be installed or
                        libc-dev
  libxft-dev: Depends: libc6-dev but it is not going to be installed or
                       libc-dev
  libxi-dev: Depends: libc6-dev but it is not going to be installed or
                      libc-dev
  libxrender-dev: Depends: libc6-dev but it is not going to be installed or
                           libc-dev
  locales: Depends: glibc-2.3.2.ds1-20ubuntu14
  lsb: Depends: libc6-dev but it is not going to be installed or
                libc-dev
  zlib1g-dev: Depends: libc6-dev but it is not going to be installed or
                       libc-dev
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


And there was flightgear AGAIN!!
rrrrrr....... 
Could you maybe do me the immense favor of explaining to me what one of these lines actually means? For me its not clear what depends on what where......
For Example:

 libdirectfb-dev: Depends: libc6-dev but it is not going to be installed or
                            libc-dev
What the heck is libc-dev doing in this sentence??:confused: 

This looks like a very complicated flow-chart problem in a 4th grade nightmare math book...

---

### Post by Xian on 2005-10-22
[QUOTE=Cud]Could you maybe do me the immense favor of explaining to me what one of these lines actually means? For me its not clear what depends on what where......[/QUOTE]
It is a series of cross-dependent packages that need to be removed but can't because they rely on other applications that will break as a result. The error messages are laying out for you exactly where the conflicts reside. Basically, you have packages installed that can't exist there because they are not system compatible, but can't be removed because they have tied themselves to other applications which are critical files.

The libc6 package is the single most important system file other than the kernel, and unfortunately that is what got involved in this problem. You can often downgrade this and fix things, but in your case there are other conflicts which are still unresolved.

---

### Post by Cud on 2005-10-28
VICTORY 
HAHAHAHAHAHAHa!
Used good old dselect to remove the offensive broken packages!

Thanks for all the help

---

