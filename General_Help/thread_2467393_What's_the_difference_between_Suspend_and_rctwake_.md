---
title: "What's the difference between Suspend and rctwake --mem?"
date: 2021-09-25
forum: General Help
---

### Post by Paddy Landau on 2021-09-25
In Ubuntu 20.04, Suspend is broken (apparently a [bug in Linux]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1925843")), at least on certain machines.

I discovered today that I can use rtcwake instead:
```
sudo rtcwake --mode=mem --date=+15days
```
(rtcwake requires a wake time, which is why I put a date far out into the future.)

rtcwake works, while Suspend doesn't.

But, reading the rtcwake manual, it looks (to my uneducated eyes) to be the same as Suspend.

Can you tell me what the difference is? (I'm just curious.)

---

