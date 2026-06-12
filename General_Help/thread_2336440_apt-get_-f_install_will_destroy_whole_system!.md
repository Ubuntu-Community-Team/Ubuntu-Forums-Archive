---
title: "apt-get -f install will destroy whole system!"
date: 2016-09-08
forum: General Help
---

### Post by k-nirvana12 on 2016-09-08
Hello. I want to install Skype on Ubuntu 16.04 I downloaded it from its website and run with "sudo dpkg -i" but then it gave errors about dependency and now it's saying that I have broken packages. I can neither install nor remove anything. It wants me to run apt-get -f install. But this command will destroy so important packages:
```
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  adium-theme-ubuntu apturl apturl-common ca-certificates-mono cli-common
  gir1.2-keybinder-3.0 gnome-software-common gnome-video-effects
  guile-2.0-libs gyp javascript-common lib32gcc1 lib32stdc++6
  liba11y-profile-manager-0.1-0 libasound2:i386 libasyncns0:i386
  libavahi-common-data:i386 libavahi-common3:i386 libc6-i386 libcap2:i386
  libcdparanoia0:i386 libcomerr2:i386 libdbus2.0-cil libevent-2.0-5
  libflac8:i386 libfontconfig1:i386 libfreetype6:i386 libgc1c2 libgconf2.0-cil
  libgcrypt20:i386 libgdiplus libgif7 libglib2.0-cil libgmp10:i386
  libgnome-keyring1.0-cil libgpg-error0:i386 libgssapi-krb5-2:i386
  libhogweed4:i386 libice6:i386 libicu55:i386 libidn11:i386
  libjack-jackd2-0:i386 libjbig0:i386 libjpeg-turbo8:i386 libjpeg8:i386
  libjs-inherits libjs-jquery libjs-node-uuid libjs-underscore libjson-c2:i386
  libk5crypto3:i386 libkeybinder-3.0-0 libkeyutils1:i386 libkrb5-3:i386
  libkrb5support0:i386 liblcms2-2:i386 liblzma5:i386 libminiupnpc10
  libmng2:i386 libmono-accessibility4.0-cil libmono-addins0.2-cil
  libmono-cairo4.0-cil libmono-corlib4.5-cil libmono-data-tds4.0-cil
  libmono-i18n-west4.0-cil libmono-i18n4.0-cil libmono-ldap4.0-cil
  libmono-posix4.0-cil libmono-security4.0-cil libmono-sharpzip4.84-cil
  libmono-sqlite4.0-cil libmono-system-componentmodel-dataannotations4.0-cil
  libmono-system-configuration4.0-cil libmono-system-core4.0-cil
  libmono-system-data4.0-cil libmono-system-design4.0-cil
  libmono-system-drawing4.0-cil libmono-system-enterpriseservices4.0-cil
  libmono-system-ldap4.0-cil libmono-system-numerics4.0-cil
  libmono-system-runtime-serialization-formatters-soap4.0-cil
  libmono-system-runtime-serialization4.0-cil libmono-system-security4.0-cil
  libmono-system-servicemodel-internals0.0-cil
  libmono-system-transactions4.0-cil
  libmono-system-web-applicationservices4.0-cil
  libmono-system-web-services4.0-cil libmono-system-web4.0-cil
  libmono-system-windows-forms4.0-cil libmono-system-xml-linq4.0-cil
  libmono-system-xml4.0-cil libmono-system4.0-cil libmono-webbrowser4.0-cil
  libmysqlclient20:i386 libnatpmp1 libnettle6:i386 libogg0:i386 libopus0:i386
  liborc-0.4-0:i386 libpcre3:i386 libpng12-0:i386 libpq5 libqqwing2v5
  libqt4-opengl libreoffice-gtk libsamplerate0:i386 libselinux1:i386
  libsndfile1:i386 libspeexdsp1:i386 libsqlite3-0:i386 libssl-dev libssl-doc
  libtasn1-6:i386 libtheora0:i386 libtiff5:i386 libuv1 libuv1-dev
  libvisual-0.4-0:i386 libvorbis0a:i386 libvorbisenc2:i386
  libwhoopsie-preferences0 libwhoopsie0 libwnck-common libwrap0:i386
  libxi6:i386 libxml2:i386 libxrender1:i386 libxslt1.1:i386 libxss1:i386
  libxv1:i386 mono-4.0-gac mono-gac mono-runtime mono-runtime-common
  mono-runtime-sgen mysql-common node-abbrev node-ansi node-ansi-color-table
  node-archy node-async node-block-stream node-combined-stream node-cookie-jar
  node-delayed-stream node-forever-agent node-form-data node-fstream
  node-fstream-ignore node-github-url-from-git node-glob node-graceful-fs
  node-gyp node-inherits node-ini node-json-stringify-safe node-lockfile
  node-lru-cache node-mime node-minimatch node-mkdirp node-mute-stream
  node-node-uuid node-nopt node-normalize-package-data node-npmlog node-once
  node-osenv node-qs node-read node-read-package-json node-request node-retry
  node-rimraf node-semver node-sha node-sigmund node-slide node-tar
  node-tunnel-agent node-underscore node-which nodejs nodejs-dev npm
  python-pkg-resources transmission-common ubuntu-wallpapers
  ubuntu-wallpapers-xenial whoopsie-preferences
Use 'sudo apt autoremove' to remove them.
The following additional packages will be installed:
  libxss1:i386 libxv1:i386
The following packages will be REMOVED:
  a11y-profile-manager-indicator activity-log-manager aisleriot appmenu-qt5
  appstream atom bamfdaemon bluez-cups brackets cheese compiz compiz-gnome
  deja-dup evince file-roller fwupd gdb gnome-calendar gnome-font-viewer
  gnome-mahjongg gnome-screenshot gnome-software gnome-sudoku gnome-system-log
  gnome-system-monitor gstreamer1.0-alsa gstreamer1.0-plugins-base-apps
  gstreamer1.0-plugins-ugly gstreamer1.0-tools gtk2-engines-murrine gvfs-bin
  gvfs-fuse indicator-appmenu indicator-messages indicator-printers kazam
  libappstream-glib8 libappstream3 libbabeltrace-ctf1 libdbus-glib2.0-cil
  libdfu1 libedataserverui-1.2-1 libfwupd1 libgkeyfile1.0-cil libgtk2.0-cil
  libgtkmm-3.0-1v5 libgtkspell3-3-0 libmetacity-private3a libnm-glib-vpn1
  libnotify-bin libnotify0.4-cil libproxy1-plugin-gsettings libqtwebkit4
  libreoffice-gnome libunity-misc4 libwnck22 light-themes nautilus-share
  network-manager-pptp-gnome notify-osd opera-stable pepperflashplugin-nonfree
  plymouth-label plymouth-theme-ubuntu-logo seahorse skype:i386 thermald
  transmission-gtk ubuntu-artwork ubuntu-desktop ubuntu-release-upgrader-gtk
  ubuntu-software unity unity-editor unity-lens-applications unity-lens-files
  unity-lens-video unity-scope-home unity-tweak-tool update-manager
  update-notifier vino whoopsie xdg-user-dirs-gtk
The following NEW packages will be installed:
  libxss1:i386 libxv1:i386
0 upgraded, 2 newly installed, 84 to remove and 5 not upgraded.
1 not fully installed or removed.
Need to get 18.7 kB of archives.
After this operation, 7401 MB disk space will be freed.
Do you want to continue? [Y/n] 


```
What do I do?

---

### Post by #&amp;thj^% on 2016-09-08
To install skype on Xenial
[http://askubuntu.com/questions/775087/how-to-install-skype-in-ubuntu-16-04](http://askubuntu.com/questions/775087/how-to-install-skype-in-ubuntu-16-04)
  

You can try this to remove Skype...(Make sure you have all you want backed-up) 
```
sudo apt-get remove skype skype-bin

```
```
rm -rf ~/.skype
```
And if this worked install skype the way in the link provided above.
Good Luck

---

### Post by k-nirvana12 on 2016-09-08
When I try to remove Skype
```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Package 'skype' is not installed, so not removed. Did you mean 'skype:i386'?
Package 'skype-bin:i386' is not installed, so not removed
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 skype:i386 : Depends: libqt4-dbus:i386 (>= 4:4.5.3) but it is not going to be installed
              Depends: libqt4-network:i386 (>= 4:4.8.0) but it is not going to be installed
              Depends: libqt4-xml:i386 (>= 4:4.5.3) but it is not going to be installed
              Depends: libqtcore4:i386 (>= 4:4.7.0~beta1) but it is not going to be installed
              Depends: libqtgui4:i386 (>= 4:4.8.0) but it is not going to be installed
              Depends: libqtwebkit4:i386 (>= 2.2~2011week36) but it is not going to be installed
              Depends: libxss1:i386 but it is not going to be installed
              Depends: libxv1:i386 but it is not going to be installed
              Depends: libssl1.0.0:i386 but it is not going to be installed
              Depends: libpulse0:i386 but it is not going to be installed
              Depends: libasound2-plugins:i386 but it is not going to be installed
              Recommends: sni-qt:i386 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).


```

---

### Post by #&amp;thj^% on 2016-09-08
Have you yet enabled the Partner Repo as suggested in the link...and maybe just maybe after updating the sources (sudo apt update) try the "apt-get -f install"
might produce better results.

---

### Post by k-nirvana12 on 2016-09-08
Okay, I got it successfully removed. APT is working now. But when I try the link you sent, I  get this;
```

sudo apt-get install skype
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 skype : Depends: skype-bin
E: Unable to correct problems, you have held broken packages.


```
and yeah, I add the repo.

---

### Post by #&amp;thj^% on 2016-09-08
Lets see how it wants to handle the broken packages now..
```
sudo apt-get -f install
```
And read carefully what it wants to remove..if anything.
EDIT you will have to Add i386 architecture

```
sudo dpkg --add-architecture i386

```
Update and install

```
sudo apt-get update && sudo apt-get install skype
```

---

### Post by k-nirvana12 on 2016-09-08
Ah thank you finally. I think what I needed to do is to 
```
sudo dpkg --add-architecture i386
```
it is working now

---

### Post by #&amp;thj^% on 2016-09-08
Hey Hey Good Job:KS
Now if you will mark this as solved to help other visitors.
Kind Regards

---

