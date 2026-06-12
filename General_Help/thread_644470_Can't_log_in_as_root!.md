---
title: "Can't log in as root!"
date: 2007-12-18
forum: General Help
---

### Post by dresman on 2007-12-18
When using the console when I use the command ''su'' to gain root access and so I enter my root password and says acces denied.I know my admin password very well.

---

### Post by ~LoKe on 2007-12-18
sudo su

root on its own is disabled, afaik.

---

### Post by diatribe on 2007-12-18
this is indeed the case.  programs can be run as root with sudo or sudo su then passwd will let you set a root pass

---

### Post by ~LoKe on 2007-12-18
> **diatribe said:**
> this is indeed the case.  programs can be run as root with sudo or sudo su then passwd will let you set a root pass

Probably not a good idea to enable the root account.  It's not a worthwhile risk and is generally unnecessary.  But yes, that's correct. :)

---

### Post by diatribe on 2007-12-18
> **~LoKe said:**
> Probably not a good idea to enable the root account.  It's not a worthwhile risk and is generally unnecessary.  But yes, that's correct. :)

well technically he shouldnt NEED to use su either ;)

---

### Post by ~LoKe on 2007-12-18
> **diatribe said:**
> well technically he shouldnt NEED to use su either ;)

Surely you jest. ;)

sudo su would allow you to do things that require root permission, without you having to use sudo each time.  This could include executing a script that takes a fair amount of time (as sudo requires a password a second (and more) time after a certain amount of time has passed).

---

### Post by aysiu on 2007-12-18
```
sudo -i
``` works too.

---

