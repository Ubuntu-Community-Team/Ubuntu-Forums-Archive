---
title: "Problem with an icon theme"
date: 2008-05-26
forum: General Help
---

### Post by orlox on 2008-05-26
Hi!

I just downloaded this icon theme:

[gartoon icon theme]("http://art.gnome.org/themes/icon/1001")

I really liked it, but I can't get folders to show accordingly. They just appear with ugly gnome standard icons...

Doees anyone know a fix to this??

---

### Post by BandD on 2008-05-26
I imagine the problem lies in the file names contained in the icon theme.  The easiest thing to do is navigate to the gnome icon theme (/usr/share/icons/gnome) and open up the "scalable" folder, then the "places" folder within scalabe (/usr/share/icons/gnome/scalable/places).  Notice which file names are the folder icon.  Leave that open.

Now navigate to where you saved gartoon (probably /home/USER_NAME/.icons/gartoon).  Go through all the places folders (there will probably be different size folders, you'll need to change the file names in EACH size folder), and add links to the folder icon you wish within gartoon with the missing file names you notice from the gnome theme.

Otherwise you'll just have to wait for the author to update the file names.

Hopefully that makes sense.  If not let me know and I'll write back, I'm short on time at the moment.

---

### Post by chrisccoulson on 2008-05-26
Yes, the problem is that a lot of the icon naming was changed for GNOME 2.22 as per the freedesktop spec, and icon developers need to catch up.

Why are you using such an antiquated version of Gartoon though? There is a much more up-to-date version (which actually works) [here]("http://www.gnome-look.org/content/show.php/Gartoon+Redux?content=74841"):)

---

