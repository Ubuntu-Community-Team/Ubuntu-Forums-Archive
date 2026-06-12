---
title: "Need help installing .tar program without internet"
date: 2007-07-09
forum: General Help
---

### Post by thesikness on 2007-07-09
The internet on my ubuntu computer is currently down. I am transferring the entire Spawn series from a windows computer to my ubuntu computer with a portable hard drive. I am also trying to install a certain picture viewer to view the comics on ubuntu. It's called ComicViewer and it's for linux. I downloaded it onto windows because of my internet problem on ubuntu. Then i transferred it to my ubuntu computer with a flash drive. I need help installing comicviewer though without the internet. Any help is greatly appreciated. Thanks and peace...

---

### Post by vineethbs on 2007-07-10
hi , 
i have also downloaded comicviewer from [http://sourceforge.net/projects/comicviewer/](http://sourceforge.net/projects/comicviewer/) 
is this the same file you downloaded ? 

assuming it is so, and you have transferred the file onto your favourite directory

say ~/comics/

for bzip2 compressed files : 
tar jxf comicviewer_alpha3.tar.bz2

for gzip use tar zxf

[explanation of switches , x for extract, f for file, a way to remember]

You also need to have java installed (for java installation help [https://help.ubuntu.com/community/Java](https://help.ubuntu.com/community/Java))

execute as 
java -jar ComicViewer.jar

I haven't used comicviewer before, it seems like it is more geared towards reading online comics.

---

