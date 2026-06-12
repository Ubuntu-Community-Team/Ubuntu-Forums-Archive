---
title: "gparted shows missing harddisk space"
date: 2007-06-05
forum: General Help
---

### Post by SpanishFranks on 2007-06-05
gparted shows /dev/hda1 (ext3, mountpoint /) as having size 111.28 GB, used 101.94 GB and unused 9.34 GB.
There is no unallocated space. 

However both xfce's free space checker and conky are showing me only 4.88 GB free. What is causing this discrepancy, and how do I get my space back?

Thanks

(gparted screen attached)

---

### Post by taurus on 2007-06-05
What's the output of this command from a terminal?

```
df -h
```

---

### Post by SpanishFranks on 2007-06-05
> **taurus said:**
> What's the output of this command from a terminal?

```
df -h
```

```
Filesystem            Size  Used Avail Use% Mounted on
/dev/hda1             110G  101G  4.9G  96% /
varrun                252M  200K  252M   1% /var/run
varlock               252M  4.0K  252M   1% /var/lock
procbususb            252M  136K  252M   1% /proc/bus/usb
udev                  252M  136K  252M   1% /dev
devshm                252M   20K  252M   1% /dev/shm
lrm                   252M   33M  220M  14% /lib/modules/2.6.20-16-386/volatile
```

---

### Post by taurus on 2007-06-05
If /dev/hda1 is an ext3, then the system reserved 5% of the disk space for root so in case you fill up your harddrive, the system won't crash.  So, that's why you don't see that 5GB from the output.

---

