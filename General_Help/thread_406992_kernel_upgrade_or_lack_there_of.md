---
title: "kernel upgrade or lack there of"
date: 2007-04-11
forum: General Help
---

### Post by Nythain on 2007-04-11
Ok, so for the last few months now... every time i run aptitude, it always kept back the linux-image-generic, linux-headers-generic and linux-restricted-modules-generic from my upgrades... that never really botherd me much since i knew i was going to be installing feisty eventually anyways.

Well now i've got the feisty goodness and still aptitude is keeping back those upgrades...
Any clue why??? and will not getting the linux-headers-generic prohibit the installation and use of any software (like nvidia drivers)???
Is there a fix for this... i would like to stay up to date, and also at least have certain packages that are available, but no matter what i try it just wont let me grab those three...

Thanks a bunch
ps you guys dont joke when you suggest burning the iso's at a super slow speed... i downloaded an burnt feisty this morning at max speed, tried installing 3 times and it hung at 91% each time, so i decide to check the iso and do the recomended burn at slow speed (i used 2x) and viola, much better

---

### Post by zvacet on 2007-04-11
```
 sudo apt-get update && sudo apt-get dist-upgrade
  sudo apt-get -f install
  sudo dpkg --configure -a 
```

---

### Post by Nythain on 2007-04-11
you are my hero... thank you so much... i guess from now on ill have to run dist-upgrade then upgrade

---

