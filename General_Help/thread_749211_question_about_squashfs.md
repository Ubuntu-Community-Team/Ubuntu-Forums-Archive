---
title: "question about squashfs"
date: 2008-04-08
forum: General Help
---

### Post by markp1989 on 2008-04-08
[http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/](http://po-ru.com/diary/linux-liposuction-or-xubuntu-in-under-a-gig-on-the-eee-pc/)

i saw this link about making /usr in to a squashfs, and it saved me alot of space.

is it posible or wise to do it to other directorys, if so which ones

currently /var and /lib are the bigest folders. is it posible to make these 2 in  to a squashfs?

---

### Post by markp1989 on 2008-04-08
i tried doing it with /lib but it caused a kernal panic , il prob try it with /var at a later date

---

### Post by anaconda on 2008-04-08
I wouldn't make /var in to a squashfs.

Basically you can make any folder that doesnt change much to a squashfs one. 
but /var has among other things apt cache, and it changes a lot each time you update or install anything, so /var isnt that good idea..

---

### Post by markp1989 on 2008-04-27
> **anaconda said:**
> I wouldn't make /var in to a squashfs.

Basically you can make any folder that doesnt change much to a squashfs one. 
but /var has among other things apt cache, and it changes a lot each time you update or install anything, so /var isnt that good idea..

ok, so compresing /var is not a good idea,  what other folders can i add to a squashfs? maybe some subfolders of /var?

---

