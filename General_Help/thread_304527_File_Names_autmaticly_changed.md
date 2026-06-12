---
title: "File Names autmaticly changed"
date: 2006-11-21
forum: General Help
---

### Post by Dr Small on 2006-11-21
Ok. So I wrote some of my things from Windows to disc, and then copied the disc onto my linux, and when I go and browse some of the files, the names of the files, that had longer names, now shorten, like this:

phpmya~1

where originally, it was: phpmyadmin
Does anyone know the cause of this, and if there is a way, that somehow I can turn something off, so it doesn't shorten and rename my files, as it would really mess things up, if I had a php program to upload to the web, for instance, the different file names would mess things up.

Any solution for this?

Dr Small

---

### Post by meng on 2006-11-21
I suspect the issue is at the Windows end, at the point you burned the disc. If it maintained long filenames, it must have only been readable in another windows system. Windows has traditionally been limited to 8.3 filenames (a hangover from DOS), and phpmya~1 is the usual Windows way of abbreviating longer names. I wonder if a different burning program in Windows might do the trick?

---

### Post by Dr Small on 2006-11-21
Ok. thanks.
Now that I think about it, that may have been the problem.
Glad to know it isn't Linux :)

Thanks.

Dr Small

---

### Post by meng on 2006-11-21
Another thing to consider is if burning continues to be a problem, some sort of archiver (zip, tar) might be better suited to maintain names. But I'm just guessing, since I don't use Windows anymore.

---

