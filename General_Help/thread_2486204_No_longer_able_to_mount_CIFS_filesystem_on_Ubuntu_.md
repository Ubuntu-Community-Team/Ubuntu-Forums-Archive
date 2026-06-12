---
title: "No longer able to mount CIFS filesystem on Ubuntu 22.04"
date: 2023-04-22
forum: General Help
---

### Post by extraspecialbitter2 on 2023-04-22
After what seemed to be a minor update, I'm no longer able to mount CIFS shares on my Ubuntu 22.04 system. The command gives no errors, but nor does it mount successfully. Here is the command:
```

sudo mount -t cifs -o credentials=/home/pablo/.credentials //10.0.0.107/asiclient /mnt/*******r/asiclient

```

The only thing I see in /var/log/syslog is the following:
```

Apr 22 17:16:51 gaviota kernel: [27290.020908] CIFS: Attempting to mount \\10.0.0.107\asiclient

```

But the filesystem is never mounted. Per some recommendations on this forum, I have installed cifs-utils, but it made no difference. I'm perplexed because I've been using this mount command to perform backups for several years without issues.

---

### Post by extraspecialbitter2 on 2023-04-22
It seems that the mount was succeeding after all, but the proceeding rsync command was failing due to a bad external hard drive.

---

