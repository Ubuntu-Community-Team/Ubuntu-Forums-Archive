---
title: "How to determine what modules I need?"
date: 2014-04-24
forum: General Help
---

### Post by rcmosher on 2014-04-24
On a recent package update my wireless, touchpad, and audio stopped working. I discovered several modules weren't loaded, and have added them to /etc/modules to resolve the issue. 

Though I'm wondering, is there a way to automatically determine what modules I need? Presumably this is possible, as I've never had to specify what modules this system has needed before. I'm guessing /etc/modules is built at install. I think I might be missing more modules as `sudo lshw` shows a number of other things as "UNCLAIMED".

This is on 12.04 if it makes a difference.

---

### Post by plucky on 2014-04-25
> **rcmosher said:**
> On a recent package update my wireless, touchpad, and audio stopped working. I discovered several modules weren't loaded, and have added them to /etc/modules to resolve the issue. 

Though I'm wondering, is there a way to automatically determine what modules I need? Presumably this is possible, as I've never had to specify what modules this system has needed before. I'm guessing /etc/modules is built at install. I think I might be missing more modules as `sudo lshw` shows a number of other things as "UNCLAIMED".

This is on 12.04 if it makes a difference.

You could boot a Live CD or USB and use the terminal to list the kernel modules ```
lsmod
``` and use that to compare what kernel modules are loaded in your current setup. That assumes all the things in Live mode are working.

Good Luck

---

### Post by rcmosher on 2014-04-27
> **plucky said:**
> You could boot a Live CD or USB and use the terminal to list the kernel modules ```
lsmod
``` and use that to compare what kernel modules are loaded in your current setup. That assumes all the things in Live mode are working.

Good Luck

Thanks. I'll see about making one. Anyone know if there's a way to discover needed modules without a live CD?

---

