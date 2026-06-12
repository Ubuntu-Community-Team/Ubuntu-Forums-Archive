---
title: "login text is not last during boot sequence"
date: 2007-11-07
forum: General Help
---

### Post by jbulcher on 2007-11-07
We have an (almost) fresh install of Ubuntu Sever Gutsy Gibbon, which due to problems with the computer we had to install by installing and upgrading older versions of Ubuntu Server.

After everything was running, we installed MySQL and VMware Server, but now when the computer boots up it displays towards the end of the boot sequence:

```

<computername> login: * Starting MySQL database sever mysqld
* Checking for corrupt, not cleanly closed and upgraded needing tables.
                                                                               * Startin
g deferred execution scheduler atd
* Starting periodic command scheduler crond
* Running local boot scripts (/etc/rc.local)
```

my question is, how can we get "<computername> login:" to come last?

---

### Post by taurus on 2007-11-07
Looks like it is trying to execute /etc/rc.local.  Does it show you a login prompt if you wait long enough?  What do you have in /etc/rc.local anyway?

```
cat /etc/rc.local
```

---

### Post by jbulcher on 2007-11-07
The prompt was the first thing in the code snippet I showed - it's just not the last thing like it should be. If I hit <enter>, the login prompt comes back again.

rc.local does nothing.

It's not a big deal, I'm just wondering why it does this and if there is anything I can do to fix it.

---

### Post by taurus on 2007-11-07
Maybe switch to another console with <Alt>F2.

---

### Post by jbulcher on 2007-11-07
smartalek *grin*

---

