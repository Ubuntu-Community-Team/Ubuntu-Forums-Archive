---
title: "cant do apt upgrade getting strange error"
date: 2017-05-04
forum: General Help
---

### Post by deathkill on 2017-05-04
i get this error when doing sudo apt upgrade: (sorry my system is dutch language but i guess its still clear):

```
(Database wordt ingelezen ... 255026 bestanden en mappen momenteel geïnstalleerd.)
Uitpakken van .../kio-extras_4%3a16.04.3-0ubuntu1~ubuntu16.04~ppa61_amd64.deb wordt voorbereid...
Bezig met uitpakken van kio-extras (4:16.04.3-0ubuntu1~ubuntu16.04~ppa61) over (4:15.12.3-0ubuntu1) ...
dpkg: fout bij verwerken van archief /var/cache/apt/archives/kio-extras_4%3a16.04.3-0ubuntu1~ubuntu16.04~ppa61_amd64.deb (--unpack):
poging tot overschrijven van '/usr/lib/x86_64-linux-gnu/qt5/plugins/kio_activities.so', wat ook in pakket kactivities 5.18.0-0ubuntu1 zit
dpkg-deb: fout: subproces plakken werd gedood door signaal (Gebroken pijp)
Uitpakken van .../kio-extras-data_4%3a16.04.3-0ubuntu1~ubuntu16.04~ppa61_all.deb wordt voorbereid...
Bezig met uitpakken van kio-extras-data (4:16.04.3-0ubuntu1~ubuntu16.04~ppa61) over (4:15.12.3-0ubuntu1) ...
dpkg: fout bij verwerken van archief /var/cache/apt/archives/kio-extras-data_4%3a16.04.3-0ubuntu1~ubuntu16.04~ppa61_all.deb (--unpack):
poging tot overschrijven van '/usr/share/kservices5/kactivitymanagerd_fileitem_linking_plugin.desktop', wat ook in pakket kactivities 5.18
.0-0ubuntu1 zit
Bezig met afhandelen van triggers voor libc-bin (2.23-0ubuntu7) ...
Fouten gevonden tijdens verwerken van:
/var/cache/apt/archives/kio-extras_4%3a16.04.3-0ubuntu1~ubuntu16.04~ppa61_amd64.deb
/var/cache/apt/archives/kio-extras-data_4%3a16.04.3-0ubuntu1~ubuntu16.04~ppa61_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


any idea whats going on here?

what is the /var/cache/apt/archives/ being used for anyway?

---

### Post by vasa1 on 2017-05-04
Please try```
LANG=C; sudo apt upgrade
```That may provide you output in English.

Re. */var/cache/apt/archives/*, that is where deb files of applications you install (via *sudo apt-get install*) are stored until you decide to get rid of them by running *sudo apt clean*.

And it is good practice to always first run *sudo apt update* before running *sudo apt upgrade*.

---

### Post by ian-weisser on 2017-05-04
> **deathkill said:**
> dpkg: fout bij verwerken van archief /var/cache/apt/archives/kio-extras_4%3a16.04.3-0ubuntu1~ubuntu16.04~ppa61_amd64.deb (--unpack):
poging tot overschrijven van '/usr/lib/x86_64-linux-gnu/qt5/plugins/kio_activities.so', wat ook in pakket kactivities 5.18.0-0ubuntu1 zit

A file can be provided by only one package.
Two packages that provide the same file *conflict *and cannot be installed at the same time.
Decide which one you want. Uninstall the other.

This kind of error usually occurs when you add non-Ubuntu sources. The source owner packaged their own way instead of matching the Debian/Ubuntu file list.

---

### Post by deathkill on 2017-05-10
problem is that i added the ppa:kubuntu-ppa/backports and it gave me a conflict error on python3-aptdaemon.pkcompat and ppa purge cant downgrade the partial upgrade anymore.

is there a way to force the original distribution packages?

---

