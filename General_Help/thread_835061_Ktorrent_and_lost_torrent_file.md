---
title: "Ktorrent and lost torrent file"
date: 2008-06-20
forum: General Help
---

### Post by griz on 2008-06-20
Hi all,
I've started downloading a large collection of public domain movies, about 30G worth, on Vista, have now dual booted my laptop and thought that I'd finish the download off with Ktorrent.  Problem is, I've lost the original torrent file (not even all that sure if I actually downloaded it or just opened it from the net).  Is there any way to restart the downloads in Ktorrent?

Griz.

---

### Post by Zorael on 2008-06-20
Try booting from Vista and see if your torrent application has some way to export that torrent; for instance, I believe Azureus has this functionality.

If it does, save it someplace, boot back into linux, enable the Ktorrent plugin **Import**. Then File -> Import existing download, point it to the right paths. Should work.

edit: Even if you just opened it from a web link, it *should* still be saved *someplace*. Else that torrent application you used in Vista wouldn't be able to remember it upon restart of the program itself. Either it saved the file in its own temporary directory (likely under /Documents and Settings/user/Application Data/application name), or in its own database. In the latter case you'd need to Export it somehow.

---

### Post by griz on 2008-06-20
Thanks for the reply.  I never thought of that.  Will try it out later.

Griz.

---

### Post by zxscooby on 2008-06-20
If it is listed under the uploads tab you can resume it from there as well.

---

