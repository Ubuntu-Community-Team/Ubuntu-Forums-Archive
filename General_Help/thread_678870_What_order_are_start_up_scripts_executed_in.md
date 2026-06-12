---
title: "What order are start up scripts executed in?"
date: 2008-01-26
forum: General Help
---

### Post by DrQuincy on 2008-01-26
I want a script to start a synergy client to run when the login screen shows. I added a script to /etc/init.d and rebooted. It executes but it does it too early and prevents the GUI login screen ever showing. How to I change the order the script is executed? I want it after gdm has stared.

Thanks.

I followed the steps here: [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

---

### Post by sisco311 on 2008-01-26
> **DrQuincy said:**
> I want a script to start a synergy client to run when the login screen shows. I added a script to /etc/init.d and rebooted. It executes but it does it too early and prevents the GUI login screen ever showing. How to I change the order the script is executed? I want it after gdm has stared.

Thanks.

I followed the steps here: [http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/](http://ubuntu.wordpress.com/2005/09/07/adding-a-startup-script-to-be-run-at-bootup/)

try this:
```
sudo update-rc.d -f *your-script* remove
sudo update-rc.d *your-script* start 99 2 3 4 5 . stop 99 0 1 6 .
```> DESCRIPTION
       update-rc.d updates the System V style init  script  links  /etc/rcrun&#8208;
       level.d/NNname  whose  target  is  the  script /etc/init.d/name.  These
       links are run by init when it changes  runlevels;  they  are  generally
       used  to  start  and stop system services such as daemons.  runlevel is
       one of the runlevels supported by init, namely, 0123456789S, and NN  is
       the  two-digit  sequence  number  that determines where in the sequence
       init will run the scripts.

---

