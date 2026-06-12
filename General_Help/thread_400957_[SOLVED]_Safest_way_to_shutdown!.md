---
title: "[SOLVED] Safest way to shutdown!"
date: 2007-04-04
forum: General Help
---

### Post by HighD on 2007-04-04
I'm running Ubuntu Server 6.10 on an old machine I got. I almost always use
```

sudo shutdown -h now
```

to shut down my pc...so I was wondering...is this the safest way to shutdown my pc from terminal? Is there a safer way? What command does Ubuntu execute when I click on the shutdown icon on gnome?

Well thanks in advance for any advice! :mrgreen:

---

### Post by coxy on 2007-04-04
Yes that is fine. The only other option would be a reboot.

Have a look at the help or man files for further information.

```

man shutdown
shutdown --help

```

---

### Post by cookfromfrozen on 2007-04-04
sudo halt is easier to type.

---

### Post by HighD on 2007-04-04
> **coxy said:**
> Yes that is fine. The only other option would be a reboot.

Have a look at the help or man files for further information.

```

man shutdown
shutdown --help

```

Awesome. That is what I wanted to hear! :D

Ok  and here's what it says in the manual about shutdown

> 
 shutdown arranges for the system to be brought down in a _***safe***_ way.  All
       logged-in users are notified that the system is going down  and  within
       the last five minutes of TIME, new logins are prevented.


Thanks coxy!

> **cookfromfrozen said:**
> sudo halt is easier to type.

Is that the same as

```
shutdown -h now
```

---

### Post by cookfromfrozen on 2007-04-06
> **HighD said:**
> Is that the same as

```
shutdown -h now
```

yes

---

### Post by HighD on 2007-04-06
> **cookfromfrozen said:**
> yes

Thanks. Problem solved :D

---

