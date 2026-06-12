---
title: "[SOLVED] An ext3 partitions mounts only for root"
date: 2007-02-16
forum: General Help
---

### Post by saul_2110 on 2007-02-16
Hi. I partitioned a logical unit in 3, hda5 for /, hda6 for my files and hda7 for the swap. 
Installed xubuntu in hda5 with the idea of being able to mount hda6 with r/w permisions so I could use it as a warehouse for my data.
The problem is that hda6 mounts with user and group set to root, and the permisions -rwxr-xr-x, which causes that only root can write.
How can I mount hda6 so that it mounts with the user or group I want?
Thanks.

---

### Post by taurus on 2007-02-16
Where do you mount /dev/hda6 to?  You can change the ownership of the mount point for /dev/hda6 with chown and you can read and write to that without using sudo/gksudo.

```
id
df -h
```

---

### Post by saul_2110 on 2007-02-16
That work! Thank you taurus.

---

