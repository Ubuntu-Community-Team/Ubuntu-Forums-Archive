---
title: "listview column height issue - gnomishgray"
date: 2016-05-20
forum: General Help
---

### Post by sameermw on 2016-05-20
I am using GnomishGray theme on Ubuntu 16.04. [http://gnome-look.org/content/show.php?content=149193](http://gnome-look.org/content/show.php?content=149193)
When I switch to listview to in nautilus and nemo listview column height looks weird. 
I don't know the location to change the height of the column size in theme settings file. support me to identify the settings.

[IMG]http://i.stack.imgur.com/MZ69R.png[/IMG]

---

### Post by Dennis N on 2016-05-20
The theme web site shows these dependencies:

> *** Current Dependencies ***

GTK3 = 3.12.X (may not work with versions < 3.8)
gtk2-engines-murrine >= 0.98.1.1 (for GTK2)
gtk2-engines-pixbuf >= 2.24.10 (for GTK2)
Metacity >= 2.34 (for GTK2)

Since this theme is intended for GTK3 version 3.12, and Ubuntu 16.04 uses GTK3 version 3.18, the theme may not work correctly. For best compatability, look for a theme which uses GTK3 version 3.18.

---

### Post by sameermw on 2016-05-21
> **Dennis N said:**
> The theme web site shows these dependencies:Since this theme is intended for GTK3 version 3.12, and Ubuntu 16.04 uses GTK3 version 3.18, the theme may not work correctly. For best compatability, look for a theme which uses GTK3 version 3.18.I also saw that. but theme works perfectly without any other error but the listview issue. That's why I try to figure it out. I love this theme.

---

