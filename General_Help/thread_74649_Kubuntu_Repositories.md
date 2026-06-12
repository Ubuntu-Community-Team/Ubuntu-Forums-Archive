---
title: "Kubuntu Repositories?"
date: 2005-10-12
forum: General Help
---

### Post by TheIdiotThatIsMe on 2005-10-12
Hi, I found when going through a thread that someone had repositories specifically for Kubuntu (with the word kubuntu in them) and realized I dont have those in my sources.list file, and I'm going to probably need them in order to do the upgrade to Breezy for Kubuntu. Does anyone know where I can find these repos to put them back into my sources.list file? (It's also not in my sources.list_backup)

---

### Post by palsyboy on 2005-10-14
Here's my sources.list:

```

deb cdrom:[Kubuntu 5.04 _Hoary Hedgehog_ - Release i386 (20050407)]/ hoary main restricted

deb http://us.archive.ubuntu.com/ubuntu hoary main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary main restricted

## Uncomment the following two lines to fetch major bug fix updates produced
## after the final release of the distribution.
deb http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted
deb-src http://us.archive.ubuntu.com/ubuntu hoary-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu hoary universe
deb-src http://us.archive.ubuntu.com/ubuntu hoary universe

deb http://security.ubuntu.com/ubuntu hoary-security main restricted
deb-src http://security.ubuntu.com/ubuntu hoary-security main restricted

deb http://security.ubuntu.com/ubuntu hoary-security universe
deb-src http://security.ubuntu.com/ubuntu hoary-security universe

deb http://archive.ubuntu.com/ubuntu hoary multiverse
deb-src http://archive.ubuntu.com/ubuntu hoary multiverse

## Backports
deb http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted
deb-src http://archive.ubuntu.com/ubuntu hoary-backports main universe multiverse restricted

```

---

