---
title: "Libreoffice 3.5 ppa update problem"
date: 2013-01-13
forum: General Help
---

### Post by cottfcfan on 2013-01-13
Is anyone else having a problem updating libreoffice from this ppa?
[https://launchpad.net/~libreoffice/+archive/libreoffice-3-5](https://launchpad.net/~libreoffice/+archive/libreoffice-3-5)
12 packages keep being held back with either upgrade or dist-upgrade.

---

### Post by dino99 on 2013-01-13
which kubuntu version ?
what says the package manager ? (broken package ?)
how is set the ppa entry into fstab ?

---

### Post by cottfcfan on 2013-01-13
Kubuntu 12.04.
Package manager says "Unable to mark upgrades. Some upgrades may have unsatisfiable dependencies at the moment, or may have been manually held back."
PPA has worked on previous upgrade to 3.5.7.

---

### Post by cottfcfan on 2013-01-13
Actually i'm now having this problem even trying to install the libreoffice from the standard repos. In a terminal i get the message:
```
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies.
 libreoffice : Depends: libreoffice-core (= 1:3.5.4-0ubuntu1.1) but it is not going to be installed
               Depends: libreoffice-writer but it is not going to be installed
               Depends: libreoffice-calc but it is not going to be installed
               Depends: libreoffice-impress but it is not going to be installed
               Depends: libreoffice-draw but it is not going to be installed
               Depends: libreoffice-math but it is not going to be installed
               Depends: libreoffice-base but it is not going to be installed
               Depends: libreoffice-filter-mobiledev but it is not going to be installed
               Depends: libreoffice-java-common (>= 1:3.5.4~) but it is not going to be installed
               Recommends: libreoffice-gnome but it is not going to be installed or
                           libreoffice-kde but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```
But there are no broken packages.

---

### Post by cottfcfan on 2013-01-13
Actually, this has been an object lesson in why not to add 3rd party ppas to your system.
It was the libreoffice ppa that was screwing everything up, even stopping me reinstalling the official libreoffice from the repo.
After much googling I had to, first disable the ppa, then run in a terminal:
```
sudo rm -rf /var/lib/apt/lists/* && sudo apt-get update
```
Only after this could I finally reinstall libreoffice.
Lesson learned.

*edit.. just an addition. The problem is the package "libexttextcat0" it is not getting update by the ppa, like it needs to be. This package may need to be removed before reinstalling libreoffice from the repo.*

---

### Post by ju2wheels on 2013-01-16
FYI I had the same problem and reported it to the ppa mailing list, they said they are working on resolving it so retry in a day or two.

---

### Post by speartip on 2013-01-16
Having the same issue.
I have just checked the ppa, and Libreoffice was rebuilt 7 hours ago.
Seems to upgrade fine now.
Thanks for the info ju2wheels.

---

