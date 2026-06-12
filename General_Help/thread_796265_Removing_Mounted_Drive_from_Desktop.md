---
title: "Removing Mounted Drive from Desktop"
date: 2008-05-16
forum: General Help
---

### Post by alkizz on 2008-05-16
Hello all..

I have a hhd mounted to /home/alkizz/storage but it also shows up on the desktop. I don't want any icons on my desktop is there any way to remove that icon without unmounting the drive?

I went to gconf-editor and unchecked volumes_visible from the app-nautilis-desktop location

is there something I'm missing?.

Thank you

---

### Post by hermes0710 on 2008-05-16
Did you start gconf-editor as root (sudo gconf-editor)? If yes then the changes are only applied to the root user. Start it normally and re-apply them

---

### Post by alkizz on 2008-05-16
damn i feel dumb now

thank you!

---

### Post by hermes0710 on 2008-05-16
Glad i helped (happened to me too :p )

---

### Post by kadafi69 on 2008-05-23
ive just tried this, however, when i restart it the icons are still there, yet the config file remains in its edited state. any ideas?

---

### Post by david_kt on 2008-06-12
> **kadafi69 said:**
> ive just tried this, however, when i restart it the icons are still there, yet the config file remains in its edited state. any ideas?

Which ubuntu version you are using? How did you run gconf-editor?

DK

---

