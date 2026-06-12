---
title: "[SOLVED] Nautilus Script: Extract Here, No Directories"
date: 2008-02-07
forum: General Help
---

### Post by arigram on 2008-02-07
I would like to have a script similar to the Extract Here option of the Nautilus pop-up menu, but without creating directories from the archive. It would really speed up my workflow.
I am not a programmer and not that familiar with the system, so please be gentle.

---

### Post by kidders on 2008-02-08
Hi there,

Naturally, the utilities Nautilus uses to extract archives don't have this option, because there would be no sensible way to handle identical filenames. You'll have to decide on the approach you want to take to that eventuality, and flatten the directory structure manually.

---

### Post by arigram on 2008-02-08
I thought it would have been an easy affair!
I mean, link a CLI command to extract all select files plus an argument to not create directories. I just don't know how to make it happen.

Actually "Archive Manager", does have the option to extract without creating directories.
I download image archives in zip format from a news agency. Each archive file contains a directory which includes the image and a text file description.
So far, I have used two approaches to this:

1) Select all zip files, extract to the temp directory, then with a list view and high magnification, collapse each folder by hand and study the image before selecting if I use it or not.
2) Select all zip files, extract to the temp directory, select all extracted folders and make a new archive, then finally open the Archive Manager GUI with that archive and with the option deselected, extract the files.

Both are too much hassle as I d/l dozens of files daily and it could have been much quicker with a simple pop up menu option. I could do it via console but that also breaks the workflow.

---

### Post by kidders on 2008-02-09
> a CLI command to extract all select files plus an argument to not create directoriesActually, in the case of zip archives, you can use unzip's "-j" modifier to discard path information. Sorry for jumping to conclusions!

---

### Post by arigram on 2008-02-09
> **kidders said:**
> Actually, in the case of zip archives, you can use unzip's "-j" modifier to discard path information. Sorry for jumping to conclusions!

Thank you, but how do I make that part of Nautilus pop up menu?

---

### Post by kidders on 2008-02-10
There are plenty of threads on that subject, for example this one: [http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

---

### Post by arigram on 2008-02-10
> **kidders said:**
> There are plenty of threads on that subject, for example this one: [http://ubuntuforums.org/showthread.php?t=87369](http://ubuntuforums.org/showthread.php?t=87369)

Thank you, I've seen scripts before, but I am no programmer or Linux veteran and don't understand them or know how to make a simple script of my own.

---

### Post by arigram on 2008-02-16
I've found this thread:
[http://ubuntuforums.org/showthread.php?t=417978&highlight=move+undo](http://ubuntuforums.org/showthread.php?t=417978&highlight=move+undo)
which was exactly what I was looking for!
I haven't gotten it working right yet, but I will...

---

### Post by FALKER on 2008-02-26
```

#!/bin/bash
#
# nautilus-extract-zips
unzip \*.zip

```

Save as whatever you like in ~/.gnome2/nautilus-scripts/ , make it executable and restart nautilus. Rightclick in folder with zips and choose scripts->name of the script. You could also make another one with the -j argument, but that was not the problem for me and could result in a mess.

---

