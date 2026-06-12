---
title: "xdg-desktop-por SPAM my journal"
date: 2019-11-25
forum: General Help
---

### Post by alain.roger on 2019-11-25
[COLOR=#2E3436][FONT=&amp]Hi,[/FONT][/COLOR]

[COLOR=#2E3436][FONT=&amp]i'm checking my journal as my computer since upgrade to kubuntu 19.10 makes my computer slower than usual.[/FONT][/COLOR]
[COLOR=#2E3436][FONT=&amp]I can see a lot of message regarding : xdg-desktop-por[3543] or xdg-desktop-por[24805] in journal with following message:
[/FONT][/COLOR]```
[COLOR=#636363][FONT=Menlo]Failed to get application states: GDBus.Error:org.freedesktop.portal.Error.Failed: Could not get window list: Cannot invoke method; proxy is for the well-known name org.gnome.Shell without an owner, and proxy was constructed with the G_DBUS_PROXY_FLAGS_DO_NOT_AUTO_START flag[/FONT][/COLOR]
```
[COLOR=#2E3436][FONT=&amp]in fact, it SPAMs my logs and i think it is useless to do so. Moreover i do not know about what the message is.[/FONT][/COLOR]
[COLOR=#2E3436][FONT=&amp]
Please can you tell me:[/FONT][/COLOR]
[COLOR=#2E3436][FONT=&amp]1. what is this message about?[/FONT][/COLOR]
[COLOR=#2E3436][FONT=&amp]2. how to solve this issue to avoid spamming my logs ?

[/FONT][/COLOR]i did several DE tests and this issue is only visible under GNOME & KDE. Xfce does not have this issue.

[COLOR=#2E3436][FONT=&amp]thx.[/FONT][/COLOR]

---

### Post by SeijiSensei on 2019-11-25
I upgraded from Kubuntu 19.04 to 19.10 using "do-release-upgrade". I don't see anything like this in my logs.  I only have Kubuntu installed and no other desktops.

Might I suggest a fresh installation of Kubuntu 19.10?  Always the easiest route, especially if, like me, you have /home on a separate partition.

---

### Post by alain.roger on 2019-11-26
I also have /home on a different partition, however i have a lot of apps installed and my computer is designed for development and video editing, so that's not a step i want (to reinstall OS).

---

### Post by SeijiSensei on 2019-11-26
If the applications all come from the repositories, then you can use the --set-selections and --get-selections options to dpkg to create a list of all installed software and use it to add the applications to a new installation.

---

### Post by Holger_Gehrke on 2019-11-26
Doing 'apt search xdg-desktop-por' shows xdg-desktop-portal and some other related packages, which - according to the description available through 'apt show xdg-desktop-portal' -- seems to be some kind of enhanced desktop integration for the sandboxed package systems snap and flatpak. If you're using neither of these package systems and have xdg-desktop-portal installed then you might think about uninstalling it.

The message more or less says that portal is trying to get a list of windows from a proxy object that is supposed to talk to the Gnome Shell but can't for some reason. Since xdg-desktop-portal is supposed to be desktop neutral I'd check whether the desktop-specific packages xdg-desktop-portal-gtk and/or xdg-desktop-portal-kde are installed, since those are probably the parts that should communicate with the actual running desktop.

Holger

---

### Post by alain.roger on 2019-11-28
SNAP and flatpak were installed but i removed them several weeks ago...So i don't understand how it could be possible to use them anymore. I read about the flatpak issue with xdg, that's why i removed it as first step and check what's going on...but the issue persists.

---

