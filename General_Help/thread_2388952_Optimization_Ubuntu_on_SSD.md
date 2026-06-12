---
title: "Optimization Ubuntu on SSD"
date: 2018-04-09
forum: General Help
---

### Post by al14 on 2018-04-09
I installed Ubuntu 16.04.4 LTS (Unity) on a new SSD...

Not really paying attention, I optimized the Ubuntu 16.04.4 install with the directions for a mint optimization from an old bookmark... --> [https://sites.google.com/site/easylinuxtipsproject/ssd](https://sites.google.com/site/easylinuxtipsproject/ssd)

Any harm done?

Should I re-install Ubuntu 16.04.4 LTS?

Thanks!!

---

### Post by oldfred on 2018-04-09
I do not see much, if anything that is different.

Default with Ubuntu is deadline.

fred@Z170N:~$ cat /sys/block/sda/queue/scheduler
noop [deadline] cfq

I do my own daily trim script.
I do add noatime for mounting any partitions on SSD. And relatime for HDD partitions.

---

### Post by al14 on 2018-04-09
I configured it for daily-->```
  sudo mv -v /etc/cron.weekly/fstrim /etc/cron.daily
```

I suppose it 'Trims' *every* time I boot into Ubuntu-

Thanks-

---

### Post by cruzer001 on 2018-04-10
> **oldfred said:**
> I do add noatime for mounting any partitions on SSD.
Interesting.  I always thought relatime was good enough for a SSD, but you like to remove all writes.

---

