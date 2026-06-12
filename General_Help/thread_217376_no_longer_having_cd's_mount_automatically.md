---
title: "no longer having cd's mount automatically"
date: 2006-07-17
forum: General Help
---

### Post by Polygon on 2006-07-17
recently ive come to find that my cd's and dvd's that i put in my drive to not mount automatically, or they are mounted but there is no icon on my desktop of the cd in the drive. (im not sure which)

usually if i go to computer > and then any one of the cd/dvd drives, it says it cannot be mounted for X reason... but then if i go to /media/cdrom0 or 1 i can view the contents of the cd there

how do i make it so it shows an icon on the desktop and i can access the drive through computer > drive again?

---

### Post by Anduu on 2006-07-17
Open gconf-editor and go to apps/nautilus/desktop and make sure "volumes_visible" is checked

---

### Post by Polygon on 2006-07-17
yeah, that is checked, and i just put a cd in there and no icon appeared on my desktop.

---

