---
title: "Can Ubuntu hard disk change from Athlon to Pentium?"
date: 2006-12-04
forum: General Help
---

### Post by larryalk on 2006-12-04
I have Kubuntu Dapper Drake 6.06 that was installed  on an AMD Athlon computer and would like to change to a much faster Intel Pentium 4.

The speed difference is 1.150 vs 2.4 ghz.
The video card is the same, I will move it to the other box.  Memory 1 gig in each case.

Is the _install_ different for different cpus or does Ubuntu make any necessary adjustments "on the fly" as it boots up?

Larryalk

---

### Post by steve.horsley on 2006-12-04
Dapper has a 386 kernel that will run on either CPU, a 686 kernel for intel and a K6 (or is it k7?) kernel for Athlons. I am guessing that if you make sure the system loads the 386 kernel, then it will probably transfer nicely. But it's only a guess - I've never tried it.

---

### Post by lamego on 2006-12-04
Yes the kernel should detect your new hardware and load the required modules.
Unless you are using the kernel optimized for AMD, in that case you should switch to the 686 kernel.

---

### Post by endersshadow on 2006-12-04
It's the same kernel image for either one, so you *theoretically* shouldn't have a problem.  I suggest making a backup of your data before undertaking the replacement, though.

---

