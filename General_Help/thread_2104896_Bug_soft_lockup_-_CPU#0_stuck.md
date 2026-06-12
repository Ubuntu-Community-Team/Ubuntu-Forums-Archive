---
title: "Bug: soft lockup - CPU#0 stuck"
date: 2013-01-14
forum: General Help
---

### Post by james3mc on 2013-01-14
I'm getting the following when trying to boot Ubuntu 12.10 64-bit:

```
Bug: soft lockup - CPU#0 stuck for 23s! [migration/0:6]
```

Does anyone have a "reasonably easy to understand" solution?

---

### Post by tgalati4 on 2013-01-14
After a fresh boot, open a terminal:

```
dmesg | more
```

Spacebar to page forward, "q" to quit.  Cut and paste the early boot up messages, up until the CPU's show their BogoMIPs.  What model machine is this?

---

### Post by james3mc on 2013-01-14
I can't get as far as a terminal, it won't boot.

---

### Post by tgalati4 on 2013-01-14
Can you boot with a Live DVD/CD using the rescue terminal (root command line)?

---

