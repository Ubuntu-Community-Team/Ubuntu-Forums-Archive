---
title: "Swap space and boot partition query"
date: 2007-01-20
forum: General Help
---

### Post by xerxesv5 on 2007-01-20
Hi All,

2 quick questions about my fresh Edgy install...

- I have a 32MB ext2 boot partition. Is it okay to mount this read-only at boot, so that I don't have to care about power failures killing it mid-write? Nothing should be writing to this regularly anyway, correct?

- Should 2GB of system RAM (on a desktop install) be enough to remove the need for swap? Any advice, or should I create a swapfile anyway?

Thanks in advance
xerxesv5

---

### Post by Kateikyoushi on 2007-01-20
2GB should be enough but there is stuff what is used only at boot and shutdown so swapping those might free up some memory. 
Whether you actually need it or not depends on how you use your rig, I had not problem running gento without swap on 512MB ram but that's my notebook and I turn of the drive often that's why.
I would recommend to make a small swap partition. 256-512MB

---

### Post by Sef on 2007-01-20
Unless you do heavy movie editing or heavy gaming, you should do fine without a swap.

---

### Post by DerHesse on 2007-01-20
I have 2GB RAM and use 1GB swap. That`s just fine.

...and: don`t put swap at the end of the disk but in the middle, for speed.

---

