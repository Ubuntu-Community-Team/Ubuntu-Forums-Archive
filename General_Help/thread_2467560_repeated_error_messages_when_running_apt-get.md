---
title: "repeated error messages when running apt-get"
date: 2021-09-30
forum: General Help
---

### Post by teabutterfly2047 on 2021-09-30
Hello fellow Ubunters,

My current laptop was bought back in 2013 and started showing signs of old age and dysfunction a few months ago.

I don't know if these are bugs that I should report, or dysfunction, but the overall system has odd, unexpected behaviors. I have ignored so far all the warnings signs, since I was super busy/overwhelmed, and mainly because just closing the warning sign message window stopped the problem and the system overall kept running smoothly.

To sum it up: I just got a big red flag today (warning sign from the system) while trying to install a new printer that suggested an error happened and that I should run the 

> apt-get

command in a terminal.

Here is what I get:

> utilisateur@utilisateur-TravelMate-P253:~$ apt-get
apt 1.6.12ubuntu0.1 (amd64)
Usage : apt-get [options] commandes
        apt-get [options] install|remove pkg1 [pkg2 ...]
        apt-get [options] source pkg1 [pkg2 ...]

apt-get est une interface en ligne de commande servant à
télécharger des paquets ainsi que des informations à leur propos
depuis des sources de confiance ainsi qu'à les installer, les mettre à jour
avec leurs dépendances.



Commandes les plus utilisées :
  update - Récupère les nouvelles listes de paquets
  upgrade - Réalise une mise à jour
  install - Installe de nouveaux paquets (pkg1 est libc6 et non libc6.deb)
  remove - Supprime des paquets
  purge - Supprime des paquets et leurs fichiers de configuration
  autoremove - Supprime automatiquement les dépendances inutilisées
  dist-upgrade - Met à jour la distribution, reportez-vous à apt-get(8)
  dselect-upgrade - Suit les sélections de dselect
  build-dep - Configure build-dependencies pour les paquets sources
  clean - Supprime dans le cache local tous les fichiers téléchargés
  autoclean - Supprime dans le cache local les fichiers inutiles
  check - Vérifie qu'il n'y a pas de rupture de dépendances
  source - Télécharge les archives de sources
  download - Télécharge le paquet binaire dans le répertoire courant
  changelog - Télécharge et affiche le journal des modifications (« changelog ») du paquet indiqué

Veuillez vous référer à apt-get(8) pour plus d'information à propos des commandes disponibles.
Les options de configuration ainsi que la syntaxe sont détaillées dans apt.conf(5).
Des informations sur la configuration des sources sont disponibles dans sources.list(5).
Les choix de paquet ainsi que la version peuvent être renseignés grâce à apt_preferences(5).
Les informations à propos de la sécurité sont disponibles dans apt-secure(8).

                                Cet APT a les « Super Cow Powers »
utilisateur@utilisateur-TravelMate-P253:~$ 



OK, this is all in French and doesn't give much info about the real issue.

I'm off to read more about apt-get as suggested on the first thread I opened (it all started with me trying to connect a new print and install HPLIP as I said earlier).

---

### Post by T6&amp;sfpER35% on 2021-09-30
you can't just run apt-get , it must be followed by an option ,eg. apt-get update
there's no red flag ,it just tell you to follow the command with an option

---

### Post by deadflowr on 2021-09-30
Further beyond running with an option like update or upgrade you also need to run it with elevated rights, like with sudo, or be running as root.
Or else it'll simply output permission denied.

More on apt-get: [https://help.ubuntu.com/community/AptGet/Howto]("https://help.ubuntu.com/community/AptGet/Howto")
More on sudo:[https://help.ubuntu.com/community/RootSudo]("https://help.ubuntu.com/community/RootSudo")

---

### Post by teabutterfly2047 on 2021-09-30
> **3nd said:**
> you can't just run apt-get , it must be followed by an option ,eg. apt-get update
there's no red flag ,it just tell you to follow the command with an option

well, there's a big red button telling me that an ERROR occurred. This is what I nickname "red flag". So I know there's an error, but I don't know which one, or where to look or what option should follow apt-get. I saw a list of options, so I got it. Except none of the options suit my needs.

Anyways, I'm back to reading this: [https://itsfoss.com/apt-vs-apt-get-difference/](https://itsfoss.com/apt-vs-apt-get-difference/)

PS: I just added my signature using > hostnamectl

@deadlfwr thanks for more useful links.

I really have to RTFM.

fully read and understood: [https://itsfoss.com/apt-vs-apt-get-difference/](https://itsfoss.com/apt-vs-apt-get-difference/)
now let's read this: [URL="https://itsfoss.com/apt-command-guide/"]https://itsfoss.com/apt-command-guide/
[/URL]

and what to avoid, of course: [https://ubuntuforums.org/showthread.php?t=1877557](https://ubuntuforums.org/showthread.php?t=1877557)

I really want to read all the info carefully, as using the sudo/root command is high risk and I want to avoid mistakes here, if possible.

---

### Post by deadflowr on 2021-09-30
Your signature for xu8buntu (I guessing you mean Xubuntu) usage precedes the OS by over seven years.

It also shows the kernel which is really old.

I would suggest running
```
sudo apt update
sudo apt full-upgrade
```
post back the results, as you have mentioned an error icon thingy showing.
The output from the commands i posted should give us an idea of where you need help with it.

---

### Post by T6&amp;sfpER35% on 2021-09-30
a big red button in the terminal? can you screenshot it and show it here ?

---

### Post by QIII on 2021-09-30
While the support lifetime for Ubuntu LTS releases is five years, the support lifetime of Xubuntu is 3 years, which means that Xubuntu 18.04 went End Of Life in April of 2021.  Some of the repos for 18.04 may have been moved, which would certainly cause problems. 
 Before doing too much more, I would suggest doing a clean installation of Xubuntu 20.04, which is the latest supported LTS release.  Please back up all important data before doing this.  This can, and will, go wrong.

---

### Post by teabutterfly2047 on 2021-09-30
big haah! moment when reading this:

> [h=2]Graphical sudo[/h] You should **never** use normal sudo to start graphical applications as root. Using sudo  with graphical apps has the potential to corrupt your environment by  allowing root to take ownership of and/or change permissions on critical  files that you must own. The forums frequently see panicked requests  for help from users who can no longer log in after running graphical  applications under sudo.

source: [https://itsfoss.com/apt-command-guide/](https://itsfoss.com/apt-command-guide/)

the thing is I was told to type the following command in teminal:

> sudo synaptic

by ex boyfriend very often, so I just believed it was right.

one of you guys suggested a version conflict created because of this.

I probably need to run the command:

> apt autoremove

to clear all unwanted files first, then upgrade.

for the last couple months, my system would send me an automatic pop-up window asking permission for an upgrade, I would always opt for the full upgrade, and received a failure/error message about the upgrade being impossible/incomplete.

time to fix that. (don't mind me, I'm just talking to myself, teaching myself the process).

I haven't logged using sudo yet, I will get a good night's sleep first.

@deadflwr indeed my first post in this thread says: "My current laptop was bought back in 2013 and started showing signs of old age and dysfunction a few months ago."

I corrected the typo in my signature.

the red circle appears in the right top corner, along the logos of wifi connection, VPN, sound volume, battery etc...

I will run the commands you suggest... but wait... shouldn't I run autoremove first? like do a real cleanup before upgrading? sounds logical to me to get rid of unwanted files first, then upgrade.

OK, I really need some rest.

Let's talk tomorrow guys.

I *did* think from the start that it was old age wrecking havoc here. The automatic upgrades are not working (repeated failures) for a few months now.

So... where do I start? Serious data backup first. I usually burn a CD. Or maybe it's time to buy an external driver to store data? 

Then upgrade.

I'm still wondering about apt autoremove.

Time for bed, folks. See ya.

---

### Post by grahammechanical on 2021-09-30
The operating system will put notification icons in the top panel to warn us of problems. They are usually clickable and bring up a small panel revealing the problem and suggesting solutions. Red is usually a warning indicator.

It may be that you have broken packages on your system. We do not know without seeing the warning message. Broken packages would make an upgrade to a newer release risky and this may be the reason for the message that the upgrade cannot take place. If you post back the result of the commands suggested by deadflowr then we will have more information to base our guesses on.

Before upgrading one version to a newer version we should make sure that the existing version is fully up to date.

Regards

---

### Post by teabutterfly2047 on 2021-10-01
Hello there,

I just ran the commands suggested by deadflwr:

```
utilisateur@utilisateur-TravelMate-P253:~$ sudo apt update
[sudo] Mot de passe de utilisateur : 
Atteint :1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal InRelease
Réception de :2 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Réception de :3 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Réception de :4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed InRelease [267 kB]
Réception de :5 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [29,0 kB]
Réception de :6 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [1&#8239;256 kB]
Réception de :7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [62,7 kB]
Réception de :8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2&#8239;464 B]
Réception de :9 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [544 kB]
Réception de :10 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [284 kB]
Réception de :11 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [641 kB]
Réception de :12 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [864 kB]
Réception de :13 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [361 kB]
Réception de :14 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Réception de :15 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main i386 Packages [27,9 kB]
Réception de :16 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main amd64 Packages [114 kB]
Réception de :17 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main Translation-en [33,7 kB]
Réception de :18 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main amd64 DEP-11 Metadata [3&#8239;876 B]
Réception de :19 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main amd64 c-n-f Metadata [1&#8239;616 B]
Réception de :20 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/restricted amd64 Packages [108 kB]
Réception de :21 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/restricted Translation-en [16,6 kB]
Réception de :22 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/multiverse amd64 DEP-11 Metadata [944 B]
Réception de :23 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/universe amd64 Packages [47,4 kB]
Réception de :24 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/universe Translation-en [22,4 kB]
Réception de :25 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/universe amd64 DEP-11 Metadata [16,1 kB]
Réception de :26 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/universe amd64 c-n-f Metadata [2&#8239;152 B]
4&#8239;934 ko réceptionnés en 21s (232 ko/s)                                        
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
1962 paquets peuvent être mis à jour. Exécutez « apt list --upgradable » pour les voir.
utilisateur@utilisateur-TravelMate-P253:~$ sudo apt full-upgrade
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Vous pouvez lancer « apt --fix-broken install » pour corriger ces problèmes.
Les paquets suivants contiennent des dépendances non satisfaites :
 printer-driver-postscript-hp : Dépend: hplip (>= 3.17.10+repack0-5) mais il n'est pas installé
 systemd : Est en conflit avec: systemd-shim mais 9-1bzr4ubuntu1 est installé
           Casse: systemd-shim (< 10-3~) mais 9-1bzr4ubuntu1 est installé
 systemd-sysv : Est en conflit avec: systemd-shim mais 9-1bzr4ubuntu1 est installé
E: Dépendances non satisfaites. Essayez « apt --fix-broken install » sans paquet
   (ou indiquez une solution).
utilisateur@utilisateur-TravelMate-P253:~$ apt --fix-broken install
E: Impossible d'ouvrir le fichier verrou /var/lib/dpkg/lock-frontend - open (13: Permission non accordée)
E: Impossible d'obtenir le verrou de dpkg (/var/lib/dpkg/lock-frontend). Avez-vous les droits du superutilisateur ?
utilisateur@utilisateur-TravelMate-P253:~$ 


```

@[QIII]("https://ubuntuforums.org/posthistory.php?p=14061264") how do I replace quote tags with code tags?

---

### Post by Dennis N on 2021-10-01
You just need to use sudo with **apt --fix-broken install** here:

```
utilisateur@utilisateur-TravelMate-P253:~$ apt --fix-broken install
E: Impossible d'ouvrir le fichier verrou /var/lib/dpkg/lock-frontend - open (13: Permission non accordée)
E: Impossible d'obtenir le verrou de dpkg (/var/lib/dpkg/lock-frontend). Avez-vous les droits du superutilisateur ?
```

---

### Post by QIII on 2021-10-01
To use code tags:

1. If you are using the "Reply to Thread" button, please type or paste your text, highlight the text and use the # button in the text box header. Alternatively, click the # button first, place your cursor between the code tags and type or paste your text.

2. If using "Quick Reply" then type [noparse]```
[/noparse] at the beginning and [noparse]
```[/noparse] at the end.  The square brackets are required.

---

### Post by teabutterfly2047 on 2021-10-01
thanks QII for the step by step. Duly noted.

@Dennis N:

As you can see from the code you're quoting yourself, I have already used sudo with the code[B] apt --fix-broken install

[/B]The answer I get (I will translate from French) says:
```
It is impossible to open the lock file (...)
It is impossible to get the lock of dpkg (...)
``` 

And then I'm asked: ```
do you have root rights?
```

Actually, I don't have the root password.

---

### Post by deadflowr on 2021-10-01
> As you can see from the code you're quoting yourself, I have already used sudo with the code apt --fix-broken install
No, you did not.
Your output is this
```
utilisateur@utilisateur-TravelMate-P253:~$ apt --fix-broken install
```

No sudo.

---

### Post by T6&amp;sfpER35% on 2021-10-01
> [COLOR=#000000]Actually, I don't have the root password.[/COLOR]





??

---

### Post by ajgreeny on 2021-10-01
You do  not need the root password; the user password you used when you created the user at installation of the OS is the one you need.

So run ```
sudo apt update
``` and it will ask for the user password, not the root password (which does not exist by default in Ubuntu) raising the user's permissions temporarily to that of root, allowing actions within the system files, eg, for installing packages.

See **[COLOR="#FF0000"]RootSudo[/COLOR]** in my signature below for a more detailed explanation of all of this.

---

### Post by teabutterfly2047 on 2021-10-01
OK, think I got it this time. Here's the result:

```

utilisateur@utilisateur-TravelMate-P253:~$ sudo apt update
[sudo] Mot de passe de utilisateur : 
Atteint :1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal InRelease
Réception de :2 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Réception de :3 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed InRelease [267 kB]
Réception de :4 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Réception de :5 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/main amd64 Packages [1&#8239;256 kB]
Réception de :6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/main amd64 DEP-11 Metadata [29,0 kB]
Réception de :7 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/universe amd64 DEP-11 Metadata [62,5 kB]
Réception de :8 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security/multiverse amd64 DEP-11 Metadata [2&#8239;468 B]
Réception de :9 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/main i386 Packages [544 kB]
Réception de :10 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/main amd64 DEP-11 Metadata [283 kB]
Réception de :11 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/universe i386 Packages [641 kB]
Réception de :12 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 Packages [864 kB]
Réception de :13 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/universe amd64 DEP-11 Metadata [361 kB]
Réception de :14 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-updates/multiverse amd64 DEP-11 Metadata [944 B]
Réception de :15 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main amd64 Packages [122 kB]
Réception de :16 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main i386 Packages [28,3 kB]
Réception de :17 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main Translation-en [34,6 kB]
Réception de :18 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main amd64 DEP-11 Metadata [3&#8239;876 B]
Réception de :19 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/main amd64 c-n-f Metadata [1&#8239;616 B]
Réception de :20 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/restricted amd64 Packages [112 kB]
Réception de :21 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/restricted Translation-en [17,1 kB]
Réception de :22 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/multiverse amd64 DEP-11 Metadata [944 B]
Réception de :23 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal-proposed/universe amd64 DEP-11 Metadata [16,2 kB]
4&#8239;876 ko réceptionnés en 6s (870 ko/s)                                 
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
1962 paquets peuvent être mis à jour. Exécutez « apt list --upgradable » pour les voir.
utilisateur@utilisateur-TravelMate-P253:~$ sudo apt --fix-broken install
Lecture des listes de paquets... Fait
Construction de l'arbre des dépendances       
Lecture des informations d'état... Fait
Correction des dépendances... Fait
Les paquets suivants ont été installés automatiquement et ne sont plus nécessaires :
  gstreamer1.0-plugins-base:i386 libamd2.4.1 libappstream3 libaudio2:i386
  libautodie-perl libavahi-common-data:i386 libavahi-common3:i386 libbind9-140
  libblas-common libboost-date-time1.58.0 libboost-filesystem1.58.0
  libboost-iostreams1.58.0 libboost-system1.58.0 libcamd2.4.1 libcap2:i386
  libcapnp-0.5.3 libccolamd2.9.1 libcdparanoia0:i386 libcholmod3.0.6
  libcloog-isl4 libcolamd2.9.1 libcryptsetup4 libdirectfb-1.2-9
  libdns-export162 libdns162 libefivar0 libextutils-pkgconfig-perl
  libffi7:i386 libfreerdp-cache1.1 libfreerdp-client1.1 libfreerdp-codec1.1
  libfreerdp-common1.1.0 libfreerdp-core1.1 libfreerdp-crypto1.1
  libfreerdp-gdi1.1 libfreerdp-locale1.1 libfreerdp-primitives1.1
  libfreerdp-utils1.1 libfwup0 libfwupd1 libgcrypt20:i386 libgfortran3
  libglew1.13 libglib2.0-0:i386 libgmp10:i386 libgnome-desktop-3-12
  libgnome2-0 libgnome2-bin libgnutls30:i386 libgpg-error0:i386 libgrilo-0.2-1
  libgssapi-krb5-2:i386 libgstreamer-plugins-base1.0-0:i386
  libgstreamer1.0-0:i386 libgweather-3-6 libhardware2 libhogweed4:i386
  libhogweed5:i386 libhybris libhybris-common1 libical1a libice6:i386
  libicu55:i386 libidn11:i386 libisc-export160 libisc160 libisccc140
  libisccfg140 libiso9660-8 libjbig0:i386 libk5crypto3:i386 libkeyutils1:i386
  libkrb5-3:i386 libkrb5support0:i386 liblivemedia50 libllvm5.0
  libllvm5.0:i386 libllvm9:i386 liblouis9 liblouisutdml6 liblwres141
  liblz4-1:i386 libmedia1 libmimic0 libmysqlclient20:i386 libnettle6:i386
  libnettle7:i386 libnma-common libogg0:i386 libopus0:i386 liborc-0.4-0:i386
  liborcus-0.10-0v5 libp11-kit0:i386 libpackagekit-glib2-16 libpng12-0:i386
  libpodofo0.9.3 libpoppler58 libppl13v5 libprocps4 libprotobuf-lite9v5
  libpython3.5 libpython3.5-minimal libpython3.5-stdlib libqpdf17
  libquvi-scripts libquvi7 libraw15 libsm6:i386 libsodium18 libsqlite3-0:i386
  libsrtp0 libssl1.1:i386 libsuitesparseconfig4.4.6 libtasn1-6:i386
  libtheora0:i386 libtiff5:i386 libtxc-dxtn-s2tc0:i386 libumfpack5.7.1
  libva-drm1 libva-x11-1 libvisual-0.4-0:i386 libvorbis0a:i386
  libvorbisenc2:i386 libvulkan1:i386 libwebpdemux1 libwebpmux1
  libwebrtc-audio-processing-0 libwildmidi1 libwinpr-crt0.1
  libwinpr-dsparse0.1 libwinpr-environment0.1 libwinpr-file0.1
  libwinpr-handle0.1 libwinpr-heap0.1 libwinpr-input0.1
  libwinpr-interlocked0.1 libwinpr-library0.1 libwinpr-path0.1
  libwinpr-pool0.1 libwinpr-registry0.1 libwinpr-rpc0.1 libwinpr-sspi0.1
  libwinpr-synch0.1 libwinpr-sysinfo0.1 libwinpr-thread0.1 libwinpr-utils0.1
  libxapian-1.3-5 libxapian22v5 libxi6:i386 libxml2:i386 libxslt1.1:i386
  libxss1:i386 libxt6:i386 libxtables11 libxv1:i386 linux-headers-4.15.0-100
  linux-headers-4.15.0-100-generic linux-headers-4.15.0-101
  linux-headers-4.15.0-101-generic linux-headers-4.15.0-102
  linux-headers-4.15.0-102-generic linux-headers-4.15.0-103
  linux-headers-4.15.0-103-generic linux-headers-4.15.0-118
  linux-headers-4.15.0-118-generic linux-headers-4.15.0-119
  linux-headers-4.15.0-119-generic linux-headers-4.15.0-42
  linux-headers-4.15.0-42-generic linux-headers-4.15.0-43
  linux-headers-4.15.0-43-generic linux-headers-4.15.0-49
  linux-headers-4.15.0-49-generic linux-headers-4.15.0-55
  linux-headers-4.15.0-55-generic linux-headers-4.15.0-73
  linux-headers-4.15.0-73-generic linux-headers-4.15.0-91
  linux-headers-4.15.0-91-generic linux-headers-4.4.0-138
  linux-headers-4.4.0-138-generic linux-headers-4.4.0-139
  linux-headers-4.4.0-139-generic linux-image-4.15.0-100-generic
  linux-image-4.15.0-101-generic linux-image-4.15.0-102-generic
  linux-image-4.15.0-103-generic linux-image-4.15.0-118-generic
  linux-image-4.15.0-119-generic linux-image-4.15.0-42-generic
  linux-image-4.15.0-43-generic linux-image-4.15.0-55-generic
  linux-image-4.15.0-73-generic linux-image-4.15.0-91-generic
  linux-image-4.4.0-138-generic linux-image-4.4.0-139-generic
  linux-image-extra-4.4.0-138-generic linux-image-extra-4.4.0-139-generic
  linux-modules-4.15.0-100-generic linux-modules-4.15.0-101-generic
  linux-modules-4.15.0-102-generic linux-modules-4.15.0-103-generic
  linux-modules-4.15.0-118-generic linux-modules-4.15.0-119-generic
  linux-modules-4.15.0-42-generic linux-modules-4.15.0-43-generic
  linux-modules-4.15.0-55-generic linux-modules-4.15.0-73-generic
  linux-modules-4.15.0-91-generic linux-modules-extra-4.15.0-100-generic
  linux-modules-extra-4.15.0-101-generic
  linux-modules-extra-4.15.0-102-generic
  linux-modules-extra-4.15.0-103-generic
  linux-modules-extra-4.15.0-118-generic
  linux-modules-extra-4.15.0-119-generic linux-modules-extra-4.15.0-42-generic
  linux-modules-extra-4.15.0-43-generic linux-modules-extra-4.15.0-55-generic
  linux-modules-extra-4.15.0-73-generic linux-modules-extra-4.15.0-91-generic
  oxideqt-codecs python3.5 python3.5-minimal snapd-login-service
  ttf-ubuntu-font-family ubuntu-ui-toolkit-theme
Veuillez utiliser « sudo apt autoremove » pour les supprimer.
Les paquets supplémentaires suivants seront installés : 
  libffi7 libffi7:i386 libgnutls-openssl27 libgnutls30 libgnutls30:i386
  libhogweed5 libhogweed5:i386 libip4tc2 libnettle7 libnettle7:i386
  libnss-systemd libp11-kit0 libp11-kit0:i386 libpam-systemd libpcre2-8-0
  libsystemd0 libtasn1-6 libtasn1-6:i386 p11-kit-modules
  printer-driver-postscript-hp systemd systemd-timesyncd
Paquets suggérés :
  gnutls-bin gnutls-bin:i386 hplip systemd-container
Les paquets suivants seront ENLEVÉS :
  consolekit libpam-ck-connector systemd-shim
Les NOUVEAUX paquets suivants seront installés :
  libffi7 libffi7:i386 libhogweed5 libhogweed5:i386 libip4tc2 libnettle7
  libnettle7:i386 libpcre2-8-0 systemd-timesyncd
Les paquets suivants seront mis à jour :
  libgnutls-openssl27 libgnutls30 libgnutls30:i386 libnss-systemd libp11-kit0
  libp11-kit0:i386 libpam-systemd libsystemd0 libtasn1-6 libtasn1-6:i386
  p11-kit-modules printer-driver-postscript-hp systemd
13 mis à jour, 9 nouvellement installés, 3 à enlever et 1949 non mis à jour.
1 partiellement installés ou enlevés.
Il est nécessaire de prendre 332 ko/8&#8239;670 ko dans les archives.
Après cette opération, 6&#8239;618 ko d'espace disque supplémentaires seront utilisés.
Souhaitez-vous continuer ? [O/n] O
Réception de :1 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal/main amd64 libffi7 amd64 3.3-4 [19,7 kB]
Réception de :2 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal/main i386 libffi7 i386 3.3-4 [17,9 kB]
Réception de :3 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal/main amd64 libtasn1-6 amd64 4.16.0-2 [38,1 kB]
Réception de :4 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal/main i386 libtasn1-6 i386 4.16.0-2 [40,6 kB]
Réception de :5 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal/main amd64 libip4tc2 amd64 1.8.4-3ubuntu2 [18,8 kB]
Réception de :6 [http://fr.archive.ubuntu.com/ubuntu](http://fr.archive.ubuntu.com/ubuntu) focal/main amd64 libpcre2-8-0 amd64 10.34-7 [197 kB]
332 ko réceptionnés en 1s (563 ko/s)
(Lecture de la base de données... 1032238 fichiers et répertoires déjà installés.)
Suppression de systemd-shim (9-1bzr4ubuntu1) ...
Suppression de « détournement de /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service en /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd par systemd-shim »
dpkg-divert: erreur: le renommage implique l'écrasement de « /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service » avec
  un fichier différent « /usr/share/dbus-1/system-services/org.freedesktop.systemd1.service.systemd », ce n'est pas autorisé
dpkg: erreur de traitement du paquet systemd-shim (--remove) :
 installed systemd-shim package post-removal script subprocess returned error exit status 2
Suppression de consolekit (0.4.6-5) ...
Suppression de libpam-ck-connector:amd64 (0.4.6-5) ...
Des erreurs ont été rencontrées pendant l'exécution :
 systemd-shim
E: Sub-process /usr/bin/dpkg returned an error code (1)
utilisateur@utilisateur-TravelMate-P253:~$ 



```

thanks @ajgreeny for the RootSudo link, I'm off to read it.

PS: I've already read this page, and thanks again.

Currently reading this: [https://www.howtogeek.com/229699/how-to-uninstall-software-using-the-command-line-in-linux/](https://www.howtogeek.com/229699/how-to-uninstall-software-using-the-command-line-in-linux/) and this: [https://www.howtogeek.com/229682/](https://www.howtogeek.com/229682/)

---

### Post by teabutterfly2047 on 2021-10-02
My printer problem has been solved. Thanks everyone.

As to updating the system, I am currently reading this: [https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs](https://blog.jdpfu.com/2011/06/24/system-maintenance-for-linux-pcs) as suggested by one of you guys (thanks!) on my printer problem thread (now SOLVED).

Phew.

---

### Post by Impavidus on 2021-10-03
If you run```
export LANG=C_LANG
```all following output in the same terminal will be in English. That may be slightly easier to some of us.

BTW, I see a huge pile of autoremovable packages. That may be the result of accidental removal of some important metapackage, so be careful before actually autoremoving them. I see some 4.4 kernels and old 4.15 kernels and 1949 upgrades still waiting. This problem must have existed for ages. Don't think too long about it, or a fresh install of 20.04 will be quicker.

---

### Post by TheFu on 2021-10-05
> **Impavidus said:**
>  a fresh install of 20.04 will be quicker.

+1.  Moving from 18.04 --> 20.04 took almost 3 hours on one of my systems.
A fresh install of 20.04 is usually 10-20 minutes and there isn't any "cruft" left over.

Seems you are using google to find answers from random locations. Each of those locations and answers may not be specific for your system.  For people really new to Linux, I point them at this   [https://blog.jdpfu.com/Lin_4_Win_Users](https://blog.jdpfu.com/Lin_4_Win_Users)  for an overview.  

Then I send them to a full document for their specific DE (Desktop Environment) google "xubuntu users guide" and finally, I send them to a CLI (Command Linux Interface) beginners book.  [http://linuxcommand.org/tlcl.php](http://linuxcommand.org/tlcl.php)

The last link provides information in the correct order, so you don't end up way over your head with commands and tools without any background first.  Put first things first and work through the first 250 pgs of that book by Shotts, then skim the other pages just to see what's in there.

In these forums, providing CLI answers is something we do because it is usually the same regardless of Ubuntu flavor and copy/pasting of text is much more efficient that screen captures.  We can say run
```
sudo apt update
sudo apt full-upgrade

```much quicker than we can describe which menu, and submenu items to select, then what button to press inside one of 5 different GUIs.  It is much easier.  Also, lots of people here use Linux servers and there isn't **any** GUI.  Only CLI commands can help them.

It is very useful if your signature is correct.  Incorrect signatures means we can't believe everything on the screen and will make bad assumptions trying to be helpful. We already have to make hundreds of assumptions just to start the conversation. Accurate information is key, and even then, there are some things specific to your system that we would never think to ask.  We each live in our bubbles and only know what we know. ;)  In the end, hopefully something someone writes here will click in your mind and lead to a solution.  Every once in a while, someone will actually know the root issue and be able to provide a correct solution too.  That's the hope.

---

