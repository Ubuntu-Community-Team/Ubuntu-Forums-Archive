---
title: "udevd, ps, pidof 100% cpu after upgrade"
date: 2013-05-06
forum: General Help
---

### Post by saberworks on 2013-05-06
I just upgraded to 13.04 (xubuntu) and now my computer is really slow.  I opened up top and I see 4 processes going crazy.  udevd, ps, pidof, ps, all using ~100% cpu.  I tried killing them with kill -9, no luck.  I don't quite know what to do next.  Please see attached screenshot of the top command.

[ATTACH=CONFIG]242246[/ATTACH]

And now the number of "ps" commands is growing and growing, each one eating as much cpu as possible, my system is about unusable at this point.

Any ideas?

---

### Post by dino99 on 2013-05-06
you only can kill your own threads
dont you have some app(s) loaded ? or is it after the session is opened but without other app loaded ?

---

### Post by saberworks on 2013-05-06
I was trying to kill them as root, and I also tried as my own user, but no luck.  This is after a fresh boot, just sitting there idle (well, obviously not idle, but I didn't have any programs open).

---

### Post by junktext on 2013-05-21
saberworks, I actually had the same issue as you tonight.  Maybe this has absolutely nothing to do with it, but the high CPU usage from 'udevd' and 'pidof' occurred somewhat recently after I installed HAL (Hardware Abstraction Layer) and got it working by adding the missing directories for Ubuntu 13.04 (there's a separate thread on this at: [http://ubuntuforums.org/showthread.php?t=2140324](http://ubuntuforums.org/showthread.php?t=2140324)).  Anyways, I just rebooted and things appear to be acting normal, and I am running 'top' in Terminal right now and I don't see any odd CPU activity yet.  Hopefully, things stay normal from here on out.

I am using a Samsung Q430 laptop with a NVIDIA 310M card (with proprietary drivers) on Ubuntu 13.04 (64-bit).

---

