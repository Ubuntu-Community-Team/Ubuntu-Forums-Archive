---
title: "Ubuntu Trusty Tahr 14.04 LTS freezes, and freezes my network"
date: 2014-05-24
forum: General Help
---

### Post by Calle_Kabo on 2014-05-24
I have a problem I'm having difficulties to grasp.

Every now and then my server and my router freezes. I don't know if the network goes down which in turn causes the server to freeze or if it's the other way around. When it happens my router disconnects from the internet (fiber, gets IP via DHCP) and the monitor connected to the server gets weird (see photos). As soon as I shut down my server by long pressing the power button the router connects to the internet again. I can see on the router before I shut down the server the activity LED for the port connected to the server blinks furiously before I shut down the server and stops blinking when the server stops.

I'm using Ubuntu Trusty Tahr 14.04 LTS Server edition. I've installed LXC and I'm running a bunch of different containers having TOR, Freenet, I2P, MariaDB, Munin, Icinga, etc.

I can't find anything in the logs (syslog, kern.log). Load is generally around 0.4 and there's lots of free memory and hard drive space. Temperature is normally around 50 degrees celsius. I did a hardware test by selecting that option in the BIOS. The test found no errors.

Dell Optiplex 790
Intel i7-2600
8GB Ram
128GB SSD

Any clues on how I can figure out what's wrong?

[ATTACH=CONFIG]253411[/ATTACH][ATTACH=CONFIG]253412[/ATTACH]

---

### Post by Calle_Kabo on 2014-06-09
Today I got to see the kernel panic message. Please see attached photo. Does anybody have a clue what's going on?

EDIT: for google, the interesting messages are
Code: Bad RIP value.
Kernel panic - not syncing: Fatal exception in interrupt
Oops: 0010 [#4] SMP
Shutting down cpus with NMI
drm_kms_helper: panic occurred, switching back to text console

[ATTACH=CONFIG]253847[/ATTACH]

---

### Post by Calle_Kabo on 2014-06-10
And this morning I got a General Protection Fault: 0000 [#1] SMP
Kernel panic - not syncing: Attempted to kill the idle task!
[ATTACH=CONFIG]253865[/ATTACH]

---

