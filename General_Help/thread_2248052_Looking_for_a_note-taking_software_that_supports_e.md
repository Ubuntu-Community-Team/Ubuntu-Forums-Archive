---
title: "Looking for a note-taking software that supports encryption, natively."
date: 2014-10-12
forum: General Help
---

### Post by markodd on 2014-10-12
Hey there,

As the title states, I'm looking for a note-taking software that supports encryption, natively.

I know I could use keepass, or a .txt encrypted with truecrypt or GPG, but that's not exactly what I'm looking for..

Does anyone have any software suggestions?

---

### Post by TheFu on 2014-10-12
Notecase pro
or
Geany with PGP encryption? [http://plugins.geany.org/geanypg.html](http://plugins.geany.org/geanypg.html)

I've used notecase (not the pro version) with encryption before the project died.
I use geany as an editor, but never tried the pgp plugin.
I use keepassx daily and it has my most important data inside, encrypted. Things like passport scans, insurance documentation scans, license keys, account numbers, in addition to passwords.

---

### Post by sudodus on 2014-10-12
Maybe one of the items in the following link's list?

[http://www.linuxlinks.com/article/20130322215851652/Diary.html](http://www.linuxlinks.com/article/20130322215851652/Diary.html)

My daughter has used Lifeograph

---

### Post by HermanAB on 2014-10-12
Maybe the simplest solution is to encrypt your whole disk drive, then you can use ordinary tools and rest assured everything will be encrypted.

---

### Post by TheFu on 2014-10-12
> **HermanAB said:**
> Maybe the simplest solution is to encrypt your whole disk drive, then you can use ordinary tools and rest assured everything will be encrypted.

Except when the system is .... running.

Also, on a multi-user system, root will still have complete access.

Even when HOME is encrypted per login, root (or anyone else assuming permissions are weak) can access these "encrypted" files when the user is logged in. Hardly ideal - but it is easier and better than nothing, I suppose.

Some HDDs have on-device encryption too - if we are thinking outside the normal "box."

of course, whenever encryption is involved, backups become 10x more important, as we all know.

---

### Post by markodd on 2014-10-12
> **TheFu said:**
> Notecase proorGeany with PGP encryption? [http://plugins.geany.org/geanypg.html](http://plugins.geany.org/geanypg.html)I've used notecase (not the pro version) with encryption before the project died.I use geany as an editor, but never tried the pgp plugin.I use keepassx daily and it has my most important data inside, encrypted. Things like passport scans, insurance documentation scans, license keys, account numbers, in addition to passwords.Notecase does seem very interesting.. Sadly it's paying software, but I'll give the trial a try and see if it's worth it. Thank you TheFu!> **sudodus said:**
> Maybe one of the items in the following link's list?[http://www.linuxlinks.com/article/20130322215851652/Diary.html](http://www.linuxlinks.com/article/20130322215851652/Diary.html)My daughter has used LifeographThx for the link, but sadly, none of those are what I'm looking for :D> **HermanAB said:**
> Maybe the simplest solution is to encrypt your whole disk drive, then you can use ordinary tools and rest assured everything will be encrypted.I do have my system fully encrypted, but it still doesn't solve the problem if I want to upload it somewhere, or take it with me on a pen, etc.

---

### Post by tgalati4 on 2014-10-13
There is some discussion about adding encryption to *zim*.  In the meantime, you can set up a script and just use an encrypted folder.  [https://github.com/jaap-karssenberg/zim-wiki/wiki/Store-notebooks-in-an-encrypted-folder](https://github.com/jaap-karssenberg/zim-wiki/wiki/Store-notebooks-in-an-encrypted-folder)

---

