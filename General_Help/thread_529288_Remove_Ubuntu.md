---
title: "Remove Ubuntu?"
date: 2007-08-19
forum: General Help
---

### Post by quordandis on 2007-08-19
Hi All,

While I love Ubuntu, there are still a number of things that I need that I either can't get to work or are not yet still fully supported on Ubuntu, I therefore need to go back from my dual-boot environment to single WinXP. 

Unfortunately, I made the grave error of loading GRUB into my MBR instead of on the linux partition - does anyone know how I can go about reversing the MBR to load up Windows's bootloader?

Thanks,
Q

---

### Post by kellemes on 2007-08-19
You need to get into the recovery-console of Windows and type **fixmbr** (or type **help** for all the info you need)

---

### Post by majorkonig1337 on 2007-08-19
**fixmbr** didn't work for me, it gave me an error saying that boot directory was corrupt. But **fixboot** did work for me. 

So try both, because I read somewhere that either one of them work for some people.

---

### Post by quordandis on 2007-08-25
I've read both options, just wanted to run it by someone just to make sure. 

Thanks!
Q

---

