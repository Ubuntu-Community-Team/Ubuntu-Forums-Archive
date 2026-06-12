---
title: "unable to find swap-space"
date: 2007-02-03
forum: General Help
---

### Post by cyber_bushi on 2007-02-03
Hi folks,

during booting i get the message "unable to find swap-space signature" and my /var/log/messages says:

```
Jan 30 20:09:22 x20 kernel: [17179592.000000]  sda:<3>Unable to find swap-space signature
Jan 30 20:26:40 x20 kernel: [17180632.200000] Free swap  = 0kB
Jan 30 20:26:40 x20 kernel: [17180632.200000] Total swap = 0kB
Jan 30 20:26:40 x20 kernel: [17180632.200000] Free swap:            0kB
Jan 30 20:26:40 x20 kernel: [17180632.204000] 0 pages swap cached

```

can anybody give me a hint what i can do?

regards,

cb

---

### Post by meng on 2007-02-03
Had you set up a swap partition? Had you made any changes to your partition table (e.g. deleted or changed an existing swap partition)?

---

### Post by cyber_bushi on 2007-02-03
thanx! with the help of this thread
[http://www.ubuntuforums.org/showthread.php?t=343570](http://www.ubuntuforums.org/showthread.php?t=343570)
i found out that my ubuntu set up an extenden partition as swap space and that somehow doesn't seem to work out...
i set the correct partition - not the extended one, but the one "inside" the extended one to swap, restarted and voilá  - it worked... thanks a lot though meng for your fast help!!!

regards,

cb

---

### Post by meng on 2007-02-03
Kudos to you for sorting out the problem on your own!

---

