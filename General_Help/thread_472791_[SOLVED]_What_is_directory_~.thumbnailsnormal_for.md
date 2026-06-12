---
title: "[SOLVED] What is directory: ~/.thumbnails/normal/ for?"
date: 2007-06-13
forum: General Help
---

### Post by Interestedinthepenguin on 2007-06-13
I was looking through folders, and came upon ~/.thumbnails/normal/.  

What's the directory for?

---

### Post by HIFH on 2007-06-13
Its a cache gnome makes when you browse through your folders in nautilus. It contains thumbnail pictures of picture files you've previously looked at. It's there so that the next time you look at the same picture file, the thumbnail loads quicker. Similar to the thumb.db files in XP.

---

### Post by Interestedinthepenguin on 2007-06-13
Wow. it sure stores a lot.  I see thumbs of pics that I deleted a least a month and a half ago!

Thanks. :)

---

### Post by HIFH on 2007-06-13
After a wee [Google search](http://ubuntu.wordpress.com/2006/02/15/clean-up-old-thumbnails/), I found this which quite helpful

```

find ~/.thumbnails -type f -atime +7 -exec rm {} \;

```

That deletes all the files in the .thumbnails directory that haven't been accesed for seven days :)

---

### Post by Interestedinthepenguin on 2007-06-13
I've no problem with the old images, but, thanks again. :D

---

