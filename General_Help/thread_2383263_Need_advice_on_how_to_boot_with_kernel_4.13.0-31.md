---
title: "Need advice on how to boot with kernel 4.13.0-31"
date: 2018-01-22
forum: General Help
---

### Post by Hewjr100 on 2018-01-22
I am running Ubuntu 16.04, currently I am booting with kernel 4.10.0-28  I cannot boot the defualt kernel because of the Nvidia situation (Nvidia gtx 1050).  Is there a workaround for this or not.

Henry

---

### Post by mzl2 on 2018-01-23
Try to boot with another kernel (4.4.0-109 and up is fine), you should consider that the kernel 4.10 isn't patched against meltdown vulnerability only the 4.13.x and 4.4.x series are being patched. In a month or so your kernel 4.10.x will be updated to 4.13.

I've seen many workarounds but are pretty dependent from every system configuration, the only thing that worked for me has been using the kernel 4.4.x.

---

### Post by Hewjr100 on 2018-01-23
I have had problems since kernel 4.12.x. but I am told it's not the kernel but Nvidia.  I have the Gtx 1050. I have the most recent kernel, but it does not boot, also lightdm for whatever reason also freezes upt too.

Henry

---

