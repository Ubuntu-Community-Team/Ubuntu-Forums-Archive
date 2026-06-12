---
title: "How to add a new MIME type?"
date: 2006-07-28
forum: General Help
---

### Post by tibbe on 2006-07-28
I would like to add a new MIME type "text/x-neko" for Neko source code. Neko files have a ".neko" file extension and I would like for them to be opened in gedit. I've already written a .lang syntax highlighting file for gtksourceview and placed it in $HOME/.gnome2/gtksourceview-1.0/language-specs and it can be selected manually from gedit's View -> Highlight Mode. I would prefer if it was possible to add the MIME type for a single user only (i.e. the settings need to go in $HOME) but if that's not possible I'm content with registering the MIME type globally.

---

### Post by josea.munoz on 2008-05-18
Hi,

U can create new mime types in /usr/share/mime. Follow [this link]("http://ubuntuforums.org/showthread.php?t=726230") as an example.

---

