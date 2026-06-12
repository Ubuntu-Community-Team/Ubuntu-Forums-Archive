---
title: "Banshee"
date: 2008-07-01
forum: General Help
---

### Post by Trzone on 2008-07-01
I downloaded the latest tarball of banshee, does anyone know how to compile and or install that?

---

### Post by skatemyturf on 2008-07-01
> **Trzone said:**
> I downloaded the latest tarball of banshee, does anyone know how to compile and or install that?

I am doing this assuming that the tarball is saved to your desktop if it isn't find it and move it there.

right click on your tarball and press extract here this unpack the tarball. Then run terminal and type:

cd Desktop (gets you to the desktop)
ls (shows the desktop find the file that has been pre compiled by extract here)
cd the pre compile/unpacked file do this by pressing cd and then typing your file name

then type ./configure 

after the text scrolls 

type make 

after more text simply type sudo make install 

then you are done

---

### Post by Trzone on 2008-07-01
When i do ./configure, it gives me this error 
configure: error: C compiler cannot create executables
See `config.log' for more details.

and i will attach the config.log file

---

### Post by skatemyturf on 2008-07-01
> **Trzone said:**
> When i do ./configure, it gives me this error 
configure: error: C compiler cannot create executables
See `config.log' for more details.

and i will attach the config.log file

sorry no idea about this i had the same problema few weeks a go unfortunately hadtoleave it the onlything i suggest is searching for c compiler in package manager

---

### Post by Trzone on 2008-07-01
I fixed the problem, i searched for gcc, found gcc-4.2 and installed all that was suggested to install.  And at the end it says it can't find 

No package 'gdk-x11-2.0' found


Hmm i will prevail! haha

Found these source lists on one of the posts, seems to be working fine

---

