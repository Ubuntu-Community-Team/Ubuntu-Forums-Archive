---
title: "Last Kernel Breaks a lot of wine programs and other Linux programs like firefox"
date: 2015-07-28
forum: General Help
---

### Post by miguelpires on 2015-07-28
I use Ubntu 14.04 in more then one off my machines, and the last kernel Breaks the wine-staging and some other progrmas like my weather.
Anyone with this problems? If yes please subscribe to this bug: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1478844](https://bugs.launchpad.net/ubuntu/+source/ubuntu-release-upgrader/+bug/1478844)

---

### Post by dino99 on 2015-07-28
so if you boot on an older kernel you does not get these crashes ?
which makes you feeling that the latest kernel need to be blamed ?

---

### Post by miguelpires on 2015-07-28
Yes if I boot with old kernel I don't the crashs in wine, only in Firefox.

---

### Post by Dave_Rove on 2015-07-28
I confirm this. Since updating today to kernel 3.13.0-59, wine will not start.

If I boot with the old kernel 3.13.0-24, then wine does start.

I've tried replacing the Ubuntu 14.04 version of wine (1.6.2) with the latest 1.7 but it has the same problem.

Edit: A workaround that seems reliable is to start wineserver first from the command line, then start wine, and then it works OK. On exit from the program running on wine, the wineserver terminates normally.

---

### Post by monkeybrain20122 on 2015-07-28
There you go about LTS being more stable. I  don't know what the problem is but it seems that LTS upgrades always become problematic after a while, probably most manpower has gone to newer releases and U+1 (and mobile) So for me 2 years is Max for any Ubuntu release despite theoretically Canonical supports LTS for 5 years (so 12.04 is probably crap by now)  But 14.04 hasn't even passed the two year poin.

I would just upgrade to the latest mainline kernel. I have been using 4.0.x and 4.1.x on 14.04 for a while and had not experience any problem. [http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.3-unstable/](http://kernel.ubuntu.com/~kernel-ppa/mainline/v4.1.3-unstable/)

---

### Post by Dave_Rove on 2015-07-30
Kernel 3.13.0-61 has appeared and that fixes the wine issue for me.

---

