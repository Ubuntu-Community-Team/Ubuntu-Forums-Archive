---
title: "cpufreq error on startup HELP"
date: 2008-03-02
forum: General Help
---

### Post by The Pinny Parlour on 2008-03-02
PLEASE HELP

I can't start my system anymore.  It hangs at:

/etc/rc2. d/s20 powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling-governor: Directory nonexistent
CPU frequency scaling not supported

then it loads a couple of other things and hangs at:
Starting Bluetooth service


What the heck do I do to makes the stupid thing start?

---

### Post by dcstar on 2008-03-02
> **The Pinny Parlour said:**
> PLEASE HELP

I can't start my system anymore.  It hangs at:

/etc/rc2. d/s20 powernowd: 156: cannot create /sys/devices/system/cpu/cpu0//cpufreq/scaling-governor: Directory nonexistent
CPU frequency scaling not supported

then it loads a couple of other things and hangs at:
Starting Bluetooth service


What the heck do I do to makes the stupid thing start?

Firstly boot off the Live CD and do a fsck on your hard drive partition (do a search for detailed instructions, if necessary).

---

### Post by The Pinny Parlour on 2008-03-02
Hi and thanks David

it says this: fsck 1.40.2 (12-Jul-2007)

what do I do now?

I can't even copy my data from my hdd to a usb ext hdd.

I need to get this sorted out.

---

### Post by The Pinny Parlour on 2008-03-02
Bump

---

