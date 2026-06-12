---
title: "Add/Remove Program problem"
date: 2007-11-09
forum: General Help
---

### Post by dannyngweekiat_85 on 2007-11-09
every time i run add/remove program it would ask me to reload the source list and it will fail. I have to go to preference and search for the best server. It will change the server and manage to update for the time. After i restart ubuntu the i will have the same error again and have to repeat selecting server. Any step to solve this?

---

### Post by geirha on 2007-11-09
does ```
sudo aptitude update
``` also fail?

---

### Post by dannyngweekiat_85 on 2007-11-09
ooo... after using sudo i am able to update. without changing the server. why is it so? 

Edited: After restarting my pc i have to 

```
sudo aptitude update
```

again to be able to use add/remove.

---

### Post by dannyngweekiat_85 on 2007-11-09
now sudo update i get this and fail to update 

```
0danny@danny-desktop:~$ sudo aptitude update
[sudo] password for danny:
0% [Connecting to ftp.hostrino.com (1.0.0.0)]

```

---

### Post by Maestro23 on 2007-11-09
> **dannyngweekiat_85 said:**
> now sudo update i get this and fail to update 

```
0danny@danny-desktop:~$ sudo aptitude update
[sudo] password for danny:
0% [Connecting to ftp.hostrino.com (1.0.0.0)]

```

Post your sources.list

> cat /etc/apt/sources.list

---

### Post by dannyngweekiat_85 on 2007-11-09
```
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy main restricted
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-updates main restricted
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy universe
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy universe
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-updates universe
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy multiverse
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy multiverse
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-updates multiverse
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-backports main restricted universe multiverse
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb http://archive.canonical.com/ubuntu gutsy partner
# deb-src http://archive.canonical.com/ubuntu gutsy partner

deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-security main restricted
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-security main restricted
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-security universe
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-security universe
deb http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-security multiverse
deb-src http://ftp.hostrino.com/pub/ubuntu/archive/ gutsy-security multiverse

```

Getting the ip 1.0.0.0 can it be Network configuration error?... i have no problem surfing the net and using torrent after disabling ipv6

---

### Post by Maestro23 on 2007-11-09
Looks like its just having trouble connecting to that server.  You can try changing your server in:

System>>Admin>>Software Sources.

---

### Post by dannyngweekiat_85 on 2007-11-09
anyone else have similar problem before? well i think the best method now is to stick with search for best server everytime i wanna add program... thx for helping! :KS

---

### Post by SkullFire on 2008-01-17
I wanna say thanks, this fixed my problem too :D

---

### Post by Zaopunk on 2008-01-18
I am having the exact same problem, but i have no clue how to disable ipv6. Any help please.

First I get this when I click to add Amarok:

"The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection. "

**Click 'Refresh' at the bottom of the error window and get:**

"Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.

cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/main/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/dists/gutsy/restricted/binary-i386/Packages.gz: Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs

Any suggestions would be wonderful. Thanks.
---Drive Fast, Take Chances, Leave a beautiful corpse---

---

### Post by geirha on 2008-01-18
System -> Administration -> Software Sources. Remove the cdrom from the list of repositories.

---

