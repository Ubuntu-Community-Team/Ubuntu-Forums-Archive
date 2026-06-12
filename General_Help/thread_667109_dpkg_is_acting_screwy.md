---
title: "dpkg is acting screwy"
date: 2008-01-14
forum: General Help
---

### Post by excelsior on 2008-01-14
Synaptic refused to run, and told me to execute "sudo dpkg--configure -a" in the terminal.
When I try to do that, I get

ubuntu@ubuntu:~$ sudo dpkg --configure -a
dpkg: failed to write status record about `libdjvulibre15' to `/var/lib/dpkg/status': No space left on device


What do I do?

---

### Post by amo-ej1 on 2008-01-14
free up diskspace ;-)

(see df -h to look at your current diskspace usage, one or more partitions will be full)

---

### Post by vojtech.t on 2008-01-14
"No space left on device"

Maybe the problem is that you fon't have enough place at harddisk...

Try for example "sudo apt-get clean" - that will delete downloaded packages...

---

### Post by excelsior on 2008-01-14
diskspace isn't the problem. This is a fresh hard drive, I just have gabby, and that's it-

ubuntu@ubuntu:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
tmpfs                 375M   16M  360M   5% /lib/modules/2.6.22-14-generic/volatile
tmpfs                 375M   16M  360M   5% /lib/modules/2.6.22-14-generic/volatile
varrun                375M   96K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
udev                  375M   84K  375M   1% /dev
devshm                375M     0  375M   0% /dev/shm
tmpfs                 375M   16K  375M   1% /tmp
/dev/sdb1             499M  449M   50M  90% /media/disk

---

### Post by Sef on 2008-01-14
> /dev/sdb1 499M 449M 50M 90% /media/disk

That's the problem.  that partition is almost full.

1) Empty out your trash.

2) ```
sudo apt-get autoremove
```

---

### Post by excelsior on 2008-01-14
> **Sef said:**
> That's the problem.  that partition is almost full.

1) Empty out your trash.

2) ```
sudo apt-get autoremove
```


1) That's not a partition. That's my removable pen drive. With it unmounted, I have

darren@darren-laptop:~$ df -h
Filesystem            Size  Used Avail Use% Mounted on
/dev/sda1              36G  2.3G   32G   7% /
varrun                375M   96K  375M   1% /var/run
varlock               375M     0  375M   0% /var/lock
udev                  375M   72K  375M   1% /dev
devshm                375M     0  375M   0% /dev/shm
lrm                   375M   34M  341M  10% /lib/modules/2.6.22-14-generic/volatile

Space isn't a problem. This is ubuntu off a fresh hard drive.

2) I can't run apt-get anything because dpkg is screwed up.

---

### Post by excelsior on 2008-01-14
Nevermind, you were right. With the pen drive removed I can run apt get --configure -a

---

