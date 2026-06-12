---
title: "NVIDIA drivers"
date: 2016-12-27
forum: General Help
---

### Post by hyburn on 2016-12-27
I just reinstalled ubuntu and want to know which driver is more stable.

in the additional driver section I have the listings of:
370
367
375

I would assume the 375 is the latest, but would it still be in the testing phase?

---

### Post by harry947 on 2016-12-27
This choice messed by computer. I selected 340 at first, but a game I played(the forest) didn't work(bad graphics), I tried to change the driver but then it all came down. Read my post about what happened.

---

### Post by SeijiSensei on 2016-12-27
Usually running
```
sudo apt-get install nvidia-current
```
will pick the best driver for your adapter.  Then run the command
```
sudo nvidia-xconfig
```
Log out and log back in to relaunch X with the new configuration.

---

