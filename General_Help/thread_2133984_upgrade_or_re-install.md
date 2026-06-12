---
title: "upgrade or re-install"
date: 2013-04-09
forum: General Help
---

### Post by BillGod on 2013-04-09
I have looked around and can't really find an answer to this.  I have always tried out Ubuntu betas since 6.04 then re-install when the final release comes out.  If you just run and apt-get upgrade will that get you everything?  If they added a new feature since the beta will you get it?  My problem is for some reason my computer WILL NOT install the BETA 2.  I have not had time to trouble shoot why but I already have BETA 1 running.  Does anyone know for sure if I will be running the exact same thing as the final version when its released or would I have to re-install?

---

### Post by snowpine on 2013-04-09
Simply "apt-get upgrade" by itself will not get you from the beta to the final release. The full command you want to run is:

```
sudo apt-get update && sudo apt-get dist-upgrade
```

---

### Post by Frogs Hair on 2013-04-09
There was no need for commands with 12,10 beta the distribution updates came via the update manager and I would expect the same with 13.04.

---

