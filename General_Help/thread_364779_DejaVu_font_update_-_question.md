---
title: "DejaVu font update - question"
date: 2007-02-18
forum: General Help
---

### Post by Books on 2007-02-18
[SIZE="2"]The DejaVu fonts project released their latest version 2.15 today (February 18, 2007). The current package for Edgy is ttf-dejavu 2.7-2 which is old. To install the new fonts is it going to cause a problem if I go into KDE's Font Installer and load up the .ttf's? Or would that conflict with the ttf-dejavu package?

Links:
[http://en.wikipedia.org/wiki/DejaVu_fonts]("http://en.wikipedia.org/wiki/DejaVu_fonts")
[http://dejavu.sourceforge.net/]("http://dejavu.sourceforge.net/")
[http://sourceforge.net/projects/dejavu/]("http://sourceforge.net/projects/dejavu/")

Thank you!!!

Books[/SIZE]

---

### Post by fragos on 2007-02-18
The Dejavu ttf fonts installed by ubuntu don't have version numbers in the names so you should just be able to replace the existing ttf files in /usr/share/fonts/truetype/ttf-dejavu.  When your done copying ttf files run "sudo fc-cache -fv" to make sure they can be seen by applications.

---

### Post by Books on 2007-02-19
> **fragos said:**
> The Dejavu ttf fonts installed by ubuntu don't have version numbers in the names so you should just be able to replace the existing ttf files in /usr/share/fonts/truetype/ttf-dejavu.  When your done copying ttf files run "sudo fc-cache -fv" to make sure they can be seen by applications.
Thanks, fragos! It worked, much appreciated.

For posterity of the thread, let me add I tried to install the new font versions over the old ones using KDE's Font Installer but it didn't update the files. I typed "kdesu konqueror" and copied over the files in root mode, then used the "sudo fc-cache -fv"... and the new characters are showing up now.

Again, thanks!

Books

---

