---
title: "Cannot install ...."
date: 2013-04-09
forum: General Help
---

### Post by Otto-C on 2013-04-09
New install of 12.04.
Tried install Picasa using xx it went thru its install process and
stopped at the EUOL and froze. I waited about 10 minutes or so and
closed the terminal. It warned all would be lost.  I powered down
the system and rebooted. I then tried to install the screensaver
using: desktop:~$ sudo apt-get purge gnome-screensaver
[sudo] password for:
it went thru its install process and stopped at the EUOL and froze.
I powered down the system and rebooted.
I retried:
desktop:~$ sudo apt-get purge gnome-screensaver
[sudo] password for:
E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
desktop:~$ 
On shut down all process supposed to be closed. How to solve?
tia
otto-c

---

### Post by ibjsb4 on 2013-04-09
Make sure you only have one package manager open at a time.  If this is not the case try removing the lock.

```
sudo rm /var/lib/dpkg/lock
```

---

### Post by Otto-C on 2013-05-07
This solved my problem.
Sorry for the delay.
Thanks

---

