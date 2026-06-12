---
title: "Blurry SVG icons"
date: 2008-04-29
forum: General Help
---

### Post by sonoxious on 2008-04-29
Hi, I'm using ubuntu 8.04 with Gnome.

Whenever I change the icon of a folder to a svg-icon, it still gets 'blurry' or 'blocky' when I increase the size of the icon. This is true even if I choose to change the icon to '/usr/share/icons/Human/scalable/filesystems/gnome-fs-directory.svg', which looks identical to the regular folder icon at standard size. The regular folder icon used by the current theme does however scale well without getting blurry.

Is there any reason why the icons I change manually cannot scale well?

---

### Post by rayblasdel on 2008-05-16
This seems to be a bug in the GNOME properties dialog. When generating the icon GNOME uses two different locations for the image data, the first is a localized image, and the second is the main address. The dialog only changes the main address and leaves the localized image address alone. So when GNOME sees the conflicting image locations it choses the main icon image, but treats it as a pixmap rather then the SVG it is. For desktop icons this is easy to fix with a text editor as the properties are contained in an easy to access file, but I'm not sure where the icon data is stored for folders.

---

