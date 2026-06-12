---
title: "removing 8.04 beta"
date: 2008-04-02
forum: General Help
---

### Post by wickedninjalo on 2008-04-02
Ok I had 7.10 Gutsy and Vista dual booting fine. I shrunk one of the partitions and installed 8.04 hardy beta on it. unfortunately i wasent paying attention and installed the boot loader on hardy. Now I would like to remove hardy while keeping 7.10  and vista. so how would I go back to using the boot menu on the 7.10 partition?

---

### Post by ramper4 on 2008-04-02
May be not exactly what you asked. But I have installed Vista Boot Pro and that controls the booting sequence / option. Perhaps that would allow you to first take control out of your Hardy partition? I am a relative newbie - so I hope I make sense here?

---

### Post by jpietari on 2008-04-02
Have you tried setting the boot flag on to your Ubuntu 7.10 or Vista partition?  This can be done by using GParted (Administration->Partition Editor)

---

### Post by wickedninjalo on 2008-04-02
Actually I thought it was gonna work, but it didnt. vistabootpro and gparted didnt do anything.

---

### Post by wickedninjalo on 2008-04-02
what would happen if i just deleted tha hardy partition? because im going to do that eventually.

---

### Post by wickedninjalo on 2008-04-04
any thoughts?

---

### Post by sekinto on 2008-04-04
You should be able to boot from a live CD and do this:
```

sudo grub
> root (hd0,0)
> setup (hd0)
> exit

```

Replace (hd0,0) with the partition that Gusty is on, and replace (hd0) with the drive your Gusty partition is on.

Example: (hd0,1) = first drive second partition, (hd0) = first drive.

---

### Post by wickedninjalo on 2008-04-05
> **sekinto said:**
> You should be able to boot from a live CD and do this:
```

sudo grub
> root (hd0,0)
> setup (hd0)
> exit

```

Replace (hd0,0) with the partition that Gusty is on, and replace (hd0) with the drive your Gusty partition is on.

Example: (hd0,1) = first drive second partition, (hd0) = first drive.

Thanks man that worked!

---

