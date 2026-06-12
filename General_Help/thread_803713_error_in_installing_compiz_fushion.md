---
title: "error in installing compiz fushion"
date: 2008-05-22
forum: General Help
---

### Post by grayfox444 on 2008-05-22
everything before this worked, but i'm getting an error here:

evan@evan-desktop:~$ sudo apt-get -y install compiz compiz-gnome compizconfig-settings-manager compiz-fusion-plugins-extra libcompizconfig-backend-gconf
Reading package lists... Done
Building dependency tree       
Reading state information... Done
compiz is already the newest version.
compiz-gnome is already the newest version.
compiz-fusion-plugins-extra is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  compizconfig-backend-gconf: Conflicts: libcompizconfig-backend-gconf but 0.6.0~git20071003+3v1ubuntu0 is to be installed
E: Broken packages

---

### Post by Forlong on 2008-05-22
What version of Ubuntu are you using?

---

### Post by grayfox444 on 2008-05-22
heron.

---

### Post by Forlong on 2008-05-22
Post your **/etc/apt/sources.list** -- and use the forum's [noparse][CODE][/noparse] tag please (# button)

---

### Post by grayfox444 on 2008-05-22
how do i find the /etc/apt/sources.list?

---

### Post by Forlong on 2008-05-22
Just run your favourite text editor and open the file with it.

---

### Post by forestpixie on 2008-05-22
Do it from terminal is easiest

```
cat /etc/apt/sources.list
```

---

### Post by raafaell on 2008-05-22
open your terminal.
then: > sudo gedit /home/$youname$/etc/apt/sources.list
write your password as necessary. :]

---

### Post by grayfox444 on 2008-05-22
```
# deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy universe
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy multiverse
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu hardy partner
# deb-src http://archive.canonical.com/ubuntu hardy partner

deb http://security.ubuntu.com/ubuntu hardy-security main restricted
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted
deb http://security.ubuntu.com/ubuntu hardy-security universe
deb-src http://security.ubuntu.com/ubuntu hardy-security universe
deb http://security.ubuntu.com/ubuntu hardy-security multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security multiverse
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

---

### Post by Forlong on 2008-05-22
> **grayfox444 said:**
> ```
deb http://download.tuxfamily.org/3v1deb [COLOR="Red"]feisty[/COLOR] eyecandy
deb-src http://download.tuxfamily.org/3v1deb [COLOR="Red"]feisty[/COLOR] eyecandy
```
Open the file being root, e.g.
```
sudo gedit /etc/apt/sources.list
``` and remove those lines.

Afterwards, run ```
sudo apt-get update
```

---

### Post by grayfox444 on 2008-05-22
alright, i've done that, but i don't see compiz anywhere in the system -> preferences.

---

### Post by Forlong on 2008-05-22
I have "only" fixed your installation issue thus far.
Now run
```
sudo apt-get install compiz
```
Afterwards, go to *System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects* and enable it there.

---

### Post by grayfox444 on 2008-05-22
okay that's working now, thanks. but how do i access the advanced visual settings, ie desktop cube etc?

---

### Post by Forlong on 2008-05-22
[How to set up Compiz Fusion]("http://forlong.blogage.de/article/2008/4/26/How-to-set-up-Compiz-Fusion-074") :)

---

