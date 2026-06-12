---
title: "everytime i run Parallels, it says i need to run parallels-config first!"
date: 2007-02-01
forum: General Help
---

### Post by syxbit on 2007-02-01
It works fine, but after a reboot, i need to recompile it before I run.
this gets a little annoying, as i have to do it every time i want to run it
any ideas?

---

### Post by glabouni on 2007-02-01
> **syxbit said:**
> everytime i run Parallels, it says i need to run parallels-config first!

then run parallels-config first !! :D :D :D 

sorry couldn't resist it.


I'm not a parallels user, but it seems the configuration isn't saved to file.
have you read this faq entry ?
[http://www.parallels.com/products/workstation/faq/2/#2-7](http://www.parallels.com/products/workstation/faq/2/#2-7)

---

### Post by Gabriel Camiro on 2007-02-01
For sure you had to change /bin/sh to /bin/bash in order to make it work.
Now go a check all other scripts and do the same, then run parallels-config once more and it will work for good.

---

### Post by syxbit on 2007-02-03
this fixed it (read it on parallels official forums) so it helps others

There's another bug with Edgy concerning auto loading the drivers at startup. Add /usr/lib/parallels/autostart/drivers_start to the file /etc/rc.local in order to get the drivers automatically loaded at startup.

---

