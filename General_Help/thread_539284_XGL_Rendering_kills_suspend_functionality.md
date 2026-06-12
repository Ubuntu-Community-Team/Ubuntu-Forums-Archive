---
title: "XGL Rendering kills suspend functionality"
date: 2007-08-31
forum: General Help
---

### Post by Venerence on 2007-08-31
**Double Edit** - After a bit of browsing, I've narrowed the problem (well specifically, the solution) down to one thing. Currently I need to do the following command: ```
sudo modprobe -r ipw3945
``` before suspension and ```
sudo modprobe -r ipw3945
```. Furthermore, I have to do this while using USWSUSP, having used the [HOWTO here](http://ubuntuforums.org/showthread.php?t=471855). Currently I don't know how to activate these terminal commands upon USWSUSP suspending and starting up, as it can't do it through the traditional methods.

---

