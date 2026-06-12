---
title: "How to generate file with alternating 0's and 1's"
date: 2012-10-17
forum: General Help
---

### Post by Valpskott on 2012-10-17
I've written a bash-script that I'm using to benchmark my NAS and various network file systems (CIFS, NFS, LOCAL), I intend to use it to pinpoint bottle-necks while fine-tuning.

First I copied a 4GB video file... but then realized that the disk I was copying from was a bottle-neck. So, after some googling I discovered "dd" and "if=/dev/urandom"

After some further testing, I wanted to compare the results with the speed locally on my NAS (Netgear ReadyNAS, which is debian based), and I noticed /dev/urandom was a bottleneck in itself (due to CPU-load).

So, I tried /dev/zero and wow, that was suspiciously "too" fast locally on the NAS.

What I'm looking for is some dev that can be used for random/garbage output (which can simulate the randomnes of a real file) without any substantially extra CPU load, nor any added disk-reading... or another way to get something similar.

---

### Post by Habitual on 2012-10-17
```
dd if=/dev/zero of=100Meg bs=1024 count=102400
``` creates a 100M file, adjust accordingly.

---

### Post by Valpskott on 2012-10-18
> **Habitual said:**
> ```
dd if=/dev/zero of=100Meg bs=1024 count=102400
``` creates a 100M file, adjust accordingly.

Thank you for your reply. Although, I already tried that.

In my original post:
"So, I tried /dev/zero and wow, that was suspiciously "too" fast locally on the NAS."

here are results from 2 of my tests.
1 minutes 52 seconds : using /dev/zero
2 minutes 15 seconds : prendered urandom from Ramdisk

So, my guess is that writing only zero's either doesn't make the write head do as much work or that there is compression over the network.

My NAS how ever does not have enough RAM to store a 4GB file on a Ram disk (locally on the NAS).

---

