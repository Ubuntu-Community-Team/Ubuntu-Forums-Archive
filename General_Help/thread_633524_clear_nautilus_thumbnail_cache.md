---
title: "clear nautilus thumbnail cache"
date: 2007-12-06
forum: General Help
---

### Post by kefurd06 on 2007-12-06
in another thread i mentioned that my photos were damaged and i managed to restore some backups. problem now is the thumbnails for the backups look like the damaged ones that i deleted (i guess because the file names and folders are all identical)

how do i clear the nautilus thumbnail cache? 

it may be worth noting that i have the indexing service generate thumbnails.

also, even after opening the photo, the nautilus thumbnail is still wrong.

thanks in advance

---

### Post by yabbadabbadont on 2007-12-06
You need to remove the files and folders in the hidden ".thumbnails" directory.  Note that the name starts with a period, which is what makes it hidden.  Just show hidden files in nautilus and then remove the .thumbnails directory in your home directory.  It will be recreated automatically the next time you view thumbnail images.

---

### Post by kefurd06 on 2007-12-06
took a few minutes but yes it started recreating thumbnails. thanks!

---

### Post by ^rooker on 2007-12-28
Just wanted to mention that the ".thumbnails" directory is actually "~/.thumbnails" - so it's in your home folder and not in the folder where the images are located (as I thought at first).

(Hope this helps future readers/finders of this thread)

---

### Post by yabbadabbadont on 2007-12-29
> **^rooker said:**
> Just wanted to mention that the ".thumbnails" directory is actually "~/.thumbnails" - so it's in your home folder and not in the folder where the images are located (as I thought at first).

(Hope this helps future readers/finders of this thread)

You just didn't read my reply closely enough...  ;)

> Just show hidden files in nautilus and then remove the .thumbnails directory **in your home directory.**

---

