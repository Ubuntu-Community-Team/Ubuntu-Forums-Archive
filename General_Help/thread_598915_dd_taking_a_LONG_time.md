---
title: "dd taking a LONG time"
date: 2007-10-31
forum: General Help
---

### Post by Old Pink on 2007-10-31
> root@matt-desktop:/home/matt# dd if=/dev/sda1 of=/image.raw
10731357+0 records in
10731357+0 records out
5494454784 bytes (5.5 GB) copied, 5448.62 seconds, 1.0 MB/s
root@matt-desktop:/home/matt# dd if=/image.raw of=/dev/sda1

So it took 5448 seconds (90 minutes) to take sda1 onto image.raw

Now putting image.raw back onto sda1 (different drive in sda1's place) has taken, so far 4 hours (14400 seconds) 

Are things working OK? Should it take this long? Is it worth leaving it? Should I cancel?

---

### Post by Old Pink on 2007-11-01
I canceled. Turns out it was fighting through at 0.25 MB/s, and had done 3.9GB out of 5.5GB. 

Probably should have left it, but looks like it'd take over another hour. 

Just set it away now with ```
sudo su
dd if=/image.raw of=/dev/sda2 && shutdown -h now
```and it should hopefully get done today.

---

