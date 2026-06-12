---
title: "Update Manager Frozen"
date: 2008-04-25
forum: General Help
---

### Post by freebullets on 2008-04-25
Whenever I try installing updates, the update manager freezes.  I click "Install Updates", then a progress bar window pops up, it disappears and my update manager is grayed out like it's frozen.  Never asked me for a password.

---

### Post by chameleonkid on 2008-04-25
You may have more than one open and working at a time or some sort of memory problem or other bug. I know I had some problems connecting to the server but I don't think I greyed out. On your next restart try the update manager again. Until then you can use the terminal to update. Input:
```
sudo apt-get update
```
then
```
sudo apt-get upgrade
```

---

### Post by natrixgli on 2008-04-25
Additionally, many people have commented that the updates have been slow today. (I tried an upgrade on a PC at the office and gave up after staring at the greyed out upgrade progress box for about 15 minutes...)

Clearly the internet tubes are clogged because of so many Microsoft developers downloading Hardy to get ideas as to how to bail themselves out of the Vista mess. (a.k.a. Windows Me MkII)

Things should chill out in a day or so.

Cheers,

-n8

---

