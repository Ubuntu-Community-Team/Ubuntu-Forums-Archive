---
title: "Upgrade Question, Please"
date: 2008-05-16
forum: General Help
---

### Post by wirelessman on 2008-05-16
I first uninstalled Automatix before doing my upgrade from 7.10.  The upgrade was done from over Internet.  After the upgrade, Java plugin no longer works.

The question of the day is: do I backup my data and do a clean install or repair each problem, one by one?

Also, if you plan to upgrade each year, what is the best install?

---

### Post by overdrank on 2008-05-16
> **wirelessman said:**
> I first uninstalled Automatix before doing my upgrade from 7.10.  The upgrade was done from over Internet.  After the upgrade, Java plugin no longer works.

The question of the day is: do I backup my data and do a clean install or repair each problem, one by one?

Also, if you plan to upgrade each year, what is the best install?

Hi and automatix is not recommended due to the fact it cause issues during upgrades and such. You can try and remove the repos from you system and repair
[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)
As for the upgrades I prefer a clean install.

---

### Post by Joeb454 on 2008-05-16
+1 for the clean install.

The last upgrade I did was 5.10 to 6.06 :) But I generally prefer clean installs, that way I know that it's all fresh ;)

---

### Post by Bubba64 on 2008-05-16
> **wirelessman said:**
> I first uninstalled Automatix before doing my upgrade from 7.10.  The upgrade was done from over Internet.  After the upgrade, Java plugin no longer works.

The question of the day is: do I backup my data and do a clean install or repair each problem, one by one?

Also, if you plan to upgrade each year, what is the best install?

The problem with Automatix installs is that even if you remove all of them it does not remove the peripheral installation that went with any install. I vote for a backup of important info and a fresh install.

---

### Post by forrestcupp on 2008-05-16
Don't do a clean install yet.  I upgraded without issues.

First, make sure that java is still installed:
```
sudo apt-get install sun-java6-plugin
```

Then make sure that openjdk is removed
```
sudo apt-get --purge remove openjdk*
```

Then java should work.

---

