---
title: "0% free disk space"
date: 2007-04-21
forum: General Help
---

### Post by matt91 on 2007-04-21
i have upgraded my server to 7.04 today, everything seems to work ok except from one thing. i have a 150GB data partition which is around 70% full but is showing that there is none left. i can delete files from this partition but i cant add files becouse of this. the partition is mounted in fstab with:
> /dev/sda1    /data/storage    ext3    defaults    0    0
this worked fine before the upgrade

---

### Post by taurus on 2007-04-21
What's the output of this command from a terminal?

```
df -h
```

---

### Post by matt91 on 2007-04-21
this is what i get where /dev/sda1 is the problem:

> root@server:~# df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda3             3.4G  2.6G  622M  81% /
varrun                506M  204K  506M   1% /var/run
varlock               506M     0  506M   0% /var/lock
procbususb            506M   80K  506M   1% /proc/bus/usb
udev                  506M   80K  506M   1% /dev
devshm                506M     0  506M   0% /dev/shm
/dev/sda1             143G  141G     0 100% /data/storage


---

### Post by taurus on 2007-04-21
```
sudo du -h /data/storage
```
That would show you how much space each directory in /data/storage is taking up.

---

### Post by matt91 on 2007-04-21
oh, problem solved! i made a backup before i upgraded and it seems to have also backed up a mounted folder which has filled the partition up. sorry](*,) could do with a bigger hard drive anyways

---

