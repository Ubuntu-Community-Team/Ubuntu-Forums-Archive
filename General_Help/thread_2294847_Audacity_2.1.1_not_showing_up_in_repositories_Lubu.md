---
title: "Audacity 2.1.1 not showing up in repositories Lubuntu 15.04"
date: 2015-09-13
forum: General Help
---

### Post by Cyb3rD0n Architectus on 2015-09-13
Hi, I noticed that while the Audacity audio editing software already has been released version 2.1.1 since July 16th 2015, but my computer is still running the 2.0.6 version, which is two release cycles behind the latest (it even skipped the version released in March 2015, 2.1.0. Now, I'm not entirely familiar with who is responsible for what concerning repositories, but seeing the version I'm running now is from 29 September 2014, it seems a bit strange it hasn't updated with the upgrade cycle of Lubuntu 15.04. :/

Is this a problem on my part or is someone not maintaining the repository for Audacity? I have refreshed the package information in my Synaptic Manager and it still says 2.0.6 is the latest version. Perhaps someone can confirm Audacity being 2.0.6 as the latest version in their (L)ubuntu package manager?

---

### Post by monkeybrain20122 on 2015-09-13
Ubuntu's software is frozen in that they don't get version updates. The easiest way to get the latest is to use ppas. This one has 2.1.1 [https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity](https://launchpad.net/~ubuntuhandbook1/+archive/ubuntu/audacity)

---

### Post by Dennis N on 2015-09-13
You are correct: 2.0.6-2 is the latest. (Candidate = newest version anywhere in sources).

```
dmn@Daphne:~$ apt-cache policy audacity
audacity:
  Installed: 2.0.6-2
  Candidate: 2.0.6-2
...

```

A newer one is unlikely to appear before the next release, if then: Lubuntu 15.10 beta is currently using the same version, I believe.

---

### Post by Cyb3rD0n Architectus on 2015-09-13
Thanks for the quick replies! I'll wait what version 15.10 is cooking up, otherwise I'll use monkeybrain's tip, as the improvements and bugfixes since 2.0.6 are too great to ignore...

---

### Post by Yellow Pasque on 2015-09-14
I doubt Wily/15.10 will have anything newer than 2.0.6 at this point in the release cycle:
[https://wiki.ubuntu.com/WilyWerewolf/ReleaseSchedule](https://wiki.ubuntu.com/WilyWerewolf/ReleaseSchedule)
[https://wiki.ubuntu.com/FeatureFreeze](https://wiki.ubuntu.com/FeatureFreeze)
[https://launchpad.net/ubuntu/+source/audacity](https://launchpad.net/ubuntu/+source/audacity)

---

### Post by ajgreeny on 2015-09-14
I am using the ppa version on my Xubuntu 14.04 and can tell you that it has not presented any problems, so if you really must have that version for some reason it is worth a try.

If it does  not work for you it is possible to make use of the **ppa-purge** utility (it's in the repos) to get you back to where you are now with version 2.0.6.

---

