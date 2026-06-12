---
title: "'attempt to access beyond end of device' in /var/log/syslog"
date: 2007-04-21
forum: General Help
---

### Post by chrisccoulson on 2007-04-21
I did a clean install of Feisty amd64 on a machine that I'd previously running Dapper on. I've noticed though that my syslog is full of messages like these:

```
Apr 20 15:55:45 localhost kernel: [   95.848917] attempt to access beyond end of device
Apr 20 15:55:45 localhost kernel: [   95.848926] sdc: rw=0, want=974583227, limit=488397168
```

This didn't happen with Dapper. Bare in mind that I'm running a striped array using DMRAID, and /dev/sdc is part of that array, so it's not actually mounted. fsck has now ran on all partitions on my striped array at least once since installing Feisty, with no errors. I've not noticed any performance hit and I haven't had any other problems. 

Is anyone else running a striped array seeing similar messages?

---

### Post by krizz on 2007-05-07
Exactly the same thing here. No clue if it's anything wrong or it's a false alarm. Everything seems to work ok thought.

Edit:
Googling around I read that it's not a real problem, but just that the kernel handles each disk of the raid as separate partitions too, that's why if complains about end of device.

Get a look at that:
[https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/106177/comments/8](https://bugs.launchpad.net/ubuntu/+source/dmraid/+bug/106177/comments/8)

---

