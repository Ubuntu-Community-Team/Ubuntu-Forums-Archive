---
title: "After installing Nautilus in Xubuntu 12.04, desktop icons and wallpaper are gone!"
date: 2013-07-11
forum: General Help
---

### Post by vcrpcant on 2013-07-11
Hi,

After installing Nautilus in Xubuntu 12.04, desktop icons and wallpaper are gone!

Besides, now I can't right-click in the desktop 

After googling for solutions, I've done te following:
- I've uninstalled Nautilus, but everything remained the same.
- reinstalled Nautilus again and installed gnome-tweak-tool and deactivated: have file manager manager the desktop.

Between these actions I've rebooted, just in case loging ou and in wouldn't make it work, but, no luck :confused:

Anyone has any hints?

---

### Post by nerdtron on 2013-07-11
Seems like nautilus became the default handler for desktop. By default, nautilus doesn't show desktop icons. You can try to restore it. Follow the tutorial.
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

---

### Post by grahammechanical on 2013-07-11
It is my understanding that Nautilus is more than just a file manager. Think of it as being embedded into the desktop. That would be the Gnome desktop environment not the Xfce environment used in Xubuntu. It is my guess that installing Nautilus also removed some bits from Xfce. So, uninstalling Nautilus would not be enough. May be you could try re-installing Xfce.

Regards.

---

### Post by vcrpcant on 2013-07-11
> **nerdtron said:**
> Seems like nautilus became the default handler for desktop. By default, nautilus doesn't show desktop icons. You can try to restore it. Follow the tutorial.
[https://help.ubuntu.com/community/DefaultFileManager](https://help.ubuntu.com/community/DefaultFileManager)

Thanks, I've been trying those solutions for the last hour or so, but still no luck :(

I think I've change too many things and could not revert to original config files :(

---

### Post by vcrpcant on 2013-07-11
> **grahammechanical said:**
> It is my understanding that Nautilus is more than just a file manager. Think of it as being embedded into the desktop. That would be the Gnome desktop environment not the Xfce environment used in Xubuntu. It is my guess that installing Nautilus also removed some bits from Xfce. So, uninstalling Nautilus would not be enough. May be you could try re-installing Xfce.

Regards.

If I do that will I loose the panels (launchers), windows and icons configurations?
If so, can I make backups of some files and afterwards paste them back?

---

