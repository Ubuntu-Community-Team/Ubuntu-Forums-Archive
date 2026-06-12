---
title: "Xubuntu theming conflict?"
date: 2013-12-20
forum: General Help
---

### Post by princeofnam on 2013-12-20
I just installed Xubuntu over Kubuntu to give it a try and I've found that I've been having some trouble tweaking the colors/themes.  It seems stuck on the color schema I chose in Kubuntu.  theme configuration doesn't really do anything.

---

### Post by Erik1984 on 2013-12-20
Usually these issues can be solved by deleting (or renaming) the proper configuration files or folders (the .dotfiles in your home directory), unfortunately I don't know the precise folders in this case. Had some similar problems when I installed Ubuntu Gnome over Kubuntu, Firefox looked especially weird. You could try to remove both the XFCE and KDE settings to a backup location and restart your desktop session. for example move the whole .kde to .kde_backup.  What I suspect is that KDE changes the GTK configuration files, so affecting also the look of Gnome/GTK applications.

---

### Post by princeofnam on 2013-12-20
Thanks.  I'll try that.

---

### Post by ajgreeny on 2013-12-20
This may not be your problem at the moment but it is one to be aware of in case you see it later.

I have a few KDE applications on my Xubuntu 12.04 and to configure the look of them I installed systemsettings.  No problems showed up until I made changes in systemsettings to the font configuration, when suddenly all fonts in a large number of applications looked very spindly and strange, and very difficult to read.  By chance I found that removing the hidden .fonts.conf file that systemsettings made in my home when configuring the fonts made everything OK again.

If there are other similar files in your home that you can find, made by systemsettings, you may find that removing them may also change the colours to the ones you want rather than what KDE thinks you should have.

---

### Post by princeofnam on 2013-12-20
Thanks.  Doesn't system settings come default with Xubuntu? Why did you have to install it.  Also how would I know which items created in the home folder were created by system settings?  Thanks for the heads up

---

### Post by ajgreeny on 2013-12-20
No; it's a different systemsettings package, note one word with no space, and it's a KDE configuration application, nothing to do with Xubuntu or xfce.

---

### Post by Toz on 2013-12-20
Something to keep in mind....

Xubuntu (Xfce) has two theme components: window themes and gtk themes.

The Window themes are managed through the "Window Manager" applet (Settings Manager -> Window Manager -> Style tab) and require the the Xfce Window Manager (xfwm4) is running. Look for it in your process list. If it is not running, you can force it replace another window manager via the command:
```
xfwm4 --replace
```
The window manager styles are the window title bars, open/close/minimize/maximimize buttons, borders, etc).

Appearance themes are GTK themes that manage the "insides" of the windows (buttons, text, dropdowns, colours, etc). The are set through the Appearance Settings dialog (Settings Manager -> Appearance -> Style). Keep in mind that these can be over-written by configuration directives in your home directory. Look for files like ~/.gtkrc-2.0 and the files in ~/.config/gtk-3.0. There maybe a directive in there forcing a theme to be displayed. (Also look at the system-wide GTK configuration files in /etc/gtk-2.0 and /etc/gtk-3.0).

---

