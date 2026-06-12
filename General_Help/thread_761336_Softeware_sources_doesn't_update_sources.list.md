---
title: "Softeware sources doesn't update sources.list"
date: 2008-04-21
forum: General Help
---

### Post by marn on 2008-04-21
My father has an odd problem with his sources.list file. Most entries are commented out (see below) and using System -> Admin -> Software Sources doesn't alter the sources.list file. And now the strange thing. Programs can still be installed
```
sudo apt-get install thunderbird
```
worked fine, as did 
```
sudo apt-get install ubuntu-restricted-extras
```
after having added the medibuntu repository. The medibuntu repostiory isn't even listed in the sources.list file!

Now if all comments (#) are removed, running 
```
sudo apt-get update
```
complains about duplicate entries (sorry, don't have the correct wording for that as I haven't got direct access to the computer he works on)

He is running ubuntu 7.10 64-Bit version - has that got anything to do with it?

Appreciate any help

Here is the /etc/apt/sources.list file:
> # deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016)]/
gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade
to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates main
restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as
to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu
security
## team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the
Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as
to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the
'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it
includes
## newer versions of some applications which may provide useful
features.
## Also, please note that software in backports WILL NOT receive any
review
## or updates from the Ubuntu security team.
# deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main
restricted universe multiverse
# deb-src [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy-backports main
restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to
Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main
restricted
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse universe
restricted main
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by skymera on 2008-04-21
You can uncomment them manually, that's what i tend to do.

---

### Post by marn on 2008-04-21
Yes, that is what I did. The response that I got was, after running sudo apt-get update, that there were duplicate entries. As far as I can work out that means ubuntus looking at a list somewhere else as well, although, as far as I understand, that cannot be.

---

### Post by plucky on 2008-04-21
Can you post your sources.list after you have changed it.

I think you need to comment out this line > deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) gutsy multiverse universe restricted main which is near the end of the file as further up the list you also have the
 > deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy main restricted
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://gb.archive.ubuntu.com/ubuntu/](http://gb.archive.ubuntu.com/ubuntu/) gutsy multiverse repositories.

So if you have both uncommented then you will get the multiple repository message.


Good Luck

---

### Post by marn on 2008-04-21
Thanks Plucky, that makes sense. I will try that, that is get my father to try it (make take a day or two)

As to the lines "# Line commented out by installer because it failed to verify:" I suppose they can all be deleted.

What I don't understand though, is why the software sources application doesn't sort things out properly? Doesn't it rewrite the sources.list?

---

