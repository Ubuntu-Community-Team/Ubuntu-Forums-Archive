---
title: "Stuck in dependencies"
date: 2013-02-23
forum: General Help
---

### Post by trasan on 2013-02-23
Hi,

Running Ubuntu server 12.04

Having the following problem, and I think I got it since partition /boot ran out of space.



Getting the following message when upgrading or trying to install anything:

(in swedish, sorry...)
```

Du bör köra "apt-get -f install" för att korrigera dessa:
Följande paket har beroenden som inte kan tillfredsställas:
 linux-server : Beroende av: linux-image-server (= 3.2.0.36.43) men 3.2.0.38.46 kommer att installeras
                Beroende av: linux-headers-server (= 3.2.0.36.43) men det kommer inte att installeras
E: Otillfredsställda beroenden. Prova med "apt-get -f install" utan paket (eller ange en lösning).

```Running  "apt-get -f install" does not help.


apt-get -f install
```

Läser paketlistor... Färdig
Bygger beroendeträd         
Läser tillståndsinformation... Färdig
Korrigerar beroenden.... Färdig
Följande paket har installerats automatiskt och är inte längre nödvändiga:
  linux-headers-3.2.0-31-generic linux-headers-3.2.0-31 linux-headers-3.2.0-32 linux-headers-3.2.0-33 linux-headers-3.2.0-34 linux-headers-3.2.0-29
  linux-headers-3.2.0-35 linux-headers-3.2.0-34-generic linux-headers-3.2.0-29-generic linux-headers-3.2.0-32-generic linux-headers-3.2.0-35-generic
  linux-headers-3.2.0-33-generic
Använd "apt-get autoremove" för att ta bort dem.
Följande ytterligare paket kommer att installeras:
  linux-server
Följande paket kommer att uppgraderas:
  linux-server
1 att uppgradera, 0 att nyinstallera, 0 att ta bort och 40 att inte uppgradera.
1 är inte helt installerade eller borttagna.
Behöver hämta 0 B/1 734 B arkiv.
Efter denna åtgärd kommer ytterligare 0 B utrymme användas på disken.
Vill du fortsätta [J/n]? J
dpkg: beroendeproblem förhindrar konfigurering av linux-server:
 linux-server är beroende av linux-image-server (= 3.2.0.36.43), men:
  Versionen av linux-image-server på systemet är 3.2.0.38.46.
 linux-server är beroende av linux-headers-server (= 3.2.0.36.43), men:
  Versionen av linux-headers-server på systemet är 3.2.0.38.46.
dpkg: fel vid hantering av linux-server (--configure):
 beroendeproblem - lämnar okonfigurerad
Ingen apport-rapport skrevs därför att MaxReports redan har uppnåtts
                                                                    Fel uppstod vid hantering:
 linux-server
E: Sub-process /usr/bin/dpkg returned an error code (1)


```Anyone knows how to fix this?







EDIT
This page contained all I needed to know to fix the problem:
[http://askubuntu.com/questions/253243/apt-wedged-by-kernel-version-mismatch](http://askubuntu.com/questions/253243/apt-wedged-by-kernel-version-mismatch)

---

