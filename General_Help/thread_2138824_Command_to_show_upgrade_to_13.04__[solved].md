---
title: "Command to show upgrade to 13.04  [solved]"
date: 2013-04-25
forum: General Help
---

### Post by geovino on 2013-04-25
I've been running a daily build of 13.04 for the past two months. I have been running apt-get update and upgrade every couple days. Now that the final is released, what command do I run to show that I have upgraded to Ubuntu 13.04 final?

---

### Post by Vaphell on 2013-04-25
you don't have to do anything special, simple upgrade of packages will make your version final, though i don't know how to obtain info that you are indeed running the real thing.

---

### Post by grahammechanical on 2013-04-25
You already have it if you have been updating every day. Did you notice that there were no updates today - the 13.04 release day?

```
lsb_release -a
```

All the 13.04 labels have been in place for some weeks and the 13.04 wallpapers came down a few weeks ago. We have 13.04. Go to System Settings>Software & Updates>Updates tab. Are to set to be notified for any new version? If yes, run Software Updater. Do you get an invitation to upgrade to 13.04? No? Neither did I. That is because we are running the new version.

Regards.

---

### Post by geovino on 2013-04-25
> **grahammechanical said:**
> You already have it if you have been updating every day. Did you notice that there were no updates today - the 13.04 release day?

```
lsb_release -a
```

All the 13.04 labels have been in place for some weeks and the 13.04 wallpapers came down a few weeks ago. We have 13.04. Go to System Settings>Software & Updates>Updates tab. Are to set to be notified for any new version? If yes, run Software Updater. Do you get an invitation to upgrade to 13.04? No? Neither did I. That is because we are running the new version.

Regards.

Thanks,, I'm there...

davek@dave-raring:~$ lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 13.04
Release:	13.04
Codename:	raring
davek@dave-raring:~$

---

