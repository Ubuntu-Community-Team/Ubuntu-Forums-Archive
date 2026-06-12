---
title: "slow boot due to &quot;random: nonblocking pool is initialized&quot;"
date: 2015-01-06
forum: General Help
---

### Post by a_m on 2015-01-06
Hallo,
I am running Ubuntu 14.04 (kernel 3.13.0-43-generic) on a Asus P6T Deluxe with an i7 920 processor and 12GiB of RAM. I noticed that the boot is remarkably slowed down by this 'nonblocking pool initialization', which takes >6 seconds. What is that? Why is it taking so long? On my other computer (Asus Zenbook; same version of Ubuntu, same kernel) it takes only 0.1 seconds.
Thank you!
```

[    4.025190] scsi 5:0:0:0: Direct-Access     ATA      Corsair Force GT 1.3. PQ: 0 ANSI: 5
[    4.025433] sd 5:0:0:0: [sdi] 234441648 512-byte logical blocks: (120 GB/111 GiB)
[    4.025477] sd 5:0:0:0: Attached scsi generic sg9 type 0
[    4.025952] sd 5:0:0:0: [sdi] Write Protect is off
[    4.025958] sd 5:0:0:0: [sdi] Mode Sense: 00 3a 00 00
[    4.026086] sd 5:0:0:0: [sdi] Write cache: enabled, read cache: enabled, doesn't support DPO or FUA
[    4.027380]  sdi: sdi1 sdi2 < sdi5 >
[    4.028023] sd 5:0:0:0: [sdi] Attached SCSI disk
[    4.057912] EXT4-fs (sdi1): mounted filesystem with ordered data mode. Opts: (null)
[    4.103264] random: nonblocking pool is initialized
[   10.733166] IPv6: ADDRCONF(NETDEV_UP): eth0: link is not ready
[   10.733172] IPv6: ADDRCONF(NETDEV_UP): eth1: link is not ready
[   10.755701] systemd-udevd[383]: starting version 204

```

---

### Post by ibjsb4 on 2015-01-07
Hi a_m

Running the same kernel and not seeing any hang time either.  Others have asked about this,
[https://www.google.com/search?q=nonblocking+pool+initialization&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a&channel=sb](https://www.google.com/search?q=nonblocking+pool+initialization&ie=utf-8&oe=utf-8&aq=t&rls=org.mozilla:en-US:official&client=firefox-a&channel=sb)
but I have not ran across a defendant solution.

I wonder if upgrading to the 3.16 kernel would do any good.  I believe thats the latest stable release with long term support.

---

