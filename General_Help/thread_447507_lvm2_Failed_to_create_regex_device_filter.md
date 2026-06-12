---
title: "lvm2: Failed to create regex device filter"
date: 2007-05-18
forum: General Help
---

### Post by Boblin on 2007-05-18
Hello,
i have problem with lvm. On my server i have /dev/md0 - boot and /dev/md1 - 1 lvm volume group with more lv's. Everything worked well, but now i can't see lvm settings:

```
root@beta:~# cat /proc/mdstat
Personalities : [raid1]
md1 : active raid1 sda2[0] sdb2[1]
      146400256 blocks [2/2] [UU]

md0 : active raid1 sda1[0] sdb1[1]
      120384 blocks [2/2] [UU]

unused devices: <none>
root@beta:~# pvdisplay
  Failed to create regex device filter
root@beta:~# vgdisplay
  Failed to create regex device filter
root@beta:~# lvdisplay
  Failed to create regex device filter
```

I don't know why ;(

I have second server with same setup and without any problems.

System is Ubuntu 6.06.1 LTS + XEN (2.6.16-xen) 3.0.2-2 (from tgz).

Any help for me? 

Thank you.

---

### Post by fanatik on 2007-05-18
you probably just need to check the filter= line in your /etc/lvm/lvm.conf file.

paste the line here, and we'll take a look.

---

### Post by Boblin on 2007-05-18
Thank you! It works :)

---

