---
title: "[SOLVED] Help resizing photos in a folder"
date: 2008-06-22
forum: General Help
---

### Post by seventhc on 2008-06-22
Hi everyone,
I sort of remember reading about this on this forum, but searching for it hasn't produced the results I was looking for.
Here is the task,
I currently have a folder that is 697 MB containing 387 photos. I took all of these pics on a 12 mega pixel setting and would like to resize them to meet web standards. I remember seeing a command that would do this for me as opposed to resizing every photo individually. I am not sure if I am remembering correctly, but if anyone knows of this command, please let me know. I guess I would like them to be 72 dpi.
As for the size they are now, they range from 1.2 MB, to 4.4 MB and I would like to get them to a size more suitable for emailing friends. I know I can do it in Gimp, but I would really like to do them all at once.
Any suggesstions, commands?
Thank you in advance.

seventhc

---

### Post by ShodanjoDM on 2008-06-22
How about installing nautilus image converter? You can use it to batch resize your images.

```
sudo aptitude install nautilus-image-converter
```

then:

```
killall nautilus
```

To restart nautilus without having to logout and log back in again. It might be better to do the latter though.

---

### Post by seventhc on 2008-06-22
Thanks for the quick reply, I will try that now.
will post back :)

---

### Post by seventhc on 2008-06-22
Thanks, that worked. :)

---

### Post by ShodanjoDM on 2008-06-22
You're welcome. Glad I can help :D

---

### Post by seventhc on 2008-06-22
-rm-

---

