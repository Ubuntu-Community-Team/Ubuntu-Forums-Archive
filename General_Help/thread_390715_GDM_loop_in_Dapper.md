---
title: "GDM loop in Dapper"
date: 2007-03-22
forum: General Help
---

### Post by total wormage on 2007-03-22
hi all,

a few hours ago i updated and upgraded an old dapper drake system. later i rebooted the machine, normally it logs itself in but this time the GDM login window popped up. i tried to login, but after a few seconds GDM looped and popped up the login window again.

not knowing what to do i just repeated my behavior a couple of times (:)} until an other screen came up asking if something was wrong with me trying to login 6 times in the past 90 seconds :D

i confessed (selected OK)

logically that brought me to the terminal, where i logged in and reinstalled GDM
didn't do anything.

i cant log in to safe mode, safe terminal or whatever

i'm going to delete GDM and try logging in without it, or with KDM or with the dm of xfce, just so you know.

does anyone else have GDM troubles after upgrading todays (or this weeks) update?

---

### Post by taurus on 2007-03-22
Boot into recovery mode from GRUB menu and post the output of this command here.

```
df -h
```

---

### Post by total wormage on 2007-03-22
lol
> mpb@Buffel:~$ df -h
Filesystem            Size Used Avail Use% Mounted on
/dev/hda1              28G   27G     0 100% /
varrun                126M  112K  126M   1% /var/run
varlock               126M  4.0K  126M   1% /var/lock
udev                  126M   88K  126M   1% /dev
devshm                126M     0  126M   0% /dev/shm
lrm                   126M   19M  107M  15% /lib/modules/2.6.15-28-386/volatile


*^_^*

i think my hdd is a bit full

ill try to remove some things and log back in :]]

---

### Post by taurus on 2007-03-22
Try

```
sudo aptitude clean
```

---

### Post by total wormage on 2007-03-22
clean and moving some files to my workstation did the trick :]]]

thank a lot! without "df -h" it would have taken me a long time to realise the problem was a full hdd :p

:KS :KS

---

