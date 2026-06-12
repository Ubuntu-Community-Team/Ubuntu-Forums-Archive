---
title: "what is this mystery account that keeps prompting me at startup to fix?"
date: 2017-03-24
forum: General Help
---

### Post by juntjoo2 on 2017-03-24
[ATTACH=CONFIG]274299[/ATTACH]

when I follow instructions it just takes me to settings and I don't see anything in there that looks like something this would be pointing to.  Thanks

---

### Post by vasa1 on 2017-03-24
Please provide context. For example, people may not be familiar with which distro you're using. When you say "startup", providing a recursive list of your autostart folder may help.

---

### Post by juntjoo2 on 2017-03-24
Thanks

[ATTACH=CONFIG]274300[/ATTACH]

and the last two at the bottom are "xscreensaver" and "zeitgeist-datahub"

I'm using 16.0.4

---

### Post by vasa1 on 2017-03-24
It's often more convenient to provide information generated via the terminal.

In this case, **cd** to your **autostart** folder and then run```
ls -lR
```Copy the entire output, including the command till the final terminal prompt that returns once the command is complete and post that here within code tags. Thanks!

---

### Post by vasa1 on 2017-03-24
It's also useful to point out what additional software you've installed. For example, I see kdeconnect, korganizer, and krunner. I'm sure people will say there's absolutely nothing wrong with that but there's no harm in letting people know :)

It's not totally unimaginable that having software from two different desktop environments can cause unexpected issues.

---

### Post by vasa1 on 2017-03-24
Since you have opened [a new thread on kde-wallet]("https://ubuntuforums.org/showthread.php?t=2356613"), should this thread be closed? It wouldn't be productive to have two threads open on what maybe the same topic.

---

### Post by juntjoo2 on 2017-03-25
> **vasa1 said:**
> It's often more convenient to provide information generated via the terminal.

In this case, **cd** to your **autostart** folder and then run```
ls -lR
```Copy the entire output, including the command till the final terminal prompt that returns once the command is complete and post that here within code tags. Thanks!

for some reason I don't remember how I got to that autostart folder.  I just tried searching via the file explorer and the search tool at the top right of the desktop sidebar to no avail.  Where is this file/folder usually?

> **vasa1 said:**
> It's also useful to point out what additional software you've installed. For example, I see kdeconnect, korganizer, and krunner. I'm sure people will say there's absolutely nothing wrong with that but there's no harm in letting people know :)

It's not totally unimaginable that having software from two different desktop environments can cause unexpected issues.

I'm sorry, I don't even know what you're talking about.  It's like I woke up one day and it was all here before me. I do recall trying different "desktop environments" to try to solve some problem, so I guess that's related but other than that I wouldn't know to disclose this information you suggested.

> **vasa1 said:**
> Since you have opened [a new thread on kde-wallet]("https://ubuntuforums.org/showthread.php?t=2356613"), should this thread be closed? It wouldn't be productive to have two threads open on what maybe the same topic.

you
tell me. I wouldn't know if they're related.  sorry.

---

### Post by vasa1 on 2017-03-25
Please post the output of```
ls /usr/share/xsessions
```

---

### Post by juntjoo2 on 2017-03-25
> **vasa1 said:**
> It's often more convenient to provide information generated via the terminal.

In this case, **cd** to your **autostart** folder and then run```
ls -lR
```Copy the entire output, including the command till the final terminal prompt that returns once the command is complete and post that here within code tags. Thanks!

okay, found it by looking at the pic I took. sorry. here:

```
ben@Hal:/etc/xdg$ ls -lR.:
total 476
-rw-r--r-- 1 root root     86 Jan  2  2016 accept-languages.codes
-rw-r--r-- 1 root root    154 Mar  7  2016 accountwizard.knsrc
drwxr-xr-x 2 root root   4096 Feb 21 14:29 akonadi
-rw-r--r-- 1 root root     99 Mar 10  2016 akonadi.categories
-rw-r--r-- 1 root root    311 Mar 10  2016 ark.categories
-rw-r--r-- 1 root root    149 Mar  1  2016 aurorae.knsrc
drwxr-xr-x 2 root root   4096 Mar 15 15:31 autostart
-rw-r--r-- 1 root root     81 Mar  1  2016 cgcgtk3.knsrc
-rw-r--r-- 1 root root     76 Mar  1  2016 cgcicon.knsrc
-rw-r--r-- 1 root root     82 Mar  1  2016 cgctheme.knsrc
drwxr-xr-x 2 root root   4096 Feb 21 14:29 colors
-rw-r--r-- 1 root root    183 Mar  1  2016 colorschemes.knsrc
-rw-r--r-- 1 root root    243 Mar  1  2016 comic.knsrc
-rw-r--r-- 1 root root    195 Mar  9  2016 dragonplayerrc
-rw-r--r-- 1 root root    132 Mar  1  2016 emoticons.knsrc
-rw-r--r-- 1 root root    126 Mar  1  2016 icons.knsrc
-rw-r--r-- 1 root root    156 Mar  7  2016 kaddressbook_themes.knsrc
-rw-r--r-- 1 root root    122 Dec  8  2015 kcm-about-distrorc
-rw-r--r-- 1 root root  19859 Jan  4  2016 kdebug.areas
-rw-r--r-- 1 root root   4337 Jan  4  2016 kdebugrc
-rw-r--r-- 1 root root   3159 Mar  7  2016 kdepim.categories
-rw-r--r-- 1 root root    105 Feb 27  2016 kdepimlibs-kioslave.categories
-rw-r--r-- 1 root root    976 Feb 29  2016 kdepim-runtime.categories
-rw-r--r-- 1 root root    202 Mar  1  2016 kfontinst.knsrc
-rw-r--r-- 1 root root  12812 Jan  2  2016 khtmlrc
-rw-r--r-- 1 root root   6322 Mar  7  2016 kmail.antispamrc
-rw-r--r-- 1 root root   1009 Mar  7  2016 kmail.antivirusrc
-rw-r--r-- 1 root root    151 Mar  7  2016 knotes_printing_theme.knsrc
-rw-r--r-- 1 root root    118 Mar  7  2016 korganizer.knsrc
-rw-r--r-- 1 root root    153 Jan  2  2016 kshorturifilterrc
-rw-r--r-- 1 root root    134 Mar  7  2016 ksieve_script.knsrc
-rw-r--r-- 1 root root 190652 Jan  4  2016 ksslcalist
-rw-r--r-- 1 root root    821 Mar  1  2016 ksysguard.knsrc
-rw-r--r-- 1 root root    218 Mar  9  2016 ktp_approverrc
-rw-r--r-- 1 root root    212 Mar  1  2016 kwineffect.knsrc
-rw-r--r-- 1 root root    212 Mar  1  2016 kwinscripts.knsrc
-rw-r--r-- 1 root root    230 Mar  1  2016 kwinswitcher.knsrc
-rw-r--r-- 1 root root     79 Nov 21  2015 libkgapi.categories
-rw-r--r-- 1 root root  24116 Mar  7  2016 libkleopatrarc
drwxr-xr-x 3 root root   4096 Mar 15 15:30 menus
-rw-r--r-- 1 root root    147 Mar  7  2016 messageviewer_header_themes.knsrc
-rw-r--r-- 1 root root     80 Mar  1  2016 org_kde_kwayland.categories
-rw-r--r-- 1 root root    622 Mar  1  2016 org_kde_kwin.categories
-rw-r--r-- 1 root root    202 Mar  1  2016 plasma-themes.knsrc
-rw-r--r-- 1 root root    189 Mar  2  2016 plasmoids.knsrc
-rw-r--r-- 1 root root    283 Mar  9  2016 servicemenu.knsrc
-rw-r--r-- 1 root root     67 Jul 29  2015 sni-qt.conf
drwxr-xr-x 2 root root   4096 Jul 19  2016 systemd
-rw-r--r-- 1 root root    494 Mar  2  2016 taskmanagerrulesrc
drwxr-xr-x 2 root root   4096 Mar 15 15:31 Thunar
-rw-r--r-- 1 root root     43 Jan  7  2016 Trolltech.conf
drwxr-xr-x 2 root root   4096 Feb 21 10:27 tumbler
drwxr-xr-x 2 root root   4096 Feb 21 14:28 ui
-rw-r--r-- 1 root root    414 Apr 14  2016 user-dirs.conf
-rw-r--r-- 1 root root    418 Apr 14  2016 user-dirs.defaults
-rw-r--r-- 1 root root    356 Mar  2  2016 wallpaper.knsrc
-rw-r--r-- 1 root root    132 Mar  1  2016 xcursor.knsrc
drwxr-xr-x 7 root root   4096 Feb 21 12:42 xdg-xubuntu
drwxr-xr-x 4 root root   4096 Feb 21 10:27 xfce4


./akonadi:
total 8
-rw-r--r-- 1 root root 3659 Apr 20  2016 mysql-global.conf
-rw-r--r-- 1 root root 3383 Mar 10  2016 mysql-global-mobile.conf


./autostart:
total 240
-rw-r--r-- 1 root root   345 Apr 14  2016 a11y-profile-manager-indicator-autostart.desktop
-rw-r--r-- 1 root root   202 Feb 24  2016 at-spi-dbus-bus.desktop
-rw-r--r-- 1 root root  1782 Jan  2  2016 baloo_file.desktop
-rw-r--r-- 1 root root   194 Mar 31  2016 blueman.desktop
-rw-r--r-- 1 root root   374 Apr  7  2016 deja-dup-monitor.desktop
-rw-r--r-- 1 root root   485 Nov  1  2015 gnome-keyring-pkcs11.desktop
-rw-r--r-- 1 root root   478 Nov  1  2015 gnome-keyring-secrets.desktop
-rw-r--r-- 1 root root   445 Nov  1  2015 gnome-keyring-ssh.desktop
-rw-r--r-- 1 root root   448 Jan  4  2016 gnome-screensaver.desktop
-rw-r--r-- 1 root root   302 Aug 22  2016 gnome-settings-daemon.desktop
-rw-r--r-- 1 root root   183 Feb 16 15:29 gnome-software-service.desktop
-rw-r--r-- 1 root root   464 Apr 20  2016 gnome-user-share-obexpush.desktop
-rw-r--r-- 1 root root   444 Apr 20  2016 gnome-user-share-webdav.desktop
-rw-r--r-- 1 root root   279 Nov 27  2015 gsettings-data-convert.desktop
-rw-r--r-- 1 root root   304 Feb 23 12:33 hplip-systray.desktop
-rw-r--r-- 1 root root   264 Jan 20 14:17 indicator-application.desktop
-rw-r--r-- 1 root root   302 May 26  2016 indicator-bluetooth.desktop
-rw-r--r-- 1 root root   310 Apr  6  2016 indicator-datetime.desktop
-rw-r--r-- 1 root root   298 Nov 25  2015 indicator-keyboard.desktop
-rw-r--r-- 1 root root   283 May  5  2015 indicator-messages.desktop
-rw-r--r-- 1 root root   286 Jan  5  2016 indicator-power.desktop
-rw-r--r-- 1 root root   202 Jan  4  2016 indicator-printers.desktop
-rw-r--r-- 1 root root   252 Apr 12  2016 indicator-session.desktop
-rw-r--r-- 1 root root   295 Apr  7  2016 indicator-sound.desktop
-rw-r--r-- 1 root root  1161 Mar 20  2016 kdeconnectd.desktop
-rw-r--r-- 1 root root  1020 Mar  2  2016 krunner.desktop
-rw-r--r-- 1 root root  2445 Dec 21  2015 light-locker.desktop
-rw-r--r-- 1 root root   203 Sep 26  2014 mybackuplinux.desktop
-rw-r--r-- 1 root root   203 Sep 26  2014 mybackuplinux.desktop~
-rw-r--r-- 1 root root   210 Mar 18  2016 nautilus-autostart.desktop
-rw-r--r-- 1 root root   350 Jun 13  2016 nm-applet.desktop
-rw-r--r-- 1 root root   289 Apr 18  2016 onboard-autostart.desktop
-rw-r--r-- 1 root root   301 Apr  7  2016 orca-autostart.desktop
-rw-r--r-- 1 root root 11713 Mar  2  2016 org.kde.klipper.desktop
-rwxr-xr-x 1 root root  7119 Mar  7  2016 org.kde.korgac.desktop
-rw-r--r-- 1 root root  2209 Mar  2  2016 plasmashell.desktop
-rw-r--r-- 1 root root   358 Nov 21  2014 polkit-gnome-authentication-agent-1.desktop
-rw-r--r-- 1 root root  3297 Apr 14  2016 polkit-kde-authentication-agent-1.desktop
-rw-r--r-- 1 root root   375 Mar  7  2016 print-applet.desktop
-rw-r--r-- 1 root root  4474 Mar 21  2016 pulseaudio.desktop
-rw-r--r-- 1 root root   363 Jul  1  2016 unity-fallback-mount-helper.desktop
-rw-r--r-- 1 root root   302 Jul  1  2016 unity-settings-daemon.desktop
-rw-r--r-- 1 root root  9344 Jun 29  2016 update-notifier.desktop
-rw-r--r-- 1 root root   312 Jul  3  2013 user-dirs-update-gtk.desktop
-rw-r--r-- 1 root root   424 Feb 18  2016 vino-server.desktop
-rw-r--r-- 1 root root   996 Mar  2  2016 xembedsniproxy.desktop
-rw-r--r-- 1 root root  3460 Jul 10  2015 xfce4-notes-autostart.desktop
-rw-r--r-- 1 root root  5182 Jan  4  2016 xfce4-power-manager.desktop
-rw-r--r-- 1 root root   223 Feb 21  2015 xfce4-volumed.desktop
-rw-r--r-- 1 root root  2280 May 13  2015 xfsettingsd.desktop
-rw-r--r-- 1 root root  4818 May 25  2015 xscreensaver.desktop
-rw-r--r-- 1 root root   244 Feb 24  2016 zeitgeist-datahub.desktop


./colors:
total 20
-rw-r--r-- 1 root root  841 Jan  4  2016 40.colors
-rw-r--r-- 1 root root 3080 Jan  4  2016 Oxygen.colors
-rw-r--r-- 1 root root 1651 Jan  4  2016 Rainbow.colors
-rw-r--r-- 1 root root 3121 Jan  4  2016 Royal.colors
-rw-r--r-- 1 root root 2582 Jan  4  2016 Web.colors


./menus:
total 76
drwxr-xr-x 2 root root  4096 Nov 25 21:49 applications-merged
-rw-r--r-- 1 root root 19392 Jun 30  2016 gnome-applications.menu
-rw-r--r-- 1 root root 10920 Feb 19  2016 kde4-applications.menu
-rw-r--r-- 1 root root   279 Mar  4  2016 kde-information.menu
-rw-r--r-- 1 root root 10795 Jan  2  2016 kf5-applications.menu
-rw-r--r-- 1 root root   279 Mar  1  2016 kinfocenter.menu
-rw-r--r-- 1 root root  2827 Jul  5  2016 unitycc.menu
-rw-r--r-- 1 root root  3891 Jul  1  2016 unity-lens-applications.menu
-rw-r--r-- 1 root root  4293 May  7  2015 xfce-applications.menu
-rw-r--r-- 1 root root  2255 May 13  2015 xfce-settings-manager.menu


./menus/applications-merged:
total 4
-rw-r--r-- 1 root root 699 Jan 17  2012 wine.menu


./systemd:
total 0
lrwxrwxrwx 1 root root 18 Nov 19 12:39 user -> ../../systemd/user


./Thunar:
total 12
-rw-r--r-- 1 root root 9191 Mar  3 08:33 uca.xml


./tumbler:
total 4
-rw-r--r-- 1 root root 2074 Nov  1  2015 tumbler.rc


./ui:
total 8
-rw-r--r-- 1 root root 6657 Jan  2  2016 ui_standards.rc


./xdg-xubuntu:
total 24
drwxr-xr-x 2 root root 4096 Feb 21 12:42 autostart
-rw-r--r-- 1 root root 2547 Jan  9  2016 compton.conf
drwxr-xr-x 2 root root 4096 Feb 21 12:42 menus
drwxr-xr-x 2 root root 4096 Feb 21 12:42 orage
drwxr-xr-x 2 root root 4096 Feb 21 12:42 Thunar
drwxr-xr-x 6 root root 4096 Feb 21 12:42 xfce4


./xdg-xubuntu/autostart:
total 4
-rw-r--r-- 1 root root 29 Jan  9  2016 xfce4-tips-autostart.desktop


./xdg-xubuntu/menus:
total 12
-rw-r--r-- 1 root root 5250 Apr 13  2016 xfce-applications.menu
-rw-r--r-- 1 root root 3511 Jan  9  2016 xfce-settings-manager.menu


./xdg-xubuntu/orage:
total 4
-rw-r--r-- 1 root root 372 Jan  9  2016 oragerc


./xdg-xubuntu/Thunar:
total 12
-rw-r--r-- 1 root root 11571 Apr 17  2016 uca.xml


./xdg-xubuntu/xfce4:
total 20
-rw-r--r-- 1 root root   93 Jan  9  2016 helpers.rc
drwxr-xr-x 2 root root 4096 Feb 21 12:42 panel
drwxr-xr-x 2 root root 4096 Feb 21 12:42 terminal
drwxr-xr-x 2 root root 4096 Feb 21 12:42 whiskermenu
drwxr-xr-x 3 root root 4096 Feb 21 12:40 xfconf


./xdg-xubuntu/xfce4/panel:
total 4
-rw-r--r-- 1 root root 2688 Jan  9  2016 default.xml


./xdg-xubuntu/xfce4/terminal:
total 4
-rw-r--r-- 1 root root 375 Jan  9  2016 terminalrc


./xdg-xubuntu/xfce4/whiskermenu:
total 4
-rw-r--r-- 1 root root 1372 Mar  2  2016 defaults.rc


./xdg-xubuntu/xfce4/xfconf:
total 4
drwxr-xr-x 2 root root 4096 Feb 21 12:42 xfce-perchannel-xml


./xdg-xubuntu/xfce4/xfconf/xfce-perchannel-xml:
total 48
-rw-r--r-- 1 root root  333 Mar 13  2016 parole.xml
-rw-r--r-- 1 root root 2007 Jan  9  2016 thunar-volman.xml
-rw-r--r-- 1 root root  247 Jan  9  2016 thunar.xml
-rw-r--r-- 1 root root 1352 Jan  9  2016 xfce4-desktop.xml
-rw-r--r-- 1 root root 7155 Feb  9  2016 xfce4-keyboard-shortcuts.xml
-rw-r--r-- 1 root root  281 Jan  9  2016 xfce4-notifyd.xml
-rw-r--r-- 1 root root  759 Jan  9  2016 xfce4-power-manager.xml
-rw-r--r-- 1 root root 2072 Jan  9  2016 xfce4-session.xml
-rw-r--r-- 1 root root  286 Jan  9  2016 xfprint.xml
-rw-r--r-- 1 root root 3498 Feb 25  2016 xfwm4.xml
-rw-r--r-- 1 root root 1089 Feb 25  2016 xsettings.xml


./xfce4:
total 24
-rw-r--r-- 1 root root  242 Sep 21  2015 helpers.rc
drwxr-xr-x 2 root root 4096 Feb 21 10:27 panel
drwxr-xr-x 3 root root 4096 Nov 25 19:07 xfconf
-rw-r--r-- 1 root root  221 May 25  2015 Xft.xrdb
-rwxr-xr-x 1 root root 5873 May 25  2015 xinitrc


./xfce4/panel:
total 4
-rw-r--r-- 1 root root 3177 Aug 31  2015 default.xml


./xfce4/xfconf:
total 4
drwxr-xr-x 2 root root 4096 Feb 21 12:42 xfce-perchannel-xml


./xfce4/xfconf/xfce-perchannel-xml:
total 24
-rw-r--r-- 1 root root  565 Apr  2  2011 thunar-volman.xml
-rw-r--r-- 1 root root 5961 May  7  2015 xfce4-keyboard-shortcuts.xml
-rw-r--r-- 1 root root  234 Oct 31  2014 xfce4-power-manager.xml
-rw-r--r-- 1 root root 1551 May 25  2015 xfce4-session.xml
-rw-r--r-- 1 root root 2553 May 13  2015 xsettings.xml
```

---

### Post by vasa1 on 2017-03-25
One thing that isn't made obvious by various blogs and tech sites is that installing several desktop environments on the same system can cause consequences, some of them confusing. If you have a vanilla system, it would be easier to trouble-shoot.

BTW, uninstalling a desktop environment isn't as easy as it appears!

---

### Post by juntjoo2 on 2017-03-25
> **vasa1 said:**
> Please post the output of```
ls /usr/share/xsessions
```

```
ben@Hal:/etc/xdg$ ls /usr/share/xsessions
gnome.desktop  ubuntu.desktop  xfce.desktop  xubuntu.desktop
```

thanks!

---

### Post by vasa1 on 2017-03-25
The output of```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl -nrn
```based on [howefield's code]("https://ubuntuforums.org/showthread.php?t=2352413&p=13606493#post13606493") will also help people get to know a little more about your system.

---

### Post by juntjoo2 on 2017-03-26
> **vasa1 said:**
> The output of```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl -nrn
```based on [howefield's code]("https://ubuntuforums.org/showthread.php?t=2352413&p=13606493#post13606493") will also help people get to know a little more about your system.

k, thanks.  here:

```
grep -Ev '(^#|^ *$|deb-src)' /etc/apt/sources.list /etc/apt/sources.list.d/* | nl -nrn     1	/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial main restricted
     2	/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates main restricted
     3	/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial universe
     4	/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates universe
     5	/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial multiverse
     6	/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-updates multiverse
     7	/etc/apt/sources.list:deb http://us.archive.ubuntu.com/ubuntu/ xenial-backports main restricted universe multiverse
     8	/etc/apt/sources.list:deb http://archive.canonical.com/ubuntu xenial partner
     9	/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security main restricted
    10	/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security universe
    11	/etc/apt/sources.list:deb http://security.ubuntu.com/ubuntu xenial-security multiverse
    12	/etc/apt/sources.list.d/inameiname-ubuntu-stable-xenial.list:deb http://ppa.launchpad.net/inameiname/stable/ubuntu xenial main
    13	/etc/apt/sources.list.d/inameiname-ubuntu-stable-xenial.list.save:deb http://ppa.launchpad.net/inameiname/stable/ubuntu xenial main
    14	/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
    15	/etc/apt/sources.list.d/ubuntu-wine-ubuntu-ppa-xenial.list.save:deb http://ppa.launchpad.net/ubuntu-wine/ppa/ubuntu xenial main
    16	/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main
    17	/etc/apt/sources.list.d/wine-ubuntu-wine-builds-xenial.list.save:deb http://ppa.launchpad.net/wine/wine-builds/ubuntu xenial main



```

---

