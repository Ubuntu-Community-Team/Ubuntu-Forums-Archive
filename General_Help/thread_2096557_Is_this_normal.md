---
title: "Is this normal?"
date: 2012-12-20
forum: General Help
---

### Post by JCM_Pico on 2012-12-20
Hello....

My dmesg is full of this:

```
[ 5497.150222] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[ 5794.635345] CPU1: Package power limit notification (total events = 1127)
[ 5794.635348] CPU2: Package power limit notification (total events = 1129)
[ 5794.635349] CPU0: Package power limit notification (total events = 1129)
[ 5794.635350] CPU3: Package power limit notification (total events = 1128)
[ 5794.635445] CPU1: Package power limit normal
[ 5794.635446] CPU2: Package power limit normal
[ 5794.635447] CPU0: Package power limit normal
[ 5794.635448] CPU3: Package power limit normal
[ 9331.435901] CPU3: Package power limit notification (total events = 1237)
[ 9331.435904] CPU2: Package power limit notification (total events = 1238)
[ 9331.435905] CPU0: Package power limit notification (total events = 1238)
[ 9331.435906] CPU1: Package power limit notification (total events = 1236)
[ 9331.436435] CPU1: Package power limit normal
[ 9331.436436] CPU3: Package power limit normal
[ 9331.436436] CPU2: Package power limit normal
[ 9331.436437] CPU0: Package power limit normal
[10189.410674] CPU1: Package power limit notification (total events = 1241)
[10189.410676] CPU2: Package power limit notification (total events = 1243)
[10189.410678] CPU3: Package power limit notification (total events = 1242)
[10189.410679] CPU0: Package power limit notification (total events = 1243)
[10189.410729] CPU1: Package power limit normal
[10189.410731] CPU2: Package power limit normal
[10189.410732] CPU3: Package power limit normal
[10189.410733] CPU0: Package power limit normal
[10425.954717] ehci_hcd 0000:00:1d.0: setting latency timer to 64
[10530.076608] CPU2: Package power limit notification (total events = 1579)
[10530.076611] CPU1: Package power limit notification (total events = 1579)
[10530.076612] CPU3: Package power limit notification (total events = 1580)
[10530.076614] CPU0: Package power limit notification (total events = 1580)
[10530.087650] CPU1: Package power limit normal
[10530.087651] CPU0: Package power limit normal
[10530.087653] CPU3: Package power limit normal
[10530.087654] CPU2: Package power limit normal

```

Is this normal?

---

### Post by Pjotr123 on 2012-12-20
Check this:
[http://superuser.com/questions/459354/the-meaning-of-thermal-throttle-counters-and-package-power-limit-notifications-i](http://superuser.com/questions/459354/the-meaning-of-thermal-throttle-counters-and-package-power-limit-notifications-i)

---

### Post by JCM_Pico on 2012-12-20
ok I understand that... but this is happening while my computer is IDLE with  a core temperature < than 50ºC !!!!

---

### Post by Bucky Ball on 2012-12-20
Um, all looks fine. dmesgs are generally long and go through everything that's happened. Try checking it out after a restart. If you are running less that 50 celcius and all is working, I wouldn't worry too much. Try to logically figure out what might be happening from the config of your machine. If no joy there, perhaps you can report s on Launchpad and help the devs:

[https://launchpad.net/](https://launchpad.net/)

---

