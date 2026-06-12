---
title: "how do i add the repository for the libdvdcss"
date: 2005-08-07
forum: General Help
---

### Post by KezzerDrix on 2005-08-07
help please
how do i add the repository for the libdvdcss, and the win32 codecs

---

### Post by jasmuz on 2005-08-07
Open a terminal

type sudo gedit /etc/apt/sources.list

add these two lines to it:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Save and close, type sudo apt-get update 
and then sudo apt-get install libdvdcss w32codecs

---

### Post by KezzerDrix on 2005-08-07
nothing, your source installed and updated but no libdvdcss

edit: got it to work thanks :)

---

### Post by jamesrw on 2005-08-21
[QUOTE=jasmuz]Open a terminal

type sudo gedit /etc/apt/sources.list

add these two lines to it:

deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-backports main universe multiverse restricted
deb [ftp://ftp2.caliu.info/backports/](ftp://ftp2.caliu.info/backports/) hoary-extras main universe multiverse restricted

Save and close, type sudo apt-get update 
and then sudo apt-get install libdvdcss w32codecs[/QUOTE]

anyway other mirrors for that? seems to be down.

---

### Post by rudiz on 2005-08-21
[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

