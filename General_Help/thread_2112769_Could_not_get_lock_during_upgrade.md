---
title: "Could not get lock during upgrade"
date: 2013-02-05
forum: General Help
---

### Post by marchelloUA on 2013-02-05
Hi all, 

I tried to upgrade 

# sudo apt-get upgrade

Got error: 

E: Could not get lock /var/cache/apt/archives/lock - open (11: Resource temporarily unavailable)
E: Unable to lock directory /var/cache/apt/archives/

How do I deal with that?

---

### Post by omeomi on 2013-02-05
This command should kill any programs locking the cache and remove the lock
```
sudo fuser -cuk /var/cache/apt/archives/lock
sudo rm -f /var/cache/apt/archives/lock
```

However, you should be careful that you don't interupt any ongoing installations as this might create an unstable system.

---

### Post by travalon on 2013-02-07
If I have something upgrading in the cli and its waiting for conformation to proceed, and I try to use packagemgr I'll get the same" can not get lock" until I complete the cli command.

---

### Post by ibjsb4 on 2013-02-07
You cannot apt-get and use another package manager at the same time.

---

### Post by grahammechanical on 2013-02-07
We can not use more than one method of updating at the same time. If Update Manager then it will lock out any other attempts to update/upgrade. The same applies to any method that we use to update/upgrade. This includes the terminal, the software Centre, and other package managers such as Synaptic.

Remember, Update Manager checks for updates in the background according to a schedule that is fixed by its settings. If we are trying to update through the terminal when Update Manager is making its connections to the repositories, then we get that cannot lock on message.

Regards.

---

