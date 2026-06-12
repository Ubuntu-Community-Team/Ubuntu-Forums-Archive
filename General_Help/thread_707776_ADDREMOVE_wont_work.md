---
title: "ADD/REMOVE wont work"
date: 2008-02-25
forum: General Help
---

### Post by skylinedna on 2008-02-25
it says that there a serious problem when i try to open it and i need to check /etc/apt/sources.list and that i should sudo update or as you see what i typed below and it came up with following error?


sudo apt-get install -f
E: Malformed line 64 in source list /etc/apt/sources.list (dist parse)
E: The list of sources could not be read.

---

### Post by zvacet on 2008-02-25
```
cat /etc/apt/sources.list
```

Post it here.

---

### Post by skylinedna on 2008-02-25
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy restricted multiverse universe main
# Line commented out by installer because it failed to verify:

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-updates restricted multiverse universe main
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb [http://nz.archive.ubuntu.com/ubuntu/](http://nz.archive.ubuntu.com/ubuntu/) gutsy-backports restricted multiverse universe main

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security restricted multiverse universe main
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy restricted
deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) gutsy-security restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-updates restricted
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-proposed restricted multiverse universe main
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy-backports restricted
deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
deb [http://amule-debian.dyndns.org](http://amule-debian.dyndns.org) debian




sorry its probably something silly but i wont learn if i dont ask


actually man sorry i just fixed it myself  i added some third party to try download amule and now i reversed it its working again thanks anyway :)  i do feel stupid now

---

### Post by stevejesus on 2008-02-25
Well, now that you know what it looks like, you should really clean that thing up!  There are alot of unnessesary stuff in there, that I guess was generated by some other program.
Just open it in a text editor with Admin rights.

---

### Post by warbird on 2008-02-25
seems it chokes on this line:
deb [http://amule-debian.dyndns.org](http://amule-debian.dyndns.org) debian

What is it?
you can comment it out (adding a # in front of it), and things should work

---

### Post by zvacet on 2008-02-25
Make this lines 

deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
deb [http://amule-debian.dyndns.org](http://amule-debian.dyndns.org) debian

like this 

#deb [http://blognux.free.fr/debian](http://blognux.free.fr/debian) unstable main
#deb [http://amule-debian.dyndns.org](http://amule-debian.dyndns.org) debian

or you can even delete it from source list.Mixed repos are not recommended.You see why.When you change your source list 

```
sudo apt-get update && sudo apt-get upgrade
```

---

