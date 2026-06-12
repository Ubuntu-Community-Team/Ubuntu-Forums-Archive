---
title: "lincity in the repository"
date: 2006-08-08
forum: General Help
---

### Post by Ramaddan on 2006-08-08
Hi,

I wasn't sure where to ask this question, but here goes.

I was just wondering who to ask about when the game lincity-ng
in the repository will be upgraded to the latest release.

The current release in the repository is 1.0.2,
and the one currently available is 1.0.3 which fixes a few things.

The site is:
[http://lincity-ng.berlios.de/wiki/index.php/Download/Installation](http://lincity-ng.berlios.de/wiki/index.php/Download/Installation)

If we wanted to provide packages that we did ourself for any program,
who do we contact to get it looked over maybe, and uploaded into the
mainstream?

What are the guidelines?

Thanks for your help.

---

### Post by mtron on 2006-08-08
dapper is in freeze since some weeks before the release, hence no new program versions will be added.

Look in the repos of edgy (drapper +1) most likely there will bew the new release. if not, look at the version in the debian sid (unstable) repos cause they will be synced with edgy (i think they they should  already be in sync. I'm not following the edgy development circle so close...).

If there is a difference between the versions in edgy & sid contact  a ubuntu [motu]("https://wiki.ubuntu.com/MOTU") or a [upstream maintainer]("http://lincity-ng.berlios.de/wiki/index.php/Contact") (= the person who currently maintains that program, outside of debian or ubuntu) for a precompiled "binary" sid (should work on edgy too) package.

cheers 
mtron

---

### Post by Gustav on 2006-08-08
You could also ask for a backport.

---

