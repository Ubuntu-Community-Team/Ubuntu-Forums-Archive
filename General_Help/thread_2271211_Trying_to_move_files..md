---
title: "Trying to move files."
date: 2015-03-28
forum: General Help
---

### Post by Arunomi on 2015-03-28
Hi I'm trying to move files from 99 sub dir's to the current.

I found this command but i cant get it to work.

```
find . -type f -mindepth 2 -exec mv -i -- {} . \;
```

What am i doing wrong?

---

### Post by dino99 on 2015-03-28
some examples using paths  [http://askubuntu.com/questions/214560/how-to-move-multiple-files-at-once-to-a-specific-destination-directory](http://askubuntu.com/questions/214560/how-to-move-multiple-files-at-once-to-a-specific-destination-directory)
or [http://ubuntuforums.org/showthread.php?t=2240915](http://ubuntuforums.org/showthread.php?t=2240915)
or [http://superuser.com/questions/658075/how-do-i-move-files-out-of-nested-subdirectories-into-another-folder-in-ubuntu](http://superuser.com/questions/658075/how-do-i-move-files-out-of-nested-subdirectories-into-another-folder-in-ubuntu)

myself prefer the drag & drop from file manager because i does not like bad surprise when using blindly bash command ; but 99 subdirs is a lot

---

### Post by Holger_Gehrke on 2015-03-28
The characters '{' and '}' are not only special to find (which will replace them with the names of the files it finds) but also to the shell. To make sure the shell does not remove them you have to escape them by prefacing them with '\', just like the ';' at the end of the command. So it should be:
```

find . -type f -mindepth 2 -exec mv -i -- **\**{**\**} . \;

```

---

### Post by Arunomi on 2015-03-28
The problems is that I can't get find to work in my current dir.

even when i try  
```
find /media/arunomi/Backup/Folder10 -mindepth 1 -type f -print0
```

---

### Post by Arunomi on 2015-03-28
Found the problem there where nothing in the subfolders #-o

---

### Post by bapoumba on 2015-03-28
You may want to mark your thread as solved anyway :)

---

