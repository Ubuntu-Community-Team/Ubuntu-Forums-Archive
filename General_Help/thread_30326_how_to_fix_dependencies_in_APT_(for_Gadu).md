---
title: "how to fix dependencies in APT (for Gadu)"
date: 2005-04-28
forum: General Help
---

### Post by areks on 2005-04-28
I would like to install some extra applications which are not in Ubuntu or Debian (ftp.nerim.net/debian-marillat) repository's. This are clients programs for Polish GaduGadu massager.
There are two of them. First Kadu is KDE based, second Gnu Gadu is for Gnome.

I add 2 line in /etc/apt/source.list
deb [http://kadu.net/download/binary/debian/sid](http://kadu.net/download/binary/debian/sid) ./
deb [http://metro.lezajsk.info/gg2/sarge/](http://metro.lezajsk.info/gg2/sarge/) ./

In last weeks both of this programs got new versions, and I would like to install them. Unfortunately in both cases apt-get (Synaptic) complains about dependencies. 

For Kadu I get:
kadu:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed

kadu-spellchecker:
  Depends: libaspell15 (>=0.60) but 0.50.5-5 is to be installed

and for Gnu Gadu:
gg2:
  Depends: libaspell15 (>=0.60) but 0.50.5-5 is to be installed
  Depends: libgadu3 (>=1:1.5+20050227) but 1:1.5-4ubuntu1 is to be installed

Unfortunately I'm new to APT and have no idea how to fix this dependencies.

Thanks for any help.
Arek

---

### Post by pinok on 2005-04-29
[QUOTE=areks]I would like to install some extra applications which are not in Ubuntu or Debian (ftp.nerim.net/debian-marillat) repository's. This are clients programs for Polish GaduGadu massager.
There are two of them. First Kadu is KDE based, second Gnu Gadu is for Gnome.

I add 2 line in /etc/apt/source.list
deb [http://kadu.net/download/binary/debian/sid](http://kadu.net/download/binary/debian/sid) ./
deb [http://metro.lezajsk.info/gg2/sarge/](http://metro.lezajsk.info/gg2/sarge/) ./

In last weeks both of this programs got new versions, and I would like to install them. Unfortunately in both cases apt-get (Synaptic) complains about dependencies. 

For Kadu I get:
kadu:
  Depends: libc6 (>=2.3.2.ds1-21) but 2.3.2.ds1-20ubuntu13 is to be installed
  Depends: libqt3c102-mt (>=3:3.3.4) but 3:3.3.3-7ubuntu3 is to be installed

kadu-spellchecker:
  Depends: libaspell15 (>=0.60) but 0.50.5-5 is to be installed

and for Gnu Gadu:
gg2:
  Depends: libaspell15 (>=0.60) but 0.50.5-5 is to be installed
  Depends: libgadu3 (>=1:1.5+20050227) but 1:1.5-4ubuntu1 is to be installed

Unfortunately I'm new to APT and have no idea how to fix this dependencies.

Thanks for any help.
Arek[/QUOTE]
 Szybko i po polsku :) (Only for polish :P)
[http://ubuntu.pl/phpBB//viewtopic.php?t=267](http://ubuntu.pl/phpBB//viewtopic.php?t=267)

---

### Post by areks on 2005-04-29
Dzieki. :)
To jest tez polskie forun Ubuntu! Dobrze wiedziec.

(It is working now)

---

