---
title: "Folders and file names are squished on upgrade"
date: 2019-01-28
forum: General Help
---

### Post by caterhamfan on 2019-01-28
So, I recently upgraded from Ubuntu 16.04 to 18. Not too keen on gnome so I got it back to unity almost! 
The only issue I've found so far is it appears to have squashed my files/folders and the names. They just don't look right, as the image shows.

[ATTACH=CONFIG]282329[/ATTACH]

Does anyone know the settings that are causing this? Will be grateful for any assistance with this.

 Thank you,

---

### Post by cmcanulty on 2019-01-28
could be a font setting limiting shortcut line width but I am not sure if you can change that without making all fonts smaller.

---

### Post by Dennis N on 2019-01-28
You can try a couple of things:

1) larger icon size (set by Nautilus zoom level) will make a wider text field for icon labels.
2) smaller desktop font size (can be independently set of interface font)
3) smaller interface font size (applies to thumbnails) 

Use Tweaks > Fonts to set interface font, set desktop font and size from dconf-editor as shown in attached image.

---

