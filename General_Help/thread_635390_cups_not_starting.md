---
title: "cups not starting"
date: 2007-12-08
forum: General Help
---

### Post by go_beep_yourself on 2007-12-08
Cups is not running after booting my computer. How can I get it to run automatically when booting my computer. Cups does not show in bum, so I would rather correct the problem using some other software. This is what happens after booting my computer. I must run sudo /etc/init.d/cupsys start each time I reboot to have the printer working.

```
chris@ubuntu:~$ lp
lp: Error - scheduler not responding!
chris@ubuntu:~$ sudo /etc/init.d/cupsys status
[sudo] password for chris:
Status of Common Unix Printing System: cupsd is not running but /var/run/cups/cupsd.pid exists.
chris@ubuntu:~$ 
```

---

### Post by linuxwizard on 2007-12-09
See if this will help you.
[http://ubuntuforums.org/showthread.php?t=636479&highlight=start+cups](http://ubuntuforums.org/showthread.php?t=636479&highlight=start+cups)

---

