---
title: "Will Windows still work after I install Ubuntu?"
date: 2007-08-03
forum: General Help
---

### Post by Squee3 on 2007-08-03
If I install Ubuntu on my computer, will I still be able to use Windows if I need to without having to reinstall windows and without having to repartition my hard drive?

---

### Post by merlinus on 2007-08-03
You can create a dual-boot system with windows and ubuntu.  It will give you a choice of os upon startup.

When you get to the partitioning menu, make sure NOT to select use entire disk, but to shrink the windows partition and use free space.

Beforehand, delete temp and other unneeded files, backup data, set virtual paging to zero (set it back to same size after ubuntu install), and defrag several times.

If using vista, use its disk manager to shrink its partition.

Good luck!

-merlin

---

### Post by cookies on 2007-08-03
> **Squee3 said:**
> If I install Ubuntu on my computer, will I still be able to use Windows if I need to without having to reinstall windows and without having to repartition my hard drive?


You will need to partition. Windows will still work, however.

---

### Post by tuxcantfly on 2007-08-03
A standard ubuntu install will shrink your windows drive and install ubuntu, so that you have a dual-boot installation. Your Windows install will still work and be bootable after installation. If you're concerned about the risks of repartitioning, you might also want to check out Wubi at [http://wubi-installer.org/](http://wubi-installer.org/) which installs Ubuntu without needing to repartition the hard drive.

---

### Post by Steve1961 on 2007-08-03
You will if you decide to shrink teh windows partition and dual boot.  Before your start though, it's always a good idea to defragment the windows partition before letting the installer shrink it.  Then use gparted from the live cd to create free space.

---

### Post by HeavyAl on 2007-08-03
You can install Ubuntu and have it repartition the hard drive for you. Depending on the version of windows you have and your hardware loadout this can be either a simple click and forget process or it could become problematic.

Personally, whenever I've set up a dual boot solution, I use something like partition magic to resize the windows partition first and then install Linux using the freed up space.

---

