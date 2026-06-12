---
title: "Bluk rename"
date: 2007-07-16
forum: General Help
---

### Post by EdUbun on 2007-07-16
Goodday. In windows there is a utility bulk rename. I was wondering what I can use for this under Ubuntu. I want to be able to rename photo files which are copied from the camera to a folder. I want to be able to rename the file to a number (counting) with pre and suffix and the extension (to small letters instead of caps)

---

### Post by strabes on 2007-07-16
[http://thunar.xfce.org/pwiki/documentation/bulk_renamer](http://thunar.xfce.org/pwiki/documentation/bulk_renamer)

or if you use kde: [http://www.kde-apps.org/content/show.php?content=9876](http://www.kde-apps.org/content/show.php?content=9876)


By the way, I found those two links with a simple google search of "linux bulk rename" and looking at the first result.

---

### Post by aysiu on 2007-07-16
There's a bulk rename utility in Windows? I didn't know there was. Wow.

I'd highly recommend KRename, which can be found in the software repositories.

---

### Post by EdUbun on 2007-07-16
lol not in windows itself (well in vista there is a minor one) I meant [http://www.bulkrenameutility.co.uk/Main_Intro.php](http://www.bulkrenameutility.co.uk/Main_Intro.php)

I don't have kde

---

### Post by dagnabit dang doohickey on 2007-07-16
There's also [gprename]("http://gprename.sourceforge.net/").

---

### Post by strabes on 2007-07-16
You can use kde apps in gnome, but you should just install "kde-core" first: ```
sudo aptitude install kde-core krename
```

---

### Post by aysiu on 2007-07-16
You don't need KDE. You don't even need *kde-core*.

Just install KRename itself. The package manager will take care of the other dependencies needed. KRename can be run in Gnome.

---

