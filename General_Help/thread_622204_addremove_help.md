---
title: "add/remove help"
date: 2007-11-24
forum: General Help
---

### Post by onlyproductions on 2007-11-24
ok, i just installed ubuntu on my comp and when ever i check an item in teh add/remove programs thing it says that the list must be reloaded so i click reload. Then it downloads 6 things. Then i check the item agian to tell the comp i want to download it and the same thing happens. I really like linux but i cant find an answer. My internet is wrking fine

---

### Post by -grubby on 2007-11-24
try going to system>Administration>synaptic and see if it still happens

---

### Post by rsambuca on 2007-11-24
Could be a problem with your software repositories for some reason.  Open a terminal (Applications -> Accessories -> Terminal) and enter the following:```
cat /etc/apt/sources.list
```Post the output here and we should be able to fix things.

---

### Post by nandorj78 on 2007-11-24
I very new to Ubuntu (installed it last night and I'm completely lost!). I'm also having this problem, so I entered what you aksed and here's the message:

```

nando@nando-laptop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
# deb http://br.archive.ubuntu.com/ubuntu/ gutsy main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
# deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
# deb http://br.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy universe
# Line commented out by installer because it failed to verify:
# deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates universe
# Line commented out by installer because it failed to verify:
# deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
# deb http://br.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy multiverse
# Line commented out by installer because it failed to verify:
# deb http://br.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security main restricted
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security universe
# Line commented out by installer because it failed to verify:
# deb http://security.ubuntu.com/ubuntu gutsy-security multiverse
# Line commented out by installer because it failed to verify:
# deb-src http://security.ubuntu.com/ubuntu gutsy-security multiverse
nando@nando-laptop:~$ 

```

---

### Post by rsambuca on 2007-11-24
> **nandorj78 said:**
> I very new to Ubuntu (installed it last night and I'm completely lost!). I'm also having this problem, so I entered what you aksed and here's the message:


There is something wrong with your repos (is your internet connection working?).  Go to System -> Administration -> Software Sources.  Make sure the boxes are checked.  Press the "Download from" Button and select "Other".  Press "Select Best Server".  It will test all of the software repository mirrors and select the quickest one to your location.  After that you should be fine.

---

### Post by HermanAB on 2007-11-24
Hmm, note that in Linux, just like in that other much maligned OS, installing things is straight forward, but removing things isn't.  The problem is that by installing schtuff, you are increasing the entropy of your system and undoing entropy is like trying to make water run uphill.

Fortunately, Linux applications are usually quite small, so you usually need not uninstall them.  So you can save yourself a lot of hair by not trying to uninstall stuff.

Just my tuppence worth.

Cheers,

H.

---

