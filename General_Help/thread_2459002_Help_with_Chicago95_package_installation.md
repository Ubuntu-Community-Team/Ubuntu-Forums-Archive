---
title: "Help with Chicago95 package installation"
date: 2021-03-08
forum: General Help
---

### Post by narakuita on 2021-03-08
[COLOR=#000000][FONT=Roboto]I need the help of the most experienced. I installed this package, and I am missing a few things:
-How to correctly change the Start button
-Change the color of the top bar of the window to blue and the one in the background to light gray.Thanks so much![/FONT][/COLOR]

---

### Post by CelticWarrior on 2021-03-08
[https://github.com/grassmunk/Chicago95/blob/master/INSTALL.md](https://github.com/grassmunk/Chicago95/blob/master/INSTALL.md)

---

### Post by narakuita on 2021-03-08
I've seen Garda, but there is something that escapes me.
I've done these steps: 

I installed the first packages with the command:
[HTML]sudo apt updatesudo apt upgrade 
sudo apt install xfconf xfce4-panel-profiles[/HTML]

Then the remaining packages I downloaded from here and installed:
[https://download.opensuse.org/repositories/home:/bgstack15:/Chicago95/xUbuntu_20.04/all/](https://download.opensuse.org/repositories/home:/bgstack15:/Chicago95/xUbuntu_20.04/all/)
After that I had the autmatic installation of the Chicago95 package; installer.py
Then I saw that some things were still missing, so I checked with the following command:

[HTML]ChicagoPlus
PlusGUI[/HTML]

and it appeared here:

[HTML]C:\home\andrea> ChicagoPlus
usage: ChicagoPlus [options] MS_Theme_File
ChicagoPlus: error: the following arguments are required: theme_file
C:\home\andrea> PlusGUI
(PlusGUI:1294): Gtk-WARNING **: 17:33:05.952: Could not load a pixbuf from icon theme.
This may indicate that pixbuf loaders or the mime database could not be found.
(PlusGUI:1294): Gtk-WARNING **: 17:33:05.976: Could not load image ‘original.png’: Failed to open file “/usr/libexec/chicago95-theme-plus/original.png”: File o directory non esistente
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.013: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.013: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.013: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.013: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.013: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.013: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.013: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed
(PlusGUI:1294): GLib-GIO-CRITICAL **: 17:33:06.014: g_dbus_proxy_new: assertion ‘G_IS_DBUS_CONNECTION (connection)’ failed[/HTML]

I await news. Thank you so much!

---

### Post by guiverc on 2021-03-08
Also asked at [https://discourse.lubuntu.me/t/help-with-chicago95-package-installation/2283](https://discourse.lubuntu.me/t/help-with-chicago95-package-installation/2283)

---

### Post by narakuita on 2021-03-08
[COLOR=#000000][FONT=Roboto]Yes, I'm looking for a solution on multiple forums.[/FONT][/COLOR][COLOR=#000000][FONT=Roboto] [/FONT][/COLOR]

---

