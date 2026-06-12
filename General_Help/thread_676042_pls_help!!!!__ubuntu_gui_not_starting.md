---
title: "pls help!!!!  ubuntu gui not starting"
date: 2008-01-23
forum: General Help
---

### Post by alwar.sumit on 2008-01-23
i installed gusty on my pc two days ago.Till today morning it worked fine but suddenly i don't what happen it stopped working.

On booting it is showing 

* Starting anac(h) ronistic cron anacron                                                                                      [OK]
* Starting deffered execution scheduler atd                                                                                 [OK]
* Starting periodic command schedular crond                                                                              [OK]
*Checking battery state ..                                                                                                              [OK]
*Running local boot scripts (/etc/rc.local)                                                                                     [OK]

and then after no processing and system stucks ....here ....

PLease give some solution if nay there ...

---

### Post by dorav on 2008-01-23
> **alwar.sumit said:**
> i installed gusty on my pc two days ago.Till today morning it worked fine but suddenly i don't what happen it stopped working.

On booting it is showing 

* Starting anac(h) ronistic cron anacron                                                                                      [OK]
* Starting deffered execution scheduler atd                                                                                 [OK]
* Starting periodic command schedular crond                                                                              [OK]
*Checking battery state ..                                                                                                              [OK]
*Running local boot scripts (/etc/rc.local)                                                                                     [OK]

and then after no processing and system stucks ....here ....

PLease give some solution if nay there ...


Sumit , i am  also facing the same problem....

---

### Post by pointone on 2008-01-23
Try hitting Ctrl+Alt+F7. If this doesn't take you to a GUI, hit Ctrl+Alt+F2; you should see a login prompt. Log in and run the command:

```
sudo /etc/init.d/gdm restart
```

... and let us know what happens.

---

### Post by alwar.sumit on 2008-01-24
sorry pointone............bcoz i cant tell u wat happens........i've formatted my pc...........

thanks alot

---

### Post by peabody on 2008-01-24
Try Alt+f2, see if you have a textual login prompt.  If so, login from there and try 'startx'

---

