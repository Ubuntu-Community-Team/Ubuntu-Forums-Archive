---
title: "Contents Samsung Smartphone"
date: 2018-08-16
forum: General Help
---

### Post by roosje69 on 2018-08-16
Hi,

Does anybody know, if it is possible to read the contents (files and photo's) of my Samsung Smartphone (s5) in Ubuntu 18.04 ?

Thanks for helping

Rosiey

---

### Post by oldos2er on 2018-08-16
Have you tried connecting it via USB? My s6 is automatically  mounted when I do this.

---

### Post by hmiersch on 2018-08-16
hm, gotta try that. so the next question is, where do i need to put my music to enable the music app to find and play it?

---

### Post by ajgreeny on 2018-08-16
Probably depends on the Android version, but there is a folder called Music in the android filesystem; try that.

---

### Post by Holger_Gehrke on 2018-08-16
It doesn't matter where you put your files. There's a service on Android called the media scanner. At boot, when a SD-card is inserted and whenever new files are put on an Android device the media scanner searches for media files and puts path, filename and metadata in a database. Media Players use that database to find files to play.

Holger

---

### Post by ajgreeny on 2018-08-16
Thanks for that info HG; I was unaware of that and it's very good to know.

---

