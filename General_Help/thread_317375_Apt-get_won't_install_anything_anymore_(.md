---
title: "Apt-get won't install anything anymore :("
date: 2006-12-12
forum: General Help
---

### Post by misse- on 2006-12-12
I think I somehow managed to upgrade libgcc1 and libstdc++6 to a version that's not supported. So now apt won't do anything but complain about this and wanting to remove most of my system packages.

Example follows, sorry for the swedish text, I think you'll be able to figure out what it means.

martin@bean:/var/www/dev$ sudo apt-get install libjpeg-progs
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
Du kan möjligen rätta detta genom att köra "apt-get -f install":
Följande paket har beroenden som inte kan tillfredsställas:
  libgcc1: Beror: gcc-4.2-base (= 4.2-20061003-1) men det kan inte installeras
           Beror: libc6 (>= 2.5) men 2.3.5-1ubuntu12.5.10.1 skall installeras
  libstdc++6: Beror: gcc-4.2-base (= 4.2-20061003-1) men det kan inte installeras
              Beror: libc6 (>= 2.5) men 2.3.5-1ubuntu12.5.10.1 skall installeras
E: Otillfredsställda beroenden. Försök med "apt-get -f install" utan paket (eller ange en lösning)

And when I try to apt-get -f install

Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
Du kan möjligen rätta detta genom att köra "apt-get -f install":
Följande paket har beroenden som inte kan tillfredsställas:
  libgcc1: Beror: gcc-4.2-base (= 4.2-20061003-1) men det kan inte installeras
           Beror: libc6 (>= 2.5) men 2.3.5-1ubuntu12.5.10.1 skall installeras
  libstdc++6: Beror: gcc-4.2-base (= 4.2-20061003-1) men det kan inte installeras
              Beror: libc6 (>= 2.5) men 2.3.5-1ubuntu12.5.10.1 skall installeras
E: Otillfredsställda beroenden. Försök med "apt-get -f install" utan paket (eller ange en lösning).
martin@bean:/var/www/dev$ sudo apt-get -f install
Läser paketlistor... Färdig
Bygger beroendeträd... Färdig
Rättar beroenden.... Färdig
Följande paket kommer att TAS BORT:
  apache2 apache2-common apache2-mpm-prefork apt apt-utils aptitude base-config build-essential clamav-daemon clamav-freshclam dselect g++
  g++-4.0 gcc gcc-3.4 gcc-4.0 groff-base kernel-package libapache2-mod-php4 libboost-date-time-dev libboost-date-time1.33.0 libboost-dev
  libboost-filesystem-dev libboost-filesystem1.33.0 libboost-program-options-dev libboost-program-options1.33.0 libboost-serialization-dev
  libboost-thread-dev libboost-thread1.33.0 libclamav1 libgc1c2 libgcc1 libgl1-mesa libgl1-mesa-dev libglu1-mesa libglu1-mesa-dev libgmp3c2
  libgmpxx3 libqt3-mt libqt3-mt-dev libsablot0 libsigc++-1.2-5c2 libstdc++6 libstdc++6-4.0-dev libtool lshw man-db mysql-client mysql-server
  nmap php4 php4-dev php4-xslt phpmyadmin phpsysinfo qt3-dev-tools re2c squirrelmail squirrelmail-locales telnet ubuntu-minimal w3m
VARNING: Följande systemkritiska paket kommer att tas bort
Detta bör INTE göras såvida du inte vet exakt vad du gör!
  apt libgcc1 (på grund av apt) libstdc++6 (på grund av apt)
0 uppgraderade, 0 nyinstallerade, 62 att ta bort och 35 ej uppgraderade.
2 ej helt installerade eller borttagna.
Behöver hämta 0B arkiv.
Efter uppackning kommer 149MB frigöras på disken.
Du är på väg att göra något som kan vara skadligt
Skriv frasen 'Ja, gör som jag säger!' för att fortsätta
 ?]


Can anyone help me with this?

---

### Post by Ramses de Norre on 2006-12-12
I can't reed the error messages but if you installed new versions of libgcc1 and libstdc++6 you'll probably be able to solve your problems by going back to the official ones which can be found [here](http://packages.ubuntu.com/).

---

### Post by hod139 on 2006-12-12
I also cannot read the error messages, but you might have better luck trying to use aptitude to fix the system.  Aptitude is smarter and may auto-downgrade the packages for you.

```
sudo aptitude update
```
```
sudo aptitude install
```

aptitude takes the same commands as apt, but is more intelligent.

---

### Post by az on 2006-12-12
> **hod139 said:**
> I also cannot read the error messages, but you might have better luck trying to use aptitude to fix the system.  

No.

The problem is that there are some packages that are not in the list of repositories.  You need to downgrade those packages "by hand" or completely upgrade your system to the new repositories.

Whether you use apt-get or aptitude will not make a difference - the package manager is faced with an impossible situation.

---

