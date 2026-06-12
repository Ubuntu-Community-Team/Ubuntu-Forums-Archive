---
title: "[Solved] /tmp is not ready"
date: 2013-06-12
forum: General Help
---

### Post by spjackson on 2013-06-12
I've been running Lubuntu 12.04 64-bit on my main laptop for over a year. Recently, perhaps for a month, I've been getting the following oddity when booting. The Lubuntu splash screen is displayed, and shortly before the GUI login is presented, the following message flashes up for a few seconds.
```

The disk drive for /tmp is not ready yet or not present.

Continue to wait, or press S to skip mounting or M for manual recovery.

```
On waiting, it continues to boot, and I can login and observe no further problems. dmesg tells me nothing and I can't spot anything obvious in /var/log/...

Now, that sounds like a message from fsck or mount, but I don't have a separate /tmp partition.

```

xxx@yyyy:~$ grep tmp /etc/fstab
xxx@yyyy:~$ df
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda8       16543104 10723444   4979316  69% /
udev             1970272        4   1970268   1% /dev
tmpfs             791636      860    790776   1% /run
none                5120        0      5120   0% /run/lock
none             1979084      280   1978804   1% /run/shm
/dev/sda5      100790704 67536676  28134080  71% /home
xxx@yyyy:~$ cd /tmp
xxx@yyyy:/tmp$ df .
Filesystem     1K-blocks     Used Available Use% Mounted on
/dev/sda8       16543104 10723444   4979316  69% /
xxx@yyyy:~$ 

```

I don't regard this as a problem, just something of an annoyance and a puzzle because I don't really understand what's going on.

Any clues? TIA.

---

### Post by slickymaster on 2013-06-12
See this: [Bug #1091792 - The disk drive for /tmp is not ready yet or not present]("https://bugs.launchpad.net/ubuntu/+source/mountall/+bug/1091792")

---

### Post by spjackson on 2013-06-12
Yes, that sounds very much like it. Thanks.

---

