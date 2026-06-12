---
title: "Why my Gutsy still have Firefox 2.0.0.6?"
date: 2007-10-27
forum: General Help
---

### Post by pjalegria on 2007-10-27
Hello

I dont understand why my Gutsy dont make Firefox updates??? I still have firefox 2.0.0.6 and firefox 2.0.0.8 was been realesed a few days ago...:confused:

Tank you

---

### Post by taurus on 2007-10-27
If you bother to run

```
sudo apt-get update
sudo apt-get upgrade
```
you will see that it will upgrade to firefox 2.0.0.8!

---

### Post by pjalegria on 2007-10-27
No upgrades found...:confused:

---

### Post by smartbei on 2007-10-27
Odd indeed, I have had firefox 2.0.0.8 since I upgraded to Gutsy.

After updating as explained above by taurus, try:
```

aptitude show firefox

```
and see what version it has there.

---

### Post by pjalegria on 2007-10-27
Pacote: firefox
Estado: instalado
Instalado automaticamente: sim
Versão: 2.0.0.6+2nobinonly-0ubuntu1
Prioridade: opcional
Secção: web
Maintainer: Alexander Sack <asac@ubuntu.com>
Tamanho Descomprimido: 26,6M
Dependente de: fontconfig, psmisc, debianutils (>= 1.16), libatk1.0-0 (>=
               1.13.2), libc6 (>= 2.6-1), libcairo2 (>= 1.4.0), libfontconfig1
               (>= 2.4.0), libfreetype6 (>= 2.3.5), libgcc1 (>= 1:4.2.1),
               libglib2.0-0 (>= 2.14.0), libgtk2.0-0 (>= 2.12.0),
               libhunspell-1.1-0 (>= 1.1.5-1), libjpeg62, libnspr4-0d (>=
               1.8.0.10), libnss3-0d (>= 1.8.0.10), libpango1.0-0 (>= 1.18.2),
               libstdc++6 (>= 4.2.1), libx11-6, libxcomposite1 (>= 1:0.3-1),
               libxcursor1 (> 1.1.2), libxdamage1 (>= 1:1.1), libxext6,
               libxfixes3 (>= 1:4.0.1), libxft2 (> 2.1.1), libxi6, libxinerama1,
               libxrandr2 (>= 2:1.2.0), libxrender1, libxt6, zlib1g (>=
               1:1.2.3.3.dfsg-1)
Recomenda: ubufox
Sugere: firefox-gnome-support (= 2.0.0.6+2nobinonly-0ubuntu1), latex-xft-fonts
Em conflito com: libnss3
Substitui: libnss3
Disponibiliza: www-browser
Descrição: lightweight web browser based on Mozilla
 Firefox is a redesign of the Mozilla browser component, similar to Galeon,
 K-Meleon and Camino, but written using the XUL user interface language and
 designed to be lightweight and cross-platform. 
 
 This browser was previously known as Firebird and Phoenix. 
 
 This is a build of a random development version (aka trunk). It is ment for
 preview and not for production use.

---

### Post by TidusBlade on 2007-10-27
I think 2.0.0.7 and 2.0.0.8 only got changes specific to the windows and/or Mac version, nothing new for linux users :(

---

### Post by Archmage on 2007-10-27
Mozilla/5.0 (X11; U; Linux i686; de; rv:1.8.1.8) Gecko/20071022 Ubuntu/7.10 (gutsy) Firefox/2.0.0.8

---

### Post by taurus on 2007-10-27
> **TidusBlade said:**
> I think 2.0.0.7 and 2.0.0.8 only got changes specific to the windows and/or Mac version, nothing new for linux users :(

I am running version 2.0.0.8 in Gutsy both at home and in my office.  Even Fedora 7 uses firefox 2.0.0.8.

pjalegria:  Can you post your /etc/apt/sources.list?

```
cat /etc/apt/sources.list
```

---

### Post by pjalegria on 2007-10-27
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.


## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.


## Internacional
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on [https://launchpad.net/products/medibuntu/+bugs](https://launchpad.net/products/medibuntu/+bugs)

## Internacional
## CANONICAL COMMERCIAL REPOSITORY (Hosted on Canonical servers, not Ubuntu
## servers. RealPlayer10, Opera and more to come.) 


deb [http://apt.emesene.org/](http://apt.emesene.org/) ./
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe multiverse restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy main universe multiverse restricted #Added by software-properties
deb-src [http://apt.emesene.org/](http://apt.emesene.org/) ./

---

### Post by artir on 2007-10-27
Go to System-Administration-Software preferences.
Then select main, universe and multiverse. 
Go to the next tab and check all the checkboxes except the gutsy-proposed.

---

### Post by pjalegria on 2007-10-27
Solved...Tank you very much:):):)

---

### Post by moktoman on 2007-10-27
I thought I would add that I had the exact same issue after installing Kubuntu 7.10 from an installation CD and after following the instructions by **artir** I also discovered that in Adept, under Adept >> Manage Repositories >> Updates, nothing was checked, meaning Adept was not checking for updates, so of course, checking the proper items and refreshing Adept immediately revealed the updates for Firefox, among other things.

Thanks, **artir**! :D

---

### Post by pjalegria on 2007-11-07
Now i have the same problem with firefox 2.0.0.8... dont upgrade to 2.0.0.9:(

---

### Post by U53R on 2007-11-10
Mine wont detect 2.0.0.9 either, and I have the software sources checked, and have done "sudo apt-get update" etc. I would build it from source but "./configure" wont work for me either.

---

### Post by FuturePilot on 2007-11-10
They're working on it. 
[https://bugs.launchpad.net/ubuntu/gutsy/+source/firefox/+bug/160895]("https://bugs.launchpad.net/ubuntu/gutsy/+source/firefox/+bug/160895")

---

