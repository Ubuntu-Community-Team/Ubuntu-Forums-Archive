---
title: "[SOLVED] Synaptic error"
date: 2007-12-11
forum: General Help
---

### Post by Xp3reMental on 2007-12-11
Every time I want to open synaptic I get this error message..

[IMG]http://i238.photobucket.com/albums/ff136/Xp3ereMental/Error2.jpg[/IMG]:(

now 'im a newbie so I have no Idea what do to..:confused:

Help would be apriciated:)

---

### Post by forestpixie on 2007-12-11
you've got a problem with the sources, do this in a terminal - paste the output here

```
cat /etc/apt/sources.list
```

---

### Post by Xp3reMental on 2007-12-11
okay so I did that and I got this (have no Idea what it means)

```
kerneels@Prodotype-ubuntu:~$ cat /etc/apt/sources.list
deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.

deb http://za.archive.ubuntu.com/ubuntu/ gutsy main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb http://za.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://za.archive.ubuntu.com/ubuntu/ gutsy universe
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy universe
deb http://za.archive.ubuntu.com/ubuntu/ gutsy-updates universe
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://za.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy multiverse
deb http://za.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse
deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://za.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://za.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

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
deb http://www.linuxmint.com/repository romeo/ apt-get update
deb http://www.linuxmint.com/repository romeo/
deb ttp://www.linuxmint.com/repository romeo/
deb http://www.linuxmint.com/repository romeo/
deb http://www.linuxmint.com/repository romeo/ apt-get update
kerneels@Prodotype-ubuntu:~$
```

---

### Post by PmDematagoda on 2007-12-11
Open the sources.list file for editing using:-

```
sudo gedit /etc/apt/sources.list
```

And change these last lines:-

```
deb http://www.linuxmint.com/repository romeo/ apt-get update
deb http://www.linuxmint.com/repository romeo/
deb ttp://www.linuxmint.com/repository romeo/
deb http://www.linuxmint.com/repository romeo/
deb http://www.linuxmint.com/repository romeo/ apt-get update

```

To these:-
```

#deb http://www.linuxmint.com/repository romeo/ apt-get update
#deb http://www.linuxmint.com/repository romeo/
#deb ttp://www.linuxmint.com/repository romeo/
#deb http://www.linuxmint.com/repository romeo/
#deb http://www.linuxmint.com/repository romeo/ apt-get update
```

Save the edited file and then do:-

```
sudo apt-get update
```

That should fix your problem.

---

### Post by forestpixie on 2007-12-11
do this in a terminal it will open it for editing - you'll need to supply your password

```
gksudo gedit /etc/apt/sources.list
```
 on the first line put a # before > deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon
delete the last four lines and change the remaining last line to read

> deb [http://www.linuxmint.com/repository/romeo/](http://www.linuxmint.com/repository/romeo/)

then save and close, in a terminal

```
sudo apt-get update
```

if you get errors post here but I think that should be it
> 
(have no Idea what it means)


each line is a repository containing packages of software- when you open add/remove or synaptic or do apt-get or aptitude in a terminal - these places are where the software is downloaded from

---

### Post by p_quarles on 2007-12-11
That would fix the problem, but what if the OP is using Linux Mint? He/she will want to have that repository enabled. 

My suggestion would be to get rid of all the lines involving Mint, and to replace them with the correct repository address for Mint Romeo:
```
[SIZE=2]deb http://www.linuxmint.com/repository romeo daryna
```
The "apt-get update" thing is a command that should be run in the terminal, not something that is inserted into the repository list. 
[/SIZE]

---

### Post by Xp3reMental on 2007-12-11
Thats it thanx

---

### Post by forestpixie on 2007-12-11
went looking for the repo for linux mint and the one I left in the sources list was the one which seemed to be the right one 

if you're done can you mark thread solved

---

### Post by p_quarles on 2007-12-11
> **forestpixie said:**
> went looking for the repo for linux mint and the one I left in the sources list was the one which seemed to be the right one 

if you're done can you mark thread solved
It was the right one, it was just formatted wrong. Here's the official info:
[http://linuxmint.com/rel_daryna.php](http://linuxmint.com/rel_daryna.php)

---

### Post by forestpixie on 2007-12-11
cheers remember that one - linuxmint is a new one to me -  - but then ubuntu was as well in may :)

---

