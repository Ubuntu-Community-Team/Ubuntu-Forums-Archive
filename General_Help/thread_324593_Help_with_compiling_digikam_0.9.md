---
title: "Help with compiling digikam 0.9"
date: 2006-12-24
forum: General Help
---

### Post by beefcurry on 2006-12-24
After waiting for a while and unable to find any debs for digikam 0.9 i decided to compile it myself from the tarball.

Everything went fine during ```
./configure --prefix=/usr
``` 

since i had ```
sudo apt-get build-dep digikam
```

But one problem was it kept on saying

```
-- digiKam configure results -------------------
-- sqlite3 found.................. YES
-- libgphoto2 found............... YES
-- libkipi found.................. YES
-- libtiff found.................. YES
-- libpng found................... YES
-- lcms found..................... YES
-- Exiv2 library found............ NO

digiKam needs Exiv2 library. You need to install Exiv2 first
Exiv2 website is at http://www.exiv2.org

```

From Synaptic I have installed everything related to Exiv2, its not the newest version but i suppose the one in the repo's should still work. But since it didnt i tried to compile the Exiv2 myself, but that didnt work as well.

Anyone care to make a howto on how to install digikam 0.9? or be even more kind as to produce a .deb file? (smack me if one has already been created)

---

### Post by po0f on 2006-12-24
beefcurry,

Did you install [libexiv2-dev](http://packages.ubuntu.com/edgy/libdevel/libexiv2-dev)?  And if you are custom compiling software, I really recommend you don't configure it with --prefix=/usr, /usr/local will do just fine.

---

### Post by beefcurry on 2006-12-24
thanks for the reply, i did install libexiv2-dev.

---

### Post by po0f on 2006-12-24
beefcurry,

I just read the README.  Looks like you need Exiv2 >=0.12, which means you'll have to compile this yourself.  What were the problems you were having with it again?  :)

---

### Post by beefcurry on 2006-12-24
I dont seem to have a problem when i use ./configure , however the make command does not work, it just seems it cannot compile properly, and because of that make install dosnt seem to work ...

---

