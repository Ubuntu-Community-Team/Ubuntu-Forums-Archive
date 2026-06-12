---
title: "gksu nautilus does not open nautilus"
date: 2013-02-11
forum: General Help
---

### Post by EpicMinerBackup on 2013-02-11
Ok i just reinstalled xubuntu and everything works fine till... 
 nautilus yes beloved nautilus i tried gksu nautilus and it asks for my password i type it in
and press enter and nothing happens i have tried it like 24 times (yes i counted and theres no error )

---

### Post by dcstar on 2013-02-11
> **EpicMinerBackup said:**
> Ok i just reinstalled xubuntu and everything works fine till... 
 nautilus yes beloved nautilus i tried gksu nautilus and it asks for my password i type it in
and press enter and nothing happens i have tried it like 24 times (yes i counted and theres no error )

Make a Launcher with the following:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

---

### Post by EpicMinerBackup on 2013-02-11
> **dcstar said:**
> Make a Launcher with the following:

```
gksudo "dbus-launch nautilus --no-desktop --browser"
```

ok that didnt work and my linux is running really slow nowwhats wrong O.o

---

### Post by arpanaut on 2013-02-11
Is not thunar the default file manager in Xubuntu?
Did you install nautilus on your install?

---

### Post by deadflowr on 2013-02-11
> **arpanaut said:**
> Is not thunar the default file manager in Xubuntu?
Did you install nautilus on your install?

+1

I thought the same thing.
Is nautilus even included in xubuntu?

I'd advise switching out nautilus with thunar and see if that works.

---

### Post by EpicMinerBackup on 2013-02-11
> **deadflowr said:**
> +1

I thought the same thing.
Is nautilus even included in xubuntu?

I'd advise switching out nautilus with thunar and see if that works.
it said they both where installed so i remove nautilus and keep thunar it opens with gksu and it works great and the system isn't running slowly anymore also :)

---

