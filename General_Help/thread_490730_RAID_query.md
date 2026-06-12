---
title: "RAID query"
date: 2007-07-02
forum: General Help
---

### Post by Hazr0x on 2007-07-02
Hey,

I *attempted* to install linux on this computer a while ago, and failed miserably because I had no idea what to do with RAID.

After losing all my data, I'm looking for better ways to install Linux on this computer.

The question I'm asking is: would RAID present any difficulty to the Wubi installation?

Thank you,

Haz

---

### Post by gtmarks on 2010-06-28
Sorry to hear about your losing your data.  I've had this misfortune myself.  (It made me very meticulous about backups!)

There shouldn't be a problem installing RAID.  I have RAID 1 (at the software level) on my machine, now running Ubuntu 10.04.  I installed it essentially following the instructions here:

  [http://cr.yp.to/hardware/build-20060107.html](http://cr.yp.to/hardware/build-20060107.html)

under the subsection "Variant: RAID1 array," with a few small changes (e.g. scaled up the swap size proportionate to my drive size, used ext4 filesystem instead of ext3).  When I first set up the system, as Ubuntu 9.04, it was necessary to use the alternate install CD (with text-based installation) to correctly configure RAID.

Incidentally, I would not regard RAID 1 as a substitute for regular backups of data.

If you can provide the details of what went wrong during your prior installation, it will be easier to suggest remedies.

---

