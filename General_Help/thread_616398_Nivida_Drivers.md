---
title: "Nivida Drivers"
date: 2007-11-18
forum: General Help
---

### Post by onlyproductions on 2007-11-18
ok this has happened to me twice now for no reason. I reinstall fiesty then i upgrade to gutsy, then it promts me to enable my nivida driver, i do that, then it tells me to restart. I restart i see the ubuntu loading thing and then a bunch or oddly assorted pixels appear and start flashing...what do  i do.

---

### Post by PmDematagoda on 2007-11-18
In Recovery Mode, do this:-
```

dpkg-reconfigure xserver-xorg
```

select the driver as Nvidia and any other options you may want. After reconfiguration, do:-

```
startx
```

to see if your problem is solved.

---

### Post by astoltz on 2007-11-18
What graphics card do you have?  If it's older, could be it's not supported by the latest nvidia driver.

Upgrades are sometimes a little problematic.  Why not install Gutsy striaght off?

---

