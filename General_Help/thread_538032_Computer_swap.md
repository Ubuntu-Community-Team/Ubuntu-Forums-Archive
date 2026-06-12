---
title: "Computer swap?"
date: 2007-08-29
forum: General Help
---

### Post by dc12volthippy on 2007-08-29
I'm getting a new motherboard(complete with AMD processor and 2GB DDR2 RAM) and graphics card from my brother. My current system is an IBM NetVista 6059 with a Pentium III Coppermine 800MHz processor and 256 MB of 100 and 133MHz SDRAM. I was planning on finding a new case, putting the "new" motherboard in it (with TONS of cooling) with my current hard drive, CD-RW/DVD-RW drive, and peripherals. I'm not sure if it's a 64-bit processor, in which case I'll definitely have to install a different version of Ubuntu. My question is: Can I swap my hard drive to a new computer and have the system able to reconfigure to the new hardware without a hassle?

---

### Post by spd106 on 2007-08-30
In general the answer is no. Though you might be able to boot into recovery mode as it uses default settings for the lowest common denominator compatibility and therefore is most likely to work when you have hardware troubles.

If I were you I would backup the home directory and repo package cache (under /var/cache/apt/archives) to save time running updates, then reinstall. If you import your home directory from the backup then you should then keep all of your original settings and it's just a matter of adding the extra software packages back.

---

