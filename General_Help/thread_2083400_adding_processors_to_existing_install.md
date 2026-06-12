---
title: "adding processors to existing install"
date: 2012-11-12
forum: General Help
---

### Post by CyberCowboy on 2012-11-12
I'm not sure the best place to post this so I'm going general, feel free to move it if needed.

I've got an existing install of Ubuntu Server x64 12.04 running on a Dell Precision T7500 presently using 1 CPU (with 4 cores) and since I'm maxing out the CPU I am going to pick up the riser and add a second processor.  Is there anything special I need to do with my install either prior to, or after the install to make sure it will see and utilize the additional processor?

---

### Post by Cheesemill on 2012-11-12
Nope.

Linux probes for available hardware and loads the correct drivers every time you boot, just add your new CPU and power up.

---

### Post by |{urse on 2012-11-12
Yep, as Cheesemill said. you can verify this with the output of:

> cat /proc/cpuinfo

---

### Post by CyberCowboy on 2012-11-12
awesome thank you both.

---

### Post by dcstar on 2012-11-14
> **CyberCowboy said:**
> awesome thank you both.

Then MARK the thread!

---

### Post by CyberCowboy on 2012-11-14
oops, sorry mate

---

