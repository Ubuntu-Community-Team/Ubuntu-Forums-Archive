---
title: "it87 modules not load"
date: 2015-02-23
forum: General Help
---

### Post by xxvirusxx on 2015-02-23
Hello guys

After I installed lm-sensors, i just try to configure fan speed control.

In Terminal if use :```
modprobe it87 force_id=0x8728
``` show fan speed sensor, so far so good.

To load modules on startup i make this:
```
sudo mousepad /etc/modprobe.d/it87.conf
```
add this
```
options it87 force_id=0x8728
```

But after restart this module isn`t load so no fan speed sensors.

How solve this, because on Arch Linux from triple boot work.



I have Xubuntu 14.04 x64

Tks

---

### Post by tgalati4 on 2015-02-23
Perhaps there is a blacklist:

> tgalati4@Mint17 /etc/modprobe.d $ grep it87 *.conf
blacklist-watchdog.conf:blacklist it8712f_wdt
blacklist-watchdog.conf:blacklist it87_wdt


tgalati4@Mint17 /etc/modprobe.d $ cat blacklist-watchdog.conf 
# Watchdog drivers should not be loaded automatically, but only if a
# watchdog daemon is installed.


Perhaps you need to install the watchdog daemon?

If you don't need the watchdog daemon, then comment out those two lines in blacklist-watchdog.conf and add your modprobe to /etc/modules with the parameters.  Your /etc/modules should look like:

> 
# /etc/modules: kernel modules to load at boot time.
#
# This file contains the names of kernel modules that should be loaded
# at boot time, one per line. Lines beginning with "#" are ignored.
# Parameters can be specified after the module name.

lp
rtc
it87 force_id=0x8728

If *it87* didn't load automatically, then perhaps the kernel didn't see it or your hardware is hiding it somehow.

---

### Post by xxvirusxx on 2015-02-24
Before was in **/etc/modules** only **it87**. Now with **it87 force_id=0x8728** work fine, without comment it87 from blacklist-watchdog.conf/
Also I remove it87.conf from modprobe.d.

Tks

---

### Post by tgalati4 on 2015-02-24
Everything is fixable.  It just takes a little patience.

---

