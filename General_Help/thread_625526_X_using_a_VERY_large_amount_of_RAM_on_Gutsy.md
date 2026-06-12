---
title: "X using a VERY large amount of RAM on Gutsy"
date: 2007-11-28
forum: General Help
---

### Post by jdhore on 2007-11-28
I'm using Ubuntu Gutsy x32 fully up-to-date, recently rebooted (about 23h13m ago) and on a system with decent specs with the binary/blob nvidia driver from the restricted driver manager (9639 i believe). Recently, I noticed a VERY large amount of my RAM was in use so i installed htop and it told me that X was using 34% of my RAM. This made me VERY suspicious because X ALONE was using well over 2GB of RAM. I don't know what the problem is, all i can say is that i never had this problem on Feisty and i've never had it on Debian Unstable with either Xorg 7.2 or Xorg 7.3 and excluding the past 2 hours or so, i haven't had this problem on Gutsy. I'm wondering if this is a known problem or if there's a fix for it or if anyone knows what's going on.

Specs:
2- Intel Xeon 5160 CPU's
8GB ECC DDR2 (all known to be working)
nVidia 7800GTX
resolution: 2560x1600,1920x1200
No compositing manager running

What htop said was the offending process name:
```
/usr/bin/X :0 -br -audit 0 -auth /var/lib/gdm/:0.Xauth -nolisten tcp vt7
```

Also, according to ```
ps aux
``` there are no other X sessions running.

---

