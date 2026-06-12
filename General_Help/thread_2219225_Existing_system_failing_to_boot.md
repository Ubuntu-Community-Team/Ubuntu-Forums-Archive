---
title: "Existing system failing to boot"
date: 2014-04-23
forum: General Help
---

### Post by faroutliving on 2014-04-23
I have Ubuntu 12.04 (server) installed on a dual proc EVGA SR2 based system, and all has been fine for years until Monday when the cooling system failed. One of the cpus bit the dust, and it is now disabled and the system is (almost) booting back up. The initial bios boot text flies by, and the ubuntu boot menu comes up. Choosing the default option, and the boot log details fly by and stops abruptly with:

BIOS EDD facility v0.16 2004-Jun-25, 0 devices found
EDD information not available

I'm a bit confused about what EDD is. I thought it allowed the BIOS to pass on the boot drive, but that is clearly defined in the BIOS.

Any ideas on what I should look at? Thanks!

Deron

---

### Post by jamesisin on 2014-04-23
You might begin by testing with a live CD.  Are you able to boot into the system using a live CD?

---

### Post by faroutliving on 2014-04-23
Not possible right now. Will have to get a drive first :-) The boot drive however _does_ boot up a similar system. So now I'm thinking either some strange BIOS setting(?) or more likely some other heat related damage occurred. Just seems strange that it would get that far and fail. An SSD boot drive also fails to boot in this dead system.

---

### Post by jamesisin on 2014-04-23
So you installed a known-good bootable SSD and it also would not boot?  Then, yes, it has to be some hardware issue.  Could be a challenge to diagnose.

---

