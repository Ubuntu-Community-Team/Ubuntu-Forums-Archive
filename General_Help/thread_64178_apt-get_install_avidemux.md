---
title: "apt-get install avidemux"
date: 2005-09-10
forum: General Help
---

### Post by abmcr on 2005-09-10
I want install avidemux: i have, in my sources.list, this lines:

deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) stable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) unstable main
deb [ftp://ftp.nerim.net/debian-marillat](ftp://ftp.nerim.net/debian-marillat) testing main

but i get an error with apt-get update
Impossibile ottenere [ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/stable/main/binary-i386/Packages.gz)  Somma MD5 non corrispondente
Impossibile ottenere [ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz](ftp://ftp.nerim.net/debian-marillat/dists/testing/main/binary-i386/Packages.gz)  Somma MD5 non corrispondente
Lettura della lista dei pacchetti in corso... Fatto
W: Impossibile controllare la lista dei pacchetti sorgente [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Impossibile controllare la lista dei pacchetti sorgente [ftp://ftp.nerim.net](ftp://ftp.nerim.net) stable/main Packages (/var/lib/apt/lists/ftp.nerim.net_debian-marillat_dists_stable_main_binary-i386_Packages) - stat (2 No such file or directory)

and avidemux is not installable. What i do? where is the error? Thank you,ciao

---

### Post by crmanski on 2005-09-10
Avidemux is in the backports extras repositories.  You might have more luck installing if you use those repositories.

Backports thread here...
[http://ubuntuforums.org/forumdisplay.php?f=47](http://ubuntuforums.org/forumdisplay.php?f=47)

---

