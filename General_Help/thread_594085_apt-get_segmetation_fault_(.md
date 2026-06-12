---
title: "apt-get segmetation fault :("
date: 2007-10-27
forum: General Help
---

### Post by peromalosutra on 2007-10-27
I just started Synaptic to install smt and after asking me for password it simply closed..I went into terminal and typed:
```

ivan@ivan-desktop:~$ sudo apt-get install xmms
Reading package lists... Done
Segmentation fault (core dumped)

```
So it apears that the problem is with apt-get.. I know that I didn't give you enoug information, I'm not shure where the error logs are..

I cannot live without apt-get, help!

Ps_ reboot didn't helped.

---

### Post by taurus on 2007-10-27
Is that a fresh Gutsy or did you upgrade it to Gutsy from a previous release?  What happen if you run this?

```
sudo apt-get update
```
Otherwise, post your /etc/apt/sources.list.

```
cat /etc/apt/sources.list
```

---

### Post by peromalosutra on 2007-10-27
I did a fresh install. Before I used Ubuntu 6.10 and it all worked great.. But know.. huh..
So, here's the sources.list file:
```

ivan@ivan-desktop:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ba.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://ba.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ba.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://ba.archive.ubuntu.com/ubuntu/ gutsy universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ba.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://ba.archive.ubuntu.com/ubuntu/ gutsy multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://ba.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://ba.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://security.ubuntu.com/ubuntu/ gutsy-security restricted main multiverse universe
# deb http://static.audacious-media-player.org/ubuntu edgy main

```

i run sudo apt-get update but still I get the same error. :s

---

### Post by chrisccoulson on 2007-10-27
Are you definately using Gutsy final?

Try downloading the latest apt deb from [http://packages.ubuntu.com/gutsy/base/apt]("http://packages.ubuntu.com/gutsy/base/apt") and installing with dpkg.

---

### Post by peromalosutra on 2007-10-28
Thanks alot, it worked!
I downloaded and installed new apt from the link you gave me, and it's all ok now. I don't know why this happend in the first place, I'm using 7.10 for few days now and I manage to install all the programs I needed without any problems.. Until yesterday..

But, now it's all ok, thanks again!

PS: Yes, I'm using 7.10 finall, I did a fresh install over Ubuntu 6.10 that was there before.

---

