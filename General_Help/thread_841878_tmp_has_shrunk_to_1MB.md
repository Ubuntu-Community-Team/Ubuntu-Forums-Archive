---
title: "/tmp has shrunk to 1MB"
date: 2008-06-26
forum: General Help
---

### Post by Cheiron on 2008-06-26
Hello,

I'm not entirely sure what has happened, but my /tmp folder has shrunk to 1MB in size according to `df -h`

[FONT="Courier New"]...
overflow              1.0M  1.0M     0 100% /tmp
...
[/FONT]

It has been causing problems with things like youtube, or even downloading files in epiphany. What can I do to fix this?

Thanks

---

### Post by p_quarles on 2008-06-26
Did you make a separate /tmp partition? 

Would you mind posting the complete output of df -h?

---

### Post by Cheiron on 2008-06-26
I did not create a separate /tmp partition.

Full output of df -h is
[FONT="Courier New"]
```

Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1             5.7G  4.7G  807M  86% /
varrun                756M  244K  756M   1% /var/run
varlock               756M     0  756M   0% /var/lock
udev                  756M   72K  756M   1% /dev
devshm                756M   48K  756M   1% /dev/shm
lrm                   756M   38M  719M   5% /lib/modules/2.6.24-19-generic/volatile
/dev/sda3              48G   42G  3.6G  93% /home
overflow              1.0M   20K 1004K   2% /tmp
gvfs-fuse-daemon      5.7G  4.7G  807M  86% /home/nathaniel/.gvfs
/dev/sdb1             3.8G  3.2G  662M  83% /media/disk

```
[/FONT]

Thanks for helping out

---

### Post by p_quarles on 2008-06-26
It looks like the /tmp/overflow thingy isn't the problem: it's the fact that the entire disk is like 90% full. If you can get rid of some stuff -- preferably by storing it elsewhere -- you may well see this problem go away.

EDIT: You may be able to free up some space on / by clearing APT's cache:
```
sudo apt-get clean
```

---

