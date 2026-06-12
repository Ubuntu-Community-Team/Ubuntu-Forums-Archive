---
title: "libavformat54"
date: 2015-05-23
forum: General Help
---

### Post by mdavis1231 on 2015-05-23
Can anyone tell me how to get this item to upgrade?  It's showing in the upgradable section of Synaptic Package Manager, yet won't upgrade.  I've tried "force version", but everytime I open Synaptic Package Manager back up, it's back in "upgradable".  What should I do?  I can't remove it because then it will remove Audacity, and I really like that program. ](*,)

---

### Post by ajgreeny on 2015-05-23
What version do you have at the moment?
Mine is 6:9.18-0ubuntu0.14.04.1 and I get no indication that an update is available on my Xubuntu 14.04.2  still running the 3.13.0-53 kernel, not the 3.16 kernel series.

Do you have all repositories enabled?
What version of audacity?

---

### Post by mc4man on 2015-05-23
simulate a dist-upgrade, if it completes without error do for real - 
first update sources
```
sudo apt-get update
```
then
```
sudo apt-get -s dist-upgrade
```
To do for real run the above command again without the -s

---

### Post by mdavis1231 on 2015-06-04
It seems that I had put in the repository for Bleachbit as 'Utopic', which you have to do to update to the latest version of Bleachbit without installing a .deb package, and which turned out to be a really bad idea.  It was wanting to update other things that would have made them incompatible with other items.  I removed the 'Utopic' repository for Bleachbit, and downgraded Bleachbit back down.  That solved the problem.

---

