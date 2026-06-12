---
title: "packages fail to authenticate"
date: 2008-02-17
forum: General Help
---

### Post by malfist on 2008-02-17
I keep getting warnings about untrusted packages because they can't be verified with ubuntu when I install or update new packages. What's up with that? Should I be worried?

Here's my /etc/apt/sources.list file:
```

deb file:/var/cache/apt-build/repository apt-build main
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
deb http://archive.ubuntu.com/ubuntu/ gutsy main restricted universe multiverse
deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-updates restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ gutsy-backports restricted main multiverse universe
deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse

#virtualbox
deb http://www.virtualbox.org/debian gutsy non-free

```

---

### Post by zvacet on 2008-02-17
You don´ have to be  worried about that,bacause you have only Ubuntu repos.You can run 

```
sudo apt-get update
```

to refresh your source list.

---

### Post by yabbadabbadont on 2008-02-17
> **zvacet said:**
> You don´ have to be  worried about that,bacause you have only Ubuntu repos.You can run 

```
sudo apt-get update
```

to refresh your source list.

```
#virtualbox
deb http://www.virtualbox.org/debian gutsy non-free
```
Only Ubuntu repos you say....  since when did Ubuntu buy virtualbox?  ;)

(They didn't, Sun did.  :D)

To the OP: You either need to get the gpg key for the virtual box repo and add it using the "apt-key add" command, or comment out that repo and run the "sudo apt-get update" command again.

---

### Post by zvacet on 2008-02-17
> Only Ubuntu repos you say.... since when did Ubuntu buy virtualbox?

Yes,I overlooked that.My mistake.

@** malfist**

From wich repos comes that untrusted packages?

---

### Post by malfist on 2008-02-19
from the all over, packages like ALSA, qtparted, etc.

---

### Post by yabbadabbadont on 2008-02-19
Get into Synaptic and edit the repositories.  Disable **all** of the repos and save the change.  Reload (shouldn't take long since you have none enabled ;)).  Now go back in and enable just the official repositories.  Reload again.  Run some tests to see if you still get the errors.

---

### Post by malfist on 2008-02-20
comment everything out? I don't want to reinstall alsa, I have a custom compilation installed right now (talk about hell making my soundcard work :P). qtparted isn't doing it anymore. Maybe the apt-get update fixed it. If I come across another package that does it I'll repost.

---

### Post by malfist on 2008-02-20
I get a lot of 'failed' hits when updating. Most seem to be to translation en-us.

---

### Post by zvacet on 2008-02-20
If your source list look like one you posted 

```
sudo apt-get update && sudo apt-get upgrade
```

You don´t have to worry,you are geting updates from ubuntu repos.

---

### Post by malfist on 2008-02-26
alsa-base and linux-sound-base still fail to authenticate. I even ran apt-get clean.

---

