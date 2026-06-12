---
title: "No updates in a week?"
date: 2007-04-20
forum: General Help
---

### Post by mrpeenut24 on 2007-04-20
I've been using Feisty for a couple months now, and I've been updating my system about twice a day, and each time there were always updates.  However, for the past week or so, there have been almost NO updates at all.  I think there was one update for the gnome-application-menu or something like that, but other than that, nothing.  I would think that with the release date happening, there would be updates more often.  But almost a week with only one or two applications updated at all?  I thought it was something to do with my sources.list file.  Can anyone tell me if there just aren't many releases happening?  Or if it's a problem with my sources.list file?  Here it is:
```

deb-src http://archive.ubuntu.com/ubuntu/ feisty restricted main #Added by software-properties


deb http://us.archive.ubuntu.com/ubuntu/ feisty main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty restricted main multiverse universe

## Major bug fix updates produced after the final release of the
## distribution.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-updates main multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-updates main multiverse restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://us.archive.ubuntu.com/ubuntu/ feisty-backports main universe multiverse restricted
deb-src http://us.archive.ubuntu.com/ubuntu/ feisty-backports main universe multiverse restricted


deb http://security.ubuntu.com/ubuntu feisty-security main multiverse restricted
deb-src http://security.ubuntu.com/ubuntu feisty-security restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-proposed restricted main multiverse universe
deb http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb-src http://archive.ubuntu.com/ubuntu/ feisty-updates restricted main multiverse universe
deb http://security.ubuntu.com/ubuntu feisty-security universe
deb http://ubuntu.beryl-project.org feisty main
deb http://nvidia.limitless.lupine.me.uk/ubuntu edgy stable unstable
## deb http://givre.cabspace.com/ubuntu/ edgy main main-all
deb http://ntfs-3g.sitesweetsite.info/ubuntu/ edgy main main-all
deb http://flomertens.keo.in/ubuntu/ edgy main main-all
```
Thanks.

---

### Post by dpar on 2007-04-20
Nope......no updates for a while now.
I don't think anyones been getting much.

---

### Post by mrpeenut24 on 2007-04-20
Thanks.  :-D

---

### Post by NikoC on 2007-04-20
Confirmed ;)

---

### Post by wersdaluv on 2007-04-20
Me too. I have been running Feisty Beta. I tried to update to the Official Feisty release, but no updates for me. 

I presume, yesterday was just a formal release, but Feisty was already finished a few days before April 19, 2007.

---

### Post by wgrant on 2007-04-20
The point of a release candidate is that is it a candidate for release. In this case, it was deemed good enough after testing, so there were no updates to the base packages for some days before the release.

---

