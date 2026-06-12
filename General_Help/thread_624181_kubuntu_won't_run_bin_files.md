---
title: "kubuntu won't run bin files?"
date: 2007-11-26
forum: General Help
---

### Post by zivxx on 2007-11-26
hey everyone...I'm trying to install mozilla firefox into kubuntu so i unzipped the tar.gz file into file called firefox, and inside it i have bin file called firefox-bin..i think that's how i run the firefox(is it?)...how do i open it?

---

### Post by PeterJS on 2007-11-26
You'd bet better off installing firefox through the repositories:
```

sudo apt-get install firefox

```

---

### Post by zivxx on 2007-11-26
ziv@ziv-desktop:~$ sudo apt-get install firefox
[sudo] password for ziv:
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package firefox is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package firefox has no installation candidate


..? :/

---

### Post by PeterJS on 2007-11-26
Well that is very odd. It should be there, you're source list might be messed up. Can you post the output of:
```

cat /etc/apt/sources.list

```

---

### Post by zivxx on 2007-11-26
root@ziv-desktop:/home/ziv# cat /etc/apt/sources.list
deb cdrom:[Kubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016.1)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

# Line commented out by installer because it failed to verify:
#deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# Line commented out by installer because it failed to verify:
#deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy universe
# Line commented out by installer because it failed to verify:
#deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates universe
# Line commented out by installer because it failed to verify:
#deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
# Line commented out by installer because it failed to verify:
#deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy multiverse
# Line commented out by installer because it failed to verify:
#deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://il.archive.ubuntu.com/ubuntu/](http://il.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by PeterJS on 2007-11-26
That's no good, all of your repositories are disabled. You're going to want to remove the # from the lines that begin with deb or deb-src, except for the ones that end in partner or include backports.

---

### Post by zivxx on 2007-11-26
how do i remove it?lol

---

### Post by PeterJS on 2007-11-26
with a text editor running as root, I'd suggest kate:
```

sudo kate /etc/apt/sources.list

```

---

### Post by zivxx on 2007-11-26
last thing, how do i know it includes backports?

---

### Post by PeterJS on 2007-11-26
I was trying to describe this block:
```

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://il.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse
# deb-src http://il.archive.ubuntu.com/ubuntu/ gutsy-backports main restricted universe multiverse

```
Generally you don't need backports until after the end of official support which is sitll a few years out.

---

### Post by zivxx on 2007-11-26
ooo thanks..then im done...but it say i don't have access to save?

---

### Post by PeterJS on 2007-11-26
did you run kate under sudo?

---

### Post by zivxx on 2007-11-26
i entered the command you gave me and what i get is,

root@ziv-desktop:/home/ziv# sudo kate /etc/apt/sources.list
Xlib: connection to ":0.0" refused by server
Xlib: No protocol specified

kate: cannot connect to X server :0.0

so i went on kate and just opened the file and tried to edit it...

---

### Post by PeterJS on 2007-11-26
Yeah, just running kate by itself won't have the security privilages to save the file, hence the need for sudo. Hmm, try:
```

gksu kate

```

---

### Post by zivxx on 2007-11-26
root@ziv-desktop:/home/ziv# gksu kate
The program 'gksu' is currently not installed.  You can install it by typing:
apt-get install gksu
bash: gksu: command not found
root@ziv-desktop:/home/ziv# apt-get install gksu
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package gksu is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package gksu has no installation candidate

---

### Post by PeterJS on 2007-11-26
It appears that we have a chick and egg problem on our hands. Can't fix the source because we don't have a text editor with elevated privilages, and can't get one because the sources are broken. I guess we'll have to use a command line editor instead:
```

sudo nano /etc/apt/sources.list

```
ctrl + o to save
ctrl + x to quit.

---

### Post by zivxx on 2007-11-26
ugh...line editor?

---

### Post by PeterJS on 2007-11-26
Sorry I tried everything else I could think of.

*grumble* Kids these days don't know how good they've got it, back in my day we marched up hill both ways in the snow, with no shoes, and used nano and liked it. :)

---

### Post by zivxx on 2007-11-26
oh got you, ok i edited it..what now?install firefox?

---

### Post by PeterJS on 2007-11-26
try:
```

sudo apt-get update
sudo apt-get install firefox

```

And it should work *crosses fingers*

---

### Post by zivxx on 2007-11-26
root@ziv-desktop:/home/ziv# sudo apt-get update
E: Type '0deb' is not known on line 1 in source list /etc/apt/sources.list


i did something wrong?lol

---

### Post by -grubby on 2007-11-26
edit the file and remove the "0"

---

### Post by PeterJS on 2007-11-26
Yeah looks like you've got an extra 0 just hanging out on line one that needs to be deleted.

---

### Post by zivxx on 2007-11-26
Its Working!#!!!
Its Workinggggggggg@@@!!!

---

