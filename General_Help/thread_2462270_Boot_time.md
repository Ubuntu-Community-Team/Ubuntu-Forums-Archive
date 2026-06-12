---
title: "Boot time"
date: 2021-05-17
forum: General Help
---

### Post by mickee384 on 2021-05-17
My Ubuntu 20.04 takes 10 minutes to do a complete restart - Is that slow? Seems slow to me.

---

### Post by him610 on 2021-05-17
Yes, that seems to take a really long time. There are methods to investigate it.
Run this from from a terminal and show the results between the code tags in another reply
```

systemd-analyze critical-chain

```

The results will help with diagnosis.

---

### Post by GhX6GZMB on 2021-05-17
It's incredibly slow.
My 13 year old laptops take 25 seconds to boot from an SSD, 1+ minute from an HDD. Shutdown is 2...3 seconds.
You have conflicts somewhere in your system.

---

### Post by oldfred on 2021-05-17
Some things to review, but 10 min is a major issue, not just a "normal" slow boot issue.

Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2450783](https://ubuntuforums.org/showthread.php?t=2450783)
[https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499](https://ubuntuforums.org/showthread.php?t=2436900&p=13932499#post13932499)
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/](https://askmeaboutlinux.com/2019/11/28/how-to-speed-up-boot-time-on-linux-if-it-boots-slowly/)

---

