---
title: "(GRUB?) Error 18-- _after_ OS has been functional for some time"
date: 2007-12-17
forum: General Help
---

### Post by DWRZ on 2007-12-17
I'm a bit unfamiliar with the hardware since it's not my PC-- a Fiujitsu, 256MB RAM, P4 @ 2.0 Ghz (?), 40GB HD. Dual booting XP and Kubuntu Feisty for more than a month without problems. XP on the first partition, Kubuntu on the second (last time I arrange things this way).

Yesterday morning suddenly I got an error 18: bla, exceeds, bla, bla. It did not say it was GRUB (looked like it was coming straight from the BIOS to me, but I'm not sure) but I think it is the exact same error.

I managed to salvage what data I needed through the Kubuntu Live CD and mounting the partitions. Still, it would be awesome to revive the whole system. Any possible way to do this?

---

### Post by Herman on 2007-12-17
:) Hello DWRZ,
Here is what I think you should try to do (if you want to to revive your present system,  [How to make a separate /boot partition]("http://users.bigpond.net.au/hermanzone/p15.htm#How_to_make_a_separate_boot_partition").

The reason for that is explained in the following link, [     Grub error 18]("http://users.bigpond.net.au/hermanzone/p15.htm#18").

I am guessing maybe you have a BIOS with an 8.45 GB BIOS limit and so far you have been lucky enough not to have had GRUB Error 18 sooner because your kernel just happened to be located within the 8.45 GB limit. Maybe you received a new kernel in an update and this time it was placed in some part further out in your file system, where the BIOS can't 'see' it now.

Just for an experiment, you might try booting your old kernel by going down a few lines in your GRUB menu when you are booting up and see what happens. :)

I hope my guess about what your problem is will be correct, but it is just a guess, If you want, you can give me your BIOS version or motherboard manufacturer and model number and I can check to see if I can learn any more factual or certain information before you go to too much trouble.
I might not get time to research that right away though.
If you are used to partitioning and using Linux then making a separate /boot partition might not be any problem for you at all.

Regards, Herman :)

---

