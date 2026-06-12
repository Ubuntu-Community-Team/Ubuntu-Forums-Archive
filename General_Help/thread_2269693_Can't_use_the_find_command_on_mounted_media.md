---
title: "Can't use the find command on mounted media"
date: 2015-03-17
forum: General Help
---

### Post by J_Me on 2015-03-17
I'm trying to change permissions on many files inside sub directories using find, it will work if the files are in my home directory but not on mounted media.
```
This works
find /home/me/Downloads/fo -name "*.mp3" -exec chmod 400 '{}' \;
But not this
find /media/5764-3857/here -name "*.mp3" -exec chmod 400 '{}' \;
```I suppose I could move all these files to my home directory but it's a large folder.
Any ideas.

---

### Post by Elfy on 2015-03-17
*Thread moved to **General Help**.*

/media/5764-3857/here is this media linux? 

Looks like a windowsesque type UUID - chmod's not going to work afaik

---

### Post by J_Me on 2015-03-17
It's vfat formatted, so it looks like I'm stuffed.
I'll mark this thread as solved.
Thanks for the reply

---

### Post by Elfy on 2015-03-17
Long time since I used or had anything to do with fat files tbh. Last time I set permissions with fstab, but that would have been partition wide - certainly not just for a specific filetype.

---

