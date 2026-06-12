---
title: "[SOLVED] Where icons live?"
date: 2008-06-28
forum: General Help
---

### Post by Darkade on 2008-06-28
Hi! I like to change default icons of things LOL and I've find that sometimes certain Icon locations are just impossible to find... well kindda.
So I've come up with this four locations for icons and I've make links to them in ~/.icons/  but are there other places to look for icons?

```

~/.icons/
/usr/share/app-install/icons/
/usr/share/icons
/usr/share/pixmaps

```

---

### Post by nhandler on 2008-06-29
The icons for .desktop files (the things in the Applications menu) are meant to go in /usr/share/pixmaps. There is an easy way to find all of the icons on your computer. You can use find to locate all .xpm files. To do this, type 'find / *.xpm' in a terminal. That will give you a list of all .xpm files on your computer. You can easily modify that command to find .png or .bmp or any other type of files you want. You can also restrict the search to a specific directory by replacing the '/' with the path of the directory.

---

### Post by Darkade on 2008-06-29
Thanks, I think I'll make a list or something :D

---

