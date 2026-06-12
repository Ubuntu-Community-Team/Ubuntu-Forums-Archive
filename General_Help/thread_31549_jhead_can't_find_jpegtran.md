---
title: "jhead can't find jpegtran"
date: 2005-05-03
forum: General Help
---

### Post by 23meg on 2005-05-03
i've been looking for software to automatically rotate jpeg images according to their exif orientation tags. i haven't found a working native gnome app that does this (i'd love it if you can point me to one), so i decided to resort to my old trusty [jhead](http://www.sentex.net/~mwandel/jhead/) which i used with joy on windows. i downloaded the executable, typed "jhead -autorot [path]" to rotate my images, but i got the error 

> sh: jpegtran: command not found
Error : Problem executing specified command 

i think this means that jhead is looking for the jpegtran library, but can't locate it. the only instance of jpegtran i have is libjpegtran.so in my usr/lib/gthumb/modules folder, should i look for a way to point jhead to this? AFAIK, and as the jhead docs state, most linux distros come with jpegtran installed, but i think this isn't the case with Ubuntu.

frankly i haven't figured out a way to install jpegtran any other way; i'd very much appreciate help on doing this.

---

### Post by 23meg on 2005-05-03
solved this. jpegtran exists as part of the libjpeg-progs package. now jhead works like a charm :)

i also found the excellent [exiftran](http://packages.debian.org/testing/graphics/exiftran) command line utility that has everything built in for automagically rotating images according to exif orientation tags.

lessons learnt: when looking for something desperately in the repositories, remember to search in both descriptions and names in Synaptic. and remember to [search the debian repositories](http://www.debian.org/distrib/packages#search_packages).
 
all these packages (jhead, exiftran, jpegtran) are in the repos.

---

