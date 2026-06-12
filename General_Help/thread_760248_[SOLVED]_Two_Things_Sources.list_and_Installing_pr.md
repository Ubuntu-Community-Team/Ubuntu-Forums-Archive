---
title: "[SOLVED] Two Things: Sources.list and Installing programs (like flash)"
date: 2008-04-20
forum: General Help
---

### Post by agrab0ekim on 2008-04-20
Okay, two things
1) My sources.list thing has been wiped clean for some reason. Can somebody post on here what it should say (vanilla?)
2) How does one install a program, say flash, properly?

---

### Post by brownknight on 2008-04-20
This is my vanilla sources.list. I am running Hardy Heron. So if you are using a different version just change the Hardy below to <whatever>

# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse

---

### Post by LaRoza on 2008-04-20
Flash: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by agrab0ekim on 2008-04-20
i am running Gusty (7.1).... so replace what?

---

### Post by agrab0ekim on 2008-04-20
> **LaRoza said:**
> Flash: [http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

how do i enable the universe/multiverse

---

### Post by brownknight on 2008-04-20
> **agrab0ekim said:**
> Okay, two things
1) My sources.list thing has been wiped clean for some reason. Can somebody post on here what it should say (vanilla?)
2) How does one install a program, say flash, properly?

There are 3 ways to install it: terminal, synaptic or add/remove from the application menu. From Add/Remove,  search for mozilla plugin and click to install.

---

### Post by agrab0ekim on 2008-04-20
> **brownknight said:**
> There are 3 ways to install it: terminal, synaptic or add/remove from the application menu. From Add/Remove,  search for mozilla plugin and click to install.

ALL three list problems with the sources.list, hence why i am working on that too

---

### Post by brownknight on 2008-04-20
> **agrab0ekim said:**
> i am running Gusty (7.1).... so replace what?

replace "hardy" to "gutsy"

---

### Post by brownknight on 2008-04-20
> **agrab0ekim said:**
> ALL three list problems with the sources.list, hence why i am working on that too

You can open up the sources.list and remove the # from the lines with the words multiverse and universe

---

### Post by brownknight on 2008-04-20
> **agrab0ekim said:**
> how do i enable the universe/multiverse

remove the # from the lines with the words multiverse and universe

---

### Post by LaRoza on 2008-04-20
> **agrab0ekim said:**
> how do i enable the universe/multiverse

Go to System->Administration->Synaptic and go to Repositories (it is in one of the menu's) and check them off.

---

### Post by agrab0ekim on 2008-04-20
source list is working now
will update (trying flash now)

---

### Post by LeoSolaris on 2008-04-20
Do a quick search for your sound card to see if there are already any tutorials or if it is a known issue. Most likely it has already been noticed as sound tends to be one of those bugs that gets immediate attention.

If you can't find anything about the issue, strike up a new post asking about it.

(Since I have no idea what sound card you're using, I can't can't help out.)

G'night
Leo

---

