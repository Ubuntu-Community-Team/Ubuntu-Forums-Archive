---
title: "lubuntu 14.04LTS...brand new install, removing &quot;transmission&quot; client breaks OS!!!"
date: 2015-08-19
forum: General Help
---

### Post by wallymann on 2015-08-19
brand new install (after +5 years using ubuntu, wanted to try something more lightweight).

after a successful install and using the OS, i'm going thru de-installing various apps that i have no reason or desire to use....turns out when removing the Transmission torrent client breaks the OS in some fashion, and it no longer loads the GUI.  picture attached of where the boot stops.

i snapped an image of my lubuntu partition before removing Transmission.  i verified multiple times that removal of this 1 application breaks the OS every time without fail.

thankfully im able to continue on with trying lubuntu.  

i'm curious how the heck removal of a simple client like this would break the entire OS!!!  would appreciate any ideas for how to "fix" the OS after removing transmission.

[IMG]https://scontent-ord1-1.xx.fbcdn.net/hphotos-xpt1/v/t1.0-9/11891056_10206595459877091_3421802705017608403_n.jpg?oh=27124c66d7078482929476f0c6806c67&oe=56824009[/IMG]

---

### Post by howefield on 2015-08-19
You decided to remove lubuntu-desktop as well as transmission.

---

### Post by wallymann on 2015-08-19
that's insane... why would the entire lubuntu-desktop be "bound" to transmission?!

fwiw...when doing the de-install thru the lubuntu software center, you dont get get any visual feedback of that dependency.

---

### Post by howefield on 2015-08-19
I take it back.. perhaps.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

I tried removing transmission with terminal, synaptic and software centre - none of which resulted in a ruined desktop.

---

### Post by Bashing-om on 2015-08-19
wallymann; Uh Humm ...

If I may suggest:
It is a whole lot easier (and saver) to build up rather than tear down. Might consider a core install of 'buntu and ONLY install exactly what you want.

[INDENT][INDENT]it's 'buntu
[INDENT][INDENT][INDENT]you can have it your way
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by wallymann on 2015-08-19
interesting.  i ran that apt command and the response was:

```
[FONT=courier new]lubuntu-desktop can not be marked as it s not installed.
```****[/FONT]> **howefield said:**
> I take it back.. perhaps.

[https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop](https://help.ubuntu.com/community/Lubuntu/Documentation/RemoveLubuntuDesktop)

I tried removing transmission with terminal, synaptic and software centre - none of which resulted in a ruined desktop.

---

### Post by monkeybrain20122 on 2015-08-19
Isn't lubuntu-desktop just a meta package? Removing it shouldn't literally break your desktop. But then I don't use lubuntu.. always find it kind of strange. If I want something lightweight and have at least 1 G of ram I would go xubuntu.

---

### Post by wallymann on 2015-08-19
yes, that appears to be the case.  the suggestion that removal of lubuntu-desktop would cause this issue is incorrect.

> **monkeybrain20122 said:**
> Isn't lubuntu-desktop just a meta package? Removing it shouldn't literally break your desktop. But then I don't use lubuntu.. always find it kind of strange. If I want something lightweight and have at least 1 G of ram I would go xubuntu.

---

### Post by sandyd on 2015-08-19
Hi, can you post the output of
```

sudo apt-get -s remove transmission transmission-*

```

---

### Post by wallymann on 2015-08-20
here ya go!

just thinking off the top of my head, maybe there's some difference in the way the package handlers are working?  i'd been using the Lubuntu Software Center, not the synaptic UI nor apt command-line.

```
[FONT=courier new]user@lubuntu:~$ sudo apt-get -s remove transmission transmission-*
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'transmission-dbg' for regex 'transmission-*'
Note, selecting 'transmission-qt' for regex 'transmission-*'
Note, selecting 'python-transmissionrpc-doc' for regex 'transmission-*'
Note, selecting 'transmission-remote-gtk' for regex 'transmission-*'
Note, selecting 'libtransmission-client-perl' for regex 'transmission-*'
Note, selecting 'python3-transmissionrpc' for regex 'transmission-*'
Note, selecting 'transmission-daemon' for regex 'transmission-*'
Note, selecting 'transmission-cli' for regex 'transmission-*'
Note, selecting 'python-transmissionrpc' for regex 'transmission-*'
Note, selecting 'transmission' for regex 'transmission-*'
Note, selecting 'transmission-remote-cli' for regex 'transmission-*'
Note, selecting 'transmission-gtk' for regex 'transmission-*'
Note, selecting 'transmission-common' for regex 'transmission-*'
Package 'libtransmission-client-perl' is not installed, so not removed
Package 'python-transmissionrpc' is not installed, so not removed
Package 'python-transmissionrpc-doc' is not installed, so not removed
Package 'python3-transmissionrpc' is not installed, so not removed
Package 'transmission-remote-cli' is not installed, so not removed
Package 'transmission-remote-gtk' is not installed, so not removed
Package 'transmission-cli' is not installed, so not removed
Package 'transmission-daemon' is not installed, so not removed
Package 'transmission-dbg' is not installed, so not removed
Package 'transmission-qt' is not installed, so not removed
The following packages were automatically installed and are no longer required:
  libevent-2.0-5 libnatpmp1
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  transmission transmission-common transmission-gtk
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
Remv transmission [2.82-1.1ubuntu3.1]
Remv transmission-gtk [2.82-1.1ubuntu3.1]
Remv transmission-common [2.82-1.1ubuntu3.1][/FONT]
```[FONT=courier new]

[/FONT]> **sandyd said:**
> Hi, can you post the output of
```

sudo apt-get -s remove transmission transmission-*

```

---

### Post by sandyd on 2015-08-20
I don't see that apt is removing anything other than transmission, transmission-common, transmission-gtk

Can I also have the output of
```

apt-cache show lubuntu-desktop
dpkg -l | grep lubuntu-desktop
```

---

### Post by wallymann on 2015-08-20
here ya go!

```
user@lubuntu:~$ apt-cache show lubuntu-desktop
Package: lubuntu-desktop
Priority: optional
Section: universe/metapackages
Installed-Size: 31
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Original-Maintainer: Lubuntu Team <lubuntu-desktop@lists.launchpad.net>
Architecture: amd64
Source: lubuntu-meta
Version: 0.55
Depends: abiword, apport-gtk, apturl, audacious, audacious-plugins, blueman, cups-driver-gutenprint, desktop-file-utils, dmz-cursor-theme, evince, ffmpegthumbnailer, file-roller, firefox, fonts-droid, fonts-liberation, fonts-nanum, galculator, gdebi, gecko-mediaplayer, gnome-accessibility-themes, gnome-disk-utility, gnome-icon-theme-symbolic, gnome-keyring, gnome-mplayer, gnome-system-tools, gnome-time-admin, gnumeric, gpicview, gucharmap, guvcview, gvfs-backends, gvfs-fuse, hardinfo, ibus, indicator-application-gtk2, language-selector-gnome, leafpad, libfm-modules, libgtk2-perl, libmtp-runtime, light-locker, light-locker-settings, lubuntu-core, lubuntu-default-session, lubuntu-software-center, lxappearance, lxappearance-obconf, lxinput, lxlauncher, lxpanel-indicator-applet-plugin, lxrandr, lxsession-default-apps, lxsession-logout, lxshortcut, lxtask, lxterminal, mobile-broadband-provider-info, modemmanager, mtpaint, network-manager-gnome, ntp, obconf, pidgin, pm-utils, python-gudev, scrot, simple-scan, software-properties-gtk, sylpheed, sylpheed-doc, sylpheed-i18n, sylpheed-plugins, synaptic, system-config-printer-gnome, transmission, ubuntu-release-upgrader-gtk, update-notifier, usb-creator-gtk, usb-modeswitch, whoopsie, wvdial, x11-utils, xdg-user-dirs, xdg-user-dirs-gtk, xfburn, xfce4-notifyd, xfce4-power-manager, xpad, xterm, xul-ext-ubufox, xz-utils
Filename: pool/universe/l/lubuntu-meta/lubuntu-desktop_0.55_amd64.deb
Size: 2182
MD5sum: 6d91fd44a5997dfb6f30d5f0e30221c3
SHA1: 6b95f53c93696d742eb2ae99cc51f3ab03d2cc9b
SHA256: 4f1ea8526024d5930a99f6e1e06c090f2d09e2970b3a24ffecc60cc09fb6a8be
Description-en: Lubuntu Desktop environment
 This metapackage package depends on all components of Lubuntu Desktop system.
 .
 It is also used to help ensure proper upgrades, but it can be safely removed
 if you want to remove some applications installed by default.
Description-md5: 4b566a27d2f6acd63de01fba297a527d
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 3y
Task: lubuntu-desktop

user@lubuntu:~$ dpkg -l | grep lubuntu-desktop
user@lubuntu:~$ 

```

> **sandyd said:**
> I don't see that apt is removing anything other than transmission, transmission-common, transmission-gtk

Can I also have the output of
```

apt-cache show lubuntu-desktop
dpkg -l | grep lubuntu-desktop
```

---

### Post by matt_symes on 2015-08-20
Hi

Can you post the log file

```
/var/log/dpkg.log
```

Uninstalling Transmission removes Lubuntu Desktop ? That seems insane :)

Maybe the logs will shed more light on exactly what is going on.

KInd regards

---

### Post by vasa1 on 2015-08-20
> **matt_symes said:**
> ...
Uninstalling Transmission removes Lubuntu Desktop ? That seems insane :)
...
There are quite a few apps whose removal also triggers the removal of *lubuntu-desktop*. Lubuntu works just fine without lubuntu-desktop which, as has already been pointed out, is just a metapackage.

The only time lubuntu-desktop (and whatever it pulls in) should be reinstalled is if one wants to upgrade to a new release. And then repeat the removal of software one doesn't need (including lubuntu-desktop).

[http://askubuntu.com/questions/233662/how-do-i-remove-ace-of-penguins-without-removing-lubuntu-desktop](http://askubuntu.com/questions/233662/how-do-i-remove-ace-of-penguins-without-removing-lubuntu-desktop)
[http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html](http://www.mail-archive.com/lubuntu-desktop@lists.launchpad.net/msg03490.html)
[http://askubuntu.com/questions/21497/what-are-the-downsides-of-removing-ubuntu-desktop-metapackage](http://askubuntu.com/questions/21497/what-are-the-downsides-of-removing-ubuntu-desktop-metapackage)

BTW, the same situation prevails in other desktop environments as well. Not just Lubuntu.

---

### Post by wallymann on 2015-08-20
relevant contents of  /var/log/dpkg.log after uninstalling transmission using Lubuntu Software Center, which results in the OS no longer booting to the UI.  

i can also post a video showing a successful boot, uninstall of transmission, then the failed re-boot.

why would it remove xserver-xorg-lts-vivid:amd64 ?!  that seems ill-advised...

```

2015-08-20 11:59:38 startup packages remove
2015-08-20 11:59:38 status installed transmission:all 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 remove transmission:all 2.82-1.1ubuntu3.1 <none>
2015-08-20 11:59:44 status half-configured transmission:all 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 status half-installed transmission:all 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 status config-files transmission:all 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 status config-files transmission:all 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 status config-files transmission:all 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 status not-installed transmission:all <none>
2015-08-20 11:59:44 status installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 remove transmission-gtk:amd64 2.82-1.1ubuntu3.1 <none>
2015-08-20 11:59:44 status half-configured transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 status half-installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:44 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-20 11:59:44 status triggers-pending gconf2:amd64 3.2.6-0ubuntu2
2015-08-20 11:59:44 status half-installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:45 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 11:59:45 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-20 11:59:45 status half-installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:45 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-20 11:59:45 status config-files transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:45 status config-files transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:45 status installed xserver-xorg-lts-vivid:amd64 1:7.7+7ubuntu3~trusty1
[COLOR=#ff0000]2015-08-20 11:59:45 remove xserver-xorg-lts-vivid:amd64 1:7.7+7ubuntu3~trusty1 <none>[/COLOR]
2015-08-20 11:59:45 status half-configured xserver-xorg-lts-vivid:amd64 1:7.7+7ubuntu3~trusty1
2015-08-20 11:59:45 status half-installed xserver-xorg-lts-vivid:amd64 1:7.7+7ubuntu3~trusty1
2015-08-20 11:59:45 status config-files xserver-xorg-lts-vivid:amd64 1:7.7+7ubuntu3~trusty1
2015-08-20 11:59:45 status config-files xserver-xorg-lts-vivid:amd64 1:7.7+7ubuntu3~trusty1
2015-08-20 11:59:45 trigproc mime-support:all 3.54ubuntu1.1 <none>
2015-08-20 11:59:45 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-20 11:59:46 status installed mime-support:all 3.54ubuntu1.1
2015-08-20 11:59:46 trigproc gconf2:amd64 3.2.6-0ubuntu2 <none>
2015-08-20 11:59:46 status half-configured gconf2:amd64 3.2.6-0ubuntu2
2015-08-20 11:59:46 status installed gconf2:amd64 3.2.6-0ubuntu2
2015-08-20 11:59:46 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-08-20 11:59:46 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 11:59:47 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 11:59:47 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-08-20 11:59:47 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-20 11:59:47 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-20 11:59:48 startup archives unpack
2015-08-20 11:59:48 install libgbm1:amd64 10.1.3-0ubuntu0.4 10.1.3-0ubuntu0.4
2015-08-20 11:59:48 status half-installed libgbm1:amd64 10.1.3-0ubuntu0.4
2015-08-20 11:59:48 status unpacked libgbm1:amd64 10.1.3-0ubuntu0.4
2015-08-20 11:59:48 status unpacked libgbm1:amd64 10.1.3-0ubuntu0.4
2015-08-20 11:59:48 install libqt5core5a:amd64 <none> 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:48 status half-installed libqt5core5a:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 status unpacked libqt5core5a:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 status unpacked libqt5core5a:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 install libqt5dbus5:amd64 <none> 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 status half-installed libqt5dbus5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 status unpacked libqt5dbus5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 status unpacked libqt5dbus5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 install libqt5network5:amd64 <none> 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:49 status half-installed libqt5network5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:50 status unpacked libqt5network5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:50 status unpacked libqt5network5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:50 install libxcb-xkb1:amd64 <none> 1.10-2ubuntu1
2015-08-20 11:59:50 status half-installed libxcb-xkb1:amd64 1.10-2ubuntu1
2015-08-20 11:59:50 status unpacked libxcb-xkb1:amd64 1.10-2ubuntu1
2015-08-20 11:59:50 status unpacked libxcb-xkb1:amd64 1.10-2ubuntu1
2015-08-20 11:59:50 install libxkbcommon-x11-0:amd64 <none> 0.4.1-0ubuntu1
2015-08-20 11:59:50 status half-installed libxkbcommon-x11-0:amd64 0.4.1-0ubuntu1
2015-08-20 11:59:51 status unpacked libxkbcommon-x11-0:amd64 0.4.1-0ubuntu1
2015-08-20 11:59:51 status unpacked libxkbcommon-x11-0:amd64 0.4.1-0ubuntu1
2015-08-20 11:59:51 install libxcb-icccm4:amd64 <none> 0.4.1-1ubuntu1
2015-08-20 11:59:51 status half-installed libxcb-icccm4:amd64 0.4.1-1ubuntu1
2015-08-20 11:59:51 status unpacked libxcb-icccm4:amd64 0.4.1-1ubuntu1
2015-08-20 11:59:51 status unpacked libxcb-icccm4:amd64 0.4.1-1ubuntu1
2015-08-20 11:59:51 install libxcb-image0:amd64 <none> 0.3.9-1ubuntu2
2015-08-20 11:59:51 status half-installed libxcb-image0:amd64 0.3.9-1ubuntu2
2015-08-20 11:59:51 status unpacked libxcb-image0:amd64 0.3.9-1ubuntu2
2015-08-20 11:59:51 status unpacked libxcb-image0:amd64 0.3.9-1ubuntu2
2015-08-20 11:59:52 install libxcb-render-util0:amd64 <none> 0.3.8-1.1ubuntu1
2015-08-20 11:59:52 status half-installed libxcb-render-util0:amd64 0.3.8-1.1ubuntu1
2015-08-20 11:59:52 status unpacked libxcb-render-util0:amd64 0.3.8-1.1ubuntu1
2015-08-20 11:59:52 status unpacked libxcb-render-util0:amd64 0.3.8-1.1ubuntu1
2015-08-20 11:59:52 install transmission-cli:amd64 <none> 2.82-1.1ubuntu3.1
2015-08-20 11:59:52 status half-installed transmission-cli:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:52 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 11:59:52 status unpacked transmission-cli:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:52 status unpacked transmission-cli:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:53 trigproc man-db:amd64 2.6.7.1-1ubuntu1 2.6.7.1-1ubuntu1
2015-08-20 11:59:53 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 11:59:53 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 11:59:53 startup packages configure
2015-08-20 11:59:53 configure libgbm1:amd64 10.1.3-0ubuntu0.4 <none>
2015-08-20 11:59:53 status unpacked libgbm1:amd64 10.1.3-0ubuntu0.4
2015-08-20 11:59:53 status half-configured libgbm1:amd64 10.1.3-0ubuntu0.4
2015-08-20 11:59:53 status installed libgbm1:amd64 10.1.3-0ubuntu0.4
2015-08-20 11:59:54 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-08-20 11:59:54 configure libqt5core5a:amd64 5.2.1+dfsg-1ubuntu14.3 <none>
2015-08-20 11:59:54 status unpacked libqt5core5a:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 status half-configured libqt5core5a:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 status installed libqt5core5a:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 configure libqt5dbus5:amd64 5.2.1+dfsg-1ubuntu14.3 <none>
2015-08-20 11:59:54 status unpacked libqt5dbus5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 status half-configured libqt5dbus5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 status installed libqt5dbus5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 configure libqt5network5:amd64 5.2.1+dfsg-1ubuntu14.3 <none>
2015-08-20 11:59:54 status unpacked libqt5network5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 status half-configured libqt5network5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 status installed libqt5network5:amd64 5.2.1+dfsg-1ubuntu14.3
2015-08-20 11:59:54 configure libxcb-xkb1:amd64 1.10-2ubuntu1 <none>
2015-08-20 11:59:54 status unpacked libxcb-xkb1:amd64 1.10-2ubuntu1
2015-08-20 11:59:54 status half-configured libxcb-xkb1:amd64 1.10-2ubuntu1
2015-08-20 11:59:54 status installed libxcb-xkb1:amd64 1.10-2ubuntu1
2015-08-20 11:59:55 configure libxkbcommon-x11-0:amd64 0.4.1-0ubuntu1 <none>
2015-08-20 11:59:55 status unpacked libxkbcommon-x11-0:amd64 0.4.1-0ubuntu1
2015-08-20 11:59:55 status half-configured libxkbcommon-x11-0:amd64 0.4.1-0ubuntu1
2015-08-20 11:59:55 status installed libxkbcommon-x11-0:amd64 0.4.1-0ubuntu1
2015-08-20 11:59:55 configure libxcb-icccm4:amd64 0.4.1-1ubuntu1 <none>
2015-08-20 11:59:55 status unpacked libxcb-icccm4:amd64 0.4.1-1ubuntu1
2015-08-20 11:59:55 status half-configured libxcb-icccm4:amd64 0.4.1-1ubuntu1
2015-08-20 11:59:55 status installed libxcb-icccm4:amd64 0.4.1-1ubuntu1
2015-08-20 11:59:55 configure libxcb-image0:amd64 0.3.9-1ubuntu2 <none>
2015-08-20 11:59:55 status unpacked libxcb-image0:amd64 0.3.9-1ubuntu2
2015-08-20 11:59:55 status half-configured libxcb-image0:amd64 0.3.9-1ubuntu2
2015-08-20 11:59:55 status installed libxcb-image0:amd64 0.3.9-1ubuntu2
2015-08-20 11:59:55 configure libxcb-render-util0:amd64 0.3.8-1.1ubuntu1 <none>
2015-08-20 11:59:55 status unpacked libxcb-render-util0:amd64 0.3.8-1.1ubuntu1
2015-08-20 11:59:55 status half-configured libxcb-render-util0:amd64 0.3.8-1.1ubuntu1
2015-08-20 11:59:55 status installed libxcb-render-util0:amd64 0.3.8-1.1ubuntu1
2015-08-20 11:59:56 configure transmission-cli:amd64 2.82-1.1ubuntu3.1 <none>
2015-08-20 11:59:56 status unpacked transmission-cli:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:56 status half-configured transmission-cli:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:56 status installed transmission-cli:amd64 2.82-1.1ubuntu3.1
2015-08-20 11:59:56 trigproc libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-08-20 11:59:56 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-08-20 11:59:56 status installed libc-bin:amd64 2.19-0ubuntu6.6

```

---

### Post by vasa1 on 2015-08-20
BTW, [http://ubuntuforums.org/showthread.php?t=2220833](http://ubuntuforums.org/showthread.php?t=2220833)

---

### Post by wallymann on 2015-08-20
yeah, saw that.  similar but different.  thx.

> **vasa1 said:**
> BTW, [http://ubuntuforums.org/showthread.php?t=2220833](http://ubuntuforums.org/showthread.php?t=2220833)

---

### Post by matt_symes on 2015-08-20
Hi

> **vasa1 said:**
> There are quite a few apps whose removal also triggers the removal of *lubuntu-desktop*. Lubuntu works just fine without lubuntu-desktop which, as has already been pointed out, is just a metapackage.

Let me rephrase my comment as i don't think you understood what i was trying to confer.

Uninstalling transmission removes the desktop from Lubuntu ? That seems insane :)

I wasn't talking about the metapackage :)

EDIT:

I going to take a good look at the log file but it does look like it's removing xorg*.

Kind regards

---

### Post by vasa1 on 2015-08-20
> **matt_symes said:**
> Hi



Let me rephrase my comment as i don't think you understood what i was trying to confer.

Uninstalling transmission removes the desktop from Lubuntu ? That seems insane :)

I wasn't talking about the metapackage :)

...
Got it now. Thanks for clarifying :)

---

### Post by matt_symes on 2015-08-20
Hi

Isn't xserver-xorg-lts-vivid itself just a meta package ? It did not seem to be removing much else.

Have you tried to start lightdm when you boot to the command prompt ?

Kind regards

---

### Post by wallymann on 2015-08-20
so the problem is the Lubuntu Software Center.

i removed transmission using apt commands and it boots fine as follows, including the contents of dpkg.log:

first, remove only transmission > sudo apt-get remove transmission

```

2015-08-20 14:30:24 startup packages remove
2015-08-20 14:30:24 status installed dkms:all 2.2.0.3-1.1ubuntu5.14.04.1
2015-08-20 14:30:26 remove dkms:all 2.2.0.3-1.1ubuntu5.14.04.1 <none>
2015-08-20 14:30:26 status half-configured dkms:all 2.2.0.3-1.1ubuntu5.14.04.1
2015-08-20 14:30:26 status half-installed dkms:all 2.2.0.3-1.1ubuntu5.14.04.1
2015-08-20 14:30:27 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 14:30:27 status config-files dkms:all 2.2.0.3-1.1ubuntu5.14.04.1
2015-08-20 14:30:27 status config-files dkms:all 2.2.0.3-1.1ubuntu5.14.04.1
2015-08-20 14:30:27 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-08-20 14:30:27 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 14:30:29 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 17:36:52 startup packages remove
2015-08-20 17:36:52 status installed transmission:all 2.82-1.1ubuntu3.1
2015-08-20 17:36:55 remove transmission:all 2.82-1.1ubuntu3.1 <none>
2015-08-20 17:36:55 status half-configured transmission:all 2.82-1.1ubuntu3.1
2015-08-20 17:36:55 status half-installed transmission:all 2.82-1.1ubuntu3.1
2015-08-20 17:36:55 status config-files transmission:all 2.82-1.1ubuntu3.1
2015-08-20 17:36:55 status config-files transmission:all 2.82-1.1ubuntu3.1
2015-08-20 17:36:56 status config-files transmission:all 2.82-1.1ubuntu3.1
2015-08-20 17:36:56 status not-installed transmission:all <none>

```

reboot successful!

now remove the related dependencies > sudo apt-get autoremove

```

2015-08-20 17:50:40 startup packages remove
2015-08-20 17:50:40 status installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 17:50:42 remove transmission-gtk:amd64 2.82-1.1ubuntu3.1 <none>
2015-08-20 17:50:42 status half-configured transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 17:50:42 status half-installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 17:50:42 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-20 17:50:43 status triggers-pending gconf2:amd64 3.2.6-0ubuntu2
2015-08-20 17:50:43 status half-installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 17:50:43 status triggers-pending man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 17:50:43 status triggers-pending desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-20 17:50:43 status half-installed transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 17:50:43 status triggers-pending mime-support:all 3.54ubuntu1.1
2015-08-20 17:50:43 status config-files transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 17:50:43 status config-files transmission-gtk:amd64 2.82-1.1ubuntu3.1
2015-08-20 17:50:43 status installed libevent-2.0-5:amd64 2.0.21-stable-1ubuntu1.14.04.1
2015-08-20 17:50:43 remove libevent-2.0-5:amd64 2.0.21-stable-1ubuntu1.14.04.1 <none>
2015-08-20 17:50:43 status half-configured libevent-2.0-5:amd64 2.0.21-stable-1ubuntu1.14.04.1
2015-08-20 17:50:43 status half-installed libevent-2.0-5:amd64 2.0.21-stable-1ubuntu1.14.04.1
2015-08-20 17:50:43 status triggers-pending libc-bin:amd64 2.19-0ubuntu6.6
2015-08-20 17:50:43 status config-files libevent-2.0-5:amd64 2.0.21-stable-1ubuntu1.14.04.1
2015-08-20 17:50:44 status config-files libevent-2.0-5:amd64 2.0.21-stable-1ubuntu1.14.04.1
2015-08-20 17:50:44 status installed libnatpmp1:amd64 20110808-3ubuntu2
2015-08-20 17:50:44 remove libnatpmp1:amd64 20110808-3ubuntu2 <none>
2015-08-20 17:50:44 status half-configured libnatpmp1:amd64 20110808-3ubuntu2
2015-08-20 17:50:44 status half-installed libnatpmp1:amd64 20110808-3ubuntu2
2015-08-20 17:50:44 status config-files libnatpmp1:amd64 20110808-3ubuntu2
2015-08-20 17:50:44 status config-files libnatpmp1:amd64 20110808-3ubuntu2
2015-08-20 17:50:44 status installed transmission-common:all 2.82-1.1ubuntu3.1
2015-08-20 17:50:44 remove transmission-common:all 2.82-1.1ubuntu3.1 <none>
2015-08-20 17:50:44 status half-configured transmission-common:all 2.82-1.1ubuntu3.1
2015-08-20 17:50:44 status half-installed transmission-common:all 2.82-1.1ubuntu3.1
2015-08-20 17:50:44 status triggers-pending hicolor-icon-theme:all 0.13-1
2015-08-20 17:50:44 status half-installed transmission-common:all 2.82-1.1ubuntu3.1
2015-08-20 17:50:44 status config-files transmission-common:all 2.82-1.1ubuntu3.1
2015-08-20 17:50:45 status config-files transmission-common:all 2.82-1.1ubuntu3.1
2015-08-20 17:50:45 status config-files transmission-common:all 2.82-1.1ubuntu3.1
2015-08-20 17:50:45 status not-installed transmission-common:all <none>
2015-08-20 17:50:45 trigproc mime-support:all 3.54ubuntu1.1 <none>
2015-08-20 17:50:45 status half-configured mime-support:all 3.54ubuntu1.1
2015-08-20 17:50:45 status installed mime-support:all 3.54ubuntu1.1
2015-08-20 17:50:45 trigproc gconf2:amd64 3.2.6-0ubuntu2 <none>
2015-08-20 17:50:45 status half-configured gconf2:amd64 3.2.6-0ubuntu2
2015-08-20 17:50:45 status installed gconf2:amd64 3.2.6-0ubuntu2
2015-08-20 17:50:45 trigproc man-db:amd64 2.6.7.1-1ubuntu1 <none>
2015-08-20 17:50:45 status half-configured man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 17:50:47 status installed man-db:amd64 2.6.7.1-1ubuntu1
2015-08-20 17:50:47 trigproc desktop-file-utils:amd64 0.22-1ubuntu1 <none>
2015-08-20 17:50:47 status half-configured desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-20 17:50:47 status installed desktop-file-utils:amd64 0.22-1ubuntu1
2015-08-20 17:50:47 trigproc libc-bin:amd64 2.19-0ubuntu6.6 <none>
2015-08-20 17:50:47 status half-configured libc-bin:amd64 2.19-0ubuntu6.6
2015-08-20 17:50:47 status installed libc-bin:amd64 2.19-0ubuntu6.6
2015-08-20 17:50:47 trigproc hicolor-icon-theme:all 0.13-1 <none>
2015-08-20 17:50:47 status half-configured hicolor-icon-theme:all 0.13-1
2015-08-20 17:50:49 status installed hicolor-icon-theme:all 0.13-1

```

reboot successful!

there are differences in dpkg.log between what was removed previously, when used the Lubuntu Software Center...WTF?!

---

### Post by matt_symes on 2015-08-20
Hi

Thanks for posting back with your analysis.

I never use any of the software centres personally and, after your thread, I'm pretty happy that I don't. :p

I'm glad you know what the problem is. If you can find out exactly what is going on then maybe raise a bug report ?

Kind regards

---

### Post by wallymann on 2015-08-20
heh.  this is pretty much a smoking-gun.  

perhaps someone with more technical know-how could investigate under-the-covers as to why the Lubuntu app does something differently from what's desired/expected when uninstalling transmission.  i'm at the limits of my linux knowledge.  :-/

> **matt_symes said:**
> Hi

Thanks for posting back with your analysis.

I never use any of the software centres personally and, after your thread, I'm pretty happy that I don't. :p

I'm glad you know what the problem is. If you can find out exactly what is going on then maybe raise a bug report ?

Kind regards

---

