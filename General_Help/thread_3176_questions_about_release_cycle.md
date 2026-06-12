---
title: "questions about release cycle"
date: 2004-11-04
forum: General Help
---

### Post by ChrisQ on 2004-11-04
Here's a couple questions I have about ubuntu:
1) There is essentially a package freeze for six months right? No new software except for security updates?
2) Is there a development repository I can add to get a more even package release cycle? Ie, I'd really like to be running x.org right now as well as xchat 2.4.
3) If there is said development repository, how stable is it? Is it debian unstable/testing stable or is it mandrake development unstable? (it's my experience that debian unstable is fine to run and usually has the same stability as a mandrake .0 release, while mandrake development repositories are scary to run anythin on).

Thanks,

Chris

---

### Post by Bob D. on 2004-11-04
> There is essentially a package freeze for six months right? No new software except for security updates?
Yes, that's my understanding. What's in Warty is it except for the security updates.

> Is there a development repository I can add to get a more even package release cycle? Ie, I'd really like to be running x.org right now as well as xchat 2.4.
Change your sources.list from warty to hoary. You'll get access to the current packages in Debian sid. See Matt Zimmerman's cautions  [here](http://www.ubuntuforums.org/showthread.php?t=2522). I don't think x.org is there yet based on the info on [this wiki page](http://www.ubuntulinux.org/wiki/HoaryGoals).

> If there is said development repository, how stable is it?
See above.

---

