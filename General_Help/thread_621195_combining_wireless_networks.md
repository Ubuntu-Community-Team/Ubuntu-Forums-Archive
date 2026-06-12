---
title: "combining wireless networks"
date: 2007-11-23
forum: General Help
---

### Post by jcrnan on 2007-11-23
Does anyone know if there is a way to connect to several wireless networks at once using all their added toghether network speed?

I found a program that does this for windows, but I have no clue how to do it in Linux. I'm running 7.10. Wireless card is an intel integrated card and it works perfectly with 7.10.

---

### Post by mellowd on 2007-11-23
what are you trying to acomplish? Genreally the wan link on the other side of the link will be a lot slower than the local of one wireless network already

---

### Post by jcrnan on 2007-12-13
I'm trying to connect to several wireless networks at once to use the bandwitdh of all of them for surfing, downloadin, uploading, etc.

---

### Post by Ocxic on 2007-12-13
yes and no, I myself have been trying to do this..

I've discovered that if you manually configure your network interfaces, instead of using the network manager, it will activate and i THINK will use both

the only other way I've ever seen to do this would be to setup a separate computer as a router with Ubuntu, and configure the router to use more then one networking interface at the same time.

Please note that you will need separate network cards for each connection to each wireless network, you cannot use one wireless card to use 2 or more different wireless networks at the same time. Also note that this will not speed up internet or general network use, as you will only use one network card for most of your "internet/networking" needs, however this will speed up such things like torrents or downloads that use multiple connections at one time to download a file, and will not speed up downloads that you would normally get from say an internet site, or limewire type download.

---

### Post by jcrnan on 2007-12-14
Ocxic: Sure you need multiple network cards? that is what I also thought until recently when I found the windows program claiming to not need two wireless cards. I testet it briefly on another pc and it seemed to work as far as I could see.

---

### Post by Ocxic on 2007-12-14
well I could be wrong but I've never seen such a program for linux tho.

---

