---
title: "Update Manager error"
date: 2007-11-09
forum: General Help
---

### Post by enchance on 2007-11-09
I clicked on "Check" to check for updates and all went well but at the end I got this error
```

W: GPG error: http://security.ubuntu.com gutsy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: GPG error: http://ph.archive.ubuntu.com gutsy-updates Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

```

---

### Post by 1337455 10534 on 2007-11-09
Ya, you dont have GPG keys for those entries..
Open a terminal:
```

gksudo gedit /etc/apt/sources.list

```
keep the terminal open.
Scroll down to where the line "**[http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates Release**" or "**[http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release**" appears.

Find the GPG numner (or URL) and read the beginning of this text file for the rest of the directions.

---

### Post by enchance on 2007-11-10
> **1337455 10534 said:**
> Ya, you dont have GPG keys for those entries..
Open a terminal:
```

Scroll down to where the line "**[http://ph.archive.ubuntu.com](http://ph.archive.ubuntu.com) gutsy-updates Release**" or "**[http://security.ubuntu.com](http://security.ubuntu.com) gutsy-security Release**" appears.

Find the GPG numner (or URL) and read the beginning of this text file for the rest of the directions.

Sorry, I don't have that for some reason. I've posted my sources.list maybe you can see the problem.

[CODE]

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ph.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ph.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
deb http://security.ubuntu.com/ubuntu gutsy-security universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
deb http://ppa.dogfood.launchpad.net/amaranth/ubuntu feisty main

# Screenlets
deb http://hendrik.kaju.pri.ee/ubuntu gutsy screenlets

#Multimeda
deb http://mirror.ubuntulinux.nl gutsy-seveas all
deb-src http://mirror.ubuntulinux.nl gutsy-seveas all


```

---

### Post by 1337455 10534 on 2007-11-10
Right. Found it.
Do you have Apt-CD or something installed? Basically, do you install packages via apt from a CD? If not, remove this line or none of your upgrades will fully work.
```

deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

```
Worked for me anyway..
Next thing:
Stick this at the beginning of your sources.list so you dont forget:
```

# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

```
Replace "KEY" with the GPG number... Unfortunately, doing a search for "http://ph.archive.ubuntu.com gutsy-updates Release" as well as "http://security.ubuntu.com gutsy-security Release" in your sources gets no hits.. Meaning that you dont have those repositories at all.

Go to your System->Admin->Software Sources
Make sure everything is ticked available. Reload the info if needed.
If you get this error:
The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored.
, then you know that this is just an apt goof.

Good luck!

edit>> and sorry for taking so long to respond, fell asleep.

---

### Post by 1337455 10534 on 2007-11-10
If all fails you my friend, go to this excellent site, and THEN go to the software sources manager. Replace your sources.list with the one give, add the two lines I gave you at the top, and then customize your repos when you have a chance:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Excellent piece of work!

---

### Post by enchance on 2007-11-10
> **1337455 10534 said:**
> 
```

# gpg --keyserver hkp://subkeys.pgp.net --recv-keys KEY
# gpg --export --armor KEY | sudo apt-key add -

```
Replace "KEY" with the GPG number...

Where do I get the GPG number? I remember using the CD to install my modem and another program which requested for the Gutsy CD but that's about it. 

Should I still do what you mentioned (delete CDROM and add those 2 lines)?

---

### Post by 1337455 10534 on 2007-11-10
If you no longer need to install that package, definately. Dont delete it, but add a sharp sign next to it so that it wont be read:
```

#deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted

```
The GPG should be right above or next to every repos's entry:
```

# Ubuntu backports project
# GPG key: 437D05B5
deb http://us.archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu gutsy-backports main restricted universe multiverse

```
If not consider:
> 
If all fails you my friend, go to this excellent site, and THEN go to the software sources manager. Replace your sources.list with the one give, add the two lines I gave you at the top, and then customize your repos when you have a chance:
[http://www.ubuntu-nl.org/source-o-matic/](http://www.ubuntu-nl.org/source-o-matic/)

Excellent piece of work!

again...

---

### Post by zvacet on 2007-11-10
```
sudo aptitude update
```

should give you new keys.

---

### Post by enchance on 2007-11-10
> **zvacet said:**
> ```
sudo aptitude update
```

should give you new keys.

It wokred! I'm not getting an error anymore. I guess all you really have to do is update it.

---

### Post by 1337455 10534 on 2007-11-11
aptitude does the same thing apt does but comerr doesn't have a brain fart (i.e bf)  during update...
Notice, if you have missing keys or repeated sources, it asks you to run apt-get update...

---

