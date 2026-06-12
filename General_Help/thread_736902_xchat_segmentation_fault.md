---
title: "xchat segmentation fault"
date: 2008-03-27
forum: General Help
---

### Post by mrynit on 2008-03-27
The problem is xchat won't work for me.  If i run xchat from the command line i get Segmentation fault (core dumped). If I run it from the applicaitons menu it will start up then immediately exit.

I think i used the add/remove to install xchat-gnome first then uninstalled it and installed xchat. xchat didnt work then. I have tried various apt-get remove purges with xchat and xchat-gnome to get ride of it but i still have these files:

```
mrynit@dell-desktop:~$ locate xchat
/usr/share/locale-langpack/es/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/pt/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/de/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/zh_CN/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/en_GB/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/fr/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/pt_BR/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/zh_HK/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/zh_TW/LC_MESSAGES/xchat-gnome.mo
/usr/share/locale-langpack/en_AU/LC_MESSAGES/xchat-gnome.mo
/usr/share/app-install/icons/xchat-gnome.png
/usr/share/app-install/icons/xchat.png
/usr/share/app-install/desktop/xchat.desktop
/usr/share/app-install/desktop/xchat-gnome.desktop
/home/christopher/.gconf/apps/xchat
/home/christopher/.gconf/apps/xchat/%gconf.xml
/home/christopher/.gconf/apps/xchat/spellcheck
/home/christopher/.gconf/apps/xchat/spellcheck/%gconf.xml
/home/christopher/.gconf/apps/xchat/irc
/home/christopher/.gconf/apps/xchat/irc/%gconf.xml
/home/christopher/.gconf/apps/xchat/main_window
/home/christopher/.gconf/apps/xchat/main_window/%gconf.xml
/home/christopher/.gconf/apps/xchat/channel_list
/home/christopher/.gconf/apps/xchat/channel_list/%gconf.xml
/home/christopher/.local/share/applications/xchat-gnome.desktop
/home/christopher/.gnome2/accels/xchat-gnome
/home/christopher/.xchat2
/home/christopher/.xchat2/xchat.conf
/home/christopher/.xchat2/downloads
/home/christopher/.xchat2/sound.conf
/home/christopher/.xchat2/notify.conf
/home/christopher/.xchat2/ignore.conf
/home/christopher/.xchat2/servlist_.conf
/home/christopher/.xchat2/keybindings.conf
/var/lib/dpkg/info/xchat-gnome-common.list
/var/lib/dpkg/info/xchat-gnome-common.postrm
/var/lib/dpkg/info/xchat-common.list
/var/lib/dpkg/info/xchat-common.postrm

```

So after uninstalling both xchat and xchat-gnome I go and install xchat and get teh same segfault problem.

how do i get xchat to work?

---

### Post by jepong on 2008-04-26
im also having the very same problem... pls help:confused:

---

### Post by Cygoku on 2008-06-01
Hello, help here needed !! :(

Cygoku

---

### Post by Ozpilot on 2008-06-28
This worked for me.

Uninstall Xchat2.

Go to your home directory and select hidden files under view.  Delete the .xchat2 directory.

Reinstall Xchat.

---

