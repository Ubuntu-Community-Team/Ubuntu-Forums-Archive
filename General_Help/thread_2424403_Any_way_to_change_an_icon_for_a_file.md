---
title: "Any way to change an icon for a file?"
date: 2019-08-08
forum: General Help
---

### Post by udalny on 2019-08-08
Hello, I'm looking for a way to change an icon for a specific file on my desktop.

 I tried changing it through file properties, but the icon shows no respond while clicking on it.

 Is there any terminal commands to do it?

I run the latest version of Lubuntu 19.04 (LXQT environment)

---

### Post by guiverc on 2019-08-08
Please specify your exact release of Lubuntu, for example the latest two releases of Lubuntu use LXQt (*LXDE was 3 releases back or earlier*).

It might also be helpful if you specify where you want to see the icon, ie. desktop ([https://manual.lubuntu.me/5/5.2/desktop_icons.html](https://manual.lubuntu.me/5/5.2/desktop_icons.html) which is the manual for the latest Lubuntu release) or within the file manager (`pcmanfm-qt` assuming the latest release of Lubuntu (LXQt), or `pcmanfm` if using an older Lubuntu 18.04 LTS (LXDE))

---

### Post by udalny on 2019-08-08
Oh, yes, i'm sorry it's actually LXQT. My version is 19.04.

> **guiverc said:**
> Please specify your exact release of Lubuntu, for example the latest two releases of Lubuntu use LXQt (*LXDE was 3 releases back or earlier*).

It might also be helpful if you specify where you want to see the icon, ie. desktop ([https://manual.lubuntu.me/5/5.2/desktop_icons.html](https://manual.lubuntu.me/5/5.2/desktop_icons.html) which is the manual for the latest Lubuntu release) or within the file manager (`pcmanfm-qt` assuming the latest release of Lubuntu (LXQt), or `pcmanfm` if using an older Lubuntu 18.04 LTS (LXDE))

I want to see the icon on desktop.

I figured it out. You can create a shortcut for your executable on desktop which could have any icon you want. To do that you need to create a blank file and edit like this:

[desktop entry]
Encoding=UTF-8
 Version=1.0
 Type=Application
 Terminal=false
 Exec=<path to your executable>
 Name=<name of your executable>
 Icon=<path to your icon>

Then save it as <name of your executable>.desktop in ~/.local/share/applications and done.

Thanks to guiverc for the link on desktop.

---

