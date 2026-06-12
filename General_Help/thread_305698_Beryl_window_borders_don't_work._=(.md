---
title: "Beryl window borders don't work. =("
date: 2006-11-23
forum: General Help
---

### Post by neoncode on 2006-11-23
I have an ati card and I'm running Kubuntu edgy. I manged to get Xgl running on the fglrx drivers with beryl, but the window borders and title bar don't appear. Everything else in beryl works flawlessly, Alt+Tab, Cube, the wavey menu's the Expose thing, window transparency. All of it. Except those window borders. Any help? ](*,)

---

### Post by d3v1ant_0n3 on 2006-11-23
How are you starting Beryl?

Have you tried running

emerald

in terminal? That *should* start up emerald (window decorator). I don't really know anything about XGL or ATI/fglrx stuff (apart from the whole "pain in the rear" thing.... sorry.

---

### Post by PriceChild on 2006-11-23
Make sure you start beryl with "beryl-manager" then selecting it from the notification area. Not starting with "beryl".

---

### Post by neoncode on 2006-11-23
Ah, sorry everyone, but I tried changing on of the settings in my xorg.conf(the composite one) But that made beryl not work at all, so I changed it back and then beryl worked perfectly, with window borders... :-k

Thanks to those that posted to help anyway. And yes I am using "beryl-manager" to launch it.

---

