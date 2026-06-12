---
title: "Nautilus can't use custom file-type handler"
date: 2015-11-17
forum: General Help
---

### Post by jeff63 on 2015-11-17
My work uses a specialised file format. I wrote a small script that handles opening these files in a useful way.

I then created a MIME type and associated my script with these files according to [this guide]("https://help.gnome.org/admin/system-admin-guide/stable/mime-types-custom-user.html.en"). This seemed to work OK - xdg/gvfs/gnome-open work entirely as intended. Unfortunately, double-clicking a file in Nautilus doesn't work at all. I get:


'Could not display "[FILENAME]". There is no application installed for [MYTYPE] files. Do you want to search for an application to open this file?'

Here [MYTYPE] is the name I defined while setting up the MIME type, so it's definitely seeing that at least. What did I do wrong?

On a related note, why, when you right-click and do "Open with other application" is there no option for an executable not on the list? That's possibly the most obviously desirable feature ever.

---

### Post by jeff63 on 2015-11-17
In case it matters, I'm using gnome-flashback

---

### Post by mc4man on 2015-11-17
If you created a .desktop that has Exec=yourscript then to make available in the context menu it has to end in %<a letter>. The most common letters would be  f, F, u, U
So for example if script was in a bin folder in $PATH and named test1 - 
Exec=test1 %f
otherwise if not in $PATH then 
Exec=/pathto/test1 %f

If after doing that nautilus still doesn't work on a d. click on filetype then go r. click on file > properties > open with & locate your .desktop. Then set as default

---

### Post by jeff63 on 2015-11-19
I needed the %F, and I also needed a small rewrite of the script I wrote, for reasons I don't entirely understand.

Anyway, it works now.  Thanks.

---

