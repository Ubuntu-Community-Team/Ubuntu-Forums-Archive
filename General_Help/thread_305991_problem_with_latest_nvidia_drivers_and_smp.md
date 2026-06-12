---
title: "problem with latest nvidia drivers and smp"
date: 2006-11-24
forum: General Help
---

### Post by bettola on 2006-11-24
Hi, this is the problem, i have two kernel in grub on my edgy:

2.6.17-386
2.6.17-generic

with the first nvidia works with aiglx (great!). But SMP doesn't work because kernel is not generic

with the second SMP works (i see it with uname -a) but xorg doesn't start (module nvidia.ko does not exist on /lib/modules/linux-2.6.17-generic/volatile is the message) If i copy nvidia from /lib/modules/linux-2.6.17-386/kernel/driver/video a message says that is not usable at the start of xorg) I can't put not even vesa!!

So now I use the 383 kernel but i prefer to use the generic type beacause SMP is important for the speed of my laptop!!

---

### Post by bettola on 2006-11-24
ah...the nvidia driver is the latest: Version: 1.0-9629

---

