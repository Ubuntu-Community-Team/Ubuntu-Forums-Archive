---
title: "Iam tryin to install Vlc player that plays Dvds On Lubuntu 18.04 32bit"
date: 2020-09-24
forum: General Help
---

### Post by mudiakoghene on 2020-09-24
when I type : sudo apt-get install vlc i get
E: Malformed line 1 in source list /etc/apt/sources.list.d/libdvdcss.list (type)
E: Malformed line 1 in source list /etc/apt/sources.list.d/libdvdread7.list (type)
E: The list of sources could not be read.

i get the same thing when i type : sudo apt-get install vlc
E: Malformed line 1 in source list /etc/apt/sources.list.d/libdvdcss.list (type)
E: Malformed line 1 in source list /etc/apt/sources.list.d/libdvdread7.list (type)
E: The list of sources could not be read.

---

### Post by gdesilva on 2020-09-24
I think the issue is that you do not have libdvdcss package installed - check out the instructions below

[https://itsfoss.com/play-dvd-ubuntu-1310/](https://itsfoss.com/play-dvd-ubuntu-1310/)

---

### Post by joris_donders2 on 2020-09-25
Question is of course if there is a 32 bits version of VLC ....

---

### Post by scorp123 on 2020-09-25
> **mudiakoghene said:**
>  E: Malformed line 1 in source list /etc/apt/sources.list.d/libdvdcss.list (type)
E: Malformed line 1 in source list /etc/apt/sources.list.d/libdvdread7.list (type)
E: The list of sources could not be read.


The error message is obvious, no? "**Malformed line 1** in source list /etc/apt/sources.list.d/libdvdcss.list"

So please post the content of that file "/etc/apt/sources.list.d/libdvdcss.list". Chances are you have a malformed line and invalid syntax in there, just as the error message says you do.

---

