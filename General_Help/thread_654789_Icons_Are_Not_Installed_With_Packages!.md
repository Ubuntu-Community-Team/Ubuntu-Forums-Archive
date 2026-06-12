---
title: "Icons Are Not Installed With Packages!"
date: 2007-12-31
forum: General Help
---

### Post by GenuineXP on 2007-12-31
So I've noticed that sometimes when I install packages a neat icon is added to my system (typically in /usr/share/pixmaps/). However, too often some programs are installed without getting that nifty icon even though I know there's supposed to be one.

Occasionally, the icon mysteriously appears days later. For instance, this happened to me when I tried out FrostWire. Initially, I got an ugly generic application icon in my menu. I searched /usr/share/pixmaps/ for a FrostWire icon and found none. Then, magically, one day an icon appeared! wtf?

This just recently happened with gsynaptic. I've seen screenshots where, indeed, there is an icon. I have none. The menu entry references "/usr/share/pixmaps/touchpad.png", but that file doesn't exist! Why didn't it install properly?

...

Okay, so I just found that touchpad.png exists in /usr/share/app-install/icons/ as I was posting this, but the file seems to be corrupted. Not only that, but there are lots of duplicate icons in that directory (copies of what's in /usr/share/pixmaps/) including icons for applications I haven't installed. Could someone please explain this to me? If the icons are in this folder, why don't they show up by default or magically appear days later?

---

### Post by disturbedite on 2007-12-31
not all packages ship with icons.  simple as that.

---

### Post by GenuineXP on 2007-12-31
That's what I figured. Some versions may not include icons either, which would explain why sometimes I see screenshots with icons when I don't have them. (Of course, people may setup their own icons too.)

I still don't understand why programs like FrostWire have no icon but then suddenly do though.

Thanks for the reply.

Does anyone know what the /usr/share/app-install/icons/ folder is for? Is it like an icon cache or something? Maybe a default in case an icon isn't shipped with a package? Thanks!

---

### Post by disturbedite on 2008-01-01
i don't know about gnome, but in kde (v3 a least) when a new program is installed and has a menu entry, the menu isn't updated to reflect it/show it until one reboots/logs out & logs back in.

---

