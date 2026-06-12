---
title: "[SOLVED] synapatic, update manager, and nautilus not working"
date: 2008-06-03
forum: General Help
---

### Post by cptnff on 2008-06-03
So I upgraded from gutsy to hardy about a month ago and have had many problems ever since. the things I really want to fix is my nautilus, synaptic package manager, and update manager. My update manager opens, but when i click on install update instead of the password window popping up, the update manager freezes. Now my nautilus, and synaptic package manager both have the same problem, they refuse to open. 

at first I thought my problem had something to do with what ever program is responsible for prompting you to put in your password, because of the problem I had with update manager, and the fact that both nautilus, and synaptic package manager, also require your password to start. But I don't think that's it, because my network manger also ask for a password to unlock it and, that works just fine(well kind of, but thats another story for another time) anyhow that leads me to believe its something els. If you have any answers, help would be appreciated.

---

### Post by Oldsoldier2003 on 2008-06-04
> **cptnff said:**
> So I upgraded from gutsy to hardy about a month ago and have had many problems ever since. the things I really want to fix is my nautilus, synaptic package manager, and update manager. My update manager opens, but when i click on install update instead of the password window popping up, the update manager freezes. Now my nautilus, and synaptic package manager both have the same problem, they refuse to open. 

at first I thought my problem had something to do with what ever program is responsible for prompting you to put in your password, because of the problem I had with update manager, and the fact that both nautilus, and synaptic package manager, also require your password to start. But I don't think that's it, because my network manger also ask for a password to unlock it and, that works just fine(well kind of, but thats another story for another time) anyhow that leads me to believe its something els. If you have any answers, help would be appreciated.

could you please post the output from and any error messages from

```
sudo apt-get update
sudo apt-get upgrade
```

you might also want to post the contents of your sources list

```
cat /etc/apt/sources.list
```

---

### Post by cptnff on 2008-06-08
sorry it took me so long to respond, to tell you the truth I forgot I started this thread, because I've been using vista all week. as for the first 2 codes you gave me they work just fine, but I did get this error message

"sudo: unable to resolve host myname-desktop"

but, I've been getting that any time I have to type sudo, since the upgrade to hardy. but as for the other code the results are:

```
# deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

deb cdrom:[Ubuntu 8.04 _Hardy Heron_ - Release i386 (20080423)]/ hardy main restricted
deb http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy main restricted universe multiverse

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse
deb-src http://us.archive.ubuntu.com/ubuntu/ hardy-updates main restricted universe multiverse

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://us.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

deb http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
deb-src http://security.ubuntu.com/ubuntu hardy-security main restricted universe multiverse
# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe

# deb http://de.archive.ubuntu.com/ubuntu dapper universe
# deb http://dvdstyler.sourceforge.net/repository/ubuntu/ dapper main

# deb-src http://ubuntu.beryl-project.org feisty main
  
# deb http://gandalfn.club.fr/ubuntu feisty motu


# deb http://download.tuxfamily.org/3v1deb feisty eyecandy
# deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

Am I missing something in my source list, or do I have something in my source list that could be causing my problems?

---

### Post by plucky on 2008-06-09
> "sudo: unable to resolve host myname-desktop"


See this [thread](http://ubuntuforums.org/showthread.php?t=723361) to fix your problem.

Good Luck

---

### Post by cptnff on 2008-06-09
Thank you the answer from post #23 seems to have done the trick

---

