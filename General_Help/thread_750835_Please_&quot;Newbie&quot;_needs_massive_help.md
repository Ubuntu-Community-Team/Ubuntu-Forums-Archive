---
title: "Please &quot;Newbie&quot; needs massive help"
date: 2008-04-09
forum: General Help
---

### Post by joecagle77 on 2008-04-09
OK, I put in my video card (geforce fx 5900) abd used the restricted driver. Then rebooted. it worked well for about 5 minutes then the screen went all billions of squares. 
 I had to do a hard restart. Sais the hell with the card took it out and when I tried to get back into ubuntu I get this

* Starting anac(h)ronistic cron anacron               [OK]
* Starting deffered execution scheduler atd       [OK]
* Starting periodic command sceduler crond        [OK]
* Checking battery state                                      [OK]
* Running local boot scripts (/etc/rc.local)            [OK]
       <-----with a curser here but nothing I type (like I know what to type anyway) nothing happens.


Please help

---

### Post by joecagle77 on 2008-04-09
No takers!??

---

### Post by hurtstotalktoyou on 2008-04-09
I would advise you put the card back in.  Ubuntu may be trying to talk to the card, and confused that it's not there.

Once you get back into a bootable situation, you can uninstall the restricted driver.

---

### Post by buried on 2008-04-09
**Put the card back in** then in the Grub Menu, Boot Ubuntu 7.10 Recovery Mode and type this in terminal
```
sudo apt-get remove nvidiadriver
```
or whatever the driver was or
```
nvidiacfg
```

---

