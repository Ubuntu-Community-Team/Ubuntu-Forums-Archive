---
title: "problem upgrade/remove dmraid Gusty --&gt; Hardy"
date: 2008-05-01
forum: General Help
---

### Post by MattiJ on 2008-05-01
Have upgraded from Gusty to Hardy but now having trouble with update it will update dmraid but fails and ask me to reinstall since it's broken. I'm pretty shore that this box is not using dmraid and I'm rely just want remove it 

```

:~/Desktop$ sudo  apt-get upgrade
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket kommer att uppgraderas:
  devscripts dmraid
2 uppgraderade, 0 nyinstallerade, 0 att ta bort och 0 ej uppgraderade.
1 ej helt installerade eller borttagna.
Behöver hämta 465kB/653kB arkiv.
After this operation, 176kB of additional disk space will be used.
Vill du fortsätta [J/n]? j
Läs:1 http://archive.ubuntu.com hardy-backports/main devscripts 2.10.26ubuntu3~hardy1 [465kB]
Hämtade 465kB på 0s (1021kB/s)
(Läser databasen ... 280339 filer och kataloger installerade.)
Förbereder att ersätta dmraid 1.0.0.rc14-0ubuntu3 (med .../dmraid_1.0.0.rc14-0ubuntu3.1_amd64.deb) ...
 * Shutting down DMRAID devices...                                                                                                                            invoke-rc.d: initscript dmraid, action "stop" failed.
dpkg: varning - gammalt pre-removal-skript returnerade felstatus 1
dpkg - försöker skript från det nya paketet istället ...
 * Shutting down DMRAID devices...                                                                                                                            invoke-rc.d: initscript dmraid, action "stop" failed.
dpkg: fel vid hantering av /var/cache/apt/archives/dmraid_1.0.0.rc14-0ubuntu3.1_amd64.deb (--unpack):
 underprocess nytt pre-removal-skript gav felkod 1
 * Setting up DMRAID devices...                                                                                                                               invoke-rc.d: initscript dmraid, action "start" failed.
dpkg: fel vid upprensning:
 underprocess post-installation script gav felkod 1
Förbereder att ersätta devscripts 2.10.11ubuntu5 (med .../devscripts_2.10.26ubuntu3~hardy1_amd64.deb) ...
Packar upp ersättande devscripts ...
Fel uppstod vid hantering:
 /var/cache/apt/archives/dmraid_1.0.0.rc14-0ubuntu3.1_amd64.deb
localepurge: Disk space freed in /usr/share/man: 140K
E: Sub-process /usr/bin/dpkg returned an error code (1)
:~/Desktop$ 

```


try to remove
```

:~/Desktop$ sudo  apt-get remove dmraid
Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  libstdc++5 libk3b2 libfluidsynth1 libjack0.100.0-0 libflac++6 libbinio1c2 gcc-3.3-base ladcca2 dh-make
Använd "apt-get autoremove" för att ta bort dem.
Följande paket kommer att TAS BORT:
  dmraid
0 uppgraderade, 0 nyinstallerade, 1 att ta bort och 0 ej uppgraderade.
2 ej helt installerade eller borttagna.
After this operation, 709kB disk space will be freed.
Vill du fortsätta [J/n]? j
dpkg: fel vid hantering av dmraid (--remove):
 Paketet är i ett väldigt dåligt inkonsistent läge - du bör
 ominstallera det innan du försöker ta bort det.
Fel uppstod vid hantering:
 dmraid
E: Sub-process /usr/bin/dpkg returned an error code (1)
:~/Desktop$ 


```

---

