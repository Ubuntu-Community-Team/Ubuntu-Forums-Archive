---
title: "Problem with samba"
date: 2016-06-22
forum: General Help
---

### Post by Leonid_Kopylov on 2016-06-22
I'm trying to mount disk shared by AirPort Extreme. With fedora  - i can mount it without any problem (I mount it as a guest)
But in ubuntu i have an error, any help would appreciated

$ sudo mount -t cifs -o guest //10.0.1.1/Media /mnt
mount error(13): Permission denied

exactly the same works on fedora without any errors. am i missing something?

---

### Post by ventrical on 2016-06-22
I have had problems with samba in the past.

I think /Media/ has to be granted a share or root permission or at least set up that way. But  I would try this and then I would get 'groups' problem  and could not configure it  to work.. at least not with nautilus.

Regards..

---

