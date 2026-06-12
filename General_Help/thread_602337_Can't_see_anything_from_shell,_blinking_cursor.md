---
title: "Can't see anything from shell, blinking cursor"
date: 2007-11-04
forum: General Help
---

### Post by jonah1980 on 2007-11-04
hi guys, i dunno if i've got the wrong resolution or what but when i press ctrl alt f1 etc or when my system does a scan after 30mounts i can't see anything. just get a blinking cursor in top corner of screen... recovery mode seems ok though, i get login prompt etc with that.

---

### Post by jonah1980 on 2007-11-04
ok fixed it, it's a gutsy bug where you have to remove the vga=791 or whatever from boot/grub/menu.lst

if you try set a resolution it breaks it...

---

### Post by ermannobonifazi on 2007-11-06
I discover a fix that let you still set vga=xxx

[http://www.blogmanno.com/?q=node/68](http://www.blogmanno.com/?q=node/68)

---

### Post by jonah1980 on 2007-11-08
cool thanks

---

