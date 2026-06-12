---
title: "Xgl using &gt;300mb of memory..."
date: 2006-09-13
forum: General Help
---

### Post by viciouslime on 2006-09-13
Is this supposed to be the case? At the moment it is using 335mb of memory and 2-5% of my cpu constantly. Specs are:

AMD64 3000
1GB DDR400 Dual Channel
Nvidia 7800GT

Is this normal or is something wrong?

---

### Post by ayoli on 2006-09-13
woow, this quite a lot, my xorg-air (aiglx) eat 128MB of memory and 0.7% to 7% of cpu. this on a toshiba celeron 1,5GHz, chipset Intel i855GM for graphics and 512MB of ram

---

### Post by mobilehavoc on 2006-09-13
Are you running compiz with cgwd...I believe there is a memory leak in cgwd. A few days ago my XGL was up to 1GIG!! of RAM usage..ridiculous.

Check out compiz.net, there are active discussions about the XGL memory leak. Long story short if you disable cgwd and use the regular gnome-window-decorator, it won't use too much memory.

---

### Post by turbojugend_gr on 2006-09-13
Well in my case it may climb up to 600 mb sometimes! I believe it somehow related to the ammount of memeory you have, the cpu usage usually is about 6-7 %. Specs: Athlon Dual core 4400, 2gb DDR2 ram, 7800gtx (512)

---

### Post by viciouslime on 2006-09-13
Thanks for all your replies. At least I now know it is normal and yes I am using cgwd.

---

