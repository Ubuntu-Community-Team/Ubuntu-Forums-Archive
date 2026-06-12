---
title: "Context menu on desktop 21.10"
date: 2021-11-18
forum: General Help
---

### Post by rwe061 on 2021-11-18
Ubuntu 21.10

The File manager Nautilus context menu does not work the same on files on the desktop.  

When using File manager context menu, I get my encrypt function, but when right click on the desktop icon I don't see the option in the context menu.

There is an option to 'Show In Files', after which you see the correct context menu.

How can I get the same context menu when right clicking on a desktop icon ?

Thanks

---

### Post by vanadium on 2021-11-21
The File Manager does not anymore provide the icons on the desktop since a few versions. Options appearing in File Manager therefore may not appear when right-clicking a desktop icon, especially for custom options provided by nautilus extensions.

That limitation is caused by Ubuntu using a shell, Gnome Shell, that essentially does not anymore support an active desktop, i.e., a desktop that works as a file manager. If desktop icons are important in your workflow, you may need to move to a desktop environment that fully supports desktop icons such as Mate, Xfce or KDE. Swapping out nautilus for e.g. nemo, which can be set to handle desktop icons, may be a workaround, but is not trivial to do.

---

