---
title: "Ubuntu Server Slowness"
date: 2007-02-16
forum: General Help
---

### Post by Sitenl on 2007-02-16
Well, I'm trying to make my Ubuntu a Kubuntu, and I'm just failing, because of the Ubuntu Server... currently I'm trying to download Kopete, and it's not even transfiring something, and when it does, its bytes! This is annoying... is there any way to improve it? Here at least?

Obs: This started to happen 5 hours ago.

---

### Post by llamakc on 2007-02-16
Post your /etc/apt/sources.list. Perhaps it would move quicker if you used a mirror repository instead? Show us what you have and somebody can recommend a quicker set of sources.

---

### Post by Sitenl on 2007-02-16
```

## Major bug fix updates produced after the final release of the
## distribution.

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb http://br.archive.ubuntu.com/ubuntu/ edgy universe
# deb-src http://br.archive.ubuntu.com/ubuntu/ edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb http://br.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse
# deb-src http://br.archive.ubuntu.com/ubuntu/ edgy-backports main restricted universe multiverse

# deb http://security.ubuntu.com/ubuntu edgy-security universe
# deb-src http://security.ubuntu.com/ubuntu edgy-security universe
deb http://archive.ubuntu.com/ubuntu/ edgy universe main multiverse restricted
deb http://security.ubuntu.com/ubuntu/ edgy-security universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-proposed universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-backports universe main multiverse restricted
deb http://archive.ubuntu.com/ubuntu/ edgy-updates universe main multiverse restricted
```


Obs: I'm not using the brazilian server because it times in times have a downtime which already ruined my Kubunt.

---

