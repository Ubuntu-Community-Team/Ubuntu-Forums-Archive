---
title: "memory usage... kernel to blame?"
date: 2005-06-25
forum: General Help
---

### Post by sreid on 2005-06-25
I've been happily using Hoary since its release, after using Debian for many years. One problem has been bothering me though...

Memory usage grows over time, and I can't account for it. The Gnome system monitor shows "user" memory usage at around 25% (of 512MB) right after a reboot, but after about 3 weeks it's over 90% and things are really slow until I reboot.

What I find odd is that I can't see any memory hogs in ps or top. Shutting down my apps (firefox, thunderbird) has very little effect. I can only account for a fraction of the used memory.

Is it possible the kernel is using up memory? How can I find that out? I tried lsmod before and after reboot, but don't see any significant change there.

Suggestions?

---

### Post by zAo on 2005-06-25
Please post 
```
free -m
```

---

### Post by sreid on 2005-06-25
```

             total       used       free     shared    buffers     cached
Mem:           504        483         21          0         44        237
-/+ buffers/cache:        201        303
Swap:         1023          0       1023

```

This is with an uptime of a few hours. Only apps running are Firefox, Thunderbird, and some terminal windows. I can post again in a couple of weeks with the difference. From past experience I expect the first line will show "used" slightly higher, "buffers" about the same, "cached" down to double-digits, and swap usage will be at 100-200 MB (even after closing Firefox and Tbird).

Any other info I should grab now for comparison later on?

---

### Post by flamarro on 2005-06-27
and how about me?

```

             total       used       free     shared    buffers     cached
Mem:           758        718         39          0         50        386
-/+ buffers/cache:        282        475
Swap:         2219          0       2219
```

and i only have 3 hours of ubuntu ON....

i'm a newbie, have gaim, firestarter and amule and one or two pages in firefox working...
is this enough to have so much memory in use.
another thing is that if i use system monitor it says that i have 287.6 of 758.2 in use (37,9%).
Isn't that swap memory to be much more in use too????

---

### Post by sreid on 2005-08-14
I'm back! Here is free -m after 32 days uptime:

```

             total       used       free     shared    buffers     cached
Mem:           504        490         14          0         36        121
-/+ buffers/cache:        332        171
Swap:         1023         42        981

```

There is over 100MB more memory "used" as compared to when I first booted.

Again, only apps running are Firefox, Thunderbird, and some terminal windows. I logged out of Gnome and back in to rule out app leakage.

What info should I gather before next reboot?

---

