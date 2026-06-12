---
title: "tune2fs -c 300 /dev/sdaX"
date: 2013-02-26
forum: General Help
---

### Post by Macamba on 2013-02-26
Hi,

I'm running 3.2.0-38-generic. I noticed my root partition was checked very regularly. Not something I want to stare at when I want to do something with Ubuntu. I learned to use tune2fs to set a longer check interval. However, it seems to me it is not working. Is this something that does not work in the latest Ubuntu version?

TIA,
Macamba

---

### Post by sudodus on 2013-02-26
It works for me, and I recommend that you use disk checking either with -c or with -i according to ```
man tune2fs
```. I use -c 30, and you might combine it with -i 30 to get a check at least once a month if you mount (or boot) less than once a day. I think -c 300 is too seldom unless you mount the drive very often.

It does work for me, but I need root privileges, so this line might be OK
```
sudo  tune2fs -c 300 -i 30 /dev/sdaX
```

By the way, you have 71 beans. Have a cup of coffee while the partition is checked ;-)

---

### Post by dcstar on 2013-02-26
> **Macamba said:**
> Hi,

I'm running 3.2.0-38-generic. I noticed my root partition was checked very regularly.
......

Define "very regularly".

If you partitions are checked more than the default 30 mount interval then you are not unmounting cleanly.

---

